---
title: "Help!  ubuntu gnome tweak tool not finding gnome-shell files"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by merrymoll on 2011-11-07
Hi there.

Right, I have Ubuntu 11.10, and as pretty as it is, I like to tinker with the looks.  I've downloaded gnome- shell and gnome tweak tool and necessary extentions and logged onto GNOME desk top.  I've got the user shell extention up and running.  I've followed the instructions to install gnome shell themes.  My problem is that when I try to set them on gnome tweak tool, the tool can find the theme files, but can;t seem to detect their contents.  I just click on "open" and it keeps going until it gets to the file, and then it shows as empty.  Those files are full, as I've checked them in the themes file I extracted them to.

I've uninstalled and re-installed the tweak tool, but am not sure where to go from here.  It's worked fine before on 11.10 install, and I'm sure I've not done anything different this time!

Any ideas?:confused:

---

### Post by Frogs Hair on 2011-11-07
Make sure you are using GTK 3 themes that are compatible with Gnome 3.2 or the themes won't work . 

(Downloaded Themes)

Install the Gnome Tweak Tool / advanced settings for making theme selections  

(Single User) Create a .themes and .icons folder in home / hidden folders .

(All Users) Use gksudo nautilus > File System / usr / share / themes or icons .

Download , extract the packages , and place the folders in either location making theme selections using Advanced Settings . Logout - in may be required .

---

### Post by merrymoll on 2011-11-08
> **Frogs Hair said:**
> Make sure you are using GTK 3 themes that are compatible with Gnome 3.2 or the themes won't work . 

(Downloaded Themes)

Install the Gnome Tweak Tool / advanced settings for making theme selections  

(Single User) Create a .themes and .icons folder in home / hidden folders .

(All Users) Use gksudo nautilus > File System / usr / share / themes or icons .

Download , extract the packages , and place the folders in either location making theme selections using Advanced Settings . Logout - in may be required .
  


Hi there,

I've done all these already - the problem is that when I go to add the shell theme to gnome tweak tool and navigate to the .themes folder and click on the extracted theme, nothing happens!  It just open the theme file but shows no contents - and there ARE contents, but Gnome tweak tool can't seem to see them.  And these are GTK 3 themes I'm trying to install.

---

