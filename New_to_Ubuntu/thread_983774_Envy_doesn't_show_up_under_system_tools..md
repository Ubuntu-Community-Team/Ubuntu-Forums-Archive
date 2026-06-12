---
title: "Envy doesn't show up under system tools."
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Roasted on 2008-11-16
I have a Nvidia 9600 GT. I have the restricted drivers installed, but due to unacceptable video tearing in VLC and all other video applications I have, I want to try Envy out and see how it runs. Currently under restricted drivers I have Nvidia drivers 177 installed.

I installed EnvyNG-GTK and it does not show up under the system tools menu and for the life of me I can't figure out why. Can anybody help?

Running Intrepid 64.

---

### Post by lovinglinux on 2008-11-16
You could reboot the machine to see if it shows up. Some applications only appear in the menu after a reboot.

Nevertheless, you can just add a new launcher for Envy with the following command:

```
/usr/share/envy/launcher
```

---

### Post by Roasted on 2008-11-16
It ended up not showing up. However, I found out how to incorporate the nvidia drivers in text mode in the command line. In the end, I ended up uninstalling envy. I was using envy as a means to test my video tearing I'm experiencing. But after disabling compiz, it seems the tearing is gone completely... so my googled answer of "try installing envy instead of restricted drivers" didn't cure the problem! It was compiz.

Hopefully we'll see a fix for it soon... but I'd much rather have a clear DVD picture than compiz, since I watch concert DVDs all the time and use compiz for basically showing off to my friends who are all actually computer illiterate in the first place.

---

### Post by lovinglinux on 2008-11-16
> **Roasted said:**
> It ended up not showing up. However, I found out how to incorporate the nvidia drivers in text mode in the command line. In the end, I ended up uninstalling envy. I was using envy as a means to test my video tearing I'm experiencing. But after disabling compiz, it seems the tearing is gone completely... so my googled answer of "try installing envy instead of restricted drivers" didn't cure the problem! It was compiz.

Hopefully we'll see a fix for it soon... but I'd much rather have a clear DVD picture than compiz, since I watch concert DVDs all the time and use compiz for basically showing off to my friends who are all actually computer illiterate in the first place.

I'm also experiencing the tearing issue and disable compiz is the most reliable way of getting rid of this problem. Unfortunately, is not a solution. For now I have a script that toggles compiz from my remote, so whenever I want to watch a video I just click the button and click again after watching the video.

You can check some alternative solutions for this problem [[COLOR="Red"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=942339").

---

### Post by alwayshere on 2008-11-16
you could use compiz switch 

[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

---

### Post by lovinglinux on 2008-11-16
> **alwayshere said:**
> you could use compiz switch 

[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

I prefer Compiz Fusion Icon, because when I installed Compiz Switch my machine always booted with Metacity. Compiz Fusion Icon is not a single click switch, so you have too choose the window manager from a menu, but since I have a script to easily switch compiz from the remote, I really don't need another application to do that.

Anyway, "Roested" might like it.

---

### Post by Roasted on 2008-11-16
> **lovinglinux said:**
> I prefer Compiz Fusion Icon, because when I installed Compiz Switch my machine always booted with Metacity. Compiz Fusion Icon is not a single click switch, so you have too choose the window manager from a menu, but since I have a script to easily switch compiz from the remote, I really don't need another application to do that.

Anyway, "Roested" might like it.

Wow, yeah. I'm digging that thing. It's nice. Good find! 

Question, though. Originally when I disabled compiz, I lost all of my settings. It seemed like my key bindings were still there, however I had to re-check "enable desktop cube" and "rotate cube" etc. Is that normal? It seems to keep my settings with this compiz switch I just downloaded, but before... why did it do that?

---

### Post by lovinglinux on 2008-11-16
> **Roasted said:**
> Originally when I disabled compiz, I lost all of my settings. It seemed like my key bindings were still there, however I had to re-check "enable desktop cube" and "rotate cube" etc. Is that normal?

No. It isn't.

> **Roasted said:**
> It seems to keep my settings with this compiz switch I just downloaded, but before... why did it do that?

Don't know.

---

