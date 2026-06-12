---
title: "What video drive am i using?"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by rj686 on 2008-11-25
It's been quite awhile since i used ubuntu and it seems things were moved around a bit. I don't know what video driver I'm using. DRI is enabled and xorg.conf just shows "configured video device". What's the command to show my driver info? Also do i still need to use FGLRX in order to game on an X1600?

---

### Post by Olivier2371 on 2008-11-25
Try to go to:

System->Administration->Hardware Drivers.

or you could try in the terminal:

uname -a

---

### Post by rj686 on 2008-11-25
Do i just not have to edit xorg.conf at all anymore? I remember when 1st using FGLRX having to change quite a few settings.

---

### Post by Olivier2371 on 2008-11-25
Do you want to see what drivers you are using?

or 

Do you want to change drivers?

You should only edit the file if you know exactly what you're doing.

---

### Post by CatKiller on 2008-11-25
> **rj686 said:**
> Do i just not have to edit xorg.conf at all anymore?

That's the plan. X.org has been significantly changed over the last few releases, to enable things like hotplugging input devices and displays. The xorg.conf side of things has been largely abstracted away.

Except for me, of course. I'm still using the carefully hand-crafted xorg.conf that I made when I was running Breezy Badger... :)

---

### Post by shifty_powers on 2008-11-25
well if you are using 8.10, then xorg.conf is largely empty...

---

### Post by philinux on 2008-11-25
> **CatKiller said:**
> That's the plan. X.org has been significantly changed over the last few releases, to enable things like hotplugging input devices and displays. The xorg.conf side of things has been largely abstracted away.

Except for me, of course. I'm still using the carefully hand-crafted xorg.conf that I made when I was running Breezy Badger... :)

What you gonna do when xorg is gone. As in gone for good. I'd be interested to know.

---

### Post by rj686 on 2008-11-25
> **Olivier2371 said:**
> Try to go to:

System->Administration->Hardware Drivers.

or you could try in the terminal:

uname -a

See what drivers I'm using. Hardware Drivres just shows me that i can change it. Uname -r shows my kernel version.

---

### Post by Olivier2371 on 2008-11-25
Yes Silly me!!! I got my command code mixed up. Sorry.

Is your graphic adapter working properly?

If yes, what more do you want.

---

### Post by CatKiller on 2008-11-25
> **philinux said:**
> What you gonna do when xorg is gone. As in gone for good. I'd be interested to know.

GNU/Linux has functionally-equivalent versions of UNIX applications that were written 40 years ago - I'm not convinced that the old methods will cease to work completely for quite a while.

At some point in the future, my computer will no longer be up to the task of running the new shiny. It's already moderately long in the tooth. When that time comes, I'll install Ubuntu on my new computer, copy my Home folder across, and probably already be using all the new stuff.

In the meantime, NVidia might have one day seen the light and opened up some specifications, or the reverse engineers have done enough of their mystical voodoo, so that the fully-automatic way is also fully-painless. For me, using the proprietary driver with the automatic configuration, the GDM login screen was absurdly huge. It was far easier to restore the backup of my xorg.conf that I knew worked than to actually fix the problem.

The only reason that I **have** a hand-crafted xorg.conf is because I used to use dual monitors, and it used to be necessary to jump through quite a lot of hoops to get that working, especially with the proprietary drivers and their pseudo-implementation of the X server. That might work perfectly well these days, but I don't run two monitors any more, so I haven't tried.

---

