---
title: "Problems with Ubuntu on HP Pavilion g7"
date: 2014-07-07
forum: New to Ubuntu
---

### Post by Nettie on 2014-07-07
[SIZE=3]**Hi all, I just Installed Ubuntu 14.04 LTS, Its pretty awesome and I like it but.....there are some issues involving my Sound System and Graphics.**

_About my computer:_
[B]
Before I installed Ubuntu I had WIndows 7[/B]

[B]Memory       5.2 GiB
Processor    AMD A8-4500M APU with Radeon (tm) HD Graphics x 4 (A8 VISION AMD)
Graphics     Gallium 0.4 on AMD ARUBA 
OS type      64-but
Disk           735.5 GB (Was 750)[/B]



**Before **I installed Ubuntu, I had a pretty good sound system: It was a HDMI / DisplayPort Built-in Audio
but after installing Ubuntu, It's now just regular Spreakers Built-in Audo which doesn't have the usual surround sound system that HDMI had. 

I tried going to **All Settings --> Sound --> Output --> Play sound through --> HDMI / Display Port (Built-in Audio)** and trying it out. 
But there's no sound when I switched it from** Speakers Built-in Audio to HDMI. **

If someone could help me with that, that would be awesome.

ALSO my Graphics on HP:

Switching to I don't know which Graphics Ubuntu has, it was pretty good when I still had Windows 7 but it got changed as well.
The color is grainy and sorta off set. I miss my old **Gallium 0.4 on AMD ARUBA**. With WIndows I had also upgraded my** AMD **previously before Ubuntu but that must've been wiped off my Hard-Drive after
I installed Ubuntu. The Video is very grainy especially on Youtube and just watching a MP4 in my Videos. 

And does anyone know how to download Sims 3? I'm addicted to this game lol

If you would please help me fix these somehow, it would be greatly appreciated! Thanks![/SIZE]

---

### Post by slooksterpsv on 2014-07-08
Do you have an HDMI Cable attached to an audio output? That's what the HDMI audio is for, otherwise it's just the internal speakers.
Sound quality-wise, I can't help you, I have the same issue, but I can work through it.

Graphics-wise, did you install any graphics drivers in Ubuntu? I'm assuming no. Windows and Linux are separate. Windows uses it's own set of drivers, and Linux has it's own. They're programmed to work with the core of the operating system using it. Windows may have some DirectX (graphical drawing) implementations, and Linux has it's own via OpenGL. You can try to go to Ubuntu Software Center -> Edit -> Software Sources -> Additional Drivers.
**NOTE: ** Even if it shows drivers there, and you install them, they may not work. It varies from system to system sometimes.

The Sims 3. Let's check WINE - [https://appdb.winehq.org/objectManager.php?sClass=application&iId=9732](https://appdb.winehq.org/objectManager.php?sClass=application&iId=9732)

Looks like they have a video tutorial of how to get it running via WINE. The Sims 3 doesn't have a Linux application, but you can use a program that will attempt to run the game or other Windows software, it's called WINE (WINE = Wine is not emulation).

I think I've answered a good selection of questions, hopefully someone can help with the quality of sound.

Oh and always - Welcome to the Ubuntu Forums! =D

---

### Post by mastablasta on 2014-07-08
by all means do this:
> **slooksterpsv said:**
> You can try to go to Ubuntu Software Center -> Edit -> Software Sources -> Additional Drivers.


the drivers you are using are opensource drivers. and while they work for some chips they are terrible on others. especially some of these newer chips have a few features lacking. you need to install those AMD proprietary drivers (just like in Windows) to get themaximum out of the card.

the HDMI sound might also be solved with that.

---

