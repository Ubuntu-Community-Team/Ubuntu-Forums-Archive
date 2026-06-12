---
title: "Pidgin Crashes with Segmentation Error"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by oxsyn on 2008-07-12
Not sure what happened, but as of tonight, pidgin crashes with a segmentation error.  So here's the thing, if I disable my networking and boot pidgin, it loads and says its trying to connect.  If I enable the networking, as soon as it connects, it crashes.

I have three accounts set up: an aim account, a yahoo account & a XMPP (gtalk) account.

Now, I found that if I run pidgin as root (it ran a fresh install, obviously didn't use my .purple/accounts.xml file), I was able to readd my aim & yahoo accounts w/o a problem & it runs fine.  


Here's what it looks like when I run the program from the terminal, w/o sudo:
> user@host:~/.purple$ pidgin
*** glibc detected *** pidgin: double free or corruption (out): 0x0861f818 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb766fa85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb76734f0]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb77d08b1]
/usr/lib/libpurple.so.0[0xb78ea72f]
/usr/lib/libpurple.so.0(purple_proxy_get_setup+0x92)[0xb78ee22c]
/usr/lib/libpurple.so.0(purple_proxy_connect+0x10f)[0xb78ee57a]
/usr/lib/purple-2/liboscar.so.0[0xb5894690]
/usr/lib/purple-2/liboscar.so.0[0xb5875f6a]
/usr/lib/purple-2/liboscar.so.0[0xb587652e]
/usr/lib/purple-2/liboscar.so.0[0xb588d1bb]
/usr/lib/purple-2/liboscar.so.0[0xb588d44b]
/usr/lib/purple-2/liboscar.so.0(flap_connection_recv_cb+0x2f1)[0xb588d767]
pidgin[0x80abca3]
/usr/lib/libglib-2.0.so.0[0xb77fcc5d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x178)[0xb77c8bf8]
/usr/lib/libglib-2.0.so.0[0xb77cbe5e]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1e7)[0xb77cc1e7]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c8a264]
pidgin(main+0xbbc)[0x80c70d5]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb761a450]
pidgin[0x806c821]
======= Memory map: ========
08048000-08115000 r-xp 00000000 08:01 1271791    /usr/bin/pidgin
08115000-08118000 rw-p 000cc000 08:01 1271791    /usr/bin/pidgin
08118000-086ae000 rw-p 08118000 00:00 0          [heap]
b3500000-b3521000 rw-p b3500000 00:00 0 
b3521000-b3600000 ---p b3521000 00:00 0 
b3670000-b36d0000 rw-s 00000000 00:09 5406741    /SYSV00000000 (deleted)
b36d0000-b36d1000 ---p b36d0000 00:00 0 
b36d1000-b3ed1000 rw-p b36d1000 00:00 0 
b3ed1000-b3ed2000 ---p b3ed1000 00:00 0 
b3ed2000-b3f12000 rw-p b3ed2000 00:00 0 
b3f12000-b3f13000 ---p b3f12000 00:00 0 
b3f13000-b4713000 rw-p b3f13000 00:00 0 
b4713000-b4773000 rw-s 00000000 00:09 5373972    /SYSV00000000 (deleted)
b4773000-b4792000 r-xp 00000000 08:01 1271618    /usr/lib/libjpeg.so.62.0.0
b4792000-b4793000 rw-p 0001e000 08:01 1271618    /usr/lib/libjpeg.so.62.0.0
b47a2000-b47a6000 r-xp 00000000 08:01 1294541    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b47a6000-b47a7000 rw-p 00003000 08:01 1294541    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b47a7000-b48ab000 rw-p b47a7000 00:00 0 
b48ab000-b4932000 r--p 00000000 08:01 1402426    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b4932000-b4949000 r--s 00000000 08:01 631101     /var/lib/aspell/en_US-wo_accents-only.rws
b4949000-b4bd1000 r--s 00000000 08:01 631089     /var/lib/aspell/en-common.rws
b4bd1000-b4cd5000 rw-p b4bd1000 00:00 0 
b4cd5000-b4cd7000 r-xp 00000000 08:01 1344176    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4cd7000-b4cd8000 rw-p 00001000 08:01 1344176    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4cd8000-b4d69000 r--p 00000000 08:01 1402427    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4d69000-b4d6f000 r--s 00000000 08:01 634018     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b4d6f000-b4d72000 r--s 00000000 08:01 635237     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b4d72000-b4d73000 r--s 00000000 08:01 635271     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b4d73000-b4d74000 r--s 00000000 08:01 635270     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b4d74000-b4d77000 r--s 00000000 08:01 635269     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b4d77000-b4d7a000 r--s 00000000 08:01 635268     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b4d7a000-b4d7d000 r--s 00000000 08:01 635244     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b4d7d000-b4d85000 r--s 00000000 08:01 635243     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b4d85000-b4d8d000 r--s 00000000 08:01 635242     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b4d8d000-b4d90000 r--s 00000000 08:01 635240     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b4d90000-b4d97000 r--s 00000000 08:01 635239     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b4d97000-b4e42000 r--p 00000000 08:01 1484915    /usr/share/icons/Tangerine/icon-theme.cache
b4e42000-b4e53000 r-xp 00000000 08:01 1295553    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b4e53000-b4e54000 rw-p 00011000 08:01 1295553    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b4e54000-b4e98000 r-xp 00000000 08:01 1278268    /usr/lib/nss/libnssckbi.so
b4e98000-b4ea3000 rw-p 00044000 08:01 1278268    /usr/lib/nss/libnssckbi.so
b4ea3000-b4edd000 r-xp 00000000 08:01 1278265    /usr/lib/nss/libfreebl3.so
b4edd000-b4ede000 rw-p 0003a000 08:01 1278265    /usr/lib/nss/libfreebl3.so
b4ede000-b4f0e000 r-xp 00000000 08:01 1278266    /usr/lib/nss/libsoftokn3.so
b4f0e000-b4f0f000 rw-p 00030000 08:01 1278266    /usr/lib/nss/libsoftokn3.so
b4f0f000-b4f10000 ---p b4f0f000 00:00 0 
b4f10000-b5710000 rw-p b4f10000 00:00 0 
b5710000-b5724000 r-xp 00000000 08:01 1271347    /usr/lib/libgadu.so.3.5
b5724000-b5725000 rw-p 00013000 08:01 1271347    /usr/lib/libgadu.so.3.5
b5729000-b572f000 r--s 00000000 08:01 635208     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b572f000-b5733000 r-xp 00000000 08:01 1294552    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5733000-b5734000 rw-p 00003000 08:01 1294552    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5734000-b575e000 r-xp 00000000 08:01 1271654    /usr/lib/libmeanwhile.so.1.0.2
b575e000-b575f000 rw-p 00029000 08:01 1271654    /usr/lib/libmeanwhile.so.1.0.2
b5761000-b576d000 r-xp 00000000 08:01 1278691    /usr/lib/purple-2/libgg.so
b576d000-b576e000 rw-p 0000b000 08:01 1278691    /usr/lib/purple-2/libgg.so
b576e000-b5784000 r-xp 00000000 08:01 3769523    /usr/lib/purple-2/libsametime.so
b5784000-b5785000 rw-p 00015000 08:01 3769523    /usr/lib/purple-2/libsametime.so
b5785000-b5786000 rw-p b5785000 00:00 0 
b5786000-b5788000 r-xp 00000000 08:01 1278687    /usr/lib/purple-2/psychic.so
b5788000-b5789000 rw-p 00001000 08:01 1278687    /usr/lib/purple-2/psychic.so
b5789000-b57c4000 r-xp 00000000 08:01 3769525    /usr/lib/purple-2/libyahoo.so
b57c4000-b57c6000 rw-p 0003b000 08:01 3769525    /usr/lib/purple-2/libyahoo.so
b57c6000-b57c8000 r-xp 00000000 08:01 1278686    /usr/lib/purple-2/offlinemsg.so
b57c8000-b57c9000 rw-p 00001000 08:01 1278686    /usr/lib/purple-2/offlinemsg.so
b57c9000-b57e5000 r-xp 00000000 08:01 3769518    /usr/lib/purple-2/libnovell.so
b57e5000-b57e6000 rw-p 0001b000 08:01 3769518    /usr/lib/purple-2/libnovell.so
b57e6000-b5813000 r-xp 00000000 08:01 3752016    /lib/libncurses.so.5.6
b5813000-b5816000 rw-p 0002c000 08:01 3752016    /lib/libncurses.so.5.6
b5816000-b5842000 r-xp 00000000 08:01 3752056    /lib/libreadline.so.5.2
b5842000-b5846000 rw-p 0002c000 08:01 3752056    /lib/libreadline.so.5.2
b5846000-b5847000 rw-p b5846000 00:00 0 
b5847000-b584a000 r-xp 00000000 08:01 1271581    /usr/lib/libhesiod.so.0
b584a000-b584b000 rw-p 00002000 08:01 1271581    /usr/lib/libhesiod.so.0
b584b000-b5855000 r-xp 00000000 08:01 1271943    /usr/lib/libzephyr.so.3.0.0
b5855000-b5856000 rw-p 00009000 08:01 1271943    /usr/lib/libzephyr.so.3.0.0
b5856000-b5859000 rw-p b5856000 00:00 0 
b5859000-b585b000 r--s 00000000 08:01 632153     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b585b000-b585f000 r-xp 00000000 08:01 1278581    /usr/lib/purple-2/ssl-nss.so
b585f000-b5860000 rw-p 00003000 08:01 1278581    /usr/lib/purple-2/ssl-nss.so
b5860000-b5861000 r-xp 00000000 08:01 1278579    /usr/lib/purple-2/ssl.so
b5861000-b5862000 rw-p 00000000 08:01 1278579    /usr/lib/purple-2/ssl.so
b5862000-b5864000 r-xp 00000000 08:01 1278680    /usr/lib/purple-2/autoaccept.so
b5864000-b5865000 rw-p 00001000 08:01 1278680    /usr/lib/purple-2/autoaccept.so
b5865000-b5867000 r-xp 00000000 08:01 1278683    /usr/lib/purple-2/joinpart.so
b5867000-b5868000 rw-p 00001000 08:01 1278683    /usr/lib/purple-2/joinpart.so
b5868000-b58ae000 r-xp 00000000 08:01 3769519    /usr/lib/purple-2/liboscar.so.0.0.0
b58ae000-b58b0000 rw-p 00045000 08:01 3769519    /usr/lib/purple-2/liboscar.so.0.0.0
b58b0000-b59cb000 r-xp 00000000 08:01 1271751    /usr/lib/libperl.so.5.8.8
b59cb000-b59d0000 rw-p 0011a000 08:01 1271751    /usr/lAborted


> user@host:~/.purple$ pidgin
Segmentation fault

Help?  Thanks.

---

### Post by ChameleonDave on 2008-07-12
For some weird reason, something in your user configuration files is causing this.  I have no explanation for it.

If you delete your ~/.purple folder, it will be fine.

You will, of course, have to re-add your accounts.

---

### Post by oxsyn on 2008-07-12
I deleted the entire .purple directory and then launched pidgin from the command line.

> user@host:~$ pidgin

Pidgin launched, asked me to add a new account.  I created my aim account, clicked OK.  It attempted to connect and then instantly crashed, again.

> user@host:~$ pidgin
Segmentation fault
user@host:~$ pidgin

... any ideas?

---

### Post by oxsyn on 2008-07-12
I just removed pidign using sudo apt-get remove pidigin & then deleted the .purple directory (it was recreated).  I then did another sudo apt-get install pidgin.  Same exact problem: as soon as my account connects to the server, pidgin crashes with a segmentation error.

---

### Post by oxsyn on 2008-07-12
OMG, just solved it.  I opened up pidgin, but didn't add an account, started looking through all the preferences.  At school, I had enabled a proxy server that wasn't available from home.  I turned off the proxy server (set it back to "I am directly connected to the internet.") Readded my account, and it worked fine.

Arrrrghhhh!

---

### Post by ChameleonDave on 2008-07-12
> **F4RR4R said:**
> OMG, just solved it.  I opened up pidgin, but didn't add an account, started looking through all the preferences.  At school, I had enabled a proxy server that wasn't available from home.  I turned off the proxy server (set it back to "I am directly connected to the internet.") Readded my account, and it worked fine.

Arrrrghhhh!
Well done on finding the source of the error.

I'm not sure why deleting your user config files didn't fix that.  I don't know where else Pidgin stores such things.

Having the proxy server listed should cause connection problems, but it certainly shouldn't cause a crash.  You should report this bug.

---

### Post by oxsyn on 2008-07-13
> **ChameleonDave said:**
> Well done on finding the source of the error.

I'm not sure why deleting your user config files didn't fix that.  I don't know where else Pidgin stores such things.

Having the proxy server listed should cause connection problems, but it certainly shouldn't cause a crash.  You should report this bug.

Apparently, the proxy configuration files must be located somewhere other than the .purple directory.  Certainly not somewhere global for all users though, since running pidgin as another user was fine.  Never would have guessed!

I've never reported a Ubuntu bug before.  Can you enlighten me as the process?  Thanks!

---

### Post by spiderbatdad on 2008-07-13
You should have 3 things:

Register an account on Launchpad

A good description of the problem, and how to reproduce it.

The name of the program that causes the problem.

[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

### Post by ChameleonDave on 2008-07-13
You can also report the problem directly to Pidgin here:
[http://developer.pidgin.im/query](http://developer.pidgin.im/query)

---

### Post by biji on 2008-09-01
hi,
seg fault because of proxy set
and the proxy is socks 5 not http
i tried direct connection for workaround
:guitar:

---

