---
title: "[SOLVED] Need Help with MBR &amp;amp; Grub/ HD dying"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by garyed on 2008-08-16
Well my primary 80 gig HD is dying so I need some help.
I've been dual booting fine for a year or so with no problems.
Here's my set-up

Primary HD 80 gig : WinXP - all one partition
Secondary HD 300 gig: Feisty - Linux only

I can hear the clicking going on in the 80 gig & it has only worked twice
in about 15 boots so i know its dying. It's happened to me twice before with 
WD 80 gig drives.
    
I want to remove the 80 gig & just use the 300 gig.
I don't need anything on the XP drive & I don't need to dual boot anymore so all I need to do is get the MBR & Grub to work from the secondary 300 gig drive which will be my only drive on the machine. Now that both drives are  working for the moment I'd like to set it up now so I can shutdown & remove the bad drive & boot Ubuntu up with just the one drive.
Any help appreciated.

---

### Post by az on 2008-08-16
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I would remove the dead drive, boot the live cd and then restore grub to the only drive left.

See the link above on how to do that.

---

### Post by sharks on 2008-08-16
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by garyed on 2008-08-16
Well I used the live CD with the instructions & the Grub menu comes up but I get errors. I think I need to change my menu.lst but I can't get to my Hard drive from the live CD. Can someone give me step by step instructions on how to mount my HD from the live CD.

---

### Post by falcon61102 on 2008-08-16
First, what error are you getting?

If you boot from the livecd again, you can mount your internal HD and then edit the menu.lst as necessary.  To find out what you need to edit the root settings to, run:
```
sudo grub
find /boot/grub/stage1
```

The output of that should be what you need in the menu.lst where it says:
```
root (hd1,0)
```
or whatever is there now.

---

### Post by garyed on 2008-08-16
Well I got the HD mounted & changed my menu.lst but it still didn't help.
I've only got one HD /dev/sda so it should be easy but I can't get it to work. 
What am I missing?

---

### Post by az on 2008-08-16
If your drive still is the primary master, then you should install grub on hd1.  What does 

find /boot/grub/stage1
 
say?


EDIT:  I meant "Primary *Slave*"

---

### Post by falcon61102 on 2008-08-16
az, it should be hd0.  GRUB starts counting at 0 so the first HD would be 0 and then if he had a second HD installed it would be 1.  

garyed, did you reinstall the GRUB before changing your menu.lst?  And as az asked, what is the output of:
```
find /boot/grub/stage1
```

---

### Post by garyed on 2008-08-16
I finally got it.
Thanks for all the help.
All I had to do was shutdown completely & everything booted up fine.
I think I had everything edited correctly but every time I restarted it kept
going in a circle. My Grub menu would come up & when I chose Ubuntu it would just reboot again. I assumed it was an error but when I decided to completely power down this last time that solved everything.

---

