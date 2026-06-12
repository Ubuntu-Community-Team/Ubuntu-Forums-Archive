---
title: "HOWTO: Keep your theme consistent when running apps as root."
date: 2006-03-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Zeroangel on 2006-03-21
If you've ever modified your theme and went into synaptic or nautilus (as root) only to find that the interface is the boring default one then this fix is for you.

It's really simple actually. Simply run these commands.
```
sudo rm -R /root/.themes
sudo rm -R /root/.icons
sudo ln -s /home/$USER/.themes /root
sudo ln -s /home/$USER/.icons /root
``` And now administrative apps (such as Synaptic) will be able to use your current theme. 

The one caveat is that should a new theme be added while gnome-theme manager is running as root, then the new theme will be uninstallable by the user unless he/she does so as root (or changes the permissions of the newly added/updated theme folder). This should never happen under normal circumstances.

---

### Post by Pretzal on 2006-03-22
me@Ubuntu:~$ sudo ln -s /home/me/.themes/* /root/.themes/
ln: when making multiple links, last argument must be a directory

what has happened here?


Thanks

---

### Post by JustRandomName on 2006-03-22
Surely this is VERY bad advice.

As soon as a program (for whatever reason) writes to ~/.icons & ~/.themes then thoose files will be owned by root, meaning you have to chmod as root.

Sorry for bashing, but this seems really stupid imo... but I am still a newbie myself so I probably wrong.

Anyone else have any thoughts?

P.S.

Pretzal, you probably have to do something like
```
sudo mkdir /root/.themes
```

---

### Post by Zeroangel on 2006-03-22
I can't see a situation where that might happen. Except maybe if you run 'gksudo gnome-theme-manager' and install the same theme over top of an existing one. 

I would like to read any better ideas that people might have.

---

### Post by Coutsos on 2006-03-22
The only thing I would change is instead of making links to the individual files in your themes folder, make a link to the themes folder itself.

What I'd really like to know is where to find the file that stores your theme settings so I can link to that too.

---

### Post by Zeroangel on 2006-03-22
That is a great idea. :KS I've just tested how gksudo reacts when the /root/.themes and /root/.icons folders do not exist (ie: if the /home/$USER folder is renamed or deleted) and it simply uses the default themes.

I have edited my first post as per your suggestion.

---

### Post by akiro.yamamoto on 2006-03-23
Thanks for the tip ZeroAngel, works like a charm ;)

---

### Post by qetuR on 2009-05-03
I have newly made a fresh install of Ubuntu 9.04 (JJ), but I can't use these commands. .themes doen't exist in /root. 

How should I do?

EDIT: Ah, just make the two last commands, since .themes isn't in the /root computer.

---

### Post by tabibito on 2009-05-03
Just extract or copy your theme files to /usr/share/themes.

Works like a charm to me.

---

### Post by tabibito on 2009-05-03
Try copying or extracting your theme files to **usr/share/themes/**. Then just select the theme you want to use from theme selector GUI. It will retain the theme you chose even when you run apps as a root.

---

### Post by tabibito on 2009-05-03
Sorry for the previous double post.

---

### Post by Zeroangel on 2009-09-01
> **tabibito said:**
> Just extract or copy your theme files to /usr/share/themes.

Works like a charm to me.
My method is more efficient, since you only have to do it once -- as opposed to every single time you change to a new theme which wasnt previously in /usr/share/themes

---

