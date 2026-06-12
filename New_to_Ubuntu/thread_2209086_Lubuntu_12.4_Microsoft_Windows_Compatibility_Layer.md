---
title: "Lubuntu 12.4 Microsoft Windows Compatibility Layer question"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by ra7411 on 2014-03-03
I need to see if I can run an MS exe program under Microsoft Windows Compatibility Layer.
I'm pretty sure I installed "wine" a few days ago in the course of setting up this o/s, but I have no idea how to find the Microsoft Windows Compatibility Layer and get it running.
The only references I've searched up seem to refering to a full ubuntu install, versus my Lubuntu version.

How do I get this done?

Thanks

---

### Post by Vladlenin5000 on 2014-03-03
You don't need to run it in the strict sense. It is run whenever you try to install or run a Windows software.

---

### Post by ra7411 on 2014-03-03
It tried to open it, but failed. It's a fsekrit encrypted exe file that asks for a password to decrypt with. Win 8.1 (64bit) says it can't open it because it's 16 bit. I was hoping this old 32 bit laptop w/ Lubuntu could get it done. 

Archive:  /home/ra/Documents/config.exe
[/home/ra/Documents/config.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/ra/Documents/config.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/ra/Documents/config.exe or
          /home/ra/Documents/config.exe.zip, and cannot find /home/ra/Documents/config.exe.ZIP, period.

Any ideas?

---

### Post by Mark Phelps on 2014-03-04
You could try invoking it through Wine as in: > wine  /home/ra/Documents/config.exe

---

### Post by grahammechanical on 2014-03-04
When we install wine we get 4 components. 1) Browse C: Drive. 2) Configure Wine. 3) Notepad and 4) Uninstall Wine Software. Look in the menu system for Unistall Wine Software. Once you load that you should see a Windows type Add/Remove Programs dialog with an Install button which will bring you to a Windows Explorer type dialog that will let you browse to the location of the exe file.

Regards.

---

### Post by monkeybrain20122 on 2014-03-04
> **ra7411 said:**
> It tried to open it, but failed. It's a fsekrit encrypted exe file that asks for a password to decrypt with. Win 8.1 (64bit) says it can't open it because it's 16 bit. I was hoping this old 32 bit laptop w/ Lubuntu could get it done. 

Archive:  /home/ra/Documents/config.exe
[/home/ra/Documents/config.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/ra/Documents/config.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/ra/Documents/config.exe or
          /home/ra/Documents/config.exe.zip, and cannot find /home/ra/Documents/config.exe.ZIP, period.

Any ideas?
 
Sounds like you have the wrong file association.

Right click it, in properties choose something like Properties > Open with and choose "Wine Windows Program Loader" then set it to be the default ( I don't have lubuntu but in pcmanfm, which is lubuntu's file manager, I am sure there is something similar)

---

### Post by ra7411 on 2014-03-04
No luck.

ra@ubuntuRA:~$ wine/home/ra/Documents/config.exe
bash: wine/home/ra/Documents/config.exe: No such file or directory
ra@ubuntuRA:~$

---

### Post by mörgæs on 2014-03-04
Lubuntu 12.04 is out of support. 
You might avoid a lot of problems by installing the supported version, 13.10. Among other improvements you will get an updated Wine.

---

### Post by monkeybrain20122 on 2014-03-04
> **ra7411 said:**
> No luck.

ra@ubuntuRA:~$ wine/home/ra/Documents/config.exe
bash: wine/home/ra/Documents/config.exe: No such file or directory
ra@ubuntuRA:~$

There should be a space between wine and /home/ra/Documents/config.exe

But as I said you can reset the file association for config.exe then right clicking it should start the .exe

+1 to lubuntu 12.04 is not supported. But you can try working this out before you get a newer version.

---

### Post by ra7411 on 2014-03-04
Using the terminal gives me file "home/ra/documents/config.exe" doesn't exist.

I tried using open with "wine windows program loader" and kept getting "bad format"

Using open with "winetricks" yields an empty win notepad.

---

### Post by monkeybrain20122 on 2014-03-04
Where did you get the .exe file? Winetricks is not for running Windows programs, it is for installing Windows components like .dlls.

---

### Post by oldos2er on 2014-03-04
The terminal is case-sensitive, so you'd need to use ```
wine /home/ra/Documents/config.exe
``` as Mark Phelps suggested.

---

### Post by ra7411 on 2014-03-04
> **monkeybrain20122 said:**
> There should be a space between wine and /home/ra/Documents/config.exe

ok.
ra@ubuntuRA:~$ wine /home/ra/documents/config.exe
wine: Bad EXE format for Z:\home\ra\documents\config.exe.

Is the "bad exe format" due to it being 16 bit?

>But as I said you can reset the file association for config.exe then right clicking it should start the .exe

I did spend some time testing different  file assns. and "open withs" - no luck. 

>+1 to lubuntu 12.04 is not supported. But you can try working this out before you get a newer version.

ok

---

### Post by Mark Phelps on 2014-03-05
Have you actually tried running this exe file in MS Windows to confirm it works? 

Also, be sure to pay attention to the upper-case "D" in Documents -- not sure you noticed that in Linux, commands are case-sensitive.

Also, Wine does not run everything that is a Windows  .exe file, far from it.  So, there is the distinct possibility that Wine simply won't execute this

---

