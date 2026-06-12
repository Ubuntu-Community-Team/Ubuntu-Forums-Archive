---
title: "Dell Dimension 4400, 256 MB RAM"
date: 2014-12-17
forum: New to Ubuntu
---

### Post by adam108 on 2014-12-17
Hello all.  I am new to linux systems and am in need of help.  First let me state that I am pretty ignorant when it comes to computers.  I do not know much more than how to use windows and even that is a basic "user" understanding.  I have searched the internet for solutions to the problem mentioned below and end up coming away more confused than I started.  So I have tried to solve this problem on my own (for about a week now) and am finally giving up and coming here for help.

I have an old Dell Dimension 4400 desktop that I would like to install Lubuntu on.  It is currently running Windows XP Home Edition.  I have no information on this computer that I need or want to save, I just want to totally do away with XP.  I have tried installing Lubuntu from a DVD with an ISO image burned onto it.  I get as far as the Lubuntu screen asking what I want to do, I click "install Lubuntu".  The computer runs through the screen that says "Lubuntu 14.10" with the 4 dots below it indicating progress.  The computer then goes to the bluish purple screen with the wavy Lubuntu lines on it and then stops.  The computer just sits there and does nothing else.  I have allowed the computer to run all night in hopes that it is just slow but it never progresses past this screen.  I have also attempted to do the install from a USB drive however every time I try that the computer gives me the finger.  I cannot get the computer to boot from the USB drive and when I attempt to open any of the information on the USB drive in XP I get the same result (the finger).

I am looking for help.  As I mentioned I do not care about what is currently on the computer and just want to get rid of XP.  I am including any and all possible specs on the computer below that I can find.  Any help would be greatly appreciated.
Thanks

Dell Dimension 4400
Windows XP Home Edition Version 2002 Service Pack 3
Pentium 4 1.60 GHZ
256 MB RAM
Display Adapter- RAGE 128 PRO Ultra GL AGP
Hard Drive-75 GB

---

### Post by grahammechanical on 2014-12-17
Clueless and need help? Aren't we all? :)

Here is the problem. 256 MB RAM. and then there is the display adapter. It is AGP. That means that it is very old. How much of its own memory does it have or does it use some of system memory (RAM). It may be called "shared memory."

[http://askubuntu.com/questions/162626/what-are-the-minimum-system-requirements-for-lubuntu](http://askubuntu.com/questions/162626/what-are-the-minimum-system-requirements-for-lubuntu)

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

[COLOR=#333333][FONT=Ubuntu Beta]> The default "Desktop" installer requires 384-800 MB of RAM (depending on selected options.) If you have problems, please use the ["Alternate" installer]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO").
[/FONT][/COLOR]
[SIZE=2][FONT=arial][COLOR=#333333]When we install Ubuntu or any of its flavours, such as Lubuntu we get an option to install third party software at the same time. This third party software includes certain proprietary audio and video codecs. It also includes the latest proprietary video drivers. These latest video drivers do not support very old video cards. Manufacturers are in the habit of dropping support for their hardware. I wonder if your display adapter ever had Linux support from the manufacturer.[/COLOR]
[/FONT][/SIZE]
So, you could try installing without ticking the box "Install third party software." You could also consider the Alternative installer method. It is more complicated because it requires us to make more decisions. I have never used the Alternative installer method. So, I cannot advise you on that.

I have used the Mini ISO or Network install method. That requires us to make lots of decisions. The Mini ISO will install Linux and we get to choose what desktop environment goes on top of it. The software packages are then downloaded over the Internet.

If we do not have too high expectations, then Linux can make very old hardware usable again.

Regards.

---

### Post by Yellow Pasque on 2014-12-17
Quick thoughts:
- If you can find a couple of cheap 256MB DDR200 modules, you could double the RAM to 512MB. That would help a bit. [http://www.oempcworld.com/OEMPCworld-com/256M-PC1600.html](http://www.oempcworld.com/OEMPCworld-com/256M-PC1600.html)
- I'd make sure to update the BIOS to the latest before removing Windows.

---

### Post by Yellow Pasque on 2014-12-17
I also noticed that with the latest BIOS, there is the possibility to use a much faster CPU. Considering that you can find dirt cheap used P4's for less than $10 after shipping, it seems like it would be worth a shot.
I have tto run out the door, but I have specific suggestions for the CPU upgrade later.

---

### Post by mörgæs on 2014-12-17
Yes, the computer needs some modifications before being useable. I once had a graphics card like yours and 'rage' is a good description of my feelings towards it.

More memory, faster processor, new graphics card... I suggest that you take a look at what a complete PC (used, but younger) costs on the second hand market before buying spare parts.

---

### Post by Yellow Pasque on 2014-12-17
> More memory, faster processor, new graphics card... I suggest that you take a look at what a complete PC (used, but younger) costs on the second hand market before buying spare parts.
Yeah, that's probably the best idea. Still, used CPU's are dirt cheap online and depending on where one lives, old RAM can be cheap.

If I had to upgrade this rig, the first thing I'd do is update the BIOS. Second, I would get a new CPU.
This is a 3GHz Northwood chip with Hyperthreading ($20): [http://www.amazon.com/gp/offer-listing/B001158P8C/ref=dp_olp_refurbished?ie=UTF8&condition=refurbished](http://www.amazon.com/gp/offer-listing/B001158P8C/ref=dp_olp_refurbished?ie=UTF8&condition=refurbished)
A cheaper option: 2.8GHz Northwood without Hyperthreading (< $10): [http://www.amazon.com/gp/offer-listing/B004573QZA/](http://www.amazon.com/gp/offer-listing/B004573QZA/)

The next thing I would do is scour any local places that sell cheap RAM for 2*512MB sticks of DDR-266 (those CPU's use a 133 MHz FSB clock unlike your current CPU, which uses 100 MHz FSB). I'm not sure how much RAM the mobo can take. I thought it was 512MB, but apparently, Dell says 1GB. You can get it online too: [http://www.oempcworld.com/OEMPCworld-com/512M-PC2100CL2.html](http://www.oempcworld.com/OEMPCworld-com/512M-PC2100CL2.html)

---

### Post by adam108 on 2014-12-17
Thanks all for the helpful advice.  I have another newer older computer that is missing a hard drive that I can possible get some of these parts out of.  I do not want to go to crazy with this old machine as it was a freebie, but would like to get some variant of linux on it to play with.  Thanks again!

---

### Post by mörgæs on 2014-12-18
Maybe it was better to move the hard disk from the old to the new(er) computer.

---

### Post by sudodus on 2014-12-18
> **mörgæs said:**
> Maybe it was better to move the hard disk from the old to the new(er) computer.

+1

At least if everything else is working in that new(er) computer :-)

-o-

But if you want to get the old computer running, because you enjoy doing it, please try an ultra-light linux distro, for example ***Wary Puppy***, ***Tiny Core*** (or the not yet officially released ***ToriOS***). You can also try to install a basic Ubuntu 14.04 LTS based system with ***OBI-9w*** and try different (light-weight) window managers and desktop environments.

---

