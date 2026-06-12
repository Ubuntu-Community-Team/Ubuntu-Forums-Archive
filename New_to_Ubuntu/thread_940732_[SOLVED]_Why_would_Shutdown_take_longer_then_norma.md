---
title: "[SOLVED] Why would Shutdown take longer then normal?"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by HellNoire on 2008-10-07
I'm not using the Custom Menu that Ubuntu has with the OS, I'm using the Main Menu type of Gnome Menu. And for some reason, hitting Shutdown takes about three minutes to load then it works normally after that. Anyone know what's taking it?

Also, I lost my splash screen under Ubuntu, it's showing me the start up commands. Any ideas on how to restore it?

---

### Post by unutbu on 2008-10-08
HellNoire, to get the splash screen back:
```

gksu gedit /boot/grub/menu.lst
```

Go down about 2/3 of the way through the file.
Find the stanza that looks like this:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```
Add 

```
quiet splash
```
to the end of the kernel line. That is, change the line that look something like this:
```

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro 

```
to 
```
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro quiet splash
```

Also look for the line that starts with
```
# defoptions
```
and make sure that the full line includes quiet splash:

```
# defoptions=quiet splash
```
By doing so, quiest splash will be added to your kernel line if/when you update your kernel package.

If your "# defoptions" line is lacking "quiet splash" this might explain why you lost the splash screen in the first place -- it would have disappeared after a kernel update.

Regarding the slow shutdown behavior: I'm not sure I know the answer. Are you saying when you click the icon in the upper right corner, it takes a long time for the window with the shutdown button to appear?
Or are you saying that you click the shutdown button and nothing happens for 3 minutes?

---

