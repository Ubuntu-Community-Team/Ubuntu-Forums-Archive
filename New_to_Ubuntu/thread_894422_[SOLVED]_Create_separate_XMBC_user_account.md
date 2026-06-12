---
title: "[SOLVED] Create separate XMBC user account?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-08-19
How would I go about creating a separate account just for using xmbc? what I want to do is create an account where I can just login and xmbc will load automatically instead of gnome and compiz e.t.c

---

### Post by SlalomMan on 2008-08-19
Alright, you mean XBMC, right? Xbox Media Center? There are two options here. The first and simplest would be to make a user account and go to System->Preferences->Sessions and remove the check mark from all boxes and then add an entry for XBMC. This wouldn't get rid of gnome or compiz, I don't think, but it would get rid of the bulk of things that take up resources. (you might want to leave things like network manager and power manager checked)

The other option seems like it would work, but I have no idea how you would carry it out. If you install KDE and Gnome at the same time, you can login to either a Gnome Session or a KDE session with the current user; I'm sure there would be a way to add an XBMC session, but I'm really not sure how. Maybe a more experienced user could help you out with this.

---

### Post by kamitsukai on 2008-08-19
> **SlalomMan said:**
> 
The other option seems like it would work, but I have no idea how you would carry it out. If you install KDE and Gnome at the same time, you can login to either a Gnome Session or a KDE session with the current user; I'm sure there would be a way to add an XBMC session, but I'm really not sure how. Maybe a more experienced user could help you out with this.

Yer that would be easier hopefully someone can help me with that,

thanks!

---

### Post by unutbu on 2008-08-19
I have an idea, but I'm going to need your help to fill in some pieces of information that I don't know:

What is the command to start XBMC?

Is it just 
```

xbmc
```
?
If so, what happens if you press Ctrl-Alt-F2 to get to a text terminal, and then type
```

xinit xbmc -- :1
```
Does it take you into XBMC?

---

### Post by kamitsukai on 2008-08-19
Yer that works Unutbu although if i exit xbmc it takes me back to the terminal.. anyway to get to the gdm? if you can get this working :)

thanks

---

### Post by unutbu on 2008-08-19
Ok, kamitsukai. Create a new user. Log in as that user.
Create a file in the home account called .xsession

In that file simply put
```

xbmc
```

Save, exit, log out.

At the orange-brown (gdm) login window, press F10. Click on "Select Session". Select "Run .Xclient script" as your choice of session. Then log back in as the new user. You should be tossed directly into xbmc.

---

### Post by kamitsukai on 2008-08-19
Ok i'll try it thanks!

---

### Post by kamitsukai on 2008-08-19
Thanks unutbu that worked perfectly! just a quick question but how do I give that account access to my home directory? so I can watch videos from xmbc

Thanks again!

---

### Post by unutbu on 2008-08-19
If the videos are located at say /home/kamitsukai/Videos, 
then log in as kamitsukai and type
```

chmod a+rx $HOME
chmod a+rx $HOME/Videos
chmod a+r -R $HOME/Videos
```

---

