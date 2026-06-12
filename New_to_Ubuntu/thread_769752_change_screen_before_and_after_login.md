---
title: "change screen before and after login"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Doormat on 2008-04-26
I am using blubuntu theme for ubuntu. The only thing I have not been able to change is the orange screen that shows just before and after login (NOT THE SPLASH SCREEN). What is this called and how do I change it?

---

### Post by frup on 2008-04-26
Do you mean the GDM theme?

---

### Post by dangerpl on 2008-04-26
System-->Administration-->Login Window/Local

You can find GDM themes on gnome-look

---

### Post by enigmaniac23 on 2008-04-26
The thing I think you are looking for is in 
System-->Administration-->Login Window

Go to the local tab.

Change the value for "Background Color"

this will change the color right before and after the login.

---

### Post by oni5115 on 2008-04-26
I'm not sure if this is still the same in 8.04, but this is what I had to do to fix the same problem in 7.10.

gksudo gedit /etc/gdm/PreSession/Default

Near the bottom of the file is BACKCOLOR="#XXXXXX" not sure what the actual default color is, but put in #000000, which is the hex code for black (or whatever hex color you want to use).

I really do wish that they would fix it so changing the desktop background color also changes this value in this file, or the GDM manager change this value... either way, it would be quite nice not to have to dig for this command every time install Ubuntu on a machine.

Edit: Using the login window manager does change the color of the login screen, but does NOT fix the color between login and desktop loading (at least not in 7.10), I haven't yet tested a non-orange theme in 8.04.  Hence the above work around found buried 2 pages deep in some post I have saved for viewing every time I reinstall and forget how to fix it. :lol:

Edit 2:  Yay, that issue is fixed in 8.04, Login Window, Local tab, is what you are looking for.  =)

---

### Post by Doormat on 2008-04-27
> **enigmaniac23 said:**
> The thing I think you are looking for is in 
System-->Administration-->Login Window

Go to the local tab.

Change the value for "Background Color"

this will change the color right before and after the login.

Thanks that was just what I was looking for.

---

