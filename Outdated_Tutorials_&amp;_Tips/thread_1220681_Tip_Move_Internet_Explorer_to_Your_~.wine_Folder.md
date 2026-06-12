---
title: "Tip: Move Internet Explorer to Your ~/.wine Folder"
date: 2009-07-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Nyken on 2009-07-23
**Properly Coping ies4linux to Your .Wine Folder**
 
Ies4linux installs it's own copy of Wine. This takes up a lot of space unnecesarily. So, in the interests of saving space, I played around and figured out how to safely move IE to my ~/.wine folder.
 
Heh, feels stange to say this in a Linux forum, but while you're in your .wine folder, backup your registry files -> system.reg, user.reg, & userdef.reg. 
 
First of all, you will need to rewrite your "ie6" script in your ~/.ies4linux/bin folder to read verbatim like this:
 
#!/usr/bin/env bash
# IEs 4 Linux script to run ie6 - [http://tatanka.com.br/ies4linux](http://tatanka.com.br/ies4linux)
debugPipe() {
while read line; do [ "$DEBUG" = "true" ] && echo $line; done
}
cd
export WINEPREFIX="/home/nyken/.wine/"
if [ -f "/home/nyken/.wine/.firstrun" ]; then
rm "/home/nyken/.wine/.firstrun"
( wine "/home/nyken/.wine/drive_c/Program Files/Internet Explorer/IEXPLORE.EXE" "[http://www.tatanka.com.br/ies4linux/startpage?lang=enUS&ieversion=ie6&firstrun=true](http://www.tatanka.com.br/ies4linux/startpage?lang=enUS&ieversion=ie6&firstrun=true)" 2>&1 ) | debugPipe
else
( wine "/home/nyken/.wine/drive_c/Program Files/Internet Explorer/IEXPLORE.EXE" "$@" 2>&1 ) | debugPipe
fi
 
Replace Nyken with your own user name, naturally (or maybe just add a "nyken" user account! Everyone should have one!) :D
 
Second: 
 
Save that file in your ~/.wine folder. **Do NOT make a "bin" folder for it there**. We're operating from the paths set up in the script.
 
 
Third:
 
Look into your "ie6" FOLDER. You will find a base install of Wine there. It's there to make Internet Explorer work. The files there are the versions you will need, not the ones that came with your Wine install. The Iexplore.exe you'll find there might not work. It didn't for me. 
 
So... 
 
Copy the "Program Files" folders and go to your Wine install's "drive_c" and paste them there. Chose "merge all" when Ubuntu asks. Also make sure both "Windows" folders have the same folders within. It should have at least the ones ~/.ies4linux/ie6/drive_c/windows has to be "safe."
 
Both ies4linux.png and the .svg version should be in the base of your .wine folder. The "Downloads" folder should as well. If you want to fell even safer, copy the ie6 folder to the base of your .wine directory. I figure the more fidelity the better, yeah? 
 
If you can't get IE to run under these directions, you may have to copy the registry files from your .ies4linux/ie6 folder. Not sure if this will kill or cripple some other Windows programs you may already have installed in Wine. A suggested possible solution is just to copy and paste the contents of your registry files from .ies4linux/ie6 to your .wine registry files, to give Wine the IE registry data it may need. I had no other programs installed in Wine except for EverQuest (not yet working completely) and both registries were identical, so there should be no need for any registry tweaks.
 
This works for me. I'm posting this with IE 6 after being modified as per this how-to to prove it does. 
 
Hope it works for everyone else that'd like to try this.

---

