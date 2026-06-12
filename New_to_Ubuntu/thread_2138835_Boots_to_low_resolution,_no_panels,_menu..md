---
title: "Boots to low resolution, no panels, menu."
date: 2013-04-25
forum: New to Ubuntu
---

### Post by wshore3107 on 2013-04-25
After installing the latest updates and restarting, ubuntu starts in low resolution and I'm unable to see any menu or desktop items. I can see the background and wallpaper and right-click opens the cs-menu but nothing else is visible (appears to be outside of the screen view).

I did attempt unsuccessfully to install Nvidia drivers (failed to install) and I'm assuming that is what is causing my issue.

So ctrl+alt+T takes me to the terminal. Any suggestions on what I can do from there? Ideally I'd like to just get back to the graphics mode I had before (the Nvidia drivers are a whole other issue).

I do have some linux experience (though new to ubuntu). Any suggestions would be greatly appreciated;

Regards,

---

### Post by Bashing-om on 2013-04-25
wshore3107;
Try this from the command line interface (terminal);
, open additional drivers.
From terminal
```
jockey-gtk
``` And from there install a different graphics driver ??
[INDENT=3]hope this helps

[/INDENT]

---

### Post by Feathers McGraw on 2013-04-25
Had this problem before. For me, I completely removed the AMD drivers and their settings and that sorted it out...obviously, your driver is an nvidia one so the solution will be a little different:

```
sudo apt-get remove --purge nvidia*
```

^ the above will uninstall and remove settings for all packages with nvidia at the start of the name. There's one that you'll want to keep, which I believe you can re-install using:

```
sudo apt-get install ubuntu-desktop
```

Then reboot.

Hope this helps,

Feathers

---

### Post by wshore3107 on 2013-04-25
That worked brilliantly, thank you.

1 caveat though; after running the above it just booted to a black screen (and the mouse pointer). I could tell it was running in the higher resolution but it was not giving me the logon screen. I opened a tty1 and tried:

```
sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop
```

then rebooted. All good again (other then the fact I'm graphics driver-less again).

Cheers,

---

### Post by Bashing-om on 2013-04-25
wshore3107;
To see your graphics card and info: Terminal codes:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga
```This line shows if/what driver is loaded:
>   configuration: driver=radeon latency=0 (mine)

Then to change/load a driver I suggest using the Additional Drivers utility.(command line codes work very well too !)[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by Feathers McGraw on 2013-04-25
Which version/distribution are you using?

What exactly did you update before it stopped working? Was it the kernel (requires reboot) or other package updates? If it was packages, can you remember if your graphics driver was updated or not?

Feathers

---

### Post by wshore3107 on 2013-04-29
I "was" running Ubuntu 12.10 (.. I believe) i.e. I was keeping it up to date.

I'm pretty sure what broke my desktop was jockey. I attempted to install the Nvidia drivers using that application and it informed me that it failed (could not install the driver). I happened to reboot due to an update (kernel perhaps?) which was applied (which I'm pretty sure was just coincidental) and got the above mentioned empty desktop.

I'm almost certain it was **not** the update that caused the issue (I don't believe there was any updates relating to graphics, etc..).

Interestingly (to me anyway); I was prompted on the weekend to upgrade to 13.04 which I did. The upgrade went smooth except for it seemed to break my sound. I started working my way through the standard Ubuntu sound troubleshooting guide when I noticed that 1 of the sound cards it was recognizing was part of my (Nvidia) video card. I took a look and 13.04 seemed to now recognize my card (Ubuntu did not before the upgrade) (though no driver was installed).. sooo (to complete the circle) I reinstalled jockey and once again installed the Nvidia drivers (which worked this time), rebooted and now my graphics and sound seem to be working nicely.

So the moral of this whole story seems to be if you're running Nvidia hardware; upgrade to 13.04.

---

