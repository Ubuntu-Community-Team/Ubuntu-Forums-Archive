---
title: "How do I stop language prompt on usb install?"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by Deaner13 on 2013-03-29
Hey All,

I'm working on creating a light-weight installation of Lubuntu on a USB key so that I can plug into any computer and boot to my OS. I used a program called Universal USB installer to install Lubuntu onto the USB drive, but everytime I boot to it I get prompted for which language I want to use and asked if I want to "Boot from USB Key, Install to the HDD...." like I'm using a live CD. 

Is there a way to by-pass both of these? Or at least by-pass the language selection portion of this?

Thanks for your help!

---

### Post by MythicManiac on 2013-03-29
I think you installed the version to your USB which you are supposed to use to install the actual OS, instead of installing the "regular" version of the OS to the USB.

---

### Post by Deaner13 on 2013-03-29
That could be true, I have this menacing looking "Install Lubuntu 12.10" icon on the desktop... 

I downloaded the file directly from the Lubuntu website (or Ubuntu, I can't remember) do you know where the correct source might be?

---

### Post by arpanaut on 2013-03-29
Take a look at the information in this post:
[http://ubuntuforums.org/showthread.php?t=2128405&p=12570429&viewfull=1#post12570429](http://ubuntuforums.org/showthread.php?t=2128405&p=12570429&viewfull=1#post12570429)

It should give you the way to get what you want.

---

### Post by C.S.Cameron on 2013-03-29
Go to the root folder of your Live USB
    Enter the syslinux directory
    Make the syslinux.cfg file writeable

  For a **Live** install replace the contents of the file syslinux.cfg with:

    ```
default live
    label live
      say Booting an Ubuntu Live session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash noprompt --

```

or if you have a **Persistent** install:

```
default Persistent
label Persistent
  say Booting an Ubuntu Persistent session...
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```


Edit:
Above is for a Startup Disk Creator install.
For a UNetbootin or Universal install you will need to look elsewhere for syslinux.cfg

---

### Post by squakie on 2013-03-29
I would just use unetbootin and build a USB installation with persistence (to remember things from one run to the next).  I also would suspect you have the installation media copied to your USB, not an actual install to the USB.  Unetbootin makes this process easy.

---

### Post by amjjawad on 2013-03-29
> **Deaner13 said:**
> Hey All,

I'm working on creating a light-weight installation of Lubuntu on a USB key so that I can plug into any computer and boot to my OS. I used a program called Universal USB installer to install Lubuntu onto the USB drive, but everytime I boot to it I get prompted for which language I want to use and asked if I want to "Boot from USB Key, Install to the HDD...." like I'm using a live CD. 

Is there a way to by-pass both of these? Or at least by-pass the language selection portion of this?

Thanks for your help!

You are not installing Lubuntu on your USB, you are simply creating a LiveUSB :)
What are you seeing is the installer which will ask for the language, etc.


To install Lubuntu on USB - [https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu#Install_Lubuntu_on_4GB_USB_Drive](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu#Install_Lubuntu_on_4GB_USB_Drive)

---

### Post by C.S.Cameron on 2013-03-30
> **squakie said:**
> I would just use unetbootin and build a USB installation with persistence (to remember things from one run to the next).  I also would suspect you have the installation media copied to your USB, not an actual install to the USB.  Unetbootin makes this process easy.

The OP asked how to get rid of the Language/try/install pages. An UNetbootin install still has a try/install/memtest page.

To remove these from an UNetbootin install edit syslinux.cfg as above in post 5. 
With UNetbootin install the syslinux.cfg file is found in the root of the USB.

---

### Post by squakie on 2013-03-30
> **C.S.Cameron said:**
> The OP asked how to get rid of the Language/try/install pages. An UNetbootin install still has a try/install/memtest page.

To remove these from an UNetbootin install edit syslinux.cfg as above in post 5. 
With UNetbootin install the syslinux.cfg file is found in the root of the USB.

Got confused there - I was thinking about when I created a running USB installation with persistence. Indeed unetbootin only creates a bootable installation media, and hence you're right - the language selection would be there because it would just be an installation media, not a running install.  Sorry about that!  I would think it would be much easier for the OP to just do an install to the flash drive as I never had the language selection screen when I've done that - no file editing needed.

---

### Post by C.S.Cameron on 2013-04-01
Removing Try/Install reduces boot time by about a half, a Full install reduces boot time by about a half again.

---

### Post by Deaner13 on 2013-04-01
Thank you all for your replies. I wasn't able to access this page until now, so I will be trying a few of the things listed here.

What I did do over the weekend in a different situation was simply install from the "Live CD" USB to a different USB key. That solved the issue, but I might as well have fun trying to tinker the other one to a working installation too. 

I'll get back to you guys in a bit!

---

### Post by squakie on 2013-04-03
glad that worked for you.  the install is what others and myself were suggesting as we knew there would be no language prompts, etc., once you did that.  multiple ways to do that install - be USB to the USB as you did, CD to USB, etc.  No file edits, etc, needed.

---

