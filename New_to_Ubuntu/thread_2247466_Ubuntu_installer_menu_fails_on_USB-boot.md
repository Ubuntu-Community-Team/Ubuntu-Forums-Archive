---
title: "Ubuntu installer menu fails on USB-boot"
date: 2014-10-08
forum: New to Ubuntu
---

### Post by Daniel_Minnaar on 2014-10-08
Hi,

As a predominately Windows-only developer, I've decided I want to start getting into linux. So I downloaded the latest Ubuntu 14.x amd64 ISO, mounted it onto a 16gb USB drive and configured my BIOS to make it as the boot drive.

This works fine, but as soon as I hit return on any of the 'Try' or 'Install' menu items, the computer locks up for a few seconds and results in a grey screen with a call trace that starts with wn-block (0,0) - looks like this: [https://www.youtube.com/watch?v=BT-2lyfXfwM](https://www.youtube.com/watch?v=BT-2lyfXfwM)

From what I've read, I've tried the following with no luck:

[LIST=1]
[*]Disabling fast/quick boot 
[*]Disabling HPET  Power Management 
[*]Changed IDE access to 'Large' 
[/LIST]

I currently have Windows 7 installed on the box, but I was planning on formatting the disk and just running Ubuntu anyway, so I'm not sure if the pre-existing install is causing a problem?

I've read some comments about booting up with command lines etc, but I have no idea how to do that...

My machine specs:

AMD Athlon X2 5200 CPU
Asus M2N Motherboard
4GB DDR2 RAM
nVidia gfx card

Any help would be greatly appreciated.

---

### Post by sudodus on 2014-10-08
Welcome to the Ubuntu Forums :-)

I suspect that you have problems with the graphics driver. I have a computer with the same motherboard (with a slightly slower CPU) and the nvidia graphic chip

     ```
*-display
          description: VGA compatible controller
          product: C68 [GeForce 7050 PV / nForce 630a]
```

as shown by ```
lshw
```

That chip work well with the still going strong version Ubuntu ***12.04.5 LTS***. Probably Xubuntu or LXLE will be much more responsive than standard Ubuntu or Kubuntu. It is the same engine under the hood, and all those versions will be supported until April 2017 (except Xubuntu, which will be supported only until April 2015).

I use the nvidia proprietary driver version 304.88

You might succeed better using the boot option **nomodeset**, and then install the nvidia proprietary driver. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

It might even work via nomodeset, to get version 14.04.1 LTS working.

Good luck and come back with questions, if this first tip is not enough!

---

### Post by Daniel_Minnaar on 2014-10-09
Thanks, I'll give the nomodeset option a try first, and then try another version if I don't come right. Could you possibly shed some light on the policy of packaged drivers... do the various distributions only support newer gfx chipsets or something?

---

### Post by sudodus on 2014-10-09
In principle new linux versions support all old hardware (with drivers), but in practical life, some old hardware will be dropped (maybe because of incompatibility with identification of new hardware, maybe by mistake, maybe planned (if very old hardware). This is about the free drivers, that come with the kernel.

Then, there are proprietary drivers, that can be installed afterwards, for example for graphics, wifi and printers. These are made and supplied by the hardware companies, and there is no guarantee, that the company bothers to supply a driver for an old chip to a new version of linux. Some companies are better than others, but many hardware companies pay much less attention to linux compared to Windows and Mac OS.

---

### Post by Daniel_Minnaar on 2014-10-09
When the menu options load up, the GUI freezes. F6 does nothing at this point. If I press TAB quickly enough when it first displays, then the lines at the bottom become visible with each key press. How do I get into nomodeset now?

My USB stick is  NTFS formatted. I'll try reformat to FAT32 when I get home later - I've read some people with a freezing problem solved by a format and new file system...

[IMG]http://i.imgur.com/UvBEUok.jpg[/IMG]

Edit: The tiling of the ubuntu logo almost seems there's something wrong with the rendering of the screen, I wonder what that might hint at?

---

### Post by sudodus on 2014-10-09
I suggest that you try something based on 12.04 LTS, for example LXLE, because you have problems with graphics at a very early stage. You can also try a couple of other linux distros, that are known to work well with old hardware, Knoppix and Wary Puppy.

Try them live, without installing until you find what you want.

---

