---
title: "How to Open a file in Dolphin, Using Kate, as root"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by GregA on 2012-01-20
On occasion, I'd like the convenience of using Dolphin to navigate to a particular file, then open the file in an editor such as Kate, make changes, and resave the file.   I'm familiar with opening any file in the Terminal Konsole using sudo, but it would save some time to open the file, right click on it, select Kate, and have the file open up with root access.

Way back in the day, it seemed this was possilbe (I recall doing it using the Xandros File Manager), but can't remember the how-details.

Thanks much.

---

### Post by pbpersson on 2012-01-20
You would want to create a new menu item, call it "Root Dolphin" and the command would be:

kdesudo dolphin

Each time you start it you will be asked for the password and you will be running dolphin with root privileges

---

### Post by mastablasta on 2012-01-20
also if it's a txt file i think you can right click it and then open as root. i think... not sure.
 
but yeah kde sudo is the sudo graphical interface.

---

### Post by oldos2er on 2012-01-20
> **GregA said:**
> On occasion, I'd like the convenience of using Dolphin to navigate to a particular file, then open the file in an editor such as Kate, make changes, and resave the file.  

You can use Root Actions Servicemenu add-on from here: [http://kde-look.org/content/show.php?content=48411](http://kde-look.org/content/show.php?content=48411)
Download the tar.gz, extract it, and run the install script installKDE4.sh
Once it's installed you'll need to log out and log back in or reboot to activate it.

---

### Post by SeijiSensei on 2012-01-20
Wow, did you abuse your moderator status there, Ann, to say you have 8,888 beans, or was I just lucky enough to read the right posting?!

---

### Post by oldos2er on 2012-01-20
You were lucky! ;)  Funny, I never pay much attention to beans anymore.

---

