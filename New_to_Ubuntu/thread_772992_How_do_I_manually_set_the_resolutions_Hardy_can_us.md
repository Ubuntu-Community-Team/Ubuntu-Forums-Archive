---
title: "How do I manually set the resolutions Hardy can use?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by piratesmack on 2008-04-28
OK well there's basically 3 resolutions that look right on my monitor:
1024x768, 800x600, and 640x480. By default, hardy will try to get a resolution of like 1280x1280. So what I've been doing is adding this to the "Screen"section of my xorg.conf:
```

SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection

```

That makes the default resolution to 1024x768, but when I go to System>Preferences>ScreenResolution it lists a million other weird resolutions. How can I make it only list the 3 resolutions that work right?

I tried:
```

sudo dpkg-reconfigure xserver-xorg

```

But it doesn't give me the option to choose what resolutions I want to use in Hardy. (It did in Gutsy)

Any help would be appreciated

---

### Post by Shazaam on 2008-04-28
Back up your files first.
Try this code carefully.....
```
gksudo displayconfig-gtk
```
From what I have read here the code been has changed for Hardy.

---

### Post by piratesmack on 2008-04-28
> **Shazaam said:**
> Back up your files first.
Try this code carefully.....
```
gksudo displayconfig-gtk
```
From what I have read here the code been has changed for Hardy.

Thanks, but that only seems to let me choose the default resolution. Basically I want to make it so that when I go to System>Preferences>Screen Resolution it only lists the resolutions:
1024x768, 800x600, 640x480

---

### Post by piratesmack on 2008-04-28
anyone?

---

### Post by alienexplorers on 2008-04-29
You could try to setup modelines for the resolution & refresh you want.  A modeline generator can be found here:
> [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)
After creating the modelines you would put them in the monitor section of your xorg.conf file.  An example modeline would look like this:
> # 1024x768 @ 70.00 Hz (GTF) hsync: 56.00 kHz; pclk: 76.16 MHz
  Modeline "1024x768_70.00"  76.16  1024 1080 1192 1360  768 769 772 800  -HSync +Vsync
The modeline above is for 1024x768x70.

---

