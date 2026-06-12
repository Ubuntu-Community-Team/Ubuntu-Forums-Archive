---
title: "[SOLVED] 8.10 on Laptop: Transmission downloads halt when laptop screen off?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Statik on 2008-11-18
Hi all,

Still noticing a few odd things with this new intrepid install. The latest is: I have transmission doing a torrent download. I usually can leave it all night and find it complete in the morning (slow internet). Now it seems that when the laptop screen is blanked, transmission stops. It keeps going while the screensaver is on, but not once the screen blanks. The laptop isn't going to sleep as I have it plugged in and told to not go to sleep. What gives? Where do I look for a setting to change to fix this?

Statik

---

### Post by PartisanEntity on 2008-11-18
I would launch transmission from the terminal and then wait until the screen goes off, then have a look at any error messages.

Right now it sounds like your computer is actually going in to sleep mode.

---

### Post by stooshbunutu on 2008-11-18
you need to set what happens when the lap-top lid is closed (some where in the power management options) and select to do blank screen when the lid is closed

---

### Post by Statik on 2008-11-18
I'll try launching it from terminal tonight. I know its not the lid thing for 2 reasons. 1 I'm not closing the lid and 2 I had it set to blank screen only on lid-close.

Thanks for the suggestions tho!

Statik

---

### Post by Statik on 2008-11-19
Well, its not going to sleep, or the screensaver, I turned them off. It says its downloading at 25KB/s (about my max), and the time remaining reflects that, but the total downloaded doesn't increase near as fast. The time decreases very slowly as well. For instance, if it says 30 minutes remaining, it might take 4 hours to go down to 15 minutes remaining. 

I installed vuse (azureus) and it seems to work as expected. I'd love to know whats wrong with transmission, but I'm back on track using vuse for now. I'll mark it as solved, unless someone has more to add.


Statik

---

### Post by stepdown on 2008-11-19
I'm having a similar issue, at first I thought it was the screensaver, but have seen transmission closing even when I'm sat at the system.

Have started it in terminal, will be back once I have some sort of clues.

EDIT
This might be connected... ?
[http://ubuntuforums.org/showthread.php?t=809314&highlight=transmission](http://ubuntuforums.org/showthread.php?t=809314&highlight=transmission)

---

### Post by stepdown on 2008-11-19
```
user@host:~$ transmission
*** glibc detected *** transmission: double free or corruption (fasttop): 0xb637cef0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75dc3f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb75de456]
/usr/lib/libcurl.so.4[0xb784f214]
/usr/lib/libcurl.so.4[0xb7846278]
/usr/lib/libcurl.so.4[0xb7852ad0]
/usr/lib/libcurl.so.4[0xb78653ed]
/usr/lib/libcurl.so.4(curl_multi_perform+0x59)[0xb7865739]
transmission[0x809ac37]
transmission(event_base_loop+0x310)[0x80c1570]
transmission(event_loop+0x1a)[0x80c172a]
transmission(event_dispatch+0x12)[0x80c1742]
transmission[0x8096890]
transmission[0x808aa5a]
/lib/tls/i686/cmov/libpthread.so.0[0xb76d150f]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb764e7ee]
======= Memory map: ========
08048000-080e6000 r-xp 00000000 fe:00 786457     /usr/bin/transmission
080e6000-080e7000 r--p 0009d000 fe:00 786457     /usr/bin/transmission
080e7000-080e9000 rw-p 0009e000 fe:00 786457     /usr/bin/transmission
0889a000-08e58000 rw-p 0889a000 00:00 0          [heap]
b5be3000-b5bf0000 r-xp 00000000 fe:00 3383311    /lib/libgcc_s.so.1
b5bf0000-b5bf1000 r--p 0000c000 fe:00 3383311    /lib/libgcc_s.so.1
b5bf1000-b5bf2000 rw-p 0000d000 fe:00 3383311    /lib/libgcc_s.so.1
b5c00000-b5cfa000 rw-p b5c00000 00:00 0 
b5cfa000-b5d00000 ---p b5cfa000 00:00 0 
b5d7d000-b5ddd000 rw-s 00000000 00:09 20578407   /SYSV00000000 (deleted)
b5ddd000-b5e3d000 rw-s 00000000 00:09 20545621   /SYSV00000000 (deleted)
b5e3d000-b5f00000 rw-p b5e3d000 00:00 0 
b5f00000-b5f89000 r--p 00000000 fe:00 3269477    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b5f89000-b5f96000 r-xp 00000000 fe:00 2956443    /usr/lib/libgvfscommon.so.0.0.0
b5f96000-b5f97000 r--p 0000d000 fe:00 2956443    /usr/lib/libgvfscommon.so.0.0.0
b5f97000-b5f98000 rw-p 0000e000 fe:00 2956443    /usr/lib/libgvfscommon.so.0.0.0
b5f98000-b5fb0000 r-xp 00000000 fe:00 3186781    /usr/lib/gio/modules/libgvfsdbus.so
b5fb0000-b5fb1000 r--p 00017000 fe:00 3186781    /usr/lib/gio/modules/libgvfsdbus.so
b5fb1000-b5fb2000 rw-p 00018000 fe:00 3186781    /usr/lib/gio/modules/libgvfsdbus.so
b5fd3000-b5fd7000 r-xp 00000000 fe:00 3383455    /lib/tls/i686/cmov/libnss_dns-2.8.90.so
b5fd7000-b5fd8000 r--p 00003000 fe:00 3383455    /lib/tls/i686/cmov/libnss_dns-2.8.90.so
b5fd8000-b5fd9000 rw-p 00004000 fe:00 3383455    /lib/tls/i686/cmov/libnss_dns-2.8.90.so
b5fd9000-b5fdb000 r-xp 00000000 fe:00 3384660    /lib/libnss_mdns4_minimal.so.2
b5fdb000-b5fdc000 rw-p 00001000 fe:00 3384660    /lib/libnss_mdns4_minimal.so.2
b5fea000-b602b000 rw-p b5fea000 00:00 0 
b602b000-b602f000 r-xp 00000000 fe:00 2999205    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b602f000-b6030000 r--p 00003000 fe:00 2999205    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6030000-b6031000 rw-p 00004000 fe:00 2999205    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6031000-b6048000 r--s 00000000 fe:00 3000134    /usr/share/mime/mime.cache
b6048000-b614c000 rw-p b6048000 00:00 0 
b614c000-b61e1000 r--p 00000000 fe:00 3269476    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b61e1000-b61e3000 r-xp 00000000 fe:00 2999128    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b61e3000-b61e4000 r--p 00001000 fe:00 2999128    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b61e4000-b61e5000 rw-p 00002000 fe:00 2999128    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b61e5000-b61eb000 r--s 00000000 fe:00 5259598    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b61eb000-b61ee000 r--s 00000000 fe:00 5259614    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b61ee000-b61ef000 r--s 00000000 fe:00 5259613    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b61ef000-b61f2000 r--s 00000000 fe:00 5259612    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b61f2000-b61f5000 r--s 00000000 fe:00 5259611    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b61f5000-b61f8000 r--s 00000000 fe:00 5259610    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b61f8000-b6200000 r--s 00000000 fe:00 5259609    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6200000-b62fb000 rw-p b6200000 00:00 0 
b62fb000-b6300000 ---p b62fb000 00:00 0 
b6300000-b63ff000 rw-p b6300000 00:00 0 
b63ff000-b6400000 ---p b63ff000 00:00 0 
b6400000-b64fe000 rw-p b6400000 00:00 0 
b64fe000-b6500000 ---p b64fe000 00:00 0 
b6502000-b6504000 r-xp 00000000 fe:00 3383468    /lib/tls/i686/cmov/libutil-2.8.90.so
b6504000-b6505000 r--p 00001000 fe:00 3383468    /lib/tls/i686/cmov/libutil-2.8.90.so
b6505000-b6506000 rw-p 00002000 fe:00 3383468    /lib/tls/i686/cmov/libutil-2.8.90.so
b6506000-b6511000 r--s 00000000 fe:00 5259608    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6511000-b6512000 r--s 00000000 fe:00 5259607    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6512000-b6534000 r--s 00000000 fe:00 5261336    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b6534000-b6537000 r--s 00000000 fe:00 5259606    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6537000-b653e000 r--s 00000000 fe:00 5259605    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b653e000-b6544000 r--s 00000000 fe:00 5259597    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6544000-b6545000 ---p b6544000 00:00 0 
b6545000-b6d45000 rw-p b6545000 00:00 0 
b6d45000-b6d67000 r--p 00000000 fe:00 3180671    /usr/share/icons/Crux/icon-theme.cache
b6d67000-b6d86000 r-xp 00000000 fe:00 3027014    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b6d86000-b6d87000 r--p 0001e000 fe:00 3027014    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b6d87000-b6d88000 rw-p 0001f000 fe:00 3027014    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b6d88000-b6d92000 r-xp 00000000 fe:00 3383456    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6d92000-b6d93000 r--p 00009000 fe:00 3383456    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6d93000-b6d94000 rw-p 0000a000 fe:00 3383456    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6d94000-b6d9d000 r-xp 00000000 fe:00 3383459    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6d9d000-b6d9e000 r--p 00008000 fe:00 3383459    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6d9e000-b6d9f000 rw-p 00009000 fe:00 3383459    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6d9f000-b6da6000 r-xp 00000000 fe:00 3383454    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b6da6000-b6da7000 r--p 00006000 fe:00 3383454    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b6da7000-b6da8000 rw-p 00007000 fe:00 3383454    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b6daa000-b6db1000 r--s 00000000 fe:00 5261335    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6db1000-b6db2000 r--p 00000000 fe:00 2973895    /usr/share/locale-langpack/en_GB/LC_MESSAGES/libc.mo
b6db2000-b6db3000 r--p 00000000 fe:00 2974778    /usr/share/locale-langpack/en_GB/LC_MESSAGES/glib20.mo
b6db3000-b6db6000 r--p 00000000 fe:00 2974646    /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20-properties.mo
b6db6000-b6dbb000 r--p 00000000 fe:00 2974735    /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20.mo
b6dbb000-b6dbc000 r--p 00000000 fe:00 2974737    /usr/share/locale-langpack/en_GB/LC_MESSAGES/transmission.mo
b6dbc000-b6dfb000 r--p 00000000 fe:00 2973713    /usr/lib/locale/en_GB.utf8/LC_CTYPE
b6dfb000-b6dfc000 r--p 00000000 fe:00 2973714    /usr/lib/locale/en_GB.utf8/LC_NUMERIC
b6dfc000-b6dfd000 r--p 00000000 fe:00 2973715    /usr/lib/locale/en_GB.utf8/LC_TIME
b6dfd000-b6ede000 r--p 00000000 fe:00 2973716    /usr/lib/locale/en_GB.utf8/LC_COLLATE
b6ede000-b6edf000 r--p 00000000 fe:00 2973717    /usr/lib/locale/en_GB.utf8/LC_MONETARY
b6edf000-b6ee3000 rw-p b6edf000 00:00 0 
b6ee3000-b6ee6000 r-xp 00000000 fe:00 3383541    /lib/libgpg-error.so.0.3.0
b6ee6000-b6ee7000 rw-p 00002000 fe:00 3383541    /lib/libgpg-error.so.0.3.0
b6ee7000-b6ee9000 r-xp 00000000 fe:00 3383532    /lib/libkeyutils-1.2.so
b6ee9000-b6eeb000 rw-p 00001000 fe:00 3383532    /lib/libkeyutils-1.2.so
b6eeb000-b6ef2000 r-xp 00000000 fe:00 2951628    /usr/lib/libkrb5support.so.0.1
b6ef2000-b6ef3000 r--p 00006000 fe:00 2951628    /usr/lib/libkrb5support.so.0.1
b6ef3000-b6ef4000 rw-p 00007000 fe:00 2951628    /usr/lib/libkrb5support.so.0.1
b6ef4000-b6ef5000 rw-p b6ef4000 00:00 0 
b6ef5000-b6f5b000 r-xp 00000000 fe:00 3383539    /lib/libgcrypt.so.11.4.4
b6f5b000-b6f5c000 r--p 00065000 fe:00 3383539    /lib/libgcrypt.so.11.4.4
b6f5c000-b6f5e000 rw-p 00066000 fe:00 3383539    /lib/libgcrypt.so.11.4.4
b6f5e000-b6f6e000 r-xp 00000000 fe:00 2951665    /usr/lib/libtasn1.so.3.0.15
b6f6e000-b6f70000 rw-p 0000f000 fe:00 2951665    /usr/lib/libtasn1.so.3.0.15
b6f70000-b7007000 r-xp 00000000 fe:00 2951509    /usr/lib/libgnutls.so.26.4.5
b7007000-b700c000 r--p 00096000 fe:00 2951509    /usr/lib/libgnutls.so.26.4.Aborted
user@host:~$ 
```
Will be looking into...
[ [SOLVED] Transmission blocks sleep/suspend: workaround?  ](http://ubuntuforums.org/showthread.php?t=974160)

and

[ New Transmission is blocking standby](http://ubuntuforums.org/showthread.php?t=809314)

---

### Post by Statik on 2008-11-19
No errors or any messages at all in terminal. It looks like its downloading like crazy, but none of it shows up in the file results. I watched it download for four hours, at 25kB/s and ended up with 4 MB downloaded. Azureus downloaded the 170MB file in 4 hours, approximately.

Something is definitely wrong with transmission's performance here.

Statik

---

### Post by stepdown on 2008-11-19
Have upgraded to 1.40 in the hope this will be fixed :popcorn:

If not I might just make the jump to Deluge.

Edit - 1.40 works fine for me!
[http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604](http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604)

---

### Post by Statik on 2008-11-21
Upgrading to 1.4 also solved this for me. Transmission is working properly again.

Thanks!

Statik

---

