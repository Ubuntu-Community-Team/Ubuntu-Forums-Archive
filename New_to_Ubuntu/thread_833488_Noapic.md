---
title: "Noapic?"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Pap3r on 2008-06-18
I once got an error in the kernel while booting ubuntu that said something about "try to use the noapic option", because the IO-APIC or soemthing, wasn't functioning correctly.

I ended up needing to reinstall ubuntu (I wanted to anyway) and the problem went away because I installed it using the noapic flag.

I received my new 8800GT today, installed it and tried booting up.  Everything worked fine in POST, so it looked good.  This is a 64-Bit install of Ubuntu, and I have never had any errors (it's been running strong for a good month, it's 7.1, I had 8.04 for a while, but it didn't play games very well...).  When I got to the part of the boot where it starts with the kernel, I got an error that told me to try booting with the noapic flag.  How do I do that?  I went into recovery mode, which booted just fine, but was unable to figure out how to use noapic.

So, two things.  How do I do it, and why did it happen?

---

### Post by Pap3r on 2008-06-18
Sorry for the double post, but this is urgent for me.  I'm on my 'Buntu comp right now.  I ended up adding ```
no apic acpi=off
```after my kernel in the menu.lst file, it hangs, no splash, screen receives nothing, but eventually it gets through.  Sadly, though, I'm in low graphics mode...

First thing to fix that I tried to change the driver I was using to the Geforce 8 series.  It told me to log off and back on, but nothing changed.  I have since tried this numerous times, every attempt has been futile.

Next, I went to the restricted drivers manager, hoping to get an easy fix.  Instead of it opening, I was told my hardware doesn't need any restricted drivers...  What?  Why?

I have no idea how to fix this, it's getting kind of annoying.

---

### Post by sdennie on 2008-06-18
I can answer one of those questions.  In the grub boot menu, select the kernel you want to boot and hit 'e'.  Then, move down one line and hit 'e' again.  That should let you edit the boot options.  Make sure noapic is there and then hit enter and then 'b' to boot that kernel.  To make that change permanent, after you've booted, edit /boot/grub/menu.lst and where you see "#defoptions=" and "#altoptions=", make sure to add noapic to those lines.  Afterwards, run:

```

sudo update-grub

```

---

