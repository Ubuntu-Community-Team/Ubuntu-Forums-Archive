---
title: "Installation and display adapters/drivers"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by zackshalac on 2008-07-29
I'm trying to install the new version of ubuntu on my desktop, it has an amd x2 proccesor and a 7600gt graphics card. The problem that i have is that when i try and boot to the live cd, it doesn't seem to have the proper drivers in it to use the graphics card, so it just diplays wierd dancing verticle flashing lines. So in order to get around this, i set the computer to use the integrated graphics card in the BIOS, then the live cd started just fine and i was able to install, then i swithed back to the nvidia card, and still got verticle flashing lines.  So i installed whatever proprietary driver it wanted me to install, and went back to the card, which worked, but came in at really low resolution, and a wierd purplish tint, so iu think i still had the wrong driver, and i tried to download the one from nvidia, but im new to linux and have no idea what to do.

Also, i had to use two different monitors with the different display adapters, because of the way it was all set up, so i dont know if that would cause problems.
thanks

---

### Post by bobnutfield on 2008-07-29
There is a program available called EnvyNG which will identify your graphics card and download and install the correct driver.  You can find it in the Synaptics package manager.

---

### Post by zackshalac on 2008-07-29
wow thanks, that will help so much

---

### Post by zackshalac on 2008-07-30
Ok, so i have gotten all of the drivers installed, but i am having another problem, my monitor is a 1080p lcd tv, but the nvidia x server settings program sems to think that it's highest resolution is 1024x768, but i need to turn it up to 1920x1080, also, the colors on the monitor are off, everything is blue, for example, the blue of the xubuntu background is the same color blue on the screen as the orange is on the ubuntu website.  I've played around with all the x-server settings, and have not been able to correct it

---

### Post by mlinsgomes on 2008-07-30
> **zackshalac said:**
> Ok, so i have gotten all of the drivers installed, but i am having another problem, my monitor is a 1080p lcd tv, but the nvidia x server settings program sems to think that it's highest resolution is 1024x768, but i need to turn it up to 1920x1080, also, the colors on the monitor are off, everything is blue, for example, the blue of the xubuntu background is the same color blue on the screen as the orange is on the ubuntu website.  I've played around with all the x-server settings, and have not been able to correct it


You could edit your xorg.conf file and add the specified resolution that you want.

> sudo gedit /etc/X11/xorg.conf

At Section "Screen", you should add the following line:

>  Option         "MetaModes" "1920x1080"

Then you need to restart your graphical interface to get this new screen resolution, e.g if you're using GDM, go to console (Ctrl+F1) login and type:

> sudo /etc/init.d/gdm restart

---

### Post by peakshysteria on 2008-07-30
Or:
```
sudo displayconfig-gtk
```

And adjust the resolution.

(alt: System --> Prefrences --> Main menu --> Other --> Check screens and graphics and you'll find it under: Applications --> Others)

---

### Post by zackshalac on 2008-07-30
ok, none of those things helped me, but i did figure out what the problem is, i just don't know how to fix it.  Basically, the way my system is set up is that i have a 1080p lcd tv acting as a monitor, i have it hooked up via component cables running through the 7 pin s-video port, the 7 pin has three modes, there is s-video output, there is regular video output, ie. the yellow rca plug, or there is component output, (rgb rca plugs) i had it hooked up coming through the component, but the card was actually sending it through just standard video, which only supports up to 1024x768 resolution, this was what was causing the discoloration issue i was having, because i had all of the video running through the plue input in component video, so everything was blue, if that makes sense.  So i need to know how to get it to use the component output rather than the standard video ouput.  Thanks, zack

---

### Post by peakshysteria on 2008-07-31
Could you tell us a bit more about your tv? Actual name, model, etc....

---

