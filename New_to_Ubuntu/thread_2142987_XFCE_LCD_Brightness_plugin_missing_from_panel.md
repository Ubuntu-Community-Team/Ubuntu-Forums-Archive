---
title: "XFCE LCD Brightness plugin missing from panel"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by cougar4u on 2013-05-07
Greetings,

I've run into a problem with XFCE power manager. It comes installed on Lubuntu 13.04 and per recommendations from other posts, I added the plugins as well from the repository. However, the brightness plugin still doesn't show.  The FN toggles do not work for my laptop's brightness (asus ul30vt) and I need a solution to control it. Any ideas? Alternatives apps? Any help would be appreicated :confused:

[IMG]http://i.imgur.com/bB2eo5v.png[/IMG]

Best Regards

---

### Post by pqwoerituytrueiwoq on 2013-05-07
[FONT=courier new]xfce4-power-manager-plugins[/FONT] if for xfce/xubuntu not lxde/lubuntu

---

### Post by Nick8 on 2013-05-07
The brightness setting should be stored in the file /sys/class/backlight/acpi_video0/brightness or /sys/class/backlight/intel_backlight/brightness

Changing the number in one of these files should change the brightness.

To set the default brightness, add an entry to /etc/rc.local, so that the bottom of the file looks like:

```

echo [x] > /sys/class/backlight/acpi_video0/brightness
exit 0

```

or

```

echo [x] > /sys/class/backlight/intel_backlight/brightness
exit 0

```

depending on which file is on your system.

[x] is a number usually from 0 to 10, but it varies between systems.

---

### Post by slickymaster on 2013-05-07
pqwoerituytrueiwoq is right.
The LCD Brightness plugin is included in Xfce4-power-manager, and it allows you to control your LCD brightness level from the xfce4-panel.

---

### Post by Nick8 on 2013-05-07
I think the op has tried installing xfce4-power-manager and xfce4-power-manager-plugins, and it still doesn't work. He said so in [this]("http://ubuntuforums.org/showthread.php?t=2096663") thread.

---

### Post by cougar4u on 2013-05-07
> **Nick8 said:**
> I think the op has tried installing xfce4-power-manager and xfce4-power-manager-plugins, and it still doesn't work. He said so in [this]("http://ubuntuforums.org/showthread.php?t=2096663") thread.

I realized my blunder after making the post. The thread was already marked as solved so I made a new topic.

Thanks for the other replies as well. The command line does indeed work to adjust brightness. I was looking for a more graphical way (if possible). I have installed xfce power manager and the plugins. However, per the screenshot linked above, I still do not see the plugin/applet listed to add to the panel. 

Regards

---

