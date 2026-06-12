---
title: "root"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Techarmy on 2008-11-12
i need to do things on my root acount but i dont know how to use it plz help:lolflag:

---

### Post by Shwefty on 2008-11-12
Well, it depends on what you're trying to do.  A lot of Linux lovin' is done through the command line too.  Before the command, you'd type "sudo" to give you root permissions.  Such as:

```
sudo apt-get wine
```

Which should download the Wine app.

---

### Post by DGortze380 on 2008-11-12
> **Techarmy said:**
> i need to do things on my root acount but i dont know how to use it plz help:lolflag:

Ubuntu doesn't suggest using a root account. Precede your command with sudo to run it as root.

That being said, if you know what you're doing, it possible to enable root. I just can't tell you how on the forum.

---

### Post by aysiu on 2008-11-12
Tell us what you think you need a root account for, and we'll tell you the proper way to do it.

---

### Post by Shippou on 2008-11-12
> **Shwefty said:**
> Well, it depends on what you're trying to do.  A lot of Linux lovin' is done through the command line too.  Before the command, you'd type "sudo" to give you root permissions.  Such as:

```
sudo apt-get wine
```

Which should download the Wine app.

That's sudo apt-get install wine .

Usually, you use sudo, as shwefty said, to gain root permissions. 

There are many things you can do as root:
1. Install applications.
2. Modify system settings.
3. Open applications as root.
4. Delete ALL files from your hard drive in ALL partitions.
5. Make files which are owned by root.
6. Change file and/or directory ownership.
7. MAC spoofing.
8. Modify disk partitions.

That's what basically you can do as root. And more.

(Btw, for #4, ask for explanations first.)

Have fun with the command line. It is a very handy tool, and a very powerful one (as compared to the Windows DOS prompt). You'll never know when you'll use it, and it IS a lot faster than GUI.

---

### Post by AndyCee on 2008-11-12
Just to clarify - the root account is disabled by default in Ubuntu, and the rules of the Ubuntuforums restrict the instructions from being posted on them.

The "sudo" command works by default similarly to "su"
"gksudo" is the graphical "su"

It is fairly easy to enable the root account (via several different means) and posted on many different websites but they aren't discussed here.

The best explanation I know of this is [here]("http://ubuntuforums.org/showthread.php?t=765414").

---

### Post by Shwefty on 2008-11-12
> **Shippou said:**
> That's sudo apt-get install wine .

Usually, you use sudo, as shwefty said, to gain root permissions. 

There are many things you can do as root:
1. Install applications.
2. Modify system settings.
3. Open applications as root.
4. Delete ALL files from your hard drive in ALL partitions.
5. Make files which are owned by root.
6. Change file and/or directory ownership.
7. MAC spoofing.
8. Modify disk partitions.

That's what basically you can do as root. And more.

(Btw, for #4, ask for explanations first.)

Have fun with the command line. It is a very handy tool, and a very powerful one (as compared to the Windows DOS prompt). You'll never know when you'll use it, and it IS a lot faster than GUI.

Haha, 'doh!  Good catch sir!

---

### Post by Techarmy on 2008-11-12
well i need to modify xorg.conf and it syays i dont have premision to do so so how would i do it???

---

### Post by llamakc on 2008-11-12
Open a Terminal. Type:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-BACKUP

sudo nano /etc/X11/xorg.conf

```

---

### Post by Techarmy on 2008-11-12
btw u can check out my personal site at geeksforu.ucoz.com

---

### Post by bodhi.zazen on 2008-11-12
See also this link : [uwiki]RootSudo[/uwiki]

---

### Post by jimmy the saint on 2008-11-12
back up the file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

then open it with root privilages with gedit (text editor)
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Koaguin on 2008-11-12
I enabled root by opening a terminal and typing,
```
sudo passwd root
```

---

### Post by aysiu on 2008-11-12
> **Koaguin said:**
> I enabled root by opening a terminal and typing,
```
sudo passwd root
```
That's completely unnecessary just to edit the /etc/X11/xorg.conf file.

---

### Post by Techarmy on 2008-12-11
> **Shippou said:**
> That's sudo apt-get install wine .

Usually, you use sudo, as shwefty said, to gain root permissions. 

There are many things you can do as root:
1. Install applications.
2. Modify system settings.
3. Open applications as root.
4. Delete ALL files from your hard drive in ALL partitions.
5. Make files which are owned by root.
6. Change file and/or directory ownership.
7. MAC spoofing.
8. Modify disk partitions.

That's what basically you can do as root. And more.

(Btw, for #4, ask for explanations first.)

Have fun with the command line. It is a very handy tool, and a very powerful one (as compared to the Windows DOS prompt). You'll never know when you'll use it, and it IS a lot faster than GUI.
well i am going to clean my old hard drive and i want to add it on to my 120 gb

---

