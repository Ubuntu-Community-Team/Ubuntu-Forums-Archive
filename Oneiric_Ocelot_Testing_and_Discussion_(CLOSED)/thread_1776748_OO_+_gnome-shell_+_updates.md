---
title: "OO + gnome-shell + updates"
date: 2011-06-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-06-06
I'm running OO with gnome-shell and I've just run the latest updates (about 12 iirc) and on rebooting, at the login screen instead of getting the blue stripey desktop background (the one that coffeecat loves so much :wink: ) I'm getting the default purplish live cd desktop backgound and on logging in my normal desktop background appears with my normal conky display.
Buuuuuut, when I open a window (any window, maximised or not) and then close that window, my conky display disappears :(
Buuuuuut, when I open another window and close it my conky display re-appears :-)

So on closing every first window my conky display disappears, but on closing the second window conky comes back!

This keeps happening.

Any ideas people?  :-)

EDIT I'm also getting a context menu now when I right-click on the desktop. That's new! I wonder if I have somehow got a cross between gnome and gnome-shell?

---

### Post by Harry33 on 2011-06-06
This is because there is a new gsettings-desktop-schemas package.
Still, obviouosly there is something strange in your desktop behaviour.

> Changelog
gsettings-desktop-schemas (3.0.1-1ubuntu1) oneiric; urgency=low

  * gsettings-desktop-schemas.gsettings-override: set the default ubuntu
    wallpaper and display the desktop by default.
 -- Sebastien Bacher <email address hidden>   Mon, 06 Jun 2011 17:15:11 +0200

---

### Post by Quackers on 2011-06-06
That may well be the case Harry :-)
I've still got the Gnome3team.ppa enabled, have you? Do I still need that?

---

### Post by Harry33 on 2011-06-07
> **Quackers said:**
> That may well be the case Harry :-)
I've still got the Gnome3team.ppa enabled, have you? Do I still need that?

The package gdm (v.3.0.2) is only available from Gnome3 PPA.
In Oneiric repos there is only the version 2.32.1
So, in order to get updates, you need it.
Or, you have to switch to lightDM.

---

### Post by Quackers on 2011-06-07
Oh, I wasn't aware. Thanks Harry33.

---

### Post by Harry33 on 2011-06-07
> **Quackers said:**
> Oh, I wasn't aware. Thanks Harry33.

Have you tried lightDM?
I am not sure, but I think lightDM will replace gdm already during this OO cycle.

---

### Post by Quackers on 2011-06-07
No, I've heard about it and seen some packages for it, but I have not tried it. (I've got enough problems with what I've already got :wink: :-) )

---

### Post by Quackers on 2011-06-07
The conky problem is solved.
Instead of using 
own_window_type override
or
own_window_type desktop
it now needs to be 
own_window_type normal.
This has been posted before in an earlier thread but it had not been necessary for me to use it until now.

The only oddity now is that the login screen has changed to the default purplish thing instead of the gnome-shell blue stripey thing. No big problem then :-)
Marked solved. Thanks.

---

### Post by ronacc on 2011-06-07
I hadn't heard of lightDM so I just installed it (its in the repos) and rebooted , no noticeable difference except the greeter looks a little different and didn't do my timed login , sign-in manually worked though .

---

### Post by Harry33 on 2011-06-07
> **ronacc said:**
> I hadn't heard of lightDM so I just installed it (its in the repos) and rebooted , no noticeable difference except the greeter looks a little different and didn't do my timed login , sign-in manually worked though .

OK, did you also uninstall gdm too?

A lot of extra packages out there:

> **Built files**
Files resulting from this build:

gir1.2-lightdm-0_0.3.7-0ubuntu1_amd64.deb (5.4 KiB)
liblightdm-gobject-0-0_0.3.7-0ubuntu1_amd64.deb (23.5 KiB)
liblightdm-gobject-0-dev_0.3.7-0ubuntu1_amd64.deb (10.5 KiB)
liblightdm-gobject-0-doc_0.3.7-0ubuntu1_amd64.deb (22.5 KiB)
liblightdm-qt-0-0_0.3.7-0ubuntu1_amd64.deb (49.0 KiB)
liblightdm-qt-0-dev_0.3.7-0ubuntu1_amd64.deb (5.4 KiB)
lightdm-greeter-example-gtk_0.3.7-0ubuntu1_amd64.deb (201.4 KiB)
lightdm-greeter-example-python-gtk_0.3.7-0ubuntu1_amd64.deb (193.2 KiB)
lightdm-greeter-example-qt_0.3.7-0ubuntu1_amd64.deb (17.8 KiB)
lightdm-greeter-example-vala-gtk_0.3.7-0ubuntu1_amd64.deb (197.0 KiB)
lightdm_0.3.7-0ubuntu1_amd64.deb (52.4 KiB)

---

### Post by ronacc on 2011-06-07
I didn't uninstall gdm but while configuring a box popped up asking which DM I wanted lightdm or gdm , I selected lightdm . On reboot I checked with gnome-system-monitor and it showed lightdm to be running and did not show gdm . Do I need to uninstall gdm to get the full effect ?

---

### Post by Harry33 on 2011-06-08
> **ronacc said:**
> I didn't uninstall gdm but while configuring a box popped up asking which DM I wanted lightdm or gdm , I selected lightdm . On reboot I checked with gnome-system-monitor and it showed lightdm to be running and did not show gdm . Do I need to uninstall gdm to get the full effect ?

I think you do not need to uninstall Gdm.
You have now two display managers, one of which is configured (LightDM) to be used.
Of course, if LightDm works well for you and you prefer it to Gdm, then you obviously can uninstall it.

To run LightDM by default, you need to run:
```
sudo dpkg-reconfigure lightdm
```

---

### Post by 23dornot23d on 2011-06-08
I put lightDM in too ..... with dual monitors ..... but it puts the login screen between the two :confused:

---

