---
title: "HOWTO: Re-install Grub after windows wipes it out"
date: 2008-06-15
forum: Outdated Tutorials &amp; Tips
---

### Post by abhiroopb on 2008-06-15
I found this really useful howto here: [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

Basically you have a good install of ubuntu and then realise that you want to dual-boot. You don't want to erase ubuntu, so you install windows. Grub then gets erased and there is NO way to get back into ubuntu.

So do the following:

1) Boot off the LiveCD

2) Open a Terminal (Applications-Accessories-Terminal) and type in the following commands, noting that the first command will put you into the grub "prompt", and the next 3 commands will be executed there. Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where you probably installed grub to during installation. If not, then adjust accordingly.

```

sudo grub
> root (hd0,0)
> setup (hd0)
> exit

```

4) Reboot (removing the livecd), and your boot menu should be back.

5) Open the grub file:
```

sudo gedit /boot/grub/menu.lst

```

6) Scroll to the bottom and add the following:
```

title   Windows XP
root   (hd0,0)
makeactive
chainloader   +1

```

Note that you should also verify that hd0,0 is the correct location for Windows. If you had installed Windows on the 4th partition on the drive, then you should change it to (hd0,3).

Good luck!

---

