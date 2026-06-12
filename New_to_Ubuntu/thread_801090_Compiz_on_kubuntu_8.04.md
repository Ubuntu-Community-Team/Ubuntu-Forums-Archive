---
title: "Compiz on kubuntu 8.04"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by browny254 on 2008-05-20
Hi, I tried setting up Compiz when i upgraded to 8.04 and havent previously used it, but I have no idea how to get it to work. I go to KMenu -> System -> Desktop Effects and it gets me to install the compiz engine which it does automatically. then when i select Extra Effects and apply that nothing happens...what else do I have to do to get it to work?

---

### Post by Golem XIV on 2008-05-20
You should install compizconfig-settings-manager either from the console or via Synaptic and then select the plugins that you want...  Any specific effect you're interested in?

---

### Post by browny254 on 2008-05-20
Ill try that. the one effect im really after is the one that displays all windows at once.

---

### Post by browny254 on 2008-05-20
ok when i try starting compiz i get this

```

$ compiz
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/kwin

```

---

### Post by browny254 on 2008-05-20
> **browny254 said:**
> ok when i try starting compiz i get this

```

$ compiz
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/kwin

```
> ok when i try starting compiz i get this

```

$ compiz
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/kwin

```

and when i close the console after doing that it pretty much crashes my desktop...all the titlebars disappear and my keyboard stopped working except for the tab button.

---

### Post by Golem XIV on 2008-05-20
What's your video card?  Looks like you need to install the restricted driver to get Compiz to work

---

### Post by browny254 on 2008-05-20
i have a nvidia geforce go 7300. 

i went here [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) and it appears i dont have the restricted drivers manager that it talks about for installing on 7.10 (i have 8.04) so i followed the instructions for 7.04. am i doing the right thing or should i be looking somewhere else?

---

### Post by Flare183 on 2008-05-20
It means that you must have your graphics card on the compatibility list for compiz.

---

### Post by browny254 on 2008-05-20
> **Flare183 said:**
> It means that you must have your graphics card on the compatibility list for compiz.
ok, so what should i do then?

---

### Post by browny254 on 2008-05-20
alright, after a bit of playing around i finally got the restricted drivers installed and compiz is working, except my resolution is at a maximum value of 640x480, how do i change this so i can get my normal resolution of 1280x800 (or higher than that if possible)

---

### Post by Golem XIV on 2008-05-20
Did you install the drivers from the "Hardware drivers" application?  That's the "official" way of doing it.

To change the resolution try installing nvidia-xconfig (through apt-get or Synaptic).  Before you run it, though, make a copy of your current configuration:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
so if you screw something up and you boot into terminal mode you can get it back with
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Good luck!

---

