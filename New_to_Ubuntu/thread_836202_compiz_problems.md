---
title: "compiz problems"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by syn0ptik277 on 2008-06-21
i installed compiz fusion using the guide at [http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/](http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/) and now when i log in all windows i open got to the top left, i cant switch between programs, when i type compiz --replace into terminal i get an xgl error message and something else i did complained about not working with the window manager(unkown).

any idea what i did wrong and how to fix it?

---

### Post by Kevbert on 2008-06-21
Please try running [compiz-check]("http://forlong.blogage.de/article/pages/Compiz-Check").  This should help solve your problem.

---

### Post by tjwoosta on 2008-06-21
if compiz gives you too many troubles you can temporarily disable it by logging on in safe mode (just choose safe mode in the bottom left corner of the login screen there is a menu)

then you can just do whatever you need to do to fix things and log back on in the normal mode

---

### Post by syn0ptik277 on 2008-06-21
after trying the previously mentioned advice it works fine if after ive logged in i alt-f2 and type compiz --replace but it still refuses to work if i have it set to default or have it load on start up

---

### Post by syn0ptik277 on 2008-06-21
success. kinda. after changing the default windows placement everything works fine if i use xfwm4 as default and use compiz --replace as an autostarted app. advice on how to make compiz default would still be appreciated though

---

### Post by Forlong on 2008-06-22
In order to make Compiz your default window manager, all you have to do on Xfce is saving your session when logging out.

---

### Post by syn0ptik277 on 2008-06-22
i had to disable that to resolve the issue of loosing the taskbar at the top

---

### Post by Forlong on 2008-06-22
Is Compiz running, when you are left without window boarders?

---

### Post by syn0ptik277 on 2008-06-22
yes it is

---

### Post by Forlong on 2008-06-22
What window decorator do you use?

---

