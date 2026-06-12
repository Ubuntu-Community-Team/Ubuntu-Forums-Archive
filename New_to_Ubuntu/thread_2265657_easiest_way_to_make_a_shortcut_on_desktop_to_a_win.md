---
title: "easiest way to make a shortcut on desktop to a windows share? (CLI/script preferred)"
date: 2015-02-16
forum: New to Ubuntu
---

### Post by ben5 on 2015-02-16
What is the easiest way to make a shortcut on desktop to a windows share? (CLI/script preferred)

---

### Post by CrAzY12 on 2015-02-16
To make a shortcut on a desktop to windows share, open a folder and grab the shared folder you are interested in and simply drag and drop on the desktop. Please see screenshot.

---

### Post by ben5 on 2015-02-16
Sorry - to be clear I am looking for how to get a link on the desktop in ubuntu to a windows share.  Screenshot you posted looks like you are running win7.   Can I access a windows share in ubuntu just by typing \\servername\sharename?

---

### Post by mooreted on 2015-02-16
smb://ServerName/ShareName
smb://DOMAIN;User@ServerName/ShareName
 
I suppose you could write a desktop file. Lets suppose the folder on the Windows machine is Music

Create a text file and name it Music.desktop with the following information and save it to your desktop:

[Desktop Entry]
Name=Network(myserver)
Comment=Open ip in Nautilus
Exec=nautilus nautilus smb://Servername/Music
Icon=network
Terminal=false
Type=Application
StartupNotify=true
Categories=GNOME;
OnlyShowIn=GNOME;Unity;
X-GNOME-Keywords=Network;myserver;
Name[en_US]=blubb

You can change that to suit your needs. In Nautilus or from the command line you can make it executable and it should work.

---

### Post by ben5 on 2015-03-27
> **mooreted said:**
> smb://ServerName/ShareName
smb://DOMAIN;User@ServerName/ShareName
 
I suppose you could write a desktop file. Lets suppose the folder on the Windows machine is Music

Create a text file and name it Music.desktop with the following information and save it to your desktop:

[Desktop Entry]
Name=Network(myserver)
Comment=Open ip in Nautilus
Exec=nautilus nautilus smb://Servername/Music
Icon=network
Terminal=false
Type=Application
StartupNotify=true
Categories=GNOME;
OnlyShowIn=GNOME;Unity;
X-GNOME-Keywords=Network;myserver;
Name[en_US]=blubb

You can change that to suit your needs. In Nautilus or from the command line you can make it executable and it should work.

This works great - thanks so much!

One small point - in case anyone else copies this solution in the future the line... 
```
Exec=nautilus nautilus smb://Servername/Music
```
...should really be...
```
Exec=nautilus smb://Servername/Music
```

(i.e. only one "nautilus")

It gave me a less than informative error message so I was not sure what it was at first.

---

