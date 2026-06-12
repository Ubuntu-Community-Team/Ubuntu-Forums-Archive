---
title: "How to switch to AMD discrete graphics on laptop (Ubuntu 16.04)"
date: 2016-09-04
forum: New to Ubuntu
---

### Post by khopesh-anu on 2016-09-04
Hello everyone!

I just recently caved in and decided to try dual-booting Ubuntu alongside Windows 10 (which finally made me realize, I HATE Windows with a passion) using a USB to install Ubuntu. I've only run into one really annoying issue so far that I can't Google and figure out how to fix; how do I get it so that the laptop I'm using uses the discrete graphics my laptop has instead of using the crappy Intel integrated graphics? I've been googling a lot about it to no avail and as a gamer it worries me that I can't figure out if I can force games to use the dedicated gpu (since I don't believe Catalyst Control Center works in Ubuntu 16.04, although if I'm wrong, please by all means inform me). I'm really hoping someone else knows what to do here, since I'm sorta not very inclined to go onto windows 10 just to play games :lolflag:

System Specs (in case you guys/girls need them to figure out what to do):
Model of Laptop: Lenovo Y40-80
Processor: Intel Core i5-5200U CPU @ 2.20 GHz x 4
Graphics (Integrated): Intel HD 5500 (Broadwell GT2)
Graphics (Dedicated): AMD Radeon R9 M275x
OS's: Windows 10 & Ubuntu 16.04

Note: typing in lspci | grep VGA only showed the Intel card, does this mean anything significant? I had to do the below to get it to show up.

khopesh_anu@Seker:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 5500 (rev 09)
khopesh_anu@Seker:~$ lspci |grep ATI
05:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Venus XTX [Radeon HD 8890M / R9 M275X/M375X] (rev ff)
khopesh_anu@Seker:~$ 





p.s: Loving Ubuntu 16.04 so far! Not surprised it seems nicely put together, since the other 2 open source programs I've tried (Blender and GIMP) are also solid. So much to learn though XD

---

### Post by Bashing-om on 2016-09-04
khopesh-anu; Hello;

As a place to start:
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
May be one good option. Please read and understand the entire tutorial .

Others report good results:
 [https://wiki.archlinux.org/index.php/PRIME](https://wiki.archlinux.org/index.php/PRIME)

The good news is that there are options


[INDENT]your results could vary
[/INDENT]

---

### Post by khopesh-anu on 2016-09-07
So, haven't made much progress with this (I believe I did everything in the Hybrid Graphics section correctly) and I'm trying the stuff that the PRIME page mentions. So, when I do ```
xrandr --listproviders
``` the code I get back is ```
Providers: number : 2Provider 0: id: 0x6c cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 3 associated providers: 0 name:Intel
Provider 1: id: 0x45 cap: 0x0 crtcs: 6 outputs: 0 associated providers: 0 name:VERDE @ pci:0000:05:00.0

``` instead of what they get, which I'm a tad confused on. And if I try using the next command they give, I get this error if I try to use the command they give ```
xrandr --setprovideroffloadsink "VERDE @ pci:0000:05:00.0" IntelX Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  34 (RRSetProviderOffloadSink)
  Value in failed request:  0x45
  Serial number of failed request:  16
  Current serial number in output stream:  17

```
This is when I go :confused: and think maybe I'll just not game as much until I actually build a desktop for gaming (since laptops seem to be quite the pain to deal with).

If anyone has any ideas, I'll try them. But I don't expect that I'll get this working anytime soon. It really doesn't help that I'm new to Ubuntu, but so far, anything AMD related has proven to be a major pain for me anyway so I am not surprised at all by this :lolflag:
P.S: Almost forgot to say thanks to [COLOR=#000000]Bashing-om for trying to help[/COLOR]

---

### Post by rdragonrydr on 2017-08-10
I am not sure how much you should trust me on this, since last time I tried it my computer decided it wanted to no longer boot up again. Of course, that might be because of a combination of Nvidia's insanity and my use of both xrandr and switcheroo at once. I never said I really have any idea what I am doing either.

With that said (and that was for an Nvidia GPU, not AMD) I have had better luck with AMD personally. (On a desktop. I suspect all luggables might be crap, though.)

Try 

xrandr --setprovideroffloadsink VERDE Intel anyway, or maybe you can use the IDs, like 1 instead of the recalcitrant AMD one.

The following is from the PRIME link from Arch:
[COLOR=#333333][FONT=UbuntuMono]
[/FONT][/COLOR][FONT=sans-serif]Example:[/FONT]
$ xrandr --setprovideroffloadsink radeon Intel
[FONT=sans-serif]You may also use provider index instead of provider name:[/FONT]
$ xrandr --setprovideroffloadsink 1 0
[FONT=sans-serif]Now, you can use your discrete card for the applications who need it the most (for example games, 3D modellers...) by prepending the DRI_PRIME=1 environment variable:[/FONT]
$ DRI_PRIME=1 glxinfo | grep "OpenGL renderer"OpenGL renderer string: Gallium 0.4 on AMD TURKS[COLOR=#333333][FONT=UbuntuMono]

One last thing: Check to see if your BIOS has a mode to switch GPUs.[/FONT][/COLOR]

---

### Post by ozp on 2018-07-20
How to switch to AMD discrete graphics on laptop (Ubuntu 18.04) ?

---

### Post by wildmanne39 on 2018-07-20
Helllo ozp, this is an very old thread, please start your own.

Thanks

Thread closed!

---

