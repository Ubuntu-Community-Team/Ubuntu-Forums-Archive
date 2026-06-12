---
title: "Make a dock icon from a desktop shortcut (18.04 LTS)"
date: 2018-06-06
forum: New to Ubuntu
---

### Post by jrwoodward on 2018-06-06
I downloaded the 64-bit version of Seamonkey and installed it from the command line. (The default download that uses Archive Manager wouldn't run because it is a 32-bit version.) It runs fine. I created a Gnome Desktop Shortcut file for Seamonkey, and it, too, runs fine. However, when Seamonkey is running and the icon is in the dock, I can't get it to pin to the Dock. Thanks to Tweaks, I have a way to right-click now on my Lenovo netbook touchpad, but all a right click does is bring up two options: "All windows" and "Quit." Is there a way to make a Dock shortcut by hand similar to the way I made the .Desktop file? If this is basic Ubuntu/Gnome wisdom, please forgive me, but I couldn't find anything on Google.

---

### Post by vanadium on 2018-06-06
Strange. A dock item, aka, a favourite, is based on a .desktop file. Normal behaviour in Ubuntu 18.04, and also in plain Gnome Shell, is to right-click the icon while the programme is running, then select  "Add to favorites". Can you start Seamonkey through the application menu? Is your desktop file present in one of the dedicated folders, i.e. /usr/share/applications or ~/.local/share/applications?

---

### Post by jrwoodward on 2018-06-06
The original instructions I used told me to put Seamonkey.Desktop in ~/Desktop, which I did. I moved the file to /usr/share/applications. I can start the program from there, but still cannot add it to the Dock/Favorites. I also, on the advise of somebody in the Seamonkey forums, add StartupWMClass=Seamonkey to the Seamonkey.Desktop script. Neither of those things worked. Is there a folder for Favorites, or some file listing the member apps? Can I copy something to a folder or edit a file to fix this? I spent some time this morning comparing .Desktop files for apps listed in Favorites with my Seamonkey.Desktop file, and did not find any lines that I could add to .Desktop to put the app in Favorites. Is this perhaps a bug I need to file with Seamonkey?

---

### Post by leunam12 on 2018-06-06
Press the SUPER key and type seamonkey, can you see the icon there? If you can see it, can you drag it to the dock?

---

### Post by andrelima175 on 2018-06-07
If you want to create a link you could use ln -s. If you want a graphical tool for it install 'alacarte' (also known as 'main menu').

sudo apt install alacarte

Then use super key, find your program and set as favorite.

---

