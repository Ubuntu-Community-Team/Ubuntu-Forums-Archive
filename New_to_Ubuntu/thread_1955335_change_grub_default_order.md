---
title: "change grub default order"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by squrl on 2012-04-09
I have tried a dozen different posts to change the boot order in Lucid. 

The startup-manager program accepts the inputs and does its post updates but nothing changes. 

How do I change the boot order in 10.04 ???

---

### Post by forrestcupp on 2012-04-09
You could try [Grub Customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer). I've had more luck with that. Just add their PPA and install it.

---

### Post by squrl on 2012-04-09
I got grub cutomizer and tried it. Nothing changed.

Thanks anyway

---

### Post by skabople on 2012-04-09
In /boot/grub/grub.cfg is where the grub config is. Simply edit that file. There should be a line that says default=1 or something like that. Whatever you change that file to afterwards run update-grub. In case something goes wrong have a live boot handy ;) . If you like you can post your grub config and let me know how you want to boot and I can let you know exactly what to do :)

---

### Post by Elfy on 2012-04-09
> Whatever you change that file to afterwards run update-grub.As soon as you run update-grub any manual changes will be lost to grub.cfg.

---

### Post by skabople on 2012-04-09
True don't run update-grub lol

---

### Post by squrl on 2012-04-09
to much screwing around. 

I removed the drive with 12.04 and reinstalled grub. Nothing seemed to work and I didn't like unity anyway.

thanks for the ideas.

---

