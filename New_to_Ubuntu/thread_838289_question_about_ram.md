---
title: "question about ram"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by XTR0RDiNAiRE on 2008-06-23
ok im just wondering why my pc lags so much when im using gimp
im having delayed reactions with anything i do on gimp
i have  3gb of ram, isnt that more than enough
i also have awn open

---

### Post by hyper_ch on 2008-06-23
I have 1 GB ram and gimp runs fine

---

### Post by XTR0RDiNAiRE on 2008-06-23
> **hyper_ch said:**
> I have 1 GB ram and gimp runs fine

thats what im sayin, 

i dont know too much about computers but im pretty sure 3 gb of ram
shouldnt make gimp run like that
im runnin compiz visual effects and awn

then when i run gimp its lags sooo much

---

### Post by Fedz on 2008-06-23
What's is system > admin > system monitor > process (tab) saying it's doing?

---

### Post by XTR0RDiNAiRE on 2008-06-23
it just says i have compiz running
everything else is sleeping

---

### Post by ukripper on 2008-06-23
can you post output of the follwoing:
```
fglrxinfo
```

I suspect it is your graphics card drivers

---

### Post by fatality_uk on 2008-06-23
When you say anything, what are your trying to do? I mean applying a blur filter to a 2000x1800px image requires a decent processor as well. It isn't all just about RAM

---

### Post by markbuntu on 2008-06-23
Compiz sucks up a lot of cpu time. Try running gimp wtih desktop effects set to none.

---

### Post by XTR0RDiNAiRE on 2008-06-23
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.1.7412 Release


thats what i got
i really doubt that compiz can use up more than a gig of ram tho
:(

---

### Post by ukripper on 2008-06-24
> **XTR0RDiNAiRE said:**
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.1.7412 Release


thats what i got
i really doubt that compiz can use up more than a gig of ram tho
:(

can you post output of below command as well when you think it is slow.
```
ps -aux
```

---

### Post by Kevbert on 2008-06-24
If you think it may be Compiz, try turning it off temporarily by installing [compiz-switch]("http://forlong.blogage.de/article/pages/Compiz-Switch").

---

### Post by XTR0RDiNAiRE on 2008-06-24
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.0   4020   880 ?        Ss   07:08   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   07:08   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   07:08   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   07:08   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   07:08   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   07:08   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   07:08   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   07:08   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   07:08   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   07:08   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   07:08   0:00 [khelper]
root        44  0.0  0.0      0     0 ?        S<   07:08   0:00 [kblockd/0]
root        45  0.0  0.0      0     0 ?        S<   07:08   0:00 [kblockd/1]
root        48  0.0  0.0      0     0 ?        S<   07:08   0:00 [kacpid]
root        49  0.0  0.0      0     0 ?        S<   07:08   0:00 [kacpi_notify]
root       137  0.0  0.0      0     0 ?        S<   07:08   0:00 [kseriod]
root       187  0.0  0.0      0     0 ?        S    07:08   0:00 [pdflush]
root       188  0.0  0.0      0     0 ?        S    07:08   0:00 [pdflush]
root       189  0.0  0.0      0     0 ?        S<   07:08   0:00 [kswapd0]
root       232  0.0  0.0      0     0 ?        S<   07:08   0:00 [aio/0]
root       233  0.0  0.0      0     0 ?        S<   07:08   0:00 [aio/1]
root      1481  0.0  0.0      0     0 ?        S<   07:08   0:00 [ata/0]
root      1482  0.0  0.0      0     0 ?        S<   07:08   0:00 [ata/1]
root      1484  0.0  0.0      0     0 ?        S<   07:08   0:00 [ata_aux]
root      1520  0.0  0.0      0     0 ?        S<   07:08   0:00 [ksuspend_usbd]
root      1522  0.0  0.0      0     0 ?        S<   07:08   0:00 [khubd]
root      1553  0.0  0.0      0     0 ?        S<   07:08   0:00 [khpsbpkt]
root      2279  0.0  0.0      0     0 ?        S<   07:08   0:00 [scsi_eh_0]
root      2280  0.0  0.0      0     0 ?        S<   07:08   0:00 [scsi_eh_1]
root      2281  0.0  0.0      0     0 ?        S<   07:08   0:00 [scsi_eh_2]
root      2282  0.0  0.0      0     0 ?        S<   07:08   0:00 [scsi_eh_3]
root      2521  0.0  0.0      0     0 ?        S<   07:08   0:00 [kjournald]
root      2599  0.0  0.0      0     0 ?        S<   07:08   0:00 [knodemgrd_0]
root      2719  0.0  0.0  17188  1296 ?        S<s  07:08   0:00 /sbin/udevd --d
root      2967  0.0  0.0      0     0 ?        S<   07:08   0:00 [kpsmoused]
root      3357  0.0  0.0      0     0 ?        S<   07:08   0:00 [scsi_eh_4]
root      3358  0.0  0.0      0     0 ?        S<   07:08   0:00 [usb-storage]
root      3406  0.0  0.0      0     0 ?        S<   07:08   0:00 [zd1211rw]
root      3611  0.0  0.0      0     0 ?        S<   07:08   0:00 [softmac]
root      4587  0.0  0.0   3864   584 tty4     Ss+  07:08   0:00 /sbin/getty 384
root      4588  0.0  0.0   3864   588 tty5     Ss+  07:08   0:00 /sbin/getty 384
root      4590  0.0  0.0   3864   584 tty2     Ss+  07:08   0:00 /sbin/getty 384
root      4593  0.0  0.0   3864   588 tty3     Ss+  07:08   0:00 /sbin/getty 384
root      4594  0.0  0.0   3864   588 tty6     Ss+  07:08   0:00 /sbin/getty 384
root      4774  0.0  0.0  13076  1748 ?        Ss   07:08   0:00 /usr/sbin/acpid
root      4815  0.0  0.0      0     0 ?        S<   07:08   0:00 [kondemand/0]
root      4816  0.0  0.0      0     0 ?        S<   07:08   0:00 [kondemand/1]
syslog    4887  0.0  0.0  12296   724 ?        Ss   07:08   0:00 /sbin/syslogd -
root      4945  0.0  0.0   8132   588 ?        S    07:08   0:00 /bin/dd bs 1 if
klog      4947  0.0  0.1   6660  3372 ?        Ss   07:08   0:00 /sbin/klogd -P
103       4969  0.0  0.0  21740  1484 ?        Ss   07:08   0:00 /usr/bin/dbus-d
root      4985  0.0  0.0  60728  2384 ?        Ssl  07:08   0:00 /usr/sbin/Netwo
root      4999  0.0  0.0  28384  1408 ?        Ss   07:08   0:00 /usr/sbin/Netwo
root      5012  0.0  0.0  35192  1212 ?        Ss   07:08   0:00 /usr/bin/system
avahi     5032  0.0  0.0  29700  1504 ?        Ss   07:08   0:00 avahi-daemon: r
avahi     5033  0.0  0.0  29580   504 ?        Ss   07:08   0:00 avahi-daemon: c
root      5062  0.0  0.0  72312  2472 ?        Ss   07:08   0:00 /usr/sbin/cupsd
root      5081  0.0  0.0  38560  1388 ?        Ss   07:08   0:00 /usr/sbin/atiev
root      5149  0.0  0.0   6272   960 ?        Ss   07:08   0:00 /usr/sbin/dhcdb
107       5168  0.2  0.1  40256  4880 ?        Ss   07:08   0:00 /usr/sbin/hald
root      5171  0.0  0.0  41092  2532 ?        Ssl  07:08   0:00 /usr/sbin/conso
root      5233  0.0  0.0  22048  1316 ?        S    07:08   0:00 hald-runner
root      5335  0.0  0.0  24156  1288 ?        S    07:08   0:00 hald-addon-inpu
root      5338  0.0  0.0  24168  1320 ?        S    07:08   0:00 /usr/lib/hal/ha
107       5340  0.0  0.0  16672   988 ?        S    07:08   0:00 hald-addon-acpi
root      5365  0.0  0.0  24156  1272 ?        S    07:08   0:00 hald-addon-stor
root      5367  0.0  0.0  24156  1272 ?        S    07:08   0:00 hald-addon-stor
root      5369  0.0  0.0  24156  1284 ?        S    07:08   0:00 hald-addon-stor
root      5371  0.0  0.0  24156  1272 ?        S    07:08   0:00 hald-addon-stor
root      5374  0.0  0.0  24156  1276 ?        S    07:08   0:00 hald-addon-stor
root      5400  0.0  0.0  17760  1292 ?        Ss   07:08   0:00 /usr/sbin/hcid
root      5415  0.0  0.0      0     0 ?        S<   07:08   0:00 [btaddconn]
root      5416  0.0  0.0      0     0 ?        S<   07:08   0:00 [btdelconn]
root      5424  0.0  0.0  17656  1388 ?        S    07:08   0:00 /usr/lib/blueto
root      5427  0.0  0.0  17580  1172 ?        S    07:08   0:00 /usr/lib/blueto
root      5435  0.0  0.0      0     0 ?        S<   07:08   0:00 [krfcommd]
root      5509  0.0  0.0 116176  1896 ?        Ss   07:08   0:00 /usr/sbin/gdm
root      5512  0.0  0.1 128920  3348 ?        S    07:08   0:00 /usr/sbin/gdm
root      5516 14.9  3.7 191616 107840 tty7    Ss+  07:08   0:59 /usr/bin/X :0 -
root      5554  0.0  0.0  12284   912 ?        Ss   07:08   0:00 /usr/sbin/anacr
daemon    5568  0.0  0.0  16428   432 ?        Ss   07:08   0:00 /usr/sbin/atd
root      5583  0.0  0.0  18616   968 ?        Ss   07:08   0:00 /usr/sbin/cron
root      5608  0.0  3.7 191616 107840 tty7    S+   07:08   0:00 /usr/bin/X :0 -
root      5687  0.0  0.0   3864   588 tty1     Ss+  07:08   0:00 /sbin/getty 384
mario     5708  0.3  0.2  44012  6008 ?        S    07:09   0:01 /usr/lib/libgco
mario     5710  0.0  0.0  62044  2256 ?        S    07:09   0:00 /usr/bin/gnome-
mario     5711  0.0  0.3 195636  9000 ?        Ssl  07:09   0:00 x-session-manag
mario     5768  0.0  0.2 214268  7180 ?        Ss   07:09   0:00 /usr/bin/seahor
mario     5772  0.0  0.0  21452  1280 ?        Ss   07:09   0:00 dbus-daemon --f
mario     5773  0.1  0.4 258500 12224 ?        Sl   07:09   0:00 gnome-settings-
mario     5788  0.0  0.2 148204  6308 ?        Sl   07:09   0:00 /usr/bin/pulsea
mario     5791  0.0  0.0  57836  2692 ?        S    07:09   0:00 /usr/lib/pulsea
mario     5804  0.1  0.1 136140  3068 ?        Ss   07:09   0:00 gnome-screensav
mario     5805  0.0  0.0   3944   616 ?        S    07:09   0:00 /bin/sh /usr/bi
mario     5807  0.3  0.8 303884 23968 ?        S    07:09   0:01 gnome-panel --s
mario     5808  0.3  0.9 431764 26816 ?        S    07:09   0:01 nautilus --no-d
mario     5817  0.0  0.1 149828  3748 ?        Ssl  07:09   0:00 /usr/lib/bonobo
mario     5841  0.0  0.0  44772  2276 ?        S    07:09   0:00 /usr/lib/gvfs/g
mario     5878  0.4  0.4 194976 13604 ?        S    07:09   0:01 /usr/bin/compiz
mario     5881  0.0  0.5 220240 15776 ?        S    07:09   0:00 update-notifier
mario     5887  0.0  0.4 258088 11676 ?        Sl   07:09   0:00 /usr/lib/evolut
mario     5888  0.0  0.2 124388  7004 ?        S    07:09   0:00 tracker-applet
mario     5891  0.8  0.3 140116  9012 ?        SNl  07:09   0:03 trackerd
mario     5894  0.0  0.5 193900 16416 ?        S    07:09   0:00 python /usr/sha
mario     5895  0.0  0.4 220280 13920 ?        S    07:09   0:00 nm-applet --sm-
mario     5897  0.0  0.3 217748  9248 ?        Ss   07:09   0:00 gnome-power-man
mario     5898  0.0  0.1 189588  5352 ?        Ss   07:09   0:00 /usr/lib/gnome-
mario     5907  0.0  0.0  44772  2356 ?        S    07:09   0:00 /usr/lib/gvfs/g
mario     5910  0.0  0.1  63536  2876 ?        S    07:09   0:00 /usr/lib/gvfs/g
mario     5920  0.0  0.4 206512 11660 ?        S    07:09   0:00 /usr/lib/gnome-
mario     5924  0.0  0.6 253368 17200 ?        Sl   07:09   0:00 /usr/lib/gnome-
mario     5927  0.1  1.5 419924 44944 ?        S    07:09   0:00 /usr/bin/python
mario     5929  0.0  0.5 222500 15128 ?        S    07:09   0:00 /usr/lib/fast-u
mario     5931  0.0  0.0   3944   552 ?        Ss   07:09   0:00 /bin/sh -c /usr
mario     5932  0.0  0.0   3944   584 ?        S    07:09   0:00 /bin/sh /usr/bi
mario     5934  0.2  0.4 146536 13280 ?        S    07:09   0:00 /usr/bin/gtk-wi
mario     5949  0.0  0.1  85676  3980 ?        S    07:09   0:00 /usr/lib/gnome-
mario     5952  0.0  0.0      0     0 ?        Z    07:09   0:00 [sh] <defunct>
dhcp      6898  0.0  0.0  15108  1468 ?        S    07:10   0:00 /sbin/dhclient
mario     7007  4.7  0.7 247980 19924 ?        Sl   07:11   0:11 transmission
mario     7122  0.7  0.5 231916 16188 ?        S    07:12   0:01 avant-window-na
root      7458  0.0  0.0   3944   552 ?        S    07:13   0:00 /bin/sh -c nice
root      7459  0.0  0.0   3848   672 ?        SN   07:13   0:00 run-parts --rep
root      7470  0.0  0.0   3944   604 ?        SN   07:13   0:00 /bin/sh /etc/cr
root      7491  0.0  0.0   8108   592 ?        SN   07:13   0:00 sleep 1042
mario     7493  5.1  2.4 472736 68616 ?        Sl   07:13   0:04 /usr/lib/firefo
mario     7881  4.8  0.8 281656 24036 ?        Rl   07:15   0:00 gnome-terminal
mario     7884  0.0  0.0  23572   968 ?        S    07:15   0:00 gnome-pty-helpe
mario     7885  1.5  0.1  20592  3500 pts/0    Ss   07:15   0:00 bash
mario     7902  0.0  0.1 151304  4524 ?        SNl  07:15   0:00 tracker-extract
mario     7905  0.0  0.3 243132  8812 ?        SN   07:15   0:00 totem-video-ind
mario     7906  0.0  0.0      0     0 ?        XN   07:15   0:00 [totem-video-i]
mario     7907  0.0  0.0  15064  1092 pts/0    R+   07:15   0:00 ps -aux

---

### Post by _sphinx_ on 2008-06-24
What's your processor dear, it's not alway RAM. Your X is using approx 14% and transmission 5%, I think that's more than normal.

---

### Post by XTR0RDiNAiRE on 2008-06-24
that is retarded i just took off visual effects and its runnin perfectly

how much ram does one need for everything to run smoothly

--whats this processor of which you speak

how would i check the processor

i know i have a amd 64
i dont know if thats what your talkin about

---

### Post by sujoy on 2008-06-24
yes thats what we were talking off :)

cpu ... central processing unit .... aka... processor
one thing i would like to add though, turn off tracker, keep compiz enabled and then try gimp.

tracker slowed me down a lot

---

### Post by ukripper on 2008-06-24
> **XTR0RDiNAiRE said:**
> that is retarded i just took off visual effects and its runnin perfectly

how much ram does one need for everything to run smoothly

--whats this processor of which you speak

how would i check the processor

i know i have a amd 64
i dont know if thats what your talkin about

I think your graphics card drivers are using more cpu to render X.
Ati drivers are notorious for this.

i would recomend you use drivers using envy not from ubuntu repos.

---

### Post by Kevbert on 2008-06-24
> **XTR0RDiNAiRE said:**
> that is retarded i just took off visual effects and its runnin perfectly

how much ram does one need for everything to run smoothly

--whats this processor of which you speak

how would i check the processor

i know i have a amd 64
i dont know if thats what your talkin about

Have you performed a memory check recently ?  You can do this via the grub boot menu (memtest).  It may be that you have some faulty ram or that it's not seated properly in its' motherboard socket.
To check the processor (CPU) you can go to System-Preferences-Hardware Information.
Are you running 64 bit Hardy 8.04 ?  That would help.

---

### Post by protogenesis on 2008-06-24
Not to sound too much like a newbie (on my end, not yours!), but are you using a graphic card or are you just running video straight from the motherboard?  If you're going straight in like my motherboard has -- I don't use a video card -- you are sharing physical memory when you use graphics.  I know for a fact that my old machines, ones that didn't have video cards, ran slow as thick syrup in the winter when I opened gimp or something visually intensive.  

If you're using a video card, you might want to post the specs here for a quick lookie-loo.  Even some medium-end video cards perform terribly with TheGimp.  

...however, 3 gigs worth of memory should be very adequate to run your system in GUI mode if you have at least a semi-decent medium-level video card.

---

