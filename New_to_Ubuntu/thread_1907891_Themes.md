---
title: "Themes"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by Elitenoname on 2012-01-12
How do i go about installing new themes in gnome fallback and unity? doesn't seem as easy as in 10.10, also i am on ubuntu 11.10 if that helps.

---

### Post by Perfect Storm on 2012-01-12
Install gnome tweak tool.

```
sudo apt-get install gnome-tweak-tool
```

To edit/change Unity install 
ccsm, scroll down to the Desktop category, and click on the Ubuntu Unity plugin.


Or try MyUnity;
[http://www.addictivetips.com/ubuntu-linux-tips/myunity-comprehensive-unity-tweak-for-ubuntu-11-04-and-11-10/](http://www.addictivetips.com/ubuntu-linux-tips/myunity-comprehensive-unity-tweak-for-ubuntu-11-04-and-11-10/)

---

### Post by Frogs Hair on 2012-01-12
(Installing Downloaded Themes / Icons)

Use GTK3 only themes  for Ubuntu 11.10 .[http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=3cfb6106ce0feb9db454be2b18ba8f3f](http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=3cfb6106ce0feb9db454be2b18ba8f3f)

Download and fully extract all the packages . 

Install the Gnome Tweak Tool / Advanced Settings from the software center for making theme selections.

(Single User) Create a .themes and .icons folder in home / hidden folders . Use Ctrl + H to open the hidden folder option in Nautilus .

(All Users) Use gksudo nautilus in the terminal to open the file system and navigate to / usr / share / themes or icons .

Place the folders in either location making theme selections using Advanced Settings . Logout - in may be required .

---

