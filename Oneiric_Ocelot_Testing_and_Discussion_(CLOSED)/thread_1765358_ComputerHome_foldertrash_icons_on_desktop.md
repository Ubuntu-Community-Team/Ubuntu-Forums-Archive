---
title: "Computer/Home folder/trash icons on desktop"
date: 2011-05-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-05-23
In my OO/Unity install since recent updates the above icons are shown on my desktop.
To get rid of them it used to be necessary to open gconf editor and navigate to Apps > Nautilus > Desktop tand then uncheck the items there.
Sadly Apps > Nautilus > Desktop isn't there any more :confused:
How do I delete them now please? Are they hiding somewhere else?
Thanks.

---

### Post by dino99 on 2011-05-23
maybe dconf instead of gconf

---

### Post by Quackers on 2011-05-23
That's it :-)  Thanks dino99
I had dconf installed and dconf-settings-backend but not dconf-tools.
It's in dconf-editor > org > gnome > nautilus > desktop

Happy again :-)

---

### Post by NormanFLinux on 2011-05-23
Why do people insist on doing it the hard way? You can remove it easily through the Ubuntu Tweak GUI!

---

### Post by lucazade on 2011-05-23
> **NormanFLinux said:**
> Why do people insist on doing it the hard way? You can remove it easily through the Ubuntu Tweak GUI!

Using gconf/dconf-editor or gconftool/gsettings from command line is not that hard.
Ubuntu Tweak instead looks like a toy coming from Windows that I'll never install in my Linux box ;)

---

### Post by dino99 on 2011-05-23
> **NormanFLinux said:**
> Why do people insist on doing it the hard way? You can remove it easily through the Ubuntu Tweak GUI!

of course you can do it, but the coming changes are:

gconf replaced by dconf
gtk2 replaced by gtk3

so gtweakui has to move on and is too buggy

and we dont like the easy way :) :) :) :)

---

### Post by Quackers on 2011-05-23
Indeed! :-)
If you do it by the book you don't get any nasty surprises!

---

### Post by MacUntu on 2011-05-23
> **lucazade said:**
> Ubuntu Tweak instead looks like a toy coming from Windows that I'll never install in my Linux box ;)
This. :)

---

### Post by lucazade on 2011-05-23
> **MacUntu said:**
> This. :)

:) I didn't want to be rude.. max respect for the author!
I prefer to use *-editor or command line tools because settings can be easily exported or included in scripts, allow to learn something of gnome internals and are usually in sync with software options.

I don't get also why ubuntu-tweak includes ppa managing and a software center, we already have proper tools.. if these are broken or difficult to use, maybe it is better to try to fix them instead of adding other layers.

---

### Post by NormanFLinux on 2011-05-23
Most of the settings are hidden or not well known to Ubuntu users and Ubuntu Tweak puts them in one place so its easier to customize Ubuntu.

---

### Post by coffeecat on 2011-05-23
> **NormanFLinux said:**
> Most of the settings are hidden or not well known to Ubuntu users and Ubuntu Tweak puts them in one place so its easier to customize Ubuntu.

Er... This is the testing forum. Oneiric is not even in alpha yet and you want to make things easy? :wink:

Seriously though, this is the testing forum. Installing software that is not only not Ubuntu supported, but not even in the Universe repository adds another layer of things to go wrong with the possible generation of false bug reports. We need to concentrate on testing the "official" stuff in order to find bugs and help the development process. 3rd party projects, however useful they are in a released version, simply muddy the water.

Imho! :)

---

