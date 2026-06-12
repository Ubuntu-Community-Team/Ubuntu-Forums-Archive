---
title: "installation directory"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by polarbear12345 on 2008-10-17
well as compared to windows which asks to give the path of
installation of software....UBUNTU does not asks so.....
it becomes very difficult to run the just installed application..
as their icon does not show up in desktop menus also....


is there any solution to this problem....????
is there any fixed dir where installation is done...

eg. i installed festlex-oald through synaptic package manager
and now i dont know how to start it...or even where is it ...


plzzzzzz help!!!!!!!!!!!!!!!!

---

### Post by nothingspecial on 2008-10-17
Normally in /usr/bin or /bin.

Try typing the apps name in the terminal so

```
festlex-oald
```

---

### Post by jerome1232 on 2008-10-17
If you want to find the full path, you can use which, or to find where all of the apps files are stored you can use locate

```
which festlex-oald
locate festlex-oald
```

Normally programs are in /usr
system wide settings are in /etc
user settings are in ~/
/opt is where one might install their own apps they've added

---

### Post by nothingspecial on 2008-10-17
The command to start it is ```
festival
```.

---

### Post by philinux on 2008-10-17
Have a look in synaptic for the app in question. Click it to highlight it. Click the installed files tab. I think you'll agree windoze does not provide this level of info.

---

