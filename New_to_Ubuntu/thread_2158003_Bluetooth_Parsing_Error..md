---
title: "Bluetooth Parsing Error."
date: 2013-06-27
forum: New to Ubuntu
---

### Post by BlueKite on 2013-06-27
Hi,

I'm having some trouble setting up the bluetooth on my netbook.
I have no icons for it anywhere and so, after some googling found out that typing

```
bluetooth-applet
```

into the terminal it shoould appear. It didn't.

On the first try the terminal returned a load of parsing errors, mostly about the adwaita theme. On this forum I found that I had to install gnome-themes-standard. I did this but it has still left me with the first line of the parsing errors, shown in the attached screenshot.

Any help in correcting this would be most appreciated.

Many thanks,

BlueKite.

[ATTACH=CONFIG]244216[/ATTACH]

---

### Post by BlueKite on 2013-06-27
Hi, 

Some information I forgot to add: Netbook is an Acer Aspire One AOA150 running Lubuntu 11.10.

In a terminal I have run apt-get update and apt-get clean, and I have also just installed the latest updates from the Update Manager.

I don't know what else to try. Any ideas?

Many thanks,

BlueKite.

EDIT: Update: I just found this by doing abit more googling, [https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/877293](https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/877293)

Look at the post marked #3.
When accessing the file /usr/share/themes/Lubuntu-desktop/gtk-3.0/gtk-buttons.css
via the terminal, do I need to use sudo?

If someone could confirm this I would be grateful.

Thanks.

---

### Post by BlueKite on 2013-06-28
Hi,
 
Well I went ahead and typed

```
sudo leafpad /usr/share/themes/Lubuntu-desktop/gtk-3.0/gtk-buttons.css
```

into the terminal, and the file opened.

But it was empty, so no wonder there is a parsing error.

Anyone know how I can fix this?

Thanks,

BlueKite.

---

