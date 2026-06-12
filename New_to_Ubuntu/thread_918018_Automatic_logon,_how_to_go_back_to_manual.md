---
title: "Automatic logon, how to go back to manual?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by egalvan on 2008-09-12
Ok, I was following a series of posts, trying to teach my self things Linux.
I messed up several items, and will be posting separately.

General Information:
Ubuntu 8.04.1
Kubuntu meta-package installed under Synaptic

Specific information:
I was playing with having a drop-down list of users show up in the log-in screen. i wanted to avoid typing the name, (picking it from the list,) and just type the password. Then pick the session (Ubuntu or Kubuntu)

But now I am automatically logged into Kubuntu, with no options at all.

i cannot find the post I followed (another problem for another post)

Can any one help get back the manual log-in routine?

Again, I am "stuck" in Kubuntu.

---

### Post by Dougie187 on 2008-09-12
I don't know how exactly to do it in KDE, but look for your login window settings. In gnome it's under administration, and then "login window", but it should be under something similar in KDE.

EDIT:
Actually, I just found this.

[http://doc.vic.computerbank.org.au/support/autologin/](http://doc.vic.computerbank.org.au/support/autologin/)

That should help, basically just undo everything that it tells you to do.

---

### Post by dualpretop on 2008-09-12
Ubuntu

Administration...Login Window...Security



Kubuntu

System settings...Advanced...Login Manager...Administrator mode...Convenience

---

### Post by dualpretop on 2008-09-12
KDE 4.1


kdesu /usr/lib/kde4/bin/systemsettings

System Settings...Advanced...Login manager...Convenience

---

### Post by bhadotia on 2008-09-12
Log out  and then login with GNOME session and follow dougie's advice. Under 'security' tab there is an option of automatic login - just uncheck it:)

EDIT: Guess, dualpretop's advice is more straight-forward:)

---

### Post by egalvan on 2008-09-12
> **dualpretop said:**
> Ubuntu

Administration...Login Window...Security



Kubuntu

System settings...Advanced...Login Manager...Administrator mode...Convenience

Thanks, exactly what I need. My fumbles fixed...

[B]OOPS, IT DID NOT WORK, I un-checked EVERYthing on this tab except under "Preselect User" the NONE is checked ...re-boot and no joy...
I am still automatically logged into Kubuntu, no login screen comes up at all.

also, I followed the KDE Help screens on this subject, and picked "default" and only "Preselect User: NONE" is checked...same as before...
still no login screen [/B]

---

### Post by bhadotia on 2008-09-12
> **egalvan said:**
> Thanks, exactly what I need. My fumbles fixed...

Now , as to what I want, :)

is there any way to have a drop-down list, the way Windows XP does it?

Or, failing that, is there a way to choose the user, but still require the password?

I thought that "pre-select user" would do it, and that checking "focus password" would let me type in the password.

Corrections gladly welcomed.
Sure: in the 'login window' application in GNOME go to apearance tab and select a theme with a face browser . You can also download and install many other themes from the net.

Cheers.

---

### Post by egalvan on 2008-09-12
> **bhadotia said:**
> Sure: in the 'login window' application in GNOME go to apearance tab and select a theme with a face browser . You can also download and install many other themes from the net.

Cheers.

OK, is there any way to do this under Kubuntu?

Or is Gnome required?

And at this time, too many other themes will just mess us up
(yeah,there are several of us learning Linux here)
Nut later, we will go wild.

---

### Post by bhadotia on 2008-09-12
Why don't you just check the help pages (khelpcenter is a better than yelp in my opinion):)
Anyways first atleast get the work done with GNOME then we'll talk about learning the KDE interface:)(i'm myself downloading KDE 4.1 now). I havent had much experience with KDE so I can't say how we do it in KDE but I'm sure someone will help here:popcorn:

---

