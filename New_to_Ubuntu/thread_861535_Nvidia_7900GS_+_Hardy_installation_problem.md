---
title: "Nvidia 7900GS + Hardy installation problem"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Zarok on 2008-07-16
Greetings.

I was trying to install Ubuntu 8.04.1 Hardy Heron on my desktop PC with a Nvidia 7900GS + Fujitsu Siemens L19-2W 19" LCD monitor. When I tried booting the installation cd, all the screen showed after the Ubuntu logo was a random rainbow of garbled colors. It starts OK, but its all messed up.

So, I downloaded the alternate installation cd and installed it with that. The OS installed fine, and boots ok, I can log in and everything, but I still have no image. Only the garbles. Monitor says on its on-screen diagnostics that refreshrates are 31,5/70Khz, res 720x400, which is what my PC shows during some POST screens. I can log in fine, but I can't see anything so I can't really try to fix the problem. I can boot it in recovery mode and get to the root console, but what should I edit to try to fix it?

Xorg.conf says Configured monitor and Configured video device as monitor/device, should I change that to something or something? I'm desperately trying to finally get rid of Windows on my desktop pc, already a happy laptop Ubuntu user, so if you could help me, I'd really appreciate it. :)

---

### Post by RomeReactor on 2008-07-16
Hi. Have you installed the nVidia driver? If not, try:
```
sudo aptitude install nvidia-glx-new
```
After the installation, restart and see if there's a difference.
```
sudo reboot
```

As for the Xorg.conf file, the new X server does more autoconfigure stuff at boot time, and seemingly doesn't reference xorg.conf as it did before.

---

### Post by Zarok on 2008-07-16
I actually just figured out the problem myself, it was my TV that was plugged into the 2nd monitor DVI input that messed it up, I unplugged it and it worked. I'll try installing the drivers now and see if my dual setup works after that. :)

---

### Post by RomeReactor on 2008-07-16
As I don't use dual monitors I can't comment much on this, but after you get your display working, I believe you can set them up in 'Applications->Other->Screens and Graphics' (if you can't see the application there, or you don't see the 'Other' menu, you can edit the menus by right-clicking on the menubar in the top panel and selecting 'Edit menus'; or you can launch the application by pressing ALT+F2 and writing:
```
gksudo displayconfig-gtk
```

Maybe even using the screen resolution application (System->Preferences->Screen Resolution) can also help with that.

To further manage your nVidia card, install nvidia-settings:
```
sudo aptitude install nvidia-settings
```

After it's installed you can find it in 'System->Administration->NVIDIA X Server Settings'.

---

### Post by Zarok on 2008-07-16
Harr, I managed to manually edit Xorg.conf to work with my monitors in all 1080p glory, cause the nvidia settings program wouldn't let me go past 1360x768. This is starting to look promising that I might actually get everything to work . :)

---

### Post by RomeReactor on 2008-07-16
Did you try using nvidia-settings? I think there's an option for that in its 'X Server Display Configuration' section.

You might get a more concrete and relevant answer in the [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334") section of the forums.

---

