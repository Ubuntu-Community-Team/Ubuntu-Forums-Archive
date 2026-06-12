---
title: "How to install tar.gz &amp; tar.bz files"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by ctoaun on 2008-10-15
I forgot how to install tar.gz files, and I've yet to find a useful post. I would appreciate help. Together, I know that we can create a useful post. Thanks in advance.

This why people get frustrated, bad directions.
Here are the directions
===========================================================================

cd Desktop/filename

This was good. It worked.
============================================================================
Now the directions become useless. See below.

./configure
make
sudo make install

Obviously, a filename (maybe a file path as well?) would factor into the above directions. However, nothing is specified. Therefore if the above bad commands are typed into the terminal, nothing happens beyond wasting someone's time. 
=================================================================================================================

If instructions are properly formatted and accurate, all one has to do copy and paste the commands into a terminal and then copy the file name & or file path, as appropriate, into the commands. I've seen this work and I've never been able to navigate back to that website.

Can someone please provide clarity?

---

### Post by MattThLinuxNewb on 2008-10-15
Could you be more specific as to what you're trying to install? You probably need to extract the contents of your tar.gz/tar.bz file into a folder first before compiling/installing it. Try this:
1. Open a new console window
2. Navigate to the directory where your archive is located, e.g.
```
cd ~/Desktop
```
3. Extract the contents of the archive to a new directory with the same name as the archive. e.g. if your archive is called 'archive':
```
tar -xjf archive.tar.bz2 archive
```
4. Navigate to the new directory containing the contents of the archive:
```
cd archive
```
5. From the looks of it, the archive is the source files for some application. So run the commands you were given:
```
./configure
make
sudo make install
```

Hope this helps, tell me if you run into any problems.

Matt

---

### Post by louieb on 2008-10-15
There is no one answer to your question.
A tar file is just an archive or collection of files.  Installation will depend on the content of the file.

[LIST]
[*]They could be source code that you need to compile.
[*]Or they could be compiled binary files.
[/LIST]
Anyway if you click the file in Nautilus It will open in the archive manager - this is a win-zip type of program.  There should be some sort of read me file that will tell you how to install the software. 

The extension  .gz (gunzip) or .bz (bzip) tells you the compression type.

---

### Post by lametike on 2008-10-15
i saw that the archive manager can work better than typing commands,especially for starters

---

### Post by irunwithknives on 2008-10-15
i have a problem

when i type the "make" command, it gives me 
```
make: *** No targets specified and no makefile found.  Stop.
```

what can i do here

Edit:keep in mind i have already done all of the previous steps, spent like an hour installing dependencies and dependencies for the dependencies, and then run the
```
 ./configure 
```

---

### Post by SunnyRabbiera on 2008-10-15
well maybe its something you wont need to compile, can you tell us the package you are trying to install>
It might be something you can install in the repositories

---

### Post by irunwithknives on 2008-10-15
im trying to install the global menu applet
its not in the repositories i dont think

---

### Post by ctoaun on 2008-10-15
> **MattThLinuxNewb said:**
> Could you be more specific as to what you're trying to install? 

 Yes I can specify. The file has changed please see below. 
Either you do a lot of fast typing or your response took awhile, which is appreciated.

> **MattThLinuxNewb said:**
>  So run the commands you were given:
```
./configure
make
sudo make install
```

Hope this helps, tell me if you run into any problems.

Matt

Commands like these are worthless. They never come with a file path or a file name. They are never part of examples or numbered steps, lots of room for failure. This is why I originally said that they were bad.



> **louieb said:**
> There is no one answer to your question.
A tar file is just an archive or collection of files.  Installation will depend on the content of the file.



**[SIZE="4"]The tar file in question along with the install instructions:[/SIZE]**

Found the install file by mistake. The extracted folder & the original tar.gz file aresitting on my desktop

 Mac4Lin_v1.0_RC.tar.gz 


#!/bin/sh

echo "*************************************"
echo "  Welcome to Mac4Lin v1.0 Installer  "
echo "*************************************"
echo
echo
echo

echo "Installing Mac4Lin UI..."
tar -xzf GTK/Mac4Lin_GTK_v1.0_RC.tar.gz -C ~/.themes/
tar -xzf GTK/Mac4Lin_GTK_Graphite_v1.0_RC.tar.gz -C ~/.themes/
tar -xzf GTK/Mac4Lin_MacMenu_v1.0_RC.tar.gz -C ~/.themes/
tar -xzf GTK/Mac4Lin_MacMenu_Graphite_v1.0_RC.tar.gz -C ~/.themes/
tar -xzf GTK/Mac4Lin_Meta_v1.0_RC.tar.gz -C ~/.themes/

gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme "Mac4Lin_GTK_v1.0_RC"
gconftool-2 --type string --set /apps/metacity/general/theme "Mac4Lin_GTK_v1.0_RC"
gconftool-2 --set /apps/metacity/general/button_layout --type string "close,minimize,maximize:menu"
gconftool-2 --type boolean --set /desktop/gnome/interface/menus_have_icons "true"
gconftool-2 --type string --set /desktop/gnome/interface/toolbar_style "icons"

echo "Done!"
echo 



This is a part of it, but I feel that I can work my way through the rest of it if I can succeed with this.

Thanks

---

