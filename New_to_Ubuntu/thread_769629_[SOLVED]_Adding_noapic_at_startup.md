---
title: "[SOLVED] Adding noapic at startup"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by SpongeBob SquarePants on 2008-04-26
Hello all,

I can get the live CD to boot up using the "noapic" code. But once  Ubuntu is installed I get a kernel panic on reboot. On  adding the "noapic" code, again, it boots into the HD install just fine. So is there any way to add this to a boot up script somewhere, so I don't have to keep on manually typing it in every time I restart my box?

Thanks

---

### Post by LaRoza on 2008-04-26
I think it can be added to the menu.lst

Run the follow commands:

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_BK
gksudo gedit /boot/grub/menu.lst

```

Add noapic to the kernel options.

If it doesn't work, boot into recovery and delete /boot/grub/menu.lst and rename /boot/grub/menu.lst_BK to menu.lst.

```

rm /boot/grub/menu.lst
mv /boot/grub/menu.lst_BK /boot/grub/menu.lst

```

---

### Post by frup on 2008-04-26
I'm going to guess you can probably add it to /boot/grub/menu.lst but I could quit well be wrong.

I have only ever seen one laptop have an acpi issue and we were able to fix it by downloading some acpi package. What manufacturer is your computer/motherboard

(I just realised to typed apic maybe I am thinking of something else even)

---

### Post by FuturePilot on 2008-04-26
You can add that to grub's menu.lst.
```
gksudo gedit /boot/grub/menu.lst
```
Find the line that looks like this
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```
you can add your options at the end of the last line like so
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **noapic**
```

Then run ```
sudo update-grub
```

---

### Post by SpongeBob SquarePants on 2008-04-26
Thanks all......it worked a treat:)

---

