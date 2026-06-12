---
title: "running programs"
date: 2010-06-20
forum: Packaging and Compiling Programs
---

### Post by kgcharan on 2010-06-20
Hi,

I recently installed Ubuntu 10.4 and also have installed the necessary packages for running the C, C++ and Java programs. the problem is: I always have to write the program in gedit text editor, save it **only in** the Administrator folder and then again have to go to the terminal and then compile and run.

Is there any way I can compile and run the programs saved in another directory?

Or much better, is there any editor to which i can go and then write the programs there and run--all inside the terminal itself (I have tried vi-editor but i dont know why, the keys are behaving abnormally.

What i need is: I need to have the flexibility within the terminal where i can go to an editor, write any program, come out of the editor, compile it and then run it--all in one window.

Please help. thanks in advance.

---

### Post by gmargo on 2010-06-20
Definitely try vim again - install the "vim-gnome" package first. This provides the gui and text versions (same binary actually) of vim.  The vim package that gets installed by default is "vim-tiny" which is just that.  Installing "vim-gnome" or "vim-gtk" will replace vim-tiny.

Then start a $HOME/.vimrc file with at least one command: "set nocp".  [The default vi-"compatible" mode is probably what made you think the keys were acting "abnormally".] See ":help vimrc" inside vim and /usr/share/vim/vim72/vimrc_example.vim for more ideas.

The great thing about using a text editor in a terminal window is that you don't have to exit the editor - just hit ^Z to put the editor in the background.  Then do your other stuff, like "make" and testing, then type "fg" to get the editor back.

There are other acceptable text editors out there too.  Just the the Editors section in Synaptic, or run "apt-cache search text editor".  Some of the popular ones are emacs, nano, jed.

---

