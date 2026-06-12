---
title: "Problem with installation [I've made a video]"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by MeTRulez on 2012-12-07
Hi Ubuntu community!

                               I have a real problem over here that I don't know what to do. When I (try to) install Ubuntu 12.10 (and other version), the boot go well but when I arrive at the point I should see some question on where to install it, etc... (you know, when you see the mouse for the first time in the process!?) It freeze and nothing move at this point. I've made a video (sorry for my terribad english, it's not my first language) So it's popcorn time :popcorn: and time to watch my little movie that show you what's my exacte problem! Thx for any advises you could give me!! 

PS: I've checked the m5sum (or something like that...everything is right)

**Here is my video ====> **[http://youtu.be/d9mY6yAgmRw](http://youtu.be/d9mY6yAgmRw)

MeTRulez
Web developper

---

### Post by oldfred on 2012-12-07
I gave up on video, too long.

But I have the same BIOS. USB flash drives only boot from hard drive menu, I use f12.
But I did not see the hard drives in your BIOS screen?

Boot into liveCD and from terminal and post this for each drive.
       sudo parted /dev/sda unit s print


What computer & what video card?
 I have nVidia and have to add nomodeset with f6 from liveCD and on first boot edit grub menu to add nomodeset.
       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by mastablasta on 2012-12-07
ok so he has a SSD drive that could be significant.

but anyway, while those 5 dots are running oyu shoul dbe able to press esc and then you should see what is loading and if there are any errors or if it gets stuck.

furthermore after the 5 dots get loaded try crtl+alt+F1 to see if you can get into console.

another thing you can try is to take for example xubuntu and see if same thing happens there as well.

---

