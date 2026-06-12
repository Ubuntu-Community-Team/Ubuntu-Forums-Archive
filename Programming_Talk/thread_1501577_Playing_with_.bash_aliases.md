---
title: "Playing with .bash_aliases"
date: 2010-06-04
forum: Programming Talk
---

### Post by hari.iiitb on 2010-06-04
Hi, 

I wanted to create an Alias, so that when I type 'c' in Terminal, C drive should be mounted and opened.

Here is what I did.

alias c='sudo -n mkdir /media/C; sudo -n mount -t ntfs /dev/sda1 /media/C; cd /media/C; nautilus .;exit'

I thought sudo -n would not ask me for password prompt and feed in my password by itself. But I thought wrong. How could I feed in the password automatically to the sudo command?

---

### Post by drpjkurian on 2010-06-04
You could also configure sudo with visudo  to allow you user to use make as sudo without password.

User_Alias USERS = your_user
Cmnd_Alias CMDS = /usr/bin/make
USERS ALL = (ALL) NOPASSWD: CMDS

---

### Post by hari.iiitb on 2010-06-04
Hi, I added your thing into my /etc/sudoers.tmp.

But still when I do sudo su, it is asking for password

---

