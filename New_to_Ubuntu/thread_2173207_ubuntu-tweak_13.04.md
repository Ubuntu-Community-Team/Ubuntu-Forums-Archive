---
title: "ubuntu-tweak 13.04"
date: 2013-09-08
forum: New to Ubuntu
---

### Post by sedoy on 2013-09-08
after install ubuntu tweak on ubuntu 13.04 it has error after run

ubuntu-tweak 
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : default
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading configurations from ~/.fonts.conf is deprecated.

(ubuntu-tweak:29055): Gtk-ERROR **: GtkBox child GtkTreeView minimum width: -1 < 0 for height 361
Trace/breakpoint trap (core dumped)


what is it? Why? How can I run it? I need it, cause I just install ubuntu 13.04

---

### Post by rburkartjo on 2013-09-09
are you trying to open a terminal and run ubuntu-tweak? i get the same errors you get if i try to do this. and what version are you running i am using 0.8.4 and it is working fine for me. you could remove and then reinstall and see what happens

---

### Post by sedoy on 2013-09-09
ubuntu-tweak --version
ubuntu-tweak 0.8.5

were I can find 0,8,4
and I have gnome 3,8 with ubuntu
and I heard that 3,8 not compotible with 3,8 

isnt it?

---

### Post by Frogs Hair on 2013-09-09
[https://launchpad.net/ubuntu-tweak/+download](https://launchpad.net/ubuntu-tweak/+download)

---

### Post by Jonathan Precise on 2013-09-09
> **sedoy said:**
> ubuntu-tweak --version
ubuntu-tweak 0.8.5

were I can find 0,8,4
and I have gnome 3,8 with ubuntu
and I heard that 3,8 not compotible with 3,8 

isnt it?

Please remove the gnome 3.8 ppa, as this breaks ubuntu-tweak. Stick to gnome 3.6 from the ubuntu repositories.

---

### Post by sedoy on 2013-09-10
> Stick to gnome 6 from the ubuntu repositories.

what does it means?

> [https://launchpad.net/ubuntu-tweak/+download](https://launchpad.net/ubuntu-tweak/+download)

I tried install ALL packages from here and NO ONE is worked

---

### Post by Jonathan Precise on 2013-09-10
> **sedoy said:**
> what does it means?

It means that you should install ppa-purge. Remove the Gnome 3 PPA:

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3
```

If you have ubuntu 13.10, then ubuntu-tweak might not work :(.

Then run:

```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update && sudo apt-get install ubuntu-tweak && ubuntu-tweak
```

That should solve the gnome 3.8 -> 3.6 issue, install ubuntu-tweak, and run ubuntu-tweak.:)

Any errors returned :(, post them here with CODE tags:

(CODE) -404 Error- (/CODE)

Change parenthesis to brackets:

```
 -404 Error- 
```

---

### Post by sedoy on 2013-09-10
Jonathan Precise, many thanks! !
It works, after your steps
But, I cant activate Wobbly windows on it cause In section desktop I have only this parameters [http://screencloud.net/v/wkEz](http://screencloud.net/v/wkEz)

HOW?

---

### Post by Jonathan Precise on 2013-09-10
> **sedoy said:**
> Jonathan Precise, many thanks! !
It works, after your steps
But, I cant activate Wobbly windows on it cause In section desktop I have only this parameters [http://screencloud.net/v/wkEz](http://screencloud.net/v/wkEz)

HOW?

Ubuntu tweak will not activate wobbly windows. For that, you need another program.

Please install:

```
sudo apt-get install compizconfig-settings-manager compiz-plugins-all
```

Then run:

```
ccsm
```

Go to wobbly windows. Enable it.

---

### Post by sedoy on 2013-09-10
no man.. I activated it in ccsm but it doesnt work

---

### Post by Frogs Hair on 2013-09-10
You asked about an older version of Ubuntu Tweak not available from the PPA , but I'm glad you found a working compatible version. Wobbly windows works out of the box here . What graphics card and driver are you using ?

```
lspci
```

---

### Post by sedoy on 2013-09-11
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710/M92 [Mobility Radeon HD 4530/4570/545v]
any more?

and also I have other trouble.. task Manager is not working and I can see icons of apps
I need it. how can I fix it

---

