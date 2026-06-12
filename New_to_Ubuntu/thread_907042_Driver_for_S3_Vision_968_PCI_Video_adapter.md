---
title: "Driver for S3 Vision 968 PCI Video adapter"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by nuddernuby on 2008-09-01
I've been helping a 12 year old get Hardy onto his rather old computer as a dual boot. 
Pentium I 200Mhz MMX; 192 MB Ram; Video card as above
HDD 1: 4GB running Windows 98 SE (no problems)
HDD 2: 20GB running Hardy

[I am reporting this from another computer] 

All appears to be OK except for the resolution, which is somewhere far below 800x600.  Only about a quarter of the window is visible at one time.  Colours are a psychedelic scramble, but the basics can just be made out.

**lshw** provides the following:
> 
display UNCLAIMED
description: VGA compatible controller
product:  86c968 [Vision 968 VRAM] rev 0
vendor: S3 Inc
physical id: 10
width: 32bits
clock: 33MHz
capabilities: vga controller
configuration: latency=0


QUESTION:
I presume this is only a driver problem, or is there another issue?  If driver, where could one download the correct driver and how is it installed?
Thank you for your response.

---

### Post by swoll1980 on 2008-09-01
I would try to configure it manually. Google for the specs on your monitor. then do 
```
sudo dpkg-reconfigure xserver-xorg
```
I can tell you to use the vesa driver your card only supports colors up to 16 bit find out what the vertical and horizontal refresh rate is for your monitor

---

### Post by nuddernuby on 2008-09-01
Thanks, swoll.  We tried
```
sudo dpkg-reconfigure xserver-xorg
```
and
```
startx
```
without any success.  Eventually changed video card to S3 Trio64 DX/VX.  Now we only have a black screen.  The Windows 98 part is still functioning well, but we'll have to find a solution for the black screen. Any ideas?

---

### Post by nuddernuby on 2008-09-03
So, we have now replaced the video card with a S3 Trio64 DX/VX card and see only a black screen.  From tty2 we get the following output when running
```
$startx
```
> 
Fatal server error:
Server is already active for display0
         If the server is no longer running, remove /tmp/.XO-lock and start again.

Invalid  MIT-MAGIC-COOKIE-1 keygiving up

xinit: Resource temporarily unavailable (error 11): unable to connect to X 
server

xinit: No such process (error 3): Server error


[/tmp/.XO-lock does not exist]

Would anybody know what went wrong here?

---

### Post by halitech on 2008-09-03
> **nuddernuby said:**
> I've been helping a 12 year old get Hardy onto his rather old computer as a dual boot. 
Pentium I 200Mhz MMX; 192 MB Ram; Video card as above
HDD 1: 4GB running Windows 98 SE (no problems)
HDD 2: 20GB running Hardy


personally on a machine with those specs, I'd be going with Puppy or DSL as (X)(K)Ubuntu will not run very well. If you want something from the Debian family, do a base install of Debian and then install XFCE or Fluxbox, it will run better then full Ubuntu and the hardware should work out of the box.

---

### Post by nuddernuby on 2008-09-06
Thank you for the advice, halitech. I share your view on the age of the equipment, but I have a sneaky suspicion that we did something (small) wrong somewhere during the setup process.

---

### Post by Bradtek on 2008-09-06
I have a Pentium 200 MMX with 192mb Ram 
& a GeForce 2 MX400 64mb PCI Video Card
and it has enough trouble running Xubuntu
I wouldnt have thought it was even possible to get 
Ubuntu running on it at all.

Same system flies running Puppy 4

---

### Post by halitech on 2008-09-06
> **nuddernuby said:**
> Thank you for the advice, halitech. I share your view on the age of the equipment, but I have a sneaky suspicion that we did something (small) wrong somewhere during the setup process.

don't take this the wrong way but yeah, you're trying to run a system that is way under the specs to run it on. Ram is pushing it for even Xubuntu with the alt install cd, way below on the CPU for Ubuntu and might run Xubuntu but very slowly. Try the minimal debian install then add XFCE and I bet you'll see it working with no problems and faster then what it would with using Ubuntu. I can safely say this because I have 2 laptops, one is a P3 750 with 256 meg of ram running Xubuntu and the other is a P266 with 96 meg of ram that I did the minimal Debian install with XFCE and it puts my P3 laptop to shame with the speed.

> **Bradtek said:**
> I have a Pentium 200 MMX with 192mb Ram 
& a GeForce 2 MX400 64mb PCI Video Card
and it has enough trouble running Xubuntu
I wouldnt have thought it was even possible to get 
Ubuntu running on it at all.

Same system flies running Puppy 4

Puppy and DSL would work good on those specs, or Debian with XFCE

---

