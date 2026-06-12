---
title: "ubuntu and power cuts (help)"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Shrimp on 2008-08-14
hokay...
i was just using my ubuntu (hardy heron edition obv) minding my own buisiness when there was a power cut.

so when the powers back i just turn it on,everything seems ok the load up screens come on...yet...once everything had 'loaded' all i get is a black screen. nothing else. computer seems to be working fine. the moniter is ok also i tested it on another machine.

what can i do? or is my computer doomed to be a black screen for all eternity? the only programmes i was using at time of power cut was emesene and firefox.

i'm a fairly new user.

any help is greatly appreciated...

thank yooh =)

---

### Post by LowSky on 2008-08-14
what do you mean a blank screen?

Right from the start with bios loading

after the Uubuntu load screen?

---

### Post by Shrimp on 2008-08-14
the screen is just black. no writing or anything. i'm sorry if this is very little help but i'm really not the sharpest tool in the shed...

WAIT...found something that might help...thanks

---

### Post by LowSky on 2008-08-14
When does it happen right at bootup? or after the ubuntu load screen?

And don't forget sometimes even sharp tools break under stress

---

### Post by diwas on 2008-08-14
Does it happen everytime u boot up??

---

### Post by Vivaldi Gloria on 2008-08-14
> **Shrimp said:**
> the screen is just black. no writing or anything. i'm sorry if this is very little help but i'm really not the sharpest tool in the shed...

When you reach the black screen can you press ctrl+alt+f1 to get a terminal?

In terminal you reach give the commands:

```
sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start
```

and restart using the command

```
sudo reboot
```

Or when the boot starts press ESC to enter grub boot menu. Choose recovery to boot into a terminal.

---

