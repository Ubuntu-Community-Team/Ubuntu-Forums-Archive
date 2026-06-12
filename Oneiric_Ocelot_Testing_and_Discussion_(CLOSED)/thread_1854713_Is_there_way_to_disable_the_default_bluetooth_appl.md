---
title: "Is there way to disable the default bluetooth applet in Oneiric?"
date: 2011-10-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dsfitzpat on 2011-10-04
With the default setup in 11.10 the bluetooth applet is part of the indicator applets in the Unity panel.  I'd like to disable it because for some reason I can't get it to connect to my Sony BD bluetooth remote control (I've tried everything I can think of.)  However, if I use the blueman bluetooth applet the remote connects with about two clicks of the mouse.
Since there's no reason to have two bluetooth applets running I'd like to disable the original one, as I did in 11.04. Unfortunately, the startup application management is extremely limited under Gnome 3 - it allows me to add new startup applications but does not allow me to remove default startup applications.
Is there a way to edit the startup programs manually?  Or do I need some sort of kludge, like writing a script to kill the unwanted bluetooth applet automatically?
(Alternatively, if anyone knows how to get this remote to work with the default bluetooth, I'd be just as happy to drop blueman!)

---

### Post by cariboo on 2011-10-04
Have a look at the first page of [this]("http://ubuntuforums.org/showthread.php?t=1795650&highlight=disable+startup+applications") thread.

---

### Post by dsfitzpat on 2011-10-04
OK thanks, I'll give that a try.  (Fortunately the answer seems to be on the first of the 7 pages.)  Not sure why I can't just get the default applet to work with this remote.  With blueman I just choose 'Proceed without pairing', then 'Input service' and I'm up and running.  With the default applet it seems to try to set up pairing even if I select the do not pair option, and setup fails.

---

### Post by sonnet on 2011-10-07
> **cariboo907 said:**
> Have a look at the first page of [this]("http://ubuntuforums.org/showthread.php?t=1795650&highlight=disable+startup+applications") thread.

This doesn't work for me. I have a cmd line system on top of which I installed Gnome-shell.
If I check on my startup application applet, the only items present in the list are caribou and nvidia settings.
But I can clearly see bluetooth service being loaded while booting up.
Is there a way i can prevent that it? (given that I can't uninstall bluetooth as gnome-shell depend on it :confused: )

---

### Post by cariboo on 2011-10-07
Did you run the following commands:

```
cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

to populate gnome-session-properties?

The screenshot is what mine looks like after running the command

---

### Post by sonnet on 2011-10-07
> **cariboo907 said:**
> Did you run the following commands:

```
cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

to populate gnome-session-properties?

The screenshot is what mine looks like after running the command

Thanks a lot, that worked.

---

### Post by dsfitzpat on 2011-10-07
That's great!  Perhaps will see this command and others like it appear in some sort of "Gnome 3 power users' manual" for those who want to do a bit of tinkering.
BTW, in my case the default bluetooth applet miraculously started communicating with my bluetooth remote, in spite of the fact that I never managed to run a successful setup!  As long as I can repeat the feat in the future, I'll just drop blueman.

---

