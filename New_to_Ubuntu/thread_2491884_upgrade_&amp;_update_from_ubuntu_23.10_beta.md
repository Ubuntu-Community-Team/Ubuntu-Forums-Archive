---
title: "upgrade &amp; update from ubuntu 23.10 beta"
date: 2023-10-24
forum: New to Ubuntu
---

### Post by tuesdaybarrett on 2023-10-24
I installed ubuntu 23.10 beta. I checked software center for new release and nothing shows. any answers to this thx

---

### Post by tuesdaybarrett on 2023-10-24
Checked my system it shows via terminal Ubuntu 23.10 \n \l. Does this full version of ubuntu 23.10 is installed?

---

### Post by grahammechanical on 2023-10-24
You are using the latest Ubuntu release (23.10). Therefore the system cannot inform you about a newer release because there will not be one until the middle of April 2024.

If we install a beta version or an even earlier development stage version and regularly update/upgrade we eventually end up with the fully released latest version.

I have being running the development version of 23.10 for most of its 26 week development period. This is what I see when I now run this command

```
lsb_release -a
```

> graham@UbuntuDev:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 23.10
Release:    23.10
Codename:    mantic

In 2 or 3 weeks I shall convert this install of 23.10 into the development version of Ubuntu 24.04. I will track its development.

Regards

---

### Post by tuesdaybarrett on 2023-10-24
[SIZE=5]thanks for info. I use the following commands to update system[/SIZE]
[SIZE=2][COLOR=#333333][FONT=&quot]sudo sh -c 'apt-get update && apt-get upgrade && apt-get autoremove'[/FONT][/COLOR][/SIZE]
[SIZE=4][/SIZE][SIZE=3][/SIZE][SIZE=2][COLOR=#333333][FONT=Comic Sans MS, cursive]sudo apt update && sudo apt upgrade -y && sudo snap refresh && sudo flatpak update[/FONT][/COLOR][/SIZE]

---

