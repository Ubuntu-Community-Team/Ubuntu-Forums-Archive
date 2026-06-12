---
title: "How to install TWLOG ham logging program"
date: 2006-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by DaveRowell on 2006-07-06
This is how I finally managed to get TWLOG running correctly on Ubuntu Dapper.  I've included some directions for those a little uncertain about Ubuntu - feel free to ignore then if you know what you're doing.

1 - Install twlog using Synaptic
*Select "System-Administration-Synaptic Package Manager" - enter password - scroll through the "Amateur Radio (universe)" menu to find twlog - click the square block left of the name - click Mark for Installation - click Apply on upper toolbar - follow the prompts - yada, yada, yada*

2 - Create a folder for Twlog in your Home Folder
*Select "Places-Home Folder" - select "File-Create Folder" - name the folder - Enter*

3 - Copy /usr/share/twlog/twlogHelp to your Twlog Folder (yes the cap. H is right)
*Select "Places-Computer" - select "Filesystem" - navigate to /usr/share/twlog - select "twlogHelp" - select "Edit-Copy" - return to your Twlog Folder - select "Edit-Paste"*

4 - Create an empty file in your Twlog Folder named "logfile"
*Select "Places-Home Folder" - open your Twlog Folder - select "File-Create Document-Empty File" - give the new file a name of "logfile" - Enter*

5 - As root edit /etx/X11/app-defaults/Twlog to change Twlog.dirpath to reflect your Twlog Folder.  
*One way to edit Twlog is to open a terminal window and type "sudo gedit /etc/X11/app-defaults/Twlog" - [enter] - [password] - Twlog.dirpath is on about line 19, the lines under the LOG FILE heading tell what to edit - don't forget to remove the "!" from the beginning of the line and add it to the line above - save Twlog - exit Gedit - exit the terminal.*

6a - You can run Twlog by opening a terminal and issuing the command "/usr/X11R6/bin/twlog"
OR
6b - You can add Twlog to one of the Applications menus using Alacarte.  *Select the menu - click File-New Entry - enter Twlog for a name - browse to the path above for the program executable - click icon and browse to /usr/X11R6/include/X11/pixmaps - click Open - choose an icon - click OK - click close*

Run Twlog and have a look through the Help file.  The discussion of the Resource file may give you ideas - you may want to edit the file again.  Step 5 above will show noobs how to do that.

(-: Nice simple logging program that works like a charm! ;-)

---

### Post by lostcity on 2006-09-03
Where do you find the Amateur Radio universe.  The Synaptic Package manager I have does not list it?  

Thanks

---

### Post by marfew on 2006-11-28
What bands do you work? I would like a schedule to discuss Ubuntu
My call is W4FFL,Winter Park,Fl.
email: [email]marfew@gmail.com[/email]
Please reply by email. Thanks,
Mark Few

---

