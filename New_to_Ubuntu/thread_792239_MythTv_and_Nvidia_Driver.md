---
title: "MythTv and Nvidia Driver"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Damned666 on 2008-05-12
Hi,

I just dumped windows for linux and am trying to build a PVR. i have a problem/question about the nvidia drivers. Do i need to install the restricted drivers to be able to output in 1080 on the tv with my 6800GT. I already have a DVI-HDMI cable and it works fine but my resolution is stuck at 640*480 once connected to it.

I have a lot of problem with those drivers on this card tried envy-ng, nvidia drivers directly, enable restricted drivers and every time i get a black screen so if i could skip this installation without any problem that would be great.

Thanks,

---

### Post by JoshuaRL on 2008-05-12
> **Damned666 said:**
> Hi,

I just dumped windows for linux and am trying to build a PVR. i have a problem/question about the nvidia drivers. Do i need to install the restricted drivers to be able to output in 1080 on the tv with my 6800GT. I already have a DVI-HDMI cable and it works fine but my resolution is stuck at 640*480 once connected to it.

I have a lot of problem with those drivers on this card tried envy-ng, nvidia drivers directly, enable restricted drivers and every time i get a black screen so if i could skip this installation without any problem that would be great.

Thanks,

Nvidia has pretty great drivers, so I would suggest using them.  Here's an easy 5 step way to install your drivers correctly:
**Five Steps to Nvidia Driver Install!**

1).  Reboot the computer and choose Recovery Mode from the GRUB menu.

2).  Move into the Desktop:
```

cd /home/username/Desktop

```
The capitol "D" is important, and "username" is the name of the user that has the file in their desktop.

3).  Find the name of the installer file:
```

ls

```
That's a lowercase L, not a 1.  The file that you downloaded to the Desktop will show up here.  When you use that name in the steps below, make sure you type it exactly.  I'll be using "nvidiainstallerfile.run" as the fake name.

4).  Change permission level of the installer file so it has internet access:
```

chmod +x nvidiainstallerfile.run

```

5).  Run the installer file in a shell:
```

sh nvidiainstallerfile.run

```
Go through all the options, picking the defaults unless you KNOW you need something else.  After that's done, you reboot the computer and the driver should be installed.

Congratulations!

---

### Post by Damned666 on 2008-05-12
Wiil i be able to run the card at a 1080 resolution connected to my tv ?

---

### Post by JoshuaRL on 2008-05-12
> **Damned666 said:**
> Wiil i be able to run the card at a 1080 resolution connected to my tv ?

Probably, I run that resolution on my 15inch CRT.

---

### Post by Damned666 on 2008-05-12
One i get back IN Ubuntu, i got a message telling me that my card could not be detected correctly and that i need to set them manually. All i have is 640*480 and 800*600. If i select anything and reboot i get the same message again

---

### Post by JoshuaRL on 2008-05-12
> **Damned666 said:**
> One i get back IN Ubuntu, i got a message telling me that my card could not be detected correctly and that i need to set them manually. All i have is 640*480 and 800*600. If i select anything and reboot i get the same message again

Well, it might just be easier to try Envy.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Damned666 on 2008-05-12
Already tried envy, thinking it would be a savior but ended up with no display at all. Screen is black even if i try ctlr-alt-f1.

---

### Post by JoshuaRL on 2008-05-13
> **Damned666 said:**
> Already tried envy, thinking it would be a savior but ended up with no display at all. Screen is black even if i try ctlr-alt-f1.

What does the video card section of your xorg.conf read?

Have you tried
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by Damned666 on 2008-05-13
i managed to install the driver from nvidia.com. Now i can CTRL-ALT-F1. But with no gui. 

sudo dpkg-reconfigure -phigh xserver-xorg still doesn't give me gui access and it override my xorg.conf with "configured video device"

Before i had Identifier=Device0
             Driver=nvidia

---

### Post by JoshuaRL on 2008-05-13
Could you try dpkg again and select vesa to get into the desktop?

---

### Post by Damned666 on 2008-05-13
each time i try dpkg, my xorg.conf comes back to "configured video device" and no driver. Tried putting vesa in the driver section of xorg.conf that the nvidia driver created but the gui still doesn't load.

Would it be better if i started from scratch ?

---

### Post by JoshuaRL on 2008-05-13
That depends on what you have on there.  It might just be.

Try dpkg again, and manually select the vesa driver.  See if that at least gets you to an X session.

---

### Post by Damned666 on 2008-05-13
how can i select it manually ? dpkg-reconfigure -phigh xserver-xorg doesn't give me anything it's all automated...

---

### Post by JoshuaRL on 2008-05-13
Try it without the -phigh modifier.  Sorry.

---

### Post by Damned666 on 2008-05-13
dpkg-reconfigure xserver-xorg doesn't give me anything about vesa. i get a question about kernel frame buffer and keyboard autodetection and other keyboard thing. Once finished, My new xorgconf have a new video option FBdev (probably frame buffer ralated)

---

### Post by Damned666 on 2008-05-14
Any other idea ?

---

### Post by Damned666 on 2008-05-14
I managed to boot in the gui using 96.xx.xx driver from nvidia but i only have 800*600 & 640*480 in the screen resolution screen.

---

### Post by JoshuaRL on 2008-05-15
Try this:
```

displayconfig-gtk

```
It's the GTK port of displayconfig from KDE.  It's a GUI for editing your xorg.conf and setting up video correctly.  See if you can get it going with that.

---

### Post by Damned666 on 2008-05-15
Tried a couple of settings ... even tried on my TV and nothing is working ... if i press the test button, i have an error in the terminal window telling me that my video card and monitor is not setup correctly. There's also another error telling me to check if there's a nvidia GPU present in the sysmte

---

### Post by Damned666 on 2008-05-15
now i'm starting to think that i will never find the solution to this

---

