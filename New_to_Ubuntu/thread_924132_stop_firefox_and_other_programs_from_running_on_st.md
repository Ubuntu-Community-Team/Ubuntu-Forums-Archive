---
title: "stop firefox and other programs from running on startup"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by nneedrelief on 2008-09-19
i tried to do some homework on stopping some programs from running

i saw these two [http://ubuntuforums.org/showthread.php?t=477391](http://ubuntuforums.org/showthread.php?t=477391)

 [http://ubuntuforums.org/showthread.php?t=238586](http://ubuntuforums.org/showthread.php?t=238586)

but i didn't understand a few things like how to do this part 

"Solved. Just un-install network-manager-gnome and reinstall. Then run "nm-applet" in Terminal."

or 

"Hi,

open the file ~/.cache/.sessions/xfce4-session-????? and remove all entries of nm-applet but one. Renumber the Client? headings appropriately and set Count equal to the last client number + 1. Save. Logout w/out saving the session and you are done.

GIulio"

and of course its solved so i can't ask them directly. please help me i get like 5 things popping up like firefox, skype, pidgin, orange calender, omg they all just come up at the same time and i can't do anything until i unlock the wifi internets keyring!

please speak slowly and translate programming lingo into english, *totall nuub status* :(

---

### Post by hellion0 on 2008-09-19
Were all these programs running when you shut down/rebooted/logged out of the machine last time? XFCE has a tendency to remember those programs on shutdown and restart them on the next login.

What you can try is this:
1. Shut down with *no* extra programs (Firefox, Pidgin, Terminal, etc) running. Then restart.
2. Once restarted, go into Applications -> Settings. Open Settings Manager.
3. On the window that opens, click "Session"
4. Search for an option to restart programs on login (or similar) and untick it.

Then, hopefully, you'll be set.

---

### Post by nneedrelief on 2008-09-19
thanks for the quick reply. i'm 95% sure i close all the programs in shutting down. i'll do it now and reboot and edit of something new happens

when i did what you said i show two tabs general and advanced

in general the shake down is like this
-display chooser on login

-automatically save session on logout
/prompt on logout
-show hibernate button
/show suspend button

where "-" means unchecked and "/" means checked

in advanced there's an option to launch Gnome services on startup... should i uncheck that?

---

### Post by hellion0 on 2008-09-19
That won't effect the problem you're having. Just leave it ticked.

---

### Post by nneedrelief on 2008-09-19
okay so closing firefox before rebooting worked. i guess i always run sudo reboot and don't realize that i haven't closed the browser i'm running. I also found the button for session just before logging in and the first option is "last session" second and third are xfce and for some reason the third was the one in default. anyways toggling between the first and third just mean firefox opened as normal but blank, so closing it worked

orage, pidgin, and firefox are all gone now, thanks

but how do i stop the internet for asking for a keyring? its the same connection i use at home and that still comes up everytime i start the computer, shouldn't it remember since its the same connection?

---

### Post by melmantheman on 2011-08-12
Thank you the same applied to KDE. but under a different sort of title. Ive been looking because GIMP always came up

---

