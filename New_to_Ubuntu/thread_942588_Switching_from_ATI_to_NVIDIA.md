---
title: "Switching from ATI to NVIDIA"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by RussW210 on 2008-10-09
I am going to switch my video card from an ATI to NVIDIA.  Bought a new computer with a cheap 128MB ATI Radeon HD 2400 Video Card but I can't get 3d Graphics to work (Google Earth, 3d games, 3d Screen Savers).  From what I can see, ATI doesn't have cards that work well with Linux and I won't be able to fix the problem with my card.

I have never switched out a Video Card before and need to know if I would be able to install the following video card on my computer:

ASUS EN9600GT TOP/HTDI/512M GeForce 9600 GT 512MB 256-bit GDDR3 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card - Retail

    * Chipset Manufacturer: NVIDIA
    * Core clock: 720MHz
    * Stream Processors: 64
    * Memory Clock: 1800MHz
    * DirectX: DirectX 10
    * OpenGL: OpenGL 2.0
    * HDMI: 1 via Adapter
    * DVI: 2

......... I have an Inspiron 530 Dell Desktop Computer with 3GB RAM, 22-inch monitor, Quad-Core processor.  I'm thinking the new Graphics Card would fix the 3d graphics because of the NVIDIA drivers. What do you guys think?  I am running Ubuntu Hardy 8.04.

---

### Post by Nxion on 2008-10-09
> **RussW210 said:**
> I am going to switch my video card from an ATI to NVIDIA.  Bought a new computer with a cheap 128MB ATI Radeon HD 2400 Video Card but I can't get 3d Graphics to work (Google Earth, 3d games, 3d Screen Savers).  From what I can see, ATI doesn't have cards that work well with Linux and I won't be able to fix the problem with my card.

I have never switched out a Video Card before and need to know if I would be able to install the following video card on my computer:

ASUS EN9600GT TOP/HTDI/512M GeForce 9600 GT 512MB 256-bit GDDR3 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card - Retail

    * Chipset Manufacturer: NVIDIA
    * Core clock: 720MHz
    * Stream Processors: 64
    * Memory Clock: 1800MHz
    * DirectX: DirectX 10
    * OpenGL: OpenGL 2.0
    * HDMI: 1 via Adapter
    * DVI: 2

......... I have an Inspiron 530 Dell Desktop Computer with 3GB RAM, 22-inch monitor, Quad-Core processor.  I'm thinking the new Graphics Card would fix the 3d graphics because of the NVIDIA drivers. What do you guys think?  I am running Ubuntu Hardy 8.04.

Well I would say go NVIDIA becasue I have never had any problems with them like I have had with ATI. 

But..

First lets take a look at something. Where I work I have a Dell Optiplex 745 and it has a 128MB ATI Radeon X1300/X1550 video card in it. I was under the same impression that ATi was a bad thing when it came to Linux, but I was able to install the driverrs without a issue and use the 3D capabilities of the card. Wobbly windows works fine, games seem to run fine etc. 

It sounds to me maybe the correct driver is just not defined in the xorg file. How is it that you loaded the drivers for your card? from the repos? Or did you use Envy to install it?

So maybe you dont have to get another card. The 2400 that you have should be fine and do what you need. please let me know if you need clarity on anything I put.

Thanks,
Nx

---

### Post by LowSky on 2008-10-09
I don't know too much about Dell's but you should be able to switch easily. All you need to do is uninstall any proprietary drivers before installing the new card. very simple

---

### Post by Nxion on 2008-10-09
> **RussW210 said:**
> I am going to switch my video card from an ATI to NVIDIA.  Bought a new computer with a cheap 128MB ATI Radeon HD 2400 Video Card but I can't get 3d Graphics to work (Google Earth, 3d games, 3d Screen Savers).  From what I can see, ATI doesn't have cards that work well with Linux and I won't be able to fix the problem with my card.

I have never switched out a Video Card before and need to know if I would be able to install the following video card on my computer:

ASUS EN9600GT TOP/HTDI/512M GeForce 9600 GT 512MB 256-bit GDDR3 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card - Retail

    * Chipset Manufacturer: NVIDIA
    * Core clock: 720MHz
    * Stream Processors: 64
    * Memory Clock: 1800MHz
    * DirectX: DirectX 10
    * OpenGL: OpenGL 2.0
    * HDMI: 1 via Adapter
    * DVI: 2

......... I have an Inspiron 530 Dell Desktop Computer with 3GB RAM, 22-inch monitor, Quad-Core processor.  I'm thinking the new Graphics Card would fix the 3d graphics because of the NVIDIA drivers. What do you guys think?  I am running Ubuntu Hardy 8.04.

And to answer you initial question, Yes you should have no issue of installing it in Insprion. The only thing to look out for if if the video card has any special power requirements. For example you would need  to have a special 6 prong plug to run it. Some video card have those, not all, but some.

Where it it that you found the NVIDIA card?

---

### Post by RussW210 on 2008-10-09
I found the NVIDIA card on NewEgg.com...

At first, when I installed Ubuntu, I used the ATI Graphics Accelerator in Hardware Drivers.  So I was using FGLRX from the repos.

I tried using the Envy driver but it screwed up my VLC player and movies/music kept freezing so I switched back.

FGLRX is defined as my device under xorg.conf.  Wobbly windows, the cube in Compiz Fusion, and any settings under Compiz works fine.  It is just when it comes down to using Google Earth, SuperTuxKart, 3d Screen Savers, etc. that I have problems...

---

### Post by Nxion on 2008-10-09
I am sorry to say I am not sure how to proceed. Let me research it and see what I can find for you. I wish I had the answer for you now :(

---

### Post by Nxion on 2008-10-09
I was reading the [release notes]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html") from the AMD/ATI site for there drivers and I think that you should load those and give it try.

Here is the link to the other post I found on how to load the drivers from the ATI/AMD site
[URL="http://ubuntuforums.org/showthread.php?t=648061"]
http://ubuntuforums.org/showthread.php?t=648061
[/URL]
Hope this helps.

---

### Post by RussW210 on 2008-10-09
Thank you Nxion... you were the first person to really give me full attention on this issue.  I will try loading the Driver from the ATI website when I get home, I haven't tried that yet.

Is that what you had done to get 3d graphics working correctly?

---

### Post by Nxion on 2008-10-09
> **RussW210 said:**
> Thank you Nxion... you were the first person to really give me full attention on this issue.  I will try loading the Driver from the ATI website when I get home, I haven't tried that yet.

Is that what you had done to get 3d graphics working correctly?

Indeed it was. If you need any further assistance, I will be glad to help in anyway I can.

Nx :)

---

### Post by RussW210 on 2008-10-09
Thanks, I saved you as a contact :)

---

### Post by Nxion on 2008-10-09
I added us as well :)

---

