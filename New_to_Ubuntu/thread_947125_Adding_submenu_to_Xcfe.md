---
title: "Adding submenu to Xcfe"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by Qtips on 2008-10-14
Hi,

I just installed Matlab and Maple 12 in my laptop running Xubuntu and i look for a way to put a launcher in the applications-->development submenu...how i can do this ?

Thanks !

---

### Post by hhhmmmhhh on 2009-05-01
I don't know how to create a submenu, but fortunately Xubuntu already has a submenu "Development".
Step1:  
create a *.desktop file in use/share/application
Ex:
cd /usr/share/applications
sudo mousepad matlab.desktop

Step2:
edit *.desktop (ex: matlab.desktop) like below

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Name=Matlab 2007b
Comment=
Categories=Development;
Exec=/home/programs/matlab/bin/matlab
Icon=/home/programs/matlab/matlab_logo.png
Terminal=true
StartupNotify=false

Step3:
Save and done.
Note: you need to change the content in "Exec=" and "Icon="

---

### Post by ihucu on 2009-06-13
how did you install it?i couldnt find tutorial to install it...
thx

---

