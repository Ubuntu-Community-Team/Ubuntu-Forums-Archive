---
title: "bash error"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by jose_2008 on 2008-08-22
Recently I started getting the following bash error when I open a gnome-terminal. 

bash: /etc/bash.bashrc: Interrupted system call
bash: /home/chandu/.bashrc: Interrupted system call
bash-3.2$

and then, as you can see, the command prompt does not show my_id@my_machine_name:~$.

After this it does not recognize some of the aliases, which means it is giving the error even before it sources the .bash_aliases file.

But even more interestingly, if I open one or two more terminals, I get a terminal that is named correctly, and without the bash error.

I would appreciate help on this.

---

### Post by glennric on 2008-08-22
Possibly there is an error in your ~/.bashrc file.  Try moving ~/.bashrc to ~/.bashrc.bak and then start a terminal.  See if that helps.  There are other settings files that could be causing the issue as well, for example ~/.profile.  If moving these files helps then you just have to go through that file and see what is causing the problem.

Considering the nature of your problem (first shell causes issues, later shells don't) it seems like it has something to do with the shell level.

---

### Post by jose_2008 on 2008-09-09
I tried a few things, moving the .bash* files and rebooting, but I still get the errors. It is not a huge problem since opening a gnome-terminal a couple of times, the error disappears.

Another thing I observed was that when I open an xterm, I don't get any errors. 

Any ideas?

---

### Post by casualfanta on 2008-10-27
bump

---

