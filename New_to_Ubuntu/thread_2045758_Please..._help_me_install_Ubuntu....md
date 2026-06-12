---
title: "Please... help me install Ubuntu..."
date: 2012-08-21
forum: New to Ubuntu
---

### Post by Numbers3 on 2012-08-21
TL;DR: Windows 7 graphics updater is ******, can't uninstall Ubuntu, I need the black screen problem explained to me like I'm five. Would be open to uninstalling Windows and just running Linux if somebody can walk me through it and it would be easier.

Please.... for the love of god... help me install Ubuntu. Sorry if this is long but I've put in like 8 hours and all I want is a functioning (non-MS) operating system. I am ready to snap.

A little background... I have a new laptop, HP 2000. Preinstalled with Windows 7. I tried to put Ubuntu 12.04 on it, loads a black screen. After some looking online, found it had something to do with graphics card. I went to the Device Manager, did "update driver software" on my graphics card (Intel(R) HD Graphics.). Didn't work, came up with some error saying that it didn't have permission or something. Now when I do it, it just says that it is all up to date. Windows updater tells me that I have an update for the graphics, but when I try to install it I get an error. System restore did not solve the problem. I don't know how much this has to do with not loading Ubuntu, so sorry if it's irrelevant.

I've looked online for solutions to the black screen problem, what I've tried hasn't worked, though I also didn't understand a lot of it (Grub, nomodeset, BIOS screen... not sure what I was supposed to do half the time). I found some solutions that looked like they might solve it by booting from USB, so I downloaded an installer to my USB. 

Unfortunately, I can't seem to uninstall Ubuntu, so I can't boot from USB. When I click on the wubi installer, which previously told me to first uninstall ubuntu before I reinstall it, nothing happens. When I click the uninstall-wubi.exe, I get an error:
    "The version of this file is not compatible with the version of Windows you're running. Check your computer's system information to see whether you need an x86 (32-bit) or x64 (64-bit) version of the program, and then contact the software publisher."
I tried to install the 32-bit.

So yeah. That's my story, thanks for reading and sorry if it's long. I'm ready to snap, very busy with school and have wasted about 8 hours trying to put Ubuntu on my laptop, have no idea what to do next. If I have to, I would be open to uninstalling windows and just running Linux (I had to do that with my previous Vista machine), though I don't know how and I would still have the graphics card problem. Please help me!!!

---

### Post by Numbers3 on 2012-08-21
So a couple additional questions. Is the "black screen problem" a Linux thing, or just Ubuntu? If I tried a different version of Linux would it work with my graphics?

If I bought a boot CD and tried to load from that, would it work better/be easier to fix?

Thank you!

---

### Post by Numbers3 on 2012-08-21
Okay one more thing I forgot. When I try to open in Ubuntu, it flashes an error for like 1/10 of a second. I took a video with my camera to see what it says:

Try (hd0.0): NTFS5: No wubildr
Try (hd0.1): NTFS5: error: "prefix" is not set

No idea what that means, hope it helps.

---

### Post by newb85 on 2012-08-21
Welcome to Ubuntu.  I'm sorry your initial experience has been so frustrating.

How have you tried to remove Ubuntu?  (Did you use a certain uninstaller?)  What were the results or error messages?

Also, how does your initial install of Ubuntu prevent you from booting from the USB?  If you have the USB listed before your harddrive in your BIOS boot order, it shouldn't matter.

---

### Post by newb85 on 2012-08-21
Please see this other thread.  [http://ubuntuforums.org/showthread.php?t=861983](http://ubuntuforums.org/showthread.php?t=861983)

---

### Post by blade4 on 2012-08-21
Okay ,I'm a bit of a noob too , so I can only help so much , but here's a shot anyway . 

For updating your graphics , try going to intel's website and running the automatic driver update utility ( if you haven't already done so ) . But this won't help you much cuz linux doesn't use windows drivers .

Regarding the blank screen problem , ubuntu is usually pretty well configured for intel . But if you still have ubuntu installed , let it boot into blank screen , then press ctrl+alt+f1 : this'll make it go into terminal prompt mode . You can update your graphics drivers for linux from here (provided your net is working): 

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update
sudo apt-get upgrade
```
(now restart by entering 'sudo reboot' )
If x-swat doesn't  work , you could try xorg-edgers
 
 ```
sudo add-apt-repository ppa:xorg-edgers/ppa
```Hope this helps 

Cheers

---

### Post by Numbers3 on 2012-08-30
Thanks for all the advice, was able to solve it. In case anybody else searches this looking for a solution, post #8, Method 2, at [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) solved it for me. This solves it temporarily, and then if you read down on post #1 it gives instructions on how to make this permanent.

---

### Post by lopean on 2012-08-31
Glad you figured it out. Can you please mark this thread as "SOLVED"? Thanks

---

