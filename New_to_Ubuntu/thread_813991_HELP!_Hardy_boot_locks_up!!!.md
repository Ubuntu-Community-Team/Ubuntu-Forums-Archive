---
title: "HELP! Hardy boot locks up!!!"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by ALex! on 2008-05-31
hi everybody! well.. I have a problem with Hardy. The thing is I first had Gutsy and the I upgraded to Hardy.... But every kernel that went out locked up on me (I think they were only two...) so I decided to insert a LiveCD and delete my Ubuntu partition (I have dual boot with Vista), but I removed as well the GRUB, so now I can't boot either to Vista! I deleted my Ubuntu partition for a later "fresh" install, but now every time I use my Live CD, hardy locks up with the same error as the other kernels (the one that made me decide to delete ubuntu and fresh-install it again)

```
[37.720909] ACPI: EC: acpi_ec_wait timeout, status = 0, expect_event = 1
[37.720955] ACPI: EC: read timeout, command = 128
```

I don't know if you get me....

PLEASE HELP!!!

---

### Post by django0909 on 2008-05-31
You're not being particularly clear, (or I'm not reading that properly)

I don't understand how Hardy can lock up if you're booting from the Live CD. Are you saying you can't get the CD to work? And are you trying to return to a state where you can dual boot Hardy with Vista?

Sorry if I misunderstood what you said, just trying to make it a bit clearer :)

---

### Post by ALex! on 2008-05-31
> **django0909 said:**
> You're not being particularly clear, (or I'm not reading that properly)

I don't understand how Hardy can lock up if you're booting from the Live CD. Are you saying you can't get the CD to work? And are you trying to return to a state where you can dual boot Hardy with Vista?

Sorry if I misunderstood what you said, just trying to make it a bit clearer :)

Yes, I am! I'm trying to boot with the Live CD but when I choose the install option (in fact.. any option!) it locks up, as it did when I had hardy and new kernels went out...

And yes... I'm trying to dual boot Hardy and Vista

---

### Post by jonathanpeter on 2008-05-31
I have the same issue.  You get that error message just before the graphical boot screen.  Disabling the graphical boot screen fixes this.  Anybody know of another fix as I'd like to keep the graphical boot up screen.

---

### Post by shifty_powers on 2008-05-31
ahve you tried downloading and using the alternate install cd?

(it has no gui and is not a live-cd iirc, but it is farily easy to install with :D)

---

### Post by sayakb on 2008-05-31
Press F4 at the LiveCD choice screen and select Text mode install/safe graphics mode.

---

