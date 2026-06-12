---
title: "usb drive read only how do I change that?"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by chickenPie4breakfast on 2012-04-09
For some reason when I try and copy a file to my usb flash stick (which was working fine earlier today) it says "the destination is read only" how do I change that using terminal or whatever

---

### Post by whatsaterminal on 2012-04-10
> **chickenPie4breakfast said:**
> For some reason when I try and copy a file to my usb flash stick (which was working fine earlier today) it says "the destination is read only" how do I change that using terminal or whatever


so how did you resolve this problem? inquiring minds want to know....

---

### Post by anejo on 2012-04-11
> **whatsaterminal said:**
> inquiring minds want to know....

If changing permissions is problematic, another way is to take ownership of that whole device with 'chown', eg.
```
chown -R yourusername:yourgroupname /path/to/usb
```

---

### Post by raja.genupula on 2012-04-11
read this

[https://help.ubuntu.com/community/Mount/USB#USB-Device_is.2C_or_become_suddenly_read_only_without_errors](https://help.ubuntu.com/community/Mount/USB#USB-Device_is.2C_or_become_suddenly_read_only_without_errors)

---

### Post by coilwinder on 2012-07-25
I did this, for a quick fix: 

Ran GParted, unmounted USB stick, formatted to fat32 (I didn't really have anything important on it).
Quit GParted, mounted it by selecting it under the "Places" menu.

Writeable again!
(Well at least I got to write one file there... so far so good)

---

