---
title: "[SOLVED] Cannot Install 8.04 from CD"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by bettyhills on 2008-11-02
I have downloaded the Ubuntu 8.04.1 standard desktop i386 .iso several times and cut to CD from various burners onto different media **12 times**.  (Also burned at slowest possible speeds.) All check out okay but will not install onto an AMD 1700 2.66ghz 512mb 80g drive Win98 PC that I am trying to convert to Ubuntu.

I get various responses when booting from the Ubuntu installation CD depending upon which of the 12 CDs is in the drive.  Sometimes he PC simply bypasses the drive going straight to Windows.  Sometimes it hangs at the Ubuntu graphical menu.  Sometimes it passes the menu but gives me an "In/out error Reboot" box. Sometimes it passes the menu, goes to black screen, and feeds a string of error messages slowly from which there is no return but to turn off the PC.  I cannot get it to repeat that error to write down the error message strings.  **In/Out ERROR** is the most common message.

I replaced the ancient CDrom drive with a less old one.  The "newer" drive reads music, pictures, and text files just fine.

I tried installing from a flash drive but the PC bypasses the USB port in startup and does not allow that change in the bios.

I do not want to install Wubi.  I want a full Ubuntu installation ridding myself of Win98 forever.

Any guidance will be most appreciated.

---

### Post by roger_1960 on 2008-11-02
Hi

Very frustrating!  A few thoughts: (sorry if I'm stating the obvious)

Are you 'burning' a disc image from the ISO onto CD rather than just copying it? - (I would guess you are doing this right from your post)

Have you got another PC you could test the 'live' CD in to check its OK?

Are you sure its not a hardware (RAM or HDD) problem with your old PC - thats what it sounds like.

---

### Post by Daveth on 2008-11-02
or, have you tried the alternative install cd option?

---

### Post by bettyhills on 2008-11-02
Yes, the .ISO files were extracted properly and burned using two different programs (just in case that was the problem.)  The installation CDs check as okay, and boot into Live sessions on other machines just fine.  

The alternate install CD did not work because of the In/Out Errors.

On the Win98 PC **In/Out Errors** occur even with prior distro CDs so I am thinking that it is something about the CDrom **Drive** OR its **Interface** into the PC.  The PC manufacture date is 1999, but its specs should be able to handle Ubuntu.

Questions:
1.  Is it possible to do a _full_ install of 8.04.1 from a **set of floppies**?  

2.  Is it possible to do a full install of 8.04.1 from another PC on the **Windows home network**?    

3.  Is it possible to do a full install of 8.04.1 from the **hard drive of the PC**?  

4.  Is it possible to do a full install of 8.04.1 **directly from the Internet**?  

5.  Is it possible to **install without rebooting**?  I have the distro on a USB flash drive that can be read once I am in Win98 but not during the boot sequence.

If any of the above are possible, please tell me how, step-by-step.  I am a beginner, will follow directions carefully, and am trying hard, so will be grateful for any help.  Thanks in advance.

---

### Post by diablo75 on 2008-11-02
It is quite possible that your BIOS is out of date.  Visit the manufactures website of your motherboard and see if the BIOS version you have is up to date or not.  I had this exact same problem on a Winfast motherboard until I updated the BIOS.  It works flawlessly now.

[http://davestechsupport.com/blog/2008/04/07/troubleshooting-the-isolinux-checksum-error/](http://davestechsupport.com/blog/2008/04/07/troubleshooting-the-isolinux-checksum-error/)

---

### Post by bettyhills on 2008-11-02
Thanks for the excellent suggestion.  The BIOS is now up to date, but the CD installation still refuses to load.  Rats!

Can anyone tell me how to install from the alternative locations I asked about:  floppies, Internet, home LAN, etc.?

Thanks.

---

### Post by ugm6hr on 2008-11-02
These may be of interest to you:
[http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)
[http://ubuntuforums.org/showthread.php?t=666267](http://ubuntuforums.org/showthread.php?t=666267)

Unfortunately, I have no idea if it is your CD-ROM that is the problem.

If you can't boot a LiveCD, not sure how you'd be able to create a separate partition for the ISO to use the 2nd method.

---

### Post by Daveth on 2008-11-03
have you tried cleaning the cd-rom drive laser. I assume this box has been sitting around the house for a while and could well have the world's fluff repository clouding the head reader, so that a cd read is patchy. Also, physically unplug and re-plug in the drive cable back into the motherboard - it may not be properly seated.
Other than that, buy a new one for Christmas!

---

### Post by bettyhills on 2008-11-03
Thanks to you all for the excellent leads.  

Unetbootin sounds great and a perfect solution for a non-CD installation, but the fine print reveals that it does not work with Win98, sadly, my situation. 

The CDrom drive, a replacement for an earlier model, was carefully installed after cleaning it.

The install discs read on newer CDrom drives in the building, soooo... we moved to the final suggestion.  A new CDrom drive is on order.  

Thank you for taking the time to think about this and write.

---

### Post by bettyhills on 2008-11-05
The new CDrom drive arrived, was mounted, read the Ubuntu installation LIVE CD fine, and installed Ubuntu 8.04.1 perfectly in under an hour.

It seems that the two older legacy CDrom drives that I was using were not able to read new media created by newest generation burners.

That said, I am extremely grateful for all your suggestions because while troubleshooting, the BIOS was updated to the max, PC was cleaned, cables tightened, and the former OS backed up as a hedge against any failure.

Thanks to all.

---

