---
title: "OpenOffice 3.2.1 Installation - GB Localisation"
date: 2010-06-10
forum: Outdated Tutorials &amp; Tips
---

### Post by scouser73 on 2010-06-10
Firstly, go to the OpenOffice website: [http://download.openoffice.org/](http://download.openoffice.org/) and download the Linux **.deb** file to your desktop

Once you have done that, right click on the file and select **Extract**

Then you'll see a file called **OOO320_m18_native_packed-1_en-GB.9502**

Remove the existing version of OpenOffice with this command: 

**> sudo apt-get remove openoffice*.***

Then paste this command:

**> sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-GB.9502/DEBS/*.deb**

Then paste this command: 

**> sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-GB.9502/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9502_all.deb**

Once you've done that you'll find OpenOffice 3.2.1 in Office.

---

