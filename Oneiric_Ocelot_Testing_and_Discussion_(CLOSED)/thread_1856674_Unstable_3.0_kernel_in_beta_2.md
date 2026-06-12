---
title: "Unstable 3.0 kernel in beta 2 ?"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by WitchCraft on 2011-10-08
I downloaded 11.10 beta 2 from 
[http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)


Just wanted to let everyone know that it's using an unstable 
kernel...


After a successful installation, it hangs at boot after
```

Refined TSC clocksource calibration: 3210.779 MHz.
Switching to clocksource tsc

```


One also gets a:
> 
Error "fixing recursive fault but reboot is needed"


One can restart as many times as one wants, that error persists.



Seems to be the same as this one here:
[http://comments.gmane.org/gmane.linux.kernel/1147176](http://comments.gmane.org/gmane.linux.kernel/1147176)

Ironically, the live-CD kernel seems to be of a lesser version, so installation and running it works fine...

I cannot boot in the recovery environment to compile a new kernel, it hangs even there. I cannot switch to an earlier kernel, since it does not have one, in short, it's permanently <snip> up...

---

### Post by MG&amp;TL on 2011-10-08
I have a 3.0 kernel and it's working fine...I thought it was stable.

---

### Post by WitchCraft on 2011-10-08
Solved, by this:

Add to your grub boot line 
```

acpi=off nomodeset xforcevesa

```

Found on
[http://askubuntu.com/questions/50451/error-fixing-recursive-fault-but-reboot-is-needed](http://askubuntu.com/questions/50451/error-fixing-recursive-fault-but-reboot-is-needed)

For people not from the en-us keyboard-layout-culture, knowledge of the en-us keyboard layout is required :)
The equal sign is top rightmost, right left before backspace ;-)
[IMG]http://www.glimpsejournal.com/images/2.1Liao-800px-KB_United_States-NoAltGr.svg.png[/IMG]

---

### Post by WitchCraft on 2011-10-08
The login screen looks nice :)

---

### Post by MG&amp;TL on 2011-10-08
That it does.

---

### Post by WitchCraft on 2011-10-12
> **MG&TL said:**
> That it does.

Unforunately, Gnome3 with Unity isn't very usable.
I switched to KDE however, in order to get a decent window mananger.
Anybody knows where one sees the list of open programs in Gnome3 ?

Wasn't able to switch to GnomeClassic with gdm, but with kdm it works. Might be my installation however, I did it in a hurry, before leaving to holidays.

The good thing however, is the bougoues telecom 3G+ stick worked fine out of the box on Ocelot.

---

### Post by MG&amp;TL on 2011-10-13
Gnome classic isn't installed by default.

Gnome3 (gnome-shell), you press the meta key, or push your mouse against the top left.

---

