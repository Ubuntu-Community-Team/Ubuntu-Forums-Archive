---
title: "Dual Monitor Display/Menu Behavior"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by strickja on 2012-12-18
I am very new to lubuntu - successful clean install of amd64 version on fuji turion 64x2 radeon 1150 4GB laptop

Very quick, very pleased except for dual display difficulties

using arandr have gotten two monitors working (with a little work) but the strange thing is when i open say abiword on vga monitor, and click a menu selection like format, the menu appears on the other monitor.  chrome, and all other apps and context menus to the same.  on the laptop mon, all is well; if i mirror, all is well; games etc perform fine on laptop and/or mirror 

xrandr returns 
Screen 0: minimum 320 x 200, current 2048 x 768, maximum 4096 x 4096
VGA-0 disconnected 1024x768+1024+0 (normal left inverted right x axis y axis) 0mm x 0mm
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9* 
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)
  1024x768 (0x55)   65.0MHz
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0H 

I have searched and found numerous threads that seem relevant, but my limited experience make it impossible to figure out what I should do.

lubuntu is current and have installed 3rd party driver package.

I would simply like to run 1280x800 on both monitors - any and all help would be very appreciated

---

### Post by audiomick on 2012-12-18
Just so you know it is not neccessarily broken, some programs do that on my 11.10 install. It is a desktop with a dual head nVidia card and two identical 21" monitors. I haven't given it a second thought, to be quite honest.

---

### Post by strickja on 2012-12-18
Thanks for the reply; its a case of being so close to having a functional working env that its frustrating;  I have been able to get everything else i wanted to do working , its just this dual monitor issue, which I have to believe is a driver issue, and I can't find a solution;  I want to switch to ubuntu on a few diff machine setups, but i can't do so until i confirm a few working configs - while i appreciate the blazing speed compared to windows, I am surprised something as normal as a dual mon cfg is so troublesome - thank you for the link to the other forum, will be posting there as well

---

### Post by dannyboy79 on 2012-12-18
what graphics card and driver are you using?

---

### Post by audiomick on 2012-12-18
> **dannyboy79 said:**
> what graphics card and driver are you using?

good question.
Do
```
sudo lshw -C video
```

if you're not sure exactly.

---

### Post by strickja on 2012-12-18
It a Fuji laptop, windows shows an 1150 for the video driver 

*-display               
       description: VGA compatible controller
       product: RS482 [Radeon Xpress 200M]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64 mingnt=8
       resources: irq:17 memory:d8000000-dfffffff ioport:c000(size=256) memory:fbff0000-fbffffff memory:fbfc0000-fbfdffff

Thank you for assistance

---

### Post by audiomick on 2012-12-18
Perhaps this might help
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by strickja on 2012-12-18
bit to digest there, thank you I will work through it and post results

thanks for the direction

---

### Post by dannyboy79 on 2012-12-18
> **audiomick said:**
> Perhaps this might help
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")according to that page, that driver has better dual-head support. I don't think that graphics card can power 3 displays which would make sence when you try to enable 3, it gets all screwy according to you.

Good luck either way

---

### Post by strickja on 2012-12-18
only trying to use two monitor, lcd on laptop and an external toshiba flat screen vga; 

have removed the fglrx , but cannot seem to get the ati driver installed; have downloaed the tar file , extracted, tried to execute autoconf.sh but cannot get confirmation it loads a driver; more of my ignorance i am sure;

i have confirmed that the card should be supported; any other guidance would be appreciated as always

---

### Post by strickja on 2012-12-18
the driver is using KMS (see below) but ligbl seems to be missing a file .drirc 

the dual mode config still returns the bizarre menu behavior 

oddly xrandr says the vga is disconnected, but it is showing on the monitor 
xrandr
Screen 0: minimum 320 x 200, current 2304 x 800, maximum 4096 x 4096
VGA-0 disconnected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
LVDS connected 1280x800+1024+0 (normal left inverted right x axis y axis) 0mm x 0mm


strickja@strickja-LifeBook:~$ dmesg |grep drm
[   10.032877] [drm] Initialized drm 1.1.0 20060810
[   11.220652] [drm] radeon defaulting to kernel modesetting.
[   11.220657] [drm] radeon kernel modesetting enabled.
[   11.221125] [drm] initializing kernel modesetting (RS480 0x1002:0x5975 0x10CF:0x13B8).

 LIBGL_DEBUG=verbose glxinfo
name of display: :0
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/r300_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/r300_dri.so
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/strickja/.drirc: No such file or directory.
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/strickja/.drirc: No such file or directory.
display: :0  screen: 0
direct rendering: Yes

---

### Post by strickja on 2012-12-18
After having been through all the steps so far, I have gotten to a point where I don't think its the driver;  I have successfully manipulated all aspects of both displays from a term with xrandr and it responds as it should, so now the only issue is the menu problem, which I guess is a window manager issue, so off to post a new thread i guess - thanks for assistance from those who contributed

---

### Post by strickja on 2012-12-18
just as follow up, i did the same configuration with a different laptop using an intel chip set and it worked first time and flawlessly, so now i am back to the radeon 1150 as the culprit.  any ideas would be appreciated.

---

