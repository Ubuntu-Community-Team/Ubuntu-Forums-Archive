---
title: "Does anyone know what files are needed in 8.04 for an Nvidia 6600GT?"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by sharkster2007 on 2008-11-20
Hello Everyone

I am fairly new to ubuntu but have grasped how to manually install .deb files and get my Nvidia 6600GT working in Ubuntu 8.10. (See my quote below for details). 

> Nvidia 177 Driver

FILES REQUIRED BY UBUNTU 8.10:

dkms_2.0.20.4-0ubuntu2_all.deb
nvidia-177-kernel-source_177.80-0ubuntu2_i386.deb
nvidia-glx-177_177.80-0ubuntu2_i386.deb

To install these .deb file double click on the icon and click install in the package manager that appears either install the three Nvidia 177 driver files mentioned above, then go to SYSTEM>ADMINISTRATION>HARDWARE DRIVERS select NVIDIA ACCELERATED GRAPHICS DRIVER VERSION 177, click enable, an arrow should appear asking you to restart your system.

However I have re-installed Ubuntu 8.04 (Because of Nvidia's "Titlebar Glitch" with ubuntu version 8.10 and Nvidia's 173 & 177 Drivers). 

Can anyone tell me which specific .deb files I need to get my Nvidia 6600GT (AGP) (with 3D using "closed source" driver) working under 8.04? 

PS: [COLOR="Red"]I can't use Synaptic (apart from manual installation) as the shared internet PC is windows not linux, my stand-alone is Windows xp & Linux but not net connected, hence my hunt for the .deb files. (Linux on the internet one is not an option, nor is putting mine on net at the moment either)[/COLOR]

PS: I also know how to thank people by clicking on the "medal icon" on the bottom right of posts and will thank users who help me, (unlike a lot of others LOL)

---

### Post by LowSky on 2008-11-20
well it isn't deb but its easily installed
[http://www.nvidia.com/object/linux_display_ia32_177.82.html](http://www.nvidia.com/object/linux_display_ia32_177.82.html) 
or the package here:[http://us.download.nvidia.com/XFree86/Linux-x86/177.82/NVIDIA-Linux-x86-177.82-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/177.82/NVIDIA-Linux-x86-177.82-pkg1.run)

save the file to somewhere you can access easily, then from terminal

type

```
cd /path to file
```
then type
```
sh NVIDIA-Linux-x86-177.82-pkg1.run
```

and FYI the title bar isue with Firefox has been fixed as of this releaese on 11/12/08

---

### Post by sharkster2007 on 2008-11-20
Thanks for trying to help me out Lowsky,

But tried that before with that .run thing was a total pain in the backside, It caused me to leave Ubuntu for Mandriva Linux One 2009, when i saw it was possible i installed ubuntu 8.10 instead. 

PS. Doesn't the Nvidia (177) Driver, suffer the same "titlebar glitch problem", I heard somewhere before you had to have below version (100) think it may be 97 driver to avoid it?

Also my knowledge of the terminal is very limited, I am a very new user.

Thanks for trying to help me on this anyhow :-)

---

### Post by LowSky on 2008-11-20
The commands i give are really simple, it really cant be that hard to install? There are plenty of guides to help you along if you need them on the web

Like I said it has been fixed
> 
Version: 177.82
Operating System: Linux x86
Release Date: November 12, 2008

Release Highlights

    * Added support for the following new GPUs:
          o Quadro NVS 450
          o Quadro FX 370 LP
          o Quadro FX 5800
          o Quadro FX 470
          o Quadro CX 
    * Fixed a problem on recent mobile GPUs that caused a power management resume from S3 to take 30+ seconds.
    * Fixed a problem with hotkey switching on some recent mobile GPUs.
    *** Fixed an image corruption issue seen in FireFox 3**.


---

### Post by sharkster2007 on 2008-11-20
I ll give it a go Lowsky

It isn't a firefox problem I mean the "title bar glitch" is the one that applies to all window titlebars, it sometimes goes grey on every window titlebar lets hope this has been fixed too.

Is it really this easy to:
> type

Code:

cd /path to file

then type
Code:

sh NVIDIA-Linux-x86-177.82-pkg1.run



Thanks again

---

### Post by Shazaam on 2008-11-20
Several ways to do it=
A. Use the Restricted Driver Manager (System>Administration>)
B. Install envy (envyng?), follow the prompts.
C. Some say the hard way but it really isn't=
1. Install build-essential...
```
sudo apt-get install build-essential
```
2. Install headers...
```
sudo apt-get install linux-headers-$(uname -r)
```
3. Download the nvidia drivers you need (preferably to your desktop).
4. CTRL+ALT+F1, login.
5. Enter this....
```
sudo /etc/init.d/gdm stop
```
(stops the gnome-display-manager)
6. cd (change directory) to where you have the driver .run file. I put mine on the desktop...
```
cd ~/Desktop
```
7. Enter this...
```
sudo sh NVIDIA-Linux-x86-drivernumber-pkg1.run
```
(where "drivernumber is the one from your driver ex= 177.82)
8 Let it build the driver module if it wants to, also let it do "nvidia-xconfig".
9. Reboot.
In some cases doing method c will require you to re-install the nvidia driver when you upgrade your kernel. Takes less than 5 minutes.

---

### Post by sharkster2007 on 2008-11-21
Thanks shazam,

I can only use synaptic in manual though

> [COLOR="Red"]PS: I can't use Synaptic (apart from manual installation) as the shared internet PC is windows not linux, my stand-alone is Windows xp & Linux but not net connected, hence my hunt for the .deb files. (Linux on the internet one is not an option, nor is putting mine on net at the moment either)[/COLOR]

I've deceided to go with the .run version Lowsky sugested From:

> [http://www.nvidia.com/object/linux_d...32_177.82.html](http://www.nvidia.com/object/linux_d...32_177.82.html)
or the package here:[http://us.download.nvidia.com/XFree8...77.82-pkg1.run](http://us.download.nvidia.com/XFree8...77.82-pkg1.run)


So far i've got to this stage, stored the .run file in home folder (altered commands 2 as had probs with root)

Code:
>  sudo su
(Logs me in as root overcoming previous problem)

Code:
> sh NVIDIA-Linux-x86-177.82-pkg1.run
(To install NVIDIA Package)

after I have done this It checks the integrity and comes up with the error: > ERROR: You appear to be running an X server; please exit x before installing

I'll try to locate the Build-essential and linux headers manually thanks for your help i'll try your solution out now

Update: i have located the files i think i need now from [http://packages.ubuntu.com/hardy/i386/]("http://packages.ubuntu.com/hardy/i386/") could only find "linux-headers" for ubuntu dapper, and got the "build-essential" for hardy.

---

### Post by mvalviar on 2008-11-21
You could try envy > [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by philinux on 2008-11-21
<snip>

---

### Post by sharkster2007 on 2008-11-21
I ve had enough of this there is too much "dependancy hell" involved with the "build essential" part, I am migrating back to Ubuntu 8.10 as we speak.

Thanks Shazaam, I seems that if I was able to carry this out it would have worked.

Lets hope Ubuntu 9.04 Eliminates this problem (or at least makes it easier as 8.10 did) I think this particular flaw puts a lot of would be new linux ubuntu user (both ATI & NVIDIA) which is a shame because Ubuntu seems to be a really good OS. 

More work needs to be done to ease the installation of "closed source" drivers in my opinion though. :-(

PS the 177.82 NVidia driver is available as an .RPM file (Incompatible) why hasn't a .DEB version been made available?

---

### Post by philinux on 2008-11-21
You could have download directly from the package. Links at bottom of page.
[http://packages.ubuntu.com/intrepid/nvidia-glx-177](http://packages.ubuntu.com/intrepid/nvidia-glx-177)

---

### Post by Shazaam on 2008-11-21
```
PS: I can't use Synaptic (apart from manual installation) as the shared internet PC is windows not linux, my stand-alone is Windows xp & Linux but not net connected, hence my hunt for the .deb files. (Linux on the internet one is not an option, nor is putting mine on net at the moment either)
```
Sorry. I thought you had internet access. philinux' post should help.

---

