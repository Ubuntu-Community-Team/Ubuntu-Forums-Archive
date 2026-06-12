---
title: "Unetbootin Too Long Loading After Install KDE"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by Malsasa on 2013-04-03
[LEFT][COLOR=#2E3436][FONT=Open Sans]In beginning time I installed Unetbootin, it is fine to add my local Linux ISO then burn it into USB. But after I install KDE, I don't know why Unetbootin face become Qt (GTK before) and needs [/FONT][/COLOR][COLOR=#2E3436][FONT=Open Sans]**too long time**[/FONT][/COLOR][COLOR=#2E3436][FONT=Open Sans] for loading KDE File Chooser Dialog. And Unetbootin becomes greyish (like usual crash on Ubuntu) soon after I clicked add ISO button.[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Open Sans]Problem: I have ran Unetbootin via $ sudo unetbootin and the result was always like these:[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Open Sans]Error: "/tmp/ksocket-master" is owned by uid 1000 instead of uid 0.[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Open Sans]Error: "/tmp/kde-master" is owned by uid 1000 instead of uid 0.[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Open Sans]Long time to open Unetbootin, and it looks like crashed, makes me difficult to burn ISO quickly like before.

[/FONT][/COLOR][/LEFT]
[IMG]http://i.imgur.com/OC9cD5f.png[/IMG]

---

### Post by mastablasta on 2013-04-03
unetbootin is a graphical application. you shouldn't run graphical applications with sudo command. it will cause ownership problems. use gksu in gnome and kdesudo in KDE run graphic apps.

are you using only KDE now? did you install KDE or Kubuntu desktop package?

---

### Post by Malsasa on 2013-04-03
I use MATE, KDE, Unity, and GNOME 3 now. I have tried all ways but same. With or without sudo/gksu. Can you give me suggestion? Thank you so much for fast answering.

---

