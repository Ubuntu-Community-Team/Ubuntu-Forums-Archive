---
title: "Help installing Unity"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by ironmaiden943 on 2012-07-22
I tried installing the new WebApps feature, didn't like it and removed (or so I thought) only the packages which I installed. Unity was also accidentally uninstalled. Now when I try to reinstall it from the software center I get this error message:

Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Details:

The following packages have unmet dependencies:

unity: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
       Depends: libunity-core-5.0-5 (= 5.12-0ubuntu1.1) but 5.12.0-0ubuntu3~webapps7 is to be installed
       Depends: libxfixes3 (>= 1:5.0-4ubuntu1) but 1:5.0-4ubuntu4 is to be installed
       Depends: unity-common (= 5.12-0ubuntu1.1) but 5.12.0-0ubuntu3~webapps7 is to be installed
       Depends: compiz-core-abiversion-20120305 but it is a virtual package
       Depends: libnux-abiversion-20120411.01 but it is a virtual package


What do I do to reinstall Unity, any help would be greatly appreciated!

---

### Post by ironmaiden943 on 2012-07-22
bump

---

### Post by anewguy on 2012-07-22
Try the following in a terminal window:

sudo apt-get build-dep <unity full package name here>

This should get all the packages that unity is dependant on.


Also - wait 24 hours before bumping a thread (forum rule).

---

### Post by ironmaiden943 on 2012-07-22
I did that, and it's still giving me the same error.

And sorry about the bump! I had no idea!

---

### Post by NikTh on 2012-07-22
Hi , 

please open a terminal (Ctrl + alt + t ) and copy-paste these 2  commands (one at time)
```
sudo apt-get install --reinstall ubuntu-desktop ubuntu-minimal ubuntu-mono unity unity-common unity-greeter
sudo apt-get install -f
``` and give the results back here.. 
**Put the results inside ```
 tags  , by highlighting the text and click # symbol on top of message pane. **

_**Question:**_ do you have the repository still enabled ? 
If yes , then try to disable it (from update manager , better remove it completely ) and then open a terminal and 
[code]sudo apt-get update 
sudo apt-get dist-upgrade
```Thanks

---

### Post by ironmaiden943 on 2012-07-22
This is the output I get:
```
andrea@andrea-laptop:~$ sudo apt-get install --reinstall ubuntu-desktop ubuntu-minimal ubuntu-mono unity unity-common unity-greeter
[sudo] password for andrea: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of unity-common is not possible, it cannot be downloaded.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity : Depends: libunity-core-5.0-5 (= 5.12-0ubuntu1.1) but 5.12.0-0ubuntu3~webapps7 is to be installed
         Depends: unity-common (= 5.12-0ubuntu1.1) but 5.12.0-0ubuntu3~webapps7 is to be installed
E: Unable to correct problems, you have held broken packages.
andrea@andrea-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andrea@andrea-laptop:~$ 

```

And yes, I removed the repository

---

### Post by NikTh on 2012-07-22
> **ironmaiden943 said:**
> 
The following packages have unmet dependencies:
 unity : Depends: libunity-core-5.0-5 (= 5.12-0ubuntu1.1) but 5.12.0-0ubuntu3~**webapps7 **is to be installed
         Depends: unity-common (= 5.12-0ubuntu1.1) but 5.12.0-0ubuntu3~**webapps7** is to be installed[/CODE]And yes, I removed the repository

Hi , 

here it seems like you have the repository still enabled. Apt search for this specific package (5.12.0-0ubuntu3) , and apt search based on lists and repositories. 

If you removed the ppa , then open a terminal and give these commands 
```
sudo apt-get update 
sudo apt-get dist-upgrade
```**Maybe you have the proposed-updates enabled , too ? **
Also give the output of these commands 
```
ls /etc/apt/sources.list.d/ 
cat /etc/apt/sources.list
```Thanks.

---

### Post by ironmaiden943 on 2012-07-23
I updated my repositories, and this time dist-upgrade worked, however trying to install Unity still gives me the same error message. 

As for the output of the second command which you gave me:
```
andrea@andrea-laptop:~$ ls /etc/apt/sources.list.d/
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
google-musicmanager.list
google-musicmanager.list.distUpgrade
google-musicmanager.list.save
google-talkplugin.list
google-talkplugin.list.distUpgrade
google-talkplugin.list.save
olmecs-ppa-oneiric.list
olmecs-ppa-oneiric.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_lordofultima_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_lordofultima_ubuntu.list.save
scopes-packagers-ppa-oneiric.list
scopes-packagers-ppa-oneiric.list.save
tiheum-equinox-oneiric.list
tiheum-equinox-oneiric.list.save
andrea@andrea-laptop:~$ cat /etc/apt/sources.list


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
andrea@andrea-laptop:~$ 

```

It looks to me as if the proposed-updates are not enabled. 
Thanks

---

### Post by NikTh on 2012-07-23
> **ironmaiden943 said:**
> It looks to me as if the proposed-updates are not enabled. 
Thanks

Hi , 

lets see a little more detailed info .. 
```
find /etc/apt/ -iname "*.list" -exec echo "FILE: {}" \; -exec cat "{}" \;
```

And to be sure , go to Update manager > settings > updates , and check by your self if precise-proposed are enabled (**if yes** , then Un-tick it and run again **apt-get update** , **apt-get dist-upgrade**. 

THanks.

---

### Post by ironmaiden943 on 2012-07-23
Hi, here's the output
```
andrea@andrea-laptop:~$ find /etc/apt/ -iname "*.list" -exec echo "FILE: {}" \; -exec cat "{}" \;
FILE: /etc/apt/sources.list


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
FILE: /etc/apt/sources.list.d/scopes-packagers-ppa-oneiric.list
FILE: /etc/apt/sources.list.d/tiheum-equinox-oneiric.list
FILE: /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_lordofultima_ubuntu.list
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/lordofultima/ubuntu precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
FILE: /etc/apt/sources.list.d/google-talkplugin.list
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main
FILE: /etc/apt/sources.list.d/google-musicmanager.list
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/musicmanager/deb/ stable main
FILE: /etc/apt/sources.list.d/olmecs-ppa-oneiric.list
FILE: /etc/apt/sources.list.d/google-chrome.list
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

```

And I checked and it's unticked.
Thanks.

---

### Post by NikTh on 2012-07-23
Hi , 
do you still have the same problem ?  

**EDIT:  **Try this 
```
sudo rm -rf /var/lib/apt/lists/* 
sudo apt-get clean 
sudo apt-get update ; sudo apt-get dist-upgrade
sudo apt-get install --reinstall unity unity-common unity-greeter ubuntu-minimal ubuntu-desktop ubutnu-mono ubuntu-standard
```

If above not work then...
....I cannot understand what happen.

We removed the ppa , we did a dist-upgrade , we unticked "precise-proposed" updates , and you still have this problem ? 

Maybe if you want to wait someone with more knowledge , or we can vanish all your sources.list and replace them with the original.. 
but you will lose all these entries..
> ```

google-chrome.list 
google-chrome.list.distUpgrade 
google-chrome.list.save google-musicmanager.list 
google-musicmanager.list.distUpgrade 
google-musicmanager.list.save google-talkplugin.list 
google-talkplugin.list.distUpgrade 
google-talkplugin.list.save 
olmecs-ppa-oneiric.list 
olmecs-ppa-oneiric.list.save 
private-ppa.launchpad.net_commercial-ppa-uploaders_lordofultima_ubuntu.list 
private-ppa.launchpad.net_commercial-ppa-uploaders_lordofultima_ubuntu.list.save 
scopes-packagers-ppa-oneiric.list 
scopes-packagers-ppa-oneiric.list.save 
tiheum-equinox-oneiric.list 
tiheum-equinox-oneiric.list.save
```I can see that half of them are useless , cause indicated to 11.10 (oneiric) ubuntu.. 
If you want tell me to give you the commands. 

Thanks

---

### Post by ironmaiden943 on 2012-07-24
Hi, it still gives me that error message. yeah, I have no idea what the problem is. can you give me the steps needed to replace the repository list with the original?
Thanks

---

### Post by Bufeu on 2012-07-24
> **ironmaiden943 said:**
> Hi, it still gives me that error message. yeah, I have no idea what the problem is. can you give me the steps needed to replace the repository list with the original?
Thanks[http://askubuntu.com/questions/124017/how-do-i-restore-the-default-repositories](http://askubuntu.com/questions/124017/how-do-i-restore-the-default-repositories)

---

### Post by NikTh on 2012-07-25
> **ironmaiden943 said:**
> Hi, it still gives me that error message. yeah, I have no idea what the problem is. can you give me the steps needed to replace the repository list with the original?
Thanks

Hi , 
here are the commands .. 

```
sudo rm /etc/apt/sources.list.d/* .list 
sudo wget "http://pastebin.com/raw.php?i=aDE6mdsP" -O /etc/apt/sources.list 
sudo apt-get update ; sudo apt-get dist-upgrade
``` 

Thanks

---

### Post by ironmaiden943 on 2012-07-25
thanks, 
I managed to install it, but now when I login with Unity instead of Gnome, the Unity launcher and panel never appear. However, I can access the terminal from a keyboard shortcut and run unity from there. Do you have any idea why it's not starting up when I log in?

---

### Post by ironmaiden943 on 2012-07-25
Nevermind, I figured out why it wasn't showing up. 
When I ran it from a terminal I got the following message:
```
andrea@andrea-laptop:~$ unity
unity-panel-service: no process found
Killed

```

The solution was to go into ccsm and enable the unity plugin, which was disabled for some reason. Now Unity finally works again!

Thanks for all the help, I really appreciate it!
Whenever my computer messes up due to errors caused 100% of the time due to my ineptitude, the gurus of the Ubuntu forums have always come to my rescue.
Thanks again!

---

### Post by NikTh on 2012-07-26
Hi , 
Ok ! Glad you fixed it. 

You can mark **thread as solved** , from **thread tools**.

Thanks

---

