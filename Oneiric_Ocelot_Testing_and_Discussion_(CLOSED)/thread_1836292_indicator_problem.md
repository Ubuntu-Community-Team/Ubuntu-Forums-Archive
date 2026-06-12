---
title: "indicator problem"
date: 2011-08-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by flipper T on 2011-08-30
indicator panel looks like attached screenshot

just me ?

any solution ?

---

### Post by lidex on 2011-08-30
I had a similar situation where 2 power-indicator icons showed in the panel. Try re-installing these:
```
sudo apt-get install --reinstall indicator-power indicator-power-gtk2
```
Logout/in

This just in:
[http://ubuntuforums.org/showthread.php?t=1835472](http://ubuntuforums.org/showthread.php?t=1835472)

---

### Post by flipper T on 2011-08-30
```
jason@jason-M570RU:~$ sudo apt-get install --reinstall indicator-power indicator-power-gtk2
[sudo] password for jason: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package indicator-power-gtk2
```

i tried...

must remain zen, it is still alpha :)

---

### Post by lidex on 2011-08-30
Have you updated your sources lately?

---

### Post by jbicha on 2011-08-31
> **lidex said:**
> I had a similar situation where 2 power-indicator icons showed in the panel. Try re-installing these:
```
sudo apt-get install --reinstall indicator-power indicator-power-gtk2
```


Where are you getting indicator-power-gtk2 from? It's not in the archives and shouldn't be installed.

---

### Post by lidex on 2011-08-31
> **jbicha said:**
> Where are you getting indicator-power-gtk2 from? It's not in the archives and shouldn't be installed.

You are correct, it is in the tista-gtk3 PPA that I added for the elementary-borderless theme. I was trying to get my indicators in line after having removed the gtk2 versions caused some issues, so I (re)installed gtk2 versions of all my gtk3

@flipper T
Did you check the other thread I linked to?

---

### Post by flipper T on 2011-08-31
hi lidex

the dconf edit appears to have worked, thx :)

---

