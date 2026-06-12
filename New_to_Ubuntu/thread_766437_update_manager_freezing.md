---
title: "update manager freezing"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Falc7 on 2008-04-25
I am trying to update to Hardy Heron, but when i click upgrade on the update manager, it goes gray, the circle continues to spin, but nothing else happens, i have left it like this for an hour to far and nothing.

edit: It has just fixed itself :)

---

### Post by joshrobinson on 2008-04-25
> **Falc7 said:**
> I am trying to update to Hardy Heron, but when i click upgrade on the update manager, it goes gray, the circle continues to spin, but nothing else happens, i have left it like this for an hour to far and nothing.

edit: just after posting this it tells me, could not download release notes, check your internet connection. 
However i am definately connected to the internet.

the servers are swamped right now is all
have you tried using a terminal to check for updates?
if you installed hardy final, or upgraded from gutsy, there shouldnt be any updates anyway

but open a terminal applications > accessories > terminal
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

although it might take awhile to update the sources

---

