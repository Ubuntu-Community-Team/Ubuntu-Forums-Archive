---
title: "How can I back out packages?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by timandjulz on 2008-06-01
I am considering installing a new package on a 64bit 8.04 Hardy system.  But if this screws up I want to ensure I can get back to my original system.

The problem is that I don't know what is changing.  Does it impact my desktop?  Does it modify boot/grub/menu.lst?  Does it add drivers, etc?  Does it overwrite files?

Windows XP added a handy System Restore feature that snapshotted drivers and gave an ability to roll back to a specific date.  Does either this feature exist or is there some way to tell what a package will modify before installing it?

Thanks,
Tim

---

### Post by Joeb454 on 2008-06-01
I doubt you'll lose anything just by installing something.

What are you trying to install?

---

### Post by philinux on 2008-06-01
Might be handy if you named the package.

---

### Post by timandjulz on 2008-06-01
> **Joeb454 said:**
> I doubt you'll lose anything just by installing something.

What are you trying to install?

I have installed app/driver/etc packages that have modified x11.org and others.  When they messed up my system I wasn't able to get back to my original system.  Since I am not a Linux expert I had no idea what to do.  Which files did I need to restore?

I am looking for a general approach to this.  i.e. When installing a package that might change /etc/{something important} then make a backup of it.

I will give you an example: I upgraded my kernel to 2.6.24-17.  I then updated a few packages and installed a couple of other packages.  Honestly I don't know what screwed up my system but sound didn't work anymore.  How do I get that back?  I ended up switching back to 2.6.24-16 kernel and everything worked again... I assume this is due to modules being loadable for that version.

------------------
But back to the question at hand... how can I tell what is going to be changed so I can back up appropriate files just in case?

---

