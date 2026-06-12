---
title: "Transfer of user settings"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by quarkhirad on 2012-02-21
I have ubuntu 11.10 installed on my HP dv 6767Tx laptop. However, i have just bought a new DELL XPS 15 laptop.I installed ubuntu 11.10 on my DELL laptop but obviously the customizations that i had done in my HP laptop are not present. For example my compiz settings and extra repositories i had added to get other software are missing in my DELL laptop . What are the config files that i need to copy so that i can get the same feel in my DELL laptop. 

 Thanks

---

### Post by grahammechanical on 2012-02-21
Open the File Manager. Click on the View menu and select Show Hidden Files. Now when you open the Home folder you will see lots of so called dot folders and files. They are files and folders with a dot ( . ) at the beginning of the file/folder name.

These are the files/folders that you are looking for. 

Regards.

---

### Post by SamoNji on 2012-06-19
After copying these files, do I need to re-install every software or updates I had previously done on the old computer? 
For other personal files and folders, it possible to do a back-up of the old computer and a restore on the new, to ensure complete transfer of user files and folders?

---

### Post by mcduck on 2012-06-19
> **SamoNji said:**
> After copying these files, do I need to re-install every software or updates I had previously done on the old computer? 
For other personal files and folders, it possible to do a back-up of the old computer and a restore on the new, to ensure complete transfer of user files and folders?

Simply copying all the stuff (including hidden files) from your hokme directory will coipy all your personal files and settings.

However, it will not copy any system-wide settings, installed programs, configured software sources or other stuff that doesn't strictly belong to your user acocunt. So you will need to either add the same software sources on the new computer, or copy the relevant system config files, and then install all the programs and updates you had on the old machine.

I believe the Ubuntu Software Center has some feature to save the information about which packages you have installed, and then eaisly reinstall them on a new machine. I haven't tried that myself, though, so I can't tell how to use it or how well it works. And I assume it still won't manage any system-wide configuration files for you.

---

