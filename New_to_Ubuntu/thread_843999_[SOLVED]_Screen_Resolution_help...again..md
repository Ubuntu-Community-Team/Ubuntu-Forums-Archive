---
title: "[SOLVED] Screen Resolution help...again."
date: 2008-06-29
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-29
My screen resolution can only be set to 1024 x 768, and i modified my xorg.conf last time by adding:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
DefaultDepth 16
     Subsection "Display"
        Depth       16
        Modes "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection
```

I tried this again, but it isn't working for some reason. Is there anything else I can do?

---

### Post by cocopuffz on 2008-06-29
try running the gui for it

gksudo displayconfig-gtk 

and select your monitor (or use generic), or autodetect etc. It should add all of the supported display modes to your xorg file apon reboot.

Been a while for me. You may need to shutdown X to get this to work right... but try it in terminal first and see if it works. 

If all goes well, you're screen resolutions should now be available in the display setup screen.

---

### Post by adobrakic on 2008-06-29
I tried this, but it only stays at 1024 x 768. Also I went over to Graphics Card to see if it has my graphics card installed or w.e, and it said "none". So I went into the list and looked for my graphics card, and i couldn't find mine specifically (s3 prosavage8 ddr), so i just went to "choose driver by name" and i chose 's3'. When I do this, and try to press "Ok" nothing happens. Would my computer maybe run a little better if i got my graphics card to work, rather than it being on "none"?

--edit--

Also, i don't know how to shutdown X, so i couldn't try that. :/

---

### Post by adobrakic on 2008-06-29
Fixed it by adding what i had in my first post and restarting with:

```

sudo reboot -f now

```

---

