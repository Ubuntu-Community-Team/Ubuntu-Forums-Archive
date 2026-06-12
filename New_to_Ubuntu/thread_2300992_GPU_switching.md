---
title: "GPU switching"
date: 2015-10-29
forum: New to Ubuntu
---

### Post by moolman-juandre on 2015-10-29
Hi Guys.

I know this is not a new topic. But, I can not seem to find the answer to my problem anywhere else, so I must ask...

Firstly I have a Toshiba Qosmio X300-15G laptop which I run Ubuntu 14.04 LTS on.
The laptop has 2 GPU's:
1. GeForce 9400M Intergrated &
2. GeForce 9800M GTS PCI in SLI.

I am unable to switch to the 9800M GPU, even with the latest drivers installed which are: NVIDIA 340.93, see below when I run inxi -Gxx

Graphics:  Card-1: NVIDIA G94M [GeForce 9800M GTS] bus-ID: 03:00.0 chip-ID: 10de:0628 
           Card-2: NVIDIA C79 [GeForce 9400M G] bus-ID: 04:00.0 chip-ID: 10de:0862 
           X.Org: 1.17.1 driver: nvidia Resolution: 1680x1050@60.1hz 
           GLX Renderer: GeForce 9400M G/integrated/SSE2 GLX Version: 3.3.0 NVIDIA 340.93 Direct Rendering: Yes

NVIDIA X Server Settings has no option to switch between the 9400 and 9800 GPU's, and this driver version comes with NVIDIA-PRIME. Bumblebee is also not doing the job.
Is there any way for me to get my laptop to use the 9800 GPU with Ubuntu?

Thanks in advance for your help.

---

### Post by grahammechanical on 2015-10-29
It is just a small point and I doubt if it will solve your problem anyway but Nvidia 340.93 is not the latest Nvidia proprietary video driver. I have an Nvidia GT220 and I get offered Nvidia 340.93 and I am running 15.10. I tried install the 346 driver and that is when I found out the Nvidia has dropped support for the GT220 from it latest drivers. I have also seen posts where the user is running on Nvidia 355 series drivers.

The Nvidia web sites offers a 352.55 Linux driver for your video cards. You should try Ubuntu 15.10 in a live session and see what Additional Drivers offers you and if the drivers do what you want. Then you can try a dual boot with 14.04 and 15.10 before upgrading to see if 15.10 is really better than 14.04

Regards.

---

### Post by moolman-juandre on 2015-10-29
Thank you for your advice grahammechanical.

I will do just that, I never really tried with a live boot, but I did downgrade from 15.10 because somehow 15.10 freezes my laptop. Also tried with Mint 17.2 and Debian, all the same issues.
I will try with the live boot maybe its a regional thing like Remmina. For instance my remmina remote desktop works when I boot live, but not when I install. I have to uninstall the rdp-plugin for it to work... but not the issue. lol.

I will keep you posted.

---

### Post by moolman-juandre on 2015-10-30
I've just checked NVIDIA's website before I boot live with 15.10, and according to them the 340.93 driver is the latest one for my GPU's. So I doubt this will solve my issue. Is there any way in NVIDIA X Server Settings where I can setup an application to use the 9800 GPU? Or to turn it on permenantly? I can not disable the 9400 in BIOS. And as far as I'm aware, there is also no keyboard shortcut to force my laptop to use the 9800. 
Any advice at this point will be welcome. I broke my GUI 3 times already, I had to fix it by editing the xorg.conf file.

Thanks in advance guys.

---

