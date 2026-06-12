---
title: "Help-Sorry if this is in the wong place"
date: 2020-06-17
forum: New to Ubuntu
---

### Post by kevingjames on 2020-06-17
Can I be pointed in the right direction to fix this problem

An error occurred,please run package manager from the right click menu or apt-get in a terminal to see what is wrong.
The error message was: Error:Broken Count >0'. This usually means that your installed packages have unmet dependencies.

It is stopping me from updating and removing programs

[IMG]https://drive.google.com/file/d/1tg0sPQzaW7zg8ufTl_qJnWiU0rqLaSyK/view?usp=sharing[/IMG]
[https://drive.google.com/file/d/1tg0sPQzaW7zg8ufTl_qJnWiU0rqLaSyK/view?usp=sharing](https://drive.google.com/file/d/1tg0sPQzaW7zg8ufTl_qJnWiU0rqLaSyK/view?usp=sharing)

---

### Post by deadflowr on 2020-06-17
Run
```
sudo apt update
sudo apt upgrade
```
from a terminal and post back the results.

---

### Post by kevingjames on 2020-06-17
Result

```
kevin@kevin-O-E-M:~$ sudo apt update
[sudo] password for kevin: 
Hit:1 [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) bionic InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease                     
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]   
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]    
Hit:5 [http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu](http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu) bionic InRelease        
Ign:6 [http://ppa.launchpad.net/philip5/extra/ubuntu](http://ppa.launchpad.net/philip5/extra/ubuntu) bionic InRelease           
Err:7 [http://ppa.launchpad.net/philip5/extra/ubuntu](http://ppa.launchpad.net/philip5/extra/ubuntu) bionic Release       
  404  Not Found [IP: 91.189.95.83 80]
Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]
Hit:9 [http://archive.canonical.com](http://archive.canonical.com) bionic InRelease                      
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main i386 DEP-11 Metadata [46.1 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe i386 DEP-11 Metadata [49.1 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse i386 DEP-11 Metadata [2,464 B]
Get:13 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main i386 DEP-11 Metadata [295 kB]
Get:14 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 DEP-11 Metadata [279 kB]
Get:15 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/multiverse i386 DEP-11 Metadata [2,468 B]
Get:16 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe i386 DEP-11 Metadata [7,972 B]
Reading package lists... Done                                                  
E: The repository 'http://ppa.launchpad.net/philip5/extra/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
kevin@kevin-O-E-M:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies.
 mpv : Depends: libplacebo18 (>= 1.18.0) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
kevin@kevin-O-E-M:~$
```

---

### Post by deadflowr on 2020-06-17
The philip5 extra ppa has no bionic archive so remove it
```
sudo add-apt-repository -r ppa:philip5/extra
sudo apt update
sudo apt upgrade
```
If an error still persists try
```
sudo apt install -f
```

---

### Post by kevingjames on 2020-06-17
Her are the results of trying everything suggested:-

```
kevin@kevin-O-E-M:~$ sudo add-apt-repository -r ppa:philip5/extra
[sudo] password for kevin: 
 Ubuntu experimental rolling release repository.

Mainly assorted media apps and other programs that I use myself or by requests. 
 More info: [https://launchpad.net/~philip5/+archive/ubuntu/extra](https://launchpad.net/~philip5/+archive/ubuntu/extra)
Press [ENTER] to continue or Ctrl-c to cancel removing it.
```

```
kevin@kevin-O-E-M:~$ sudo apt update
Hit:1 [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) bionic InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease                                                     
Hit:3 [http://archive.canonical.com](http://archive.canonical.com) bionic InRelease                                                            
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease                                             
Hit:5 [http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu](http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu) bionic InRelease                                        
Hit:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease                                           
Hit:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease                                     
Reading package lists... Done                                                   
Building dependency tree       
Reading state information... Done
365 packages can be upgraded. Run 'apt list --upgradable' to see them.
kevin@kevin-O-E-M:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies.
 mpv : Depends: libplacebo18 (>= 1.18.0) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
kevin@kevin-O-E-M:~$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libclamav7 libdav1d1 libdav1d2 libdav1d4 libplacebo7 linux-headers-4.15.0-55 linux-headers-4.15.0-55-generic
  linux-image-4.15.0-55-generic linux-modules-4.15.0-55-generic linux-modules-extra-4.15.0-55-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libplacebo18
The following NEW packages will be installed
  libplacebo18
0 to upgrade, 1 to newly install, 0 to remove and 365 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/139 kB of archives.
After this operation, 376 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 313974 files and directories currently installed.)
Preparing to unpack .../libplacebo18_1.18.0-1~bionic1_i386.deb ...
Unpacking libplacebo18:i386 (1.18.0-1~bionic1) ...
dpkg: error processing archive /var/cache/apt/archives/libplacebo18_1.18.0-1~bionic1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/i386-linux-gnu/libplacebo.so.18', which is also in package libplacebo7:i386 1.8.0-1~bionic
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libplacebo18_1.18.0-1~bionic1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
kevin@kevin-O-E-M:~$
```

---

### Post by deadflowr on 2020-06-17
Try
```
sudo apt autoremove
sudo apt upgrade
```
There is a conflict between libplacebo7 and libplacebo18.
But libplacebo7 is listed in the output for autoremove, so perhaps removing it will allow the installation of the newer libplacebo18 package, 
which in turn will allow the rest of the system to update.

If that still fails, then you might try the method posted here:
[https://askubuntu.com/questions/1189308/software-update-problem-libplacebo18-on-ubuntu-18-04]("https://askubuntu.com/questions/1189308/software-update-problem-libplacebo18-on-ubuntu-18-04")
Of course you'd need to change the path from

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libplacebo18_1.18.0-1~bionic1_amd64.deb
```
 to
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libplacebo18_1.18.0-1~bionic1_i386.deb
```

---

### Post by kevingjames on 2020-06-17
Tried 
```
sudo apt autoremove
sudo apt upgrade
```

and then

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libplacebo18_1.18.0-1~bionic1_i386.deb
```

this is the result

```
kevin@kevin-O-E-M:~$ sudo apt autoremove
[sudo] password for kevin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies.
 mpv : Depends: libplacebo18 (>= 1.18.0) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
kevin@kevin-O-E-M:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies.
 mpv : Depends: libplacebo18 (>= 1.18.0) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
kevin@kevin-O-E-M:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/libplacebo18_1.18.0-1~bionic1_i386.deb
(Reading database ... 313974 files and directories currently installed.)
Preparing to unpack .../libplacebo18_1.18.0-1~bionic1_i386.deb ...
Unpacking libplacebo18:i386 (1.18.0-1~bionic1) ...
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/lib/i386-linux-gnu/libplacebo.so.18', which is also in package libplacebo7:i386 1.8.0-1~bionic
Setting up libplacebo18:i386 (1.18.0-1~bionic1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
kevin@kevin-O-E-M:~$
```

---

### Post by kevingjames on 2020-06-17
And after the above I did

```
sudo apt -f install
``` 

and the result

```
kevin@kevin-O-E-M:~$ sudo apt -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclamav7 libdav1d1 libdav1d2 libdav1d4 libplacebo7 linux-headers-4.15.0-55 linux-headers-4.15.0-55-generic
  linux-image-4.15.0-55-generic linux-modules-4.15.0-55-generic linux-modules-extra-4.15.0-55-generic
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 365 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mpv (2:0.30.0+git1~bionic1) ...
kevin@kevin-O-E-M:~$
```

---

### Post by deadflowr on 2020-06-17
So it ended as it should, no errors on the end,
so try running the upgrade command again.

---

### Post by kevingjames on 2020-06-17
It appears to be working OK,thanks very much for your help in fixing it,it is very much appreciated as it was starting to drive me bananas because I couldn't fix it,thanks again deadflowr

---

### Post by ActionParsnip on 2020-06-17
You may want to report a bug as there is a package overlap

---

### Post by DuckHook on 2020-06-17
@kevingjames

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by mmoseeker on 2020-06-19
well.i met same problem,thanks for the code

---

