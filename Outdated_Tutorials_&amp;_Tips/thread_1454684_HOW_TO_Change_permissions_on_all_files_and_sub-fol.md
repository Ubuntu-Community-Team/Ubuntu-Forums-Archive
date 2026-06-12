---
title: "HOW TO: Change permissions on all files and sub-folders"
date: 2010-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Francewhoa on 2010-04-15
**EDIT: Find below comment #2 for a more stable and user friendly tool**
[http://ubuntuforums.org/showpost.php?p=10012703&postcount=2](http://ubuntuforums.org/showpost.php?p=10012703&postcount=2)

---

ISSUE
Ubuntu 8.04 user interface is not yet able to change permissions on all files and sub-folders. 

WORK AROUND
Here is an easy work around for those who don't use command line.

STEPS
Installing 'PCMan File Manager' from the repositories. It's a sweet little lightweight file manager (ordinarily part of the LXDE desktop, but it's modular).

Navigate to the following Ubuntu's menu APPLICATIONS > SYSTEM TOOL > PCMAN FILE MANAGER

Navigate to the folder you want to edit the permissions. Select the folder with one left click.

Navigate to the following PCMAN FILE MANAGER's menu TOOL > OPEN CURRENT FOLDER AS ROOT. 

Navigate to the following PCMAN FILE MANAGER's menu FILE > FILE PROPERTIES

Type in the OWNER

Type in the GROUP

Choose permissions for all the files in that folder.

Make sure SET UID and SET GID boxes are checked. Find attached screenshot to clarify.
Note: UID stands for USER ID. GID stands for GROUP ID. Do not check STICKY unless you know what you're doing. 

Click on OK button.

PCMAN FILE MANAGER will ask 'Do you want to recursively apply these changes to all files and sub-folders?' This is what you want to do so click on YES button.

That's it. You have successfully changed all files and sub-folders permissions.



Source: [http://start.ubuntuforums.org/showpost.php?p=8407926&postcount=14](http://start.ubuntuforums.org/showpost.php?p=8407926&postcount=14)

Link to Ubuntu issue/confusion: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/165113](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/165113)

---

### Post by Francewhoa on 2010-10-22
**ISSUE**
Ubuntu 8.04 user interface is not yet able to change permissions on all files and sub-folders

**WORK AROUND**
Here is an easy work around for those who don't use command line

**STEPS**

[LIST]
[*] Installing *'GNOME Commander'* file manager from the repositories
[*]To clarify how to use it find below attached screenshot
[/LIST]

SOURCE: [http://www.nongnu.org/gcmd/index.html](http://www.nongnu.org/gcmd/index.html)

---

