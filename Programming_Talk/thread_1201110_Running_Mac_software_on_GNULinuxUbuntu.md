---
title: "Running Mac software on GNU/Linux/Ubuntu"
date: 2009-06-30
forum: Programming Talk
---

### Post by freakalad on 2009-06-30
I've heard the argument countless times that Mac is not much more than a glorifies BSD/Unix spin/port, and the OS seems to be testament to that fact (commands, file structure, etc)

What I've been wondering for a while now, is if there's a way of porting Mac software for use on my Ubuntu system, without the need to run it in a VM or an "emulator" like Wine (or a VM, both of which I've not been able to find: Mac on Linux)?

Some of the biggest motivators are:
* Games. games, games, games. Sorry to say guys, but the gaming on Linux is pretty sucky, and it's hard to convince people that I'm trying the get to "make the switch" to do so, especially kids, unless there are decent games to be had, without the mucking about with VM's or Wine
* Video & graphic apps. My fiancée & some mated are into video & multimedia production, and unfortunately Gimp & Blender are not nearly as production ready as PhotoShop & Maya, both of which have native Mac candidates. If I can offer some of those apps on Linux & show that they would actually run better on it, they'd be more willing to take the plunge

The the very least, I'll settle for some sort of Wine-type app that'll allow me to run Mac apps on my Ubuntu box(es), but something that'll build me a native tar.gz or deb installed would suffice (something similar to alien)

---

### Post by Tibuda on 2009-06-30
> **freakalad said:**
> I've heard the argument countless times that Mac is not much more than a glorifies BSD/Unix spin/port, and the OS seems to be testament to that fact (commands, file structure, etc)

What I've been wondering for a while now, is if there's a way of porting Mac software for use on my Ubuntu system, without the need to run it in a VM or an "emulator" like Wine (or a VM, both of which I've not been able to find: Mac on Linux)?
The Mac OS X kernel (Darwin) is based on FreeBSD and NEXTSTEP. It is opensource, and you can download it from Apple website. But this don't help you to run Mac apps in Linux. The executable binary format is different, and OS X applications rely on a proprietary toolkit not available (Cocoa). You would need to do to Cocoa what Wine did to the Win API.


> * Games. games, games, games. Sorry to say guys, but the gaming on Linux is pretty sucky, and it's hard to convince people that I'm trying the get to "make the switch" to do so, especially kids, unless there are decent games to be had, without the mucking about with VM's or Wine
I don't think Mac gaming is really any better than Linux gaming. There are some commercial games ported to Mac, but only few. It probably reflects the user market-share.


> * Video & graphic apps. My fiancée & some mated are into video & multimedia production, and unfortunately Gimp & Blender are not nearly as production ready as PhotoShop & Maya, both of which have native Mac candidates. If I can offer some of those apps on Linux & show that they would actually run better on it, they'd be more willing to take the plunge
Maya got a native Linux version, and Photoshop got a Windows version that you could try to run in Wine.

---

### Post by phrostbyte on 2009-06-30
GNUStep is to Mac, what Winelib is to Windows. They are implementing Cocca libraries on Linux. 

There is no Mach binary loader though so the author of the program must recompile the Obj-C code. But if it ever has a real demand an Mach binary loader can be written.

---

