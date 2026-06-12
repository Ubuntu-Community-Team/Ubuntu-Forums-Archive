---
title: "Dell Latitude D430"
date: 2014-03-29
forum: New to Ubuntu
---

### Post by freedda on 2014-03-29
With the demise of support for windows XP, I'm considering what to do, and besides getting a new one, I was thinking of "re-using" my slightly older dell laptop. 

I was thinking of trying to install win7 on it, but that's getting costly and complicated. This leads me to Ubuntu. 

So, basic question is, would I be able to install and use it on this laptop? And if so, can I do this by either downloading the OS directly from the web or installing it from a USB flash drive?? 

Also, where can I see what programs are available? I think I mainly want to use the laptop for email and web browsing, but I might also want to do some writing (word processing) and edit photos, as I do now with Photoshop. 

Best, David.

---

### Post by elliotn on 2014-03-29
Hi David
You can download Ubuntu or its variants with Lubuntu being the slimest when it comes to system resources thus it is good for older laptops and has a familiar interface to XP, if your laptop has enough juice to run Ubuntu then its a plus . download Ubuntu and lubuntu and test drive them and whichever runs to your satisfaction then make it permanent

---

### Post by sudodus on 2014-03-29
I suggest that you download the iso file to Windows XP and use ***Unetbootin*** to create a USB boot drive. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

If you specify your computer, at least

- (Brand name Dell) and model
- CPU
- RAM (size)
- Graphics chip/card
- Wifi chip/card

it will be possible to give you relevant tips about different flavours and versions of Ubuntu. There are standard Ubuntu, Kubuntu, Lubuntu, Ubuntu Gnome and Xubuntu, and there are versions 12.04.4 LTS, 13.10 (and in April the new 14.04 LTS).

---

### Post by EnglishElectricAndy on 2014-03-29
Creating a bootable USB is probably the best route. Once you've rejigged your BIOS settings to allow booting from the USB to take precedence over the machines internal drive you should be given an option to 'Try without installing'. This option gives you the chance to explore the OS by running it directly from the USB without affecting your current installation. I spent the best part of two weeks, on and off, using this option before deciding to go for a full install to my HD.

This was with Xubuntu, which breathed new life into a 6 year old Sony Vaio.

I'd add this caveat though, Linux is not Windows - so don't expect it to be like Windows.

---

### Post by elliotn on 2014-03-29
The thing is if the old dell doesn't boot from USB you will have to burn into a dvd

---

### Post by Rob Sayer on 2014-03-29
> **freedda said:**
> ... I was thinking of trying to install win7 on it, but that's getting costly and complicated. This leads me to Ubuntu. 

I don't think new copies of windows 7 have been available since the end of last October.  I do know people who have downloaded 'cracked' copies of windows and installed them but that's just stupid.

Remember the big fuss when people found out that Internet Explorer was downloading system/usage details to Microsoft?  They stopped that but now Windows itself does it.  It's not exactly well documented.

So I'm not surprised this is leading you to ubuntu.

> So, basic question is, would I be able to install and use it on this laptop? And if so, can I do this by either downloading the OS directly from the web or installing it from a USB flash drive?? 

It shouldn't be too much trouble.  There may be some issues with hardware support which may take a bit of configuring.  I've come to expect at leas a bit of config in linux.  But that's more of a problem with bleeding edge hardware, not xp machines.

As mentioned, you need to post detailed specs.

Which affects *which* ubuntu version you'd want.  I'm seeing a lot of total linux novices here lately who don't understand that there are 4 ubuntu desktop versions.  Unity may be their 'default' one but it's designed for modern hardware.  It's as heavy on resources as windows 7.

On my more modern laptop that came with windows 7 I use kubuntu (with the KDE desktop).  It's considered weighty but unlike unity you can pare it down in settings and make it run a lot faster.  But I've had it on my 1Gb netbook too and, while it's surprisingly good and faster than the Win 7 Starter it came with, I'd want at least 2Gb RAM for KDE.

I'm using lubuntu 13.10 (LXDE desktop) on my 1Gb netbook now.  I also have a minimal KDE install but I'm going to upgrade the RAM to 2Gb before I decide whether or not to use it.  LXDE is *seriously* fast.

> Also, where can I see what programs are available? I think I mainly want to use the laptop for email and web browsing, but I might also want to do some writing (word processing) and edit photos, as I do now with Photoshop.

I haven't had any problems.  In fact in Windows 7 I used mostly programs that were ported from Linux because they're better behaved.  Especially media software.  Windows ones have a bad habit of installing flaky 3rd party codec packs because the developers can't or won't do their own.

You can't do that so easily in linux.  The permission levels actually work the way they should.  This is largely why there aren't linux viruses.  I know  guys who have been running linux on their personal computers for 20 years.  Not *one* uses an antivirus program running in the background like you have to in windows.

I'm seeing a lot of new users who think they can run all their windows programs using Wine.  That isn't strictly true ... it's not reliable.  You can get close equivalents generally but not always.

Many linux people, for example, say you can use Gimp instead of Photoshop, and that's true for many users.  But if you're actually using it professionally, no.  There's a proprietary file format used by all digital printing shops and Gimp doesn't support it.  With Pantone it's the same situation.

For that reason, I'd recommend keeping at least one Windows partition and dual boot that, though if that has to be XP I'd never, ever go online in XP again.  It's called an air gap and it's pretty effective security.  As good as you can get.

---

### Post by freedda on 2014-03-29
In response to an earlier post asking for more info about my laptop: 

Latitude D430  
Processor Intel Core2 CPU U7600 @ 1.20GHz 
Processor Speed 1.17 GHz 
Memory (RAM) 2048 MB 
Operating System Microsoft Windows XP Home Edition, Ver. 5.1.2600 
Hard Drive 74GB capacity. 

Wifi: 
Dell Wiireless 1390 WLAN Mini-Card Rev 4.4
Chipset: BCM4311 / BCM2050

Based on this, if people can give me suggestions for which flavor of the OS might be best, that would be great. Best, David. Also, where can I look at which programs are available in Ubuntu?

---

### Post by Vladlenin5000 on 2014-03-29
Info about the GPU is missing and it may or may not be a decisive factor in the end. However, based on the data you already provided, the hardware is enough for running the 'standard' Ubuntu, ie, the one with Unity. It's exactly the one I'm posting from - not my usual laptop - and it has worse specs (CPU) than yours but it also has a dedicated nVIDIA mobile GPU with 512MB Video RAM.

I foresee trouble with the WiFi - it'll need a few tweaks - but that will happen with any flavor.

---

### Post by sudodus on 2014-03-29
1. If you have a reasonably fast internet connection, I suggest that you try standard Ubuntu as Vladlenin5000 suggests, and also Xubuntu, with a 'medium light' desktop environment (lighter than standard Ubuntu).

2. Broadcom wifi needs some tweaking to work, so it is best to use wired internet (ethernet) for updating/upgrading until you get the wifi working.

3. And please let us know about your graphics chip/card: Intel or nVidia or AMD/ATI/Radeon? And the model number, if you can find it via the Control Panel in Windows.

4. I'm sure that your computer can boot from USB, so Unetbootin should make a good USB boot drive from the Ubuntu or Xubuntu desktop installer ISO file (unless the USB system is damaged).

-o-

Finally, there is a ***Software Center***, where you can find many programs to install easily from the repositories. It is much better to install programs from the repositories than to download programs from an external site, [compile and] install it.

You can also search for programs or applications via the internet; use the search phrase linux kind-of-program for example ***linux video player***. And don't forget that you can get personal recommendations, if you ask here at the Ubuntu Forums. But open a new thread for that purpose to attract persons who can help with that/those program(s) that you need.

---

### Post by amanchesterman on 2014-03-29
I have a Dell D420 on which I have dual booted Windows XP and various flavours of Linux: currently Peppermint, but I have run Xubuntu on it with no problem.
There's a website [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html) which lists Windows programs and their Linux equivalents. It's a couple of years out of date now but for someone making the transition from Windows (as I did a few years back) it's a helpful overview: there are many alternatives available.

---

### Post by freedda on 2014-03-29
> **Vladlenin5000 said:**
> 
I foresee trouble with the WiFi - it'll need a few tweaks - but that will happen with any flavor.What does this mean? New hardware? Software? Difficult?

---

### Post by freedda on 2014-03-29
> **Vladlenin5000 said:**
> Info about the GPU is missing ... I foresee trouble with the WiFi - it'll need a few tweaks - but that will happen with any flavor. I gave the info I found: "Processor Intel Core2 CPU U7600 @ 1.20GHz" is there more?

---

### Post by freedda on 2014-03-29
Thanks all. I was hoping that this would be simpler than installing Window 7, but from the range of responses, I'm not sure. My little pee brain is overwhelmed, but I'll read through all this and try to make sense of it. 

What I'm looking for is an OS that's stable and secure and where i can do the major tasks I need, such as email, writing, etc. As to GIMP, I'll just have to try it and see--I have a Win7 computer that I keep offline, just for doing photo work on, so GIMP may work as an adjunct to that. 

David 

Best, David.

---

### Post by monkeybrain20122 on 2014-03-29
That will work. I had a D430 with Ubu10.10 on it for a while. Wifi may take some work.

---

### Post by mörgæs on 2014-03-29
It is indeed simple to install. Just try - there are lots of people ready to help if anything comes up.
As for the Broadcom card it might work out of the box if you check 'install restricted drivers' during install.

---

### Post by monkeybrain20122 on 2014-03-29
> **mörgæs said:**
> 
As for the Broadcom card it might work out of the box if you check 'install restricted drivers' during install.

Not necessarily. My current machine has a BCM 4313, it works out of the box with the open brcmsmac driver but checking 'install third party software' during install switch to the wl driver which killed my internet connection immediately. So my suggestion is don't check the box if wifi works in the live usb and only check it if it doesn't.

---

### Post by freedda on 2014-03-29
> **monkeybrain20122 said:**
>  ... my suggestion is don't check the box if wifi works in the **live usb** and only check it if it doesn't. Sorry, but that makes absolutely no sense to me. david

---

### Post by tripp98 on 2014-03-29
Create a live usb boot of either lubuntu or ubuntu and try it.  See how it works from the usb.  It will run faster once you "install" it on the hard drive but give it a try.  This isnt like a windows boot disk.  You can actually run the whole operating system from a usb device or dvd.

---

### Post by sudodus on 2014-03-29
> **freedda said:**
> What does this mean? New hardware? Software? Difficult?

Not difficult with guiding from someone who has done it :-)

> **freedda said:**
> I gave the info I found: "Processor Intel Core2 CPU U7600 @ 1.20GHz" is there more?

Vlad and I ask for the ***graphical*** processor, chip or card: probably Intel, nVidia or AMD/ATI/Radeon (and if possible a model number). If you can't find it, never mind, linux is free. ***Try how it works*** (live from the CD/DVD/USB drive) without installing. It costs only the downloading and your own efforts to install it.

> **freedda said:**
> Thanks all. I was hoping that this would be simpler than installing Window 7, but from the range of responses, I'm not sure. My little pee brain is overwhelmed, but I'll read through all this and try to make sense of it. 

What I'm looking for is an OS that's stable and secure and where i can do the major tasks I need, such as email, writing, etc. As to GIMP, I'll just have to try it and see--I have a Win7 computer that I keep offline, just for doing photo work on, so GIMP may work as an adjunct to that. 

David 

Best, David.

We want to help you at the early stage, so that you can avoid heading in a wrong direction. I can assure you, that normally it is at least as simple to install Ubuntu and Xubuntu as to install Windows 7. But there are a few things that might be difficult, if you have certain hardware components in the computer.

---

### Post by chili555 on 2014-03-30
> **freedda said:**
> 

Wifi: 
Dell Wiireless 1390 WLAN Mini-Card Rev 4.4
Chipset: BCM4311 / BCM2050

Quite easy. Please see here: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

