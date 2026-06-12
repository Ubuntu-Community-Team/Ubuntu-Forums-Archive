---
title: "I plug in my Ipod and open Amarok"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by ericxhall on 2008-04-28
I click autodetect in Amarok and given the message "No new media devices were found. If you feel this is an error, ensure that the DBUS and HAL daemons are running and KDE was built with support for them. You can test this by running "dcop kded mediamanager fullList" in a Konsole window."

I ran that code but it didnt work.

---

### Post by ericxhall on 2008-04-28
bump

---

### Post by Jammin80503 on 2008-04-28
What generation iPod is it?

---

### Post by ericxhall on 2008-04-28
It's 6th Gen 80g

---

### Post by Jammin80503 on 2008-04-28
You're screwed, at least for a while. The firmware on the latest ipods is made to only work with real versions of iTunes. I havent heard anything about it being cracked to work with linux yet.

---

### Post by ericxhall on 2008-04-28
You didn't update to Hardy did you?
The newest version of Ubuntu has the libraries already installed so it works, but it just wont happen in amarok, i can use rhythmbox or gtkpod, i just want to use amarok.

---

### Post by Jammin80503 on 2008-04-28
I am running Hardy, but I didnt know it had support for the newest generation of iPods. I guess I dont know how to help, then. Sorry.

---

### Post by bfkeats on 2008-04-28
I've upgraded and amarok doesn't work. Is rhythmbox working for you in Hardy?

---

### Post by albeano2004 on 2008-04-28
This SHOULD work:
-Open Amarok (duh :))
-Click on Settings -> Configure Amarok -> Media Devices -> Add Device...
- Select 'Apple iPod Media Device' from the drop down box at the top
- Enter a name in the next box down eg 'ericxhall iPod'
- Enter the mount point. To find yours out, open the iPod in the file browser, then press ctrl + l.  On my PC, this is /media/IPOD. Not sure if this is different on yours.
- Plug in the iPod, and you should be able to read it. Click on the iPod second toolbar (above the playlist) - I had to click on the double arrow. From there you should be able to change the iPod model ('classic' in your case).
- Transfer music as normal

Hope this works out for you. The reason ```
dcop kded mediamanager fullList
``` didn't work, was that you are running GNOME, rather than KDE. That code is for KDE only :).

---

