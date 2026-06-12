---
title: "Bug in Hardware Drivers Manager under 2.6.24-19?"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by t0p on 2008-08-29
I originally posted about this yesterday in [someone else's thread]("http://ubuntuforums.org/showthread.php?t=902787"), but I'm making this thread now because I want to know if I was alone in experiencing this problem or if there is a deeper issue.

My computer's a little old - it's a Pentium 4, with a NVIDIA graphics chip - I think it's a **TNT2 RIVA** or something similar.

I've always had no problem getting the proprietary driver for this chip through Hardware Drivers Manager - I'd enter the manager, the driver would be listed there, and I could click to enable.  Easy-peasy.

But yesterday, I got a kernel update - from 2.6.24-16 to **2.6.24-19**.  After the update I restarted as usual... and it booted into some "low graphics mode", I couldn't even successfully click onto the System menu until I rebooted into recovery and told it to fix X!  This has never ever happened on this computer before - and I've installed Feisty, Gutsy and now Hardy on this machine.

Once X had been "fixed" so I got 800 x 600 res, I went into Hardware Drivers Manager so I could get the driver and restore my res to 1280 x 1024... but there was no driver listed there!

Following advice given on this forum, I tried to install a driver from the NVIDIA site.  The install did not work.  So then I installed **Envyng**.  I ran Envy, told it to install a driver for me.

Watching the console messages as Envy did its thing, I noticed one that said it was removing **glx-legacy** driver.  This set off some alarm bells, as I thought I recognized that as being the driver I wanted.  If Envy was removing it, that meant glx-legacy was originally there.  But the Hardware Drivers Manager hadn't shown it.

Anyway, Envy installed a driver.  I restarted... and again got the low graphics mode and had to use recovery to fix X.  800 x 600 again.  I revisited the Drivers Manager... and now the legacy driver I needed *was* there.  So I clicked it through, restarted, and now I have my 1280 x 1024 res back.

So: is this behavior *normal* now for the 2.6.24-19 kernel?  Because it is not how things have ever gone before on this machine, with all the kernels I've had on it before.  Or is this a bug?

Also: the kernel update also "broke" my keyboard.  Not in any serious way, just swapped around a few symbols like @ and " and # and \... now I have two percentage symbols, and no uk pound sterling symbol (which is a pain as I live in the uk).  But that's a minor issue.

**If people could post details of their experiences of the Hardware Driver Manager under the new kernel (2.6.24-19) I would be very grateful** :)

---

### Post by falcon61102 on 2008-08-29
As far as  your graphics go, that sounds about normal.  Depending on the chipset some people have experienced problems just like your were they needed to reinstall the drivers.  Also, there is a new glx-legacy out and if i remember correctly it's actually named glx-legacy-new or something similar and thats more than likely what was installed back in the place of glx-legacy that was removed.  You should be good to go at this point.

As far as your keyboard goes, the kernal update more than likely reset your keyboard to the standard layout and may just need to be switched back to your UK settings.  Unfortunately, for the life of me, I can't remember exactly where those settings are.  It's under one of the System menus.  Sorry I couldn't be more helpful on that one as I'm not on my system right now.

---

