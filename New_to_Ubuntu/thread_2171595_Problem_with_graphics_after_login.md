---
title: "Problem with graphics after login"
date: 2013-08-31
forum: New to Ubuntu
---

### Post by tim10 on 2013-08-31
Hello.  The problem is that Ubuntu installs fine...but after restarting and logging in, the graphics turn into a full screen of diagonal lines.  Complete garble. 
I don't know how common a problem this is, but I couldn't find a relevant post. Anyone know what's going on ??  Thanks in advance.  :)

---

### Post by grahammechanical on 2013-08-31
Could you give us a little bit more information? Not much. Stuff like, the Ubuntu version, the hardware specification (especially the graphic/video card).

You see, if you are using Ubuntu 12.04 I would give a certain set of directions but if you are using Ubuntu 13.04 I would give a slightly different set of directions.

Did you try the Live session before installing? Did you see this problem in the live session? When you installed did you tick to install third party software? If you did then that would automatically install a proprietary video driver and that could be the problem. An incompatible video driver.

At the Grub boot menu select Recovery mode and at the Recovery menu select Resume. That may get you to a desktop that you can use. Now open Additional Drivers and experiment with some of the video drivers listed there. You may have to wait a few seconds for Ubuntu to find video drivers and you will have to reboot to see if there is any improvement.

Specific directions depend upon the specific version of Ubuntu installed.

Regards.

---

### Post by Frogs Hair on 2013-08-31
Hello and Welcome 

It may be a graphics problem , so start by providing some information about your computer  . If you have older hardware Unity might not be supported in which case you could try Lubuntu or Xubuntu.

---

### Post by tim10 on 2013-08-31
> **grahammechanical said:**
> Could you give us a little bit more information? Not much. Stuff like, the Ubuntu version, the hardware specification (especially the graphic/video card).

You see, if you are using Ubuntu 12.04 I would give a certain set of directions but if you are using Ubuntu 13.04 I would give a slightly different set of directions.

Did you try the Live session before installing? Did you see this problem in the live session? When you installed did you tick to install third party software? If you did then that would automatically install a proprietary video driver and that could be the problem. An incompatible video driver.

At the Grub boot menu select Recovery mode and at the Recovery menu select Resume. That may get you to a desktop that you can use. Now open Additional Drivers and experiment with some of the video drivers listed there. You may have to wait a few seconds for Ubuntu to find video drivers and you will have to reboot to see if there is any improvement.

Specific directions depend upon the specific version of Ubuntu installed.

Regards.

Thanks for the reply.

I was using 13.04 - I burned the ISO to disk and it installed fine.
I have 12.04 and 13.04 downloaded now and intend on using 13.04.

I didn't try the live session so I couldn't say if it would've worked but I tried installing it twice with the same results.

I did tick the 3rd party software box.

I'm not sure how to access the "Grub Boot menu"....is this accessible at the Login screen ? I will try the different drivers if I can get in.

Just so you know....I'm running an old HP Pavillion a6030n PC,  X86
                                                   AMD Anthlon 64 Dual Core
                                                    Built in Nvidia graphics

Thank You :)

---

### Post by Quackers on 2013-08-31
Read about (and try) the nomodeset boot option in this thread. If it works make the change permanent by following the instructions below or install the proprietary graphics driver for your card.
[http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by tim10 on 2013-08-31
Thank You Quackers....and thanks to everyone else.  I tried the advise on the thread Quackers linked me to, and I'm currently using the "trial" mode off the disk.  I will now try to reinstall Ubuntu.  Thanks again and I will post if successful.

---

### Post by Quackers on 2013-08-31
Excellent. Keep that link handy as you will need to use nomodeset to boot the new installation and that link shows you how to do that.
Once booted, if there are additional graphics drivers you can install those and you won't need nomodeset again. If not, you can make the nomodeset boot option permanant, as described in that link.
Good luck and have fun.

---

### Post by tim10 on 2013-08-31
> **Quackers said:**
> Excellent. Keep that link handy as you will need to use nomodeset to boot the new installation and that link shows you how to do that.
Once booted, if there are additional graphics drivers you can install those and you won't need nomodeset again. If not, you can make the nomodeset boot option permanant, as described in that link.
Good luck and have fun.

It was a success.  Thanks again.  Things are a bit slower with this OS than Windows but I'm sure it's just a matter of a little research and some tweaking here and there.  Cheers.  :)

---

### Post by Quackers on 2013-08-31
You're welcome! Have fun.
It shouldn't be slower than Windows - it's usually faster by some margin. 
See how things go once everything is updated etc etc.

---

