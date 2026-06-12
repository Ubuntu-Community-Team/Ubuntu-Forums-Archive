---
title: "Transmission Crash in 8.10"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by bbc on 2008-11-01
I know I'm probably not going to get an answer for this, since these forums are terrible, but I'd figured I'd give it a shot.

So I just updated from 8.04 and transmission crashes after about a minute or so, while it's up all of my seeded torrents says "connect limit exceeded" when I check the details.

In 8.04 I never had any problems with transmission 1.34. This is what I got in the term....

(transmission:8702): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(transmission:8702): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
*** glibc detected *** transmission: corrupted double-linked list: 0xb5e11a30 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb765d3f4]
/lib/tls/i686/cmov/libc.so.6[0xb7660472]
/lib/tls/i686/cmov/libc.so.6[0xb7660e5f]
/lib/tls/i686/cmov/libc.so.6(realloc+0x106)[0xb7661d86]
/usr/lib/libcurl.so.4[0xb78d9b72]
/usr/lib/libcurl.so.4[0xb78dad73]
/usr/lib/libcurl.so.4(curl_mvaprintf+0x46)[0xb78db4d6]
/usr/lib/libcurl.so.4[0xb78c5cef]
/usr/lib/libcurl.so.4[0xb78c6c07]
/usr/lib/libcurl.so.4[0xb78d3ad0]
/usr/lib/libcurl.so.4[0xb78e63ed]
/usr/lib/libcurl.so.4(curl_multi_perform+0x59)[0xb78e6739]
transmission[0x809ac37]
transmission(event_base_loop+0x310)[0x80c1570]
transmission(event_loop+0x1a)[0x80c172a]
transmission(event_dispatch+0x12)[0x80c1742]
transmission[0x8096890]
transmission[0x808aa5a]
/lib/tls/i686/cmov/libpthread.so.0[0xb775250f]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb76cf7ee]
======= Memory map: ========
08048000-080e6000 r-xp 00000000 08:01 8095743    /usr/bin/transmission
080e6000-080e7000 r--p 0009d000 08:01 8095743    /usr/bin/transmission
080e7000-080e9000 rw-p 0009e000 08:01 8095743    /usr/bin/transmission
08fc1000-099b0000 rw-p 08fc1000 00:00 0          [heap]
b3b41000-b3b4e000 r-xp 00000000 08:01 10010693   /lib/libgcc_s.so.1
b3b4e000-b3b4f000 r--p 0000c000 08:01 10010693   /lib/libgcc_s.so.1
b3b4f000-b3b50000 rw-p 0000d000 08:01 10010693   /lib/libgcc_s.so.1
b3b63000-b3b64000 ---p b3b63000 00:00 0 
b3b64000-b4364000 rw-p b3b64000 00:00 0 
b4364000-b4365000 ---p b4364000 00:00 0 
b4365000-b4b65000 rw-p b4365000 00:00 0 
b4b65000-b4b66000 ---p b4b65000 00:00 0 
b4b66000-b546a000 rw-p b4b66000 00:00 0 
b546a000-b54e7000 r--p 00000000 08:01 8258064    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
b54e7000-b54e8000 ---p b54e7000 00:00 0 
b54e8000-b5ce8000 rw-p b54e8000 00:00 0 
b5ce8000-b5cf3000 r-xp 00000000 08:01 8094535    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b5cf3000-b5cf4000 r--p 0000a000 08:01 8094535    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b5cf4000-b5cf5000 rw-p 0000b000 08:01 8094535    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b5cf5000-b5d77000 rw-p b5cf5000 00:00 0 
b5d77000-b5e00000 r--p 00000000 08:01 8257708    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b5e00000-b5e2b000 rw-p b5e00000 00:00 0 
b5e2b000-b5f00000 ---p b5e2b000 00:00 0 
b5f03000-b5f63000 rw-s 00000000 00:09 1474583    /SYSV00000000 (deleted)
b5f63000-b5fc3000 rw-s 00000000 00:09 1441808    /SYSV00000000 (deleted)
b5fc3000-b5fdc000 r--s 00000000 08:01 8193353    /usr/share/mime/mime.cache
b5fdc000-b5fde000 r-xp 00000000 08:01 10014346   /lib/tls/i686/cmov/libutil-2.8.90.so
b5fde000-b5fdf000 r--p 00001000 08:01 10014346   /lib/tls/i686/cmov/libutil-2.8.90.so
b5fdf000-b5fe0000 rw-p 00002000 08:01 10014346   /lib/tls/i686/cmov/libutil-2.8.90.so
b5fe0000-b5fed000 r-xp 00000000 08:01 8028213    /usr/lib/libgvfscommon.so.0.0.0
b5fed000-b5fee000 r--p 0000d000 08:01 8028213    /usr/lib/libgvfscommon.so.0.0.0
b5fee000-b5fef000 rw-p 0000e000 08:01 8028213    /usr/lib/libgvfscommon.so.0.0.0
b5ff2000-b5ffa000 r-xp 00000000 08:01 8031396    /usr/lib/libtrackerclient.so.0.0.0
b5ffa000-b5ffb000 r--p 00007000 08:01 8031396    /usr/lib/libtrackerclient.so.0.0.0
b5ffb000-b5ffc000 rw-p 00008000 08:01 8031396    /usr/lib/libtrackerclient.so.0.0.0
b5ffc000-b6000000 r-xp 00000000 08:01 8095274    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6000000-b6001000 r--p 00003000 08:01 8095274    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6001000-b6002000 rw-p 00004000 08:01 8095274    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6002000-b601a000 r-xp 00000000 08:01 8094547    /usr/lib/gio/modules/libgvfsdbus.so
b601a000-b601b000 r--p 00017000 08:01 8094547    /usr/lib/gio/modules/libgvfsdbus.so
b601b000-b601c000 rw-p 00018000 08:01 8094547    /usr/lib/gio/modules/libgvfsdbus.so
b601c000-b6120000 rw-p b601c000 00:00 0 
b6120000-b61b5000 r--p 00000000 08:01 8257707    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b61b5000-b61b7000 r-xp 00000000 08:01 8160206    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b61b7000-b61b8000 r--p 00001000 08:01 8160206    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b61b8000-b61b9000 rw-p 00002000 08:01 8160206    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b61b9000-b61bf000 r--s 00000000 08:01 9127976    /var/cache/fontconfig/945677eb7aeaf62f1d50eAborted

If anyone can help me it would be appreciated.

---

### Post by muniak on 2009-01-12
Hey,
I know it's been a while since you asked but it appears that this happens when you've got a torrent running that can't find the dir it should be downloading to... eg. you changed the dir name after having started the torrent.

---

