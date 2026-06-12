---
title: "Python script test run as root from IDE"
date: 2008-06-02
forum: Programming Talk
---

### Post by unclecameron on 2008-06-02
I'm logged in as a regular user running SCITE Python IDE and the script I'm writing needs to run as root, is there code I can add in the script to sudo and run as root? I don't want to login as root and run the SCITE IDE. Also I could open another terminal as root and just run it, but that defeats the purpose of the simulator in the IDE.

---

### Post by LaRoza on 2008-06-02
> **unclecameron said:**
> I'm logged in as a regular user running SCITE Python IDE and the script I'm writing needs to run as root, is there code I can add in the script to sudo and run as root? I don't want to login as root and run the SCITE IDE. Also I could open another terminal as root and just run it, but that defeats the purpose of the simulator in the IDE.

**Remember all the warnings that go with running as root**

Can you try running the IDE as root? (press Alt + F2 and type "gksu scite" or whatever the IDE is called)

---

### Post by unclecameron on 2008-06-03
when I attempt to run it as root I get an error
```
(scite:5602): Gtk-WARNING **: cannot open display: :0
```
which is a similar error I got trying to run OpenKomodo and Eclipse as root wile logged in as a regular user.

---

### Post by unclecameron on 2008-06-26
well, I "fixed" it by logging in as root, since my IDE SCITE will run the python app, but since it needs to run os.system("runmyrootbashscript") then the IDE (which is gui-based) needs to run as root. Anyone got any workarounds for this?

---

### Post by geirha on 2008-06-26
```
os.system("gksudo runmyrootbashscript")
```

---

