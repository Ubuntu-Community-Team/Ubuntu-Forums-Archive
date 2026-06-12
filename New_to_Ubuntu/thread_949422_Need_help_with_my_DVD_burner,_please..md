---
title: "Need help with my DVD burner, please."
date: 2008-10-16
forum: New to Ubuntu
---

### Post by L Campbell on 2008-10-16
I have an Iomega 'Super DVD' R/RW model #31367200 which I am hoping to get operating on my PC with 8.04. After doing a couple of searches, it appears that this is NOT Iomega's latest version of this machine and I didn't find any information about his model number.

It is connected to my 'puter and functions to the point that the drawer opens and closes. Also, I can feel a minute vibration, as if the DVD inside is spinning up.

When I go to Places > Computer the Computer – File browser opens and I see the icon for my Iomega but when I click on it, all I get is this message:-

"Unable to mount location"
"No media in drive"

I have tried this with a Knoppix DVD and a Live Ubuntu CD, all with the same result.

If you have a suggestion as to what I should try next, I would appreciate it.

TIA.

---

### Post by 3rdalbum on 2008-10-16
This is an unusual problem; DVD burners don't require any special drivers, and it looks like your computer is recognising the burner. For some reason, Nautilus doesn't want to mount the device.

Try mounting the disc manually:

```
pmount /dev/scd0 iomega
```

If it doesn't work, then it might be the wrong device file. Try /dev/scd1 or /dev/hdc or /dev/hdd, and then remember which one worked.

When you need to eject the disc:

```
pumount iomega
```

Then press the little button on your drive and the disc should come out.

[COLOR="Red"]If any of this doesn't work, send me a PM.[/COLOR]

---

