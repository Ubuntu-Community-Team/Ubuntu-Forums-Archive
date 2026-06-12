---
title: "Lubuntu 12.10 install fails"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by StumbleineMT on 2013-02-21
Hello all,

I am a newbie to all things Linux, so figured I'd best start here!

I have spent the last three days searching forums, but not yet found anything like the issue that I am currently experiencing.

I am attempting to install Lubuntu 12.10 on a Toshiba Satellite L30-115 (Celeron M). I have checked the MD5SUM and they are perfect, so I then installed the OS to USB and the demo is great, I can load anything just fine, but the install fails!

When the USB has booted, I can select the option to install to HDD (The CD icon on the desktop won't work), and the first page loads so you may choose a language. Once I click on 'Continue' however, the screen goes black, and I am taken back to the live session. 

If anyone has any advice to share, I would be most grateful. :)

---

### Post by blackbird34 on 2013-02-21
Have you tried burning a live C instead of a live USB stick?

---

### Post by TheFu on 2013-02-21
Before installing, try it with a live-CD.  I think you did that with the USB, but I'm not 100% certain.  How does everything work? Good?  Networking, audio, video?  This is before you try to install.
**Why? ** It provides a good hint as to whether your system is supported out-of-the-box or if you'll need to do some extra work during/after install.

With all that said, 12.10 is not known as an extremely stable release. Someone new to Linux should start with an LTS release, like 12.04 unless there is real requirement to use something newer. An example where 12.10 is needed instead of 12.04 is if you need SecureBoot support.

For any laptop, google "ubuntu install {vendor-model-number}" to see if someone has figured out the issue, if any exist.  So, "ubuntu install L30-115" is the query you should use. Seems there are special  audio drivers needed.

There is a 12.04 Lubuntu too.  BTW, I run LXDE myself. Excellent choice.

There is a troubleshooter for installation black screens ... let me google for it.  Found this: [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it) , which is not what I was searching for.

When you are at the boot selection screen, isn't there an option at the bottom of the screen for alternate installs?  "Something Else?"
Sorry, I don't have the Lubuntu ISO handy now, so I'm looking at a 12.04 Desktop install.

Without seeing the logged errors, it is next to impossible to help.

---

### Post by MoebusNet on 2013-02-21
I don't have personal experience with this notebook, but from what I read it is old enough that 12.04 may support your hardware better than 12.10. It may also be the case that you need the 32-bit instead of the 64-bit version, if the processor does not support 64-bit OS's.

Lubuntu 12.04 & Xubuntu 12.04 are both worth trying out; I use Xubuntu 12.04 on my 2002 Dell Latitude D800 notebook (1.4 Ghz Pentium-M).

You may need to use *nomodeset* to run the VESA driver for your video card until you can install the ATI proprietary driver. I have read that ATI does not do a good job of supporting some of their older cards under Linux; that might be worth looking into.

---

### Post by grahammechanical on 2013-02-21
> It may also be the case that you need the 32-bit instead of the 64-bit version, if the processor does not support 64-bit OS's.

I agree with that but I would like to add that if the CPU does not support what is call PAE  (Physical Address Extension), then you will need a non-pae kernel version of Ubuntu.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

If you need a non-pae kernel version of Ubuntu then you cannot use 12.10 even Lubuntu 12.10.

[http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html](http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html)

> Further more, with 12.10, Xubuntu and Lubuntu no longer come with a  non-PAE Linux Kernel, so by default, you can't install any Ubuntu 12.10  flavour on computers using CPUs that lack PAE support (such as Intel  Pentium M).

Regards.

---

### Post by mörgæs on 2013-02-21
Try the alternate ISO:
[http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/)

---

### Post by MoebusNet on 2013-02-21
> **grahammechanical said:**
> I agree with that but I would like to add that if the CPU does not support what is call PAE  (Physical Address Extension), then you will need a non-pae kernel version of Ubuntu.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

If you need a non-pae kernel version of Ubuntu then you cannot use 12.10 even Lubuntu 12.10.

[http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html](http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html)



Regards.

It looks as though either Xubuntu 12.04 LTS or Lubuntu 12.04 in the 32-bit version will be what the OP needs because his Celeron M 380 will not support the PAE-required kernels of 12.10 and will not support 64-bit OS's.

---

### Post by TheFu on 2013-02-21
> **grahammechanical said:**
> If you need a non-pae kernel version of Ubuntu then you cannot use 12.10 even Lubuntu 12.10.


I'd think this is the most likely issue, PAE.
Good catch.  I know that PAE kernels are included on 12.04, but I thought that non-PAE kernels were not included at that time. Didn't look it up, but if true, then switching from Ubuntu (or any derivative like Mint) to pure Debian would be my recommendation.  Definitely stay with APT.

Now I'm curious.  [http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html) explains.

---

### Post by mörgæs on 2013-02-21
No, PAE is not a problem here. A successful live boot proves that the CPU supports PAE.

---

### Post by blackbird34 on 2013-02-21
+1

---

