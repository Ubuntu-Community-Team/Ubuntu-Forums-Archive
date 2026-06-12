---
title: "Problem opening iMindMap"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by leedsal on 2012-01-12
Hi,
I'm new to Ubuntu (running 11.10) and I must admit it's been a bit of a struggle so far. At present I'm trying to open a free trial of iMindMap. The program won't open and I get a 1028 error message. I have contacted the iMindMap support centre and they sent the following reply:

[COLOR="Red"]The simplest resolution to this issue is to run iMindMap as an
administrator (from the Terminal either su or sudo iMindMap). 

If this does not resolve the issue it is likely that your user does
not have permissions to write to the neccessary locations, please run
the following commands to create the neccessary locations: 

mkdir -m 777 /usr/share/ThinkBuzan
[/COLOR]
Could anyone explain (in simple terms!!) how I do this?
Many thanks

---

### Post by Salbono on 2012-01-23
Hi leedsal,
I would also like to try iMindMap but can't seem to even get it  installed. Did you have issues with the install? Were you able to get it operate?
 
Thanks,

---

### Post by Salbono on 2012-02-04
I was able to install and run iMindMap in Ubuntu.

After extracting the file right click and the new file and goto properties. There you will find a tab with e check box you need to check that will allow the the file to run as an executable file. Check it, close the window then double click on the file. This allowed the program to install but it still wold not run. There seems to be an issue with Ubuntu not allowing programs to make changes to the file system. There is no dialog box it just doesn't make it. I seem to be having the same issue with MythTv and Wingware (tutorial files). anyways you may have to make the directory files yourself from a command line (like the old DOS). It is easy and you can find what to type (the code) here. Well can't seem to locate the link nut there is a youtube video showing the Ubuntu screen.
Best of luck

You may also try Xmind, it pretty good too.

This is the reply I received for Buzzan...
[FONT=Candara, Verdana, Arial, Helvetica][SIZE=3]Before you can  run the file you'll need to change its permissions, to do this you can  right click the file and go to properties then choose the premissions  tab.
From here you should be able to see a checkbox which says 'Execute', if  you check this box and close the properties window you'll be able to run  the installer file by double clicking it.

Once you have installed iMindMap 5 you'll need to do the same thing on the file called 'iMindMap.desktop'.
This file will be located in the installation directory (usually a subfolder called 'iMindMap5' found in your home folder).
You can move the iMindMap.desktop file to your desktop if you wish to  have easy access to the program, and after changing its permissions you  can double click it to run iMindMap 5.[/SIZE][/FONT]

---

