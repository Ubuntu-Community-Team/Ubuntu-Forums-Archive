---
title: "help using the command line"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by Kojak Peg on 2013-05-10
Hi Everyone
If I had any hair left I'd be pulling it out, around about now. I've read the instruction website telling you how to execute some basic commands in the terminal, but I can't get them to work

I'm trying to check my iso is good before I burn it. So in the terminal is saids

kojak@kojak-OptiPlex-760:~$

so I type in pwd and it says 
/home/kojak
kojak@kojak-OptiPlex-760:~$ 

then I typed in ls and it says 
Calibre Library  Documents  Music     Public     Videos
Desktop          Downloads  Pictures  Templates
kojak@kojak-OptiPlex-760:~$ 

so then I type in 
cd /home/kojak/downloads

and it says 
bash: cd: /home/kojak/downloads: No such file or directory
kojak@kojak-OptiPlex-760:~$ 

and I've tried all sorts of combinations, but nothing. So what am I doing wrong 

Thanks

---

### Post by Vaphell on 2013-05-10
names are case sensitive, Downloads is not the same as downloads

learn to use tab for autocompletion
eg **cd Do[tab]** will put the whole name for you so you minimize risk of typos, in case there are multiple matches to what you typed you can get them printed with [tab]x2, eg
**cd D[tab][tab]** will produce Desktop Downloads, so you can add few more chars to remove ambiguosity and use [tab] again to autocomplete.

and use ~ as a shorthand for /home/yourname
eg **cd ~/Desktop**

---

### Post by arsenic23 on 2013-05-10
It's case sensitive.  'Download' not 'downloads'.

---

### Post by grahammechanical on 2013-05-10
When we open a terminal we are already in /home/ourusername. This is what you confirmed when you typed pwd. The command means print working directory. So, you did not need to type the path /home/kojak/Downloads. Just cd Downloads. If you type pwd when you are in the Downloads directory you will get /home/username/Downloads. But the command prompt should be telling you which directory you are in. kojak@kojak-Optiplex-760:~Downloads $. A change from kojak@kojak-Optiplex-760:~$

It is as clear as mud.

---

### Post by Kojak Peg on 2013-05-10
Thanks everyone I know it would be simple, but is b***d hard when you don't know how, lol

cheers

---

### Post by 3rdalbum on 2013-05-10
You can also drag files and folders to the terminal to fill in their paths.

For instance, type 'cd ' and don't hit Enter. Drag the Downloads folder to the terminal and its full path will appear. Press Enter and you will change directory to the folder you dragged in.

---

### Post by oldos2er on 2013-05-10
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by cortman on 2013-05-10
+1 for tab completion. It's possibly the single handiest feature of the shell.
Keep learning and trying, once you are somewhat familiar with the CLI GNU/Linux in general becomes much, much less scary. :)

---

