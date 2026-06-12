---
title: "login screen"
date: 2011-07-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by brazov on 2011-07-24
Hi.

I have installed Oneiric since a week and have a problem with the login screen. It seems somewhat corrupted, there are two missing images in the top right corner (maybe shutdown options and keyboard) and the graphic is minimal. This would be not so bad, but when I disconnect the user I get just the wallpaper. I am not able to login again. The only thing I can do is enter a terminal with Ctrl-Alt-F1 and shut down. So my questions are:

1) Is it normal at this stage such a login screen?

And

2) How can I restart a Unity session from a terminal? 

Thank you

---

### Post by Harry33 on 2011-07-24
> **brazov said:**
> Hi.

I have installed Oneiric since a week and have a problem with the login screen. It seems somewhat corrupted, there are two missing images in the top right corner (maybe shutdown options and keyboard) and the graphic is minimal. This would be not so bad, but when I disconnect the user I get just the wallpaper. I am not able to login again. The only thing I can do is enter a terminal with Ctrl-Alt-F1 and shut down. So my questions are:

1) Is it normal at this stage such a login screen?

And

2) How can I restart a Unity session from a terminal? 

Thank you

The two missing icons on top right corner will show,
if you install the package gnome-icon-theme-symbolic.
Are you using LightDM or GDM as a display manager?

---

### Post by brazov on 2011-07-24
> **Harry33 said:**
> The two missing icons on top right corner will show,
if you install the package gnome-icon-theme-symbolic.
Are you using LightDM or GDM as a display manager?

Attempting to install the package turns out in a message saying it is already installed.

I am using LightDM and suppose it is the default one. As I read your message I tried
```
sudo restart lightdm
```
and succeeded in having the login screen again.:)

---

### Post by brazov on 2011-07-24
> **brazov said:**
> Hi.
It seems somewhat corrupted, there are two missing images in the top right corner (maybe shutdown options and keyboard) and the graphic is minimal. This would be not so bad, but when I disconnect the user I get just the wallpaper. I am not able to login again.

Do you think I should report a bug for this?

---

### Post by nrayever on 2011-07-26
Hi: I kind of have the same error. I just installed Oneiric a few hour ago. When i click on my account i can't access, i can't even put my password. Is there any temporary work around for this issue or when is going to be solved. Is really annoying not being able to enter Ubuntu with GUI.
Regards, nrayever

---

### Post by meborc on 2011-07-26
> **nrayever said:**
> Hi: I kind of have the same error. I just installed Oneiric a few hour ago. When i click on my account i can't access, i can't even put my password. Is there any temporary work around for this issue or when is going to be solved. Is really annoying not being able to enter Ubuntu with GUI.
Regards, nrayever

it has been discussed in many threads already ;)

first time after install you have to click on the OTHER user, type in your own user name and password, next time you are able to click on your user name in the menu and enter password

---

### Post by nrayever on 2011-07-26
> **meborc said:**
> it has been discussed in many threads already ;)

first time after install you have to click on the OTHER user, type in your own user name and password, next time you are able to click on your user name in the menu and enter password

Thanks meborc i didn't knew that. I was on lynx and i am not used to it. I solved the issue installing gdm. But now that you point me to the correct method i will give it a shoot.

Regards, nrayever

---

