---
title: "Error update"
date: 2019-05-07
forum: New to Ubuntu
---

### Post by richoandika on 2019-05-07
```
richoandika@hp:~$ sudo apt update
Hit:1 http://packages.microsoft.com/repos/vscode stable InRelease
Hit:2 http://linux.teamviewer.com/deb stable InRelease                         
Hit:3 http://archive.ubuntu.com/ubuntu bionic InRelease                        
Hit:4 http://ppa.launchpad.net/bluetooth/bluez/ubuntu bionic InRelease   
Hit:5 http://ppa.launchpad.net/bovender/bovender/ubuntu bionic InRelease 
Hit:6 http://archive.ubuntu.com/ubuntu bionic-updates InRelease          
Hit:7 http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic InRelease
Hit:8 http://archive.ubuntu.com/ubuntu bionic-backports InRelease        
Ign:9 http://ppa.launchpad.net/trebelnik-stefina/ubuntu-tweak/ubuntu bionic InRelease
Hit:10 http://archive.ubuntu.com/ubuntu bionic-security InRelease
Hit:11 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease
Hit:12 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic InRelease
Err:13 http://ppa.launchpad.net/trebelnik-stefina/ubuntu-tweak/ubuntu bionic Release
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/trebelnik-stefina/ubuntu-tweak/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
richoandika@hp:~$

```
Somebody help me

---

### Post by Holger_Gehrke on 2019-05-07
The Ubuntu-Tweak PPA doesn't have any packages for distributions newer than 17.10, so it has no Release file for 18.04. Remove that PPA from your sources and everything should be good again.

Holger

---

### Post by richoandika on 2019-05-07
How to fix that using terminal

---

### Post by Impavidus on 2019-05-07
Search in /etc/apt/sources.list and the files in /etc/apt/sources.list.d/ for lines containing ubuntu-tweak. Delete those lines. If the resulting file only contains empty lines or comments, delete it. Use a terminal-based text editor.

---

### Post by deadflowr on 2019-05-07
To remove simply reverse course and use the remove  (-r) option like so
```
sudo add-apt-repository -r ppa:trebelnik-stefina/ubuntu-tweak
```
Then run
```
sudo apt update
```

---

### Post by richoandika on 2019-05-07
```

richoandika@hp:~$ sudo apt update && sudo apt upgrade
Hit:1 http://packages.microsoft.com/repos/vscode stable InRelease
Hit:2 http://linux.teamviewer.com/deb stable InRelease                   
Hit:3 http://ppa.launchpad.net/bluetooth/bluez/ubuntu bionic InRelease   
Hit:4 http://archive.ubuntu.com/ubuntu bionic InRelease                  
Hit:5 http://ppa.launchpad.net/bovender/bovender/ubuntu bionic InRelease 
Hit:6 http://archive.ubuntu.com/ubuntu bionic-updates InRelease          
Hit:7 http://archive.ubuntu.com/ubuntu bionic-backports InRelease        
Hit:8 http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic InRelease
Hit:9 http://archive.ubuntu.com/ubuntu bionic-security InRelease         
Hit:10 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease
Hit:11 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic InRelease
Reading package lists... Done 
Building dependency tree       
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  openjdk-11-jdk openjdk-11-jdk-headless openjdk-11-jre openjdk-11-jre-headless
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
richoandika@hp:~$ sudo apt list --upgradable
Listing... Done
openjdk-11-jdk/bionic-updates,bionic-security 11.0.2+9-3ubuntu1~18.04.3 amd64 [upgradable from: 10.0.2+13-1ubuntu0.18.04.4]
openjdk-11-jdk-headless/bionic-updates,bionic-security 11.0.2+9-3ubuntu1~18.04.3 amd64 [upgradable from: 10.0.2+13-1ubuntu0.18.04.4]
openjdk-11-jre/bionic-updates,bionic-security 11.0.2+9-3ubuntu1~18.04.3 amd64 [upgradable from: 10.0.2+13-1ubuntu0.18.04.4]
openjdk-11-jre-headless/bionic-updates,bionic-security 11.0.2+9-3ubuntu1~18.04.3 amd64 [upgradable from: 10.0.2+13-1ubuntu0.18.04.4]
richoandika@hp:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  openjdk-11-jdk openjdk-11-jdk-headless openjdk-11-jre openjdk-11-jre-headless
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
richoandika@hp:~$ 

```
why now?

---

### Post by deadflowr on 2019-05-07
Much like the older apt-get upgrade, apt upgrade has a few caveats that require a more wider approach.
Try
```
sudo apt full-upgrade
```

man apt (upgrade:
> upgrade (apt-get(8))
           upgrade is used to install available upgrades of all packages
           currently installed on the system from the sources configured via
           sources.list(5). New packages will be installed if required to
           satisfy dependencies, but existing packages will never be removed.
           If an upgrade for a package requires the removal of an installed
           package the upgrade for this package isn't performed.


man apt (full-upgrade:
> full-upgrade (apt-get(8))
           full-upgrade performs the function of upgrade but will remove
           currently installed packages if this is needed to upgrade the
           system as a whole.

---

### Post by richoandika on 2019-05-09
```

richoandika@hp:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  openjdk-11-jdk openjdk-11-jdk-headless openjdk-11-jre
  openjdk-11-jre-headless
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
richoandika@hp:~$ 

```
Still not upgrade

---

### Post by oldrocker99 on 2019-05-09
It is, for newbies, a lot easier to open Software and Updates, hit the second tab, and look for the URL of the PPA. Uncheck that, enter your password, and you'll be able to update without an error message.

---

### Post by deadflowr on 2019-05-09
Couple options to try from here:
[https://askubuntu.com/questions/601/the-following-packages-have-been-kept-back-why-and-how-do-i-solve-it]("https://askubuntu.com/questions/601/the-following-packages-have-been-kept-back-why-and-how-do-i-solve-it")
```
sudo apt-get --with-new-pkgs upgrade
```
or 
```
sudo apt-get install openjdk-11-jdk openjdk-11-jdk-headless openjdk-11-jre openjdk-11-jre-headless
```

A third option would be to try removing the packages and reinstalling them.

---

