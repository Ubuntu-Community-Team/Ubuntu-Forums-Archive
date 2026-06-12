---
title: "how to setup counter-strike with wine"
date: 2006-04-12
forum: Outdated Tutorials &amp; Tips
---

### Post by ice.man on 2006-04-12
Get the Ubuntu .deb from the wine sourceforge site, [http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803) (wine_0.9.7-winehq-1_i386.deb)

sudo dpkg -i wine_0.9.7-winehq-1_i386.deb to install wine.

then type winecfg and just close the window

Then change directory to the program files directory:
cd .wine/drive_c/Program\ Files/
(Well to download the file you would type:
wget [http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz](http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz)


Now to extract it:
tar xvzf mozcontrol.tgz

Now change directory tot he mozcontrol folder:
cd mozcontrol

Then type the regsv32 command to register the dll with wine:
regsvr32 mozctlx.dll

Install tahoma.ttf from either a windows installation, or download from the net.

how to install tahoma.ttf home your file browser and press Ctrl + h and u will see all these files “.” in front of them now make a folder called fonts with the “.” in front of it now copy/past your tahoma.ttf in there and close it.

(Alternatively you can right-click the username input box and it will give you keyboard focus. In this case you can skip steps 5-7)

Run winecfg as user, select the Graphics tab, then check "Emulate a virtual desktop". Select at least a 1024x768 desktop size and click Apply. Close the app.
Install Steam with steaminstall.exe from the Steampowered website. When it asks for your username and password, close the application.

 Start Steam.exe from .wine/drive_c/Program Files/Steam/. After entering your username and password, make SURE that "Remember my username and password" is checked. 

You cannot enter your username or password when Wine is not running with an emulated desktop, so it must remember them now, before we switch that setting back.

Click OK, close the HTML window that pops up by clicking the X at the top. The Close button at the bottom does not work. Close the app.

Return to winecfg and uncheck "Emulate a virtual desktop". Apply and exit the app.

Your steam install is now complete.

JUST DON'T UPDATE WINE!!!!!!

---

