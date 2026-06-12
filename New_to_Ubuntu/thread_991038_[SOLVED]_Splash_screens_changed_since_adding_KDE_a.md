---
title: "[SOLVED] Splash screens changed since adding KDE and XFCE"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2008-11-23
I added KDE and XFCE to my Ubuntu install, but what's odd is my splash screens have changed.

My loading screen is Kubuntu (the screen with the progress bar) and my login screen is Xubuntu.

Is there a way to set them both back to Ubuntu (and keep them that way)?

---

### Post by Michael.Godawski on 2008-11-23
You can try to change the login screen via System > Administration > Login Window.

I can remember I had these glitches too, when I installed additional desktops like you; since then I use only one.

---

### Post by drs305 on 2008-11-23
I had the same issue except in only happened when I tried to switch users. the Xubuntu screen always came up. I tried the following commands. The first one didn't work for me but reportedly does for some users. The second one restored my Ubuntu logon screen when I switch users:

```

sudo update-alternatives --config usplash-artwork.so  # may work
sudo apt-get install --reinstall usplash # worked for me

```

---

### Post by Lazy-buntu on 2008-11-23
Thanks, I'm going to reboot and take a look :)

---

### Post by Lazy-buntu on 2008-11-23
I managed to get the Ubuntu login screen back, but the color between screens is still XFCE blue. Could you tell me the hex color for the Ubuntu login brown? Under system administration > login window > (Local Tab > Background Color)?


However, I still have the Kubuntu loading screen with the blue progress bar. Does that have to do with Grub settings?

---

### Post by drs305 on 2008-11-23
> **lazy-buntu said:**
> could you tell me the hex color for the ubuntu login brown? Under system administration > login window > (local tab > background color)?

#dab082

Go into grub or even easier, use StartUp-Manager. It has settings for the usplash screen.
Install it with "sudo apt-get startupmanager". Run via System, Admin, StartUp-Manager. There is a link in my signature line with a tutorial.

---

### Post by Lazy-buntu on 2008-11-23
> **drs305 said:**
> #dab082

Thanks, that's one more thing fixed :lolflag:


Now if I can get my Ubuntu loading screen back I'll be happy :)

---

### Post by Lazy-buntu on 2008-11-23
Using that startup manager, there was an option to switch between the different usplash themes. It was set to kubuntu, so I switched it back to ubuntu, which will hopefully fix my problem. I'll let you know how that turns out.

---

### Post by Lazy-buntu on 2008-11-23
That fixed it :)

I'm going to try switching sessions and seeing if it holds this configuration, but thanks a lot. You've been a great help.

---

### Post by Paqman on 2008-11-23
+1 for startupmanager, it's a really good tool. Should be prettied up a bit and included in the default Ubuntu, IMO.

---

