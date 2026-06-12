---
title: "What WM do you like."
date: 2010-05-26
forum: Recurring Discussions
---

### Post by dragos240 on 2010-05-26
I've tried lots of window managers, including DEs as well. I really liked GNOME and KDE, and grew accustomed to them, but under a small computer, then didn't run well. So I searched through many window managers. At first I liked Fluxbox, it was nice simple and light, but it lacked touchpad support that I needed. I later figured out that that would need to be configured in HAL, which I couldn't find a driver for. I just wanted to stop using the mouse because of this, the buttons on the mouse require a lot of force to push down on, and therefore were nearly unusable. Today, I tried ratpoison, It's just great. No need for the mouse to get around, I just love it, while I still need to use the mouse for browsers, I still use it a lot less. I was annoyed at first because the menu button combo was Ctrl + T, I use that to open a new tab. But I figured out that If I did Ctrl + T T, it did the same thing. Not too bad. I think I'll stick with this WM for a while. But enough about my favorite WM. What's yours?

---

### Post by slackthumbz on 2010-05-26
compiz ;)

---

### Post by RiceMonster on 2010-05-26
The only lightweight wm I really like is dwm. I find most lightweight wms to have messy config files, or I tend to spend hours configuring them, only to get them sort of how I want them. dwm is a lot cleaner. Still though, I prefer to use GNOME, KDE or Xfce. dwm is my choice for minimal setups (which I don't often use).

Also, configure your touchpad via xorg and it will work under any wm. Check this out: [http://wiki.archlinux.org/index.php/Touchpad_Synaptics](http://wiki.archlinux.org/index.php/Touchpad_Synaptics). While it's from the Arch wiki, it will work on most distros. It even works on FreeBSD.

---

### Post by dragos240 on 2010-05-26
> **RiceMonster said:**
> The only lightweight wm I really like is dwm. I find most lightweight wms to have messy config files, or I tend to spend hours configuring them, only to get them sort of how I want them. dwm is a lot cleaner. Still though, I prefer to use GNOME, KDE or Xfce. dwm is my choice for minimal setups (which I don't often use).

Also, configure your touchpad via xorg and it will work under any wm. Check this out: [http://wiki.archlinux.org/index.php/Touchpad_Synaptics](http://wiki.archlinux.org/index.php/Touchpad_Synaptics). While it's from the Arch wiki, it will work on most distros. It even works on FreeBSD.

Thanks ricemonster. By the way, who is that in your avvy?

---

### Post by jerenept on 2010-05-26
Compiz ... Wobbly Windows WooHoo!

---

### Post by Shining Arcanine on 2010-05-26
I use Kwin.

---

### Post by RiceMonster on 2010-05-26
> **dragos240 said:**
> Thanks ricemonster. By the way, who is that in your avvy?

It's Hinagiku from Hayate no Gotoku

---

### Post by chessnerd on 2010-05-26
On my laptop, I use Compiz. On my desktop, I use Metacity. On my older desktop, I use the Xfce4 WM. Why? Because the laptop and newer desktop use Gnome while the older uses Xfce.

As far as windows managers and desktop environments are concerned, on newer hardware I prefer Gnome. KDE is okay, but something about it just makes it seem tougher to use for me. I have used it for extended periods of time over the course of a few weeks and liked its features a lot, but something just didn't feel right about it. I'm hoping that 4.5 will be the build that pushes me over, because I don't like how the Gnome development is going.

For lower end machines, I prefer Xfce (vanilla Xfce, not Xubuntu) which I've found to be light-weight and usable. If that doesn't suit you, LXDE is fine. 

If you are set on a window manager instead of a desktop environment, I've used Openbox and found that to be enjoyable. Also, IceWM is pretty good.

---

### Post by handy on 2010-05-26
Openbox/xfce4-panel must be all I need, I haven't changed it for over 18 months.

---

### Post by chessnerd on 2010-05-26
> **handy said:**
> Openbox/xfce4-panel must be all I need, I haven't changed it for over 18 months.

I've heard that's a good combination. How much RAM does that setup require compared to just regular Xfce? My install of Xfce uses about 94 MB on boot.

---

### Post by handy on 2010-05-27
> **chessnerd said:**
> I've heard that's a good combination. How much RAM does that setup require compared to just regular Xfce? My install of Xfce uses about 94 MB on boot.

I run Arch, so the system is very personalised, though looking at the xfce4-panel output, I could perhaps trim down its resource usage, but I won't bother as I've got plenty of resources & it is all fast enough for me. :)

I'll post the memory usage output for Openbox first followed by xfce4-panel below.

**Openbox:**

```
handy /mnt/store/pkg/vid/.tmp  $  pmap 4036
4036:   /usr/bin/openbox
0000000000400000    328K r-x--  /usr/bin/openbox
0000000000652000      4K rw---  /usr/bin/openbox
0000000000653000     20K rw---    [ anon ]
0000000002415000   6060K rw---    [ anon ]
00007f967ace2000    608K r----  /usr/share/fonts/TTF/DejaVuSans.ttf
00007f967ad7a000    560K r----  /usr/share/fonts/TTF/DejaVuSans-Bold.ttf
00007f967ae06000    180K r--s-  /var/cache/fontconfig/f6b893a7224233d96cb72fd88691c0b4-le64.cache-3
00007f967ae33000     48K r-x--  /lib/libnss_files-2.11.1.so
00007f967ae3f000   2044K -----  /lib/libnss_files-2.11.1.so
00007f967b03e000      4K r----  /lib/libnss_files-2.11.1.so
00007f967b03f000      4K rw---  /lib/libnss_files-2.11.1.so
00007f967b040000    152K r-x--  /usr/lib/libexpat.so.1.5.2
00007f967b066000   2044K -----  /usr/lib/libexpat.so.1.5.2
00007f967b265000     12K rw---  /usr/lib/libexpat.so.1.5.2
00007f967b268000     20K r-x--  /usr/lib/libXdmcp.so.6.0.0
00007f967b26d000   2044K -----  /usr/lib/libXdmcp.so.6.0.0
00007f967b46c000      4K rw---  /usr/lib/libXdmcp.so.6.0.0
00007f967b46d000      8K r-x--  /usr/lib/libXau.so.6.0.0
00007f967b46f000   2044K -----  /usr/lib/libXau.so.6.0.0
00007f967b66e000      4K rw---  /usr/lib/libXau.so.6.0.0
00007f967b66f000    516K r-x--  /lib/libm-2.11.1.so
00007f967b6f0000   2044K -----  /lib/libm-2.11.1.so
00007f967b8ef000      4K r----  /lib/libm-2.11.1.so
00007f967b8f0000      4K rw---  /lib/libm-2.11.1.so
00007f967b8f1000     96K r-x--  /usr/lib/libz.so.1.2.5
00007f967b909000   2044K -----  /usr/lib/libz.so.1.2.5
00007f967bb08000      4K rw---  /usr/lib/libz.so.1.2.5
00007f967bb09000    192K r-x--  /lib/libpcre.so.0.0.1
00007f967bb39000   2044K -----  /lib/libpcre.so.0.0.1
00007f967bd38000      4K rw---  /lib/libpcre.so.0.0.1
00007f967bd39000      8K r-x--  /lib/libdl-2.11.1.so
00007f967bd3b000   2048K -----  /lib/libdl-2.11.1.so
00007f967bf3b000      4K r----  /lib/libdl-2.11.1.so
00007f967bf3c000      4K rw---  /lib/libdl-2.11.1.so
00007f967bf3d000     12K r-x--  /lib/libuuid.so.1.3.0
00007f967bf40000   2048K -----  /lib/libuuid.so.1.3.0
00007f967c140000      4K rw---  /lib/libuuid.so.1.3.0
00007f967c141000    580K r-x--  /usr/lib/libfreetype.so.6.4.0
00007f967c1d2000   2048K -----  /usr/lib/libfreetype.so.6.4.0
00007f967c3d2000     24K rw---  /usr/lib/libfreetype.so.6.4.0
00007f967c3d8000    200K r-x--  /usr/lib/libfontconfig.so.1.4.4
00007f967c40a000   2048K -----  /usr/lib/libfontconfig.so.1.4.4
00007f967c60a000      8K rw---  /usr/lib/libfontconfig.so.1.4.4
00007f967c60c000     76K r-x--  /usr/lib/libXft.so.2.1.13
00007f967c61f000   2048K -----  /usr/lib/libXft.so.2.1.13
00007f967c81f000      4K rw---  /usr/lib/libXft.so.2.1.13
00007f967c820000     28K r-x--  /lib/librt-2.11.1.so
00007f967c827000   2044K -----  /lib/librt-2.11.1.so
00007f967ca26000      4K r----  /lib/librt-2.11.1.so
00007f967ca27000      4K rw---  /lib/librt-2.11.1.so
00007f967ca28000     16K r-x--  /usr/lib/libgthread-2.0.so.0.2400.1
00007f967ca2c000   2044K -----  /usr/lib/libgthread-2.0.so.0.2400.1
00007f967cc2b000      4K rw---  /usr/lib/libgthread-2.0.so.0.2400.1
00007f967cc2c000     12K r-x--  /usr/lib/libgmodule-2.0.so.0.2400.1
00007f967cc2f000   2044K -----  /usr/lib/libgmodule-2.0.so.0.2400.1
00007f967ce2e000      4K rw---  /usr/lib/libgmodule-2.0.so.0.2400.1
00007f967ce2f000    280K r-x--  /usr/lib/libgobject-2.0.so.0.2400.1
00007f967ce75000   2048K -----  /usr/lib/libgobject-2.0.so.0.2400.1
00007f967d075000      8K rw---  /usr/lib/libgobject-2.0.so.0.2400.1
00007f967d077000    284K r-x--  /usr/lib/libpango-1.0.so.0.2800.0
00007f967d0be000   2044K -----  /usr/lib/libpango-1.0.so.0.2800.0
00007f967d2bd000     12K rw---  /usr/lib/libpango-1.0.so.0.2800.0
00007f967d2c0000    160K r-x--  /usr/lib/libpangoft2-1.0.so.0.2800.0
00007f967d2e8000   2044K -----  /usr/lib/libpangoft2-1.0.so.0.2800.0
00007f967d4e7000      8K rw---  /usr/lib/libpangoft2-1.0.so.0.2800.0
00007f967d4e9000     28K r-x--  /usr/lib/libpangoxft-1.0.so.0.2800.0
00007f967d4f0000   2044K -----  /usr/lib/libpangoxft-1.0.so.0.2800.0
00007f967d6ef000      4K rw---  /usr/lib/libpangoxft-1.0.so.0.2800.0
00007f967d6f0000    108K r-x--  /usr/lib/libxcb.so.1.1.0
00007f967d70b000   2044K -----  /usr/lib/libxcb.so.1.1.0
00007f967d90a000      4K rw---  /usr/lib/libxcb.so.1.1.0
00007f967d90b000     12K r-x--  /usr/lib/libxcb-atom.so.1.0.0
00007f967d90e000   2048K -----  /usr/lib/libxcb-atom.so.1.0.0
00007f967db0e000      4K rw---  /usr/lib/libxcb-atom.so.1.0.0
00007f967db0f000     12K r-x--  /usr/lib/libxcb-event.so.1.0.0
00007f967db12000   2048K -----  /usr/lib/libxcb-event.so.1.0.0
00007f967dd12000      4K rw---  /usr/lib/libxcb-event.so.1.0.0
00007f967dd13000      8K r-x--  /usr/lib/libxcb-aux.so.0.0.0
00007f967dd15000   2048K -----  /usr/lib/libxcb-aux.so.0.0.0
00007f967df15000      4K rw---  /usr/lib/libxcb-aux.so.0.0.0
00007f967df16000     20K r-x--  /usr/lib/libXfixes.so.3.1.0
00007f967df1b000   2044K -----  /usr/lib/libXfixes.so.3.1.0
00007f967e11a000      4K rw---  /usr/lib/libXfixes.so.3.1.0
00007f967e11b000     36K r-x--  /usr/lib/libXrender.so.1.3.0
00007f967e124000   2044K -----  /usr/lib/libXrender.so.1.3.0
00007f967e323000      4K rw---  /usr/lib/libXrender.so.1.3.0
00007f967e324000   1352K r-x--  /lib/libc-2.11.1.so
00007f967e476000   2048K -----  /lib/libc-2.11.1.so
00007f967e676000     16K r----  /lib/libc-2.11.1.so
00007f967e67a000      4K rw---  /lib/libc-2.11.1.so
00007f967e67b000     20K rw---    [ anon ]
00007f967e680000     92K r-x--  /lib/libpthread-2.11.1.so
00007f967e697000   2044K -----  /lib/libpthread-2.11.1.so
00007f967e896000      4K r----  /lib/libpthread-2.11.1.so
00007f967e897000      4K rw---  /lib/libpthread-2.11.1.so
00007f967e898000     16K rw---    [ anon ]
00007f967e89c000   1288K r-x--  /usr/lib/libxml2.so.2.7.7
00007f967e9de000   2048K -----  /usr/lib/libxml2.so.2.7.7
00007f967ebde000     36K rw---  /usr/lib/libxml2.so.2.7.7
00007f967ebe7000      8K rw---    [ anon ]
00007f967ebe9000    892K r-x--  /usr/lib/libglib-2.0.so.0.2400.1
00007f967ecc8000   2044K -----  /usr/lib/libglib-2.0.so.0.2400.1
00007f967eec7000      8K rw---  /usr/lib/libglib-2.0.so.0.2400.1
00007f967eec9000   1228K r-x--  /usr/lib/libX11.so.6.3.0
00007f967effc000   2048K -----  /usr/lib/libX11.so.6.3.0
00007f967f1fc000     24K rw---  /usr/lib/libX11.so.6.3.0
00007f967f202000     92K r-x--  /usr/lib/libICE.so.6.3.0
00007f967f219000   2044K -----  /usr/lib/libICE.so.6.3.0
00007f967f418000      4K rw---  /usr/lib/libICE.so.6.3.0
00007f967f419000     16K rw---    [ anon ]
00007f967f41d000     28K r-x--  /usr/lib/libSM.so.6.0.1
00007f967f424000   2048K -----  /usr/lib/libSM.so.6.0.1
00007f967f624000      4K rw---  /usr/lib/libSM.so.6.0.1
00007f967f625000     16K r-x--  /usr/lib/libobparser.so.21.0.9
00007f967f629000   2044K -----  /usr/lib/libobparser.so.21.0.9
00007f967f828000      4K rw---  /usr/lib/libobparser.so.21.0.9
00007f967f829000     88K r-x--  /usr/lib/libobrender.so.21.0.9
00007f967f83f000   2044K -----  /usr/lib/libobrender.so.21.0.9
00007f967fa3e000      4K rw---  /usr/lib/libobrender.so.21.0.9
00007f967fa3f000     36K r-x--  /usr/lib/libstartup-notification-1.so.0.0.0
00007f967fa48000   2044K -----  /usr/lib/libstartup-notification-1.so.0.0.0
00007f967fc47000      4K rw---  /usr/lib/libstartup-notification-1.so.0.0.0
00007f967fc48000     36K r-x--  /usr/lib/libXcursor.so.1.0.2
00007f967fc51000   2044K -----  /usr/lib/libXcursor.so.1.0.2
00007f967fe50000      4K rw---  /usr/lib/libXcursor.so.1.0.2
00007f967fe51000     68K r-x--  /usr/lib/libXext.so.6.4.0
00007f967fe62000   2048K -----  /usr/lib/libXext.so.6.4.0
00007f9680062000      4K rw---  /usr/lib/libXext.so.6.4.0
00007f9680063000     32K r-x--  /usr/lib/libXrandr.so.2.2.0
00007f968006b000   2044K -----  /usr/lib/libXrandr.so.2.2.0
00007f968026a000      4K rw---  /usr/lib/libXrandr.so.2.2.0
00007f968026b000      8K r-x--  /usr/lib/libXinerama.so.1.0.0
00007f968026d000   2044K -----  /usr/lib/libXinerama.so.1.0.0
00007f968046c000      4K rw---  /usr/lib/libXinerama.so.1.0.0
00007f968046d000    120K r-x--  /lib/ld-2.11.1.so
00007f96804a4000   1732K r----  /usr/lib/locale/locale-archive
00007f9680655000     68K rw---    [ anon ]
00007f9680680000     36K r--s-  /var/cache/fontconfig/d62e99ef547d1d24cdb1bd22ec1a2976-le64.cache-3
00007f9680689000      4K rw---    [ anon ]
00007f968068a000      4K r----  /lib/ld-2.11.1.so
00007f968068b000      4K rw---  /lib/ld-2.11.1.so
00007f968068c000      4K rw---    [ anon ]
00007fffe86a8000     84K rw---    [ stack ]
00007fffe86c1000      4K r-x--    [ anon ]
ffffffffff600000      4K r-x--    [ anon ]
 total            98120K 
```



**xfce4-panel:**

```
handy /mnt/store/pkg/vid/.tmp  $  pmap 4057
4057:   xfce4-panel
0000000000400000     96K r-x--  /usr/bin/xfce4-panel
0000000000617000      8K rw---  /usr/bin/xfce4-panel
0000000001d25000   2152K rw---    [ anon ]
00007f6666f20000  44660K r----  /usr/share/icons/gnome/icon-theme.cache
00007f6669abd000   1704K r----  /usr/share/icons/hicolor/icon-theme.cache
00007f6669c67000    384K rw-s-    [ shmid=0x18001 ]
00007f6669cc7000      8K r-x--  /usr/lib/gconv/ISO8859-1.so
00007f6669cc9000   2044K -----  /usr/lib/gconv/ISO8859-1.so
00007f6669ec8000      4K r----  /usr/lib/gconv/ISO8859-1.so
00007f6669ec9000      4K rw---  /usr/lib/gconv/ISO8859-1.so
00007f6669eca000    608K r----  /usr/share/fonts/TTF/DejaVuSans.ttf
00007f6669f62000    180K r--s-  /var/cache/fontconfig/f6b893a7224233d96cb72fd88691c0b4-le64.cache-3
00007f6669f8f000      8K r-x--  /usr/lib/libXRes.so.1.0.0
00007f6669f91000   2044K -----  /usr/lib/libXRes.so.1.0.0
00007f666a190000      4K rw---  /usr/lib/libXRes.so.1.0.0
00007f666a191000    240K r-x--  /usr/lib/libwnck-1.so.22.3.26
00007f666a1cd000   2048K -----  /usr/lib/libwnck-1.so.22.3.26
00007f666a3cd000      8K rw---  /usr/lib/libwnck-1.so.22.3.26
00007f666a3f2000     16K r-x--  /usr/lib/xfce4/panel-plugins/libpager.so
00007f666a3f6000   2044K -----  /usr/lib/xfce4/panel-plugins/libpager.so
00007f666a5f5000      4K rw---  /usr/lib/xfce4/panel-plugins/libpager.so
00007f666a5f6000     36K r-x--  /usr/lib/xfce4/panel-plugins/libsystray.so
00007f666a5ff000   2044K -----  /usr/lib/xfce4/panel-plugins/libsystray.so
00007f666a7fe000      4K rw---  /usr/lib/xfce4/panel-plugins/libsystray.so
00007f666a7ff000     12K r-x--  /usr/lib/xfce4/panel-plugins/libseparator.so
00007f666a802000   2044K -----  /usr/lib/xfce4/panel-plugins/libseparator.so
00007f666aa01000      4K rw---  /usr/lib/xfce4/panel-plugins/libseparator.so
00007f666aa02000     32K r-x--  /usr/lib/xfce4/panel-plugins/libclock.so
00007f666aa0a000   2048K -----  /usr/lib/xfce4/panel-plugins/libclock.so
00007f666ac0a000      4K rw---  /usr/lib/xfce4/panel-plugins/libclock.so
00007f666ac0b000     36K r-x--  /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
00007f666ac14000   2048K -----  /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
00007f666ae14000      4K rw---  /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
00007f666ae15000     48K r-x--  /lib/libnss_files-2.11.1.so
00007f666ae21000   2044K -----  /lib/libnss_files-2.11.1.so
00007f666b020000      4K r----  /lib/libnss_files-2.11.1.so
00007f666b021000      4K rw---  /lib/libnss_files-2.11.1.so
00007f666b022000     20K r-x--  /usr/lib/libXdmcp.so.6.0.0
00007f666b027000   2044K -----  /usr/lib/libXdmcp.so.6.0.0
00007f666b226000      4K rw---  /usr/lib/libXdmcp.so.6.0.0
00007f666b227000      8K r-x--  /usr/lib/libXau.so.6.0.0
00007f666b229000   2044K -----  /usr/lib/libXau.so.6.0.0
00007f666b428000      4K rw---  /usr/lib/libXau.so.6.0.0
00007f666b429000     12K r-x--  /usr/lib/libxcb-atom.so.1.0.0
00007f666b42c000   2048K -----  /usr/lib/libxcb-atom.so.1.0.0
00007f666b62c000      4K rw---  /usr/lib/libxcb-atom.so.1.0.0
00007f666b62d000     12K r-x--  /usr/lib/libxcb-event.so.1.0.0
00007f666b630000   2048K -----  /usr/lib/libxcb-event.so.1.0.0
00007f666b830000      4K rw---  /usr/lib/libxcb-event.so.1.0.0
00007f666b831000      8K r-x--  /usr/lib/libxcb-aux.so.0.0.0
00007f666b833000   2048K -----  /usr/lib/libxcb-aux.so.0.0.0
00007f666ba33000      4K rw---  /usr/lib/libxcb-aux.so.0.0.0
00007f666ba34000     12K r-x--  /lib/libuuid.so.1.3.0
00007f666ba37000   2048K -----  /lib/libuuid.so.1.3.0
00007f666bc37000      4K rw---  /lib/libuuid.so.1.3.0
00007f666bc38000    152K r-x--  /usr/lib/libexpat.so.1.5.2
00007f666bc5e000   2044K -----  /usr/lib/libexpat.so.1.5.2
00007f666be5d000     12K rw---  /usr/lib/libexpat.so.1.5.2
00007f666be60000     28K r-x--  /usr/lib/libxcb-render.so.0.0.0
00007f666be67000   2048K -----  /usr/lib/libxcb-render.so.0.0.0
00007f666c067000      4K rw---  /usr/lib/libxcb-render.so.0.0.0
00007f666c068000     12K r-x--  /usr/lib/libxcb-render-util.so.0.0.0
00007f666c06b000   2044K -----  /usr/lib/libxcb-render-util.so.0.0.0
00007f666c26a000      4K rw---  /usr/lib/libxcb-render-util.so.0.0.0
00007f666c26b000    372K r-x--  /usr/lib/libpixman-1.so.0.18.2
00007f666c2c8000   2048K -----  /usr/lib/libpixman-1.so.0.18.2
00007f666c4c8000     16K rw---  /usr/lib/libpixman-1.so.0.18.2
00007f666c4cc000     76K r-x--  /lib/libresolv-2.11.1.so
00007f666c4df000   2048K -----  /lib/libresolv-2.11.1.so
00007f666c6df000      4K r----  /lib/libresolv-2.11.1.so
00007f666c6e0000      4K rw---  /lib/libresolv-2.11.1.so
00007f666c6e1000      8K rw---    [ anon ]
00007f666c6e3000    108K r-x--  /usr/lib/libxcb.so.1.1.0
00007f666c6fe000   2044K -----  /usr/lib/libxcb.so.1.1.0
00007f666c8fd000      4K rw---  /usr/lib/libxcb.so.1.1.0
00007f666c8fe000      8K r-x--  /lib/libdl-2.11.1.so
00007f666c900000   2048K -----  /lib/libdl-2.11.1.so
00007f666cb00000      4K r----  /lib/libdl-2.11.1.so
00007f666cb01000      4K rw---  /lib/libdl-2.11.1.so
00007f666cb02000    192K r-x--  /lib/libpcre.so.0.0.1
00007f666cb32000   2044K -----  /lib/libpcre.so.0.0.1
00007f666cd31000      4K rw---  /lib/libpcre.so.0.0.1
00007f666cd32000     96K r-x--  /usr/lib/libz.so.1.2.5
00007f666cd4a000   2044K -----  /usr/lib/libz.so.1.2.5
00007f666cf49000      4K rw---  /usr/lib/libz.so.1.2.5
00007f666cf4a000    160K r-x--  /usr/lib/libpng14.so.14.1.0
00007f666cf72000   2044K -----  /usr/lib/libpng14.so.14.1.0
00007f666d171000      4K rw---  /usr/lib/libpng14.so.14.1.0
00007f666d172000     20K r-x--  /usr/lib/libXfixes.so.3.1.0
00007f666d177000   2044K -----  /usr/lib/libXfixes.so.3.1.0
00007f666d376000      4K rw---  /usr/lib/libXfixes.so.3.1.0
00007f666d377000      8K r-x--  /usr/lib/libXdamage.so.1.1.0
00007f666d379000   2044K -----  /usr/lib/libXdamage.so.1.1.0
00007f666d578000      4K rw---  /usr/lib/libXdamage.so.1.1.0
00007f666d579000      8K r-x--  /usr/lib/libXcomposite.so.1.0.0
00007f666d57b000   2044K -----  /usr/lib/libXcomposite.so.1.0.0
00007f666d77a000      4K rw---  /usr/lib/libXcomposite.so.1.0.0
00007f666d77b000     36K r-x--  /usr/lib/libXcursor.so.1.0.2
00007f666d784000   2044K -----  /usr/lib/libXcursor.so.1.0.2
00007f666d983000      4K rw---  /usr/lib/libXcursor.so.1.0.2
00007f666d984000     32K r-x--  /usr/lib/libXrandr.so.2.2.0
00007f666d98c000   2044K -----  /usr/lib/libXrandr.so.2.2.0
00007f666db8b000      4K rw---  /usr/lib/libXrandr.so.2.2.0
00007f666db8c000     56K r-x--  /usr/lib/libXi.so.6.1.0
00007f666db9a000   2044K -----  /usr/lib/libXi.so.6.1.0
00007f666dd99000      4K rw---  /usr/lib/libXi.so.6.1.0
00007f666dd9a000      8K r-x--  /usr/lib/libXinerama.so.1.0.0
00007f666dd9c000   2044K -----  /usr/lib/libXinerama.so.1.0.0
00007f666df9b000      4K rw---  /usr/lib/libXinerama.so.1.0.0
00007f666df9c000     36K r-x--  /usr/lib/libXrender.so.1.3.0
00007f666dfa5000   2044K -----  /usr/lib/libXrender.so.1.3.0
00007f666e1a4000      4K rw---  /usr/lib/libXrender.so.1.3.0
00007f666e1a5000     68K r-x--  /usr/lib/libXext.so.6.4.0
00007f666e1b6000   2048K -----  /usr/lib/libXext.so.6.4.0
00007f666e3b6000      4K rw---  /usr/lib/libXext.so.6.4.0
00007f666e3b7000     36K r-x--  /usr/lib/libstartup-notification-1.so.0.0.0
00007f666e3c0000   2044K -----  /usr/lib/libstartup-notification-1.so.0.0.0
00007f666e5bf000      4K rw---  /usr/lib/libstartup-notification-1.so.0.0.0
00007f666e5c0000     92K r-x--  /usr/lib/libICE.so.6.3.0
00007f666e5d7000   2044K -----  /usr/lib/libICE.so.6.3.0
00007f666e7d6000      4K rw---  /usr/lib/libICE.so.6.3.0
00007f666e7d7000     16K rw---    [ anon ]
00007f666e7db000     28K r-x--  /usr/lib/libSM.so.6.0.1
00007f666e7e2000   2048K -----  /usr/lib/libSM.so.6.0.1
00007f666e9e2000      4K rw---  /usr/lib/libSM.so.6.0.1
00007f666e9e3000     28K r-x--  /lib/librt-2.11.1.so
00007f666e9ea000   2044K -----  /lib/librt-2.11.1.so
00007f666ebe9000      4K r----  /lib/librt-2.11.1.so
00007f666ebea000      4K rw---  /lib/librt-2.11.1.so
00007f666ebeb000     16K r-x--  /usr/lib/libgthread-2.0.so.0.2400.1
00007f666ebef000   2044K -----  /usr/lib/libgthread-2.0.so.0.2400.1
00007f666edee000      4K rw---  /usr/lib/libgthread-2.0.so.0.2400.1
00007f666edef000    200K r-x--  /usr/lib/libfontconfig.so.1.4.4
00007f666ee21000   2048K -----  /usr/lib/libfontconfig.so.1.4.4
00007f666f021000      8K rw---  /usr/lib/libfontconfig.so.1.4.4
00007f666f023000    580K r-x--  /usr/lib/libfreetype.so.6.4.0
00007f666f0b4000   2048K -----  /usr/lib/libfreetype.so.6.4.0
00007f666f2b4000     24K rw---  /usr/lib/libfreetype.so.6.4.0
00007f666f2ba000    284K r-x--  /usr/lib/libpango-1.0.so.0.2800.0
00007f666f301000   2044K -----  /usr/lib/libpango-1.0.so.0.2800.0
00007f666f500000     12K rw---  /usr/lib/libpango-1.0.so.0.2800.0
00007f666f503000    480K r-x--  /usr/lib/libcairo.so.2.10800.10
00007f666f57b000   2048K -----  /usr/lib/libcairo.so.2.10800.10
00007f666f77b000     12K rw---  /usr/lib/libcairo.so.2.10800.10
00007f666f77e000     44K r-x--  /usr/lib/libpangocairo-1.0.so.0.2800.0
00007f666f789000   2044K -----  /usr/lib/libpangocairo-1.0.so.0.2800.0
00007f666f988000      4K rw---  /usr/lib/libpangocairo-1.0.so.0.2800.0
00007f666f989000    160K r-x--  /usr/lib/libpangoft2-1.0.so.0.2800.0
00007f666f9b1000   2044K -----  /usr/lib/libpangoft2-1.0.so.0.2800.0
00007f666fbb0000      8K rw---  /usr/lib/libpangoft2-1.0.so.0.2800.0
00007f666fbb2000    704K r-x--  /usr/lib/libgio-2.0.so.0.2400.1
00007f666fc62000   2044K -----  /usr/lib/libgio-2.0.so.0.2400.1
00007f666fe61000     12K rw---  /usr/lib/libgio-2.0.so.0.2400.1
00007f666fe64000      4K rw---    [ anon ]
00007f666fe65000    116K r-x--  /usr/lib/libatk-1.0.so.0.3009.1
00007f666fe82000   2048K -----  /usr/lib/libatk-1.0.so.0.3009.1
00007f6670082000     12K rw---  /usr/lib/libatk-1.0.so.0.3009.1
00007f6670085000   1352K r-x--  /lib/libc-2.11.1.so
00007f66701d7000   2048K -----  /lib/libc-2.11.1.so
00007f66703d7000     16K r----  /lib/libc-2.11.1.so
00007f66703db000      4K rw---  /lib/libc-2.11.1.so
00007f66703dc000     20K rw---    [ anon ]
00007f66703e1000     92K r-x--  /lib/libpthread-2.11.1.so
00007f66703f8000   2044K -----  /lib/libpthread-2.11.1.so
00007f66705f7000      4K r----  /lib/libpthread-2.11.1.so
00007f66705f8000      4K rw---  /lib/libpthread-2.11.1.so
00007f66705f9000     16K rw---    [ anon ]
00007f66705fd000    516K r-x--  /lib/libm-2.11.1.so
00007f667067e000   2044K -----  /lib/libm-2.11.1.so
00007f667087d000      4K r----  /lib/libm-2.11.1.so
00007f667087e000      4K rw---  /lib/libm-2.11.1.so
00007f667087f000   1228K r-x--  /usr/lib/libX11.so.6.3.0
00007f66709b2000   2048K -----  /usr/lib/libX11.so.6.3.0
00007f6670bb2000     24K rw---  /usr/lib/libX11.so.6.3.0
00007f6670bb8000    892K r-x--  /usr/lib/libglib-2.0.so.0.2400.1
00007f6670c97000   2044K -----  /usr/lib/libglib-2.0.so.0.2400.1
00007f6670e96000      8K rw---  /usr/lib/libglib-2.0.so.0.2400.1
00007f6670e98000     12K r-x--  /usr/lib/libgmodule-2.0.so.0.2400.1
00007f6670e9b000   2044K -----  /usr/lib/libgmodule-2.0.so.0.2400.1
00007f667109a000      4K rw---  /usr/lib/libgmodule-2.0.so.0.2400.1
00007f667109b000    280K r-x--  /usr/lib/libgobject-2.0.so.0.2400.1
00007f66710e1000   2048K -----  /usr/lib/libgobject-2.0.so.0.2400.1
00007f66712e1000      8K rw---  /usr/lib/libgobject-2.0.so.0.2400.1
00007f66712e3000    128K r-x--  /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00007f6671303000   2048K -----  /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00007f6671503000      4K rw---  /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00007f6671504000    676K r-x--  /usr/lib/libgdk-x11-2.0.so.0.2000.1
00007f66715ad000   2048K -----  /usr/lib/libgdk-x11-2.0.so.0.2000.1
00007f66717ad000     20K rw---  /usr/lib/libgdk-x11-2.0.so.0.2000.1
00007f66717b2000     60K r-x--  /usr/lib/libxfce4util.so.4.1.1
00007f66717c1000   2044K -----  /usr/lib/libxfce4util.so.4.1.1
00007f66719c0000      4K rw---  /usr/lib/libxfce4util.so.4.1.1
00007f66719c1000      4K rw---    [ anon ]
00007f66719c2000   4232K r-x--  /usr/lib/libgtk-x11-2.0.so.0.2000.1
00007f6671de4000   2044K -----  /usr/lib/libgtk-x11-2.0.so.0.2000.1
00007f6671fe3000     44K rw---  /usr/lib/libgtk-x11-2.0.so.0.2000.1
00007f6671fee000      8K rw---    [ anon ]
00007f6671ff0000    340K r-x--  /usr/lib/libxfcegui4.so.4.3.0
00007f6672045000   2048K -----  /usr/lib/libxfcegui4.so.4.3.0
00007f6672245000     16K rw---  /usr/lib/libxfcegui4.so.4.3.0
00007f6672249000     68K r-x--  /usr/lib/libxfce4panel.so.1.1.2
00007f667225a000   2044K -----  /usr/lib/libxfce4panel.so.1.1.2
00007f6672459000      4K rw---  /usr/lib/libxfce4panel.so.1.1.2
00007f667245a000    120K r-x--  /lib/ld-2.11.1.so
00007f667248c000   1732K r----  /usr/lib/locale/locale-archive
00007f667263d000     88K rw---    [ anon ]
00007f667266d000     36K r--s-  /var/cache/fontconfig/d62e99ef547d1d24cdb1bd22ec1a2976-le64.cache-3
00007f6672676000      4K rw---    [ anon ]
00007f6672677000      4K r----  /lib/ld-2.11.1.so
00007f6672678000      4K rw---  /lib/ld-2.11.1.so
00007f6672679000      4K rw---    [ anon ]
00007fff4c829000     88K rw---    [ stack ]
00007fff4c8cd000      4K r-x--    [ anon ]
ffffffffff600000      4K r-x--    [ anon ]
 total           189780K

 
```

---

### Post by chessnerd on 2010-05-27
> **handy said:**
> I run Arch, so the system is very personalised, though looking at the xfce4-panel output, I could perhaps trim down its resource usage, but I won't bother as I've got plenty of resources & it is all fast enough for me. :)

I'll post the memory usage output for Openbox first followed by xfce4-panel below.

Looks like you posted xfce4-panel twice. :)

EDIT: Okay, you fixed it now.

---

### Post by handy on 2010-05-27
> **chessnerd said:**
> Looks like you posted xfce4-panel twice. :)

You caught me between edits, I made the output not so wide for you. :)

---

### Post by BoneKracker on 2010-05-27
dwm rules

---

### Post by handy on 2010-05-27
> **BoneKracker said:**
> dwm rules

It might rule you, but it doesn't rule all of us. :)

---

### Post by BoneKracker on 2010-05-27
> **handy said:**
> It might rule you, but it doesn't rule all of us. :)

:lol:

---

