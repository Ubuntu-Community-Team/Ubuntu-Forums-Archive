---
title: "&quot;screens found but not useable&quot; (low graphics mode)"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by lila on 2008-11-21
Hello,
having installed xubuntu 8.10, every time I start it tells me 
Error
Framebuffer bpp32 not supported for this chipset
Screen(s) found but not useable

I need to click ok for it to do anything else,
And then it starts anyway, with a few more "can't do this" type messages, all needing to be clicked ok, and eventually it tells me the display will be restarted in low graphics mode.
I click ok again, and it starts.
And it looks quite normal to me, I don't know what's low graphics about it, other than it refuses to download flash.  Or rather, it tells me it did but then the websites continue telling me I still need it.  But I don't know if that has anything to do with the low graphics or whether it's an independent problem.

Any ideas?
Lila:confused:

---

### Post by Peter09 on 2008-11-21
As a First Pass at configuring your Video Driver:
1. Check that there is no driver waiting to be enabled in System->Administration->Hardware Drivers
2. Boot into recovery mode and select 'xfix' from the menu, this may resolve it. (Check 1. after doing this as well)

Can you post the output of the terminal command to confirm the driver that you are using.
```
lshw -C display
```

---

### Post by midtoad on 2009-02-04
I have been having this same problem as well, running Ubuntu 8.10 inside a Parallels VM in Mac OS X.  Using the 'xfix' fix eliminated that error message for me. 

thanks!

---

