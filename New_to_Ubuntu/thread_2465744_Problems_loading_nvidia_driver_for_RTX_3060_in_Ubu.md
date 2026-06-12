---
title: "Problems loading nvidia driver for RTX 3060 in Ubuntu 18.04"
date: 2021-08-10
forum: New to Ubuntu
---

### Post by dieguels13 on 2021-08-10
[COLOR=#333333][FONT=DIN-Web-Pro]Hi,[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]I am having problems with my driver in Ubuntu 18.04 with a GPU Geforce RTX 3060 and CPU intel core i7 on a computer with dual booting (Windows 10 and Ubuntu). I have installed the driver by all the methods I have seen online, but with all of them I get the following after introducing the command nvidia-smi:[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]“NVIDIA-SMI has failed because it couldn’t communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running”

[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]Right now I am trying with the driver 460, but I have also tried with 470.

[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]I dont have the file: “/lib/modprobe.d/blacklist-nvidia.conf”

[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]If I introduce the command sudo prime-select nvidia, I get: “Info: the nvidia profile is already set”

[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]My bug report states the following:
"Unable to load nvidia-installer ncurses v6 user interace.
Using: nvidia-installer ncurses user interface.
Error: An NVIDIA kernel module 'nvidia' appears to already be loaded in your kernel . This may be because it is in use (for example, by an X server, a CUDA program, or the NVIDIA persistence daemon)."

I dont know how to fix it. Could someone help me?
Thanks.

[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]Thanks.[/FONT][/COLOR]

---

### Post by Autodave on 2021-08-10
I believe that you are going to have to update to at least 20.04.  The RTX 3060 is very new and will not likly be supported by 18.04.  Hopefully someone else will wander by and confirm this, but I seem to remember having to update to 20.04 for my RTX 2070.

---

### Post by monkeybrain20122 on 2021-08-10
Probably you need to grab a newer kernel. [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/) Try something like 5.11

---

### Post by linuux on 2021-08-21
Did you fix it, OP?   I am wondering whether a new nvidia or amd card is a good choice for a (future) new build.

I think you should 'switch' to 21.04 - therefore, new packages/software and new kernel.  I think an upgrade from 18.04 to 20.04, for example, probably won't go smoothly.

I think RTX/Ampere cards will run more smoothly with newer versions - later kernels etc. - recent Nvidia driver.  I read that it's advisable to use Nvidia for CUDA, Blender and other video editing software - for the newer cards, you just need to enable 'Additional Drivers' in the repository (thus, check 'non-free' repository) and update your system.   It's probably better to do this after a fresh install - the nouveau drivers are probably enabled beforehand but will be 'disabled' if you enable the binary drivers.

If anything goes wrong, you purge everything nvidia - and 'autoremove' the nvidia stuff - and start over.  You shouldn't have to do that if you use the nvidia driver in the Ubuntu repo (as of this date, it's probably 465 or 470*).

*470 - is the latest one as of today and it might be able to be used with XWayland - YMMV

---

