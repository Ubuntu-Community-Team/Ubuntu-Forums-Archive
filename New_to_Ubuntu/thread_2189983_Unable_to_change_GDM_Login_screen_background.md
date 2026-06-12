---
title: "Unable to change GDM Login screen background"
date: 2013-11-25
forum: New to Ubuntu
---

### Post by sankar.kaza on 2013-11-25
I am new to linux and I have recently installed Ubuntu Gnome 13.10 on my laptop. I don't like the default dark gray background of the Gnome Login Screen and want to change it.

I have googled for this and found a tool called GDM3Setup. I have installed the tool and tried to change the background, but it didn't work.

Can you please help me in changing the login screen background?

---

### Post by fantab on 2013-11-25
GDM Background Grey is loacated in /usr/share/gnome-shell/theme/noise-texture.png
To change this you have to copy a background of your choice in the above folder- Rename noise-texture.png as noise-texture.png.bak and rename the background image you've copied as noise-texture.png.
You have to do this as root. (Every update to gnome-shell will replace your noise-texture.png with the original, so you have keep repeating the above after every gnome-shell upgrade)

To do this from GUI as root:
```
sudo nautilus /usr/share/gnome-shell/theme
```
Find the file and do the necessary.

Then restart gnome-shell- Alt+F2, type 'r' and hit enter/return key.

---

### Post by sankar.kaza on 2013-11-26
Thank you. That worked perfectly. :D

---

### Post by PopsTheSailor on 2014-01-11
To keep it from changing back during a gnome-shell update, could you name your new background file noise-texture.png?

---

### Post by SurfaceUnits on 2014-01-19
The real real
copy the image you want to use into the /usr/share/gnome-shell/theme folder
sudo gedit /usr/share/gnome-shell/theme/gnome-shell.css

Search for the following section

#lockDialogGroup {
background: #2e3436 url(noise-texture.png);
background-repeat: no-repeat;

change the name of the image to your image
set background to repeat or no-repeat

Save the file
logout and your new background is there

---

### Post by miceagol on 2014-11-03
> **SurfaceUnits said:**
> The real real
copy the image you want to use into the /usr/share/gnome-shell/theme folder
sudo gedit /usr/share/gnome-shell/theme/gnome-shell.css

Search for the following section

#lockDialogGroup {
background: #2e3436 url(noise-texture.png);
background-repeat: no-repeat;

change the name of the image to your image
set background to repeat or no-repeat

Save the file
logout and your new background is there

Thanks, SurfaceUnits, for a very elegant solution. Worked perfectly!

---

