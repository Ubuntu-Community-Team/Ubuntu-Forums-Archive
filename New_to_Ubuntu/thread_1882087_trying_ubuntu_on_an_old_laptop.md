---
title: "trying ubuntu on an old laptop"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by Olethros on 2011-11-16
have an old gateway laptop that's missing a boot file for the windows it has, and I set up a live disc trying to boot it from that but it seems to skip past the disc whenever I try to boot up and all I get is a short checklist and a message saying error loading operating system. anyone have ideas on this? first time playing with any linux, so pretty clueless.

---

### Post by Rex Bouwense on 2011-11-16
Did you change the boot order in the BIOS?  If a CD will not work try booting from a flash drive.

---

### Post by Olethros on 2011-11-16
tried a flash drive, have hard drive at the bottom of the boot list in bios. if I knew how to completely format the hard drive I would there's nothing important on this computer.

---

### Post by Rex Bouwense on 2011-11-16
On some of the older computers (and some new ones as well), a flash drive is seen as another hard drive so check to see if there is more than one hard drive seen.
I have a couple of other questions.  When you downloaded the ISO did you check the md5sum?  When you burned the ISO to the CD did you burn the imagine to the CD or merely copy the files?  What did you use to create the bootable flash drive?

---

### Post by Olethros on 2011-11-16
just copied it onto a rw disc, just tried reorganizing the hard drive, and good call, it showed as a new hard drive. getting a blank screen now, and not sure how to proceed. it's a cruzer flash drive, and I just moved the ISO onto it. should it be empty first? no clue what the md5sum is but I'm pretty sure I didn't.

---

### Post by Rex Bouwense on 2011-11-16
First things first.  See here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Second, you cannot just copy the files on to a CD or a flash drive.  You have to burn the image.  Is the computer that you are trying to install Ubuntu on the same one that you downloaded the ISO to?

---

### Post by Olethros on 2011-11-16
nope, trying to install on an otherwise dead computer.

---

### Post by Rex Bouwense on 2011-11-16
Sorry.  My wife called for supper.  Now here are two help pages.  The first is installing from a CD and the second is from a flash drive.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
They are both self explanatory but I will be around for a while longer and if I am not someone else will jump in.  Enjoy.

By the way, what version are you trying to install.  As you can see I am using Lubuntu 11.10 which is the lightest of the Buntus and also the fastest.

---

### Post by Olethros on 2011-11-16
using an 11.04 I picked up a while ago when I was still looking for the charger to this dead laptop. and thanks for the assistance!

---

### Post by JayKay3OOO on 2011-11-16
I always use unetbootin to create bootable ubuntu flash drives from Linux ISO images.

Always worked thus far.

---

### Post by rng on 2011-11-16
You may try the livecd on some other computer. If it is booting fine then the problem lies somewhere else. Booting from usb may be difficult with old computers so using livecd, if possible, should be preferable.

---

### Post by David006 on 2011-11-16
Step One.

Powerup the laptop, and stop the boot process by pressing a key (usually 'F9' on a PC, but maybe 'Esc' for laptop).

You need to specifically pick the boot source, either the USB device or CD, for installing Linux from.


The auto-boot order function expects to see Windows (or DOS) on a lot of older BIOS, and will skip past Linux.

---

### Post by Olethros on 2011-11-16
hugely helpful. set up the disc properly, and found a way to clear the hard drive, and it's like butter. working great now, thanks!

---

### Post by Olethros on 2011-11-16
seem to be getting as lot of load time with not much apparent action. mouse doesn't respond well, and if it isn't a black screen its a colorful wallpaper, but otherwise featureless. still much better than what I had before, but any clues where to go from here? is this particular version too much for an old system? bumped up to 11.1, btw.

---

### Post by David006 on 2011-11-17
You should definitely try **Ubuntu 10.04.3 LTS**, which should be fine even for older laptop.


After that, by all means try out (demo mode) the latest: **Ubuntu 11.10 (Oneiric)**

---

### Post by mastablasta on 2011-11-17
If things are too slow you should use Lubuntu or Xubuntu. New Ubuntu uses a lot of memorry.
 
as mentioned anothe roption is 10.04.3

---

### Post by mörgæs on 2011-11-17
After 16 posts still noone has asked for a hardware description, so: Please give all the details.

---

### Post by mastablasta on 2011-11-17
LOL that's true.
 
To the OP open terminal and copy this command in it:
 ```
lshw
```
 
copy and post the output here using the code tags (the # icon when you make the reply). This command will list the hardware.
 
 
You can also use a graphic user interface for this but i am not sure where it is "hidden" now in Ubuntu as i use a different desktop environmnt.

---

