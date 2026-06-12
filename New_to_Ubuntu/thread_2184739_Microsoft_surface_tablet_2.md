---
title: "Microsoft surface tablet 2"
date: 2013-10-30
forum: New to Ubuntu
---

### Post by misswham2 on 2013-10-30
Morning, I have searched to see if this topic has been discussed and I couldnt find if it did.  I have been reading things about the new Surface PRO 2 tablet being able to run ubuntu.  It said you can disable secure boot in the PRO 2 but it doesnt say if u could in the regular Surface 2.  I know you cant in the original Surface RT but I was wonderfing if you could also in the NEW regular surface 2 that replaced the original RT?  I dont NEED a pro, I just like the concept of having ubuntu 12.04 on a tablet/laptop.

Also I saw that the PRO 2 has hyper V where you can install Linux in a virtual machine but it doesnt say that the Regular Surface 2 has Hyper V or if we could install it in a virtual machine.  I would just hate spending an extra $500.00 on a product where I wont use the functions of it just to be able to put ubuntu on the tablet.

Another thing, IF we can put it on either one, being dual boot OR  in hyper V or virtual machine, will the touch features still work because I have dual boot on a touch screen desktop and the touch function doesnt work with ubuntu 12.04 but it still works in windows 7?

Thanks in advance.

---

### Post by grahammechanical on 2013-10-30
> [COLOR=#000000]will the touch features still work [/COLOR]

You already know the answer to that.

> [COLOR=#000000]the touch function doesn't work with ubuntu 12.04 [/COLOR]

Some of this has been discussed at the Ubuntu Developers Summit (UDS) back in May. There is a video of the discussion.

[http://summit.ubuntu.com/uds-1305/meeting/21736/client-1305-convertibles-and-touch-desktop/](http://summit.ubuntu.com/uds-1305/meeting/21736/client-1305-convertibles-and-touch-desktop/)

Ubuntu with Touch gestures is being developed for mobile devices and that code will be converged on to desktop Ubuntu but not until Ubuntu 14.10 is released. I would think that a key factor in whether Linux/Ubuntu will install on any device on the market is the hardware of the device.

We would make a mistake to think that Linux will run on very new devices, especially device that are made specifically for operating systems of companies like MIcrosoft and Apple.

Regards.

---

### Post by PointSource on 2013-11-10
Yes, there was a bug with touch screens in 12.04, where the screen would stop responding to input. That has been fixed in 13.04.

The new Surface 2 (the sucessor to Surface RT) does not - and quite possibly will never - work with ubuntu, for the same reasons the RT does not: The device requires a signed bootloader whose keys are held by Microsoft.

The Surface Pro 2 does work, albeit with issues, [there is a forum thread discussion linked here]("http://ubuntuforums.org/showthread.php?t=2183946").

In regards to virtualisation, you would need an app in Windows RT that could do it, I haven't heard of one. The issue there is that the application has to work on an ARM architecture.

---

### Post by 3rdalbum on 2013-11-11
The Surface 2 and Surface 2 Pro are actually completely different machines.

Surface 2 Pro is basically an x86 desktop PC stuffed into a tablet, so you can run Ubuntu like on any other x86 PC. Surface 2 has an ARM CPU and by definition that makes it rather difficult to get a different operating system onto it.

Surface 2 is more like your TV or washing machine - you are stuck with what operating system is on it.

Oh, and as for virtualisation, you can only virtualise the same CPU as what you have. You can't use an ARM CPU to virtualise an x86 CPU, that is called Emulation and it carries a massive speed penalty. Not that there are any emulators available for Windows RT anyway.

In short, if you want to run Ubuntu, you must buy something with an x86 CPU. Anything else, you can consider to be unhackable. If you must buy a Surface it must be a Pro otherwise you are stuck with Windows RT and its limited variety of Windows RT-ARM apps.

---

