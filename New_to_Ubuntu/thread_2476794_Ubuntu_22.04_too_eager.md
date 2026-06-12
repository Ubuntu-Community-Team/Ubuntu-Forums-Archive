---
title: "Ubuntu 22.04 too eager"
date: 2022-07-07
forum: New to Ubuntu
---

### Post by hakelm on 2022-07-07
When running a program that takes some time to become idle, for instance a lengthy sql-query I get a popup window containing text like:

**“Rgbtest” is not responding.**
**You may choose to wait a short while for it to continue or**
**Force the application to quit entirely.**
**Force Quit Wait**

This is very annoying and repeats around every ten seconds after pressing wait.
Is there any way to disable this timeout?
Thanks in advance for any tip
H

---

### Post by DuckHook on 2022-07-09
The default setting for the popup that you are experiencing is 5 seconds. This is sometimes not enough elapsed time for some processes to return control to the user. This limitation applies only to GUI apps. Running queries from the CLI bypasses the popup.

You can change the default from 5 seconds to a time of your choice with:```
gsettings set org.gnome.mutter check-alive-timeout 60000
```Note that the actual time is measured in milliseconds, so the above example would set the timeout to 60 seconds which may be too long, as it will now effect every GUI app including all future instances in which an app is truly hung. I would find it frustrating having to wait a full minute for the prompt to kill an app. Of course, in Linux, you can always kill any process using the terminal *kill* command.

If you really can't abide making system changes via CLI, you can also change this setting with dconf-editor. You will need to first install dconf-editor. This utility is not part of a standard install because it is dangerous in the hands of the careless.

---

### Post by hakelm on 2022-07-09
Thanks a lot. Soon I will see if it works.
H

---

### Post by hakelm on 2022-07-09
The [COLOR=#000000][FONT=&quot]check-alive-timeout remains a nuisance especially when debugging. Is it possible to disable the "feature" entirely?[/FONT][/COLOR]

---

### Post by deadflowr on 2022-07-09
Set it to 0 to disable the alive check.

---

