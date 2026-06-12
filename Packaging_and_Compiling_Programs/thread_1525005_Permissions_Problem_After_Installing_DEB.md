---
title: "Permissions Problem After Installing DEB"
date: 2010-07-06
forum: Packaging and Compiling Programs
---

### Post by dodle on 2010-07-06
I created a new version of a project that I have been working on.  I had no problems with the previous version, but now I am having trouble accessing files in subdirectories.  

Here is what the folder tree looks like after the app is installed:
```
/usr/share/project_name
/usr/share/project_name/pic
/usr/share/project_name/sound
```

The main executable is located in "/usr/share/project_name", and needs to access files in the subdirectories "pic" and "sound".

The problem that I am having is that the permissions for the folders "pic" and "sound" are messed up after the deb is installed and the files can only be accessed if the application is run as a sudoer or root.  I am completely confused.  Other sample debs that I have made work fine, but every time I build and install this particular project the folders get messed up.  

I am using fakeroot to build the package:
```
fakeroot dpkg -b project_name
```

Any ideas why this could be happening?

**Edit:** After looking over the permissions, "Folder Access" is changed to "None" for "Group" and "Other".

---

### Post by SevenMachines on 2010-07-06
all i can think of off-hand is that files in that folder will be read-write for root and read for everyone else by default i think, when you say 'program needs to access files in pic etc..', is your program code opening them read only?

---

### Post by dodle on 2010-07-06
As far as I know it is read-only.  The files are not being opened to be edited.  Here, I will upload the deb, will someone test to see if it works on their machine?

[http://www.filesend.net/download.php?f=2a45ee6ebc2ca87ad470315923f0bb58](http://www.filesend.net/download.php?f=2a45ee6ebc2ca87ad470315923f0bb58)

It's kind of large because it contains a lot of png and wav files.  I'm going to try to switch from wav to ogg sound files so the download will be smaller.

---

### Post by SevenMachines on 2010-07-07
if its any consolation, it works fine here as normal user

---

### Post by dodle on 2010-07-07
Oh, thanks!  That is consolation.  At least I know it is my machine and not me.

**Edit:** Just as a note, it worked fine for me as well after I installed it on a new Ubuntu machine.

---

