---
title: "Distro for old hardware?"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by braluca on 2013-05-20
Hello,
I would like to install linux on my old notebook:
[TABLE="class: tborder, width: 100%, align: center"]
[TR]
[TD="class: alt1, bgcolor: #E7E9EB"]- Intel Pentium 4 
- CPU 2.4 GHz
- Cache 512 kB
- Chipset SiS 645DX
- Memory510 MB
- Mobility Radeon M9/GL (Omega Plutonium X.1.1.18a)
- Hard disk 27GB NTFS
- CD-ROM DVD
- Windows XP installed[/TD]
[/TR]
[/TABLE]
I have understood that best distro for me should be lubuntu due to oldness of my pc.
Before proceeding I would like to be sure that I can use all graphical potentiality of my graphic adapter.
Is it sure that with this Mobility Radeon M9/GL all will work?
Should I found drivers before (not possible to find at all also in AMD site)?
Should be then be able to play CD and DVD?
Must be done some operation before install linux or just put CD in reader and turn on notebook?
Sorry for silly questions and thanks in advance

---

### Post by lykwydchykyn on 2013-05-20
Lubuntu or Xubuntu would be best, as far as the Ubuntu family goes.  BodhiLinux might be worth a look if you don't like the desktop interface of either of the others.

ATI/AMD graphics are kind of a gamble;  you might get better performance from the built-in free drivers, or the proprietary might do better.  You'll just have to try both and see.  Just install them from the hardware drivers tool in the menu, don't download anything from AMD.  That'll just complicate your setup.

Before you install, you'll want to backup anything important on the system, because things can always go bad and destroy whatever's on there.  It happens now and then.

---

### Post by sudodus on 2013-05-20
I just want to add, that you can get a very good feeling of the different flavours of Ubuntu without touching the hard disk drive. 'Try' Lubuntu and Xubuntu live booted from the CD/DVD/USB drive before installing anything to the hard disk drive. Normally the built in drivers will work with old hardware. It might not give you all the advanced graphics effects, but it will do what it can do fast, probably faster than Windows.

---

### Post by Lars Noodén on 2013-05-20
Try the distros from the live cd or usb stick as suggested.  You can also go lighter than LXDE by skipping the desktop environment entirely and just running a window manager instead.  Openbox is popular, but Oroborus is probably the lightest of all.

---

### Post by braluca on 2013-05-20
thanks
I shall try with lubuntu 13.04 desktop i386 
I am downloading iso for testing without touching the old Windows.
Hope to join your family

---

### Post by sudodus on 2013-05-20
Welcome :-)

By the way, the simple Openbox window manager, that Lars mentioned comes with Lubuntu. At the login screen you can select it.

The first time you might think it does not work. It's only a grey screen! But right-click with the mouse, and you get a small menu, where you can select a terminal window, a web browser (and to exit). You can run all programs from the terminal window. And there you go without the eye-candy that makes an old computer slow :-)

---

### Post by Mark Phelps on 2013-05-20
> **braluca said:**
> ... Before proceeding I would like to be sure that I can use all graphical potentiality of my graphic adapter. 

Then ... spare yourself major disappointment and don't bother.  With an ATI chipset that old, even the open-source drivers might not work.  There have not been any proprietry drivers that would work for several years.

---

### Post by braluca on 2013-05-21
> **Mark Phelps said:**
> Then ... spare yourself major disappointment and don't bother.  With an ATI chipset that old, even the open-source drivers might not work.  There have not been any proprietry drivers that would work for several years.
I have not understood, do you mean that it is better to avoid at all the installation of Lubuntu and stay with my Win XP?

---

### Post by nerdtron on 2013-05-21
Your ATI chipset is very old. We may not be sure it will be supported so don't expect to much from it. Still, you should try Live mode first and see if it will work. It won't hurt since you won't be touching your hard drive.

---

### Post by nerdtron on 2013-05-21
> Should I found drivers before (not possible to find at all also in AMD site)?
Linux doesn't work this way. Just hope that the drivers included in the default Lubuntu will work for your card.
> Should be then be able to play CD and DVD?
Yes. If it is a Music CD, or MP3 files, you need to install extra codecs to play them. Or just install VLC and you'll be able to play music, videos, pretty much anything that plays on VLC on XP will play on VLC on Lubuntu.
> Must be done some operation before install linux or just put CD in reader and turn on notebook?
Depends on your notebook. But to be sure, set the first boot priority as the CDROM. When you turn on the notebook, press DEL key or F12 or any key that would give access to the BIOS, use you arrow keys to navigate and look for the BOOT sequence or Boot Priority or something along those lines (every computer has a different BIOS so exact steps can't be given) and set the CDROM as the first choice to boot.
> Sorry for silly questions and thanks in advance
No silly questions here. It's OK to clear up things before trying something new.
Goodluck and have fun!

---

### Post by mastablasta on 2013-05-21
m9 is marked here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

as having good 3D support with opensource driver. so it's worth a shot i would say. just don't expect much. :-D

you might need nomodeset boot option to boot the OS: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
if you do and if oyu decide to install the OS post back and we will help you make it permanent.

---

### Post by braluca on 2013-05-24
> **mastablasta said:**
> m9 is marked here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

as having good 3D support with opensource driver. so it's worth a shot i would say. just don't expect much. :-D

you might need nomodeset boot option to boot the OS: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
if you do and if oyu decide to install the OS post back and we will help you make it permanent.
Hi,
thanks a lot.
I used live cd and I am satisfied.
I did not use nomodeset boot option.
At this moment hard disk has 2 partition under WinXP, I hope when Lubuntu installed to have only one.
I am ready to proceed to instal Lubuntu on HD and erase WinXp.
Some particular tips? or only using live cd choose option permanet install?

---

### Post by braluca on 2013-05-25
Lubuntu installed
WinXP erased

Very fast boot now....
thanks to everybody for support

---

### Post by sudodus on 2013-05-25
Congratulations :KS

Please edit the first post in the thread, go advanced and change the prefix to SOLVED :-)

---

