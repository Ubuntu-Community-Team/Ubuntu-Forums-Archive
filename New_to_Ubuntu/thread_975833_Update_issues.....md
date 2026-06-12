---
title: "Update issues...."
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Volund on 2008-11-08
I just (attempted) to update to 8.10 from hardy, and though it installed fine, on restart, it froze on the loading bar (the one with the ubuntu logo above, and the orange bar filling below) in the 3rd bar section (if that matters somehow). I have restarted several times, and it freezes up in exactly the same place every time.

Do I have any options? or should I just go and download the ISO and re-install?

Thanks for any help.

---

### Post by tvtech on 2008-11-08
sure there are always options. boot into recovery mode/ safe mode I can't remember what grub calls it.

---

### Post by Volund on 2008-11-08
> **tvtech said:**
> sure there are always options. boot into recovery mode/ safe mode I can't remember what grub calls it.

well... I tried booting into recovery mode, but it freezes up at [22.224615] cs: IO port probe 0x3e0-0x4ff

what does that mean?

---

### Post by defishguy on 2008-11-08
Are you using a laptop with a Dlink network card by any change?

---

### Post by Volund on 2008-11-08
> **defishguy said:**
> Are you using a laptop with a Dlink network card by any change?

No, it is a Atheros® 802.11b/g wireless-LAN card

---

### Post by Volund on 2008-11-09
Sorry to bump, but my laptop is useless untill I get a fix :(.

any help is very much appreciated

---

### Post by kernelhaxor on 2008-11-09
It might not be worth your time to debug .. If I were you, I'd go for a fresh install

---

### Post by Crafty Kisses on 2008-11-09
You should try booting into verbose mode so we can see where it stops at, while it's booting press the following:
```
Cntrl+Alt+F2
```
It will tell you where it stops at. You then can post it back here at the forums then I or someone else can help you.

---

### Post by Volund on 2008-11-09
> **Codename said:**
> You should try booting into verbose mode so we can see where it stops at, while it's booting press the following:
```
Cntrl+Alt+F2
```
It will tell you where it stops at. You then can post it back here at the forums then I or someone else can help you.

well, ctrl+alt+F2 did nothing while booting.


while booting into recovery mode it came up that it stopped at

```
[22.224615] cs: IO port probe 0x3e0-0x4ff
```

---

