---
title: "Feeling uneasy with Microsoft and want to put Ubuntu on my machine"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by conure on 2013-06-07
Hello,

I posted yesterday but didn't really get a response to my problem.

Basically I am unable to install Ubuntu on "bare metal" due to problems I don't yet understand. Eventually I'll work them out, but for now I just want rid of Windows. The way the XBox One (and Kinect) is being developed, the constant requests for Bing etc is making me a bit uneasy with regards to my privacy. I don't want to feel like I'm constantly being tracked (recently I tried to put an expensive copy of Microsoft Office 2013 on my second system having removed it from the first, and couldn't do it!)

So anyway, enough about the ranting. If I install Ubuntu from Windows which is the only way it works for me, then reboot into Ubuntu, is ANY Windows software running, or is the Ubuntu installation which I've performed from Windows a pure Ubuntu installation so Windows in no way runs on the machine?

Apologies if this sounds newbie and paranoid but I'm really growing tired of having the boundaries of privacy and advertising pushed!

---

### Post by Impavidus on 2013-06-07
Even if you install Ubuntu from windows, meaning wubi, then Ubuntu will still run without any windows software being active. Keep in mind that wubi doesn't work on windows 8.

---

### Post by BBQdave on 2013-06-07
> **conure said:**
> Basically I am unable to install Ubuntu on "bare metal" due to problems I don't yet understand.

You may have already tried this: if your computer came with Windows 7, try the live iso of Ubuntu Unity 12.04LTS. Hopefully it will boot Ubuntu and allow you to test your hardware for compatabiliy. I recommend 12.04, because after a year, it is stable, fast and smooth :)

If you computer came with Windows 8, Secure Boot may be causing problems with an Ubuntu install. The short answer on Secure Boot - hardware and Linux, is disable Secure Boot to install Linux.

There is much discussion about Secure Boot, for my thoughts on this, I believe it is a gimmick and attempt at vendor lock in by Microsoft. It is not apparent the value to security that is Microsoft *Secure Boot*.

---

### Post by fantab on 2013-06-07
> **conure said:**
> Hello,

I posted yesterday but didn't really get a response to my problem.

Basically I am unable to install Ubuntu on "bare metal" due to problems I don't yet understand. Eventually I'll work them out, but for now I just want rid of Windows. The way the XBox One (and Kinect) is being developed, the constant requests for Bing etc is making me a bit uneasy with regards to my privacy. I don't want to feel like I'm constantly being tracked (recently I tried to put an expensive copy of Microsoft Office 2013 on my second system having removed it from the first, and couldn't do it!)

So anyway, enough about the ranting. If I install Ubuntu from Windows which is the only way it works for me, then reboot into Ubuntu, is ANY Windows software running, or is the Ubuntu installation which I've performed from Windows a pure Ubuntu installation so Windows in no way runs on the machine?

Apologies if this sounds newbie and paranoid but I'm really growing tired of having the boundaries of privacy and advertising pushed!

What machine do you have? What are its specifications? 
It is recommended that you do a true dual boot rather than go WUBI way. WUBI may be phased out, its already not included in the latest version of Ubuntu, which is 13.04.

---

### Post by conure on 2013-06-07
> **fantab said:**
> What machine do you have? What are its specifications? 
It is recommended that you do a true dual boot rather than go WUBI way. WUBI may be phased out, its already not included in the latest version of Ubuntu, which is 13.04.

Thank you all for replies. There are a couple of issues stopping me from doing a full installation of Ubuntu - the first is that whenever I install nvidia-current, my screen locks to 640-480 and there's nothing I can do to change that! The default driver which comes with Ubuntu makes things feel a bit sluggish in comparison to Windows.

the other problem is the one posted in my previous thread, but nobody responded so I presumed nobody really knew what my problem was! I have been completely unable to install Ubuntu from USB. I'll get the link and post it here.

My Machine specs are:

core i5 2500k
GTX 660ti 2gb
8GB Ram @ 1333mhz
OCZ 128GB SSD
24" dell monitor which is quite old now

---

### Post by conure on 2013-06-07
Here is an image of my problem when I try to install from USB:

[http://img153.imageshack.us/img153/7264/ubuntu2.png](http://img153.imageshack.us/img153/7264/ubuntu2.png)

---

### Post by fantab on 2013-06-08
What version of Windows do you have?

You USB seems to be corrupt. Have you tried another USB?
It could also be a case for 'bad download' or 'bad burn'... Check these first.

---

### Post by grahammechanical on 2013-06-08
It is my understanding that when we do a Wubi install then Ubuntu is running just like another Windows application. That means that Windows itself is running. I may be wrong but if you do not want Windows or any windows application to be running, then you need to install Ubuntu to the hard disk and boot into it. Then only Ubuntu and its applications will be running.

Regards.

---

### Post by 3rdalbum on 2013-06-08
> **grahammechanical said:**
> It is my understanding that when we do a Wubi install then Ubuntu is running just like another Windows application. That means that Windows itself is running. I may be wrong but if you do not want Windows or any windows application to be running, then you need to install Ubuntu to the hard disk and boot into it. Then only Ubuntu and its applications will be running.

Your understanding is not correct. Installing Ubuntu with Wubi requires Windows for the installation step only, but on booting Ubuntu there is absolutely no Microsoft code running. You can even remove everything except the root.disk and the Windows bootloader and Ubuntu can still boot.

To the original poster: A Wubi install of Ubuntu will not sidestep the problem you have with nvidia-current. Do a full install of Ubuntu, then you can either try the latest version of Ubuntu if you haven't already, or try installing the latest Nvidia driver manually or via a PPA.

---

### Post by TNFrank on 2013-06-08
Both used HP/Compaq laptops I recently bought came with Windows 7 on them.  I used wubi to install Ubuntu inside Windows then use the Startup Disk Creator with Ubuntu to make a start up USB drive to boot to so I could over write Windows and install Ubuntu.  Just make sure you get the right Ubuntu(32 or 64 bit) that's compatable with your machine. Download it to the Ubuntu desktop, go to the Startup Disk Creator and use it to put it on your USB drive. Then make sure your computer is going to look at the USB drives first on start up and boot to it and follow the install instructions.

---

### Post by monkeybrain2012 on 2013-06-08
> **Impavidus said:**
> Even if you install Ubuntu from windows, meaning wubi, then Ubuntu will still run without any windows software being active. Keep in mind that wubi doesn't work on windows 8.

Why do you want to run Ubuntu inside Windows? OP wants to get rid of Windows. WUBI is for demo anyway and it is buggy and dependent on Windows.

---

### Post by monkeybrain2012 on 2013-06-08
> **TNFrank said:**
> Both used HP/Compaq laptops I recently bought came with Windows 7 on them.  I used wubi to install Ubuntu inside Windows then use the Startup Disk Creator with Ubuntu to make a start up USB drive to boot to so I could over write Windows and install Ubuntu.  Just make sure you get the right Ubuntu(32 or 64 bit) that's compatable with your machine. Download it to the Ubuntu desktop, go to the Startup Disk Creator and use it to put it on your USB drive. Then make sure your computer is going to look at the USB drives first on start up and boot to it and follow the install instructions.

That seems to be unnecessarily round about, OP can create a live usb for Ubuntu in Windows using unetbootin or [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Then boot into a Ubuntu live session, test the hardware a bit, if it works ok then overwrite Windows and install Ubuntu.

@OP, 

As someone said, the resolution with the Nvidia card is driver related. If everything works, you can choose a different driver from ppas such as x-swat or xorg-edgers.

---

### Post by oldfred on 2013-06-08
I have an older nVidia card and on every boot of live installer whether CD or flash and first boot after install, I have to use nomodeset.
But I have had few issues installing the proprietary nVidia driver that Ubuntu offers. With 12.10 I did have to install kernel headers first to get it to correctly install the nVidia driver.

Since you have an i5, do you have dual graphics? Or can turn one or the other off in UEFI/BIOS? Is system set up in UEFI mode or BIOS boot mode?

---

