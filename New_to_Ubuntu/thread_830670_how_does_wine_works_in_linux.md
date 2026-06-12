---
title: "how does wine works in linux?"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by branthan on 2008-06-16
Hi every 1, i just installed ubuntu in ma system and i heard of wine which will run windows programs in linux. Could some one tell me how this works and the commands used for executing this

---

### Post by iaculallad on 2008-06-16
Try visiting [WinE's FAQ page]("http://wiki.winehq.org/FAQ").

---

### Post by djdarrin91 on 2008-06-16
I have found wine very easy to use,and i've really never used any commands.only problem i've had with wine was uninstalling programs,it would uninstall but the program would still be there.but i did find a fix for that.Press "Alt+F2" to open up the Run App bar and copy in:


nautilus ~/.local/share/applications/wine

All your wine menu entries are in that folder.just delete what you don't want:)
Hope that helps ya in some way. Good luck

---

### Post by FruitieX on 2008-06-16
Once you got Wine installed with "sudo apt-get install wine", you should be able to run Windows executeables by right clicking them in the file-manager and choosing "Open with Wine".

Edit: If nothing happens you can try opening a terminal and typing:

"wine /path/to.exe"

to get some output on why it doesn't work. Maybe some DLL's are missing? :)

---

### Post by nowshining on 2008-06-16
or u can set-it up to launch the exe when double-clicking, etc... or it should do that by default. Note: Not all apps will run - WINE is still a work in progress and wine 1.0 should be released soon officially.

---

