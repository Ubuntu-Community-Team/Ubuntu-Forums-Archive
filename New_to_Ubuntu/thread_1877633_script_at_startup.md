---
title: "script at startup"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by Psychokiller1888 on 2011-11-08
Hello!
 
I'm having a little issue with a script I want to run on my session startup. It launches a java GUI actually. So the thing is that I have my shell script, containing start/stop/update/backup commands, placed in init.d folder, starting the java program. It works normally, only that on first start, it can't load the GUI as it says that 
 
"No X11 variable was set....."
 
So of course, I thought ok, it starts before x11 has even started...
 
So my temp solution is after session start, quickly stop the sript via my terminal, and start it again :)
 
But the question is now, how can I make it start only after x11 has initialized? On the french forum, the one and only """answer""" I got was: "We do not start a GUI at session startup, get ride of it". Sorry, that's not a reply for me....
 
Thank you for any help you can provide!

---

### Post by aeiah on 2011-11-08
the reply is correct, in a way. the cleanest way to do it would be to let your desktop environment start up the application

---

### Post by Psychokiller1888 on 2011-11-08
So there's no way??? In other linux distro, you can just place the scripts in other init level folder and it's made, but on Ubuntu it's not possible??

---

### Post by cbowman57 on 2011-11-08
You'd make it an autostart .desktop file.

Open up Startup Applications (gnome-session-properties) and add an entry that runs the script or command.

---

