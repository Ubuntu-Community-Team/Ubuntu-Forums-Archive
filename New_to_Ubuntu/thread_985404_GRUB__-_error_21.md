---
title: "GRUB  - error 21"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by RLuck on 2008-11-17
I have been using a full install of ubuntu 8.04  luv it...

Today on booting up I got the following:

"grub loading Stage 1.5"

"grub loading  please wait"
"Error 21"

I've searched and found references to going to a terminal and entering 
fixmbr - when I do I get 

bash: fixmbr: command not found

also found references to using fdisk /mbr   -  but will that not require me to reload everything?

Some years ago I tried linux and had to make several changes to lilo but have never messed with grub.  I feel and hope there is an easy answer to this without reloading  

I HOPE  -  Thanking everyone in advance !

Bob

---

### Post by jenkinbr on 2008-11-17
fixmbr is a windows command that you would use on a windows recovery disk.

What hard drive is your ubuntu installation installed on?  If it is on a second disk (/dev/sdb), I have found that it does not always spin up in time for grub to scan it, generating this error.  Press the reset button on your computer or turn it off and on quickly and see if the problem continues.

---

### Post by phidia on 2008-11-17
There is a solution to this I believe without resorting to a re-install.

See if the guide for repairing and re-installing grub [here]("https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB") will help you to recover grub. If you run into problems with that post the specific errors or problems you have.

---

### Post by caljohnsmith on 2008-11-17
Do you have more than one HDD? That could be the problem. How about first posting the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by RLuck on 2008-11-17
Thanks to everyone for the replys and help  -  I use Hard drive slides so the computer had only one HD on booting up.  Although I may have a flakey HD the install has work without a hitch for about a week now.  

phidia  -- That GrubHowto was about the best Howto I've ever tried to use.

>  Command line

   1. Boot your computer up with Ubuntu CD
   2. Open a terminal window or switch to a tty.
   3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
   4. Type "grub"
   5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
   6. Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
   7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
   8. Quit grub by typing "quit".
   9. Reboot and remove the bootable CD.

worked great - Mine was "root (hd0,0)and it booted right thru grub but then dropped me back into a terminal - I tried "startx"  I don't even remember where I got that - but didn't work.

I'll go back now and try to make a boot floppy so I can learn a little more about grub.  It may not like my monitor (lcd flat) but it has been using since I made the full install.  

Bob

---

