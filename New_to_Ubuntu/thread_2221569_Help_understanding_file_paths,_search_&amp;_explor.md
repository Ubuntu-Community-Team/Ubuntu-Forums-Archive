---
title: "Help understanding file paths, search &amp; explorer"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by Shyrak on 2014-05-02
Hello,

I just started using Ubuntu 14.04 (I was previously using Windows 7) and I'm having some difficulties navigating and searching for folders/files.  

In Windows, /C: is the root for pretty much everything.  If I search or browse in /C: I can find pretty much anything I need to find.

For my Ubuntu set up it seems that "/home/shyrak" is the root for everything. (Am I correct about this???)  But there are files and folders I can't find in "/home/shyrak"  

For example, I needed to remove some files from "/home/shyrak/.playonlinux" but when I go to "/home/shyrak" there is no visible folder named "/.playonlinux".  When I click the search box and try searching for ".playonlinux" 0 results come up.  I know the folder exists because I can access it using the Terminal.  But why can't I access it from the explorer?  And why can't I find it using a search?  

Thanks in advance :)
~Shyrak

---

### Post by Bashing-om on 2014-05-02
Shyrak; Hi ! 

Lemme try and give ya a jump start.

An explanation of the linux file system, what is where and how it all hangs together:
[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)
In the liux file tree structure the 'root' of the file structure is '/' . The '/' means root, as in the 'root' of the file system. All directories/files and everything is below '/'.
The directory /home/shyrak is where all your own personal files and configurations for the applications you use are kept, 
There would be separate directories under '/home' for each user created. All other places are system directories and files. Administrator level ( linux's strong security point) to mess about with them.
As to why you do not see the '.' file; dot files are hidden files. When you want to see the dot files, in the file manager the universal shortcut key combo ctl+h will reveal them. There also is a menu selection in your file manager to do so.
As to why it does not come up using the search box - can not address that one, as I do not use that Desktop Environment and rarely use the  GUI tools.

For additional guidance please see the 2 links in my signature and let the adventure begin -> follow your curiosity and interest.

[INDENT][INDENT]my Welcome ! to out world
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2014-05-02
If you open the file manager (Files). It is the second icon from the top of the Launcher. There will be a panel to the left of the application window. At the top of the panel it will say Places and it will list, Home, Desktop, Documents, Downloads, Music, Pictures and Vidoes. They are all folders under /home. Scroll down the panel until you see Devices. Under that heading should be the partitions on the hard disk. They are designated as Volumes and given a size in GB. At the bottom of that list you will see Computer. Open computer and you will see all the folders under / (root). Go to the View menu and select Show Hidden Files or press Ctrl+H. Those hidden dot ( . ) files will appear.

Mouse-over the desktop top panel at the left and an application's menu system will appear. File, Edit, View etc.

Regards.

---

