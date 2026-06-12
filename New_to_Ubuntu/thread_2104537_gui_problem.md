---
title: "gui problem"
date: 2013-01-13
forum: New to Ubuntu
---

### Post by john rosswrock on 2013-01-13
I'm using ubuntu 12.10 and have installed compiz and fustion icon... but now no side bar or bar at the top r not showing.so how do i get gnome back and below is the pic of my screen...plz help

---

### Post by 64Buntu on 2013-01-13
can you open terminal? ctrl + alt + t ?

---

### Post by john rosswrock on 2013-01-13
> **64Buntu said:**
> can you open terminal? ctrl + alt + t ?

yes i can

---

### Post by deadflowr on 2013-01-13
Where you running the default Ubuntu desktop, which is unity.
Or did you install the gnome-shell?
If you are using the default setup, compiz was already installed.
Chances are you reset compiz which would have disabled the unity shell.
In the terminal:
```
unity --reset
```

or if that doesn't help:

```
sudo apt-get update && sudo apt-get install compizconfig-settings-manager
```

When installed, in the terminal type 'ccsm'.
This will open the settings manager. go to the ubuntu unity shell plugin, or whatever it called and enter it. In the left pane is an enable button. Click it if it is NOT enabled(don't touch it if it is).

Of course the preceding only applies if your running the default setup. If you've installed Gnome-shell or other DEs let us know.

---

### Post by john rosswrock on 2013-01-13
> **deadflowr said:**
> Where you running the default Ubuntu desktop, which is unity.
Or did you install the gnome-shell?
If you are using the default setup, compiz was already installed.
Chances are you reset compiz which would have disabled the unity shell.
In the terminal:
```
unity --reset
```or if that doesn't help:

```
sudo apt-get update && sudo apt-get install compizconfig-settings-manager
```When installed, in the terminal type 'ccsm'.
This will open the settings manager. go to the ubuntu unity shell plugin, or whatever it called and enter it. In the left pane is an enable button. Click it if it is NOT enabled(don't touch it if it is).

Of course the preceding only applies if your running the default setup. If you've installed Gnome-shell or other DEs let us know.

there is no ubuntu unity shell plugin...i search but didn't find it ... and how do i know is i have installed gnome-shell ...(actually i m new to ubuntu)

---

### Post by deadflowr on 2013-01-13
Run:

```
echo $DESKTOP_SESSION
```

If it says ubuntu, then you are running Unity.
If it says anything else then you are running whatever it says.

When you opened ccsm, did you look in the desktop section? That is where the ubuntu unity plugin is located. 
The name has changed several times so I forget what it's called in 12.10( I'm currently running 13.04 development so...)

---

### Post by john rosswrock on 2013-01-14
Thanks a lot deadflowr problem solved ....actually it was conflicting with gnome and i choose resolve conflict option...thanx

---

