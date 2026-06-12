---
title: "Quick and dirty emacs initiation"
date: 2010-07-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Zorgoth on 2010-07-30
Surprisingly I did not find any beginner's emacs tutorials here already.

I am posting this because I, as a relatively recent emacs user (about two months) still remember how it was when I started.  There is the emacs tutorial, which is too long in my opinion, and others like it on the internet, but I haven't seen an introduction that both explains the fairly small number of simple concepts you need to know at first, tells you all the keyboard shortcuts, and isn't long and scary.  I am trying to give a good enough explanation of concepts for basic use and practice, which I think is the best way to learn, while keeping it short enough to use as an easy reference.

I am fairly new so if I made any mistakes please correct me.

Without further ado:

    Basics - Quit, select, cut, copy, paste, undo, run command

____________________________________________________________________


C-x C-c (Control-x followed by release and then Control-c) - Quit emacs

Ctrl-Space - set mark - this is used for selection like you would do with a mouse; the selected region is the area between the mark and your cursor, also the 'point'

Alt-W, Ctrl-W, Ctrl-Y, Alt-Y - the first three are analogous to Copy, Cut, Paste, respectively.  Alt-Y will cycle through previously copied (or technically "killed") text.

Note that emacs interprets "Alt" as "Meta" and will in its own notation refer to commands with Alt using an M, e.g. M-w is Alt-w.  You can also type Esc and then (quickly) the command.  So Esc w = M-w = Alt-w

Another note about copying: Emacs uses a different mechanism for copying and pasting than most things in X (I think) and so C-y will automatically paste the contents of the X clipboard, commands like C-w and M-w will *not* copy to it.  You shouldn't have to copy stuff from emacs to outside of emacs *too* often, but when you do, I would recommend that for short snippets you just select the text with the mouse and middle click where you want to paste, while for longer sections you use the menu bar or the button.  If someone knows a better way to do this (without damaging any current functionality) please tell me and I'll put it here!

C-x C-x - exchange 'mark' and 'point' - this basically takes you to your last mark and selects the text in between - many commands like searching automatically will set marks for you to return to, and you can set them manually with C-space.

Use C-_ to undo a command, and for redo, use C-g and then C-_ again - you are basically undoing the undo when you redo, and C-g "switches directions."

M-x - enter a command (use <tab><tab> for a list of commands beginning with an initial segment, just like in the terminal); pressing C-g (in general, this is the "interrupt" key for the minibuffer) will leave the "minibuffer" where you type commands (and other things like file names) - I find that thinking of likely command names and looking for them with tab is one way I learn a lot of new emacs tricks, particularly since emacs often tells you the keyboard shortcut for a command after you execute it.

    File operations

____________________________________________________________________


C-x C-s - save current buffer

C-x C-w - analogous to Save as...

C-x C-f - Load file

- you type the file names in the same minibuffer as you run commands in; you can use <tab> to complete a  folder/file name

Almost any command that requires input will use the minibuffer.

    Window and Buffer Operations

____________________________________________________________________


These are extremely useful so I put them in early.  You can use multiple frames to, for example, edit one or more source files and to have a shell to run commands, or use a debugger (gdb, a powerful debugger, is integrated with emacs), and compile your code.  Most powerful emacs tools will use these windows by default, and completions from <tab><tab> show up in them.

C-x 2 - split window vertically

C-x 3 - split window horizontally

C-x o - cycle through windows - note that is the letter o, not the number zero - you can of course also click on them in GUI mode

C-x rightarrow and C-x leftarrow - switch between "buffers" - currently open files and processes

C-x C-b - bring up a list of buffers

C-x k - kill the current buffer (this will expose another buffer)

C-x 0 - kill the current window (but not the buffer)

C-x 1 - kill all windows but the current window (not buffers)
ESC-ESC-ESC will also do this, so be careful about repeatedly pressing escape when you get annoyed...

C-x 4 0 - kill current buffer and window

    Search and Replace

____________________________________________________________________

Emacs has simple and powerful built-in search functionality that, due to its entirely keyboard-driven nature, is fast enough that it can be used far more frequently and usefully than the standard search boxes in standard graphical editors and word processors; I actually often use it to move my cursor within a line because typing something like "C-r <some letter or symbol> <enter>" often takes much less time than getting the mouse to the character or using the arrow keys or something similar.

C-s and C-r - search forward and backward - repeat C-s / C-r to keep searching

M-C-S and M-C-r - regexp (regular expression) search forward and backward (regular expressions - the important things are . is any character, .* is any string, empty or otherwise, \ is the escape character, ^ marks the beginning of line, and $ marks the end) - if you want to know more read "man grep"

After using M-C-s/r, you can use C-s/r to keep searching in the exact same way, no Meta necessary.

M-% (M-Shift-5 on a US keyboard) - replace
C-M-% - regexp replace (queries each time)
M-x "replace-regexp" - regexp replace (does NOT query)


    Miscellaneous

____________________________________________________________________


M-! - run a shell command

Use a command like "shell" or "eshell" to get a bash shell - they both have their advantages and disadvantages
- note that if you navigate to an already executed line in either of these shells, you can edit it and hit enter to execute it again

M-f and M-b - move forward or backward one word
You can usually also use C-left/right or M-left/right

C-p, C-n, C-f, and C-b: These replicate the functionality of the arrow keys; (they stand for previous [line], next [line], forward, and backward)

M-d - delete next word

C-k - delete everything to the end of the line

M-<backspace> - delete last word

M-x "goto-line" <type number> - goto a particular line number

M-< and M-> - goto beginning and end of buffer

C-M-b, C-M-f - go to next/last matching bracket

F10 or M-` will give you access to the menu bar

In console mode, you can type M-x "menu-bar-mode" to get rid of the menu bar on top - as far as I can see it is useless with no mouse; I don't use it much anyway except as a guide to keyboard shortcuts right after I see a new menu from some addon for the first time

If you don't get the proper mode for whatever you're programming (syntax highlighting and whatnot), you can often use a command to get it - e.g. "shell-script-mode" will give you shell script mode.  Usually this won't be a problem, particularly if you are using the right file extension.

____________________________________________________________________


I hope that my that this is helpful and can help both with getting started doing basic functions in emacs so that you can start learning the many, many powerful functions it can perform.

---

### Post by pgmario on 2010-09-03
Thank you very much. This is really appreciated, even after I read the tutorial that comes with emacs (C-h t).

---

