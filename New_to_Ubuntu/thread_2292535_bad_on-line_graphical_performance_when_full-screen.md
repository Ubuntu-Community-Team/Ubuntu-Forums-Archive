---
title: "bad on-line graphical performance when full-screen (display UNCLAIMED for Nvidia)"
date: 2015-08-28
forum: New to Ubuntu
---

### Post by jgervais89 on 2015-08-28
Hi there,  

 I have been using Ubuntu 14.04 (LTS) on two different computers: a dell laptop (AMD inspiron) and a XPS 27 (all-in-one; integrated intel card and a nvidia card).  
 
 Now, with both computers, when I watch videos in full-sceen, on-line,  there is a bad performance. I found another post here: ([http://askubuntu.com/questions/635901/chromium-bad-html5-flash-video-performance](http://askubuntu.com/questions/635901/chromium-bad-html5-flash-video-performance)) where an user has provided pictures of the problem (it is the same for me). You can see somehow horizontal lines that are “out of sync”.  Moreover, this problem seems to be true only/mostly with chrome, chromnium and Iron browser; it seems to be fine with Firefox or when I watch a video found on YouTube with youtube-ql.  

 Now, if it was just for YouTube, I could easily live with that, by using FireFox. Unfortunately, I watch a lot of Netflix videos, and I can't use it with FireFox.  
 
My impression is that the problem is related to chrome itself, since the result is the same on two completely different computers. I tried the  proposed solution, but it didn't work for me.  

Does anyone as a way to deal with this (more particularly with chrome-stable)?  
 
Thank you.

---

### Post by yetimon_64 on 2015-08-29
> Now, with both computers, when I watch videos in full-sceen, on-line,  there is a bad performance.

Ubuntu usually installs nouveau drivers (open source) by default on any installation.
**Question:** Have you installed the proprietary drivers for the AMD card (fglrx) on the Inspiron and for the Nvidia card (nvidia) on the XPS27 ?

Some commands are posted below that can show what you have installed, you may need to install lshw and inxi; the lspci command is standard in Ubuntu iirc.

_*If*_ you need to install lshw and/or inxi, open a terminal (ctrl + alt + t key combination in unity gives a terminal) then copy/paste the following code boxes to the terminal and press "enter" ...
```
sudo apt-get install lshw
```
```
 sudo apt-get install inxi
```


_*To see what you have installed*_ ...
```
sudo lspci | grep VGA
```
```
sudo lshw -c video
```
```
inxi -G
```

As an example, output from my hybrid graphics laptop (HP envy 17) are below to give you an idea where to look ... > ```
yetiman@********:~$ sudo lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
yetiman@********:~$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:66 memory:c3000000-c3ffffff memory:d0000000-dfffffff ioport:6000(size=64)
  *-display
       description: 3D controller
       product: GM107M [GeForce GTX 850M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:0a:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: **driver=nvidia** latency=0
       resources: irq:71 memory:c4000000-c4ffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:3000(size=128)
yetiman@********:~$ inxi -G
Graphics:  Card: Intel Broadwell-U Integrated Graphics 
           X.Org: 1.16.0 drivers: **nvidia**,intel Resolution: 1920x1080@60.0hz, 1920x1080@60.0hz 
           GLX Renderer: GeForce GTX 850M/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 349.16
yetiman@********:~$
```

_*If*_ your results read as "nouveau" where I have bolded the "nvidia", instead of "fglrx" on the AMD card and "nvidia" on the Integrated/hybrid nvidia card, you may need to install the proprietary drivers to get improved performance. 

I found that installing the proprietary drivers, and specifically for an nvidia card set the "prime" settings to "nvidia" with the nvidia-settings command (see attached screenshot), gave me much improved video performance. 
I had far worse tearing and loss of sections of the screen display than your link shows when using the nouveau driver along with the intel only settings on these hybrid graphics. 

Post back any terminal results here in between [noparse]```

```[/noparse] tags for readability if you need help understanding the output. Note: the asterisks in my output are only me deliberately masking my hostname of this install when posting on a public forum etc. 

Regards, yeti.

---

### Post by jgervais89 on 2015-08-29
Thank you. For the Inspiron, no, I didn't install the proprietary driver. I think it will be better to start with the XPS 27 machine, since I think I'll be to complicated to handle two devices at the same time ... 


For the XPS 27, well, I installed Bumblebee, and when I look for addition drivers, I see that I am using NVIDIA legacy binary driver - version 304.125 from nvidia-304 (proprietary). But, using your codes, I think that it is possible that something is not ok. 

 With the sudo lspci | grep VGA:

```
                         
00:02.0 VGA compatible controller: [COLOR=#800000]Intel Corporation [/COLOR]Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)                                                                               

01:00.0 VGA compatible controller: [COLOR=#800000]NVIDIA Corporation[/COLOR] GK107M [GeForce GT 640M] (rev a1) 

```

With the sudo lshw -c video :  
```
                
*-display [COLOR=#800000]UNCLAIMED    [/COLOR]  
        description: VGA compatible controller 
        product: GK107M [GeForce GT 640M] 
        vendor: NVIDIA Corporation 
        physical id: 0 
        bus info: pci@0000:01:00.0 
        version: a1 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress vga_controller cap_list 
       [COLOR=#800000] configuration: latency=0 [/COLOR]
        resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff 
   *-display 
        description: VGA compatible controller 
        product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller 
        vendor: Intel Corporation 
        physical id: 2 
        bus info: pci@0000:00:02.0 
        version: 09 
        width: 64 bits 
        clock: 33MHz 
        capabilities: msi pm vga_controller bus_master cap_list rom 
        [COLOR=#800000]configuration: driver=i915 latency=0 [/COLOR]
        resources: irq:39 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)
```
                        
With the inxi -G:

  
```
   
Card-1: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller  
Card-2: NVIDIA GK107M [GeForce GT 640M] X.Org: 1.17.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 2560x1440@60.0hz  
 GLX Renderer: Mesa DRI Intel Ivybridge Desktop GLX Version: 3.0 Mesa 10.5.2 

```

I also used the                                                                    sudo update-alternatives --config x86_64-linux-gnu_gl_conf :

```
    Selection    Path                                       Priority   Status 
 ------------------------------------------------------------ 
   0            /usr/lib/nvidia-304/ld.so.conf              9701      auto mode 
   1            /usr/lib/nvidia-304/ld.so.conf              9701      manual mode 
 * 2            /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf   500       manual mode 



```

  
   I also open the NVIDIA X Server Settings. However, I only have to option: Application Profiles and nvidia-settings Configuration.

Sorry, I know that this is pretty dry, but I don't use Ubuntu (and Linux) since a long time, and I don't really know what to do with all this information.

Thank you for your time.

---

### Post by yetimon_64 on 2015-08-29
> I installed Bumblebee That is something I didn't install at all with my machine, I just added the xorg edgers ppa to get the nvidia drivers to show in the additional drivers utility then activated the 349 driver and everything worked.

I do have a different intel card (Broadwell-U) to your Xeon. I would suggest you wait for further advice from someone with your specific hardware as the procedure for setting up that card may differ from mine. I am unfamiliar with your set up and whether or not adding the xorg edgers ppa will be of any use to you. You mention that you are "using NVIDIA legacy binary driver" whereas I had absolutely NO drivers listed at all and had to add the xorg edgers ppa to get any drivers listed.

Are there any other higher numbered drivers listed as well as the 304 driver you noted ? If the 346 or 349 driver is listed it may pay you to try one of them, otherwise the xorg edgers ppa may be needed to supply them. Your nvidia card is pretty newish (GeForce GT 640M) so I suspect a later nvidia driver may suit better than the 304 driver but don't know for certain with your hardware.

> But, using your codes, I think that it is possible that something is not ok. 
Seeing the "UNCLAIMED" status of your nvidia card and no driver listed as used by it does indicate to me you need to fix something with your install as well. 

Good luck, I hope someone who knows your set up requirements pops in soon to help you. Regards, yeti.

---

### Post by jgervais89 on 2015-08-29
Thank you very much for your help. I just want to add that I installed  Bumblebee using codes from another user who uses the same computer:


```
sudo add-apt-repository ppa:bumblebee/stable



```

```
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia
```


```
sudo gedit /etc/bumblebee/bumblebee.conf
```

and then :

> 1) **Replace** 
   Driver= 
   **by** 
   Driver=nvidia

2) **Replace** 
   KernelDriver=nvidia-current 
   **by** 
   KernelDriver=nvidia

Then reboot, and you should be fine for optirun.

Hope this can help to find a solution to my problem.


EDIT: Just want to add that I run the following code : sudo ubuntu-drivers devices

```
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd00000FD2sv00001028sd0000054Bbc03sc00i00
model    : GK107M [GeForce GT 640M]
driver   : nvidia-340-updates - distro non-free
_**driver   : nvidia-346 - distro non-free recommended**_
driver   : nvidia-304 - distro non-free
driver   : nvidia-340 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-304-updates - distro non-free
driver   : nvidia-346-updates - distro non-free

```

If I go to the additional drivers, I got several options. I'll put them into attachment.

---

### Post by yetimon_64 on 2015-08-29
I just noted your edit; you do have the 346 driver available and it is the recommended one going by your ubuntu-drivers command output (I didn't even know that command existed ;)). I'd suggest you try activating it in Additional Drivers and rerun the lshw command and see if it changes the unclaimed status. You might get lucky with that, as I suggested in my last post the GeForce GT 640M is a fairly recent card, worth a try :).

With this GeForce GTX 850M and the xorg edgers ppa I have 3 options, the 340, 346 and 349 driver. I first tried the 340 and it was pretty bad, the 346 worked ok, I then read of someone else using the 349 driver on a similar set up so I tested it and it is working perfect for this install. Hopefully your problem is a simple wrong driver issue only, good luck.

---

### Post by jgervais89 on 2015-08-29
> I'd suggest you try activating it in Additional Drivers When I change it, it returns to the 304 driver. Does it mean that I have to do something before I can make the change and choose the 346 ? 

Here: ([https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)), they are saying to do the following code (for nvidia 331) :

```
sudo apt-get install nvidia-331
```

Do I have to do this first? I'm always insecure when playing with nvidia settings, I had some bad black screen experiences ... 

Thank you for your help!

---

### Post by yetimon_64 on 2015-08-29
> When I change it, it returns to the 304 driverHmm, that doesn't sound good. 

> Do I have to do this first?  No, usually just selecting it in the Additional Drivers will download and install it.  That apt-get code for the 331 driver is just the terminal command for  what the Additional Driver (the GUI equivalent) runs in the background  as far as I understand the situation. I can understand you being insecure if you are not too experienced with nvidia drivers, those black screens aren't nice. Something is definitely amiss here if the recommended driver won't install.

> Thank you for your help!You're welcome. As I not so familiar with the Xeon and the Additional Drivers is sticking on the 304 driver I am at a bit of a loss as to what is exactly happening. Wait for further advice from other helpers with this one. Cheers.

---

### Post by jgervais89 on 2015-08-30
Just want to add that, after rebooting, it changes to the 346 driver, and seems to stay with it.  However, the display unclaimed is still present (so is the graphical problems); I guess the problem is to find a way to make it active ...

---

