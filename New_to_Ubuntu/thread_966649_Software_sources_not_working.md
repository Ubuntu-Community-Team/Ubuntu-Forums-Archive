---
title: "Software sources not working"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by blakebb on 2008-11-01
So I downloaded the Beta of 8.10 before the final release and I feel that I'm feeling the pangs of this decision.  

Does anyone have any idea what might be happening with my system:

Problem-software sources won't open, so I'm unable to change the third party listings to upgrade to 8.10 final release

Thanks for your time

---

### Post by eatingganesh on 2008-11-01
no idea why it is doing that (I'm a noob too), but for an immediate fix you could try re-installing the beta on the assumption that software sources is broken somehow. I'm sure there is a way to get at software sources through terminal, but that is beyond me. Hopefully someone else will post those instructions if they possible.

Of course, if you've just done a clean install of the beta, you might consider downloading the final release iso, burning it,and starting fresh with a clean install. 

Hope this gives you some ideas!
EG

---

### Post by Martje_001 on 2008-11-01
Try
```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```
in a terminal. What's the output?

---

### Post by cosmoshell on 2008-11-01
hey try sudo nano /etc/apt/sources.list in the terminal

---

### Post by blakebb on 2008-11-01
(gksu:6863): Gtk-WARNING **: Theme directory scalable/places/22 of theme black-white_2-Vista_big has no size field


** (gksu:6863): WARNING **: Invalid borders specified for theme pixmap:
        /home/be/.themes/Mac4Lin_GTK_v0.4/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image
Traceback (most recent call last):
t/__init__.py:18: FutureWarning: apt API not stable yet
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 78, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 516, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 85, in get_sources
    "Error: could not find a distribution template")
aptsources.distro.NoDistroTemplateException
be@be-desktop:~$

---

