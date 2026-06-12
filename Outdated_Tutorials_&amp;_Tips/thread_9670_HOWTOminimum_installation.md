---
title: "HOWTO:minimum installation"
date: 2004-12-30
forum: Outdated Tutorials &amp; Tips
---

### Post by feneks on 2004-12-30
I recogniced a HOWTO which can help to set up Ubuntu on old computers. 
You will have to do some handwork of course.
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

I copied the text in parts from the hompage just to get sure the text doesn't vanish.

[SIZE=5][CENTER][B]Ubuntu Mini-RAM HOWTO
by [email]ingo@binonabiso.com[/email][/B] [/CENTER][/SIZE]

[SIZE=3]**Convention:**[/SIZE]
*# command*
Type command as root [SIZE=1](you can do a sudo su- before, in order to get the root-prompt. Or you put sudo before the command.)[/SIZE]

*$ command*
Type command as user.

[SIZE=3]**1 The Basesystem**[/SIZE]

Get Ubuntu CD-ROM see [http://www.ubuntulinux.org/](http://www.ubuntulinux.org/)
After inserting the CD-ROM into the drive, boot and when asked to press Enter, type *custom* before. (Not linux custom!)
[SIZE=1]The result will be a minimal-system with less than 300 MB on the HD and only a textprompt (no GUI). [/SIZE]

[SIZE=3]**2 Postinstall the GUI**[/SIZE]

[SIZE=1]I did it in the following order, but probably the order is not important:[/SIZE]

[I]$ sudo su -
# vi /etc/apt/sources.list [/i]
[SIZE=1](If you are not familiar with vi you can use nano or any other texteditor instead.)
Enable the universe-repository by removing the Hashmarks (=# (2 times)) [/SIZE]
[I]# apt-get update
# apt-get install icewm
# apt-get install xserver-xfree86
# apt-get install x-window-system-core
# apt-get install xdm
# apt-get install numlockx
# apt-get install xterm [/i]

[SIZE=1]The result is a system with X and iceWM as windowmanager. You log in as user and on the prompt:
[/SIZE]
$ startx
[SIZE=1]starts the GUI. (After the first reboot, xdm autostarts and puts you directly into the GUI-mode)
So far this system needs 468 MB on your harddrive. [/SIZE]


The homepage continues with installation of packets like Mozilla or Openoffice and shows the need of several packets for harddisk space.
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

---

### Post by Ozitraveller on 2004-12-30
There is also an existing thread titled :
'Ubuntu Mini-RAM HOWTO"

here:
[http://www.ubuntuforums.org/showthread.php?t=8338](http://www.ubuntuforums.org/showthread.php?t=8338)

with further information if anyone is interested!

---

### Post by towsonu2003 on 2007-03-05
also see [http://ubuntuforums.org/showthread.php?t=171203](http://ubuntuforums.org/showthread.php?t=171203) for a few other tips

---

