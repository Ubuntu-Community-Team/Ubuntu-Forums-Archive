---
title: "Shell don't start - JS ERROR"
date: 2011-07-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ZamekM on 2011-07-07
Hi everyone!

Today, afer a partial upgrade i had a problem: Gnome shell desen't start and gnome classic start. I had a Clutter error i already had once so i re-install my nvidia drivers like i did the first time. But now i have a better one: Gnome shell still doesen't start (and Classic neither if i don't select it at start) and i have this error when i try gnome-shell --replace:

```
JS ERROR: !!!   Exception was: Error: FIXME: Only supporting zero-terminated ARRAYs
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = '("FIXME: Only supporting zero-terminated ARRAYs")@gjs_throw:0
()@/usr/share/gnome-shell/js/ui/placeDisplay.js:273
()@/usr/share/gnome-shell/js/ui/placeDisplay.js:213
PlacesManager()@/usr/share/gnome-shell/js/ui/placeDisplay.js:131
start()@/usr/share/gnome-shell/js/ui/main.js:144
@<main>:1
'
    JS ERROR: !!!     message = 'FIXME: Only supporting zero-terminated ARRAYs'
Window manager warning:*: Log level 32: Execution of main.js threw exception: Error: FIXME: Only supporting zero-terminated ARRAYs
usr@usr-comp:~$ gnome-shell-calendar-server[2142]: Got HUP on stdin - exiting
```

If you have an idea to go back to gnome shell... (it's hard to use Classic when you use every day Shell!!)

Thanks

Ps: sorry for my english

---
Ubuntu Oneiric 64bit

---

### Post by DavidCHill on 2011-07-07
Same issue here... I'm trying to debug but I don't know gnome3 ... :)

---

### Post by cariboo on 2011-07-07
Try:

```
sudo apt-get -f install
```

to see if that fixes the problem.

If update-manager offers to do a partial upgrade, please don't, as it leads to problems. I would suggest you use either synaptic, or the command line to update during the testing period.

---

### Post by ZamekM on 2011-07-07
Result :

```
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.

```

Sorry it's in french but it's always the same message: no updates offered.

---

### Post by DavidCHill on 2011-07-07
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/807168](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/807168)

---

### Post by DavidCHill on 2011-07-07
> **DavidCHill said:**
> [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/807168](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/807168)

The problem is with the calls:

GLib.spawn_command_line_sync ('pkill -f "^bluetooth-applet$"'); in /usr/share/gnome-shell/js/ui/status/bluetooth.js

and
Util.killall('indicator-application-service'); in /usr/share/gnome-shell/js/ui/statusIconDispatcher.js

If you comment them out, the Gnome thing will start ok.

This is an ugly hack and could incure some other problems but for the time being, my laptop doesn't have bluetooth and ... statusIconDispatcher is ... I don't know... something useful for something I guess.

---

### Post by ZamekM on 2011-07-07
> **DavidCHill said:**
> [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/807168](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/807168)

Your error log come from "gnome-shell --replace"?
Because if yes, i'm not sure that's the same bug than mine.
Someone can confirm?

---

### Post by dino99 on 2011-07-08
yesterday i've directly mailed this issue with backtrace to the maintainer. so we might get an upstream fix today via ricotz testing ppa.

---

### Post by DavidCHill on 2011-07-08
> **dino99 said:**
> yesterday i've directly mailed this issue with backtrace to the maintainer. so we might get an upstream fix today via ricotz testing ppa.

It's the same line of the same .js file so... yeah it's the same thing.

---

### Post by ZamekM on 2011-07-08
> **DavidCHill said:**
> It's the same line of the same .js file so... yeah it's the same thing.

Ok thank's and sorry for the dummy question.
Today, after updates Gnome Shell is back!!
Thank's to all the OO team for their great job.

---

