---
title: "Boot-repair --force-yes ist veraltet"
date: 2016-12-19
forum: New to Ubuntu
---

### Post by catgar on 2016-12-19
Hello to the community.
I am just starting with Ubuntu, producing a major (?)  problem with the boot-loader:
I installed Ubuntu 16.04.1 on a w7 64bit dual-boot computer (Changing from openSUSE to Ubuntu). Created separate partition for /home. Then used Paragon "backup & recovery 2014 free" to copy a saved home-partition. Then got the message to reinit the bootloader.
I followed the steps published in the Community Help Wiki: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair).
Download and install of Boot-Repair using an Ubuntu-live-DVD - no problem
Then click on "Recommended repair"
When the the window "Configuring grub-pc" appeared I clicked yes  for "remove Grub2 from /boot/grub?
Everything working  until the following message in the terminal: W: --force-yes ist veraltet, benutzen Sie stattdessen Optionen , die mit "--allow"" beginnen.
(Means that the order "--force-yes" is outdated and one must use an order starting "--allow")
Messages before this line were:
Deleting configuation files of grub-common (2-02-beta2-36ubuntu3.1) ...
Running in chroot, ignoring request.
Running in chroot, ignoring request.
Trigger for man-db (2.7.5.1) are processed ...
Trigger for install-info (6-1-0.dfsg.1-5) are processed ...
Then it ends with the input-request:ubuntu-gnome@ubuntu-gnome: ~
I decided to post it in a forum, first time, was requested to inform myself about how to do.....
Decided to store everything on the hard disc. So trying to open the fileadministration the screen froze.
Exept the mouse-pointer nothing reacts.

What to do?
Extinguish the computer by force and start the procedure again??

PS: I didn't read all the info about the forum till now. Shall do it when the problem is solved.I hope so!

---

### Post by oldfred on 2016-12-19
Are you still in live installer?
Normally you use REISUB to force shutdown.
       Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Was Internet working when you run Boot-Repair. The full uninstall/reinstall of grub requires Internet as it downloads a new copy of grub and that may trigger other updates.

If system does not boot:
       
 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by catgar on 2016-12-19
Hello oldfred,
thanks for answering to my problem.
I did as you told me- success!
The computer booted and now shows as follows:

GNU GRUB version 2.02~beta2-36ubuntu3.1

Minimal BASH-like line editing is supported.
For the first word, TAB lists possible command completions.
Anywhere else TAB lists possible device or file completions.

grub> _

You tell me how to continue?

---

### Post by oldfred on 2016-12-19
That is not success.
You probably have an old grub in MBR and new version did not get installed.

You may be able to manually boot. But probably easier to use Boot-Repair again.
        [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 
    
       [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655027#655027](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655027#655027)
See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,5) ? If so, run the next command. Change if not hd0,5.
configfile (hd0,5)/boot/grub/grub.cfg
OR:
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

---

