---
title: "Ubuntu live locks up on start"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Lukky on 2008-05-14
Hello All,
   I am trying to install Ubuntu on my new Hp dv6700 laptop. I have a live cd of version 7. It locks up with two lines on a black screen. Something like 
Checking battery
running cd scripts for boot

I let it set on that screen for a while like 15 or 20 minutes and nothing. I checked cd integrity and it shows to be fine. I just used this cd to load up my desktop.

---

### Post by NightwishFan on 2008-05-14
Move over the desired boot option in live cd, press f6, delete "quiet splash" and add ```
--acpi=off
```

---

### Post by Lukky on 2008-05-15
I tried that and Ubuntu said something about no timer try booting with "Noacpi"
That worked.

Thanks

---

