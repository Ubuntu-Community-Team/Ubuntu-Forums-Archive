---
title: "Graphics issues even after fresh 20.04 install"
date: 2021-04-18
forum: New to Ubuntu
---

### Post by guybutterworth on 2021-04-18
Hey everybody, I'm struggling to resolve what seems to be a graphics problem. It started a few days ago, and I've done a fresh install to see if that resolves it, but I'm still having issues. 

I'm not really sure how to describe what I'm seeing, and I'm having trouble attaching a short video/gif to show it. Basically in Firefox text and images appear and disappear, and text changes into what looks like wingdings, and then changes back. The other day Zoom froze completely in a call, although the sound continued to work fine.

If any of the above sounds familiar and you have a fix, I'd really appreciate it.

---

### Post by CelticWarrior on 2021-04-18
Welcome.

Please post hardware specifications, particularly graphics.

---

### Post by mastablasta on 2021-04-18
publish video on you tube, make it view with link only and post the link. though maybe you cant' post links since you are new.

garbled image with text items could mean GPU is failing. does it go green or black when it does that? another thing it could happen is overheating.

psensor can show the temperature in nice format. if it fails when hot, then you could try to clean it from dust using compressed air. make sure the fans spin well.
phoronix test suite can strain the card with one of it's tests. if it fails under pressure during the test then it is time to change it. but nowadays they are pricy. 

if it's a laptop, then it's a problem.

also make sure correct drivers are installed and card is recognised well. 

```
inxi -Fz 
``` command will give all system info and you can copy it and paste it here. another one that is a bit less nice is but will do fine is
```
lshw -sanitize
```

or there should be a GUI interface that dispalys hardware info (maybe infocenter or something like that - i use Kubuntu so i don't know what is on Ubuntu but we have kinfocenter)

---

### Post by guybutterworth on 2021-04-18
Thank you for taking the time to respond, I appreciate it. I made a short video then thought perhaps I could turn it into a gif, but the gif wound up being more MB than the mp4!

The video is here, hopefully the link will work - [https://youtu.be/Dk7wJHwzpGI](https://youtu.be/Dk7wJHwzpGI)

---

### Post by guybutterworth on 2021-04-18
I can't seem to upload an image of the summary from Ubuntu, but basically it's as follows:

```
Memory - 3.8gb
Processor - Intel Core i5-4200u CPU @ 1.60ghz x 4
Graphics - Intel HD Graphics 4400 (HSW GT2)

```
The machine is about 8 years old!
```

guy@guy-MMLP5AP-00:~$ inxi -Fz
System:
  Kernel: 5.8.0-50-generic x86_64 bits: 64 Desktop: Gnome 3.36.7 
  Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: GIGABYTE product: MMLP5AP-00 v: 1.x serial: <filter> 
  Mobo: GIGABYTE model: MMLP5AP-00 v: 1.x serial: <filter> 
  UEFI: American Megatrends v: F4 date: 12/03/2013 
CPU:
  Topology: Dual Core model: Intel Core i5-4200U bits: 64 type: MT MCP 
  L2 cache: 3072 KiB 
  Speed: 798 MHz min/max: 800/2600 MHz Core speeds (MHz): 1: 805 2: 798 
  3: 801 4: 836 
Graphics:
  Device-1: Intel Haswell-ULT Integrated Graphics driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.9 driver: i915 resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 4400 (HSW GT2) 
  v: 4.5 Mesa 20.2.6 
Audio:
  Device-1: Intel Haswell-ULT HD Audio driver: snd_hda_intel 
  Device-2: Intel 8 Series HD Audio driver: snd_hda_intel 
  Device-3: Logitech OrbiCam type: USB driver: snd-usb-audio,uvcvideo 
  Sound Server: ALSA v: k5.8.0-50-generic 
Network:
  Device-1: Realtek RTL8723AE PCIe Wireless Network Adapter 
  driver: rtl8723ae 
  IF: wlp2s0 state: down mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 111.79 GiB used: 13.94 GiB (12.5%) 
  ID-1: /dev/sda vendor: Crucial model: CT120M500SSD3 size: 111.79 GiB 
Partition:
  ID-1: / size: 105.18 GiB used: 13.93 GiB (13.2%) fs: ext4 dev: /dev/sda6 
Sensors:
  System Temperatures: cpu: 56.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 229 Uptime: 6h 09m Memory: 3.76 GiB used: 2.15 GiB (57.2%) 
  Shell: bash inxi: 3.0.38
```

---

### Post by mastablasta on 2021-04-20
saw it on you tube. this is your GPU chip: [COLOR=#000000][FONT=&quot]Intel HD Graphics 4400
[/FONT][/COLOR]
it uses opensource driver supported &made by Intel which is in kernel.

it look like a display issue. Are you using wayland or xorg? at the login you should be able to chose and try to switch to the old xorg. i also saw something similar at my kids computer, but let's first try the xorg.

---

### Post by guybutterworth on 2021-04-20
Thanks for your reply. I just logged out and logged back in so I could check which of those two I was using, and it looks like I was using Xorg. I've now switched over to Wayland, and things are different, but still basically unusable once the graphics deteriorate past a certain point; stuff disappears, reappears, blocks of colour come and go. It's weird!

---

### Post by Autodave on 2021-04-20
Have yo tried pulling the cover and checking that all fans are clean and functioning?

---

### Post by mastablasta on 2021-04-21
it can be caused by overheating but that one usually freezes or you would see it turn off and back on.

another option really is failing chip or also something with RAM (since this GPU uses computer RAM). to test the ram, memtest is available on Ubuntu boot/install disk. does this happen immediately when you start it up or after some time of usage?

for GPU i don't know hot to test it. i saw similar strange behaviour on Ryzen - for example the widnows won't display properly and this already showed at boot. but that issue is supposed to be only on AMD.and you have Intel.

---

### Post by guybutterworth on 2021-04-21
[INDENT] 					Have yo tried pulling the cover and checking that all fans are clean and functioning? 				[/INDENT] 			
  			   		


Yes I did. There was a surprising amount of dust in there, and it's something that I'll keep an eye on more closely in the future. Unfortunately, the cleaning didn't yield any ongoing benefits in terms of the problem I've been experiencing. But thanks!

---

### Post by guybutterworth on 2021-04-21
> **mastablasta said:**
> it can be caused by overheating but that one usually freezes or you would see it turn off and back on.

another option really is failing chip or also something with RAM (since this GPU uses computer RAM). to test the ram, memtest is available on Ubuntu boot/install disk. does this happen immediately when you start it up or after some time of usage?

for GPU i don't know hot to test it. i saw similar strange behaviour on Ryzen - for example the widnows won't display properly and this already showed at boot. but that issue is supposed to be only on AMD.and you have Intel.

It's deceptive, I think initially that everything is fine, and then as time passes, the graphics become more and more distorted, things get covered in blocks of colour, etc.

---

### Post by wowotiel on 2021-04-21
May be you are struggling with the same problem I have had. After an kernel update from 5.8.0-48 to 5.8.0-49 and 5.8.0-50 I have had a very unstable desktop with graphics problems.
You can temporary try to boot from an older kernel (for instance 5.8.0-48) if this will help (advanced option in the GRUB)
I have older hardware so I do not need the 5.8 kernel series provided from Ubuntu 20.04.2 images.
Ubuntu came in the beginning with kernel 5.4 and that serie is still updated. I eventually went back to the 5.4 serie.
The inxi-Fxz from my hardware:
```
System:
  Kernel: 5.4.0-72-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: Gnome 3.36.7 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:
  Type: Desktop System: Gigabyte product: N/A v: N/A serial: <filter> 
  Mobo: Gigabyte model: H77-DS3H v: x.x serial: <filter> 
  UEFI: American Megatrends v: F10 date: 11/14/2013 
CPU:
  Topology: Quad Core model: Intel Core i7-3770 bits: 64 type: MT MCP 
  arch: Ivy Bridge rev: 9 L2 cache: 8192 KiB 
  flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 54275 
  Speed: 1596 MHz min/max: 1600/3900 MHz Core speeds (MHz): 1: 1597 2: 1597 
  3: 1596 4: 1596 5: 1596 6: 1596 7: 1596 8: 1596 
Graphics:
  Device-1: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics 
  vendor: Gigabyte driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.9 driver: fbdev unloaded: modesetting,vesa 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 4000 (IVB GT2) 
  v: 4.2 Mesa 20.2.6 direct render: Yes 
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition Audio 
  vendor: Gigabyte driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.4.0-72-generic 
Network:
  Device-1: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet vendor: Gigabyte 
  driver: atl1c v: 1.0.1.1-NAPI port: e000 bus ID: 02:00.0 
  IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 1.82 TiB used: 425.03 GiB (22.8%) 
  ID-1: /dev/sda vendor: Samsung model: SSD 860 EVO 1TB size: 931.51 GiB 
  ID-2: /dev/sdb vendor: Seagate model: ST31000524AS size: 931.51 GiB 
Partition:
  ID-1: / size: 915.40 GiB used: 264.30 GiB (28.9%) fs: ext4 dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 29.8 C mobo: 27.8 C 
  Fan Speeds (RPM): cpu: 0 fan-1: 1369 fan-3: 682 fan-4: 784 fan-5: 0 
  Voltages: 12v: N/A 5v: N/A 3.3v: N/A vbat: 3.22 
Info:
  Processes: 288 Uptime: 1h 16m Memory: 15.53 GiB used: 3.08 GiB (19.8%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 clang: 10.0.0-4ubuntu1 
  Shell: bash v: 5.0.17 inxi: 3.0.38
```

---

### Post by guybutterworth on 2021-04-21
I've just gone through the GRUB menu and booted up using an older version of the kernel, and while it might still be too soon to be certain, everything is now functioning perfectly. I've got the webcam on, numerous Firefox tabs open, and it looks like your suggestion has done the trick.

Thanks!



> **wowotiel said:**
> May be you are struggling with the same problem I have had. After an kernel update from 5.8.0-48 to 5.8.0-49 and 5.8.0-50 I have had a very unstable desktop with graphics problems.
You can temporary try to boot from an older kernel (for instance 5.8.0-48) if this will help (advanced option in the GRUB)
I have older hardware so I do not need the 5.8 kernel series provided from Ubuntu 20.04.2 images.
Ubuntu came in the beginning with kernel 5.4 and that serie is still updated. I eventually went back to the 5.4 serie.
The inxi-Fxz from my hardware:
```
System:
  Kernel: 5.4.0-72-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: Gnome 3.36.7 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:
  Type: Desktop System: Gigabyte product: N/A v: N/A serial: <filter> 
  Mobo: Gigabyte model: H77-DS3H v: x.x serial: <filter> 
  UEFI: American Megatrends v: F10 date: 11/14/2013 
CPU:
  Topology: Quad Core model: Intel Core i7-3770 bits: 64 type: MT MCP 
  arch: Ivy Bridge rev: 9 L2 cache: 8192 KiB 
  flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 54275 
  Speed: 1596 MHz min/max: 1600/3900 MHz Core speeds (MHz): 1: 1597 2: 1597 
  3: 1596 4: 1596 5: 1596 6: 1596 7: 1596 8: 1596 
Graphics:
  Device-1: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics 
  vendor: Gigabyte driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.9 driver: fbdev unloaded: modesetting,vesa 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 4000 (IVB GT2) 
  v: 4.2 Mesa 20.2.6 direct render: Yes 
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition Audio 
  vendor: Gigabyte driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.4.0-72-generic 
Network:
  Device-1: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet vendor: Gigabyte 
  driver: atl1c v: 1.0.1.1-NAPI port: e000 bus ID: 02:00.0 
  IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 1.82 TiB used: 425.03 GiB (22.8%) 
  ID-1: /dev/sda vendor: Samsung model: SSD 860 EVO 1TB size: 931.51 GiB 
  ID-2: /dev/sdb vendor: Seagate model: ST31000524AS size: 931.51 GiB 
Partition:
  ID-1: / size: 915.40 GiB used: 264.30 GiB (28.9%) fs: ext4 dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 29.8 C mobo: 27.8 C 
  Fan Speeds (RPM): cpu: 0 fan-1: 1369 fan-3: 682 fan-4: 784 fan-5: 0 
  Voltages: 12v: N/A 5v: N/A 3.3v: N/A vbat: 3.22 
Info:
  Processes: 288 Uptime: 1h 16m Memory: 15.53 GiB used: 3.08 GiB (19.8%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 clang: 10.0.0-4ubuntu1 
  Shell: bash v: 5.0.17 inxi: 3.0.38
```

---

### Post by wowotiel on 2021-04-21
Which kernel are you using now?
You can check this in the terminal with uname - r.
Mine output now (I am on kernel serie 5.4):
```
silencio1@silencio1:~$ uname -r
5.4.0-72-generic
silencio1@silencio1:~$
```

---

### Post by mastablasta on 2021-04-21
if you are on LTS you can move to original kernel 5.4. if that one works well i suggest you do that. also this then looks like drivers issue and should be reported on launchpad (bug).

downgrading to 5.4 can be easy: [https://askubuntu.com/questions/1310622/downgrade-to-kernel-5-4-0-because-kernel-5-8-45-doesnt-like-my-bluetooth-contro](https://askubuntu.com/questions/1310622/downgrade-to-kernel-5-4-0-because-kernel-5-8-45-doesnt-like-my-bluetooth-contro)

other things that can cause degradation through time during usage:
- bad RAM chip - as chip fills data reaches part that are problematic and errors appear
- bad capacitors on GPU (or in your case motherboard) - sometimes it works sometimes it doesn't, sometimes it is stable other times it freezes or does strange things to display.  seen it once on very old GPU card.
- bad drivers can always lead to strange results since they control the whole thing. in case of intel GPU they are baked into kernel. so different kernel version will have different driver version

---

### Post by guybutterworth on 2021-04-21
Here ya go -

```
guy@guy-MMLP5AP-00:~$ sudo uname -r
[sudo] password for guy: 
5.4.0-42-generic

```

---

### Post by guybutterworth on 2021-04-21
Thanks for that, I've followed the instructions that you linked to, rebooted, and everything works just as it did before, just fine.

Thanks a lot!


> **mastablasta said:**
> if you are on LTS you can move to original kernel 5.4. if that one works well i suggest you do that. also this then looks like drivers issue and should be reported on launchpad (bug).

downgrading to 5.4 can be easy: [https://askubuntu.com/questions/1310622/downgrade-to-kernel-5-4-0-because-kernel-5-8-45-doesnt-like-my-bluetooth-contro](https://askubuntu.com/questions/1310622/downgrade-to-kernel-5-4-0-because-kernel-5-8-45-doesnt-like-my-bluetooth-contro)

other things that can cause degradation through time during usage:
- bad RAM chip - as chip fills data reaches part that are problematic and errors appear
- bad capacitors on GPU (or in your case motherboard) - sometimes it works sometimes it doesn't, sometimes it is stable other times it freezes or does strange things to display.  seen it once on very old GPU card.
- bad drivers can always lead to strange results since they control the whole thing. in case of intel GPU they are baked into kernel. so different kernel version will have different driver version

---

### Post by wowotiel on 2021-04-22
The meta-package linux-generic ensures that your current kernel 5.4.0-42-generic will be updated to the current supported kernel = 5.4.0-72-generic (supported till august 2021).
Is your kernel now 5.4.0-72-genereic? (uname -r)

Some similarities between your hardware and mine:
Mobo: Gigabyte
Uefi: American Megatrends
i915 v: kernel
Display: x11 server: X.Org 1.20.9 driver
Mine OpenGL: renderer:Mesa DRI Intel HD Graphics 4000 (IVB GT2)  v: 4.2 Mesa 20.2.6 direct render: Yes
Yours OpenGL: renderer:Mesa DRI Intel HD Graphics 4400 (HSW GT2)  v: 4.5 Mesa 20.2.6

@Mastabla: May be there could be a bug in the newer Linux kernels (>5.8.0-48) with those hardware specifications?

Luckily guybutterworth and I can continue with the 5.4 kernel serie.:D

---

### Post by mastablasta on 2021-04-22
> **wowotiel said:**
> 
@Mastabla: May be there could be a bug in the newer Linux kernels (>5.8.0-48) with those hardware specifications?


yes, it could be. it certainly looks that way. but they can't fix it unless they know about it. which is why it should be reported.

---

### Post by wowotiel on 2021-04-22
> **mastablasta said:**
> yes, it could be. it certainly looks that way. but they can't fix it unless they know about it. which is why it should be reported.
Thanks for your reply. I will certainly do that, one of these days.

---

### Post by wowotiel on 2021-04-22
I have found out that there is already an bugrapport:
After upgrade to 5.8.0-49/5.8.0-50 with Intel graphics (gen7, Haswell/Ivy Bridge) a lot of glitches render screen unusable
[https://bugs.launchpad.net/ubuntu/+source/linux-meta-hwe-5.8/+bug/1924624]("https://bugs.launchpad.net/ubuntu/+source/linux-meta-hwe-5.8/+bug/1924624")
It looks that it is corrected in kernel 5.8.0-51 which is not released yet.
As said: Kernel 5.8.0-48 and all of the kernels from the 5.4 serie does work good.

---

### Post by broadwaylion2 on 2021-04-24
Yes. I had that problem, and so know what you are seeing even if you cannot describe it. My box is set up with two monitors and it was the VGA monitor that was giving trouble. If you can switch to a DVI monitor connection, that might help, I fixed my problem by installing a new video card in the computer. (I always keep spare video and audio cards in my shop (Oh lucky me--I got a shop!) )

I thought that is was my problem, but coming here I see that there is an issue. Let us know if moving to a DVI cable helps your issue. (Power Down before disconnecting cables)
ROAR

---

### Post by fermilesi on 2021-04-28
> **guybutterworth said:**
> I've just gone through the GRUB menu and booted up using an older version of the kernel, and while it might still be too soon to be certain, everything is now functioning perfectly.

                        Same problem here with two ThinkPad E430 (Intel HD Graphics 4000; driver i915) when upgrading to -49 or -50


 Additionally, with -50 I can't login into Ubuntu 20.04: after boot and unlocking disk protection successfully, cursor appears moves fine in a colored but empty login screen (e.g., no logo, no username, no password box, no response after click or keyboard). However I can still open non-graphical consoles (e.g., tty3)


 Everything works fine booting into -48-generic

[now waiting for that -51 !!!]

---

