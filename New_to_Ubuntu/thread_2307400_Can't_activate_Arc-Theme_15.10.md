---
title: "Can't activate Arc-Theme 15.10"
date: 2015-12-24
forum: New to Ubuntu
---

### Post by notone2 on 2015-12-24
Hi guys i just started using Ubuntu a week ago so maybe I'm just missing something obvious 

I checked and i have all requirements:

[LIST]
[*]Gnome/GTK 3.14, 3.16 or 3.18 
[*]The gnome-themes-standard package 
[*]The murrine engine. This has different names depending on your distro.
[LIST]
[*]gtk2-engines-murrine (Debian, Ubuntu, elementary OS) 
[/LIST]
  
[/LIST]

I added the repository and installed it
```
sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10/ /' >> /etc/apt/sources.list.d/arc-theme.list"
sudo apt-get update
sudo apt-get install arc-theme
```

I added the key:
```
wget http://download.opensuse.org/repositories/home:Horst3180/xUbuntu_15.10/Release.key
sudo apt-key add - < Release.key  
```

I have arc theme in filesys:
[IMG]http://img.photobucket.com/albums/v346/ltldzmaj/Screenshot%20from%202015-12-24%2020-48-21_zpsoomjkkku.png[/IMG]


Still when I click "Appearance" I don't see Arc-Theme, I also installed Unity and Gnome tweak tools, just to be sure but I can't see it there either.


If you need any more informations please let me know.

---

### Post by Frogs Hair on 2015-12-24
Try installing the unity tweak tool and enable from there.

---

### Post by notone2 on 2015-12-24
> **notone2 said:**
> I also installed Unity and Gnome tweak tools, just to be sure but I can't see it there either.

hi

I did installed unity tweak tool and gnome tweak tool but I don't see it there either.

---

### Post by Frogs Hair on 2015-12-24
Missed that .;)

Check computer usr/share/themes and see if it's in there, if so you may have to change permissions to enable the theme. I don't remember having to do that when I installed.

Go to the linked page an see the section that reads ***grab binary packages directly ***and download the 15.10 .deb package which will install from the software center. If the theme is already installed follow the remove previous version instructions posted below the link first.   

[http://software.opensuse.org/download.html?project=home%3AHorst3180&package=arc-theme](http://software.opensuse.org/download.html?project=home%3AHorst3180&package=arc-theme)

```
sudo rm -rf /usr/share/themes/{Arc,Arc-Darker,Arc-Dark}
rm -rf ~/.local/share/themes/{Arc,Arc-Darker,Arc-Dark}
rm -rf ~/.themes/{Arc,Arc-Darker,Arc-Dark}
```

---

### Post by notone2 on 2015-12-24
hi thanks i will try that first

i checked the share/theme folder seems like there is more themes then i see in tweak tool
[IMG]http://img.photobucket.com/albums/v346/ltldzmaj/themes_zpsp80wnoal.png[/IMG]
Tweak tool:
[IMG]http://img.photobucket.com/albums/v346/ltldzmaj/gtt_zpsep4lj65o.png[/IMG]




Should I copy the whole folder from Home and delete it or just copy some parts?
[IMG]http://img.photobucket.com/albums/v346/ltldzmaj/arc_zpslpmuu7uz.png[/IMG]

---

### Post by notone2 on 2015-12-24
hi i downloaded the package and opened it and there was just reinstall option, then i tried deleting it via terminal and nothing happened, then opened package again after i deleted it, and there was "reinstall" again so it didn't deleted it, but I tried reinstalling it and it works!!! :)))) thank you! i didn't tried it still :)))) not sure what happened it seems like it was installed but in the wrong place?

---

### Post by Frogs Hair on 2015-12-24
I had forgotten that the .deb was available until I visited the page again. Some themes in usr/share themes are gtk 2 and won't display in newer versions of Ubuntu. Appearance preferences won't display 3rd party themes and that's where the unity tweak tool comes in handy.

---

### Post by notone2 on 2015-12-24
thank you! :)

---

