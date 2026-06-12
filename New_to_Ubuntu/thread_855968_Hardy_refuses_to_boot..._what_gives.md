---
title: "Hardy refuses to boot... what gives?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by LordKthulhu on 2008-07-11
Just upgraded to Hardy. On first boot, the splash screen proceeded as far as progress bar, and then stuck there for a while, ultimately reverting to a black screen with a bunch of messages (beginning with ata2:00 Exception Emask). Any idea what's going on? Where do I start looking?

Thanks!

---

### Post by Dark_Stang on 2008-07-11
Hit Ctrl+Alt+F1 when booting to go to a terminal while it's booting. Let us know if you see any error messages or if you're able to login. If you are able to login run the command "startx" to see if you can get a GUI up.

---

### Post by LordKthulhu on 2008-07-11
Weird. Older kernel version boots just fine. Maybe I should just stick with that and save myself some effort...

---

### Post by wolfen69 on 2008-07-11
i chose to stick with the .16 kernel. if it is not broke, don't fix it. but that's just me.

---

### Post by Dark_Stang on 2008-07-11
> **LordKthulhu said:**
> Weird. Older kernel version boots just fine. Maybe I should just stick with that and save myself some effort...
There yah go. Just lock that kernel version so it stops bugging you to upgrade.

---

### Post by LordKthulhu on 2008-07-11
2.6.22-15 for me, then. Just changed GRUB to boot it by default. Thanks, guys.

---

