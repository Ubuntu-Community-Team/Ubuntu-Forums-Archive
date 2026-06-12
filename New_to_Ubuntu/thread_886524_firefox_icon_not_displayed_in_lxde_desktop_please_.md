---
title: "firefox icon not displayed in lxde desktop please help"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by imgkg on 2008-08-11
i switched to [SIZE="7"][COLOR="Red"]lxde[/COLOR][/SIZE] desktop but firefox icon and many other isnt displayed in my panel any help to fix this out  i have attached a screen shot if u can see what i mean i am highlighting that [SIZE="7"][COLOR="Red"]lxde[/COLOR] [/SIZE]thing for you not to mistake it for gnome it different from gnome please dont reply how to do it in gnome desktop i am having trouble in [SIZE="7"][COLOR="Red"][SIZE="7"]lxde[/SIZE][/COLOR][/SIZE] desktop, try to understand its [SIZE="7"][COLOR="Red"]lxde[/COLOR][/SIZE] not gnome, please give solution related to [SIZE="7"][COLOR="Red"]lxde[/COLOR][/SIZE] desktop not gnome, its [SIZE="7"][COLOR="Red"]lxde[/COLOR][/SIZE] not gnome

---

### Post by gaussian on 2008-11-08
Found this via Google... I am really not an absolute beginner :), I am more somewhere close to the midpoint between between absolute beginner and a kernel hacker. 

Anyhow, I am having exactly same problem. I'll try to post the answer if I found one.

---

### Post by gaussian on 2008-11-08
Ok, found the answer:

1) You need to edit file /usr/share/applications/firefox.desktop with root privileges (sudo gedit...) and change the line that says Icon=firefox-3.0 to Icon=firefox.png

2) Go to command line and do
```

sudo cp /usr/share/icons/nuoveXT2/36x36/apps/firefox.png /usr/share/pixmaps/

```

3) Logout and log back in

---

