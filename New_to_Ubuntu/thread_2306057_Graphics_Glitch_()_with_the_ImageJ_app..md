---
title: "Graphics Glitch (?) with the ImageJ app."
date: 2015-12-11
forum: New to Ubuntu
---

### Post by schwobi on 2015-12-11
Hi there,

I just recently switched to Unix/Linux Ubuntu 15.10 with the GNOME desktop after using Windows OS for years... therefore - just in advance - I would like to ask for Your forgiveness regarding my inexperience.
I am running Ubuntu 15.10 (64-bit), GNOME desktop interface on the following machine: Lenovo-ThinkPad-L450, Intel® Core&#8482; i5-5200U CPU @ 2.20GHz × 4, Intel® HD Graphics 5500 (Broadwell GT2), plus some minor hardware changes (substituting the built-in HDD with Samsung 850 V-NAND SSD, and a SODIMM RAM upgrade).

So here is my problem:
ImageJ is a Java-based image analysis tool I run in parallel to the 'gimp' and 'inkscape' applications due to easy customizability (plugins, macros, data-sheet output, ...) I need for intended scientific purposes.
After successfully installing the ImageJ application either through the Ubuntu-Software-Manager, or the 'sudo apt-get' command via the terminal, I am able to both, start the application by clicking on the respective icon, or by accessing an image-file through right-click 'open-with...ImageJ'.
So far, so good...
                           
Unfortunately quite a lot of **the selections in the ImageJ 'user interface' (i.e. the 'menu-bar') and some additional writings are heavily distorted, or have been replaced by irregular black bars**. (I tried to do screen-shots using both, key-shortcuts, or the 'screenshot'application, but neither runs while I am actually inside this menus.)

I tried to make sure to get an updated version using the following commands: 'sudo apt-get update && sudo apt-get upgrade', which seemed to work - at least I didn't get a single error message...
Because the problem persisted I suspected an **issue with the Linux driver for my Intel HD 5500 graphics card (?)**, which is not displayed under the 'Software & Updates' > 'Additional Drivers' > 'Proprietary Drivers' panel (neither did I find any clue in the Ubuntu-Software-Manager after enabling 'Universe' and 'Proprietary' repositories).
Therefore I went to the intel homepage to try and find the respective Linux-compatible driver manually. The manufacturer re-directed my to the following website [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads) from where I downloaded and ran [Graphics Installer 1.2.1 for Ubuntu* 15.10, 64-bit]("https://download.01.org/gfx/ubuntu/15.10/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.2.1-0intel2_amd64.deb") which apparently tried to read out my system and automatically get me the latest appropriate driver:
[...] Performing diagnostics [...] 
Checking if Intel graphics card available... OK
Retrieving information from 01.org... OK
Checking distribution... OK
Checking kernel version... OK
Checking available repositories... OK
Checking package manager status... OK

[I hit the 'Next'/'Install' button]

[...] Upgrading components [...]
Ensuring consistent system... OK
Listing packages... OK
Setting up repositories... OK
Installing packages...
**Updating package cache... Failed**



...so therefore I am somehow stuck here... for whatever reason...


Interestingly I noticed, since the latest update of the Ubuntu-GNOME OS [this morning] that sometimes [but only sometimes after multiple times of opening and closing] the entries in the ImageJ user interface are miraculously displayed correctly... how can I make that happen consistently?

I am open for any suggestions regarding either, how to get the proprietary driver for my intel graphics card properly installed, or, how to get rid of those glitches with ImageJ. :)
[I am also having issues to launch the 'Utopia Documents reader' (scientific .pdf reader), I got from the Ubuntu Software center, but I suppose I should open a separate thread for this purpose?]

Thanks in advance!


# Update [2015.12.12] - I ran the 'sudo apt-get upgrade' command line which seemed to have solved an internal issue; I was able to run the intel program just to determine that the newest graphic cards driver has already been installed. The issue withe the ImageJ graphics glitch still persists.

---

### Post by blm-ubunet on 2015-12-11
There is no proprietary driver for the intel GPU. The Intel driver is FOSS..

Before running "apt-get upgrade" one would normally run
```
sudo apt-get update
```
to refresh the package database cache.

Your ubuntu version should have very recent kernel etc.

If this screen menu corruption only affects one specific application I would not suspect the video driver 2d acceleration etc. More likely the GUI "toolkit" library the app is using.

---

### Post by schwobi on 2015-12-12
Thank You for Your response.

> **blm-ubunet said:**
>  Before running "apt-get upgrade" one would normally run
```
sudo apt-get update
```
to refresh the package database cache.

Your ubuntu version should have very recent kernel etc. 

I did indeed run ```
sudo apt-get update && sudo apt-get upgrade
```.
Therefore the cache should have been up to date...?
Just to make sure, I also ran both commands independently ```
sudo apt-get update
```, followed by ```
sudo apt-get upgrade
```, but the glitch persists.

> If this screen menu corruption only affects one specific application I would not suspect the video driver 2d acceleration etc. More likely the GUI "toolkit" library the app is using.

Yes, as far as I recognized, only the ImageJ application seems to be affected. Searching both, this forum and the web, I did not find people reporting something similar - therefore I argued it would like have something to do with my personal hardware/driver setup...

Independently - do You have any suggestions of how to solve this issue?

---

### Post by blm-ubunet on 2015-12-12
Impressive s/w project (ImageJ) & author..

ImageJ has dependency on the java runtime default-jre or openjdk-7-jre.
The menus render fine with Ubuntu 14.04 & old intel atom h/w.

Assuming that the display glitches are caused by interaction between GTK2 "toolkit" & the direct rendering manager..
It is possible that disabling some 2d acceleration features (SNA etc) of your intel GPU might fix /workaround bugs in the GTK2? toolkit.
There is a program "driconf" that can be used to disable diff aspects of the intel driver DRI. This program is not widely recommended & could be too out-dated so YMMV.

---

