---
title: "Adobe Reader as default (acroread as default)"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by benedict-m-holland on 2014-04-29
So another ubuntu and another time wasted trying to figure out how to get it to use acroread as the default PDF viewer. How about we don't get into the discussion about why acroread sucks or why other readers are better because this is the only reader which is widespread and useful with beamer presentations. Yes. No other viewer will display beamer presentations correctly. I don't know why. It doesn't matter. acroread is it. 

So first thing you need to do is get acroread. I like to go to here: [https://get.adobe.com/reader/otherversions/](https://get.adobe.com/reader/otherversions/) and download the .deb. 

Of course, it is a only a 32bit application and I run 64. That means you need a few libraries to get it working. I found this link to be useful but the two libraries are 

sudo apt-get install libxml2:i386
sudo apt-get install libxml2:i386

and just because you will get a ton of errors like 
(acroread:25529): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

you need to install

sudo apt-get install gtk2-engines-murrine

You will still get these errors:
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"

but thankfully it doesn't actually crash the application. What fun. 

But wait a sec, it still isn't the default and ubuntu changes how to set the default with every passing revision of the OS because why wouldn't you follow in the footsteps of apple by changing how you manage your server every single time you want to upgrade the OS? Yes, I am bitter because I wasted about an hour trying to figure out something buried in the archives. 

[http://ubuntuforums.org/showthread.php?t=1500211&page=2](http://ubuntuforums.org/showthread.php?t=1500211&page=2)

last comment. Apparently the .desktop file needs %f appended to it so that nautilus will see that it can be used as a default. I am sure it took that poster hours to figure that one out too. So you need to edit:

sudo emacs /usr/share/applications/AdobeReader.desktop

and turn 
Exec=acroread

into Exec=acroread %f

Then it will show up as you would normally set the defaults for anything. I would strongly discourage editing the /etc/gnome/defaults.list file but if you do, the previous link worked fine. I cannot wait until the developers change the %f flag to something else too, perhaps something less obscure like another line in the .desktop that says possibledefault=true or something. 

[B]Breakdown of the steps:
[/B]
go here to download the .deb  [https://get.adobe.com/reader/otherversions/](https://get.adobe.com/reader/otherversions/)

sudo apt-get install libxml2:i386
sudo apt-get install libxml2:i386
sudo apt-get install gtk2-engines-murrine

edit /usr/share/applications/AdobeReader.desktop to have Exec=acroread %f

---

