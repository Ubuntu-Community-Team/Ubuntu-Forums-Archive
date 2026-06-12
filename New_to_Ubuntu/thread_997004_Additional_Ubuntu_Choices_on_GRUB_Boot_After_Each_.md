---
title: "Additional Ubuntu Choices on GRUB Boot After Each Update"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Tr!p on 2008-11-29
I've recently noticed after each update of Ubuntu 8.04 the list gets longer within the GRUB boot menu. I have two hard drives with Ubuntu on one and XP on the other. When I first installed Ubuntu there were three choices Ubuntu 2.6.24-19 (Generic) & 2.6.24-19 (Recovery) and XP. After a couple of security, etc updates that list is growing. 2.6.24-21, 2.6.24-22 (recovery and generic) I'm guessing these are the versions before the updates. Any way to correct this so ONLY the latest version shows up within the boot menu?

---

### Post by w4ett on 2008-11-29
You can delete the prior kernels using Synaptic...BUT I recommend that you keep at least one prior kernel to use if you have problems with the newest one.

---

### Post by bruce2000 on 2008-11-29
One way to do this is to edit the grub menu and comment out the sections you don't want:

First backup up the grub menu:

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.bak

```

Then edit the file with gedit:

```

gksu gedit /boot/grub/menu.lst

```

Next comment out the sections you don't want with #'s

---

### Post by bruce2000 on 2008-11-29
Just to add to what W4ett said, if you choose to use the synaptic method - be careful only to remove the kernal image and not any of the dependencies that go with it. I've done this before and screwed up the kernel, had to use an older one.

---

### Post by maandverband on 2008-11-29
> **bruce2000 said:**
> Then edit the file with gedit:

```

sudo gedit /boot/grub/menu.lst

```

It's the same thing I'd advise, but you use the wrong command. The right command is:

```

gksu gedit /boot/grub/menu.lst

```

For CLI-apps: use sudo.
For GUI-apps: use gksu (or kdesu when running KDE).

---

### Post by w4ett on 2008-11-29
> only to remove the kernal image and not any of the dependencies that go with it

Yep...I agree...plus when you remove the kernel image, grub automatically is updated.

---

### Post by bruce2000 on 2008-11-29
> **maandverband said:**
> It's the same thing I'd advise, but you use the wrong command.


Yes well spotted thanks for the correction Maandverband.

---

### Post by Tr!p on 2008-11-29
If I was to use Synaptic to remove prior kernal images (without the dependencies). I'm seeing tons of different packages, some with the Ubuntu symbol, some without. How would I identify these prior kernal images?

---

### Post by w4ett on 2008-11-29
For example...I am using 2.6.24-22...I can remove the [COLOR="Red"]kernel 2.6.24-21 and prior if I wanted to do so[/COLOR]  Installed packages are ticked in green (usually) in the package manager. (See Screenshot)

---

