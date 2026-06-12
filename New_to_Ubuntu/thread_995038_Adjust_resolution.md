---
title: "Adjust resolution"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by theamber on 2008-11-27
hi, I installed Ubuntu in a laptop and in the beginning it had nice resolution then I did the updates and now is 640x480 too big fonts.
The card drivers are privative is enable and all. I went to resolution and can cant chage it smaller nor better than 640 x480. Any tips, thaks.

---

### Post by overdrank on 2008-11-27
> **theamber said:**
> hi, I installed Ubuntu in a laptop and in the beginning it had nice resolution then I did the updates and now is 640x480 too big fonts.
The card drivers are privative is enable and all. I went to resolution and can cant chage it smaller nor better than 640 x480. Any tips, thaks.

Hi and what is the model of the graphics card? If you are using Hardy 8.04 you may try the command ```
gksu displayconfig-gtk
``` and adjust there.

---

### Post by theamber on 2008-11-27
> **overdrank said:**
> Hi and what is the model of the graphics card? If you are using Hardy 8.04 you may try the command ```
gksu displayconfig-gtk
``` and adjust there.

Nvidia gforce 7 series.

---

### Post by brigadoon on 2008-11-27
I had similar problems with the NVIDIA driver in my laptop. In my case the driver didn't recognize the display resolutions settings of the laptop flat panel display. I have my solution posted at the following link...

[http://ubuntuforums.org/showthread.php?t=773391](http://ubuntuforums.org/showthread.php?t=773391)

Just read through till you get to the driver solution. You may or may not have the same issues with your display. I hope this helps.

---

### Post by theamber on 2008-11-27
The thing is that when I installed at first it was fine. Then after the updates it went big and I can change it. Also when I turn it off the ubuntu and the status bar look great.

---

### Post by brigadoon on 2008-11-27
> **theamber said:**
> The thing is that when I installed at first it was fine. Then after the updates it went big and I can change it. Also when I turn it off the ubuntu and the status bar look great.

I feel your pain. When I installed Ubuntu the display was OK. My laptop was using the default Ubuntu graphics driver at any resolution I wanted. However, the default driver did not allow me to use a game that required OPENGL. I am am a big fan of Neverwinter Nights and Unreal style games. OPENGL is a must for these games. When I loaded in the NVIDIA driver I was stuck in low resolution with choppy 3D graphics. I was in contact with NVIDIA and they admit it was an NVIDIA issue. I was able to work around it.

My system required the tweaking that I detailed in my post. It sounds like the custom EDID option would work in your situation. Do you know what the resolution settings of your display are? example 1024x768, 800x600, etc...

---

