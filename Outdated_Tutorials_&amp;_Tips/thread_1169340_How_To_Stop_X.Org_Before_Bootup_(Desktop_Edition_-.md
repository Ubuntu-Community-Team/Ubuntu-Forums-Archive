---
title: "How To: Stop X.Org Before Bootup (Desktop Edition --&gt; Enhanced Server)"
date: 2009-05-25
forum: Outdated Tutorials &amp; Tips
---

### Post by BslBryan on 2009-05-25
Hello, everyone. :-)

A lot of people have a machine installed with Ubuntu desktop edition, but they find that they'd like to try out the server edition, so they dual-boot, reinstall, whatever.  

After seeing countless people doing this, I kept thinking "wouldn't it be easier to just stop the graphical environment from ever starting up?"  This way, it's possible to maintain resources, and have the option of going back to the Desktop anytime.  So, I'm writing a tutorial so we can do just that. :-)

**1. ** So we can disable the graphical environment, we'll need to disable the GDM (or KDM).  To do this, simply run this at the command line:
```
sudo update-rc.d -f gdm remove
```

Obviously, if you have KDE, you'll have to substitute accordingly.

**When you reboot your machine, you'll be presented with a text-only login prompt in place of the GDM.**

And there you have it!  It only took one step. :-)  Here are some things that you might want to try though:

If you want to run X.Org while it's disabled, run **as a normal user**
```
startx
```

There will be a gray screen that might stay up for a little while.  Do not freak out. :-)  This is normal, and it will go away once GNOME is fully loaded.

If you'd like to re-enable X.Org, run

```
sudo update-rc.d -f gdm defaults
```

When you reboot, you'll be presented with the GUI that we all know and love, i.e. the Desktop edition.

I hope that I've been of some help to everyone!

---

