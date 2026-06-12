---
title: "Root needed for gparted"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by Alan_Dean on 2014-05-21
I need to format a usb drive and I have always used gparted in Ubuntu. I have just installed Xubuntu which I like alot but do not know how to log in as root as now required to use gparted. Any ideas or alternative sotware to format my usb sticks. I do like using gparted though.

Thank you 

Alan

---

### Post by LastDino on 2014-05-21
Your  password is the one you used while installation. That should enable you to use gparted.

---

### Post by Alan_Dean on 2014-05-21
Thanks but I still need to login as root and this option is not available. Gparted is not shown in the menu

---

### Post by slickymaster on 2014-05-21
> **Alan_Dean said:**
> Thanks but I still need to login as root and this option is not available. Gparted is not shown in the menu

If you have Gparted installed you'll have an icon for it in Settings Manager, under the System section. Just double click it, type you password and you'll be good to go.

---

### Post by pfeiffep on 2014-05-21
I believe you should be able to launch gparted from a terminal with the correct permissions. To launch a terminal press keys **ctrl-alt-t **at the same time.
```
gksudo gparted
```

---

### Post by LastDino on 2014-05-21
> **Alan_Dean said:**
> Thanks but I still need to login as root and this option is not available. Gparted is not shown in the menu

I don't know who told you that, but if you've installed it, you can use it from the methods described in this thread. Xubu doesn't come with gparted installed like Ubuntu, you need to open software centre and type it in search, then install it.

---

### Post by slickymaster on 2014-05-21
> **LastDino said:**
> I don't know who told you that, but if you've installed it, you can use it from the methods described in this thread. Xubu doesn't come with gparted installed like Ubuntu, you need to open software centre and type it in search, then install it.

This ^^^

One other way of installing it is through the command line```
sudo apt-get update && sudo apt-get install gparted
```

---

### Post by deadflowr on 2014-05-21
> **LastDino said:**
> I don't know who told you that, but if you've installed it, you can use it from the methods described in this thread. Xubu doesn't come with gparted installed like Ubuntu, you need to open software centre and type it in search, then install it.

Ubuntu doesn't come with gparted installed either.
It does, however, come with in the live session.
But it isn't part of the installation packages.

That said, all you need to do if look for gparted within the xubuntu's menu system, probably under administration, or whatever xfce menu's say.
Once you click on it, you'll get a prompt for a password.
As already stated several times.

---

### Post by LastDino on 2014-05-21
> **deadflowr said:**
> Ubuntu doesn't come with gparted installed either.
It does, however, come with in the live session.
But it isn't part of the installation packages.

That said, all you need to do if look for gparted within the xubuntu's menu system, probably under administration, or whatever xfce menu's say.
Once you click on it, you'll get a prompt for a password.
As already stated several times.

:o
Well, pardon me then, my memory is bit fuzzy about it since I haven't used Ubuntu since 13.10. And the buntu fork I use, does come with it pr-installed :)

---

### Post by Alan_Dean on 2014-05-21
Thank you works great

---

### Post by pfeiffep on 2014-05-21
> Well, pardon me then, my memory is bit fuzzy about it since I haven't used Ubuntu since 13.10. And the buntu fork I use, does come with it pr-installedAll of us have fuzzy memories at times ... So open a terminal and type gparted - the instructions should be given to install gparted.

---

### Post by Alan_Dean on 2014-05-21
All those suggestions worked. Many thanks for the prompt and positive replies

---

### Post by LastDino on 2014-05-21
> **pfeiffep said:**
> All of us have fuzzy memories at times ... So open a terminal and type gparted - the instructions should be given to install gparted.

I believe  you! You forgot who was asking the question :P

@OP, I'm glad we could help ^^

---

