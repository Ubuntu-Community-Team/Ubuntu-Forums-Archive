---
title: "If I need to reach a directory in windows..."
date: 2008-07-10
forum: New to Ubuntu
---

### Post by nullbyte0 on 2008-07-10
that has spaces in it, how do I type it in the terminal?  I've tried to cd C:\Program Files\... but the terminal stops recognizing the command at program,  I've also tried to encompass the folder in quotation marks to no avail.  Finally I tried replacing the spaces with % marks and it didn't work.

How would I do this?  I need to do so to get a game working through wine.

---

### Post by Xerp on 2008-07-10
Assuming it is mounted, and you want to use the terminal rather than the icons, you'll need to do something like this:

```
cd /media/sda1
```

Where you replace sda1 with the device used by your drive that has Microsoft Windows on it.

---

### Post by jerome1232 on 2008-07-10
if it has spaces yeah add a \ before the space
```
cd example\ with\ spaces\ in\ it/another_directory/program
```

---

### Post by fatality_uk on 2008-07-10
> **nullbyte0 said:**
> that has spaces in it, how do I type it in the terminal?  I've tried to cd C:\Program Files\... but the terminal stops recognizing the command at program,  I've also tried to encompass the folder in quotation marks to no avail.  Finally I tried replacing the spaces with % marks and it didn't work.

How would I do this?  I need to do so to get a game working through wine.

I don't think you can just access a game using WINE by navigating to it on a Windows drive or partition. Install the game in Ubuntu. Just insert the game CD and it will autoload. If you already have WINE installed, open the CD, and the right click on the start.exe or install.exe which ever exe installs the game. It should say Open With WINE and then select that.

---

### Post by nullbyte0 on 2008-07-10
Alright, I've got the program working through wine.

On a side note related to wine, is there anyway to stop the flicker that opengl programs get with the ati drivers?  I'm trying to play WoW but the game flickers too much.


edit: To the above poster, I got it working through the terminal by doing "cd /media/sda1/Program\ Files/World\ of\ Warcraft"

and then doing "wine Launcher.exe"

---

### Post by Xerp on 2008-07-10
Turn compiz (the desktop effects) off to stop the flicker.

---

### Post by nullbyte0 on 2008-07-10
Alright, so I got it running without the flicker.  

The thing is that it is really choppy, and the sites say that WoW runs beautifully through wine.  I'm wondering if there are other drivers I should be installing.  I installed the "ATI accelerated graphics driver" that was in the proprietary drivers manager.  Is there something I'm missing?

---

### Post by Xerp on 2008-07-10
Yeah, I have ATI and stuff runs smoothly. Try some tips from here:

[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

---

### Post by bodhi.zazen on 2008-07-10
Or use quotes

"path with spaces"

---

