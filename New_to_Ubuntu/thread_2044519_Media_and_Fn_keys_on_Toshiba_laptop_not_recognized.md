---
title: "Media and Fn keys on Toshiba laptop not recognized"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by Annorax on 2012-08-19
I have an older Toshiba Satellite laptop with Kubuntu 12.04 installed. I am unable to get my laptop specific keys (Fn, Play, Stop, etc...) to be recognized. They are not showing up in xev nor via any KDE keymapper I can see.

I have installed fnfxd but when I launch it as root, I get 

```

FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could not open /proc/acpi/toshiba/keys.
Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or http://fnfx.sf.net/index.php?section=doc#kernel.

```

Going to that link doesn't work and I can't seem to access the documentation for fnfxd from their website ([http://fnfx.sourceforge.net/index.php?section=doc](http://fnfx.sourceforge.net/index.php?section=doc)).

Could someone please help me set this up? It looks like I need to enable something in the kernel which I am not sure how to do.

---

