---
title: "Where are apps stored in Ubuntu?"
date: 2014-01-01
forum: New to Ubuntu
---

### Post by ansari.ibrahim1 on 2014-01-01
I am an advanced user and want to access the files of an app. I would like to know the directories in which apps and their data are stored. If they are stored in multiple directories then you may give me all the directories in which they are stored.

---

### Post by wyliecoyoteuk on 2014-01-01
If you are an "advanced user" surely you would already know?
There are no hard and fast rules.

The easiest way I can think of using the GUI, as I expect that is what you want, is to install synaptic, then view the installed files data in the properties of a particular installed application.

If you are advanced enough to use the CLI, then:

To see all the files the package installed onto your system, do this:

dpkg-query -L <package_name>

To see the files a .deb file will install

dpkg-query -c <package_name.deb>

To see the files contained in a package NOT installed, do this once (if you haven't installed apt-file already:

sudo apt-get install apt-file
sudo apt-file update

then

apt-file list <package_name>

---

### Post by ansari.ibrahim1 on 2014-01-01
Just needed a refresh. I had forgot it, wyliecoyoteuk. By the way, thanks.

---

### Post by grahammechanical on 2014-01-01
If you are looking for an application's configuration file, then they are hidden files in the user's home folder. They are called dot files because they have a dot ( . ) at the front of the file name and that dot hides the file from File Manager unless we set the File Manager View options to Show Hidden files.

Regards.

---

### Post by oldos2er on 2014-01-01
Moved to Absolute Beginners.

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by Jonathan Precise on 2014-01-01
Apps are usually stored in:


[LIST]
[*]/usr/local/sbin
[*]/usr/local/bin
[*]/usr/sbin
[*]/usr/bin** - it is somewhat common to see applications in here**
[*]/sbin
[*]/bin
[*]/usr/games** - where games are stored**
[*]/usr/local/games** - more games**
[/LIST]

If not, they might be stored (somewhere) in /opt (normally used when building software or installing software not from **L**aunch**p**ad **P**ersonal **P**ackage **A**rchives or the standard ubuntu repositories)

---

### Post by ansari.ibrahim1 on 2014-01-16
> **Jonathan Precise said:**
> Apps are usually stored in:


[LIST]
[*]/usr/local/sbin
[*]/usr/local/bin
[*]/usr/sbin
[*]/usr/bin** - it is somewhat common to see applications in here**
[*]/sbin
[*]/bin
[*]/usr/games** - where games are stored**
[*]/usr/local/games** - more games**
[/LIST]

If not, they might be stored (somewhere) in /opt (normally used when building software or installing software not from **L**aunch**p**ad **P**ersonal **P**ackage **A**rchives or the standard ubuntu repositories)

Best answer yet! Just what I was looking for...

---

### Post by ansari.ibrahim1 on 2014-01-16
> **oldos2er said:**
> Moved to Absolute Beginners.

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

I am not a beginner...

---

### Post by oldos2er on 2014-01-16
> **ansari.ibrahim1 said:**
> I am not a beginner

Possibly not, but the question you asked is one common for beginners to ask. Also it was posted to the wrong subforum (Installation & Upgrades, if I remember correctly), so this forum seemed the best fit.

---

### Post by deadflowr on 2014-01-16
The listed bin directories above are where the various executables are usually stored.
Configuration files are more commonly found in
/etc 
/usr/share 
and /home/username/.*(the * in this case represents most of the folders that are hidden in the home folder, the most common folder the store configuration data is the .config folder, but some apps have there own, like mozilla/firefox.)
Most apps store the saved bits and pieces in the same areas.

---

### Post by ansari.ibrahim1 on 2014-01-24
> **deadflowr said:**
> The listed bin directories above are where the various executables are usually stored.
Configuration files are more commonly found in
/etc 
/usr/share 
and /home/username/.*(the * in this case represents most of the folders that are hidden in the home folder, the most common folder the store configuration data is the .config folder, but some apps have there own, like mozilla/firefox.)
Most apps store the saved bits and pieces in the same areas.
Thanks for the additional info.

---

### Post by SeijiSensei on 2014-01-24
See also: [http://ubuntuforums.org/showthread.php?t=2167982&p=12758685&viewfull=1#post12758685](http://ubuntuforums.org/showthread.php?t=2167982&p=12758685&viewfull=1#post12758685)

---

