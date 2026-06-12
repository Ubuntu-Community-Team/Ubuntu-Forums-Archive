---
title: "black login screen, mouse/keyboard won't respond"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by noodles19 on 2011-10-25
toshiba  satellite l355-s9700. running ubuntu 11.04 no dual boot just linux. So  after some great times getting use to using linux this happens.... hit  power button, bios starts up, enter bios pswd, purple ubuntu sceen comes  up then it goes to my login screen... BUT no sound was made. My custom  background no longer shows up (a little paper icon with a red x does)  and even the login gray box is different and my keyboard or mouse wont  respond. The mouse is also stuck at the lower right corner. Show the  correct date and time up at the top middle. I have no clue what to do???  If I hit left shift key when starting, it will let me run the shell but  I have no clue how to fix this in there. PLEASE HELP

---

### Post by jnorthr on 2011-10-25
if it were me, i'd be SURE to take a backup of all your critical data, music, videos etc as you may loose these. You DO take backups anyway don't you ? Then find a live CD from the front of a PC magazine or a previous CD you created with ubuntu. Put that into your PC and reboot it. This should bring up linux from the CD. Then you can proceed to see if we can fix things this way. You can do all your backups to another drive, burn to DVD - whatever.

You can then research the problem by learning how to look at the system log files. These typically are found in /var/log and there is a system command called dmesg that shows the log content. Look at the bottom end of the log - for the newest messages. There might be clues as to what the problem is.

If you boot from a live CD, and open a console terminal, the dmesg command will show you the /var/log file from the live CD and not from your existing /var/log set of files on your hard drive.

---

### Post by Edward Nsolo on 2011-10-25
the same problem had happened to me in ubuntu 10.04 but i solved the problem by
1) CRTL + ALT + F8 THEN PRESS CRTL + ALT + F7.

if solution number doesn't work just try to boot with live cd or bootable flash disk then try to free some space in the partition containing your linux(ubuntu). then your done.

---

### Post by noodles19 on 2011-10-28
that ctr alt stuff did not work..... Just going to save all my stuff via live cd and reinstall. The point was to figure out why it crashed and fix it

---

