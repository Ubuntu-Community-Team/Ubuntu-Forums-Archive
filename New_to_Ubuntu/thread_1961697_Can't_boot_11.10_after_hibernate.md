---
title: "Can't boot 11.10 after hibernate"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by BlueAZ on 2012-04-19
Worst crash yet...  Please help me!  I've had trouble suspending or hibernating in Ubuntu 11.04 with a dual HDD AMD-64 system (W-XP on other HD).  So I downloaded something called 'smartlyhibernate....'  Went to a T> & typed 'hibernate'.  It told me I needed to be root.  So I opened a root terminal (OH such a bad idea!), & typed hibernate.  There was a long pause while it seemed to be suspending, but then went completely off.

When I tried to start Ubuntu again, I got a blank screen, w/ no HD activity.  After searching & trying things (thru XP HD), Recovery Mode got me to the basic grub screen, & here's what it said:

error: out of disk.
grub rescue>   with a blinking cursor

I've typed in dozens of things, but nothing works.

Tried getting in with my Live CD, got to Advanced Options, F6 & adjusted an EDD setting, rebooted, just back to that sad grub message.

I've spent so much time tricking out my Natty, I really don't want to reinstall & lose everything.  Can anyone help me?  I promise I won't try to hibernate it again!!!!
Thanks  :confused:

---

### Post by for.i.am.root on 2012-04-19
Never run code as root!!!!!

See if you can point us to the file you ran as root so we can find out how some script kiddie messed up your rig.

---

### Post by sffvba[e0rt on 2012-04-19
Changed the title to something more appropriate.


404

---

### Post by BlueAZ on 2012-04-19
OK, sorry about title.

If you're not supposed to run code as root, why is there such a thing as a Root Terminal?

The thing I downloaded thru Software search for "Sleep" is named "smartly...  something" having to do with hibernate/suspend.  I can't access anything but my XP HDD now, so can't look up anything re: Ubuntu apps.

Thanks!

---

### Post by lisati on 2012-04-19
Always be careful about running things as "root".

Think of a business situation. The boss has taken the trouble to organize a decent set of equipment with a decent selection of software. He wants his employees to be able to get on with their work easily and efficiently. Being concerned about the safety and integrity of his system, he organizes a set of user permissions, so that the people can't hurt the system or make off with the data, accidentally or otherwise.

Now we move on to the situation at home. While it is true that we are in charge of our own gear, and should be allowed to do what we want, right? The trouble is that sometimes accidents happen. We might make a typo and do some serious damage. We also might hook up to the internet. Who knows what mischief the rascals who have designed a website might get up to? This is why people advise not to run everything as root: it adds a layer of protection against things going wrong.

---

### Post by NikTh on 2012-04-19
Hibernation wants big swap memory to function correct.
Suspend from the other not. 
But those are not only software - operation system problems , maybe are hardware problems also. 
Maybe your hardware not support hibernation or suspend or not responding properly . Maybe kernel bug or problem too. 
Its tricky things. 

To correct your problem the easy way i think is from LiveCD. 
You must mount your root drive. If that drive is for example /dev/sda1 then open terminal and 
```
sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
``` 
If you want to reinstall grub.. maybe works.. just try 
```
sudo grub-install --boot-directory= /media/sda1 /dev/sda
```
reboot .

If you want to connect , then ```
cd /media/sda1
``` .
There are all your system files .

---

### Post by for.i.am.root on 2012-04-19
I was thinking along the lines of a malicious script being run. If that's the case we have no real idea of what is going on.

The "out of disk error" I am assuming is not enough free space on the target drive.

The fact that he got GRUB at all means GRUB is still installed on the drive.

My approach would be to find out where said code was acquired from, determine what said code did, and finally attempt to repair damage.

Assuming he installed through "Software Center" the code is not malicious, just not functioning. If that's the case a chroot may resolve the problem:

Boot to live cd/usb.
Open a terminal (Applications --> Accessories --> Terminal)
```

mkdir /media/corrupt
mount /dev/sdaX /media/corrupt (X being the partition number of your linux system
mount -o bind /proc /media/corrupt/proc
mount -o bind /dev /media/corrupt/dev
mount -o bind /dev/pts /media/corrupt/dev/pts
mount -o bind /sys /media/corrupt/sys
chroot /media/corrupt
history (this will list all recent commands, the last one you ran was probably the suspect one)
which (output of above command)
dpkg --purge (output of above command)
sudo update-initramfs -u all
sudo update-grub
exit
sudo shutdown -r now
Remove usb/cd

```
This *should remove the program in question (as long as it's not malicious), repair your initramfs, repair your grub install and allow you to boot.

---

### Post by for.i.am.root on 2012-04-19
Constance83 and garyness if we could try helping the OP rather than just trying to beef up our beans it would be much appreciated.

If you can't / don't want to contribute to the conversation please refrain from posting.

---

### Post by BlueAZ on 2012-04-19
Correction: running 11.04 Natty on AMD-64 system w/ 2 HDD's: one w/ Ubuntu, the other with W-XP (which is all I can use now).  Recap: I typed 'hibernate' in a Root Terminal after installing from Software Center something called "smartly..." put your system to sleep or something like that.  Can't find it online, but it was offered when I searched "sleep" in Software Center.  Then couldn't boot into ubuntu.  In Recovery Mode, got:  Error: out of disk. Grub rescue>_   

The HDD w/ Ubuntu is 320 Gb, only about 10% used space.  I think it means I'm locked out of disk, not out of space.  Entering commands in Grub rescue> does nothing or returns w/ "no such disk" or "unknown command".

Using Live CD, 11.04, I can find /dev/sda1 = Linux.  Using sudo mount, it responds "according to mtab, /dev/sda1 is already mounted on /mnt".  Trying sudo mkdir /media/sda1, it says "Cannot create directory/media/sda1: file exists".  Sudo mount /dev/sda1 /media/sda1 causes an icon for my Ubuntu filesystem to appear on the desktop.  I can open it & see my Home Folder, my files, etc., but not run programs within it.  When I tried sudo grub-install --boot-directory= /media/sda1 /dev/sda,   it says"More than one install devices?"  cd command wasn't recognized.  Rebooted, & still had the Grub rescue> only.

Just went back in w/ Live CD, & tried for.i.am.root's solution.  Upon sudo mkdir /media/corrupt creation, mounting it showed an icon on the desktop for my W-XP HDD.  I didn't want to mess w/ that, as it's all I have now.  I tried dpkg --purge, using 'hibernate' or 'smartly...', & got the reply "no installed package".  I tried sudo update-initramfs -u all, & it was disabled in the read-only Live CD.  Sudo update-grub replied:  "cannot stat 'aufs'.

Since I can't copy any of this, I've typed it all dozens of times now...   So I hope someone can figure out what it all means.  I miss my Unity desktop, & am in need of files I hadn't backed up yet, for my work.  BTW, he's a she.    Thanks :confused:

---

### Post by for.i.am.root on 2012-04-19
Copy the text and E-mail it yourself. If your internet doesn't work from the live CD, save the page to a file on a USB stick for access later from within Windows / Linux.

If internet works on the live CD just boot into it and then come back to the forum. You'll figure it out. Just takes patience and time.

/dev/sda1 appears to be your Linux installation. It looks like it is auto mounting at /mnt.

sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
sudo mount -o bind /sys /mnt/sys
sudo chroot /mnt
history
Look for whatever is the last command you ran. hibernate or whatever.
which (program you last ran)
dpkg --purge (output from which)
sudo update-initramfs -u ALL
sudo update-grub
exit

Then restart.

---

### Post by BlueAZ on 2012-04-21
Tried all that.  Still boots into grub rescue>  I even downloaded a fresh iso of 11.10, installed it alongside my existing 11.04, restarted, & got grub rescue again!

History only shows current Terminal session activity, as far as I can tell.  No way to go back 3 days, unless you can tell me how.

I guess it's back to Windows for me -- just don't have this kinda time to waste...

Thanks anyway, it was fun for awile!  Wish you all well.

---

### Post by BlueAZ on 2012-05-09
[SIZE=3]Ended up missing Ubuntu...  Had to completely wipe the drive, then was able to fresh-install 11.10 from the live CD.  Works pretty well now, but I lost some files.  I was able to access & save some before wiping drive, but couldn't get T-bird to give me an email backup.

I guess this'll teach me to back up all to USB, DVD, or to my Windows drive, which hasn't lost a file in years!
[/SIZE]

---

