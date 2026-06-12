---
title: "connecting my laptop to windows local network"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by macvr on 2008-08-21
hi,i'm new to ubuntu[and a huge linux noob]

when i first used ubuntu, it listed my local windows network [i connect to the web via a router, which also has connects a desktop], and i was able to view shared files on the desktop...

but after that once i am not able to find the local network nor am i able to list the desktop....

i'm not sure what i have done , or how do i bring it back?[want to interact with that other desktop, the printer is connected to the desktop]

i searched for network sharing, and found SAMBA, but i was able to interact with the desktop before installing samba[isnt samba to make the laptop a network, if so i dont need it right?]

simplifying my babble>i dont know how to connect to the desktop as before,
need to share printer, how?

thanx in advance guys...

---

### Post by sherin on 2008-08-21
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by tarps87 on 2008-08-21
Samba allows you to talk to windows networks, it uses the same protocol as windows pc's so will allow you to see their shared folders and share your own folders with windows pc's.
open up add programs and search for samba, at the top of the list will be a nice simple gui for managing samba shares, install this (its should install samba if it is not already there).
It you get stuck just post back and I will try to help

---

### Post by macvr on 2008-08-21
hi, previously after not being able to connect i had _gsambad _installed[since it had the gnome icon in the listing], now i have removed it and installed _samba_

but i get this error initially , but when i close the warning the GUI opens
should i just ignore this error...

PS: BUT how come that i was able to previously interact with the windows desktop  without samba?

---

### Post by tarps87 on 2008-08-21
Try renaming the smb.conf file to something like smb.conf.bck, then open samba, this should make a new smb.conf file but if it doesn't rename the smb.conf.bck to smb.conf
I don't know about previously, I can only assume samba was installed by something else. Maybe someone else will be able to explain this

---

### Post by macvr on 2008-08-21
nope renaming didnt create a new config file... samba wouldnt start...

so restored the file...

what if i remove the line "_49: 	enable spoolss = yes_" which is displayed as the error, from the config???

would it mess it up?

---

### Post by tarps87 on 2008-08-21
Try commenting out the line:
#49: enable spoolss = yes
should work

---

### Post by tarps87 on 2008-08-21
I think it is to do with printing to an windows nt pc
Try running:```

testparm
```
this should test your samba config for any errors

---

### Post by macvr on 2008-08-21
ok did that commenting , and now i dont get the error warning...

now that i have done that what have i turned off? what is that setting... just since this is going to allow others to connect, acting a little paranoid

---

### Post by macvr on 2008-08-21
> **tarps87 said:**
> I think it is to do with printing to an windows nt pc
Try running:```

testparm
```
this should test your samba config for any errors

for this i get
```
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE

```

is this ok?

---

### Post by tarps87 on 2008-08-21
That's fine, it just telling you that there are some names over 12 characters that older os may not be able to see. The only way someone can connect is if you right click on a folder and click share. Using the samba gui you can set the users and their passwords for each file share. Samba enable file sharing but you tell it which on to share, its basically the same concept as on windows in terms of what the user does.
All I can find out about the line:
enable spoolss = yes
is linked to sharing printers on an windows NT pc

---

