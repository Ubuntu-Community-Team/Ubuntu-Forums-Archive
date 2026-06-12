---
title: "Klik Applications"
date: 2005-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by KillerKiwi on 2005-10-29
Klik allows you to run applications from a single file (Like OSX application dirs), but its for linux ;) 

to install the Klik client :
1) Press Alt-F2 and paste **wget klik.atekon.de/client/install -O -|sh**
2) Restart your browser

Now to try some applications

[klik://pingus]("klik://pingus") - lemmings clone *
[klik://supertux]("klik://supertux") *
[klik://opera]("klik://opera")
[klik://skype]("klik://skype")
[klik://enlightenment]("klik://enlightenment")

* also avalibe in ubuntu universe repo

Lots more at [http://klik.atekon.de/]("http://klik.atekon.de/")

To 'uninstall' simply delete the file on your desktop

---

### Post by manicka on 2005-10-30
Would I be correct in assuming that you could then move the app to say /opt and it would still work the same as when it is on your desktop.


Edit: no they don't work moving them to a root directory, however you can place them within a folder in your home directory (I dislike icons on my desktop)

---

### Post by kashms on 2005-10-30
Do klik packages interact with the gnome menu at all? For example will there be a menu entry if I install opera this way?

---

### Post by bugmenot on 2005-10-30
Yes, klik applications add them selves to the menu the first time you run them.

Klik apps can be moved anywhere within your home directory.

btw, you could also email/ftp/fileshare the klik file

---

### Post by kashms on 2005-10-30
I installed pingus and abiword, but they did not show up in the menu. I can start them by clicking the cmg file.

---

### Post by manicka on 2005-10-30
[QUOTE=bugmenot]Yes, klik applications add them selves to the menu the first time you run them.
[/QUOTE]
That hasn't happened for me with any programs I've tried.
 I assumed it was just a  stand alone package

---

### Post by kashms on 2005-10-30
How can I launch a klik cmg file from a panel launcher? I can double click the file in nautilus, but I didn't find a way to start it from a terminal.

---

### Post by ltmon on 2005-10-30
[QUOTE=kashms]How can I launch a klik cmg file from a panel launcher? I can double click the file in nautilus, but I didn't find a way to start it from a terminal.[/QUOTE]

From the terminal:

~/.zAppRun.sh <application>.cmg

L.

---

### Post by kashms on 2005-10-30
Thanks, that worked.

---

### Post by kashms on 2005-10-31
[QUOTE=ltmon]
~/.zAppRun.sh <application>.cmg
L.[/QUOTE]

This command apparently doesn't work in panel launcher. 

It would be nice to click start an application from the panel instead of opening nautilus, finding the directory and then clicking to start the application.

---

### Post by angrykeyboarder on 2005-10-31
> **KillerKiwi]Klik allows you to run applications from a single file (Like OSX application dirs), but its for linux  said:**
> klik.atekon.de/client/install[/URL] -O -|sh**
2) Restart your browser

Now to try some applications

[klik://pingus]("klik://pingus") - lemmings clone
[klik://supertux]("klik://supertux")
[klik://opera]("klik://opera")
Lots more at [http://klik.atekon.de/]("http://klik.atekon.de/")

To 'uninstall' simply delete the file on your desktop 
I was thrilled to see them making their way to Ubuntu. I used them often with Knoppix.

However....

---

### Post by bugmenot on 2005-10-31
[QUOTE=kashms]This command apparently doesn't work in panel launcher. 

It would be nice to click start an application from the panel instead of opening nautilus, finding the directory and then clicking to start the application.[/QUOTE]
try /home/USERNAME/.zAppRun.sh <application>.cmg

angrykeyboarder, what klik package gave you this error?

Also it on the list of things to do to make klik packages executable :) as well as icons

---

### Post by kashms on 2005-11-01
[QUOTE=bugmenot]
try /home/USERNAME/.zAppRun.sh <application>.cmg
[/QUOTE]

This works in the terminal, but in a panel launcher I get an error message: "unable to mount /tmp/app/1", followed by ".zAppRun: line 127: /tmp/app/1/wrapper: No such file or directory"

---

### Post by manicka on 2005-11-01
An easy way to make a panel launcher is to drag the *application*.cmg file and drop it on the launcher bar. This will create a new link icon on the panel. Change the icon by right clicking on the panel icon-->properties, then change the icon in the usual way.

You could also look at the command that it creates to make a menu entry with smeg.

Works for me :)

---

### Post by manicka on 2005-11-01
[QUOTE=angrykeyboarder]I was thrilled to see them making their way to Ubuntu. I used them often with Knoppix.

However....[/QUOTE]


Pingus and Supertux are available in the universe repos

---

### Post by angrykeyboarder on 2005-11-01
[quote=manicka]Pingus and Supertux are available in the universe repos[/quote]

How does this relate to my situation?

---

### Post by kashms on 2005-11-01
[QUOTE=manicka]An easy way to make a panel launcher is to drag the *application*.cmg file and drop it on the launcher bar. This will create a new link icon on the panel. Change the icon by right clicking on the panel icon-->properties, then change the icon in the usual way.

You could also look at the command that it creates to make a menu entry with smeg.

Works for me :)[/QUOTE]

Thanks, but it turned out I wasn't being very careful in observing what I was actually doing :???: 

I was writing abiword.cmg instead of abiword_2.41-2.cmg :D

---

### Post by manicka on 2005-11-01
[QUOTE=angrykeyboarder]How does this relate to my situation?[/QUOTE]

Ah I see, I thought you were talking about the applications, not Klik itself.

Looks like they still have some work to do on some apps.

---

### Post by westmatrix on 2008-05-06
Mine says Choose application.
See attached.

Does not work for me.

---

