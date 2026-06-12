---
title: "no alt+f2 for run?"
date: 2011-06-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by josephmills on 2011-06-27
title says it all has this been taken away in in 11.10? I can seem to get it to work. thanks for your time.

---

### Post by fjgaude on 2011-06-27
It's early Alpha; lots of things don't work. Wait until the release in October and things will be full-up.

---

### Post by Framli on 2011-06-27
@josephmills, which desktop are you using

---

### Post by sparker256 on 2011-06-27
> **josephmills said:**
> title says it all has this been taken away in in 11.10? I can seem to get it to work. thanks for your time.

It is working on my 64 bit Ubuntu 11.10 on the Unity 3D, Unity 2D and Gnome desktops.

Bill

---

### Post by josephmills on 2011-06-27
thanks for the answers guys I know that it is in alfa but me likie testy :) it is 32bit and it is under unity that it is not working just thought that this might be useful just want to be more involved in the community also it is in vbox with all the guest additions and I noticed that it is the 3.0.1 kernel YEAH

---

### Post by jerrylamos on 2011-06-28
This is 28 June .iso.  Just tried Alt-F2 and it said run a command which it did.

I usually use Ctrl-Alt-t to open a terminal session window which I prefer to Alt-F2 because the latter doesn't keep a window open and I can't see any messages from the run command.

Jerry

---

### Post by Framli on 2011-06-28
Do you see the *Applications* item in the launcher?
In the file /usr/share/unity/places/applications.place do you see these lines?
```
[Entry:Runner]
DBusObjectPath=/com/canonical/unity/applicationsplace/runner
Name=Commands
SearchHint=Run a command
ShowGlobal=false
ShowEntry=false
```

---

