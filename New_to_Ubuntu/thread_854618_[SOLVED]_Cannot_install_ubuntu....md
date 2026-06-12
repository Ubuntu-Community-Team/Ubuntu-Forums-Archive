---
title: "[SOLVED] Cannot install ubuntu..."
date: 2008-07-09
forum: New to Ubuntu
---

### Post by cristo-father on 2008-07-09
Hi ubunters.
While running the livecd of ubuntu the following message hits me right on the face(it still hurts).
"Busybox v1.1.3 (Debian...)...
Enter 'help' for a list of built-in commands.

(initramfs)"
Hope you can help.

---

### Post by Xerp on 2008-07-09
Sounds like a dodgy burn.

---

### Post by AOZ on 2008-07-09
When does this happen? right when you click dlownload or when u try to run the live cd? does the error say anythign else?

---

### Post by spiderbatdad on 2008-07-09
try pressing F6 at the boot up screen. You should see a line of code ending in "quiet splash." Delete --quiet splash, up to "ro" add the option "noapic" after "ro" so you have: ro noapic

Hit enter to boot.

---

### Post by cristo-father on 2008-07-09
> **AOZ said:**
> When does this happen? right when you click dlownload or when u try to run the live cd? does the error say anythign else?

When i run the live cd.
After i choose to install or run without changes.

---

### Post by cristo-father on 2008-07-09
> **spiderbatdad said:**
> try pressing F6 at the boot up screen. You should see a line of code ending in "quiet splash." Delete --quiet splash, up to "ro" add the option "noapic" after "ro" so you have: ro noapic

Hit enter to boot.

I deleted "quiet splash --" and in it's place i inserted 
"ro noapic" and pressed enter, but it still has busybox.

---

### Post by avtolle on 2008-07-09
Try this: delete "noapic" and insert therefor "all_generic_ide", press Enter.

---

### Post by spiderbatdad on 2008-07-09
you might also try: noapic nolapic

if that still fails, it might be worth considering burning a new image at slowest possible speed...also perhaps start with a new download...verify the md5sums...burn image...verify the md5sums of the cd.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by cristo-father on 2008-07-09
> **avtolle said:**
> Try this: delete "noapic" and insert therefor "all_generic_ide", press Enter.

It worked i was able to install.
Thanks.

---

