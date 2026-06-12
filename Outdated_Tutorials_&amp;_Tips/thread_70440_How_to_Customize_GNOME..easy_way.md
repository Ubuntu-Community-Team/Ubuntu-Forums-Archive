---
title: "How to Customize GNOME..easy way"
date: 2005-09-29
forum: Outdated Tutorials &amp; Tips
---

### Post by xthaparian on 2005-09-29
Ok. for all the GEEKS who want to make their Gnome look sweet...I have written this tutorial

I am assuming that you have added the repositiries in the Synaptics Package manager. If not then refer

[http://ubuntuguide.org/](http://ubuntuguide.org/)

First thing you have to do is install the following:

Smeg

$ sudo apt-get install smeg
$ sudo killall gnome-panel

This will allow to customize the gnome menue. You can see that in the system tool tab.

This is to add and remove commands in the menue of the Gnome. Many times we install the packages in the gnome which dont show up in Gnome menue. So you can add the commands and good looking in menue with this application.

Now we want to install ICONS, SplashScreens, Borders, Loginthemes, Gnomethemes, etc etc..

we will do this:

go to

[http://www.miketech.net/gnome-art/](http://www.miketech.net/gnome-art/)

download gnome-art-0.2.tar.gz

dont do anything yet as it needs extra stuff to work

you need

Ruby
Ruby-Gnome2
ReXML

For this go to synaptic package manager and search for ruby and libart2-ruby and libart1-ruby, libgnome2-ruby, ruby, ruby1.8

Install them

then search for rexml, then select all packages displayed.
Install them

all Done..now we will proceed.

untar the gnome-art-0.2.tar.gz and cd.. to the directory where its untared.

$ sudo sh setup.sh

this will install gnome-art and gnome-splashscreen-manager

Now we are preety much done

Go to smeg menue editor in the System Tools and add new entry for gnome-art and other entry for gnome-splashscreen-manager

in the command type

gnome-art (when you are creating gnome-art entry)

gnome-splashscreen-manager (when you are creating gnome-splashscreen-manager)

Now..once this is done..Refresh your GNome panel by

$ sudo killall gnome-panel

Now check for the new entry you created for gnome-art and gnome-splashscreen-manager

Fire them up...

and then donwload whatever you want.....and there you go...

Install the stuff you want..and customize your..GNOME...

ENJOY....and LIBERATE..the world

---

### Post by aysiu on 2005-09-29
[QUOTE=xthaparian]
First thing you have to do is install the following:
Smeg
$ sudo apt-get install smeg
$ sudo killall gnome-panel
This will allow to customize the gnome menue. You can see that in the system tool tab.[/QUOTE] Don't forget that SMEG comes preinstalled with Breezy Ubuntu.

---

### Post by frodon on 2005-09-30
Sorry but what does GNOME Art  does that you cannot already do ?
Because there is already a theme manager in GNOME and a simple drag and drop install a new theme, the only interest i see is to have an interface to install new splash screen.
Is there something that you can do with GNOME Art and not with the theme manager ?
is it just a GUI ?

Thanks to enlighten me about this tool.

---

### Post by bored2k on 2005-09-30
Gnome-art:
>  install GNOME themes from art.gnome.org
 Gnome Art is a tool for downloading and installing GNOME themes
 from [http://art.gnome.org/](http://art.gnome.org/) website. It provides a nice theme list
 with options to preview, download and install them.

This you cannot do with the gnome-control-center.
Note: This package is on Breezy.

---

### Post by xthaparian on 2005-09-30
The use of getting gnome-art is to directly downlaod lots of Backgorunds, Iconssets, Splash Screens, Login Screens, GTK themes, etc etc..which is painful if you have to install every one of them individually.

Also this tutorial is for newbies as experienced users can get around and do stuff in Terminal..

So its a One good GUI interface for every goody to install, Donwload and Look..

I hope this helps..

---

### Post by frodon on 2005-09-30
Yep, I will try it this week end, usually i download and install theme myself and make my own splash screen images, but i'm curious to try this tool.
Thx for the tips and the quick reply ;)

---

### Post by arnieboy on 2005-09-30
breezy has its own splash screen manager and u can use the gnome art manager (which also comes with breezy) to automatically download, preview and install all splash screens (and also window styles, application borders and icons) on art.gnome.org. I found both apps quite nifty.

---

