---
title: "Run Java app when user logs in"
date: 2010-08-05
forum: Programming Talk
---

### Post by Smigh on 2010-08-05
Let's say I want to have a JCheckBox in a Java application labeled "Start this application automatically when the computer starts up" like many messenger and voip applications.

In windows maybe I could put a shortcut or a bat file in the startup folder or maybe add a line to the registry pointing to my application.

How would I do this in Ubuntu? This application has a GUI so I would want to run it when the graphical environment starts. I don't know much about the internal mechanisms of nix's and nux's but there must be a place where I can generate some script to execute a "java -jar ..." command on startup (or on logon).

---

### Post by Queue29 on 2010-08-05
I put all my startup scripts in ~/.bashrc which works well enough, though there's probably a [S]better[/S] more recognized way of doing it.

---

### Post by ju2wheels on 2010-08-05
Add your script or command to /etc/rc.local .

---

