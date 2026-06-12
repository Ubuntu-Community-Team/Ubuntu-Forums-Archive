---
title: "Grub question"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by NWAdawg on 2008-09-18
I couldn't be happier, I fairly new to Linux, and managed to get a dual booting Ubuntu 8.10a5 and Xubuntu (each on their own HDD's) on my test machine. Everything is running great. Grub is working, only thing is where and how do I edit boot order? Right now Xubuntu is loading by default, I would like to change to Ubuntu as default.

---

### Post by iaculallad on 2008-09-18
To edit your menu.lst file:

Open /boot/grub/menu.lst for editing (Ubuntu):

```
gksudo gedit /boot/grub/menu.lst
```

When doing it in (x)Ubuntu:

```
sudo mousepad /boot/grub/menu.lst
```

Find this line and change the default value to point to the value of your desired kernel.

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR="DarkRed"]default         0[/COLOR]**
```

Sample values using my current menu.lst file will be:

```
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-15-generic		**[COLOR="Blue"]<----- 0[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)		**[COLOR="Blue"]<----- 1[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic		[COLOR="Blue"]**<----- 2**[/COLOR]
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)		**[COLOR="Blue"]<----- 3[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+		**[COLOR="Blue"]<----- 4[/COLOR]**
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

If I want to boot on "Ubuntu 7.10, kernel 2.6.22-14-generic" as default, I would change the value of default to 2 instead of 0.

> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR="DarkRed"]default         2[/COLOR]**

After you had changed it, Save and close. And while on your terminal, reboot.

```
sudo shutdown -r now
```

---

### Post by rockerphil on 2008-09-18
you can edit the GRUB menu by running this command:

```
sudo nano /boot/grub/menu.lst
```

but be sure to make a backup of the file just i case, hope this helps,

Phil

---

### Post by kansasnoob on 2008-09-18
I like to just install startupmanager:

```
sudo apt-get install startupmanager
```

It'll then show up in System > Administration > Startup-Manager:

[ATTACH]85640[/ATTACH]

---

### Post by NWAdawg on 2008-09-18
Thanks for the fast replies. I got it changed through the startup manager. Thank again.

---

