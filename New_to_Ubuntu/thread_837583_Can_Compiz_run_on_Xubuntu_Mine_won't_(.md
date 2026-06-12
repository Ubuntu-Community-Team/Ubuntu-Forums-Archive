---
title: "Can Compiz run on Xubuntu? Mine won't :("
date: 2008-06-22
forum: New to Ubuntu
---

### Post by esotericguy on 2008-06-22
I've just installed Xubuntu via Wubi the other day and then installed compiz. i've checked the boxes and tried the commands but nothing works. Is something extra needed to run it on Xubuntu?

---

### Post by saj0577 on 2008-06-22
alt+F2

```
compiz --replace
```

Saj

---

### Post by esotericguy on 2008-06-22
> **saj0577 said:**
> alt+F2

```
compiz --replace
```

Saj

nope, did not work

---

### Post by stalkier on 2008-06-22
> **esotericguy said:**
> I've just installed Xubuntu via Wubi the other day and then installed compiz. i've checked the boxes and tried the commands but nothing works. Is something extra needed to run it on Xubuntu?

Do you have CCSM, Emerald, and Fusion-icon installed also? Please also check if your restricted drivers are enabled.

---

### Post by bigplrbear on 2008-06-22
> **stalkier said:**
> Do you have CCSM, Emerald, and Fusion-icon installed also? Please also check if your restricted drivers are enabled.

+1
also, be sure that the system you are trying to run Compiz on has at least 256Mb of RAM. If it has anything less than that, Compiz won't even try to load.

---

### Post by stalkier on 2008-06-22
> **bigplrbear said:**
> +1
also, be sure that the system you are trying to run Compiz on has at least 256Mb of RAM. If it has anything less than that, Compiz won't even try to load.

I didn't even think of that. Good add man.

---

### Post by esotericguy on 2008-06-22
> **bigplrbear said:**
> +1
also, be sure that the system you are trying to run Compiz on has at least 256Mb of RAM. If it has anything less than that, Compiz won't even try to load.

I have 1gb of ram so that's not the problem, and i have all that other stuff, how do i check on the restricted drivers?

---

### Post by Biggy on 2008-06-22
> **esotericguy said:**
> I have 1gb of ram so that's not the problem, and i have all that other stuff, how do i check on the restricted drivers?

System > Administration > Hardware Drivers

enable device driver

---

### Post by Happy_Man on 2008-06-22
He's on Xubuntu, so it's not going to follow the regular GNOME menu system. Hm, I forget how to do it. What video card do you have? Can you enable XFCE's compositing? If so, then you have the correct drivers. 

To install CCSM, Emerald, and fusion-icon, enter this into a terminal: ```
sudo apt-get install compizconfig-settings-manager emerald fusion-icon
```

---

### Post by esotericguy on 2008-06-23
:-?> **Happy_Man said:**
> He's on Xubuntu, so it's not going to follow the regular GNOME menu system. Hm, I forget how to do it. What video card do you have? Can you enable XFCE's compositing? If so, then you have the correct drivers. 

To install CCSM, Emerald, and fusion-icon, enter this into a terminal: ```
sudo apt-get install compizconfig-settings-manager emerald fusion-icon
```

still nothing. I was thinking of just "uninstalling" xubuntu with wubi, then puting back ubuntu. Thanks for the help. although i switched to xubuntu because ubuntu was having the same problems. I'm not sure what i did to my system that's stopping me from having a sweet compiz desktop:-?

---

### Post by gn2 on 2008-06-23
> **esotericguy said:**
> I was thinking of just "uninstalling" xubuntu with wubi, then puting back ubuntu. 

No need, just run:```
sudo apt-get install ubuntu-desktop
``` then re-boot, click Sessions at the log-in screen and select Gnome.

---

### Post by forestpixie on 2008-06-23
Just a question because I don't know - does compiz work in wubi?

---

### Post by esotericguy on 2008-06-24
> **gn2 said:**
> No need, just run:```
sudo apt-get install ubuntu-desktop
``` then re-boot, click Sessions at the log-in screen and select Gnome.

then how do i get rid of the xfce enviroment?

---

### Post by gn2 on 2008-06-24
> **esotericguy said:**
> then how do i get rid of the xfce enviroment?

Copy and paste the relevant terminal command on [**this page**]("http://www.psychocats.net/ubuntu/puregnome.php") to remove Xubuntu 8.04

Note: you will need to use the different links listed on the page for different versions, 7.10 Gutsy, 7.04 Feisty, 6.10 Edgy, 6.06 Dapper if you are using any of those.

---

