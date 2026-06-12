---
title: "Does Eclipse IDE PORTABLE  version exist? for GNU/Linux platforms"
date: 2014-11-26
forum: Programming Talk
---

### Post by dylan0005 on 2014-11-26
Hello 

I'd like to know if there is a _portable version_ of the **Eclipse IDE** for Xubuntu, Ubuntu, Lubuntu...... just like the_ indepent Os zip_ in **Netbeans** that I can run on the system without install it.

---

### Post by Toz on 2014-11-26
Yes, you can run eclipse as a regular user without having to install it into a system directory.

Download the appropriate .tar.gz file from [eclipse.org]("http://www.eclipse.org/downloads/"), uncompress it to a location in your home folder, and run the "eclipse" executable from within there. You'll need to have java installed somewhere on your computer or alternatively, you'll need to [download it]("https://java.com/en/download/manual.jsp") and uncompress it to a location in your home directory as well. In this case you'll need to specify in the eclipse.ini file the location of java using the [-vm config directive]("https://wiki.eclipse.org/Eclipse.ini#-vm_value:_Linux_Example").

---

### Post by dylan0005 on 2014-11-28
Well, I've got to say that I didn't know that. Excellent answer I will try it.

---

### Post by dylan0005 on 2014-11-28
Hey I tried to run it guess what? I didn't work I dont know why? I placed the directory in a USB and The system doesn't allowed me to run the program even if mark the option *"run as a program"* in the_ properties_ of the file it just unmark itself then I tried to give it permission through the terminal but the same thing came out it didn't run.** Do I missing something? **

---

### Post by Toz on 2014-11-29
How is your USB key formatted? Which filesystem?

If you are planning on using this USB in just linux, then format it with ext4. If you are using it both windows and linux environments, then you'll need to do some extra work. [Here]("http://ubuntuforums.org/showthread.php?t=1914416") is some more info on how this can be accomplished.

---

### Post by dylan0005 on 2014-12-01
USB file system is Fat 32. What does have to do the filesystem format? forgive me if i ask this kind of  question but be patient to me I am new to the world of ubuntu and i don't know a bunch of things that you might do.
I read what you posted in the answer above but I saw it for ntfs... so I didn't understand that well if that works for both formats including FAT 32 obviously..

---

### Post by Toz on 2014-12-01
In a nutshell, fat32 does not support linux file permissions, which is why you can't set the file executable. There is a way to work around this and it is to set all files on the drive as executable. More information can be found [here]("http://www.psychocats.net/ubuntu/mountwindowsfstab").

Other resources: 
- [http://askubuntu.com/questions/96923/how-do-i-change-permissions-on-a-fat32-formatted-drive/96929#96929]("http://askubuntu.com/questions/96923/how-do-i-change-permissions-on-a-fat32-formatted-drive/96929#96929")
- [http://askubuntu.com/questions/268222/mount-fat32-partition-with-777-permissions]("http://askubuntu.com/questions/268222/mount-fat32-partition-with-777-permissions")

Your initial question was in regards to running eclipse without installing it. And yes its possible. The further complication here is that you want to run it on a fat32-formatted drive that, by default, does not support linux file permissions. It is possible to do, but it requires further tweaking (as noted in the links above). Personally, I don't use fat32 or ntfs anymore, and haven't in a long time, so I'm not sure I can offer more assistance on this manner. IMO, if you are only going to use this USB key on linux, then format it ext4 and don't look back. If you want to use it on Windows-based machines as well, then you'll need to do some further tweaking and experimenting to get it to work. If you wish to pursue this, perhaps it would be best to create a new thread asking for assistance in making a fat32 drive capable of executing linux executables.

---

### Post by dylan0005 on 2014-12-04
Well, it's great, as you said, you answered my question. Sorry for the extra information regarding all this USB thing.
Anyway now I think I can understand more about it. Thanks for your help, I truly appreciate it.

---

