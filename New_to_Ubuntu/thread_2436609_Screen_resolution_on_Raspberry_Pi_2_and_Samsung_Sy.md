---
title: "Screen resolution on Raspberry Pi 2 and Samsung Syncmaster 193T Monitor"
date: 2020-02-10
forum: New to Ubuntu
---

### Post by marhof on 2020-02-10
Hi all,

I just installed Ubuntu on a Raspberry Pi 2. I have an old Samsung SyncMaster 193T monitor with DVI input, so I connected the monitor with a HDMI to DVI cable, no problems so far. Only, the display resolution on Ubuntu is just 640x480, and I can't change any settings. The maximum resolution of the monitor is 1280x1024. Any ideas how to get a higher resolution on Ubuntu?

Regards,

Mark Hofland

---

### Post by yetimon_64 on 2020-02-10
You may need to do a bit of research into the make of adapter you are using and its capabilities. 

One adapter I used from and old laptop (no HDMI availabe, IIRC it had DVI out) to a 1920x1080 HDMI monitor would at best give me 1024x768 resolution on that HD monitor. I was limited in what the hardware (adapter) would allow me to use. Although you seem to be going the other way to what I did ie. HDMI out to DVI in, I suspect the limiting factor for the resolution may be the adapter itself.

Do you know what brand/model of adapter you are using?

---

### Post by CatKiller on 2020-02-10
Automatic resolution detection is done through EDID. Old monitors were terrible at providing accurate EDID. Adaptors often interfere with EDID even if both the monitor and the graphics device would otherwise have functioning EDID.

There are lots of posts here already about how to manually add the information that would be otherwise provided through EDID. A quick search of your monitor's specifications suggests that you're after ```
HorizSync 30-81
VertRefresh 56-85
```

---

### Post by marhof on 2020-02-11
No, I'm not sure. It's the HDMI output from a RaspBerry PI2.

---

### Post by marhof on 2020-02-12
Thanks, I'll look around in the posts to find settings which are good for me.

---

### Post by Frogs Hair on 2020-02-12
I use an old Sony monitor with my PI and bought an actual HD video converter because my reading indicated that the cables would not work on older monitors. I had purchased some now useless cables first. There might be other options though.

---

### Post by CatKiller on 2020-02-12
> **marhof said:**
> Thanks, I'll look around in the posts to find settings which are good for me.

Well, the settings I gave should be good for your monitor: that's what I searched for.

For the syntax of the thing, you'd create a file called something like **/etc/X11/xorg.conf.d/20-monitor.conf**. In it you'd put something like

```

Section "Monitor"
    Identifier "Default Monitor"
    HorizSync 30-81
    VertRefresh 56-85
EndSection 

```

Restart X and it should pick up the resolutions that your monitor can do.

---

