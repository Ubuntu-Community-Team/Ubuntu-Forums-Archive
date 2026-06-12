---
title: "Cant download windows programs"
date: 2014-01-22
forum: New to Ubuntu
---

### Post by iant8565 on 2014-01-22
i previously downloaded wine and thought i could then download all the windows files i could. it started off all right,but then when i tried to open the files, Archive Manager came in and said "An error occurred while loading the archive" i have no idea what this means but its ticking me off. HELP! thanks

---

### Post by deadflowr on 2014-01-22
It's usually helpful to say what type of file you were downloading.

But that aside, If you are trying to install them then you'll need to start the wine installer program.
Open the program "wine program uninstaller".

Any downloads will be in the user(you)s home/Downloads folder.
So you'll have to navigate up in the open section.
(if that makes sense)
Sorry, it's been a while since I installed or even ran wine.

---

### Post by Ravi5kumar on 2014-01-22
I think you are opening a '.exe' file. Archive Manager is default for .exe extension. Do this:

Right click on the windows file you are trying to open and click 'open with' and choose wine.

---

### Post by EnglishElectricAndy on 2014-01-23
If you haven't got them already I'd also recommend the 'rar' and 'unrar' add-ons to Archive Manager. I found them in the Software Center.

---

### Post by 3rdalbum on 2014-01-23
> **iant8565 said:**
> i previously downloaded wine and thought i could then download all the windows files i could.

Ubuntu is not a drop-in replacement for Windows, and Wine can only run a small percentage of the programs available for Windows. **Most Windows programs do not work in Wine. Some do work but only after some tweaking.**

Wine is a last resort. You're meant to run as many native Linux programs as you can, but if there's just one or two programs on Windows that you absolutely need, then you might be able to use them with Wine.

The right-click menu method mentioned earlier should work for attempting to run those programs in Wine. If it doesn't, you can hit Control-Alt-T to open a terminal, type *wine* and press the spacebar once, then drag the Windows program to the terminal window. Click on the terminal window to bring it back to the front and then hit Enter.

---

### Post by Mark Phelps on 2014-01-23
You can save yourself a lot of unnecessary work if, before you download any Windows programs, you go to the WineHQ website (linked below) and do a search for the programs and version you want to run.  Anything not found or rated less than Gold is essentially going to be a waste of your time: [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

---

