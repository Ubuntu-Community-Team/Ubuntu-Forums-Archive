---
title: "Installing with Wine (Ubuntu 11.10)"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by Anteres on 2012-01-04
Hello all,

I have just got rid of my windows and ready to use Ubuntu at its fullest.
I'm also fairly new to Ubuntu.
I have had the 10.04 version before but not for too long, and now I'm back with the 11.10,
and I found an old game I like, but it's a Windows game .exe....

Now I heard you could install such files using WINE,
and I searched it and apparently it's standard in 11.10 (correct me if mistaking) but I have
no clue on how to use it.

I want to use this now to install an old game with .exe files.
And also for another game to install Unity Web Player (which is also .exe) that hasn't succeeded to install thusfar (also tried in Wine)

Sorry if this is too much in one thing, but I thought I might ask while I'm at it...

Thanks in advance!

---

### Post by Rodney9 on 2012-01-04
PlayOnLinux is said to be much easier then Wine, it is available in the Software Centre.

> PlayOnLinux is a front-end for wine. It permits you to easily install
Windows Games  and softwares on Linux. It is advised to have a functional
internet connection.

Rodney

---

### Post by Anteres on 2012-01-04
> **Rodney9 said:**
> PlayOnLinux is said to be much easier then Wine, it is available in the Software Centre.



Rodney
Thanks, indeed this seems easier and I have set it to install
the game, but on the desktop it just shows a blank icon and it doesn't open by any means.
Do you have experience with the program or just heard about it?

Thanks!

---

### Post by dFlyer on 2012-01-04
Have you checked on the wine web page to make sure your game is supported?

---

### Post by Toz on 2012-01-04
Unity Web Player does not look promising (See: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=23917]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=23917"))

What is the name of this game that you are trying to run? You can look it up on wine's application database ([http://appdb.winehq.org]("http://appdb.winehq.org")) to see how it is rated and possibly get some information on how to get it running.

Keep in mind that wine is very hit and miss and usually requires some tinkering to get things to work (if they work at all). PlayOnLinux is a good front-end to wine. You can click the "Configure" button, select the game you are trying to run and check off "Enable Debugging" on the "General" tab to get some information as to why it isn't working.

---

### Post by Anteres on 2012-01-04
> **Toz said:**
> Unity Web Player does not look promising (See: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=23917]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=23917"))

What is the name of this game that you are trying to run? You can look it up on wine's application database ([http://appdb.winehq.org]("http://appdb.winehq.org")) to see how it is rated and possibly get some information on how to get it running.

Keep in mind that wine is very hit and miss and usually requires some tinkering to get things to work (if they work at all). PlayOnLinux is a good front-end to wine. You can click the "Configure" button, select the game you are trying to run and check off "Enable Debugging" on the "General" tab to get some information as to why it isn't working.
It's Jazz Jackrabbit.
The first version is rated Garbage on the appdb but the 2nd is rated Platinum.
I've installed via PlayOnLinux but it doesn't work but I'm not really finding how to install via Wine, this is still unknown to me in any way.

---

### Post by saneearth on 2012-01-04
Typically if a program is a .exe, you just click on it or right click on it and choose open with wine. There should be an option in the menu. Whether or not it will be fully functional is another matter.

---

### Post by Toz on 2012-01-04
Just had a look at the PlayOnLinux script to install Jazz2 ([http://www.playonlinux.com/repository/?script=411]("http://www.playonlinux.com/repository/?script=411")) and the script downloads the install files from:
> POL_SetupWindow_download "$LNG_JJ2_DL" "$TITLE" "http://www.abandonware-utopia.com/pages/telechargement/jeux/Jazz%20Jackrabbit%202.zip"
POL_SetupWindow_wait_next_signal "$LNG_INSTALL" "$TITLE"
...but that site is no longer valid - so this package will no longer work through POL until they fix the link (or allow the install from the original media).

---

