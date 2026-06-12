---
title: "Boot Loader issues"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by jchap1590 on 2012-06-23
I've been working with command line for a couple of years now and fell that I am ready for my first Linux build! ubuntu seemed like the perfect place to start, however, I am having issues getting the boot loader to start the installer and can't figure out why. I've tried multiple methods to load the ubuntu installer at boot time; USB with the .iso burned directly to it (both x86 and 64bit), USB using the 'Universal USB Installer' utility as directed on this site to create a bootable USB device, a DVD+RW with the .iso burned directly to it, and finally the windows installer run from my desktop (which produced a 'nonetype' object error, twice). This is very frustrating to not even be able to get a start on my first build. I've loaded other install discs at boot with no issue and can't understand what I'm doing wrong now. Also, I want to install Linux on a separate physical drive than the one my 'usual' OS boots from, so please include any recommendations for that setup in your response.

HP BIOS version 7.04
Windows 7 Home Premium 64-bit *existing OS

Method 1: USB device (16GB) with .ISO image burned directly
Method 2: USB device (16GB) setup via 'Universal USB Installer 1.9.0.2'
Method 3: Windows Installer 'wubi.exe' (resulted in 'nonetype' object error)
Method 4: DVD+RW disc with .ISO image burned directly

Thanks in advance for any responses.

---

### Post by jtarin on 2012-06-23
Where did you download your image from? Did you MD5Checksum it? Are you formatting the medium before burning? If so what filesystem?

---

### Post by HeroOfCanton on 2012-06-24
You can also try [pen drive linux]("http://www.pendrivelinux.com/"). Although I agree you should take a good look at that iso. Maybe download it again just in case.

If that doesn't work I'd look for crazy BIOS settings. My only HP experience is a Proliant server which is certainly different from the desktop BIOS, but it does have a "boot to ________ operating system" option.

---

### Post by black veils on 2012-06-24
go to post #8 on this thread:

[http://ubuntuforums.org/showthread.php?t=2007631]("http://ubuntuforums.org/showthread.php?t=2007631")

---

### Post by NikTh on 2012-06-24
Hi , 
try unetbootin (as @black veils suggest) . Download it from here --> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Download iso image from here --> [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/) , Desktop CD 64bit version

Also check the usb flash , if you have another , try it instead. 
Thanks.

---

