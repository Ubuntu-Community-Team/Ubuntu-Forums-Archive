---
title: "What roles are played by autorun.exe and autorun.inf in linux?"
date: 2013-09-14
forum: New to Ubuntu
---

### Post by arroy_0209 on 2013-09-14
I burned one iso file corresponding to a backup program on a dvd and then I notice that the /media has these two files: autorun.exe and autorun.inf among others. The files have only read permission but no execution permission for anybody (-r--r--r--). Can anybody please explain what roles are played by these files if I use the backup live DVD in ubuntu12.04? (I thought autorun.exe is kind of virus in windows but my idea is vague.) The file autorun.inf has contents:
```
[autorun]  
open=autorun.exe  
icon=autorun.exe,0 
label=Program_name
```

---

### Post by grahammechanical on 2013-09-14
No, you are wrong about autorun.exe being a kind of virus in Windows. It is the little program that Windows runs when it automatically loads a CD or DVD disk. And autorun.inf is a file with information in it that Windows uses when running an autorun.exe file.

After burning a Ubuntu ISO image to a DVD it will contain an autorun.inf file and instead of an autorun.exe file you will see wubi.exe. So, if you are in Windows when the DVD loads it is wubi.exe that Windows can, if you choose, load.

All those CDs and DVDs that computer magazines have been giving away for years with Windows programs on them would not load without both autorun.exe and autorun.inf. Are you sure that the backup program is for Linux? It might be for use on Windows systems.

Regards.

---

### Post by tgalati4 on 2013-09-14
The purpose of autorun in a media directory is so that it will automatically display a slideshow when put into a Windows computer.  You can do the same thing in linux, and I believe many multimedia apps just read the autorun.inf file and then play a slideshow of pictures or play a video depending on the type of media in the directory.  Nero and some other burning programs will automatically put those files on a media disk.

---

### Post by CeejRab on 2013-09-15
[**[COLOR=#000000][/COLOR]**[COLOR=#000000]Hello[/COLOR]**[COLOR=#000000] arroy_0209[/COLOR]**]("http://ubuntuforums.org/member.php?u=1330943"),

I can reassure you that autorun.exe and autorun.inf are not viruses or infected files, they are very common windows files for external devices usually.

When you buy an external HD or USB drive it may have these files on it. The exe is an executable windows file which basically says to the operating system: "hey, im an external storage device, im ready to be used!" and it shows up in the system's attached devices list. The .inf file is an information file which tells the autorun exe what to say pretty much. Sometimes the inf file has info leading to a picture that will display as the external drive's icon, what to do when plugged into the computer, etc. 

Nothing to worry about. These files are also harmless to delete, they are pretty much cosmetic for windows users, and you can delete them if they bother you. Windows will probably just put a new one there next time you plug it in, but you can either leave it there or delete it, whatever makes you happy!

All the best,

-Christian

---

### Post by squakie on 2013-09-15
autorun.inf is the key file (for windows).  It is the one windows looks for to see if it should do anything automatically when the disk is mounted in windows.  Within that file can be several options, including what program to run automatically when the disk is opened - in your example it's called autorun.exe, but it could be any windows executable.  As others have mentioned - no they aren't a problem, they are just files windows uses when it mounts the disk to automatically start a program - things like an installer when it's a software disk, for example.  For the other part of your question:  they won't do a thing in Linx.  They are purely Windows files and won't do anything in  Linux.

---

