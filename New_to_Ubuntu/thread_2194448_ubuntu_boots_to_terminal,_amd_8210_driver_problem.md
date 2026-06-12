---
title: "ubuntu boots to terminal, amd 8210 driver problem?"
date: 2013-12-18
forum: New to Ubuntu
---

### Post by frankelrs-gmail on 2013-12-18
[solved] tried 12.04.3, 13.04, 13.10, mint16 on acer v5-122p
all boot to terminal,  This is not a dual boot problem, but a graphics driver problem.
how do I get the correct driver onto my usb boot drive?
Or is there any other way to get there from here?

---

### Post by Bashing-om on 2013-12-18
frankelrs-gmail; Hi ! Welcome to the forum .

Your situation may well be that no driver is loaded.

Please provide the output of terminal codes:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
Then we can advise on a means to install the graphics driver.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by frankelrs-gmail on 2013-12-20
Thank You "bashing-om".  I decided not to add the missing driver at this time.  Mainly because this notebook doesn't have a Ethernet connector
and first I would have had to get the wifi codes added via console input; a bit beyond my skills.  What I did do was try to install Fedora 20, which worked!
Anyway, maybe in a few months, Ubuntu will have fixed this problem and I can return home.   Perhaps my "temporary fix might help some beginner with a newish
AMD APU or AMD Graphics set.  Thanks again

Bob

---

### Post by Bashing-om on 2013-12-20
frankelrs-gmail; Hey,

Quite welcome. Any solution beats no solution.
Getting WiFi up and running with no wired connection can be a real pain. It can be done; I have seen threads where it happened !

As you do have resolution, please mark this thread as solved, aids others seeking a solution and helps keep the forum tidy .

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

