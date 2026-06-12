---
title: "Accessing GRUB through GNOME desktop"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by ChrisRChamberlain on 2008-04-28
Hi all

Linux newbie - please be gentle :)

Installed Ubuntu Server 8.04 and was able to access and delete/ rename etc GRUB entries through a menu option on the GNOME desktop.

Seem to remember 'Hardware' as part of the option - unable to locate that facility again.

Any pointers, please?

TIA

---

### Post by ad_267 on 2008-04-28
Usually you edit the GRUB menu by editing the file /boot/grub/menu.lst. You will need superuser privileges to do this. So assuming you haven't installed a desktop in the server edition you would use:

```
sudo nano /boot/grub/menu.lst
```
or
```
sudo vim /boot/grub/menu.lst
```

If you have a desktop you can use:

```
gksu gedit /boot/grub/menu.lst
```

Edit: Reread your post, this might be what you're after: [http://packages.ubuntu.com/hardy/qgrubeditor](http://packages.ubuntu.com/hardy/qgrubeditor)

so:

```
sudo apt-get install qgrubeditor
```

---

### Post by Wilfred on 2008-04-28
There is also a package called "startupmanager" from the universe repository.
It creates a new entry in System-Administration where you can configure Grub and usplash.

It seem to work fine, but changing the resolution, gave on my laptop an error message while booting.

hope this helps!

---

