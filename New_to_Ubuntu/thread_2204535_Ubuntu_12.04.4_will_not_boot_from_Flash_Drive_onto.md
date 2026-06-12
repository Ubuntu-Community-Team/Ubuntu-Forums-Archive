---
title: "Ubuntu 12.04.4 will not boot from Flash Drive onto my 2008 HP laptop"
date: 2014-02-09
forum: New to Ubuntu
---

### Post by Dombon on 2014-02-09
Okay, I am going to go step by step with what I have done so far in my endeavor to get this OS on my laptop... 
**1)** I wiped my laptops Disk Drive with DBAN.
**2)** I downloaded the **Ubuntu OS *ubuntu-12.04.4-desktop-i386d*** *(I kept this as an ISO file.)*
**3)** I downloaded ***Universal-USB-Installer-1.9.5.2** ***and then followed the steps > create > finished installation on Flash Drive****)** 
**4)** I then went on my laptop,**F10 > System Configuration > Boot Options > Boot Order > USB Diskette on Key/USB Hard Disk**[I] (I sent this to the top of the boot order.)
[/I]**5) **I then took my Flash Drive that I had previously described and placed it in the USB port of my Laptop.  [B]
6) [/B]I then restarted my laptop and got the message > SYSLINUX 4.07 EDD 2013-07-25 Copyright (C) 1994-2013 H.Peter Anvin et al

This seems to be the only thing that happens, I have left it running for hours with no luck.  Sometimes it just turns off after 20 minutes at this screen, nothing changes.  I have tried **unetbootin-windows-585 **aswell with the same results.  I have also tried 2 different flash drives, they are formatted to _Fat32_, someone said try to format them to _Fal_ but I was unable to find that option available in the format index.  I have tried switching the isolinux files to syslinux with no luck either.  I tried to get help on the !ASK but after hours of frustration and being so nice to people who never replied to my question, I am left to wonder if I will ever get this laptop up and running.  I just need someone to stick it out with me and help a noob out with this. Please and Thank you, I will be very grateful.

---

### Post by QIII on 2014-02-09
I'll start out with you ...  but it's late and I don't know about sticking too long!  :)

My first question is always this:  Did you check the md5sum when you downloaded the ISO?

---

### Post by Dombon on 2014-02-09
Okay, I am going to go step by step with what I have done so far in my endeavor to get this OS on my laptop... 
**1)** I wiped my laptops Disk Drive with DBAN.
**2)** I downloaded the **Ubuntu OS *ubuntu-12.04.4-desktop-i386d*** *(I kept this as an ISO file.)*
**3)** I downloaded ***Universal-USB-Installer-1.9.5.2** ***and then followed the steps > create > finished installation on Flash Drive****)** 
**4)** I then went on my laptop,**F10 > System Configuration > Boot Options > Boot Order > USB Diskette on Key/USB Hard Disk**[I] (I sent this to the top of the boot order.)
[/I]**5) **I then took my Flash Drive that I had previously described and placed it in the USB port of my Laptop. [B]
6) [/B]I then restarted my laptop and got the message > SYSLINUX 4.07 EDD 2013-07-25 Copyright (C) 1994-2013 H.Peter Anvin et al

This seems to be the only thing that happens, I have left it running for hours with no luck. Sometimes it just turns off after 20 minutes at this screen, nothing changes. I have tried **unetbootin-windows-585 **aswell with the same results. I have also tried 2 different flash drives, they are formatted to _Fat32_, someone said try to format them to _Fal_ but I was unable to find that option available in the format index. I have tried switching the isolinux files to syslinux with no luck either. I tried to get help on the !ASK but after hours of frustration and being so nice to people who never replied to my question, I am left to wonder if I will ever get this laptop up and running. I just need someone to stick it out with me and help a noob out with this. Please and Thank you, I will be very grateful.

I apologize for posting this a second time in this forum, I figured maybe more people would see if in both sections.  If this is an issue, I have no problem with deleting one. Again I apologize.

---

### Post by Dombon on 2014-02-09
Ummm I dont know what that is?

---

### Post by QIII on 2014-02-09
Aha!  Well, guess what!  You're in luck and get a chance to learn something, which is the fun part of all of this.

Rather than trying to re-invent the wheel, have a look [here]("https://help.ubuntu.com/community/HowToMD5SUM").  If that just makes things clear as mud -- and you get back before I drag myself off to bed -- I'll try to answer any questions without being punchy, sleepy and stupid!

Let us know how you get along.  There are plenty of others here who will pick up if I nod off.

---

### Post by Dombon on 2014-02-09
I got to this site [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/) and am lost on what to download=(
Oh another 731mb file? LOL=( have a goodnight Qll

---

### Post by erasmusp on 2014-02-09
The very first download on this page - MD5SUMS - is a text file which contains all the check sums for the different versions of Ubuntu that you can download. Pick the check sum that is correct for yours and compare it with the ISO file you downloaded...

---

### Post by Dombon on 2014-02-09
This appears to be the check sum you are talking about, what do I do with it? [COLOR=#000000]14ad92270218a8925d802b3d3b6e140f I'm sorry if my questions are a bit nubbish, I've never used linux or ubuntu let alone installed an OS.[/COLOR]

---

### Post by QIII on 2014-02-09
OK -- just to let you know, the chances are slim that your image is fouled up but we need to check before we move on to more frustrating things only to discover later that the iso is not clean.

If you scroll down a bit on the page you posted, you'll see "Parent Directory" and just below that you'll see "MD5SUMS".  That link will take you [here]("http://releases.ubuntu.com/precise/MD5SUMS"), so just click on it in this post.

That will take you to a page that looks like this:

```
46e0fac240154bf59a11426a47a61363 *ubuntu-12.04.4-alternate-amd64.iso
788435b2778d6c7901f14d8cc3ceb4a7 *ubuntu-12.04.4-alternate-i386.iso
c7f439e864d28d9e5ca2aa885c4ec4cb *ubuntu-12.04.4-desktop-amd64.iso
14ad92270218a8925d802b3d3b6e140f *ubuntu-12.04.4-desktop-i386.iso
e83adb9af4ec0a039e6a5c6e145a34de *ubuntu-12.04.4-server-amd64.iso
0081e57fb8c7e4094fb9767384f087c6 *ubuntu-12.04.4-server-i386.iso
b2cb7cb840eaa2c2a6301cae3b94a179 *ubuntu-12.04.4-wubi-amd64.tar.xz
446ab62c33b15357c457078fa12dca43 *ubuntu-12.04.4-wubi-i386.tar.xz
da0cd423b2b4e4b899751f05a27adba0 *wubi.exe
```

The column on the left is a "hash".  Don't worry about what that means right now, because may become evident later.

What you need to do is find what you downloaded in the right column and compare the series of characters in the left column against what you get if you follow the instructions under "Check the iso file" in the [page]("https://help.ubuntu.com/community/HowToMD5SUM") I gave you previously.

If they match, we can be fairly confident that the iso you downloaded is not messed up.

Again, I'm either here or snoring softly if you have questions.  In case of the latter, someone else will be along shortly.

---

### Post by Dombon on 2014-02-09
So I open CMD.exe and open the ISO file?  I comfused because the instructions say open a terminal=/

---

### Post by QIII on 2014-02-09
Ah!  You see here is the place where the tired, punchy and stupid comes in.  You are obviously on a Windows machine and I should have picked up on that...

On the "HowToMD5SUM" page, scroll down a bit to "MD5SUM on Windows".  Let us know if the instructions there don't make sense!

---

### Post by Dombon on 2014-02-09
I'm sorry I should have made that more clear that I am doing this all from a Vista desktop>< My laptop is gonna be a ubuntu tho>.o

---

### Post by QIII on 2014-02-09
No prob.  My bad.  And don't worry, I won't bite you for using Windows.  I do, too -- along with several other Ubuntu "flavors" and other distros entirely.  Use what works, I say.

---

### Post by Dombon on 2014-02-09
They are different, so I guess I got a bad file from the ubuntu website lol???

!!!Correction after correctly loading my file into the md5sum checker thingy>< they appear to be the same after comparison.

---

### Post by QIII on 2014-02-09
It most likely means there was a burp in the transmission.  The file is right on the server.  This happens and this is why I asked before we moved on.

Delete the iso you downloaded before and try again.  Then go through the same check to be sure you got a clean copy.

Edit --  I'm slow.  I see your edit now.  And elfy is having a fine Sunday morning whereas I am having a tired midnight on Saturday!

---

### Post by Dombon on 2014-02-09
I got a clean one, nubbishly compared the Md5sum of the MD5sum checker to the hash

---

### Post by QIII on 2014-02-09
OK.  Assuming that you got the process of creating the installer done correctly, you need to eliminate the device(s) itself as the culprit.  Do you have a third one you can start over with -- a different brand?

EDIT -- and I am off to dreamland.  There are plenty of others here to help, so hang in there.

---

### Post by Dombon on 2014-02-09
Unfortunatley this are my only Flash Drive:/ Good night Qlll hopefully someone will reply either tonight or tomorrow, anyways im probably off to bed too.  I hope to crack this tomorrow.

---

### Post by oldfred on 2014-02-09
Merged two threads. Please do not create duplicates.

It seems you are doing it correctly & have correct download.
Sometimes different installers do work, but it seems you have tried a couple.

And sometimes certain flash drives, or different USB ports on computer make a difference.
What brand/size flash drive?
And some Gigabyte motherboards need a BIOS update to see flash drives over 4GB. So a larger one may not work?

        Installation/FromUSBStick - with lots of details on various USB drive issues by  sudodus
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

Edit - Just saw this a couple of threads down.
       Windows 7 DVD video How to burn ISO to DVD  just over 1 minute
[http://www.youtube.com/watch?v=bAr6NkMvImA](http://www.youtube.com/watch?v=bAr6NkMvImA)

---

### Post by Dombon on 2014-02-09
Thanks, you but I had a quick idea, I can currentl remove the hard drive disk from my laptop and connect it to my desktop.  Note I do not wish to change me desktop in anyway, but was wondering if I could install Ubuntu onto the harddisk via connection with my desktop???

---

### Post by oldfred on 2014-02-09
You usually can install from any system and use in another system. Just do not install any proprietary drivers.


But you need to install in a mode that works with old system.
If other system is  a new UEFI system, then you can only install in BIOS mode. The mode you boot installer in UEFI or BIOS is how it installs.

---

### Post by Dombon on 2014-02-09
Okay so maybe you could help me with that? I have a windows desktop, and would like to boot ubuntu onto my 2008 hp laptop harddisk while connected to my desktop.  Then I plan to simply plug it back into my laptop and hopefully that will work?

EDIT-- I Found this guide that I think applies to what I am talking about.  Problem is I get lost on some of the instructions, specifically step 3 and below:/
[https://help.ubuntu.com/community/Installation/FromImageLoadedOnHardDrive](https://help.ubuntu.com/community/Installation/FromImageLoadedOnHardDrive)

---

### Post by oldfred on 2014-02-10
Those instructions are to use another partition on a hard drive where you cannot boot a DVD or flash drive.
If you can boot the DVD or flash drive on your other system, you do not need those instructions.

It becomes like any normal manual install. Do not use any auto install options as that will normally install the grub2 boot loader to the MBR of the internal drive and then you will not be able to boot newer computer when you move drive to older computer. And drive will not have its own boot loader.

 Install to external drive. Also any second drive.
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)


My screen shots show the combo box at the bottom of the partitioning screen. Mine still shows sda, as it is not changed yet, but I am reinstalling to an existing partition (with old install) on sdc.

---

