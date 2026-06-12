---
title: "vim (zenburn) &amp; gnome-terminal color conflicts"
date: 2010-02-05
forum: Programming Talk
---

### Post by dreikin on 2010-02-05
**Problem:**
With the settings below, I get this weird effect where when I
o Scroll (with mouse) inside of vim, or
o Run a program such as man after vim
lines don't show up with the right background (pictures attached).

In both cases, the problem areas show fields with characters having the correct background, and fields without having the wrong background.
In the first case, the lines that have been scrolled have the dark background w/ characters, but a transparent background in the empties.
The second case is the similar, but with the colors reversed and is fixed by scrolling.

Any ideas on how to fix that?

**Setup:**
I have gnome-terminal set with a semi-transparent background, .bashrc with the line:
```
# Set to 256 colors
export TERM=xterm-256color
```

and .vimrc with:
```
" NOTE: See ':options' for more.

" Enable the mouse.
set mouse=a

" Enable 256 colors for the zenburn colorscheme
set t_Co=256
" Turn on syntax highlighting, letting it know the background is dark, and
" which scheme to use.
syntax enable
set background=dark
colors zenburn "delek desert, koehler, pablo, slate, torte...

" Ignore case in file searches..
set ic
" ..except when we use any upper case in the pattern.
set scs

" Make long lines wrap
set wrap

" Show the line number for each line
" (local to window)
set nu

" Highlight the line the cursor is on
" (local to window)
"set cul

" Number of spaces a <Tab> is equal to
" (local to buffer)
set ts=8

" Number of spaces used for autoindent
" (local to buffer)
set sw=8
" Do clever autoindenting
set si
" Do indenting for C code
set cin
```
*(maybe not the best, but I haven't messed with it in a long time).*

With the zenburn theme from here:
[http://slinky.imukuppi.org/zenburnpage/](http://slinky.imukuppi.org/zenburnpage/)

---

### Post by LKjell on 2010-02-06
You get the same problems using gvim?

---

### Post by dwhitney67 on 2010-02-06
I am unable to duplicate the issue with the scant information given.
```

1.  export TERM=xterm-256color

2.  Downloaded zenburn.vim

3.  Copied zenburn.vim to ~/.vim/color

4.  Edited ~/.vimrc to add the following:

    set t_Co=256
    set background=dark
    colors zenburn

```
Then I edited files using a gnome-terminal with tabs.  I spun the scroll-wheel on the mouse to go up/down the edited file.  Ran a shell command from within vim (!man fopen).

And still no issues... other than the zenburn background color (olive green) is not to my liking.

P.S.  I also use a semi-transparent terminal with a black background.

---

### Post by dreikin on 2010-02-06
> **LKjell said:**
> You get the same problems using gvim?

No, I do not have the problems when using gvim (that has another problem - [garbage in the terminal on launch]("https://bugs.launchpad.net/gentoo/+source/vim/+bug/402188"))

> **dwhitney67 said:**
> I am unable to duplicate the issue with the scant information given.
```

1.  export TERM=xterm-256color

2.  Downloaded zenburn.vim

3.  Copied zenburn.vim to ~/.vim/color

4.  Edited ~/.vimrc to add the following:

    set t_Co=256
    set background=dark
    colors zenburn

```
Then I edited files using a gnome-terminal with tabs.  I spun the scroll-wheel on the mouse to go up/down the edited file.  Ran a shell command from within vim (!man fopen).

And still no issues... other than the zenburn background color (olive green) is not to my liking.

P.S.  I also use a semi-transparent terminal with a black background.

Interesting.  I ran some more controlled trials, and it seems that the problem does not present if a shell command was used from within vim.
Also, the vim corruption only occurred on the computer with the large display, but the manpage corruption occurred on both computers tested.

**New trials:**

tested on:
[INDENT]desktop: Ubuntu 9.10 x86_64 (not upgrade)
laptop: Ubuntu 9.10 x86_64 (not upgrade)[/INDENT]

using:
[INDENT]current settings, and
the settings below.[/INDENT]

.vimrc:
```
syntax enable
colors blue
```

echo $TERM:
```
xterm
```

reboot.

[LIST]
[*]**Commands1**:
```
$ vim main.c
:!<man man || echo "hello">
:q
$ man <man || fopen>
```
No problems.

reboot.

[*]**Commands2**:
```
$ vim main.c
:q
$ man man
```
Problem shows up in manpage.

reboot.

[*]**Commands3**:
```
$ vim main.c
    <scroll off page with mouse>
:q
$ man man
```
Problem shows up in manpage.

reboot.

[*]**Commands4**:
```
$ vim main.c
    <scroll off page with mouse>
:!<man man || echo "hello">
:q
$ man <man || fopen>
```
No problems.

reboot.

[*]**Commands5**:
```
$ vim main.c
    <scroll off page with mouse>
:!<man man || echo "hello">
    <scroll off page with mouse>
:q
$ man <man || fopen>
```
No problems.
[/LIST]

All cases: man does not show problems until vim opened.
All cases: does not depend on gnome-terminal background (transparent or flat)

Final note: as one might expect, this does not happen in a non-X terminal ( <ctrl>+<alt>+<F4> ).

**Odd one out:**
There was one effect I was not able to reproduce on both machines, but I believe that to be from a hardware limitation.  The case where vim itself is corrupted was reproducible only on the desktop.  This appears to result from a combination of three things:

[LIST]
[*]Size of display: the laptop is 1440x900, but the desktop is 1600x1200.
[*]State of gnome-terminal window: Effect shows up on desktop only when the window is maximized by button.  Can be stretched larger, but then the effect does not show up.
[*]Tab number: this only happen on tabs that are NOT the oldest tab present in the terminal.  The oldest present tab is always fine, even after visual reordering.
[/LIST]

**TL;DR :**:
(this refers primarily to the multi-machine effect)

Effect DOES depend on:
[LIST]
[*]vim having a background color not matching the terminal.
[*]whether a shell command is executed from within vim.
[*]terminal type (linux terminal does not show the effect, others not tested).
[/LIST]

Effect MIGHT depend on:

[LIST]
[*]non-upgrade 9.10 x86_64 edition
[*]gnome_terminal not clearing something
[*]vim not clearing something
[*]compiz
[/LIST]

Effect does NOT appear to depend on:

[LIST]
[*]machine used (out of those available)
[*].vimrc
[*]$TERM={xterm-256color, xterm}
[*]file read (linux/{...}/main.c and ~/.bashrc tested)
[/LIST]

~/.bashrc (full) [attached]
~/.vimrc (full) [attached]

I'd do a bug report, but I'd rather get it narrowed down to one program first.

---

### Post by Kevinator on 2010-05-09
I know this thread is a few months old, but I'm investigating a (probably) related issue.

First things first, dreikin, did you ever file a bug? If so please post a link because I'd like to take a look.

For the mouse issue I don't know what the deal is. I can't reproduce it. You might want to try (in insert mode) pressing Ctrl-V followed by moving the wheel once to see what code the terminal is using. Figuring out what this code means is a pain in the ***, but you could post it for help. I get "^[[M`!!" for up and "^[[Ma!!" for down. The "!!" varies with the mouse cursor position (I kept it in the top left cell for testing). This page explains what it all means, but it's no easy task to make sense of it:

[http://invisible-island.net/xterm/ctlseqs/ctlseqs.html](http://invisible-island.net/xterm/ctlseqs/ctlseqs.html)

Moving on, the man page background issue is what really interests me. There's a bit of important background info here: xterm (and gnome-terminal by extension, which is based on xterm) has an "alternate screen buffer" mode that is used for full-screen applications like vim and less. You can usually tell when this mode is active because the scroll bar thumb expands to fill the scroll bar, which ceases to function.

The alternate screen buffer appears to have its own color settings. When vim is running, it sets the background color. It looks like when vim exits, this color is still set. The next time an application (like less) uses the alternate screen buffer mode, the alternate screen is automatically cleared, but the background color that gets used is still the one vim set. This gives results like the man page screenshot dreikin posted in the first message in this thread.

Here's a test command that demonstrates this issue:

```
echo -e "\e[?1049h\e[45m\e[?1049l" ; man man
```

That switches to the alternate screen buffer, sets the background color to magenta, and switches back to the normal screen buffer before running man. The results are pretty clear.

I think this is a bug, but I don't know exactly where the bug is or what project introduced it. It could be in gnome-terminal's implementation of the alternate screen buffer switch command (perhaps it should be reseting the background color first), or it could be in the terminfo codes that use that command. I think it can be worked around by modifying the terminfo codes, though.

---

### Post by Kevinator on 2010-05-09
After some experimentation I've hacked up this script to fix the alternate-screen-buffer-background issue:

```

#!/bin/sh

TMPFILE=$(mktemp) || exit 1
infocmp xterm-256color | sed -r \
    -e 's/^xterm-256color/xterm/' \
    -e 's/\\E\[\?1049l,/\\E[49m&/' \
    >> $TMPFILE \
    && tic $TMPFILE

rm -f $TMPFILE

```

Running this will create a new terminfo file, ~/.terminfo/x/xterm, that is based on the 256 color xterm terminfo file but modified to reset the background color when switching out of the alternate screen buffer. It also changes the terminal name in the file to 'xterm' to match the value of TERM that gnome-terminal uses. This could be bad if you happen to use other terminals that identify as xterm.

You can undo the effect by deleting ~/.terminfo/x/xterm, or the whole ~/.terminfo directory assuming you don't have anything else there.

Note that this makes it unnecessary to explicitly set t_Co=256 in your .vimrc file, since the terminfo database will now supply the correct value. It's probably not a great idea to tweak t_Co manually anyway, since it will be wrong for other terminals (like the linux terminal, which you'll need if you ever break X). Of course, zenburn won't work right on terminals without t_Co=256, so you should probably do this:

```

if &t_Co == 256 || has('gui_running')
    colors zenburn
else
    colors desert " Or some other 16-color scheme
endif

```

---

### Post by drdnl on 2012-05-21
Still present in 12.04, having a full height (1200px) VIM with differing background/terminal colours triggers it.

Attached screenshots. The hack above doesn't seem to work for me, do I have to do anything after applying it?

Current workaround seems to be shortening the gnome-terminal by 5px or so (IE: slightly less than full height and the effect stops)

---

