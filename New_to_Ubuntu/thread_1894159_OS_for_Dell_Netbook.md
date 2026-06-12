---
title: "OS for Dell Netbook?"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by joshswain123 on 2011-12-11
What would be the best version of Linux to put on a Dell Mini 1010?

---

### Post by llamabr on 2011-12-11
You could try ubuntu:

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

---

### Post by joshswain123 on 2011-12-11
There are so many issues listed that it doesn't seem worth it...

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Dell_Mini_10_.28Inspiron_1010.29](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Dell_Mini_10_.28Inspiron_1010.29)

---

### Post by PhilGil on 2011-12-11
> **joshswain123 said:**
> There are so many issues listed that it doesn't seem worth it...

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Dell_Mini_10_.28Inspiron_1010.29](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Dell_Mini_10_.28Inspiron_1010.29)

It does look grim, but that information is somewhat outdated as it applies to Ubuntu 10.04 (Lucid) and earlier. Perhaps things have improved in newer releases. It never hurts to make a live USB and give Ubuntu a try. Ubuntu's hardware support is usually pretty good, it's likely you'll have similar problems with most other Linux distros.

---

### Post by nmaster on 2011-12-12
apparently ubuntu 9.10 works well.  you could try jolicloud:
[http://www.mydellmini.com/forum/linux/24763-best-linux-dell-mini-1010-a.html](http://www.mydellmini.com/forum/linux/24763-best-linux-dell-mini-1010-a.html)

---

### Post by kseise on 2011-12-12
I am running Linux Mint Debian Edition on mine.  The Unity interface was the main reason I removed Ubuntu.  On a netbook, Unity is really difficult to work with.  Keep in mind, if you go with an older version of Ubuntu, ultimately you will be forced to move up to a Unity version when your chosen version reaches the end of its' life.  

Debian doesn't seem to like the touchpad on the mini 10v.  Mint Debian edition gives you the best of both worlds.  

As always, what works for me might not suit your needs.  Give each one a try for your self.  Report back with your ideas.

---

### Post by joshswain123 on 2011-12-12
I'm having trouble booting both Lubuntu (11.10) and Ubuntu Netbook Remix (11.10) onto my netbook. I get to the bootloader, and click on "try ubuntu without installing". The screen flashes, and then after a few moments it loads the ubuntu splash screen. It then flashes some sort of error message, too quickly to read, and then goes back to the bootloader (which now has some strange character replacements) and a terminal prompt below it...

Where could I find Debian? I'd like to try it instead for the netbook.

---

### Post by kseise on 2011-12-12
You get Debian at [http://www.debian.org/](http://www.debian.org/)  Be aware though, Ubuntu is built on Debian, so it might be largely familiar, but Ubuntu's developers put a lot of polish on the OS... right down to the installer process.  Debian does not like to be put onto a flash drive for the netbook installs but if you search for instructions, it is possible.  If you have a USB CD Rom, it would really help.

---

### Post by joshswain123 on 2011-12-12
I have a USB/IDE converter, so I'll see what I can piece together 0:]

---

### Post by PhilGil on 2011-12-12
> **kseise said:**
> You get Debian at [http://www.debian.org/](http://www.debian.org/)  Be aware though, Ubuntu is built on Debian, so it might be largely familiar, but Ubuntu's developers put a lot of polish on the OS... right down to the installer process.  Debian does not like to be put onto a flash drive for the netbook installs but if you search for instructions, it is possible.  If you have a USB CD Rom, it would really help.
Actually, it's easy to install Debian stable from a flash drive using [unetbootin]("http://unetbootin.sourceforge.net/") and a live image from [Debian Live]("http://live.debian.net/").

If you have a Linux machine handy you should be able to find unetbootin it in the software repository. If not, there are Windows and Linux builds available on the website. Unetbootin will also work with the images on the Debian site, but I think they're install only, you won't be able to try them live.

1) Download the Debian Squeeze live iso from the Debian Live website. Be sure to pick the correct architecture (probably i386 for a netbook)
2) Use unetbootin to install the image to your flash drive
3) Boot the netbook with the flash drive and you'll have the option of running a live Debian system or installing Debian

The Debian installer is much improved. It's not as pretty or as idiot-proof as the Ubuntu installer, but a reasonably computer-savvy user should be able to do the install.

---

### Post by mastablasta on 2011-12-13
why would debian stabel work better if Ubutnu 10.04 doesn't work so well? 
 
The best (easiest) way would indeed be to use Linux Mint Debian Edition as it uses more recent kernels so things maywork better due to newer drivers. Ofcourse there is always debian testing and unstable, but for someone that wants the system to work on and not fix it constantly other options are better.
 
New Ubuntu (or it's derivatives) might also work.

---

### Post by asifnaz on 2011-12-13
I suggest you Debian 6 . It is very stable and light

---

### Post by PhilGil on 2011-12-13
> **mastablasta said:**
> why would debian stabel work better if Ubutnu 10.04 doesn't work so well? 
The OP has a netbook that may not be well supported by Ubuntu. The OP may need to try several distros/version to find one that supports his/her hardware.

I don't come here to slam Ubuntu, but my experience has been that Ubuntu suffers from more hardware support regressions than Debian. The upgrade from Ubuntu 9.10 to 10.04 was especially painful, with two of my three computers not working properly after the upgrade. Debian Squeeze, however, worked fine on all three machines.

---

### Post by mastablasta on 2011-12-13
> **PhilGil said:**
> The OP has a netbook that may not be well supported by Ubuntu. The OP may need to try several distros/version to find one that supports his/her hardware.
 
I don't come here to slam Ubuntu, but my experience has been that Ubuntu suffers from more hardware support regressions than Debian. The upgrade from Ubuntu 9.10 to 10.04 was especially painful, with two of my three computers not working properly after the upgrade. Debian Squeeze, however, worked fine on all three machines.
 
sorry, i didn't know it's an older maschine. you are quite right that Debian supports more in that way. but for newer hardware Debian stable might not support it. Ubuntu has newer kernel and hence includes newer drivers.
 
i too switched to Debian Stable based Chrunchbang for this same reason. better support for a bit older hardware.

---

### Post by intruderukr on 2011-12-13
I am dual-booting with Oneric on my Dell mini, had it set up for a few months, so far no problems...

---

### Post by joshswain123 on 2011-12-13
I tried booting Lubuntu (Oneric Ocelot 11.10) on my netbook (Dell Mini 1010) using the same LiveCD as I used for my desktop (so I know the disk works fine). But when I boot it up, it loads the menu screen (try before you install, etc) and if I click either try or install, it goes to the splash screen, loads for a while, and then flashes an error message (I'm not sure what it says, it's too quick to read). It then gave me a terminal prompt. I thought this was the same bug I ran into with my desktop (lxdm not starting), but in trying to fix that, the following happened:

```
ubuntu@ubuntu:~$ sudo start lxdm
lxdm start/running, process 3064
```

---

### Post by joshswain123 on 2011-12-14
I'm going to try Lubuntu 10.10 and see if that does any better...
If not, I might try Debian?

---

### Post by joshswain123 on 2011-12-14
There's definitely a blank CD-R in the drive, and I'm pretty sure the computer even thinks so, considering it opened an autorun menu when I put in the disk...

---

### Post by joshswain123 on 2011-12-14
This is as good as I could get for a picture of the error when bootin lubuntu 11.10 on the netbook. From there it just goes to a terminal prompt

---

### Post by mikewhatever on 2011-12-14
> **PhilGil said:**
> The OP has a netbook that may not be well supported by Ubuntu. The OP may need to try several distros/version to find one that supports his/her hardware.

I don't come here to slam Ubuntu, but my experience has been that Ubuntu suffers from more hardware support regressions than Debian. The upgrade from Ubuntu 9.10 to 10.04 was especially painful, with two of my three computers not working properly after the upgrade. Debian Squeeze, however, worked fine on all three machines.

GMA500 is not a regression. It's been notorious for the lack of Linux support, a licensing mess and Intel's indifference. I doubt that switching to any version of Debian will help.

The Poulsbo wiki page has some very informative articles at the bottom.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by mikewhatever on 2011-12-14
Hey joshswain123, I'd recommend Ubuntu 10.04. That's what I use on the mini 10, actually, the Netbook Remix. You'll have to add the PPA and install the driver, etc, as advised in the Poulsbo Wiki. It works decently, despite the issues, but I've had a lot of time to get used to them.

What you've experienced with 11.10 is a known problem, but if you have to use it, try the custom made iso for GMA500.

[http://ubuntuforums.org/showpost.php?p=11356431&postcount=4605](http://ubuntuforums.org/showpost.php?p=11356431&postcount=4605)

---

