---
title: "Using commands in Emacs"
date: 2011-11-03
forum: Programming Talk
---

### Post by alexandros81 on 2011-11-03
Hi. I have open a file in Emacs called Insertion_sort_in_C.c.
I have found some commands in the web such as C-x 2 (split Emacs screen).
In Emacs under the 'Tools' option I have selected the 'Shell command' feature.
Now at the bottom of emacs window a command line prompt is awaiting for a command.
In this prompt I typed 'C-x 2' but the reply was '/bin/bash: C-x: command not found'
I typed as well the 'M-x gdb' command to initiate the debugger but '/bin/bash: M-x: command not found' came up
Then I run the debugger by the 'Tools' tab and the (gdb) prompt came  up. I typed 'break 11' to enter a breakpoint in line 11 of Insertion_sort_in_C.c but warning: 'No symbol table is loaded.  Use the "file" command' came up.

I also thought that when the debugger is running I could left-click in the fringe so that a red disk appears (a breakpoint). But nothing happens.

Is there anything wrong with Emacs/gdb?

Alexandros

---

### Post by schauerlich on 2011-11-03
C-x 2 and M-x are not commands, they are a notation for keyboard shortcuts. See [here](http://sean.wenzel.net/docs/emacs/quick_reference/).

---

### Post by cgroza on 2011-11-03
Those are not commands. In emacs, commands are made of words separated by hyphens.
Those are keyboard shortcuts intended to use the emacs commands faster.
In emacs, every action is a command. Even the keys a-z are mapped the self-insert command.

---

