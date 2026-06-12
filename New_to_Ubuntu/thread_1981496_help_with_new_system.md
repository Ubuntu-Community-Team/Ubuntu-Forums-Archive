---
title: "help with new system"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by dbowlin17 on 2012-05-16
Hi,

I just installed 12.04 on a new AMD AM3 chip with onboard video. (i went for a budget (100 or less) build) and it went fine. until i turned the machine on after the installation of ubuntu when it says on a black screen in white text that it can not display my video format or something of the sort. any clues? i can't really give much more information or try to do anything as the system is just going to a black screen with white text. no ubuntu boot screen or anything. it looked fine and dandy when i booted from the flash drive though...

---

### Post by sammiev on 2012-05-16
Check out [this]("http://ubuntuforums.org/showthread.php?t=1613132") thread and maybe NOMODESET may fix your problems. Take a look at the other options as well. GL :)

---

### Post by dbowlin17 on 2012-05-18
the message is "cannot display this video mode"

not sure what to do. did a reinstall with nomodeset but it didn't fix anything...

---

### Post by dbowlin17 on 2012-05-19
update. i reinstalled with basically everything disabled/selected with the F6 thing. and update manager came up and is trying to install stuff... additionally, there was something about propriety drivers but i can't access any sort of navigation menu to actually get this driver installed. i hope that if i can get it installed then it will be good...

---

### Post by anewguy on 2012-05-19
I would try adding the following at boot time by editing the boot line (just like when you did nomodeset - press F6 while the machine is booting to get to the boot line - BEFORE ubuntu starts booting):

vga=778

or 

vga=793


I know these are depricated now since grub 2 but it's worth a try.  This options will set the video resolution mode lower, which may let your system boot.  If so, the screen may be a little distorted, but just go to additional drivers (assuming you have an internet connection!) and it should load whatever driver it might find for your video.

Please note the option is only good for a single boot when you just edit the boot line.  This is not a "fix" - just hopefully a work-around until you can let the system look for additional drivers.

Dave ;)

---

### Post by dbowlin17 on 2012-05-22
Dave,

Thank you for your advice. I did some install and it allowed me to get to the desktop, in some sense of the meaning, but at least enough for me to log out and log in using unity 2D. the computer still says that it can't display the video mode while booting, but in 2D unity, it all works fine. I found out that the graphics driver had already been selected and loaded before I even got into 2D, so not really sure where I should go from here. what are the disadvantages of using 2D over 3D?

---

