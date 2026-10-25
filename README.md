<p align="center">
  <img src="eh-logo.png" alt="eh" width="220">
</p>

# why eh?

`eh` is a small vi-like editor for people who want to edit text, not
configure an editor.

Here are a few useful `eh` commands and command sequences. They are intended
to be read, tried, and adapted.

## Start editing

```sh
eh file.txt
```

```text
i       insert text
ESC     return to command mode
h j k l move left, down, up, right
w / b   move by word
G       go to a line
W       write the buffer
Q       quit
```

Most commands accept a count:

```text
5j      move down five lines
123G    go to line 123
2dw     delete two words
3yy     copy three lines
```

## Move while inserting

In `eh`, insert mode does not prevent you from moving through the text.

The arrow keys, `Ctrl+B`, and `Ctrl+F` can move the cursor while you remain
in insert mode:

```text
insert → move → keep typing
```

The traditional vi workflow usually requires a mode change:

```text
insert → ESC → move → i/a → insert again
```

With `eh`, a small correction can stay in one continuous flow:

```text
insert → move to another line → continue inserting
```

This is useful when writing prose or correcting nearby lines without
repeatedly leaving and re-entering insert mode.

## Yank, delete, and paste

```text
yy      yank the current line
dd      delete the current line
p       paste after the cursor
P       paste before the cursor
u       undo
U       redo
```

Commands can be combined with motions:

```text
dw      delete to the end of the word
c$      change to the end of the line
y}      yank through the paragraph
```

## Search and replace

Search for an extended regular expression after the cursor:

```text
/pattern/
```

Replace the next match:

```text
/old/new/
```

Replace every match:

```text
/old/new/a
```

## Format a paragraph

Place the cursor in a paragraph and run:

```text
!{fmt -w68
```

`!` sends the text selected by `{` through the shell command `fmt -w68` and
puts the formatted result back in the buffer.

This is one of the useful things about `eh`: the editor can stay small while
Unix tools do the work they already know how to do.

## Work with text

```text
%       find the matching bracket
m a     set mark a
` a     return to mark a
> }     indent through the paragraph
< }     outdent through the paragraph
~       invert character case
```

Read another file after the cursor or write the current buffer:

```text
R       read a file
W       write the buffer
```

Lightweight. No configuration. No plugins. No separate directory of plugins,
scripts, or support files is required.

Just a small, keyboard-driven editor with UTF-8 support, shell filters, and a
focused command set.

## See also

- [eh project](https://codeberg.org/SirWumpus/eh)
- [eh(1) reference / README.md](https://codeberg.org/SirWumpus/eh/src/branch/main/README.md)
