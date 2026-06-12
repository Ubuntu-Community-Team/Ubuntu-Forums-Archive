---
title: "updates"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by hotcarl on 2008-07-19
Last night I did my Ubuntu 8.04 updates via the update manager.  It looked like everthing went smoothly and I shutdown my computer for the night. Today when I went to go load up my computer everything was running fine.  When I started WOW (through wine) my computer got all pixely and weird boxes were showing all over my screen.  Everything was working fine until the updates last night/this morning.  Is there any way to roll-back these updates and possibly re-install them fresh so that this error does not occur any longer?

Thanks

---

### Post by brian_p on 2008-07-19
> **hotcarl said:**
> Last night I did my Ubuntu 8.04 updates via the update manager.  It looked like everthing went smoothly and I shutdown my computer for the night. Today when I went to go load up my computer everything was running fine.  When I started WOW (through wine) my computer got all pixely and weird boxes were showing all over my screen.  Everything was working fine until the updates last night/this morning.  Is there any way to roll-back these updates and possibly re-install them fresh so that this error does not occur any longer?

Use your file manager to arrange the files in /var/cache/apt/archives/ in date order. Determine which files correspond to last night's update. Find the versions immediately prior to these and install with

```
sudo dpkg -i <file>
```

May be a bit messy if the dependencies are awkward and doesn't work if you have cleared out apt's cache.

Also, your problem and updating may be completely unrelated.

---

### Post by JagDragon on 2008-07-19
If you are using a proprietary driver from ATI or Nvidia or somewhere else, that driver will not have rolled forward with the kernel, due to legal restrictions. Every time you kernel updates, you have to re-install the drivers (I made a script to do mine).

This artefacting you are seeing could be to do with a nonexistent driver.

---

### Post by hotcarl on 2008-07-19
Thanks for the tips.  But so far nothing has helped.  I tried looking to see which updates I had done so that I may rollback the updates I had made.  For some reason those updates do not show.  All I see from today is a filed named "locked" and another named "partial" both which contain about 0 bytes.  

As for the driver idea.  I used envy to remove the driver, restarted my machine and had envy reinstall the driver.  When I went to go load the game the same issue occurred.  Any ideas why this could be happening?  I really appreciate the help.

---

### Post by JagDragon on 2008-07-19
Hmm. Wine recently went through an overhaul, as they announced version 1.0. Wine could be playing up, but it sounds more likely to be your graphics card.

Check the [wine page for WOW]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329"), and see if anyone has had the same issue. There is also some config there that you may have yet to do to your system.

---

### Post by brian_p on 2008-07-19
> **hotcarl said:**
> Thanks for the tips.  But so far nothing has helped.  I tried looking to see which updates I had done so that I may rollback the updates I had made.  For some reason those updates do not show.  All I see from today is a filed named "locked" and another named "partial" both which contain about 0 bytes.

If that is all you get it looks like you have the cache cleared daily. On my machine (with date format being year-month) I could do

```
ls -l /var/cache/apt/archives/ | grep "2008-07"
```

to see what had been downloaded in July.

---

