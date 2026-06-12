---
title: "Fresh install - how to do"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by kingleviathan on 2008-11-27
Hi Guys

I was reccently trying to update my ubuntu from 7.04 to 7.10. Though the process is straightforward i must have done something wrong. The result is that my screen is full of squigly lines on a large orange background. Looks kinda like playdough melting away. Its boots ok until the main screen is meant to come up.then the screen is just bizarre.

Anyway considering I have no valuable data on the hard drive. Seems to me it would make more sense to just wipe the disk and install the latest Ubuntu.

How do I wipe the hard drive? and then add a fresh install? (I will need to either get a cd copy of ubuntu or download a copy on my windows computer.

---

### Post by dross_kuh on 2008-11-27
Just get the latest CD of whichever flavour you prefer and go for an install.
When it gets to the part about patitioning just tell it to use the full Hard Drive and it will format and repartition it for you.

---

### Post by fooman on 2008-11-27
before you reformat/reinstall, try this...boot up and at the grub menu,  choose "recovery mode".  when you get to the prompt,  type the following and press enter:

```
dpkg-reconfigure -phigh xserver-xorg
```

then see if you can boot normally.

---

### Post by kingleviathan on 2008-11-27
Ok, I got into the grub menu and i select recovery mode. But I get this message straight away Error 17: Cannot mount selected partition...press any key to continue (returns back to grub menu).

I tried this on all the menu options  and get the same response except for the Ubuntu option whch leads to the blurry screen.

So im not sure how to apply foomans suggestion??? 

But im wondering, if I cant select anything in the grub menu, how does the hard disk recognise if I wanted to do a fresh install from a Cd??

---

### Post by Michael.Godawski on 2008-11-27
> Ok, I got into the grub menu by pressing ESC on the keyboard. But for some reason when i press the up and down arrors (or any keys on the keybard for that matter) there is no response on the grun menu. Why would this be?Just curious.. Do you really need to know why your badly upgraded system does somehow not recognize your keyboard? :) 
Perhaps you have plenty of time, then we might work our way through... but you could just consider doing a fresh install of the newest version. And probably everything will work again.

Edit:
 > how does the hard disk recognise if I wanted to do a fresh install from a Cd??
Posted before your last post... Let's just try to boot from the latest Live CD.

---

### Post by kingleviathan on 2008-11-27
Thanks Michael...

I actually worked out why grub didnt recognise my keyboard. Apparentl Grub doesnt recognise USB keyboards. So was able to fix that with my old keyboard. :)

Ok..will try get my hands on a CD of UBUNTU tomorrow and do a fresh install. :)

---

### Post by CatKiller on 2008-11-27
> **kingleviathan said:**
> I actually worked out why grub didnt recognise my keyboard. Apparentl Grub doesnt recognise USB keyboards. So was able to fix that with my old keyboard. :)

Actually, that's not strictly true. The older, dedicated, keyboard interfaces are well-supported in hardware. USB keyboards need something that can interpret the generic USB signals as keyboard signals.

This interpreter is provided by the kernel, once the kernel has loaded. At the point that GRUB is running (or any bootloader, for that matter, or if you were running something really old like DOS) the kernel hasn't loaded, so this interpreter isn't in place. Bootloaders are tiny.

However, motherboards that came out after USB keyboards became common are able to load an interpreter themselves. This is set with the USB Keyboard Legacy Mode setting (or something similar) in the BIOS. This setting is generally not set by default, since it can occasionally cause key press problems, and Operating Systems have their own interpreter anyway.

Unfortunately, without this interpreter being loaded, you can't get into the BIOS to set it with a USB keyboard ](*,) So you could plug in a non-USB keyboard, go into the BIOS, set this, and then re-boot with just the USB keyboard. Then you can use your USB keyboard with the BIOS, and with GRUB, or whatever bootloader you choose to use.

---

### Post by CatKiller on 2008-11-27
> **kingleviathan said:**
> I tried this on all the menu options  and get the same response except for the Ubuntu option whch leads to the blurry screen.

Now that you've got your keyboard working in the GRUB menu, you can look at the boot options for each of the entries and see what the difference is between the option that boots and the options that don't. I suspect that the boot partition location is different for the ones that don't work, which is why those entries can't find the drive to boot from.

> But im wondering, if I cant select anything in the grub menu, how does the hard disk recognise if I wanted to do a fresh install from a Cd??

Your hard disk doesn't need to recognise anything, and doesn't really have anything to do with the keyboard. It's your motherboard's BIOS settings that will determine which drive your computer will try to boot from.

---

