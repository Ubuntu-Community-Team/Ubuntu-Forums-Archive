---
title: "Pidgin runtime error"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by noidian on 2012-09-30
Hi,

I am unable to open pidgin. I have attached the error in the terminal:
Any help would be good. I have tried uninstall and re installing but of no use.

```
*** glibc detected *** pidgin: double free or corruption (fasttop): 0x09411410 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b161)[0xbd1161]
/lib/tls/i686/cmov/libc.so.6(+0x6c9b8)[0xbd29b8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0xbd5a9d]
/lib/libglib-2.0.so.0(g_free+0x36)[0x237fc6]
/usr/lib/purple-2/libskype_dbus.so(send_messages_thread_func+0x45)[0x1d1ac48]
/lib/libglib-2.0.so.0(+0x65def)[0x259def]
/lib/tls/i686/cmov/libpthread.so.0(+0x596e)[0x44596e]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xc3398e]
======= Memory map: ========
00110000-00115000 r-xp 00000000 08:03 4984132    /usr/lib/libgtkspell.so.0.0.0
00115000-00116000 r--p 00004000 08:03 4984132    /usr/lib/libgtkspell.so.0.0.0
00116000-00117000 rw-p 00005000 08:03 4984132    /usr/lib/libgtkspell.so.0.0.0
00117000-00130000 r-xp 00000000 08:03 4982809    /usr/lib/libatk-1.0.so.0.3009.1
00130000-00131000 ---p 00019000 08:03 4982809    /usr/lib/libatk-1.0.so.0.3009.1
00131000-00132000 r--p 00019000 08:03 4982809    /usr/lib/libatk-1.0.so.0.3009.1
00132000-00133000 rw-p 0001a000 08:03 4982809    /usr/lib/libatk-1.0.so.0.3009.1
00133000-0014b000 r-xp 00000000 08:03 5043298    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
0014b000-0014c000 r--p 00017000 08:03 5043298    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
0014c000-0014d000 rw-p 00018000 08:03 5043298    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
0014d000-00151000 r-xp 00000000 08:03 4982803    /usr/lib/libgthread-2.0.so.0.2400.1
00151000-00152000 r--p 00003000 08:03 4982803    /usr/lib/libgthread-2.0.so.0.2400.1
00152000-00153000 rw-p 00004000 08:03 4982803    /usr/lib/libgthread-2.0.so.0.2400.1
00153000-0015a000 r-xp 00000000 08:03 4718935    /lib/tls/i686/cmov/librt-2.11.1.so
0015a000-0015b000 r--p 00006000 08:03 4718935    /lib/tls/i686/cmov/librt-2.11.1.so
0015b000-0015c000 rw-p 00007000 08:03 4718935    /lib/tls/i686/cmov/librt-2.11.1.so
0015c000-0015e000 r-xp 00000000 08:03 4718920    /lib/tls/i686/cmov/libdl-2.11.1.so
0015e000-0015f000 r--p 00001000 08:03 4718920    /lib/tls/i686/cmov/libdl-2.11.1.so
0015f000-00160000 rw-p 00002000 08:03 4718920    /lib/tls/i686/cmov/libdl-2.11.1.so
00160000-00163000 r-xp 00000000 08:03 4718606    /lib/libuuid.so.1.3.0
00163000-00164000 r--p 00002000 08:03 4718606    /lib/libuuid.so.1.3.0
00164000-00165000 rw-p 00003000 08:03 4718606    /lib/libuuid.so.1.3.0
00165000-00166000 r-xp 00000000 08:03 4981744    /usr/lib/pidgin/gtkbuddynote.so
00166000-00167000 r--p 00000000 08:03 4981744    /usr/lib/pidgin/gtkbuddynote.so
00167000-00168000 rw-p 00001000 08:03 4981744    /usr/lib/pidgin/gtkbuddynote.so
00168000-00183000 r-xp 00000000 08:03 4727057    /lib/ld-2.11.1.so
00183000-00184000 r--p 0001a000 08:03 4727057    /lib/ld-2.11.1.so
00184000-00185000 rw-p 0001b000 08:03 4727057    /lib/ld-2.11.1.so
00185000-001c2000 r-xp 00000000 08:03 4982801    /usr/lib/libgobject-2.0.so.0.2400.1
001c2000-001c3000 r--p 0003c000 08:03 4982801    /usr/lib/libgobject-2.0.so.0.2400.1
001c3000-001c4000 rw-p 0003d000 08:03 4982801    /usr/lib/libgobject-2.0.so.0.2400.1
001c4000-001e8000 r-xp 00000000 08:03 4718929    /lib/tls/i686/cmov/libm-2.11.1.so
001e8000-001e9000 r--p 00023000 08:03 4718929    /lib/tls/i686/cmov/libm-2.11.1.so
001e9000-001ea000 rw-p 00024000 08:03 4718929    /lib/tls/i686/cmov/libm-2.11.1.so
001ea000-001ec000 r-xp 00000000 08:03 4984630    /usr/lib/libxcb-aux.so.0.0.0
001ec000-001ed000 r--p 00001000 08:03 4984630    /usr/lib/libxcb-aux.so.0.0.0
001ed000-001ee000 rw-p 00002000 08:03 4984630    /usr/lib/libxcb-aux.so.0.0.0
001ee000-001f0000 r-xp 00000000 08:03 4984632    /usr/lib/libxcb-event.so.1.0.0
001f0000-001f1000 r--p 00001000 08:03 4984632    /usr/lib/libxcb-event.so.1.0.0
001f1000-001f2000 rw-p 00002000 08:03 4984632    /usr/lib/libxcb-event.so.1.0.0
001f3000-001f4000 r-xp 00000000 00:00 0          [vdso]
001f4000-002bc000 r-xp 00000000 08:03 4718726    /lib/libglib-2.0.so.0.2400.1
002bc000-002bd000 r--p 000c7000 08:03 4718726    /lib/libglib-2.0.so.0.2400.1
002bd000-002be000 rw-p 000c8000 08:03 4718726    /lib/libglib-2.0.so.0.2400.1
002be000-002d6000 r-xp 00000000 08:03 4984638    /usr/lib/libxcb.so.1.1.0
002d6000-002d7000 r--p 00017000 08:03 4984638    /usr/lib/libxcb.so.1.1.0
002d7000-002d8000 rw-p 00018000 08:03 4984638    /usr/lib/libxcb.so.1.1.0
002d8000-002e6000 r-xp 00000000 08:03 4983638    /usr/lib/libXext.so.6.4.0
002e6000-002e7000 r--p 0000d000 08:03 4983638    /usr/lib/libXext.so.6.4.0
002e7000-002e8000 rw-p 0000e000 08:03 4983638    /usr/lib/libXext.so.6.4.0
002e8000-002f2000 r-xp 00000000 08:03 4982442    /usr/lib/libpangocairo-1.0.so.0.2800.0
002f2000-002f3000 r--p 00009000 08:03 4982442    /usr/lib/libpangocairo-1.0.so.0.2800.0
002f3000-002f4000 rw-p 0000a000 08:03 4982442    /usr/lib/libpangocairo-1.0.so.0.2800.0
002f4000-002fd000 r-xp 00000000 08:03 4983893    /usr/lib/libenchant.so.1.6.0
002fd000-002fe000 r--p 00008000 08:03 4983893    /usr/lib/libenchant.so.1.6.0
002fe000-002ff000 rw-p 00009000 08:03 4983893    /usr/lib/libenchant.so.1.6.0
002ff000-00302000 r-xp 00000000 08:03 4984628    /usr/lib/libxcb-atom.so.1.0.0
00302000-00303000 r--p 00002000 08:03 4984628    /usr/lib/libxcb-atom.so.1.0.0
00303000-00304000 rw-p 00003000 08:03 4984628    /usr/lib/libxcb-atom.so.1.0.0
00304000-00306000 r-xp 00000000 08:03 4983648    /usr/lib/libXinerama.so.1.0.0
00306000-00307000 r--p 00001000 08:03 4983648    /usr/lib/libXinerama.so.1.0.0
00307000-00308000 rw-p 00002000 08:03 4983648    /usr/lib/libXinerama.so.1.0.0
00308000-00421000 r-xp 00000000 08:03 4983621    /usr/lib/libX11.so.6.3.0
00421000-00422000 r--p 00118000 08:03 4983621    /usr/lib/libX11.so.6.3.0
00422000-00424000 rw-p 00119000 08:03 4983621    /usr/lib/libX11.so.6.3.0
00424000-00425000 rw-p 00000000 00:00 0 
00425000-00438000 r-xp 00000000 08:03 4718790    /lib/libz.so.1.2.3.3
00438000-00439000 r--p 00012000 08:03 4718790    /lib/libz.so.1.2.3.3
00439000-0043a000 rw-p 00013000 08:03 4718790    /lib/libz.so.1.2.3.3
0043a000-0043c000 r-xp 00000000 08:03 4983634    /usr/lib/libXdamage.so.1.1.0
0043c000-0043d000 r--p 00001000 08:03 4983634    /usr/lib/libXdamage.so.1.1.0
0043d000-0043e000 rw-p 00002000 08:03 4983634    /usr/lib/libXdamage.so.1.1.0
00440000-00455000 r-xp 00000000 08:03 4718922    /lib/tls/i686/cmov/libpthread-2.11.1.so
00455000-00456000 r--p 00014000 08:03 4718922    /lib/tls/i686/cmov/libpthread-2.11.1.so
00456000-00457000 rw-p 00015000 08:03 4718922    /lib/tls/i686/cmov/libpthread-2.11.1.so
00457000-00459000 rw-p 00000000 00:00 0 
00459000-0045f000 r-xp 00000000 08:03 4983658    /usr/lib/libXrandr.so.2.2.0
0045f000-00460000 r--p 00005000 08:03 4983658    /usr/lib/libXrandr.so.2.2.0
00460000-00461000 rw-p 00006000 08:03 4983658    /usr/lib/libXrandr.so.2.2.0
00462000-00465000 r-xp 00000000 08:03 4984250    /usr/lib/liblaunchpad-integration.so.1.0.0
00465000-00466000 r--p 00002000 08:03 4984250    /usr/lib/liblaunchpad-integration.so.1.0.0
00466000-00467000 rw-p 00003000 08:03 4984250    /usr/lib/liblaunchpad-integration.so.1.0.0Aborted

```

I installed the pidgin-skype module prior to this issue.

Thanks

---

### Post by T.J. on 2012-09-30
This could be a bug in the module in question, or one of the libraries it is tied into.  If you haven't tried it already, I'd suggest that you try removing the plugin and restarting Pidgin to see if it still crashes.  I It's possible that the plugin is not directly maintained in Ubuntu.   Canconical maintains only the main parts of Ubuntu, and depends on the community for the rest. 

The best way to make sure the skype plugin is removed is:

sudo apt-get remove --purge pidgin-skype

'm sorry I can't give you more specific advice, but I do not use Skype.

---

### Post by dodo3773 on 2012-09-30
There is an old bug reported about pigdin + skype plugin. Try to disable skype plugin and see if it works.


[https://developer.pidgin.im/ticket/10689](https://developer.pidgin.im/ticket/10689)

[http://pidgin.im/pipermail/tracker/2009-November/057010.html](http://pidgin.im/pipermail/tracker/2009-November/057010.html)

---

### Post by noidian on 2012-09-30
k dodo3773, TJ

The only solution seems to be to purge the plugin, although I think the pidgin reported that error 3 years ago, this must be some regression bug!

Thanks

---

### Post by dodo3773 on 2012-09-30
> **noidian said:**
> k dodo3773, TJ

The only solution seems to be to purge the plugin, although I think the pidgin reported that error 3 years ago, this must be some regression bug!

Thanks

Yeah the bug was marked as invalid / nofix. The reason being pidgin is not the ones developing it. So, it's out of their hands. Get with the skype people for a fix or look there.

---

