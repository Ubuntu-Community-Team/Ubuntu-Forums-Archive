---
title: "how do i install tvants?"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by natedogg23 on 2008-09-17
ive downloaded it but cant find how to install. ubuntu is new to me

---

### Post by aloshbennett on 2008-09-17
What kind of file is it?
If it's a .deb, you could install by double clicking.
If its any of the archives (.tar, .tar.bz, .tar.gz) you have to extract and see what is inside.

---

### Post by crazypenguin2008 on 2008-09-17
do you have wine installed? you have to have wine to run tvants i do belive

---

### Post by prshah on 2008-09-17
> **natedogg23 said:**
> ive downloaded it but cant find how to install. ubuntu is new to me

> **aloshbennett said:**
> What kind of file is it?


> **crazypenguin2008 said:**
> do you have wine installed? you have to have wine to run tvants i do belive

tvants is a Windows application. As suggested, you need to use WINE to run it in ubuntu. To get WINE, open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo apt-get install wine vlc
``` It will download and install wine (if it doesn't you need to enable "universe / multiverse" in System-Preferences-Software Sources)

Once downloaded and installed, you can close the terminal, browse to the downloaded file, right-click it, and choose "Open with another application", and then, in the list that comes up, choose "WINE Windows program loader".

Note that while tvants is rated as gold on [WINE's appdb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4603") you need vlc to actually view the streams, the address for which you have to get from the tvants player, which is why I've also had you install vlc in the first command.

Post back if you run into difficulties.

---

### Post by natedogg23 on 2008-09-17
ive tried double clicking but nothing happens. i also downloaded sopcast with the same results. tried opening it with media player but nothing there either. is there a different program to watch free tv with i should be using with ubuntu? didnt have wine. thanks guys i think tvants is junk! nothing but bad request pages

---

