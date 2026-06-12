---
title: "Black Screen When Attempting Using the Lubuntu LiveCD"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by MyVitalRemains on 2012-09-04
Recently I tried to install Lubuntu via a frugal install with Unetbootin. So, instead of using a USB or a CD to boot the LiveCD, I used Unetbootin to enable me to boot the LiveCD via my operating system's (Windows XP) default bootloader. So after rebooting I was greeted with the bootloader screen and selected Unetbootin, after that this thing that said something along the lines of "To enter the menu please press Esc......8(countdown)" popped. So at times I waited for it to count down to zero and at times I went to the menu and selected "Try Lubuntu before installing" I was greeted with a black screen. Anybody know about this issue or how it may be fixed. 

[Here are the specifications for my PC if helpful. ]("http://www.cnet.com/laptops/acer-aspire-one-d150/4507-3121_7-33517218.html")

---

### Post by anewguy on 2012-09-04
Don't know if it will solve the problem or not, but the I945 is one the gpu's that sometimes requires nomodeset.  I *think* for that series of Intel it might be either "i915.modeset=0" or "i915.modeset=1" that you need to add to the boot line.  You should be able to add that entry via an entry on the menu before selecting Try Ubuntu.  There are MANY posts on the forum about using nomodeset (used to be for nVidia only, but it may be all-inclusive now) - follow one of those posts but replace "nomodeset" with one of the options I put in quotes above (don't include the quotes).

---

### Post by MyVitalRemains on 2012-09-05
Okay, thank you very much!

---

### Post by MyVitalRemains on 2012-09-05
I've previously had an issue with i915.modeset=0, which was one of the few options that worked for me (in a way). Whenever I added that to quiet splash, I got a VGA resolution output instead of the native 1024x600.

---

### Post by anewguy on 2012-09-06
That can be a driver issue - the trick is to at least get booted to a GUI and have an internet (hard-wired or wireless either one) connection and then go to Additional Drivers and see if it finds another driver and says it's not activated.  If it finds a driver and says it's not activated, try activating it and reboot to see if that changes things for you.

If no driver is found, or the found one is already activated, it might be worth putting:

ubuntu <type your version number here> 945 resolution

in a net search string and see what comes up.


There are also other options that can be tried to "define" your adapter, its options, your monitor and its options as well as possible resolutions to Ubuntu.

For now I would try the Additional Drivers thing first.  If that doesn't help, then try the net search.  If you see things that sound similar but need help just post back so we can try to help.  Lastly we can try to define things to Ubuntu.

---

### Post by MyVitalRemains on 2012-09-06
Okay, I checked the additional drivers and found nothing. I'll have to Google this. I created a thread about this a while ago, btw. [Link.]("http://ubuntuforums.org/showthread.php?t=2046952")

---

