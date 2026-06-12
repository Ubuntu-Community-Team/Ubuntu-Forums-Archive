---
title: "computer name change issue"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by VorlonShadow on 2008-07-17
I recently asked on this forum how to change the name of the computer. Someone said to edit the /etc/hostname and change it there.  I did this, and later found that I also had to edit the /etc/hosts file as well.  Well, I also discovered today after "receiving mail" in /var/mail/jesse that it makes reference to "root@uhura.SME".  uhura is the old name of the machine, so there appears to be some additional settings out there that have not been changed.  I'm assuming the e-mail server.  When I installed Ubuntu, I had it install the e-mail server, but I have never taken the time to figure out how to configure or use it.  Can anyone point me in the right direction?

Also, I tried to do a "grep" command to find out if there were any other files with "uhura" in it, but it I can't tell if it found anything.  It appears to start by showing a bunch of text at the beginning, none of which appears to be file names, then it just sits there for a very long time, and never displays any file names.

Thanks,
Jesse

---

### Post by nowshining on 2008-07-17
reboot into recovery mode - press esc @ the countdown

then do

sudo nano /etc/hosts

ur pw won't show as you type

alas

the proper way is to do it is in the terminal

sudo hostname <new hostname>

...

when ur done editing the hosts file, do the following:

ctral+x then press y and y again, then  type exit at the root prompt to continue booting up to a non-recovery environment.

---

