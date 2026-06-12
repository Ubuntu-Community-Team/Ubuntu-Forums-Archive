---
title: "Can't install GTK+"
date: 2011-01-22
forum: Programming Talk
---

### Post by ctult on 2011-01-22
Hi!  I tried to install gnome's core libraries, but I got an error:
```

$ sudo apt-get install gnome-core-devel build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-core-devel : Depends: libgtk2.0-dev (>= 2.18) but it is not going to be installed
                    Depends: libbonoboui2-dev (>= 2.24) but it is not going to be installed
                    Depends: libglade2-dev (>= 1:2.6.4) but it is not going to be installed
                    Depends: libgnomecanvas2-dev (>= 2.26) but it is not going to be installed
                    Depends: libgnomeui-dev (>= 2.24) but it is not going to be installed
                    Depends: libpango1.0-dev (>= 1.26) but it is not going to be installed
                    Depends: libgnome-desktop-dev (>= 2.28) but it is not going to be installed
                    Depends: libpanel-applet2-dev (>= 2.28) but it is not going to be installed
                    Depends: python-gnome2-desktop-dev (>= 2.28) but it is not going to be installed
                    Depends: libgtkhtml3.14-dev (>= 3.28) but it is not going to be installed
                    Depends: libgtksourceview2.0-dev (>= 2.8) but it is not going to be installed
                    Depends: libgail-gnome-dev (>= 1.20.1) but it is not going to be installed
                    Depends: libgnomekbd-dev (>= 2.28) but it is not going to be installed
                    Depends: libgweather-dev (>= 2.28) but it is not going to be installed
                    Depends: librsvg2-dev (>= 2.26) but it is not going to be installed
                    Depends: libwnck-dev (>= 2.28) but it is not going to be installed
                    Depends: libnautilus-extension-dev (>= 2.28) but it is not going to be installed
                    Depends: libtotem-plparser-dev (>= 2.28) but it is not going to be installed
                    Depends: libvte-dev (>= 0.22) but it is not going to be installed
                    Depends: python-gnome2-dev (>= 2.28) but it is not going to be installed
                    Depends: python-gtk2-dev (>= 2.16) but it is not going to be installed
E: Broken packages

```

Can someone help me?

Thanks in advance,
CTuLT

---

### Post by lavinog on 2011-02-01
Have you tried running apt-get update first?

---

### Post by lykeion on 2011-02-01
I think it's easiest to fix broken packages in Synaptic:
[LIST]
[*]Start System > Administration > Synaptic Package Manager
[*]Click Reload
[*]Edit > Fix broken packages
[/LIST]

---

### Post by ashickur.noor on 2011-02-01
run ```
sudo apt-get install -f
```

---

