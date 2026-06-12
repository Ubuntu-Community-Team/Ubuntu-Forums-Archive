---
title: "Booting up into Ubuntu."
date: 2013-06-25
forum: New to Ubuntu
---

### Post by Spockhead on 2013-06-25
When I turn on my computer, and after the computer Post, the Ubuntu menu shows up. The first option is to go into Ubuntu as normal. The initial Ubuntu screen. If I don't choose anything, and after 20 seconds. (I think it's 20 seconds) my primary screen turns purple, no text, and there is  no hard drive activity until I push my Space Bar key on my keyboard. Then Ubuntu proceeds to load up.
 Is this a bug or a feature??

---

### Post by dino99 on 2013-06-25
you can see more boot details if you remove "quiet splash" from the boot line. Maybe it hang due to a bad bios setting, like an activated floppy device, or an usb device plugged.

---

### Post by Spockhead on 2013-06-25
I am a Newbie to Ubuntu and Linux, I don't know exactly how to remove "quiet splash". ( I know Linux and Ubuntu is the same, but I have tried other distro's for a very short period.)
Also why would pushing the spacebar make it continue to boot normally into Ubuntu if there was a USB issue. I do know that I have disabled in the BIOS floppy disk support. As I don't have a floppy disk drive.
Thanks for the help your trying to give.
Also thanks for any help that anyone may give too.
I have only been using Linux for about a month now, with no tutoring. Baby steps first before running. I did try Linux mint, Kubuntu, and now Ubuntu. All in a month time frame.

---

### Post by oldfred on 2013-06-25
Behind each menu entry in the grub menu are several lines that make up the boot stanza. Various required settings.

If you press e on the menu it opens up a simple editor to make changes just for one time. You can use that to test alternatives or different boot parameters.

If you press e and scroll down to the linux line which should be second from the bottom and scroll over to near the end (it may carry to next line but really is not a new line), you then should see quiet splash. Just use delete and remove just those two words quiet splash and then boot. Editor shows a couple of choice to boot but I use control x.

You then see time stamps and all the lines of drivers loading and other processes of booting.

But not sure why you have to press another key?

---

### Post by sandyd on 2013-06-25
moved to absolute beginners section

---

### Post by Spockhead on 2013-06-25
To Oldfred, dino99.
As soon as I had done that, And continued to boot, the screen went purple with no text.
I correct myself, It's after the 10 second countdown to chose in the Grub menu then the screen goes blank or blank purple screen. Like it wants to continue to boot with no hard drive activity. Until I press a key, then my HD light blinks.
I am gonna try a reboot again, and leave it for about 5 minutes to see what happens.

---

### Post by Spockhead on 2013-06-25
Wow, with no keys pressed, it took 7 minutes. much longer than windows. :D

---

### Post by oldfred on 2013-06-25
Have you tried replacing quiet splash with nomodeset?

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Spockhead on 2013-06-25
It worked, I had time today to test. Thanks!!
SOLVED
Can't find that friggin solved thing.

---

