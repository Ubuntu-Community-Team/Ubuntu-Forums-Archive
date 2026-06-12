---
title: "Dependency error while installing R"
date: 2017-11-01
forum: New to Ubuntu
---

### Post by pantho on 2017-11-01
while trying to install R i followed these steps [HTML]https://askubuntu.com/questions/971307/dependency-errors-while-installing-r-in-ubuntu-17-10/971438?noredirect=1#comment1556945_971438[/HTML]

```
sudo apt update[sudo] password for mahim: Ign:1 http://ppa.launchpad.net/marutter/rdev/ubuntu artful InRelease           
Hit:2 http://archive.ubuntu.com/ubuntu artful InRelease                        
Get:3 http://security.ubuntu.com/ubuntu artful-security InRelease [70.3 kB]    
Ign:4 http://cran.rstudio.com/bin/linux/ubuntu artful/ InRelease               
Hit:5 http://ppa.launchpad.net/marutter/rrutter/ubuntu artful InRelease        
Err:6 http://ppa.launchpad.net/marutter/rdev/ubuntu artful Release             
  404  Not Found
Hit:7 http://cran.rstudio.com/bin/linux/ubuntu artful/ Release                 
Hit:9 http://bd.archive.ubuntu.com/ubuntu artful InRelease                     
Hit:10 https://cran.rstudio.com/bin/linux/ubuntu xenial/ InRelease             
Get:11 http://security.ubuntu.com/ubuntu artful-security/universe amd64 DEP-11 Metadata [2,184 B]
Get:12 http://bd.archive.ubuntu.com/ubuntu artful-updates InRelease [76.7 kB]  
Get:13 https://cran.rstudio.com/bin/linux/ubuntu zesty/ InRelease [3,587 B]    
Hit:14 http://bd.archive.ubuntu.com/ubuntu artful-backports InRelease          
Ign:15 https://cran.rstudio.com/bin/linux/ubuntu xenial2/ InRelease
Get:16 http://bd.archive.ubuntu.com/ubuntu artful-updates/main amd64 Packages [19.3 kB]
Get:17 http://bd.archive.ubuntu.com/ubuntu artful-updates/main i386 Packages [19.3 kB]
Get:18 http://bd.archive.ubuntu.com/ubuntu artful-updates/main amd64 DEP-11 Metadata [8,268 B]
Get:19 http://bd.archive.ubuntu.com/ubuntu artful-updates/universe amd64 Packages [9,780 B]
Get:20 http://bd.archive.ubuntu.com/ubuntu artful-updates/universe i386 Packages [9,792 B]
Get:21 http://bd.archive.ubuntu.com/ubuntu artful-updates/universe amd64 DEP-11 Metadata [2,188 B]
Err:22 https://cran.rstudio.com/bin/linux/ubuntu xenial2/ Release              
  404  Not Found
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/marutter/rdev/ubuntu artful Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'https://cran.rstudio.com/bin/linux/ubuntu xenial2/ Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```
 and then [COLOR=#111111][FONT=Consolas]sudo apt install r-base

[/FONT][/COLOR]```
sudo apt install r-baseReading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 r-base : Depends: r-recommended (= 3.4.2-2zesty) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



```

what is the problem?? please advise the procedures to install R-base and R studio properly

---

### Post by ian-weisser on 2017-11-01
> **pantho said:**
>  r-base : Depends: r-recommended (= 3.4.2-2zesty) but it is not going to be installed

That's easy: version 3.4.2-2zesty is not a package from an Ubuntu source.
The version number is higher than the Ubuntu version (3.4.2-1ubuntu1). Apt always wants to install a higher version.
You must locate and disable that source on general principles - it is not your friend.
Alternately, you can pin to the Ubuntu version, but that's rather a temporary hack.

Please show us the output of:
```
apt policy r-recommended
```

---

### Post by pantho on 2017-11-01
```

mahim@mahim-HP-15-Notebook-PC:~$ apt policy r-recommended
r-recommended:
  Installed: (none)
  Candidate: 3.4.2-2zesty
  Version table:
     3.4.2-2zesty 500
        500 https://cran.rstudio.com/bin/linux/ubuntu zesty/ Packages
     3.4.2-2xenial2 500
        500 https://cran.rstudio.com/bin/linux/ubuntu xenial/ Packages
     3.4.2-2artful4 500
        500 http://cran.rstudio.com/bin/linux/ubuntu artful/ Packages
        500 http://ppa.launchpad.net/marutter/rrutter/ubuntu artful/main amd64 Packages
        500 http://ppa.launchpad.net/marutter/rrutter/ubuntu artful/main i386 Packages
     3.4.2-1zesty1 500
        500 https://cran.rstudio.com/bin/linux/ubuntu zesty/ Packages
     3.4.2-1xenial1 500
        500 https://cran.rstudio.com/bin/linux/ubuntu xenial/ Packages
     3.4.2-1ubuntu1 500
        500 http://bd.archive.ubuntu.com/ubuntu artful/universe amd64 Packages
        500 http://bd.archive.ubuntu.com/ubuntu artful/universe i386 Packages
        500 http://archive.ubuntu.com/ubuntu artful/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu artful/universe i386 Packages
     3.4.1-2zesty0 500
        500 https://cran.rstudio.com/bin/linux/ubuntu zesty/ Packages
     3.4.1-2xenial0 500
        500 https://cran.rstudio.com/bin/linux/ubuntu xenial/ Packages
     3.4.1-1zesty0 500
        500 https://cran.rstudio.com/bin/linux/ubuntu zesty/ Packages
     3.4.1-1xenial0 500
        500 https://cran.rstudio.com/bin/linux/ubuntu xenial/ Packages
     3.4.0-1zesty 500
        500 https://cran.rstudio.com/bin/linux/ubuntu zesty/ Packages
     3.4.0-1xenial0 500
        500 https://cran.rstudio.com/bin/linux/ubuntu xenial/ Packages
     3.3.3-1xenial0 500
        500 https://cran.rstudio.com/bin/linux/ubuntu xenial/ Packages
     3.3.2-1xenial0 500
        500 https://cran.rstudio.com/bin/linux/ubuntu xenial/ Packages
     3.3.1-1xenial0 500
        500 https://cran.rstudio.com/bin/linux/ubuntu xenial/ Packages
     3.3.0-2xenial0 500
        500 https://cran.rstudio.com/bin/linux/ubuntu xenial/ Packages
     3.3.0-1xenial0 500
        500 https://cran.rstudio.com/bin/linux/ubuntu xenial/ Packages
     3.2.5-1xenial 500
        500 https://cran.rstudio.com/bin/linux/ubuntu xenial/ Packages



```

---

### Post by ian-weisser on 2017-11-01
Ah. [You neglected to tell us]("https://askubuntu.com/questions/971307/dependency-errors-while-installing-r-in-ubuntu-17-10/971438?") that you tried to install R several times using different methods, and you didn't clean up the old tries.
That changes the AskUbuntu answer.
You DO need step #4 (remove non-Ubuntu sources). 

Always clean up. The old packages from four different sources are all still there, and that's the current problem.

DELETE those obsolete xenial and zesty sources. Never mix packages from different releases of Ubuntu.
DISABLE all remaining non-Ubuntu sources. Keep archive.ubuntu.com, disable the rest.
There's a difference between 'delete' and 'disable'. Do each one properly.

Afterward, since your sources have changed, run 'apt update' to refresh your package database.

Then return to Step #3 of the AskUbuntu question.

---

### Post by pantho on 2017-11-01
how do i delete those?? please give those commands. Actually i am a noob to all these and new in ubuntu , if you please could help me out here

---

### Post by ian-weisser on 2017-11-01
Go into System Settings
Open the Software & Updates control panel
Click the 'other software' tab.

Disable by unchecking.
Delete by using the 'remove' button.

---

### Post by pantho on 2017-11-01
please stay with me .. i am doing those and giving you continues updates

---

### Post by pantho on 2017-11-01
thanks a lot. it installed.

---

### Post by ian-weisser on 2017-11-01
Hooray!

---

### Post by ajgreeny on 2017-11-01
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by pantho on 2017-11-01
ok sure

---

