---
title: "How to disable the bootup splash screen?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by matiz on 2008-07-15
How to disable the bootup splash screen?
I just want to know what are loading when boot, the fedora is doing it in well.

---

### Post by philinux on 2008-07-15
Install and run startupmanager.

Very easy gui for changing boot stuff.

---

### Post by bobnutfield on 2008-07-15
If you don't already have it installed, install StartUpManager from Synaptics.  You can disable it from there.  Or, you can remove the "splash" option from the booting kernel in your /boot/grub/menu.lst file.

Bob

---

### Post by WRDN on 2008-07-15
Type:

```
sudo gedit /boot/grub/menu.lst
```

Now, on a "kernel" line, remove the words "quiet splash".

For example:

```
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=90ea8561-1dc6-4bb6-86bf-4ec61513e6cc ro quiet splash
```

. . . would become:

```
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=90ea8561-1dc6-4bb6-86bf-4ec61513e6cc ro 
```

---

### Post by kukibird1 on 2008-07-15
You can hit CTRL ALT F1 when the bootsplash starts to see which programs are loading without disabling bootsplash.

---

### Post by matiz on 2008-07-15
Oh, thanks for all the replies, so nice ^^

---

