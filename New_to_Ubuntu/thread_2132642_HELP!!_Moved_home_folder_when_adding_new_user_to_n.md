---
title: "HELP!! Moved home folder when adding new user to new users folder"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by hankyknot on 2013-04-05
A colleague of mine added a new user to our hardy heron server and in doing so managed to kinda kill everything.

When they added the user their home folder was set to \home and saved
He then realised that it shouldn't be that and changed it to \home\jthe and saved again
He never changed any of the settings in the Upon Save box at the bottom of the WebAdmin console and moved the contents of the entire home folder into \home\jthe and now none of the users can access their files.

We can't move their files when we log in as jthe because we don't have permission
We can't log in with our admin account because it tells us we have no home folder

How on earth do we undo this?
:confused::confused::confused:

---

### Post by coldcritter64 on 2013-04-05
Being a server, can you access a live cd and a graphical environment and fix the move that way ? That is, does the server have cd/dvd drive or even usb access for a live cd/usb installer and peripherals like a monitor, keyboard etc ? The live cd/usb is for accessing only ("Try Ubuntu" option) not for installation. Or is the server accessed remotely only ?

Should be relatively easy to reverse the changes and check permissions and ownership etc from a live cd if your setup has such access.

---

