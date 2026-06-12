---
title: "Need help installing a theme!"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by SAIYANPRINCE on 2012-02-12
Hi, I recently found this theme [http://gnome-look.org/content/show.php/Greyness-Orange+GTK+Theme?content=148498](http://gnome-look.org/content/show.php/Greyness-Orange+GTK+Theme?content=148498)

and I really want to install it. When I download it, its a zip file which i extract and it becomes a folder and not a .gz file. I know how to install gz files but when its a folder I have absolutely no clue how to install it. 

How can I install this theme??

If it matters then I'm running ubuntu 10.04, using gnome

---

### Post by SAIYANPRINCE on 2012-02-13
Hi, I recently found this theme [http://gnome-look.org/content/show.p...content=148498](http://gnome-look.org/content/show.p...content=148498)

and I really want to install it. When I download it, its a zip file which i extract and it becomes a folder and not a .gz file. I know how to install gz files but when its a folder I have absolutely no clue how to install it. 

How can I install this theme??

If it matters then I'm running ubuntu 10.04, using gnome

---

### Post by SAIYANPRINCE on 2012-02-13
pleeeasseeeee

---

### Post by HiImTye on 2012-02-13
move it to ~/.themes

---

### Post by sadaruwan12 on 2012-02-13
just rename the extention .zip to .gz and try it. And let us know what happened.

---

### Post by raja.genupula on 2012-02-13
> **SAIYANPRINCE said:**
> Hi, I recently found this theme [http://gnome-look.org/content/show.p...content=148498](http://gnome-look.org/content/show.p...content=148498)

and I really want to install it. When I download it, its a zip file which i extract and it becomes a folder and not a .gz file. I know how to install gz files but when its a folder I have absolutely no clue how to install it. 

How can I install this theme??

If it matters then I'm running ubuntu 10.04, using gnome

what you got while you drag that downloaded file into the appearance window  ?

---

### Post by SAIYANPRINCE on 2012-02-13
I did that and it doesnt work

---

### Post by HiImTye on 2012-02-13
did you move the .zip or the folder to ~/.themes

---

### Post by SAIYANPRINCE on 2012-02-13
Nope,that doesnt work

---

### Post by SAIYANPRINCE on 2012-02-13
I tried both, I even tried renaming the zip to gz and still nohting

---

### Post by lisati on 2012-02-13
Threads merged, creating duplicates dilutes the community's efforts.

---

### Post by HiImTye on 2012-02-13
then theres likely an issue with the layout of the theme
try moving the folder to /usr/share/themes as the download page suggests

---

### Post by SAIYANPRINCE on 2012-02-13
Done that still nothing. BUT I heard there was a command that you need to do after you put it there, do you know what it is? I will try

---

### Post by Frogs Hair on 2012-02-13
The drag and drop method no longer works with Gnome 3 . See below if you are using 11.10 . 

(install Downloaded Themes or icons in Ubuntu 11.10)

Download and fully extract the theme packages and hold the folders on the desktop until needed . 

Install the Gnome Tweak Tool / Advanced Settings for making theme selections from the software center .  

(Single User) Create a .themes and .icons folder in home / hidden folders . Use Crtl + H to open hidden folders in Nautilus.

(All Users) Use gksudo nautilus in the terminal to open the Nautilus as root and navigate to > File System / usr / share / themes or icons .

Place the folders in either Loation . Use Advanced Settings to make theme selections . Logout - in may be required before theme are visible in Advanced Settings .

---

### Post by HiImTye on 2012-02-13
> **SAIYANPRINCE said:**
> If it matters then I'm running ubuntu 10.04, using gnome
I'm unsure of a command that needs to be run, maybe logging out and back in or restarting

---

### Post by Dennis N on 2012-02-13
Since you are trying to install this on Ubuntu 10.04, the dependencies are probably not satisfied. The theme it is based on requires GTK2 -> Murrine GTK2 engine 0.98.1.1 or later, while Lucid has only 0.90.

---

