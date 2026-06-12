---
title: "Aspect ratio problem in VirtualBox after Ubuntu Update"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by dunbankin on 2012-11-16
Only just installed VirtualBox with Ubuntu as a guest OS on my Win7 64-bit PC a couple of days ago, so a real beginner, and already having problems.

Started Ubuntu in VirtualBox today, and was told I had Ubuntu updates waiting, just like Windows Update.  I said go ahead, and they were installed (53Mb).  I had to reboot the Ubuntu guest OS afterwards.  That's when my problems started.  I discovered I needed to reboot the host OS, and re-install Guest Additions in VirtualBox, after which some of the problems went away, but I'm left with this annoying one:
Before the update, Ubuntu fitted nicely into whatever window size I gave it, scaling nicely and properly as you'd expect as I re-sized the window.  After the update, it now insists on only being a rigid 4:3 aspect ratio, which doesn't work on my 16:9 1920x1080 screen.  So within the maximised VirtualBox window I have white space at left and right of the Ubuntu display, and I have Ubuntu scroll bars for up and down.  A quarter of the (Ubuntu) screen is off the bottom of the (VirtualBox) screen, and I have to use the scroll bars to see it.

Choosing Settings/Display shows that my display (unhelpfully described as 'VBX 0"') only has 4:3 resolution settings (max is 1600x1200).  I've tried 'Sticky Edges' both On and Off (no idea what this means), but it doesn't make any difference.

In the VirtualBox Toolbar, under View I have 'Switch to Fullscreen', 'Switch to Scale Mode' and 'Adjust Window Size' available, but none of these help.  There's also 'Switch to Seamless Mode' and 'Auto-resize Guest Display', but these are greyed out.  I can't get a fully-resizeable Ubuntu display which automatically scales to fit the window, like I had before the update.  

What am I doing wrong?  Why has the Ubuntu Update seemingly wrecked the display?  Can anybody help?

Regards
John

---

### Post by dunbankin on 2012-11-17
Ok - as you were.  I've started Ubuntu today, and it's working fine.  God knows what I did differently.  The problem has gone away, though why, I don't know.

---

### Post by El Tito on 2012-11-17
To get a full screen, you need to install guest additions (at least my case).

The problem you are talking about, is about the kernel. When you update your system,
if there is an update for the linux kernel and you do update, it may cause problems not only in virtualbox but also in some programs that work with a specific version of the kernel.

For example, in Fedora, the kernel updates are more frequent, and I had to repair my virtualbox every week (almost).

---

