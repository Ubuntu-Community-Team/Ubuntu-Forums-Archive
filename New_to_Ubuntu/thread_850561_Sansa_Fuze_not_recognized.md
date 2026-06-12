---
title: "Sansa Fuze not recognized??"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Andrew79 on 2008-07-05
I just got a Sansa Fuze. The computer won't recognize it. What do i need to do to make it recognized?

---

### Post by Fass on 2008-07-05
[http://www.howtoforge.com/sandisk_mp3_player_linux](http://www.howtoforge.com/sandisk_mp3_player_linux)

Does that help? Especially the bit about:

> Here is how to set up your Sansa player for use with Linux, requiring only one step.  On the Sansa main menu, with the player disconnected, push the menu button repeatedly past Music, Video, Voice, to "Settings."  This is where you'll start.  Push the center button, then the top button, "USB Mode."  From there scroll to "MSC" and press the center button again.  That's it.  The player will, when connected, appear as a standard flash drive.

There is also this thread on it in the fora: [http://ubuntuforums.org/showthread.php?t=827693&highlight=sansa+fuze](http://ubuntuforums.org/showthread.php?t=827693&highlight=sansa+fuze)

---

### Post by shortylonglegs on 2008-07-10
In a terminal, run lsusb.  This will mount it.  Its a temporary solution, as it has to be done each time you hook it up, but its better than nothing.

---

### Post by quietriot88 on 2008-07-12
I'm having this problem too (not trying to hijack the thread or anything, I just thought this would be a good place to ask). 

I've tried the MSC/USB mode method but the Fuze is still not recognized. I typed 'lsusb' into the terminal, which listed all the devices plugged into USB ports but the Fuze was not listed. It did not mount the device. 

I've even tried plugging it into different USB ports to no avail.

Please help!

Thanks

---

### Post by fmc6338 on 2008-07-14
I have the same problem, my fuze not getting recognized in msc mode on ubuntu.  If I plug in a plain old usb stick then the fuze will automatically be recognized, dont know whats up with that.  Therefore i plug in a usb stick and then my fuze and everything seems to work.  i guess i am waiting for a fix.

---

### Post by fmc6338 on 2008-07-14
ditto worked for me. thanks.

---

### Post by DarKnyht on 2008-07-16
I find that the fuze is added to the Places menu but not placed on the desktop until you click on it.

Annoying, but it works.

---

### Post by jaygo on 2008-09-04
there's something uniquely broken with the fuze. It doesn't function in MSC mode as other sandisk players -- it simply doesn't work. The most helpful solution I've found so far is to run lsusb after connecting it, then wait a few seconds for it to show up (in places, desktop, wherever).

---

### Post by e.m.fields on 2009-11-22
> **quietriot88 said:**
> I'm having this problem too (not trying to hijack the thread or anything, I just thought this would be a good place to ask). 

I've tried the MSC/USB mode method but the Fuze is still not recognized. I typed 'lsusb' into the terminal, which listed all the devices plugged into USB ports but the Fuze was not listed. It did not mount the device. 

I've even tried plugging it into different USB ports to no avail.

Please help!

Thanks

Hey guys. Same problem here.  No lsusb detection.

Dont' have a USB stick to test this "fix", but there must be a "real" solution somewhere.

Please someone respond if you've figure this out and I'll add it to a "solved" thread.

---

### Post by Talon1021 on 2010-08-31
I switched mine to be in MTP format not MSC manually and then it was recognized.... why does Auto-detect not work on these... some of you should try that instead. it may work like mine does now.... problem is, when it downloads the songs, it will not recognize them from the player.... nor does it show up in rhythm box.

---

