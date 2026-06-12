---
title: "[SOLVED] Help!  Complete newbie, can't install Ubuntu over Windows XP!"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Moll on 2008-09-27
Hi there, 

Just got the Ubuntu 8.04.1 LTS desktop edition on CD and was gleefully looking forward to scrubbing windows off my computer.  However, windows doesn't seem to share this opinion - it wouldn't boot from the CD, then when I chose "help me reboot" on the CD, the keyboard won't tab to Ubuntu in the part just before startup.

I'm a complete newbie to Ubuntu, and am a bit clueless about advanced computing (such as BIOS etc).  Can anyone give me a few clues about how to fix this?  You may need to use very small words to explain any coding etc. XD  I'd be most grateful!

---

### Post by chrisod on 2008-09-27
Press F12 before you see the Windows logo when booting to bring up the boot menu where you should be able to tell the PC to boot from the CD drive. If it's not F12 on your system watch the screen when it first boots. There is usually a very brief message telling you how to get to the boot options menu. Once you see the Windows logo it is too late as Windows has started.

---

### Post by Moll on 2008-09-27
Thanks mate!  I've managed to get it to boot, now there's a whole new problem. XD Thanks for taking the time to reply.

---

### Post by thane1 on 2008-09-27
I agree with your first respondent basically.  It sounds like your computer may not automatically boot up from a cd before it tries the hard drive and your installed WinDuh os.  If this is the case, you (or a knowledgeable friend, etc) will need to reset the bios (basic input/output services) settings on a bootup of your computer to look in the cd or dvd drive for a disc (Ubuntu) before it looks for the operating system on your hard drive (windows).  I'll try to explain how this is basically done.  Give it a read.  If you've never done it and don't feel comfortable messing with your system yourself after reading this, I'd suggest finding a friend, who is competent at changing a bios and look over their shoulder and ask questions, while they look at your system.  Alternatively take it to a shop to have it done.  Different computers as the other writer alluded to use different codes (one keypress) to enter the bios feature, where you will then be able to change the bootup device priority yourself.  You can find what your specific key (to be pressed) is in your motherboard/cpu manuals, which came with your computer.  If you never got them with your computer, the information can be found by googling your system components.  Its usually something like the DEL or F2 key, depending on who makes your system.  It used to be much easier to time the pressing this key, when computers were older and slower, but now systems do everything so much quicker, that the window of opportunity to press this magical key is often quite short.  When your computer is first turned on there will be a brief delay, while a tiny file checks for some things needed to do a bootup.  After these things have been ok'd, you will hear one short beep (the POST check completed beep).  To make sure you hit your special bios entry key on time, start pressing it repeatedly, once you have heard that first beep.  Keep pressing repeatedly until you see a bios screen appear.  At this point I really need to stress, WATCH WHAT YOU THEN PRESS and then save.  You can really mess up your system and will then need to get it re-setup if there are any special bios settings already in there from when the system was built, which are different from the default bios settings.  Use the up/down, pg up/pg dn, left/right, enter, etc keys as shown to carefully navigate through the menu system until you come across the entry, which sets the boot-up sequence.  The usual suspects here are floppy, cdrom or hard drive.  Yours is probably set on floppy or hard drive first and probably has cdrom listed after the hard drive in this list.  You will need to rearrange the list until the cdrom is first before the hard drive.  When this is done you will need to navigate out of the bios menu system while saving your changes.  If you make a mistake or lose your place in the bios menu system, just navigate an exit from bios WITHOUT saving any changes. Once you have made the necessary bootup sequence change and saved and pressed exit, the computer will boot up using your new bootup sequence.  It will look first in the cdrom.  Learning how to alter your bios can be a real learning experience and can help to sort out some of your possible problems later on.  If you're not feeling comfortable with this though a local friend, who can guide you through this step by step can take a lot of the risk out of the process.  Just make sure they know enough to do it themselves.  Hope this helps.  Cheers.

---

### Post by kansasnoob on 2008-09-27
When you restart with the CD in the drive do you get a screen that looks like the first two screenshots here:

[http://www.herman.linuxmaniac.net/p24.html](http://www.herman.linuxmaniac.net/p24.html)

NOTE: don't use that tutorial to install!

I'm just trying to figure out what's going on.

Edit: Also is this a CD you burned? If so did you burn it as an ISO image?

---

