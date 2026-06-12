---
title: "[SOLVED] installing themes"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Arthur Millar on 2008-10-20
I found a theme i liked on gnome look
[http://www.gnome-look.org/](http://www.gnome-look.org/)

i downloaded a file "GrayDark-Ice.emerald"
how do I enable this file 
or where do I put it

---

### Post by aeiah on 2008-10-20
emerald is a somewhat outdated program that was used early on with compiz and beryl to draw the window borders. you will need to install emerald and add the theme that way. im probably the only person in the world who still uses emerald though, as there are nicer methods for adding window border themes for compiz now. if there is a metacity or gtk version of the theme, you're best using that. if not, download and install emerald first. you need to be running compiz as well.

---

### Post by Arthur Millar on 2008-10-20
whats the best way to install/find themes

---

### Post by bcom on 2008-10-20
I'm not sure if by themes you mean the background Wallpaper.  If it is, here is how to change it:

Right-click on the desktop and click Change Desktop Background.  Click the Add Wallpaper button and go to the place where you downloaded the image, select it and click OK.

Try [http://art.gnome.org](http://art.gnome.org) for other wallpaper packages.

---

### Post by tjwoosta on 2008-10-20
a .emerald is an emerald theme


you will need to have compiz fusion working 

then install the emerald theme manager

after installing emerald there will be an entry in the preferences menu that says Emerald Theme Manager


go into the emerald theme manager and choose import (then find your .emerald)


now to make the emerald theme start to work, you will need to do this

press alt-f2 (**do not** use a terminal here) and type

```
emerald --replace
```

if everything goes right your theme should instantly switch on after the command


now if you want emerald to start every time you log in you would need to add the command to the sessions

go to System-Preferences-Sessions  then click "add" and put emerald --replace for the command  (put whatever you want for the name and descroption)

now every time you login the command will be automaticaly run


> emerald is a somewhat outdated program that was used early on with compiz and beryl to draw the window borders. you will need to install emerald and add the theme that way. im probably the only person in the world who still uses emerald though, as there are nicer methods for adding window border themes for compiz now. if there is a metacity or gtk version of the theme, you're best using that. if not, download and install emerald first. you need to be running compiz as well.

emerald has been around for a while, but the themes are definatly far better looking then plain old gtk or metacity


i use it and so do alot of people

(your supposed to use the emerald theme in conjunction with the gtk themes)

emerald only decorates the window boarders and title bars

gtk theme decorates the actual window itself

---

### Post by perlluver on 2008-10-20
To install themes, you download the tar.gz file, then drag it into System>Preferences>Appearance, and it will show up immediately.  Also you want to download Gtk2.x themes.

---

### Post by fooman on 2008-10-20
you could also install the "compiz-fusion icon" which will give you easy access to turning emerald on and off as well as a host of other compiz-fusion options.  its in the repos:

```
sudo apt-get install fusion-icon
```

or search for "fusion-icon" in synaptic.

---

### Post by Arthur Millar on 2008-10-20
im beginning to understand 
this is only a partial mod 
im looking for somthing really nice 
it doesnt even have to be this emerald theme which looks ok 
[the part i got any way]
this is what i want 
[http://praji.files.wordpress.com/2008/06/ubuntu_theme_mockup___dark_by_bradwjensen.jpg](http://praji.files.wordpress.com/2008/06/ubuntu_theme_mockup___dark_by_bradwjensen.jpg) 
or similar

---

### Post by Arthur Millar on 2008-10-20
cool i got a nice combination of themexs now how do i change the panels
to the one in the link above

---

### Post by perlluver on 2008-10-20
> **Arthur Millar said:**
> cool i got a nice combination of themexs now how do i change the panels
to the one in the link above

You mean on the bottom, that is called AWN, you can find it in Add/Remove, Avant Window Navigator.

---

### Post by fooman on 2008-10-20
that is not a panel...it is a dock.  not sure which one,  either awn or cairo i assume.  here is some info:

[http://www.blog.hyperend.info/avant-window-navigator-cairo-dock-and-kiba-dock/](http://www.blog.hyperend.info/avant-window-navigator-cairo-dock-and-kiba-dock/)

---

### Post by Arthur Millar on 2008-10-20
awn manager not working 
installed but no activity after run

---

### Post by perlluver on 2008-10-20
Do you have compiz enabled?  In order for AWN to work, you have to have Compiz.

---

### Post by Arthur Millar on 2008-10-20
> **perlluver said:**
> Do you have compiz enabled?  In order for AWN to work, you have to have Compiz.

Im pretty sure i have compiz 
as i have installed it from synaptic
awn just doesnt launch

---

### Post by fooman on 2008-10-20
try starting awn in a terminal.  that way you can see any error messages that pop up.  type or copy paste the following in a terminal:

```
avant-window-navigator
```

post back with the output.

---

