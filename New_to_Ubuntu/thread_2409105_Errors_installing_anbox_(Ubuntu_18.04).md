---
title: "Errors installing anbox (Ubuntu 18.04)"
date: 2018-12-27
forum: New to Ubuntu
---

### Post by rndbroom on 2018-12-27
[COLOR=#242729][FONT=Arial]I am new to Linux and not sure how to fix these problems.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have attached an image showing the two problems while running the following commands[/FONT][/COLOR]
$ sudo apt install linux-headers-generic anbox-modules-dkms
$ snap install --devmode --beta anbox
[COLOR=#242729][FONT=Arial]I am running the update command as well. It returns there are 317 packages that could be updated. I run the command to see the list, but not sure how to install the updates.[IMG]https://i.stack.imgur.com/Pbmwo.png[/IMG][/FONT][/COLOR]

---

### Post by howefield on 2018-12-27
Use..

```
sudo apt upgrade
```

to upgrade the packages, then try the anbox install again and see how it goes.

---

### Post by pauljw on 2018-12-27
also, 18.04 is setup to auto-update out of the box which may explain the locked files.  if you just give it some time after first booting to complete checking for updates you may be able to then install said software.

---

### Post by rndbroom on 2018-12-27
> **howefield said:**
> Use..

```
sudo apt upgrade
```

to upgrade the packages, then try the anbox install again and see how it goes.


Thank you.
I am still getting the same udev error though.

It keeps failing at 'connect anbox: opengl to core: opengl'
That is when is starts failing and throwing errors.

Just got this error:

ERROR can not set up udev for snap "anbox" : cannot reload udev rules : exit status 2

---

