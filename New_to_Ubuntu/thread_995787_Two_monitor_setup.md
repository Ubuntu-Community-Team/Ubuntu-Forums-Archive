---
title: "Two monitor setup?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Accordionista on 2008-11-28
Hi all here's my problem, 

Whilst running windows I can plug in the VGA cable into the laptop, stick the other end in my TV and it automatically sorts itself out so I can have two monitors running at once and have a connected desktop sort of thing over the two screens. 

I tried to do this on linux and was surprised it doesnt do it automatically like it seems to do with everything else! I've looked about on the internet for help but everywhere just talks about video cards and things, i dont really understand! 

Im sure there must be a simple solution somewhere but im just not typing it into help or search boxes right?

any help much appreciated!

---

### Post by overdrank on 2008-11-28
> **Accordionista said:**
> Hi all here's my problem, 

Whilst running windows I can plug in the VGA cable into the laptop, stick the other end in my TV and it automatically sorts itself out so I can have two monitors running at once and have a connected desktop sort of thing over the two screens. 

I tried to do this on linux and was surprised it doesnt do it automatically like it seems to do with everything else! I've looked about on the internet for help but everywhere just talks about video cards and things, i dont really understand! 

Im sure there must be a simple solution somewhere but im just not typing it into help or search boxes right?

any help much appreciated!

Hi and it does help to know the model of the graphics card. If you are using Hardy 8.04 you can try the command ```
gksu displayconfig-gtk
``` and see if your second monitor is detected.

---

### Post by Accordionista on 2008-11-28
Hi, 

When i put that in the terminal it says VESA driver (generic) as my graphics card? Sorry I really dont know that much about linux or computer bits. 

That window seems to be what i need though right? I change the model settings and test it but it doesnt seem to work. My TV model isnt on the list.

---

### Post by overdrank on 2008-11-28
> **Accordionista said:**
> Hi, 

When i put that in the terminal it says VESA driver (generic) as my graphics card? Sorry I really dont know that much about linux or computer bits. 

That window seems to be what i need though right? I change the model settings and test it but it doesnt seem to work. My TV model isnt on the list.

You can use the command ```
lspci
``` and look for VGA and this is the graphics card. If you test the setup and it doesn't detect your second monitor it maybe cause of the vesa driver.
As you can see in the screen shot I have attached it detects my second monitor. But I am using the nvidia driver.

---

### Post by Accordionista on 2008-11-28
Hi thanks for your help. When i typed in the second command I did see this on the big list:

 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

I restarted everything and wow the monitor now displays my current desktop, just like a copy of it, rather than an extension of it. When I try to make it the secondary and extended to the right it doesnt work, no error messages, just resets and stays the same?

---

### Post by overdrank on 2008-11-28
> **Accordionista said:**
> Hi thanks for your help. When i typed in the second command I did see this on the big list:

 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

I restarted everything and wow the monitor now displays my current desktop, just like a copy of it, rather than an extension of it. When I try to make it the secondary and extended to the right it doesnt work, no error messages, just resets and stays the same?

Yea sorry as I have not be able to test and setup the dual monitors with the intel graphics. Maybe some one else can jump in.

---

