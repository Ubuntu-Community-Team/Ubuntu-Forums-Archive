---
title: "Login issue with fresh alpha3 alternate install"
date: 2011-08-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Strike0 on 2011-08-05
Hi,
I just did three fresh install of the alpha 3 with the alternate installer. Installs went smoothly, but each time I could not login with the created default account at the login. login with the Guest works fine (with unity, gdm fails to create a session). Booting time is delightful btw. 
First time I used a english default-locale and german keymap. Second both German, third both German but with an easy "qwert" password without special chars, all to no avail. Each time I also tried to login via terminal and used the keyboard wizard at install (which did choose the correct layout). 

Edit: 
meanwhile I did a parallel install with the normal i386 image. This worked fine for unity, so I got my alpha3 running. Also I noted that the default user created is now shown in the login default screen (in my previous attempts only the guest account was named there). Hence, it seemed more of a useradd than keymap problem in my trials with the alternate installer. I confirmed that by looking into the passwd and my default user is missing there indeed. 
Any suggestions what I might have missed out on using the alternative install?

---

### Post by cariboo on 2011-08-05
If you are using lightdm, you may have to select other and enter your username and password the first time you login, after that your name should show on the login screen.

---

### Post by Strike0 on 2011-08-05
> **cariboo907 said:**
> If you are using lightdm, you may have to select other and enter your username and password the first time you login, after that your name should show on the login screen.

Thanks, but that did not solve it. As I wrote terminal login was not possible as well. The problem was that the alternate installer did apparently not create the user at all during the install. A bit strange I know, but to me it looks like a bug in the alternate install really. I managed to solve it by manually adding the user afterwards using the recovery console, but this is surely not the way the installer is meant to be..

---

