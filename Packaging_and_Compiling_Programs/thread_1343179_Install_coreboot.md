---
title: "Install coreboot"
date: 2009-12-01
forum: Packaging and Compiling Programs
---

### Post by ubuntosaure on 2009-12-01
Hello,

I want to install a free bios on an old computer.
Can you explain how to install coreboot?

Thanks

---

### Post by Yellow Pasque on 2009-12-01
```
sudo apt-get install grub-coreboot
```

---

### Post by SevenMachines on 2009-12-01
if your looking to actually flash your rom with coreboot firmware, look at 
[http://www.coreboot.org/Category:Tutorials](http://www.coreboot.org/Category:Tutorials)
for your motherboard and see if its supported. there should be a little set of build instructions there which you can use to build a rom and then use flashrom, also from that site, to flash it to your motherboard.
as mentioned before, you'll want grub-coreboot too, i believe this is the 'payload' that the minimal coreboot bios uses. although it should be said i havent used coreboot so i'm not certain on these things
obviously great thought needs to go into deciding to flash your bios, as i'm sure you know, this can turn your old computer into an old brick :)

---

### Post by SevenMachines on 2009-12-01
you might actually want to try the [hardware forum]("http://ubuntuforums.org/forumdisplay.php?f=332") for this and see what they say, there might be more coreboot users there.

---

