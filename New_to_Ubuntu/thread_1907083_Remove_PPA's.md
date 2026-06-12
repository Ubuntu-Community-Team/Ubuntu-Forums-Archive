---
title: "Remove PPA's?"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by d4m1r on 2012-01-10
Hey guys, I am wondering how to remove the listings on the left side? I think those are PPA's I've previously added but uninstalled the software so I don't need them anymore. How can I remove them?

I did try;

Open "Ubuntu Software Center"
- Edit Menu
--- Select "Software Sources...", enter your password
----- Select tab "Other Software"

Removed 2 useless PPA's (each had 2 entries), closed software centre, and re-opened it but they are still there :(

[IMG]http://i.imgur.com/vyX8p.png[/IMG]

---

### Post by oldos2er on 2012-01-10
After you add or remove any repository, you need to refresh your sources.list, which you can do in a terminal by running ```
sudo apt-get update
``` I'm sure you can do it in Software Center, but I'm not sure how.

---

### Post by Frogs Hair on 2012-01-10
When you attempted to remove the sources did you select the whole line and choose remove or just remove the checks from the boxes ?

Remove the check from the box , right click on the source line , select remove and the source should be gone . Do this for each line because there is often two source addresses for each PPA . 

When you attempt close software sources the package system information should update. After this check the source list again .

---

### Post by d4m1r on 2012-01-10
> **Frogs Hair said:**
> When you attempted to remove the sources did you select the whole line and choose remove or just remove the checks from the boxes ?

I first unchecked the boxes and then removed all 4 lines as well.

The problem has fixed itself apparently....I just rebooted my PC and they are no longer there, without having to do apt update :D

---

### Post by BlinkinCat on 2012-01-10
> **d4m1r said:**
> I first unchecked the boxes and then removed all 4 lines as well.

The problem has fixed itself apparently....I just rebooted my PC and they are no longer there, without having to do apt update :D

Hi, Kindly mark thread as "solved" with the thread tools at top of page - :)

---

