---
title: "Ubuntu Release for TOSHIBA M2???"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by abro89 on 2013-02-26
Hi:

just started testing Ubuntu...really a great OS. What ver do I need for a TOSHIBA M2??? I have a non-PAE CPU (Pentium M at 1.6G/1G RAM/60G HD) and nVIDEA GeForce FxGo5200 grapic processor. 

Thx...appreciate any help/direction.....abro89

---

### Post by BarfBag on 2013-02-26
The standard, 32 bit .iso is the one you'll want.

---

### Post by DuckHook on 2013-02-26
No distro from 12.04 onwards will work with a non-PAE CPU. You have two choices: Install 11.10, pin the kernel and upgrade to 12.04 (not recommended), or install using an alternate minimal install ISO that has a custom kernel and build your desktop the custom way. Either way, it is a project. Moreover, your laptop is too underpowered to run Ubuntu, but Lubuntu would be ideal. Xubuntu, reasonable.

Overview:
You will have to build your Desktop Environment up from a minimal install using a modified kernel from [this]("http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html") site. WEB UPD8 is a phenomenal site for Ubuntu tweaking, tinkering and hacking. I have used this kernel for my old Dell laptops with the same Pentium 'M' CPU that you have. For what it's worth, I can vouch for the safety of their download. If you want more reassurance, you should Google extensively before downloading. Their instructions on the site are excellent and it is pointless for me to repeat them.

Remember to pin your kernel before doing your first update.

Good luck!

---

### Post by abro89 on 2013-02-27
thx....very good info and well described I will start w/ Lubuntu and see how it goes. Other people have suggested ZORIN.....any thought????. Als0 if my laptop is "underpowered" what is a good laptop I should be using for Ubuntu latest ver???? I am a DELL man and use Ebay extensively . 

btw........LINUX MINT 12 boots right out of the gate but I have a video driver issue w/ nVIDA (I think). I cant see desktop again after reboot....everything disappears and left with 2 icons and a basic (grey) desktop, no toolbars or icons like in WINDOWS. Any thoughts?

really appreciate your help.....

thx again......abro89

---

### Post by Nr90 on 2013-02-27
> **DuckHook said:**
> No distro from 12.04 onwards will work with a non-PAE CPU. You have two choices: Install 11.10, pin the kernel and upgrade to 12.04 (not recommended), or install using an alternate minimal install ISO that has a custom kernel and build your desktop the custom way. Either way, it is a project. Moreover, your laptop is too underpowered to run Ubuntu, but Lubuntu would be ideal. Xubuntu, reasonable.

Overview:
You will have to build your Desktop Environment up from a minimal install using a modified kernel from [this]("http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html") site. WEB UPD8 is a phenomenal site for Ubuntu tweaking, tinkering and hacking. I have used this kernel for my old Dell laptops with the same Pentium 'M' CPU that you have. For what it's worth, I can vouch for the safety of their download. If you want more reassurance, you should Google extensively before downloading. Their instructions on the site are excellent and it is pointless for me to repeat them.

Remember to pin your kernel before doing your first update.

Good luck!

Another option is building your own kernel, but that might be a bit much for a first time installing linux...

---

### Post by Paqman on 2013-02-27
> **DuckHook said:**
> 
You will have to build your Desktop Environment up from a minimal install using a modified kernel from [this]("http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html") site.

Are you sure about that? Non-PAE kernels are still in the repos, and my understanding was that the minimal image does use a non-PAE kernel. It should just be a matter of firing up the mini.iso and slapping (l/x)ubuntu-desktop on.

---

### Post by prodigy_ on 2013-02-27
Lubuntu 12.04 32-bit comes with non-PAE kernel. LXDE could be perfect considering your hardware.

---

### Post by DuckHook on 2013-02-27
> **Paqman said:**
> Are you sure about that? Non-PAE kernels are still in the repos, and my understanding was that the minimal image does use a non-PAE kernel. It should just be a matter of firing up the mini.iso and slapping (l/x)ubuntu-desktop on.

It's worth a try. Didn't work for me. But perhaps I had other incompatibility issues than just the kernel. Once I installed the WEB UPD8 kernel, install went fine. My info re: non-PAE kernels are from their site.

---

### Post by DuckHook on 2013-02-27
> **abro89 said:**
> Other people have suggested ZORIN.....any thought????.

There are too many choices to count. You can try Bodhi or Crunchbang, but I would stick with Lubuntu for well tested flavour and access to the Ubuntu repos.

>  Als0 if my laptop is "underpowered" what is a good laptop I should be using for Ubuntu latest ver????Minimal practical specs are: Duo-core CPU, 2GB system RAM, 3-D Video with 256MB dedicated VRAM (not shared from system RAM). Ubuntu will run with less but you won' t be happy. If you want to do anything needing substantial resources like running VMs, then even more of everything is better.

> btw........LINUX MINT 12 boots right out of the gate but I have a video driver issue w/ nVIDA (I think). I cant see desktop again after reboot....everything disappears and left with 2 icons and a basic (grey) desktop, no toolbars or icons like in WINDOWS. Any thoughts?See subsequent posts by others. You may want to try full install of Lubuntu 12.04 - 32-bit. Seems it comes with non-PAE kernel (news to me). Might solve your video issues too.

---

