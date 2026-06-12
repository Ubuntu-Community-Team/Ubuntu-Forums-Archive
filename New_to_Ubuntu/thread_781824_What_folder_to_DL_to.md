---
title: "What folder to DL to?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by kattman on 2008-05-04
Im trying to install my printer, using this page as a guide. [https://help.ubuntu.com/community/PrintersBrotherMfc420cn](https://help.ubuntu.com/community/PrintersBrotherMfc420cn) , But I have know idea what folder the drivers should be in! Firefox has them on my Desktop.
 
Help!!!

Kattman

---

### Post by philinux on 2008-05-04
If its a .deb file the desktop is fine just double click it when you've downloaded it.

---

### Post by SunnyRabbiera on 2008-05-04
right, as the installer works very similar to how windows .exe files are.
but if you want to avoid desktop clutter in firefox you can go to edit and to preferences and under main you will see a box with the name "save files to" next to it, just click on the "browse" button and you can select where you want to download your stuff to.
Your home folder will have your screen name on it so if your home directory is "ted" then you can just click on your "ted" folder in the side panel and click "open" and with this you can save folders to your home directory. 
Me I created a special downloads folder in my home directory, to do this you can open your home directory and create a new folder and call it "downloads" or something, this way you dont clutter up your home folder either.

---

### Post by kattman on 2008-05-04
I keep getting the "Printer Class was not found", when I right click on the "cupswrapper*****.deb" file

---

### Post by SunnyRabbiera on 2008-05-04
hmm, you should be able to just left click it and the inststaller should pop up....
let me verify, did you follow the instructions on the page you linked to?

---

### Post by kattman on 2008-05-04
This is as far as I can get

kattman@kattman-desktop:~$ sudo dpkg -i mfc420cnlpr-1.0.2-1.i386.deb
dpkg: error processing mfc420cnlpr-1.0.2-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc420cnlpr-1.0.2-1.i386.deb
kattman@kattman-desktop:~$

I dont know what to do !

---

### Post by kattman on 2008-05-05
Ok I found the prob. 
Here is the fix

# Ubuntu 8.04 does not have /usr/share/cups/model directory where our driver create a ppd file.
Please follow the instruction below when the installation failed with the message about it.

1. Uninstall the cupswrapper driver.
Command : sudo dpkg -P (driver name)

2. Create /usr/share/cups/model directory
Command : sudo mkdir /usr/share/cups/model

3. Install the cupswrapper driver
Command : sudo dpkg -i --force-all --force-architecture (driver file name)

---

