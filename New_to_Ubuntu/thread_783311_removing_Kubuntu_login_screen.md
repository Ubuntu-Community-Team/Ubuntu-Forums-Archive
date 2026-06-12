---
title: "removing Kubuntu login screen"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by andyrue304 on 2008-05-05
Hello folks,

I just installed KDE on my Hardy 8.04, mainly just out of curiosity. I think I'm going to stick with GNOME though, but keep KDE installed for somethings that may work better.

Anyway I'd like to know how I can change back the loading screen and login screen to the GNOME defaults as installing KDE had changed them and I don't like it :)

Cheers!

---

### Post by ChompTheMan on 2008-05-05
Open up a terminal(K Menu->System->Konsole in KDE, Applications->Accessories->Terminal in Gnome) and type in the following:

```
sudo apt-get remove kubuntu-artwork-usplash kubuntu-default-settings
```

---

### Post by andyrue304 on 2008-05-05
> **ChompTheMan said:**
> Open up a terminal(K Menu->System->Konsole in KDE, Applications->Accessories->Terminal in Gnome) and type in the following:

```
sudo apt-get remove kubuntu-artwork-usplash kubuntu-default-settings
```

Thanks did this and now the Kubuntu splash screen has gone...

BUT now when I go to the login screen I get a message that says

> Cannot open theme file /usr/share/apps/kdm/themes/kubuntu

I think I have KDM activated and I need to re-activte the GNOME version to get that screen back again. How do I do that?

EDIT: now fixed

---

### Post by dodle on 2008-08-02
If you're still having a problem with this use this command in a terminal:```
sudo dpkg-reconfigure gdm
```or```
sudo dpkg-reconfigure kdm
```It doesn't matter which.

This should allow you to switch between the Kde Display Manager and the Gnome Display Manager.

---

