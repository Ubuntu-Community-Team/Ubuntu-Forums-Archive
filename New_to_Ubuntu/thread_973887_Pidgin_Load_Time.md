---
title: "Pidgin Load Time"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Rylix on 2008-11-07
Hi there everybody, this is my first time on these forums :)

I've been really happy with Ubuntu and as i've got more comfortable with it i've started fiddling and customizing. However i've run into a bit of a problem with my Pidgin IM.

Whilst on a fresh install Pidgin would load relatively quickly when I press it's icon, it is now taking upwards of 5 seconds just to show the window. I recently added the purple addons pack for the list plugin so I could copy contacts from one email into another- however I managed to crash pidgin copying contacts from one email to another and then back to the original. I was forced to resistall pidgin from the synaptics package manager as it wouldn't load at all, but now it will take an odd amount of time to load. Also of note is that when pressing Accounts > Manage, the window freezes for over 10 seconds which didn't use to happen before this started.

Has anybody got any ideas on fixing this? I use pidgin alot and so this is quite frustrating.

Thanks for your help in advance :)

---

### Post by Liviu-Theodor on 2008-11-07
From what you said, I can think only of a small memory environment. How much RAM do you have?

---

### Post by ww711 on 2008-11-07
> **Rylix said:**
>  I recently added the purple addons pack for the list plugin

Try temporarily disabling any plug-ins that you've add to pidgin.

---

### Post by Rylix on 2008-11-07
Thanks for the replies :)

I have 2 gigabytes of ram, and I have removed all plug-ins to test the problem, which stayed even when there were no plugins installed, including the entire purple plug-ins Debian package through synaptic.

I have, however, noticed that disabling/removing my display picture solves the problem. What could cause that?

Thanks for your time already!

---

### Post by Karilex on 2008-11-07
I know this isn't the answer you are looking for but if you are willing to give it a try why not use an alternative open source instant messenger such as amsn or xchat?

---

### Post by Rylix on 2008-11-07
> **Karilex said:**
> I know this isn't the answer you are looking for but if you are willing to give it a try why not use an alternative open source instant messenger such as amsn or xchat?

Heh, I have. aMsn is very intrusive in my oppinion and xchat feels too much like an irc client. Pidgin is really good, I just stuffed it up somehow :P.

Is there any settings that can be left behind after removal through synaptic package manager that i should look for to delete? :)

---

### Post by pgorillaman on 2008-11-07
Did you do a complete removal from synaptic?

---

### Post by Rylix on 2008-11-08
> **pgorillaman said:**
> Did you do a complete removal from synaptic?

Yes, as well as the data package and all plugins.

---

### Post by Tom--d on 2008-11-08
CouldI suggest Emesene?

---

### Post by ./. on 2008-11-08
> **Rylix said:**
> Is there any settings that can be left behind after removal through synaptic package manager that i should look for to delete? :)

You could try GtkOprhan (available from the Universe Repository).  It's a graphical tool that can be used to remove any configuration files / libraries associated with uninstalled applications.

Or course, I don't know if this will speed up your load times.

---

### Post by DoctorBeaver on 2008-11-08
I use emesene and I like it. I find pidgin a bit simplistic.

---

### Post by Karilex on 2008-11-08
maybe kopete hunt around to find a nice chat that you would like

---

### Post by Rylix on 2008-11-09
I tried GTKOrpahn, looked like a good idea, but I didn't find anything related to Pidgin. Is there a particular package I should look for through it?

And thanks for the suggestions about alternative messenger programs- however, I really like pidgin and it's not it's fault I stuffed it up somehow. Any ideas finding out what's wrong with it? It's only on startup and accessing the accounts menu, i'm thinking it's something to do with that...

---

