---
title: "Application autostart"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by MidnightJulia on 2008-07-01
Hi! 

I've got some apps that I'd like Ubuntu to autostart when booting. Where do I define that some applications are to be started when booting? :)

/MJ

---

### Post by avtolle on 2008-07-01
System>>Preferences>>Session contains a list of applications that are started upon boot. You would edit that file to add the applications you want to start, I noting here that this may degrade startup time a bit.

---

### Post by drs305 on 2008-07-01
> **MidnightJulia said:**
> Hi! 

I've got some apps that I'd like Ubuntu to autostart when booting. Where do I define that some applications are to be started when booting? :)

/MJ

System, Preferences, Sessions, Startup Programs.

---

### Post by MidnightJulia on 2008-07-01
Wow fast answer! Thanks! That was exactly what I was looking for. 

Out of curiosity thou: if I'd ever want to change this myself (without the use of the Sessions app) what file would I need to change? 

/MJ

---

### Post by drs305 on 2008-07-01
> **MidnightJulia said:**
> Wow fast answer! Thanks! That was exactly what I was looking for. 

Out of curiosity thou: if I'd ever want to change this myself (without the use of the Sessions app) what file would I need to change? 

/MJ

These configuration files are stored in:
```
/home/*username*/.config/autostart
```

You can open one with a text editor to see how the contents are written should you want to create them on your own.

---

### Post by avtolle on 2008-07-01
Or, instead of opening the file with a text editor (to avoid an inadvertent edit) you could inspect the contents by ```
cat /home/*username*/.config/autostart
```

---

### Post by MidnightJulia on 2008-07-01
Are you sure that is the right place? I've just look in that dir and I can't find that file.

[email]user@oden:~/.conf[/email]ig$ ls -alF
total 28
drwxr-xr-x  5 user user 4096 2008-06-19 21:16 ./
drwxr-xr-x 48 user user 4096 2008-07-01 15:54 ../
drwx------  2 user user 4096 2008-06-29 20:28 gtk-2.0/
drwx------  2 user user 4096 2008-06-19 21:27 totem/
drwx------  2 user user 4096 2008-05-28 13:16 tracker/
-rw-------  1 user user  630 2008-05-28 13:16 user-dirs.dirs
-rw-r--r--  1 user user    5 2008-05-28 13:16 user-dirs.locale
[email]user@oden:~/.conf[/email]ig$ pwd
/home/user/.config

What am I missing? :)

---

### Post by avtolle on 2008-07-01
Just checked it; try to ```
cd /home/USERNAME/.config/autostart
ls
```lists the apps that start up for me. I suppose in your post you changed your USERNAME to user for security purposes, right?

---

### Post by drs305 on 2008-07-01
Do you show anything in Syst, Prefs, Sessions, Startup Programs? The folder and entries may not be created until you add something in the Sessions/Startup pane.

---

### Post by MidnightJulia on 2008-07-01
> **drs305 said:**
> Do you show anything in Syst, Prefs, Sessions, Startup Programs? The folder and entries may not be created until you add something in the Sessions/Startup pane.

And that solved it! As soon as I addad an app to autostart the dir was created. Thank you :)

---

