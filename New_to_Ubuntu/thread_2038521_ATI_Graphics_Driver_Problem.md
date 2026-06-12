---
title: "ATI Graphics Driver Problem"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by ub07 on 2012-08-06
I am running Ubuntu 12.04 32-bit on a Toshiba Satellite-L355D laptop with an AMD Athlon X2 dual core processor. I have 2 Mb of RAM and a 150 Gb hard drive. I do not dual boot. Mostly I've been having fun with Ubuntu until lately when things began to fall apart on this computer.

I installed Gnome shell about a month ago and all was pretty much ok except my CPU temperature would occasionally make big excursions and the computer would shut down once it got close to 100 degrees C. Ordinarily it operates between 55 and 75 degrees C. (Yes, it has been cleaned out.) I thought that maybe the problem was the graphics driver and I checked for a proprietary driver and indeed I found one (ATI/AMD proprietary FGLRX graphics driver). I installed it and that's when my problems began.

The machine is now very slow and sluggish. TOP reports high CPU use (approximately 80-90% and higher in both cores)  by Gnome shell and xorg. Additionally, when I ran Gnome before installing the ATI driver, the system was using approximately 400 Mb of memory. Now it is using over 1 Gb.

There is a post-release update to the ATI driver, but it fails to install. I can't even tell if the ATI driver is still installed because the “Additional Drivers” show it still gray and says that no proprietary drivers are installed on my system. However, the Catalyst Control Center seems to work in changing display parameters. 

Is there any way to tell if the driver is installed and installed correctly? What can I do about the sluggishness, CPU burden, and memory use that didn't used to be there?

Thanks.

---

### Post by QIII on 2012-08-06
Did you install the driver using the "Additional Drivers" graphical method?

That sometimes does not work well.  The post release updates version also can cause problems.

Does this machine have hybrid Intel/ATI or dual ATI/ATI graphics, by chance?

---

### Post by ub07 on 2012-08-06
> **QIII said:**
> Did you install the driver using the "Additional Drivers" graphical method?

That sometimes does not work well.  The post release updates version also can cause problems.

Does this machine have hybrid Intel/ATI or dual ATI/ATI graphics, by chance?

Yes, I installed the driver using the "Additional Drivers" graphical method.

I don't think that the graphics are hybrid or dual. Looking at the specs I found online it says the graphics are ATI Radeon 3100.

---

### Post by z3nhakr on 2012-08-06
if you want to check what drivers are in use run this:
```
lshw -c video
```
 it should show your video hardware with vendor ids and the name of the driver in use.
also i would recommend trying a benchmarking utility. "glxgears" is a good place to start but you could also try something like "glmark2-es2". check and see if the heat increases, check your frame rate and compare it to what other people are getting. with glxgears i get a little more than 1500 fps with my 1gb radeon card. And also find an application that will challenge your graphics card e.g. a game of sorts and see if your cpu  load increases significantly when your graphics card is stressed. post what you find on the forums and it will help us to find a cure ;)

---

### Post by ub07 on 2012-08-06
> **z3nhakr said:**
> if you want to check what drivers are in use run this:
```
lshw -c video
```
 it should show your video hardware with vendor ids and the name of the driver in use.


Thanks. Here is the result of lishw -c video:

```
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RS780MC [Mobility Radeon HD 3100 Graphics]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:80000000-8fffffff ioport:6000(size=256) memory:96300000-9630ffff memory:96200000-962fffff

```

I will check out those benchmarking programs.

---

### Post by QIII on 2012-08-07
I would recommend trying to reinstall the driver using the terminal.

In the ATI driver wiki in my signature, please see the table of contents  and click on "Using the Ubuntu repositories (alternate command line  method, including hardware acceleration)"

For the moment, skip step 8.  You can do that later.

The section after that details how to install the latest driver by  making a .deb file.  That might be something you will want to look in to  later, but I'd say not to attempt that now.

z3nhakr had good results getting his hybrid graphics to work by simply downloading and running the .run file downloaded from the AMD website.  I've toyed with adding that to the wiki and I think I will now.

Anyway...

What you will get doing it from the terminal is the 12.4 driver.  Not the latest, but it has been well tested.  Installing from the command line works better for some users than the "Additional Drivers" method, but I can't guarantee that will be your case.

But we can at least try that and explore further.

---

### Post by ub07 on 2012-08-07
Thanks, QIII. Do I need to try to uninstall the previous installation?

Edit: Oops, sorry. I see it's in the WIKI.

---

### Post by GreatDanton on 2012-08-07
Yes.

Follow the instructions and hopefully it will work.

Regards.

---

### Post by ub07 on 2012-08-07
> **QIII said:**
> I would recommend trying to reinstall the driver using the terminal.

In the ATI driver wiki in my signature, please see the table of contents  and click on "Using the Ubuntu repositories (alternate command line  method, including hardware acceleration)"

For the moment, skip step 8.  You can do that later.

The section after that details how to install the latest driver by  making a .deb file.  That might be something you will want to look in to  later, but I'd say not to attempt that now.

z3nhakr had good results getting his hybrid graphics to work by simply downloading and running the .run file downloaded from the AMD website.  I've toyed with adding that to the wiki and I think I will now.

Anyway...

What you will get doing it from the terminal is the 12.4 driver.  Not the latest, but it has been well tested.  Installing from the command line works better for some users than the "Additional Drivers" method, but I can't guarantee that will be your case.

But we can at least try that and explore further.

I installed the driver (skipping Step 8 ) and I didn't get any errors during the installation process. However, I lost Gnome 3. Now when I log on to Gnome, it looks like Gnome Classic.

How do I get Gnome 3 back?

---

### Post by NikTh on 2012-08-07
Hi , 
please open a terminal and  post the output of 
```
/usr/lib/nux/unity_support_test -p
lspci -nnk | grep -iA2 vga
```                                  Put the results inside [CODE] tags by highlighting the output and then click on the  [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button in the message toolbar.
  Thanks

---

### Post by ub07 on 2012-08-07
Hi, NikTh. Here are the results:

```
jeo@jeo-Satellite-L355D:~$ /usr/lib/nux/unity_support_test -p
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  138 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  23
  Current serial number in output stream:  23
jeo@jeo-Satellite-L355D:~$ lspci -nnk | grep -iA2 vga
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS780MC [Mobility Radeon HD 3100 Graphics] [1002:9613]
	Subsystem: Toshiba America Info Systems Device [1179:ff6a]
	Kernel modules: radeon
jeo@jeo-Satellite-L355D:~$ 

```

---

### Post by NikTh on 2012-08-08
Hi , 
you hadn't install fglrx driver for AMD/ATI , or installed incorrectly. 

Please open a terminal and run below command.
```
 sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```this command will remove-purge fglrx driver permanent.It will remove config files too.
There have been reports that also removes critical packages so after above command give below commands
```
sudo apt-get install --reinstall libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```and ```
sudo dpkg-reconfigure xserver-xorg xserver-xorg-core xserver-xorg-video-ati
```reboot your computer and again , give the results of 
```
lspci -nnk | grep -iA2 vga
/usr/lib/nux/unity_support_test -p
```Thanks

---

### Post by ub07 on 2012-08-08
NikTh,

I ran the commands you suggested and almost got Gnome Shell back, but it hung on log in after it displayed the Gnome 3 desktop, and I had to forcibly shut the computer down. Here is the output you requested:

```
jeo@jeo-Satellite-L355D:~$ lspci -nnk | grep -iA2 vga
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS780MC [Mobility Radeon HD 3100 Graphics] [1002:9613]
	Subsystem: Toshiba America Info Systems Device [1179:ff6a]
	Kernel driver in use: radeon
jeo@jeo-Satellite-L355D:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD RS780
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

Thanks for your help!

---

### Post by NikTh on 2012-08-08
Hi , 
Ok we are now to an original position . (As when Ubuntu installed). 

Now you can try to install fglrx again with below commands 
```
sudo apt-get install fglrx fglrx-amdcccle
```When installation finish , reboot your pc and see if Gnome works well. 

If above command returns errors , post them here. 
Thanks

---

### Post by QIII on 2012-08-08
Typo there...

"amdccclete" is a typo on askubuntu.  Use "amdcccle".

Also, be sure to do

```
sudo aticonfig --initial
```

before rebooting since you renamed it previously.  A new xorg.conf is generally supposed to be generated by the install, but don't depend on that.

Also note that unless it has been fixed recently, GNOME 3 running with the fglrx driver may exhibit some artifacts in the top panel.

---

### Post by ub07 on 2012-08-08
Thanks, guys, you are absolute life savers! I've got my Gnome shell back and also my system is no longer sluggish! Thanks again!

I have one question though: How do I check that the it is the proprietary driver that I am using?

---

### Post by QIII on 2012-08-08
```
fglrxinfo
```should return something like

```
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc. 
OpenGL renderer string: AMD Radeon HD 6300M Series 
OpenGL version string: 4.2.11733 Compatibility Profile Context
```

---

### Post by NikTh on 2012-08-08
> **ub07 said:**
> 

I have one question though: How do I check that the it is the proprietary driver that I am using?

Hi , 
another option might be 
```
 lspci -nnk | grep -iA2 vga 
```
It should return something like this
```

01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS780MC [Mobility Radeon HD 3100 Graphics] [1002:9613]     
Subsystem: Toshiba America Info Systems Device [1179:ff6a]     
**Kernel driver in use: fglrx**
```Thanks

---

### Post by ub07 on 2012-08-08
Thanks, guys. It looks like it installed. 

Unfortunately, I think maybe I spoke too soon when I called this thread solved. I'm getting funny playback of videos - the timing is off like frame-by-frame slow motion. It is definitely noticeable. I didn't have this problem when I first installed Ubuntu so maybe it would be better to go back to the open-source driver?

The pci adapter is still getting very hot whenever I put the system under stress (like playing a video).

```
jeo@jeo-Satellite-L355D:~$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon 3100 Graphics 
OpenGL version string: 3.3.11627 Compatibility Profile Context
jeo@jeo-Satellite-L355D:~$ lspci -nnk | grep -iA2 vga
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS780MC [Mobility Radeon HD 3100 Graphics] [1002:9613]
	Subsystem: Toshiba America Info Systems Device [1179:ff6a]
	Kernel driver in use: fglrx_pci


```

---

### Post by ub07 on 2012-08-09
I ran the commands in NikTh's post (Post 12) and put the open source driver back. It just seems to work much better. No problem with video and it is less of a burden on the CPU. Gnome Shell came back when I rebooted for the second time.

The pci adapter temperature with the open source driver is about 10 degrees C less than with the proprietary driver. However, the temperature is less stable, and it will increase a LOT for seemingly no reason. I'm not sure this is related to the graphics driver. I might start an independent thread about it because overheating is my main concern (along with having a usable computer). I never really had a problem with overheating in Windows Vista.

Thanks NikTh and QIII for all your help.

---

### Post by QIII on 2012-08-09
The problem might be that graphics acceleration was not installed and decoding was dumped on your CPU.  ATI's Linux hardware acceleration is not as full featured as nVIDIA's but H.264 does work.

It might be worth another go and enabling hardware acceleration.

I just got done making some changes to the wiki and moved the hardware acceleration to its own section, so now you will see "Using the Ubuntu repositories (alternate command line method)" and "Enabling Hardware Acceleration" as two separate sections.

---

### Post by ub07 on 2012-08-09
Ok, I'll give it one more try tomorrow and see how it goes. As long as I can get back to where I am now, I'm willing to try anything.

Thanks.

---

### Post by NikTh on 2012-08-09
> **ub07 said:**
> 
The pci adapter temperature with the open source driver is about 10 degrees C less than with the proprietary driver. However, the temperature is less stable, and it will increase a LOT for seemingly no reason. I'm not sure this is related to the graphics driver.

Hi , 
_If you still have the Open source driver (radeon)_, then follow this: 

please open a terminal and run these commands. ```

sensors
sudo echo low >  /sys/class/drm/card0/device/power_profile
```Keep an eye on temperature. Is it lower ? 
Run again ```
sensors
``` after 10-15 secs , and see. 
Above command is temporally and will not apply if you reboot your PC. 
If works well , we can make it permanent. 
Thanks

---

### Post by QIII on 2012-08-09
You can get the temperature directly from the card itself if you still have the driver installed

```
aticonfig --od-gettemperature
```

---

### Post by NikTh on 2012-08-09
> **QIII said:**
> You can get the temperature directly from the card itself if you still have the driver installed

> **ub07 said:**
> I ran the commands in NikTh's post (Post 12) and  put the open source driver back. It just seems to work much better. No  problem with video and it is less of a burden on the CPU. Gnome Shell  came back when I rebooted for the second time.

I assume the fglrx is uninstalled.

---

### Post by QIII on 2012-08-09
Unless, as he said he would try, he has reinstalled it to see what happens if he enables hardware acceleration.  ;)

---

### Post by NikTh on 2012-08-09
> **QIII said:**
> Unless, as he said he would try, he has reinstalled it to see what happens if he enables hardware acceleration.  ;)
Hi,
Yes. You have right. Now I must edit my post one more time :p 
Thanks

---

### Post by ub07 on 2012-08-09
I use psensor to get a graph of my temperature sensors. Ok, I'm going to give it a try now.

---

### Post by ub07 on 2012-08-09
I enabled acceleration as described in the Wiki, but the problem with video is still there. Also, I'm indeed running hotter than with the open source driver.

Unless you guys have any other ideas, I'm going to go back to the opensource driver and will try NikTh's suggestion to try to get it to run less hot. I'll keep you posted.

---

### Post by ub07 on 2012-08-10
I put back the opensource driver. For some reason, it just works much better with less freezing and halting than the proprietary driver.

Also, I ran this command:

```
sudo echo low >  /sys/class/drm/card0/device/power_profile
```

as NikTh suggested earlier.

Indeed, it does make a difference. The pci temperature runs about 5 degrees C cooler, but more importantly it is stable. I ran the computer all evening without rebooting and pushed it by running two videos simultaneously, having a browser open, and doing updates. There were no large excursions in temperature and the maximum temperature was 15 degrees C less than yesterday without the fix.

So, yes, I'd like to make it permanent.

Thanks.

---

### Post by NikTh on 2012-08-10
> **ub07 said:**
> I put back the opensource driver. For some reason, it just works much better with less freezing and halting than the proprietary driver.

Also, I ran this command:

```
sudo echo low >  /sys/class/drm/card0/device/power_profile
```as NikTh suggested earlier.

Indeed, it does make a difference. The pci temperature runs about 5 degrees C cooler, but more importantly it is stable. I ran the computer all evening without rebooting and pushed it by running two videos simultaneously, having a browser open, and doing updates. There were no large excursions in temperature and the maximum temperature was 15 degrees C less than yesterday without the fix.

So, yes, I'd like to make it permanent.

Thanks.

Hi , 
glad it meet your needs. 

Open a terminal and ```
gksudo gedit /etc/rc.local 
``` add this command _before **exit 0**_
```
echo low >  /sys/class/drm/card0/device/power_profile
``` without sudo. No need for sudo when you add something in rc.local. 

Save the document and on next reboot you will be fine. 
To check if command works , open a terminal and run this command
```
cat /sys/class/drm/card0/device/power_profile
``` 
it must returns ```
low
```
Thanks.

---

### Post by ub07 on 2012-08-10
Thank you, NikTh. You are awesome!

---

