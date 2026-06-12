---
title: "[SOLVED] Azureus Language Switch?"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-05-07
Ok, I have to show you this one.

I was surfing around looking for plug-ins for Azureus.  I found one called AutoStop in the Azureus wiki.  The description reads:```
Azureus AutoStop Plugin
Copyright(c) 2004 Chris Rose
Released under the GPL

The purpose of this plugin is to help with people whose ISPs are anal-retentive
about upload bandwidth usage, like mine is.  Its purpose is to be a community-
friendly implementation of an upload limiter.  It will not permit upload cutoff
at less than a 1.0 share ratio, but other than that it will disable uploads for
a few ratios that are equal to or greater than that.
```
As I do have an anal retentive ISP, I thought this might be a good item to have.  I have used the same feature in BitComet for Windows with good success.  I downloaded it and installed it and got the result in the attached file.  Some of the menus appear to have to turned to Farsi or Hebrew or something equally unreadable to me.

I uninstalled the plug-in.  No change.
I re-installed Azureus.  No change.
I uninstalled Azurues and then installed Azureus.  No change.
I completely uninstalled Azureus and then installed Azureus.
I rebooted and went through the 2nd, 3rd and 4th steps again.  No change.

Help?

---

### Post by H.Callahan on 2008-05-07
Ok, the file attachment didn't work the first time.  Attempt #2.

Sorry about that!

---

### Post by H.Callahan on 2008-05-08
Ha!

I think I fixed my own problem. \\:D/ 

Apparently "Completely Remove" does not really mean completely remove.  After the 3rd go-around with this, I finally noticed that even after a "Completely Remove" uninstall, that there were two subdirectories (.azureus and .Azureus) in my ~/ directory that had not been removed.  Doing a complete removal and then deleting those subdirectories followed by an install seems to have brought back readable (at least by me) menus again.

Where's the button to thank myself? :wink:

---

