---
title: "pythonpath and alt-f2 problem."
date: 2011-01-29
forum: Programming Talk
---

### Post by FreeTheBee on 2011-01-29
Hi,
It seems I'm experiencing some path problems, when I run scripts
from the (alt-f2) run box.

I was trying to make a 'execute file' context menu item in nautilus.
Since this did not work I tried to get the command working from the run
box first. The command looks something like this,

xterm -e "cd /path/to/script;./scriptname.py;bash"

Initially I used 'gnome-terminal -x/e', which gave me 'failed to create
child process'. The cd is needed since the script operates on local
files in the directory. The bash command is only there to keep the
terminal window open after everything completes.

Using xterm, the script gets called as it should, except python gives me
an import error on importing a local module. The pythonpath is properly
set in my .bashrc and if I run the script either directly from a
terminal or nautilus it executes fine without errors.

I tried to source my .bashrc explicitly in the command I enter in the
run box. In addition I tried to specify the pythonpath in the command as
well. Neither worked.

Does anyone have an idea on what is going wrong?

---

### Post by FreeTheBee on 2011-01-29
I just tried the same thing on my pc at home, also with ubuntu maverick, and there everything works as it should.

I think I had a related problem earlier this week. I have added my texlive folder to my path in .bashrc. Compiling tex documents worked from vim, but gvim could not find pdflatex. After adding a path line for the texlive folder to my .vimrc all was good. This problem did not occur on my home pc either. 

It seems there is some issue with my path settings and gui programs. Unfortunately I have no clue about the difference in settings between the two pc's.

---

### Post by FreeTheBee on 2011-01-30
Specifying my path in ~/.profile solved the problem.

---

