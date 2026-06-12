---
title: "How do I make Ubuntu work with GeForce 8800gts?"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by L.G.S on 2008-08-28
I have Ubuntu on one HDD, along with Windows XP on another parition.

I want to move my HDD into another computer, but this computer has no on board graphics and uses GeForce 8800GTS graphics card.

When I try to boot into Ubunutu I get an error about the GUI, then it shuts down. 

Is there some kind of tutorial or could somebody please tell me how to get it working with ubuntu?

---

### Post by halitech on 2008-08-28
you probably need to boot into recovery mode (as root) and reconfigure the video card

when you start to boot and get to grub, select recovery mode and let it boot (you'll end up in a shell) then run
dpkg-reconfigure xserver-xorg then reboot and it *should* work

---

### Post by tuxxy on 2008-08-28
Can you pull up a terminal before it shuts down by pressing CTRL + ALT + F1

If so enter this command and re-enable the drivers

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by philinux on 2008-08-28
> **L.G.S said:**
> I have Ubuntu on one HDD, along with Windows XP on another parition.

I want to move my HDD into another computer, but this computer has no on board graphics and uses GeForce 8800GTS graphics card.

When I try to boot into Ubunutu I get an error about the GUI, then it shuts down. 

Is there some kind of tutorial or could somebody please tell me how to get it working with ubuntu?

If this is Hardy do as suggested and select the recovery mode.

In Hardy there is now a menu not a shell that appears first. Choose xfix then reboot.

---

### Post by L.G.S on 2008-08-28
I'm not too good with Ubunutu so I will give it and try and get back.

I'm running Feisty Fawn.

---

### Post by C.S.Cameron on 2008-08-28
I think it is much easier to install Nvidia cards in Hardy than in Feisty.

---

### Post by L.G.S on 2008-08-28
There were so many steps to the reconfig!

I got up to when I had to choose the colour amounts, 16/24/etc, then I had a problem.

For some reason when I choose one, ubuntu opens up the command line underneath and doesn't let me choose any options. I only have the ability to run a command. Is this supposed to happen?

---

### Post by halitech on 2008-08-28
once it was done configuring everything it should have dropped you back to the command line. Try typing in ```
startx
``` and see what happens

---

