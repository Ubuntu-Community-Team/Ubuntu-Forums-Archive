---
title: "Users not showing on login"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by Esot-Eric on 2011-09-22
Hey chaps, I've got a HP pavilion dv6 here and often in spite of it being set to show all users it only shows the one I made when I installed Ubuntu 11.04, it allows me to sign in as another account by typing the username and then the password but this is not how I'd like things to be done. Is there a solution to this?

---

### Post by Esot-Eric on 2011-09-22
Bump, I should add that it can't be anything to do with the usernames themselves, I have the exact same usernames on my main PC and have never had the problem.

---

### Post by corncob on 2011-09-22
System > Administration > Login Screen
Check the button "Show the screen for choosing who will log in".

---

### Post by Krytarik on 2011-09-22
First, try reinstalling "gdm":
```
sudo apt-get install --reinstall gdm
```If that doesn't fix it already, try:
```
sudo cp /usr/share/gdm/gdm.schemas /etc/gdm
```If that doesn't fix it either, I have no other clue than to "Include" the concerning users manually, which would work in any case:

[http://library.gnome.org/admin/gdm/stable/configuration.html.en#daemonconfig](http://library.gnome.org/admin/gdm/stable/configuration.html.en#daemonconfig)

Greetings.

---

