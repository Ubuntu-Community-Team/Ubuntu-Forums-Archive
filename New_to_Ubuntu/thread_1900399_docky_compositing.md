---
title: "docky compositing"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by Primus1 on 2011-12-26
Hi I'm getting a message saying docky needs compositing and when I look at dockys settings there is no mention about what this is. I have searched the forum but not found anything on this. using lucid.
thanks

---

### Post by alphacrucis2 on 2011-12-26
> **Primus1 said:**
> Hi I'm getting a message saying docky needs compositing and when I look at dockys settings there is no mention about what this is. I have searched the forum but not found anything on this. using lucid.
thanks

Compositing means that your graphics card/driver supports 3d acceleration. What graphics card do you have? You can find out via:

```
sudo lshw -C display
```

---

### Post by Primus1 on 2011-12-26
Thanks:

display               
       description: VGA compatible controller
       product: RV630 [Radeon HD 2600XT]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:26 memory:d0000000-dfffffff(prefetchable) memory:fdde0000-fddeffff ioport:ce00(size=256) memory:fdd00000-fdd1ffff(prefetchable)

---

### Post by alphacrucis2 on 2011-12-26
> **Primus1 said:**
> Thanks:

display               
       description: VGA compatible controller
       product: RV630 [Radeon HD 2600XT]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:26 memory:d0000000-dfffffff(prefetchable) memory:fdde0000-fddeffff ioport:ce00(size=256) memory:fdd00000-fdd1ffff(prefetchable)

Strange. The fglrx driver should be giving you the required 3d acceleration support. What does

```
fglrxinfo
```

say.

---

### Post by Primus1 on 2011-12-27
Thanks for getting back :), here is the result:

dave@dave-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 XT
OpenGL version string: 3.2.9756 Compatibility Profile Context

dave@dave-desktop:~$

---

### Post by mcduck on 2011-12-27
> **alphacrucis2 said:**
> Compositing means that your graphics card/driver supports 3d acceleration. What graphics card do you have? You can find out via:

```
sudo lshw -C display
```

Working 3d acceleration isn't enough, you also need a compositing manager running. You can either use a window manager that has built-in compositing support (like Compiz) or a separate compositing manager like xcompmgr.

Primus1, what desktop environment (or session) are you using? If you use the old Gnome 2 desktop you need to make sure you are running Compiz ("desktop effects" enabled) or have enabled the compositing support in Metacity. Unity session (not Unity 2D) uses Compiz already so you shouldn't have problems there.

---

### Post by Primus1 on 2011-12-27
I don't know about  desktop environments/sessions but I've gone to 'CompizConfig Settings Manager' > Effects > Animations, Fading Windows, Window Decoration are ticked in use. Enable Gnome Compatibility is also ticked.
Oh, is this it? > Gnome Desktop, version: 2.30.2, Ubuntu, Build Date: 25/06/10

---

### Post by mcduck on 2011-12-27
Do you also actually get the mentioned effects? In that case Compiz is working and Docky should also work.

If you don't get the effects, go to System/Preferences/Appearance and make sure visual effects are enabled.

---

### Post by spcwingo on 2011-12-27
If you're on Gnome 2 and would like to enable compositing with metacity, press ALT+F2.  In the run dialog that pops up enter

```
gconf-editor
```

From within that editor click the drop-down for apps, then click the drop-down for metacity, next click general, and finally click the box beside "compositing_manager".

---

### Post by Primus1 on 2011-12-28
sorry, having more problems, the mouse keeps freezing and the screen hangs so I have to hold the power button till the machine closes down then restart it but have to go through this many times, sometimes the machine bleeps 4 times while booting and just keeps beeping, I assume this is like a POST error, are the two problems linked, I don't know it's driving me crazy. :confused:

---

### Post by spcwingo on 2011-12-29
> **Primus1 said:**
> are the two problems linked

More than likely they are linked.  If you still have a live CD laying around, boot from it and run the memtest.  Allow it to have a good overnight run, then check it in the morning.

---

### Post by Primus1 on 2011-12-29
> **spcwingo said:**
> More than likely they are linked.  If you still have a live CD laying around, boot from it and run the memtest.  Allow it to have a good overnight run, then check it in the morning.

I left the machine on all night suspended and when I woke it the screen didn't freeze, problem not fixed of course. Also I remember I have two hard drives on this machine! both have Ubuntu 10.04 so when starting I could boot from that :D hopefully it would not have the problems, could I run this memtest from the second disk to check the disk with the problem on it?

---

### Post by mcduck on 2011-12-29
> **Primus1 said:**
> I left the machine on all night suspended and when I woke it the screen didn't freeze, problem not fixed of course. Also I remember I have two hard drives on this machine! both have Ubuntu 10.04 so when starting I could boot from that :D hopefully it would not have the problems, could I run this memtest from the second disk to check the disk with the problem on it?

Memtest tests your RAM, not your hard drives. So it makes absolutely no difference which hard drive, CD, USB drive or whatever you run the memtest from.

Anyway, spcwingo most likely didn't mean that you should leave the computer powered on, or suspended, over night. Instead he meant that you should run the memtest, and let it run overnight. (since it's quite common for memory problems only start occurring after long continuous stress, which makes running a single cycle of memtest pretty much pointless). And no, memtest is not supposed to fix your problem. It might, however, tell you where the problem is, so you know what to fix. :)

---

### Post by spcwingo on 2011-12-29
Yes, I meant exactly what mcduck said.  I'm sorry to have caused any confusion.  :oops:

---

### Post by Primus1 on 2011-12-29
No not your confusion - mine. What I tried to say is I left the machine on standby instead of shutting it down completely to see if that would get around my problem of the mouse freezing which shows itself when I turn the machine on (no the keyboard doesn't work either at that time) As I say I woke the machine from standby this morning and the problem did not show itself. Hope I clearified what I said a little? Thanks

---

