---
title: "Install worked great... but which USB option is my drive in boot menu?"
date: 2016-04-11
forum: New to Ubuntu
---

### Post by tinpanalley on 2016-04-11
Everything went fine from burning my ISO to installing Ubuntu via the tutorials online to my USB3.0, 64GB flash drive. But when I boot, and go into boot drive selection I get 
- USB-ZIP
- USB-FDD
- USB-HDD
- USB-another one here that I don't remember. I want to say "USB-CD"

I've tried them all with the flash drive plugged into motherboard USB ports (I mean not add-on PCIs or faceplate readers) and it's like the drive isn't there? It definitely installed correctly and has the drive structure it should have. 

Any thoughts? Thank you!!

---

### Post by howefield on 2016-04-11
You'd normally expect it to be the USB-HDD option.

If you are plugging in to a USB3 port, try a USB2 one instead.

Assuming you have done the basics, ie, checksum the iso and have burned the image correctly (not simply copied the iso to the disk).

---

### Post by tinpanalley on 2016-04-11
> **howefield said:**
> You'd normally expect it to be the USB-HDD option.
If you are plugging in to a USB3 port, try a USB2 one instead.
Well, it HAD been in a 2.0 port but maybe just not the right one. I got it to work. Might be strange for some people to believe but this is the first time I've ever run Linux on a computer (not counting Android bootloaders). 
Just some quick questions if someone can help me out...
1. How similar is it going to run from there as opposed to from an internal HDD? Night and day different?
2. Does my internal hardware ever need new drivers, BIOS, firmware and if so, will those things install to my windows c drive?
3. I know one could try distros forever and it's impossible to talk about one or another but is there at least a list somewhere divided by general UI style? This stock Ubuntu theme is a little too Apple for my tastes.
And completely totally unrelated...I was hoping rhythmbox was going to be an actual program but it appears to just be baked into the OS so there's no menu with music library, settings, etc? Or was I just not able to bring it up.

---

### Post by grahammechanical on 2016-04-11
I used to do all my installs from the ISO image burned to a DVD disc. Then I tried using a USB memory stick and I discovered that on my Motherboard BIOS (not UEFI) settings utility I had to go to the boot section and select which drive to boot from as the BIOS boot system was seeing the USB stick as an external USB hard drive.

1) If you have not installed Ubuntu to the USB stick with what is called Persistence then every time you shutdown Ubuntu you will lose any changes & documents that you have made or created during the session. And that is a night & day difference. We can install Ubuntu to an external USB drive in the same way as installing to an internal hard drive & it will work in exactly the same way. But you asked about USB flash drives.

2a) One of the reasons for running a Ubuntu Try/Live session from a DVD disc or USB stick is to find out if there are drivers for all the hardware. The live session uses an open source video driver. We may need a proprietary video driver. As the live session runs in RAM memory use can install drivers during a live session as a test.

2b) We install Linux to its own set of partitions. They are completely separate from any Windows partitions. There is no interaction between Windows & Linux. Unless we (the user) instigates the interaction.

3) We have Ubuntu (with Unity and please do not insult my preferred user interface). Then there is Kubuntu with KDE & Ubuntu Gnome with Gnome 3 shell, & Xubuntu with Xfce, & Lubuntu with LXDE, & Ubuntu Mate with Mate desktop environment. Each has its own web site where you can find information about the different desktop environments & user interfaces. There are other Linux distributions which I do not give support to. So, I will not list them. That is my choice.

Unrelated)

You are wrong about Rhythmbox. It is not baked into the OS. It is one of the default set of applications that are installed when we install Ubuntu. It is an actual application & it can be removed just like any other application. We can also install other music players as well. And it does have menus.

I suggest that you go to the power/cog icon and from the menu that we use to shut down then select Ubuntu Help and learn about the user interface and how application menus appear in the top panel when an application is loaded and we mouse-over the left side of the top panel. You will learn from Help how to change some of these settings.

Regards.

---

### Post by Geoffrey_Arndt on 2016-04-11
Just type the name of any application that you don't see an icon for (in the dash - topmost icon in Launcher panel) . . and you'll get back a search result with that program's icon.   Then, you can click it to start it, or first, drag it to the Launcher and click it there.     Probably easiest just to go to youtube and find the Ubuntu Unity video tutorials there.    If it is a big deal for you, you can also do a reinstall and this time go with Kubuntu, which will give you probably the closest to Windows style of interface.

---

