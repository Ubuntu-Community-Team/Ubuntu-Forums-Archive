---
title: "NO way of intall any DISTRO differents PC's"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by Tuexnovia on 2013-03-12
Well most of us we are having the same problem no idea why...

I've  touched everything in bios and keeps going wrong, I've touched ASCI  SATA. I've put as first boot in bios my HDD and then in loading screen  when I turn on the computer on I press F12 to chose from where I want to  boot... I chose USB bla bla...

Everything works from my USB, windows, hiren's... bla bla and even the linux isos, but then same problem.

Busybox

(initramfs) Unable to find a medium containing a live file system



Third  Computer that it happen to me the same I touched as I said everything  in bios but there is not way to make it run, in 3 differents computers c'mon guys... and besides a lot of people that talks about the same, change the USB port touch this in BIOS do this do that. but for me there is no way... WHY??


I think I'm gonna give up.

---

### Post by carl4926 on 2013-03-12
Can you or can't you boot to a Live session of Ubuntu?

---

### Post by Cheesemill on 2013-03-12
What method are you using to create your bootable USB's?

---

### Post by mastablasta on 2013-03-12
It says what you need to know:
(initramfs) Unable to find a medium containing a live file system


what is on USB disk? .iso file?
did you use something like unetbootin or linuxliveUSB?
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

Did you check the md5sum after download? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Tuexnovia on 2013-03-12
> **carl4926 said:**
> Can you or can't you boot to a Live session of Ubuntu?
well in several distros which are...

lubuntu-12.10-desktop-amd64
lubuntu-12.10-desktop-i386
ubuntu-12.10-desktop-amd64
in just one of them I can do live session... lubuntu-12.10-desktop-i386 so that is 32bits right? it should work in every singler PC...

> **Cheesemill said:**
> What method are you using to create your bootable USB's?
Yumi my friend I've put win7, those ISOS, and Hiren's... Now I'm gonna just gonna format the USB Kingston 16Gb and do it again with yumi, this time I'll just install 4 linux isos.
Lubuntu 32 and 64 -2 ISOS-
Ubuntu 32 and 64 -2 ISOS-

> **mastablasta said:**
> It says what you need to know:
(initramfs) Unable to find a medium containing a live file system


what is on USB disk? .iso file?
did you use something like unetbootin or linuxliveUSB?
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

Did you check the md5sum after download? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[COLOR=#b22222]EDIT: I've checked md5sum one by one, and they are ok...[/COLOR] (I've used yumi my friend... and in diferents USB and computers) KHAOS is the word...



Guys I really feel bad  xDDD the most important thing I want to do is to install Ubuntu in my AMD Athlon  (tm) x2 Dual core 4200+ 2.21 [COLOR=#b22222](which it had to be... ubuntu-12.10-desktop-amd64 right?)[/COLOR]
and I can't guys... is telling me always the same I have mess with several bios of several computers... Well I'm gonna do it again and let's see.. I'll keep you inform and if you got any idea or tip. I'd like to hear it...

---

### Post by Tuexnovia on 2013-03-12
Have a look what I found (is it correct the expression? always good moments to learn about everything)

While I was trying to install several ISOS in several pc's in the screen in which is usually loading Lubuntu/Ubuntu
I've press Alt+Tab and I've seen the console writing this...

/init: line 7: can't open /dev/sr0: No medium found
/init: line 7: can't open /dev/sr0: No medium found
/init: line 7: can't open /dev/sr0: No medium found


Infinite times...


I need help pls....

---

### Post by Cheesemill on 2013-03-12
I've never used Yumi so I don't have any experience with it.

If you are using Windows to create your USB then try using [Win32 Disk Imager]("http://sourceforge.net/projects/win32diskimager/") instead.
It's basically a Windows version of dd with a GUI so it should be the most reliable way of creating a bootable USB. Unlike all of the other methods your USB will be using the bootloader from the iso file, instead of syslinux or the grub chainloading method which most of the other tools use.

---

### Post by Tuexnovia on 2013-03-12
> **Cheesemill said:**
> I've never used Yumi so I don't have any experience with it.

If you are using Windows to create your USB then try using [Win32 Disk Imager]("http://sourceforge.net/projects/win32diskimager/") instead.
It's basically a Windows version of dd with a GUI so it should be the most reliable way of creating a bootable USB. Unlike all of the other methods your USB will be using the bootloader from the iso file, instead of syslinux or the grub chainloading method which most of the other tools use.

Wow I'll try it right now. and thanks for that information, I'll tell you soon how it has work...

---

### Post by Tuexnovia on 2013-03-13
well guys I've finally finish my installation LOL, I came at 00:30 and I've been trying until 9:00 in the morning LOL I woke up at 4:00 and still the going xD
well I've installed Ubuntu tried kde, [COLOR=#ff0000]but ubuntu is gnome or unity?[/COLOR] and now I'm just studing the distros and how to install them and so on... to get use to it.
well finally I could intall UBUNTU, just because I used linuxliveUSB...

so I'm thinking on don't put many distros and bottable things in one USB... my conclusion.

---

### Post by TK999 on 2013-03-13
In response to your desktop environment question: Ubuntu 11.04 and up runs Unity by default, and its fallback view is based on GNOME 2.0. Unity was forked from GNOME ([https://www.gnome.org](https://www.gnome.org)) in 2010.

---

