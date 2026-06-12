---
title: "I uninstalled GIMP and it cause ubuntu-desktop to be uninstalled and now I can not"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by legolas_w on 2008-10-11
Hi
Thank you for reading my post
during my effort for installing Gimp 2.6 i uninstalled ubunut-desktop.
Now when I try to install it using 

```

sudo apt-get install ubuntu-desktop

```

I get 

```

The following NEW packages will be installed:
  ekiga evolution evolution-common evolution-exchange evolution-plugins evolution-webcal firefox firefox-3.0
  firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support pidgin-otr ubuntu-desktop
0 upgraded, 13 newly installed, 0 to remove and 38 not upgraded.


```

what can I do in order to only install ubuntu-desktop instead of installing all of these pages?

Thanks

---

### Post by SuperSonic4 on 2008-10-11
ubuntu-desktop is a meta package, thus meaning it exists only to install it's dependencies which in this case are the ones you mention below

---

### Post by legolas_w on 2008-10-11
Thank you for reply.

So, If I restart my computer will I see my desktop again? I mean will it boot and show Gnome login page? I do not need those package that are listed there.

---

### Post by namegame on 2008-10-11
You do *need* those packages. "ubuntu-desktop" requires those packages. Otherwise it will not function properly.

That being said. You could just install the gnome desktop environment along with gdm or something else of that nature.

---

### Post by OutOfReach on 2008-10-11
Right, ubuntu-desktop is just a meta package (as SuperSonic4 stated). Those packages will be needed to install ubuntu-desktop

---

