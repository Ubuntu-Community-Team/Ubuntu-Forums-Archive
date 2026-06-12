---
title: "brightness keyboard shortcut not working properly"
date: 2020-07-04
forum: New to Ubuntu
---

### Post by gabriel119435 on 2020-07-04
I currently have a fresh Ubuntu 20.04 installed on my Vostro laptop with Nvidia's MX 230 video card. I installed the proprietary drivers [doing this]("https://gist.github.com/bitsurgeon/b0f4440984c9e60dcd8fe8bbc346c029#secure-boot"). Every time I try to increase or decrease my screen brightness using keyboard shortcuts my entire UI freezes for a little while before actually 'applying' it. Everything works normal using UI brightness sliders as well as executing 
```

sudo su
"echo 200 > /sys/class/backlight/intel_backlight/brightness"

```

Following [this post]("https://ubuntuforums.org/showthread.php?t=2181534"), here's my output:

cat /proc/cmdline
```

BOOT_IMAGE=/boot/vmlinuz-5.4.0-40-generic root=UUID=7163b0a7-caf2-426c-9cb9-ab5d1e148018 ro quiet splash vt.handoff=7

```

lspci -k | grep -A3 VGA
```

00:02.0 VGA compatible controller: Intel Corporation UHD Graphics (rev 02)
    DeviceName: To Be Filled by O.E.M.
    Subsystem: Dell UHD Graphics
    Kernel driver in use: i915

```

for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

/sys/class/backlight/intel_backlight
120000
120000
120000

```

pastebinit /var/log/Xorg.0.log
[here's my pastebin]("https://paste.ubuntu.com/p/7v5VjvDPJG/")

here's additional info about my nVidia card:
[IMG]https://i.imgur.com/ZfAjbez.png[/IMG]
[IMG]https://imgur.com/a/KIUwVBB[/IMG]
[IMG]https://imgur.com/a/KIUwVBB[/IMG]

---

