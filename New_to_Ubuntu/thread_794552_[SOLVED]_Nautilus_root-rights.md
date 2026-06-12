---
title: "[SOLVED] Nautilus root-rights"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by loldrup on 2008-05-14
I recently wanted to copy my homedir to a USB stick. For some rights-reason I couldn't just copy using nautilus. Therefor I had to use this command:

sudo cp -rf /home/jon /media/backup

(with the side effect that the copied dir had its owner changed to root)

Couldn't Nautilus have an easy way for allowing its copy/paste commands of to obtain sudo-rights so it can do the copying itself?

---

### Post by ZabiGG on 2008-05-14
Hi ;)

If you're familiar with the terminal, this quote will help

> **billgoldberg said:**
> It's easy to decide when you should use sudo or gksudo

gksudo: for graphical applications (like gksudo nautilus to open nautilus as root).
sudo: for use inside the terminal (or launching a file with gedit or something).

note: you can use sudo instead of gksudo 99% of the time without problems.

If you need more info, follow the link in my signature. There's an explanation and reference link on page 3, I think.

Have a great day,

ZabiGG

---

### Post by mkoehler on 2008-05-14
ZabiGG, be careful with your words.  If you want to open an application from a CLI interface (the terminal), either sudo or gksudo will work.  However, if you need root permission when you use ALT+F2, then you need to use gksudo.  However, there is a very specific difference in the two commands:

*SUDO* provides you with root permissions, but every action that you do is applied to the user that you are currently logged on as.

*GKSUDO* provides you with root permissions, but every action that you do is applied to the root's configuration.

That is to say, if I open up the compiz settings manager by typing "gksudo ccsm", nothing will appear to happen on my screen because the changes will take effect for the root account (granted you don't need root permissions to edit ccsm, but apply this concept to other situations).  It is not typically a problem because the setting which you wish to change are used by all accounts, but keep it in mind :)

*Edit: You need not use "gksudo" with ALT+F2, you can use sudo.  However, if have not gained root permissions recently, then you are not given a prompt in which to type your password.*

---

### Post by ZabiGG on 2008-05-14
Hence my directing to the complete information ;) I did say I was no expert.

Cheers :)

---

