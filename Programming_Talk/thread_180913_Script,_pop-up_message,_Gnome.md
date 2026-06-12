---
title: "Script, pop-up message, Gnome"
date: 2006-05-23
forum: Programming Talk
---

### Post by DrSkalpell on 2006-05-23
Hi,

If I have made a script that runs every day (cron) and I want to get a popup-message in gnome every time it runs, what do I have to program to make it so?

In other words, is there a Gnome API which I can access and find commands to do such things?

---

### Post by Kvark on 2006-05-23
zenity is a program that can display all kinds of popup dialogs. For example to display a text message do:
```
zenity --info --text "message here"
```

---

### Post by tkjacobsen on 2006-05-23
maybe you can use zenity - installed in gnome by default. see man zenity

---

### Post by DrSkalpell on 2006-05-23
That worked excellent. Thanks!

---

