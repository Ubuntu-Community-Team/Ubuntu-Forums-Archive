---
title: "Help me collect distro themes"
date: 2008-12-23
forum: Other OS Talk
---

### Post by Flimm on 2008-12-23
Do you use another distro? Could you help me collect the default themes that come with the most popular linux distros?

And what will I do with them, you may ask. Put them in 'pigment' format, for the world to use with [Epidermis](http://epidermis.tuxfamily.org). Simply put, Epidermis lets you customise the look and feel of your entire GNOME desktop in one go.
That will help me finish [this blueprint](https://blueprints.launchpad.net/epidermis/+spec/make-distro-skins)

I'll need themes that can be applied on Ubuntu (GNOME), including:
[LIST][*]GTK themes
[*]Metacity themes
[*]wallpapers
[*]icon sets
[*]GNOME splash images
[*]mouse cursors
[*]GDM login themes
[*]usplash themes
[*]grub themes
[/LIST]

I've had trouble finding these on [gnome-look.org](http://gnome-look.org), people only post modifications of the official themes on there.

I've heard that Fedora and Linux Mint have particularly good looking themes by default, I'd love to see them. I've already got the Ubuntu Studio theme.

Thank you for your help.

---

### Post by maybeway36 on 2008-12-23
Most if not all of the Linux Mint theme is in this .deb package:
[http://packages.linuxmint.com/pool/main/m/mint-artwork-gnome/mint-artwork-gnome_1.7_all.deb](http://packages.linuxmint.com/pool/main/m/mint-artwork-gnome/mint-artwork-gnome_1.7_all.deb)
Be careful, installing it will also change your GNOME defaults. Use:
```
dpkg -x mint-artwork-gnome*.deb linuxmint/
```
to extract to a folder without installing.

---

### Post by Flimm on 2008-12-26
Thanks, I've made the [Linux Mint skin](http://epidermis.tuxfamily.org/?q=node/62).

---

### Post by Orlsend on 2008-12-27
We should move this to the Desktop & Customization sub-forum

---

