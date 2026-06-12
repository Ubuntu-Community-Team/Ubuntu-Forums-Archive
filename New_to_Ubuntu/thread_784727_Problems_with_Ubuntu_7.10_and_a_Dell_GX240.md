---
title: "Problems with Ubuntu 7.10 and a Dell GX240"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by EdBecerra on 2008-05-06
I just installed Ubuntu 7.10 on a used Dell Optiplex 240, and I'm having two problems with it.

First, and most important, is that it won't shut down properly. It does NOT display the usual shutdown progress bar, and it ends with a screen full of "network error" messages, then hangs there. I have to hit the power button to shut it down. This is even MORE annoying than the previous shutdown behavior with v7.04.

Second is that 7.10 does NOT like my Acer AL1512 LCD monitor. Halfway through the bootup, I get an error message from the _monitor_ stating "Input not supported". This also happens during shutdown. The screen eventually returns, but this is *very* irritating. This did NOT happen with v7.04, mind you.

I realize that this isn't much info, but being a relative new person to Ubuntu, and not the sort of person who mucks around in system internals, I need help knowing what sort of help I need to ask for!

And as a side note, please understand that I'm disabled and living on a (very!) small medical pension - most of my gear is donated and/or junked equipment (the Optiplex, for example, was a college machine that was no longer wanted when they bought all new machines.)

This means that "solutions" that involve things like "buy a new monitor" or "get a new piece of (fill-in-the-blank) gear" are solutions I can't undertake, because I can't afford them. I *use* Ubuntu because it's free. $300 or more for BillGates-ware isn't an option either.

If there's no solution, I'll have to go back to Ubuntu 7.04, simply because it *works* on the GX240 - and I really don't want to do that.

Thank you,

Ed Becerra

---

### Post by peterthewolf on 2008-05-20
Shutdown problem

     Replace network manager with wicd (just search wicd in google).

     Add acpi=force to the kernel line in /boot/grub/menu.lst

Screen problem
     Cannot help - same thing happens with my thinkvision - I am prepared to    just live with it.

---

