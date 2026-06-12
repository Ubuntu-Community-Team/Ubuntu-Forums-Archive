---
title: "is this possible? [multiple user/sessions question]"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by navidad on 2008-04-25
Ok, so I'm partial to simplicity/performance: openbox, terminals, lightweight console apps, plethora of keyboard shortcuts, etc.

The lady in my life (who seems to make all the rules) is partial to  the exact opposite: fully featured desktop environments, lots of icons that she can click on, applets, firefox 3 with a multitude of plugins, etc. (she's a long time Windows user and I don't want to give her a harsh transition)

Is there a way to change which programs are loaded at login depending on the user? For example, I want to type in my username/password, click on Openbox Session, and login with only my personalized apps/background processes running (no gnome bloat). Two minutes later, I log off, she types in her username/password, clicks on Gnome Session, and all of her pretty apps are loaded up.

Is this possible with only one installation of Ubuntu, or are two separate installs (desktop edition for her, cli install + few apps for me) in our future??

Thanks!!

---

### Post by Paqman on 2008-04-25
Completely doable. Since you're using two completely different desktop environments completely different services will start up at login. The only slight hassle is manually changing your session every time you log in. Plus you'll have a lot of packages installed that you won't use, as will she.

---

### Post by navidad on 2008-04-25
So just because we'll have lots of packages installed, doesn't mean they'll be slowing down my lightweight session? Do I have to manually shut off the processes that run in Gnome when I log into Openbox session?

---

### Post by Oldsoldier2003 on 2008-04-25
> **navidad said:**
> So just because we'll have lots of packages installed, doesn't mean they'll be slowing down my lightweight session? Do I have to manually shut off the processes that run in Gnome when I log into Openbox session?

Nope they wont slow you down because they wont be loaded unless you launch a gnome application. We get a variation of this question a lot in reference to people that like Amarok but use gnome for their desktop. 

Basically if you don't launch gnome aps you won't load gnome libraries.( There are ways to load libraries for other desktops to speed app launch, but I don't think you are interested in that)

---

### Post by navidad on 2008-04-25
Excellent, thanks guys!

---

