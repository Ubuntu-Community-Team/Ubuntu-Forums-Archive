---
title: "Wine help"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by SalsaShark on 2008-06-14
So, I'm having problems with Wine - namely that I don't know how to use it at all.

I want to install civilization 4 and nothing is working.  I've tried just double clicking the setup.exe and nothing happens.  I've tried using the autorun it says permission denied.  And using terminal I just get gibberish.  Any ideas?

---

### Post by icouldntfindausername on 2008-06-14
First of all, here's what you want to do:

1. Copy the content from your CD/DVD to somewhere else.
2. Open up a terminal and change directory to where you copied your CD/DVD content with this command: "cd /directory"
3. Start the setup using this command: "wine setup.exe". You should be able to follow the setup normally.
4. Once you've got it installed, open a terminal again. Change directory to where you installed your game with same command: "cd /game's directory" then run command "wine startgame.exe(or whatever the .exe file is".

If your unsure how well the game will work in wine, check out the winehq appdb: [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by SalsaShark on 2008-06-14
But what difference does it make if I run the setup from the CD or from the harddrive with the contents of the CD?

---

### Post by Joeb454 on 2008-06-14
Not all applications (this is more the case with games) will work under Wine.

Unfortunately, I've been unable to find an entry on the Wine AppDB for Civilization 4. My guess is that it probably won't work :(

If you really want to play games, I still believe that currently, you're best option is to dual-boot with Windows

---

### Post by SalsaShark on 2008-06-14
Oh yeah, I've got a dual boot already.  I'm just planning on getting a new computer and was hoping to not having to dual boot.  But if there's nothing else I can do...

---

### Post by Joeb454 on 2008-06-14
It's still the easiest way to play games. I'd dual boot if I wanted to play games on my PC.

As it happens, I triple boot, but that's a different story ;)

---

