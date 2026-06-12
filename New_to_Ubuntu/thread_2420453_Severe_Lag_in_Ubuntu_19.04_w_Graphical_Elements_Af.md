---
title: "Severe Lag in Ubuntu 19.04 w/ Graphical Elements After Installation Using Nomodeset"
date: 2019-06-05
forum: New to Ubuntu
---

### Post by whisper1530 on 2019-06-05
I recently attempted to install Ubuntu 19.04 onto my desktop to replace Windows 10. I have never before used Ubuntu.

I created a bootable flash drive using Rufus. The first problem I encountered was when booting. The boot menu listed the flash drive twice, once with the prefix "UEFI" and another time without the prefix. I get a different menu depending on which I select. The non-UEFI option shows me a purple screen with a little man and keyboard at the bottom. The UEFI screen says "GRUB" at the top and gives five or so options.

I selected the UEFI option and selected "install Ubuntu." After seeing an Ubuntu loading screen, my monitor went dark and did nothing. I read online that I must install Ubuntu by selecting "nomodeset" in the non-UEFI menu (the one with the little man and keyboard). I pressed the down arrow key, F6, and selected "nomodeset," marking it with a little "x," while within the non-UEFI menu. I then selected "install Ubuntu."

After the installation was complete, I booted up my computer. I noticed immediately that any graphical task like window animations, pressing the Ubuntu start menu, watching videos, etc. were unusably sluggish. I read online that I must install proprietary video drivers under the "additional drivers" menu. When I looked there, however, it said that no drivers were available. I attempted to install the AMD drivers manually. I downloaded them from AMD's website, unpacked the compressed folder, and used the terminal to install them. After what appeared to be a typical installation, the terminal informed me that there was an error. (I believe it is because the drivers stated they are for Ubuntu 18, not 19.)

So, now I'm stuck. I reinstalled Windows to look for an answer online, but I cannot find one. I have my heart set on Ubuntu 19.04, but I don't know what to do from here. Could someone please instruct me what to do to resolve this frustrating issue?

My PC hardware includes:

[LIST]
[*]Intel Core i5-6500 Processor
[*]16 GB of RAM
[*]AMD R9 390 Graphics Card
[/LIST]

---

### Post by wildmanne39 on 2019-06-06
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

