---
title: "GTK+ devel in ubuntu"
date: 2009-03-20
forum: Programming Talk
---

### Post by cthug on 2009-03-20
How do i install GTK+ devel for ubuntu, I have an internet connection, so i can use apt-get. By the way i use Anjuta and code::blocks, anything special i need for those?

-Thanks

---

### Post by cabalas on 2009-03-20
this command will install the Gtk development files

```
apt-get install libgtk2.0-dev
```

Anjuta should do most of the configuring for your projects though you may have to install automake and related programs.

---

### Post by cthug on 2009-03-20
Hey thanks cabalas,

I tried and this is the output?

root@zac-laptop:/home/zac# apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libcairo2-dev but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libx11-dev (>= 2:1.0.0-6) but it is not going to be installed
                 Depends: libxcomposite-dev but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxdamage-dev but it is not going to be installed
                 Depends: libxext-dev but it is not going to be installed
                 Depends: libxfixes-dev but it is not going to be installed
                 Depends: libxi-dev but it is not going to be installed
                 Depends: libxinerama-dev but it is not going to be installed
                 Depends: libxrandr-dev but it is not going to be installed
E: Broken packages

Any suggestions ;)

---

### Post by cthug on 2009-03-20
Maybee i should try something else like wxwidgets, see i come from a windows background, and know the win32 api, and just want the equivelent for my ubuntu laptop. all i want to use it for is simple GUI's and gamedev.

So u got any suggestions for GUI toolkits?

---

### Post by cthug on 2009-03-20
Ew, wxwidgets is for C++, might have a look at winelib.

Thanks for your help. ;)

---

### Post by Can+~ on 2009-03-20
> **cthug said:**
> I have an internet connection, so i can use apt-get.

Yeah, I pictured that, since you posted in.. well.. an online forum.

Btw, you can install the glade plugin for Anjuta and have Glade (GTK+ tool) in ajunta:

[http://anjuta.sourceforge.net/screenshots/anjuta-2.1.2-9.png](http://anjuta.sourceforge.net/screenshots/anjuta-2.1.2-9.png)

---

### Post by mmix on 2009-03-21
```
sudo aptitude
```

> **cthug said:**
> Hey thanks cabalas,

I tried and this is the output?

root@zac-laptop:/home/zac# apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libcairo2-dev but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libx11-dev (>= 2:1.0.0-6) but it is not going to be installed
                 Depends: libxcomposite-dev but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxdamage-dev but it is not going to be installed
                 Depends: libxext-dev but it is not going to be installed
                 Depends: libxfixes-dev but it is not going to be installed
                 Depends: libxi-dev but it is not going to be installed
                 Depends: libxinerama-dev but it is not going to be installed
                 Depends: libxrandr-dev but it is not going to be installed
E: Broken packages

Any suggestions ;)

---

### Post by geirha on 2009-03-22
Are you using Jaunty?
```
lsb_release -a
```

---

