---
title: "Stuck installing gnome-power-manager-2.23.6"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by one_iota on 2008-08-09
I downloaded gnome-power-manager-2.23.6 and am trying to install it manually in a terminal.

I have entered the ./configure command and been working my way through all the missing packages that I was prompted to install.

I am stuck on one package at the moment though...
```
No package 'polkit-gnome' found
```

I don't have anything called 'polkit-gnome' in Synaptic. Is it part of another package or can it be installed from somewhere else?

(When I googled for the phrase I found a result that suggested polkit-gnome was aka 'pkgconfig'. In Synaptic the only thing I had similar was 'libextutils-pkgconfig-perl'. I installed that but am still prompted for polkit-gnome.)

Many thanks if someone can help.:)

---

### Post by jordanmthomas on 2008-08-09
Have you tried
```
sudo apt-get build-dep gnome-powermanager
```

This will download and install what is required to build gnome-powermanager 2.22.1-ubuntu4

While it's possible that the dependencies have changed from 2.22 to 2.23, it's worth a shot.  Sorry I can't be of much more help, but I use Arch

**edit**
fixed, it's build-dep,  not build-deps

---

### Post by one_iota on 2008-08-09
Thank you for your reply.:)

sudo apt-get build-dep gnome-powermanager gives me the following...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for gnome-powermanager
```

I tried:
 
sudo aptitude update
sudo aptitude install build-essential

just on the off chance it would help, but still stuck.

I really don't have a clue what I'm doing!:lolflag:

---

### Post by jordanmthomas on 2008-08-09
oops, forgot a - 

The package is named gnome-power-manager

---

### Post by gunnar123 on 2008-09-08
How do I clean up my system after I have done the build dep and is finally finished buiding?  There should be lots of data laying around afterwards that I would benefit from removing.

---

