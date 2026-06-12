---
title: "Reinstall gnome desktop without al of the extra apps"
date: 2014-08-10
forum: New to Ubuntu
---

### Post by the-paul-84 on 2014-08-10
Hi everyone. I was attempting to erase some of the bloated programs on my Ubuntu box (all of the games, open office, abd a few others) because I mostly use this box as a samba server.

However, I must have removed something that should have stayed, because doing things like clicking on settings, or opening the update manager do not always work.

I know I could probably use ```
sudo aptitude install ubuntu-desktop
```

But, I am wondering if there is a way to re install the desktop without all of the extra software so I don't mes things up by uninstalling things again.

I'm not sure if this makes a differemce, but to see what applications are installed and then uninstall them, I use the Ubuntu Software Center.

---

### Post by gbauer156 on 2014-08-10
Are you trying to install gnome 2, 3, or unity?

---

### Post by the-paul-84 on 2014-08-10
I am using gnome version 3.10.4

The os is Ubuntu 14.04 I should have said that originally, sorry for the over-site.

---

### Post by gbauer156 on 2014-08-10
Okay so type in a terminal 'sudo apt-get install gnome-shell' that should install it. But it will have dependencies so whatever apps it installs you will have to keep if you want GNOME.

---

### Post by the-paul-84 on 2014-08-10
I tried that n a VM I have and it seemed to do what I wanted, thanks for that! I'll give it a shot on the server and let you know how it goes

---

### Post by the-paul-84 on 2014-08-10
That seemed to do the trick! Thanks for your help

---

### Post by gbauer156 on 2014-08-10
No problem.

---

