---
title: "HOWTO Install GTK Themes, Engines, Customize the"
date: 2007-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by edmondt on 2007-04-18
I find it confusing sometime when trying to install themes, so a easy way to do it, by using Gnome-Art:

[IMG]http://www.guia-ubuntu.org/images/b/bf/Gnome_Art_Aplications.png[/IMG]

To install, just enter:

```
sudo apt-get install gnome-art
```


You would need to get the theme engines:

```
sudo apt-get install gtk2-engines-thingeramik gtk2-engines-mist gtk2-engines-clearlooks gtk2-engines-pixbuf gtk2-engines-metal gtk2-engines-geramik gtk-engines-geramik-data gtk2-engines-smooth gtk2-engines-qtpixmap gtk2-engines-magicchicken gtk2-engines-cleanice gtk2-engines-thinice gtk2-engines-crux gtk2-engines-industrial gtk2-engines-highcontrast gtk2-engines-spherecrystal gtk2-engines-wonderland gtk2-engines-lighthouseblue gtk-engines-thingeramik-data
```

Now getting themes is easier :)

---

### Post by boob11 on 2008-03-27
Thnx

---

### Post by nebu on 2008-03-28
i think there is some problems with the second command.....

i get.....

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gtk2-engines-mist is a virtual package provided by:
  gtk2-engines 1:2.12.2-0ubuntu1
You should explicitly select one to install.
E: Package gtk2-engines-mist has no installation candidate

```

---

### Post by lajevardi on 2008-04-02
Agree with nebu. 
which source I should to add!?

---

### Post by phantom74 on 2008-04-03
so i get the same error, anyone can help please!?!?!?!?!?

---

### Post by ekow on 2008-08-04
Bumping for above errors, i'm getting it too.

---

### Post by gjoellee on 2008-08-04
I don't have any errors...don't know why this happens to you..sorry, but just to check, enable all the third party software...

however the software is pretty awesome!

---

### Post by ben2talk on 2008-08-17
wow, well I got a message that libgtk2.0-0 (= 2.12.9-3ubuntu2) amongst a whole load of other dependency problems!

Is this another abort?

---

### Post by krimzonstarr on 2008-08-18
I replaced the apt-get commands with aptitude and my installation worked fine for me. YMMV though, ubuntu noob here. :)

---

### Post by jlochhead on 2008-12-05
Spotted this thread on google.

Just so it is here... you don't really need to use the sudo apt-get install command. 

Go to System > Administration > Synaptic Package Manager

Search for gnome art then check it for installation. Then, search for gtk and just check all the packages starting with gtk2-engines. Press the apply button; and there you go. ;)

It is much easier than using apt-get if the command is not working properly.

You should be able to find gnome art under System > Preferences > Art Manager.

---

### Post by alibi89 on 2008-12-06
thanks

---

### Post by khaosgott on 2008-12-09
excellent stuff, thanks for the tip!

---

### Post by Dumbestcrayon on 2009-01-15
For those of you getting the errors try this.

```
sudo apt-get install gtk2-engines-*
```

---

### Post by pieisgood4589 on 2009-01-16
> **Dumbestcrayon said:**
> For those of you getting the errors try this.

```
sudo apt-get install gtk2-engines-*
```

Thanks, that code works great :P

---

