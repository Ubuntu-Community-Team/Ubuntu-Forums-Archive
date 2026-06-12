---
title: "ultimate gos"
date: 2008-04-06
forum: Other OS Talk
---

### Post by iamclueless on 2008-04-06
anyone else play with it?

i finally managed to get the torrent file. played with the Live CD... really liked it.

Did the full install.  but got into problems... once you create a new account... the settings on new user revert back to regular GOS rocket.

it seems all the setting changes from GOS rocket to Ultimate GOS is localised to the live cd account/user.

:(

unfortunte. 

question is... is there a way i can make the changed settings the base setting for ALL users?

thanks

---

### Post by Ptero-4 on 2008-04-10
Open the liveCD with reconstructor, then click the "terminal" (dunno the name, but it's got like a gnome-terminal icon) button and in the xterm window copy all the hidden files and folders from the liveCD account's home folder to the /etc/skel folder and change the permissions to root (use chown root:root filename and chown -R root:root foldername) then let reconstructor rebuild the iso and burn the new iso.

---

### Post by wannadumpwindows on 2008-04-10
P-tero4: I dig the sig! 

P.S. I also avoid the noid . . . . .

---

