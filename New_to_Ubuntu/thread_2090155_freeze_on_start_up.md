---
title: "freeze on start up"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by unibroker on 2012-12-01
I shutdown my computer at the end of every day.  The next morning, without exception, I have to do a hard shutdown twice before I get a successful boot and no problems for the rest of the day.

I understand that dmesg overwrites the previous data with a subsequent reboot which I can confirm looking at that log with nothing signifying a problem.  Any suggestions for capturing the events leading up to these freezes?

I'm running 12.04 64 bit.

---

### Post by unibroker on 2012-12-02
I had the customary start up problems this morning and both events dropped me to terminal-like screen with a lot of computer output.  I wrote down one of the lines (Kernel panic-not syncing:Fatal exception in interrupt).  On googling this I'm finding similar complaints and everyone points to the 64 bit kernel iso.  Would building my own kernel solve this?

---

### Post by Wim Sturkenboom on 2012-12-02
Old logs are kept; check for files that have .1, .2 etc in them and analyze those.

> **unibroker said:**
> I had the customary start up problems this morning and both events dropped me to terminal-like screen with a lot of computer output.  I wrote down one of the lines (Kernel panic-not syncing:Fatal exception in interrupt).  On googling this I'm finding similar complaints and everyone points to the 64 bit kernel iso.  Would building my own kernel solve this?
If you can find the bug and fix it, building your own kernel will help.

---

### Post by unibroker on 2012-12-02
> **Wim Sturkenboom said:**
> Old logs are kept; check for files that have .1, .2 etc in them and analyze those.


If you can find the bug and fix it, building your own kernel will help.

Thanks for the suggestion.  I've been looking at the logs of this morning and wanted to share the last lines of the first crash to see if they are meaningful to anyone.  

```
ADDRCONF(NETDEV_UP): eth0: link is not ready
ADDRCONF(NETDEV_UP): eth0: link is not ready
 e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
 17.068789] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
 17.069091] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
27.632072] eth0: no IPv6 routers present
59.624959] do_trap: 42 callbacks suppressed
59.624965] sh[1630] trap invalid opcode ip:40f4fb sp:7fff2167cec0 error:0 in dash[400000+1a000]
59.680883] unity-greeter[1295]: segfault at 43800000788 ip 00007fb574d790a9 sp 00007fff23bf7800 error 4 in libgtk-3.so.0.400.2[7fb574ac2000+47a000]
59.772803] Process 1634(apport) has RLIMIT_CORE set to 1
59.772807] Aborting core
59.822087] apport[1633]: segfault at 7fff6d310cc8 ip 00000000004685f5 sp 00007fff6b78d528 error 6 in python2.7[400000+271000]
59.822113] Process 1633(apport) has RLIMIT_CORE set to 1
59.822116] Aborting core

```

Looks like these are only present in the first failed boot.  Something must change with each subsequent boot until by the 3rd one everything is as it should be for a stable boot.  At least it's reproducible!

---

### Post by unibroker on 2012-12-02
I shut down my computer this afternoon for a couple of hours.  When I restarted it and had gotten just past the login screen it crashed and a terminal screen appeared.  The last line said "Fixing recursive fault but reboot is needed!"  From what I've researched this has to do with the graphic driver(s).  In going back over the kernel log for this crash, I found this segment interesting ```
13.350480] [drm] nouveau 0000:01:00.0: Detected 1024MiB VRAM
 [   13.351596] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
 [   13.398127] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
 [   13.398131] [drm] No driver support for vblank timestamp query.
 [   13.419336] Adding 2095100k swap on /dev/sdf6.  Priority:-2 extents:1 across:2095100k 
 [   13.702966] [drm] nouveau 0000:01:00.0: allocated 1920x1080 fb: 0x310000, bo ffff880079134800
 [   13.703105] fbcon: nouveaufb (fb0) is primary device
 [   13.703262] Console: switching to colour frame buffer device 240x67
 [   13.703307] fb0: nouveaufb frame buffer device
 [   13.703309] **drm: registered panic notifier**
 [   13.703317] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
```

I bolded "drm:  registered panic notifier".  I believe "nouveau" is the open source graphics driver that installs by default.  During the installion of Ubuntu 12.04 I ticked Install Proprietary Drivers because I have a Nvidia graphics card.  Can these 2 drivers coexist or is this causing the conflict?

---

### Post by unibroker on 2012-12-03
I am almost positive it is a problem with the graphic's driver.  But when I checked Synaptic Package Manager there were no Nvidia drivers to remove.  This is what I get for the output of lshw ```
 *-display
                description: VGA compatible controller
                product: GT218 [GeForce 210]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:fb000000-fbffffff memory:d0000000-dffff
```I have read of other Nvidia card users having problems with the Nouveau drivers that are installed by default with the Ubuntu install.  I'm thinking of downloading the appropriate Nvidia drivers and purging the Nouveau.

---

### Post by aish_varya on 2013-07-05
i have the same problem, did you resolve this ?

---

### Post by dannyboy79 on 2013-07-05
i actually have this issue as well. i just keep rebooting until it finally boots into my login manager. i can post logs when i get home but wanted to post here to stay subscribed

---

### Post by unibroker on 2013-07-05
> **aish_varya said:**
> i have the same problem, did you resolve this ?

I just finished re-reading what I wrote 8 months ago hoping to refresh my memory.  I believe I encountered the problem when I tried to go open-sourced graphics driver instead of Nvidia's proprietary ones.  When I purged the open-source and then downloaded/installed the appropriate Nvidia drivers the problems were solved.  Currently my 7 year old HP desktop boots once on startup in the morning and hasn't frozen in months.

---

