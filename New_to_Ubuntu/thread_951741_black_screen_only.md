---
title: "black screen only"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by melrokz on 2008-10-18
Hi. My ubuntu is giving me a black screen on login, with only terminal accessible on typing ctrl-alt-F1. Sometimes, even the login screen doesnt appear. What may I do?

I did a dmesg and saved the file as boot.messages. This file is attached, renamed as boot.txt, if needed by u.

---

### Post by phidia on 2008-10-18
Actually dmesg while useful only provides some of the start up log. If you want to trouble shoot this yourself you can look at /var/log/xorg.log & maybe messages in /var/log too.

Try typing > startx press enter and post the output of that.

You can also try > sudo dpkg-reconfigure -phigh xserver-xorg

Other useful things to know would be did you ever have a desktop login? 
If you did did you do an update recently and what graphics card are you using?

---

### Post by melrokz on 2008-10-18
Yes, I did have many successful logins. Yes, I updated xserver-xorg and gdm recently, but I've been having a lot of this problem before that. My graphics card is Intel 82845GL Graphics controller with 64MB video RAM.

---

### Post by melrokz on 2008-10-18
This is an error message that i got from xorg.21.log:Fatal server error:
xf86OpenConsole: VT_WAITACTIVE failed: Interrupted system call

---

### Post by phidia on 2008-10-18
You may want to check out the Ubuntu wiki guide [here]("https://help.ubuntu.com/community/Video#Intel") on enabling intel video cards.

---

