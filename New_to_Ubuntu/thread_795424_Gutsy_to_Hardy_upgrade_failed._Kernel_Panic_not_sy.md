---
title: "Gutsy to Hardy upgrade failed. Kernel Panic not syncing"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by sitmex on 2008-05-15
Hi all..

I was about to make the transition to the newest Ubunto release, 8.04 (I guess) but something went terribly wrong.

the process ended abnormaly, not finishig the upgrade, it was almos at 97% and then, wham!!, all aborted, no cleaning up, no nothing.

I restarted the computer, and I got an error : Kernel Panic not syncing. for what I understand, that means that the system is not finding any volume to load Linux from, so in GRUB I used a previous version and that's where I am sending this.

Second I try to run the adept updater and this is what I got.

DATABASE LOCKED: Another process is using the packaging system database..
would you like to attempt to resolve...

I hitted yes and the program failed with these errors
```

(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x2b71986983c0 (LWP 6696)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#5  0x00002b7197717095 in raise () from /lib/libc.so.6
#6  0x00002b7197718af0 in abort () from /lib/libc.so.6
#7  0x00002b71970100e4 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#8  0x00002b719700e076 in ?? () from /usr/lib/libstdc++.so.6
#9  0x00002b719700e0a3 in std::terminate () from /usr/lib/libstdc++.so.6
#10 0x00002b719700e18a in __cxa_throw () from /usr/lib/libstdc++.so.6
#11 0x00000000004a3551 in ?? ()
#12 0x00000000004a3994 in ?? ()
#13 0x00000000004a4ee3 in ?? ()
#14 0x00000000004d8ec4 in ?? ()
#15 0x0000000000445e26 in ?? ()
#16 0x0000000000435350 in ?? ()
#17 0x000000000043567c in ?? ()
#18 0x00002b71935d5fd0 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#19 0x00002b719394e181 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#20 0x00002b71935f41a3 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#21 0x00002b71935fb9e4 in QSingleShotTimer::event ()
   from /usr/lib/libqt-mt.so.3
#22 0x00002b719356e33a in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#23 0x00002b7193570093 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#24 0x00002b719261740d in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#25 0x00002b71934ff20e in QApplication::sendEvent ()
   from /usr/lib/libqt-mt.so.3
#26 0x00002b7193561abc in QEventLoop::activateTimers ()
   from /usr/lib/libqt-mt.so.3
#27 0x00002b7193514107 in QEventLoop::processEvents ()
   from /usr/lib/libqt-mt.so.3
#28 0x00002b71935885bf in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#29 0x00002b71935882ab in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#30 0x00002b719356fe00 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#31 0x0000000000432d6c in ?? ()
#32 0x00002b71977031c4 in __libc_start_main () from /lib/libc.so.6
#33 0x0000000000432af9 in ?? ()
#34 0x00007fff1a31b018 in ?? ()
#35 0x0000000000000000 in ?? ()

```

any Idea on how to clean that mess? now my system is PACKED!!! only 1% free space left...

Thanks in advance...

---

### Post by unutbu on 2008-05-15
Ah, I think you just diagnosed the problem:

> my system is PACKED!!! only 1% free space left...

I suspect the installation was going along fine until your hard drive got too full and it was unable to write new files.

---

### Post by sitmex on 2008-05-15
> **unutbu said:**
> Ah, I think you just diagnosed the problem:
I suspect the installation was going along fine until your hard drive got too full and it was unable to write new files.

Hey Thanks for your response, 
I guess my system had nearly 30 - 35% of free space, these are the stats:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             23798008  22301940    287180  99% /
varrun                  505720       184    505536   1% /var/run
varlock                 505720         0    505720   0% /var/lock
udev                    505720       104    505616   1% /dev
devshm                  505720         0    505720   0% /dev/shm
lrm                     505720     38324    467396   8% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1            165276684 134466700  30809984  82% /media/SITMEX

```

---

