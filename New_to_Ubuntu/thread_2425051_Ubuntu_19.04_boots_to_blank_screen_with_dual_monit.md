---
title: "Ubuntu 19.04 boots to blank screen with dual monitors and AMD Radeon HD 7730"
date: 2019-08-19
forum: New to Ubuntu
---

### Post by MrRubik on 2019-08-19
I just loaded Ubuntu 19.04 onto my Dell XPS 8500 desktop last week. I am using an AMD Radeon HD 7730 with dual monitors (1 HDMI, 1 DisplayPort). Most of the time when I reboot my system, it will boot to a completely blank login screen. It shows nothing at all, just a blank screen. I have tried the things below and nothing is working. Deleting the raven_dmcu.bin file seemed to work but now I'm having the problem again. If anyone could please tell me how to fix this, I would very much appreciate it. I don't want to have to buy a new video card but I'm going to have to if I can't get this fixed. I have got all other issues on my system worked out except this one. Thanks.

1 - Tried with only one monitor and the same issue occurs.
2 - Tried switching monitor 1 and 2 cables and adjusting the display settings to put their left/right orientation back.
3 - I read someones post that said this would work and it did for a while but I'm having the issue again now. Delete the file /lib/firmware/amdgpu/raven_dmcu.bin and then run [COLOR=#242729][FONT=Consolas]sudo update-initramfs -u -k all[/FONT][/COLOR]

---

### Post by oldfred on 2019-08-20
I do not know AMD issues, I thought AMD just worked with some issues on very new systems.

Have you updated UEFI from Dell?
Can you boot using just internal video? You may have to temporarily turn off video mode in UEFI settings for external video.

       [https://ubuntuforums.org/showthread.php?t=2372733](https://ubuntuforums.org/showthread.php?t=2372733)
If your card is supported by AMDGPU, it will be installed when you install Ubuntu. You can only install the AMDGPU-PRO overlay if AMDGPU is installed. If your card is not supported by AMDGPU, the Radeon driver will be installed.
It's automagic now. You don't need to do anything unless you have a need or pressing desire for the overlay-- for instance if you need Vulkan support. In that case, AMD has a script that will take care of it. 
[https://www.amd.com/en/support/kb/faq/gpu-635](https://www.amd.com/en/support/kb/faq/gpu-635) 
    
One user also posted this:
       After adding "GRUB_GFXMODE=1920x1080x32" to the grub config the next reboot Ubuntu worked perfectly, both monitors fully functional and I could watch videos

---

### Post by Frogs Hair on 2019-08-20
Duplicate post in general help. Closed

---

