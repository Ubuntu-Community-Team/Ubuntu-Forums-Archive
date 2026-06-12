---
title: "Fonts"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by CrimsonV on 2008-05-25
How do i add .ttf fonts to Unbuntu so that i may use them in Open Office?  I am very new to Linux and i have very little coding/terminal experience.

---

### Post by bwhite82 on 2008-05-25
Create a directory inside of your home directory and name it: .fonts
Place any fonts you want inside of this directory.

---

### Post by kaboodle_fish on 2008-05-25
This is quite a handy guide 

[http://tombuntu.com/index.php/2008/04/17/how-to-install-fonts-in-ubuntu-804/](http://tombuntu.com/index.php/2008/04/17/how-to-install-fonts-in-ubuntu-804/)

---

### Post by sayakb on 2008-05-25
Install this:
```
sudo apt-get install msttcorefonts
```
Also, to add more, copy all fonts from a Windows box (find them at C:\Windows\Fonts). 
Then create a folder:
```
sudo mkdir  /usr/share/fonts/truetype/MyFonts
```Then open Nautilus as root:
```
gksudo nautilus
```And copy the Windows fonts to the newly created folder.

---

