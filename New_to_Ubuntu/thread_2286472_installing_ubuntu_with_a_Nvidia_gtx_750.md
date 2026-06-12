---
title: "installing ubuntu with a Nvidia gtx 750"
date: 2015-07-12
forum: New to Ubuntu
---

### Post by ricardo_fonzo on 2015-07-12
Hello, i want to install Ubuntu on my PC but i cant. i burned the 14.02 version on a dvd and and reboot the PC with the disc on it. when i choose the "install ubuntu" option the screen turn black and nothing happens (it's the same with "try ubuntu"). i found on google that there are problems with the drivers of the Nvidia gtx750, but i just find how to install the drivers but with ubuntu allready installed.

i have a Gigabite motherboard, Nvidia gtx750 and a screen via HDMI cable.

someone help me please D:

pd: sorry about my english, it's not my language.

---

### Post by oldfred on 2015-07-12
Have you tried nomodeset to get into gui with low quality graphics?
Or second menu entry recovery mode?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

[/URL]
 Maxwell 750 - kernel 3.15 or newer required
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://ubuntuforums.org/showthread.php?t=2265505](http://ubuntuforums.org/showthread.php?t=2265505)
Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)
[http://ubuntuforums.org/showthread.php?t=2261714](http://ubuntuforums.org/showthread.php?t=2261714)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)
 open-source driver support for Maxwell, there's none right now, at least not mainline.  Feb 2014
Asus z97-A with nVidia GTX 970 Ubuntu  15.04
[http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896](http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896)

[URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

### Post by ricardo_fonzo on 2015-07-12
it works with nomodeset, i have ubuntu now but everytime i turn on the computer i have to edit the command line on the Grub. can i fix that?

---

### Post by ricardo_fonzo on 2015-07-12
nevermind, i fixed it thanks!

---

### Post by Vladlenin5000 on 2015-07-12
The purpose of *nomodeset* is to avoid loading the open source driver, the one that doesn't support your hardware yet, so you can have video, albeit with low quality/resolution, and then install the recommended proprietary nvidia for your hardware, as explained in post#2, starting at "usually better to use PPA".

It ISN'T a permanent solution, actually NO solution at all... It's a mere temporary workaround until you get the proper drivers. Otherwise there's really no point in using such powerful graphics. You don't buy a Ferrari to drive at 5mph, do you?

---

### Post by buzzingrobot on 2015-07-12
The open source driver for Nvidia -- Nouveau -- used in that release has poor support for the specific graphic chip used in a number of Nvidia cards, including the 750. Nouveau is used by default if the kernel detects an active Nvidia card.  (I have a 750ti and see exactly the same behavior, on Ubuntu and elsewhere.) 

If you wish to use the Nvidia card, my suggestion is to suffer with the poor display just long enough to run Ubuntu's "Additional Drivers" app.  It will list the drivers that are available in the Ubuntu repos for the video card it detects is in use.  You should see that the Nouveau driver is in use, and should see that a few proprietary drivers are also listed.  Select the recommended proprietary driver, let it install (this takes a few, if not several, minutes) then reboot.  You should come up on the proprietary driver. 

I will add the caveat that I'm not using 14.04.02, and that 15.04 requires a driver in the 340-release sequence from Nvidia to work properly here; I don't know if those are available in the official repos for 14.04.2.  They are available in unsupported PPA's, but the upside and downside of doing that is for another question and another thread.

---

### Post by Vladlenin5000 on 2015-07-12
> **buzzingrobot said:**
> I will add the caveat that I'm not using 14.04.02, and that 15.04 requires a driver in the 340-release sequence from Nvidia to work properly here; I don't know if those are available in the official repos for 14.04.2.  They are available in unsupported PPA's, but the upside and downside of doing that is for another question and another thread.

In 14.04 it goes up to 331 only, I'm afraid, hence the PPA suggestion. And no, 331 won't work either for that card, according to many user reports (and dozens of threads here).

---

### Post by grahammechanical on 2015-07-12
At the end of July Ubuntu 14.04.3 will be released. That will come with newer Linux kernels and newer proprietary video drivers. At the right time we will be able to upgrade 14.04.2 to 14.04.3. But to get the newer video drivers we may have to accept something called a hardware enablement stack.

And alternative is to download 14.04.3 when it comes out. There are daily images being built which we can also download and install.

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/97708/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/97708/downloads)

Regards.

---

### Post by Vladlenin5000 on 2015-07-12
@grahammechanical 

Thanks for the additional info :p

---

### Post by mc4man on 2015-07-12
Haven't used nomodeset for an install  in some time but it can be that on recent Ubuntu releases when it is used to do the install it is added to grub so after installing, getting proper drivers ect you have to edit it out.
(that may have been the nevermind,, ect.

---

