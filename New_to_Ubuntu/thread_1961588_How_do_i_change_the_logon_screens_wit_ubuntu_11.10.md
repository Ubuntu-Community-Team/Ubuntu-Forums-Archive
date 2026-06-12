---
title: "How do i change the logon screens wit ubuntu 11.10"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by koll on 2012-04-19
How do i change the logon screens with ubuntu 11.10 useing the downloads from 
[http://art.gnome.org/themes/gdm_greeter](http://art.gnome.org/themes/gdm_greeter)

---

### Post by jerome1232 on 2012-04-19
Firstly, Ubuntu uses Lightdm as it's display manager, so your are downloading theme's for a dm that you don't even use. You can however install gdm,I believe installing gnome-tweak-tool would then allow you to change gdm's theme, gnome-tweak-tool will also drag in gnome-shell with it.

edit: I was personally happy with simply changing the background lightdm uses, in /etc/lightdm/unity-greeter.conf

---

### Post by PhantomTurtle on 2012-04-19
There is a simple and easy program for this in 11.10. It's called [Simple Light DM Manager]("http://www.omgubuntu.co.uk/2011/10/simple-lightdm-manager-lets-easily-tweak-ubuntu-11-10-login-screen/"). In 12.04, which comes out in 7 days (I'm super exited:)), the background will change according to what wallpaper the user has.

EDIT: Also Ubuntu uses LightDM and not GDM so that tool will not work but Simple LightDM Manager will(it's sole purpose is to change the background in LightDM).

---

### Post by koll on 2012-04-19
sweet that works for me i can wait 7 days

---

