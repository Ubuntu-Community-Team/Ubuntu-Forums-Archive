---
title: "System Settings and other commands not working!!"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by touches on 2012-10-24
I have Ubuntu 11.10 and while trying to fix my pygame installation i gave the following commands in order:
```
sudo apt-get clean && sudo apt-get update
```

An update happened for sometime and it updated many packages.
After that when i tried to launch firefox using this command
```
sudo firefox or just  
firefox
```
I get this error:
```
sudo: firefox: command not found
```
```
-desktop:~$ firefox
/usr/bin/python: can't find '__main__' module in '/usr/share/command-not-found'
```

Now when i tried to check the version of Ubuntu installed with this command 
```
desktop:~$ lsb_release -a
/usr/bin/python: can't find '__main__' module in '/usr/share/command-not-found'
```
I get the error above

And when i try to open up System Settings from the top right corner of my desktop by clicking on System Settings or Displays or Software Up to Date none of these options open up

I even tried installing system settings by giving
```
sudo apt-get install systemsettings
```
It installed and i still am not able to open up any of the option on the top right corner of my desktop

I am very new to Ubuntu and are these errors very complicated like it requires a re-install??? Please anybody help me out

PS: I was able to use all these commands prior to my attempt at fixing up my pygame installation

---

### Post by NikTh on 2012-10-24
```
[s]sudo[/s] firefox **# **this command is forbidden
```Never open graphical applications with sudo , use gksudo instead. 
Similar forums thread explains why ? 
[http://ubuntuforums.org/showthread.php?t=1684377](http://ubuntuforums.org/showthread.php?t=1684377)

And as you are using 11.10  and you messed up so much your system (I guess a breakage of python here) I will easily  suggest you to make a new install of 12.04 (LTS). 

**EDIT:  **I found 2 new threads opened by you , referring to python (installation problems - experiments ? ) so , I assume my guess is true. 
[http://ubuntuforums.org/showthread.php?t=2075729](http://ubuntuforums.org/showthread.php?t=2075729)
[http://ubuntuforums.org/showthread.php?t=2075680](http://ubuntuforums.org/showthread.php?t=2075680)

Thanks

---

### Post by touches on 2012-10-24
The Ubuntu Software Center seems to have disappeared and i cannot find it on Dash and also whenever i click on any of the apps in Dash the screen blinks and re-appears

When i try to install software-center using the apt-get install method i get these errors:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 software-center : Depends: aptdaemon (>= 0.40) but it is not going to be installed
                   Depends: python-gobject (>= 2.90) but it is not going to be installed
                   Depends: python-gobject-cairo but it is not going to be installed
                   Depends: python-xapian but it is not going to be installed
                   Depends: python-apt (>= 0.7.93.1) but it is not going to be installed
                   Depends: python-aptdaemon (>= 0.40) but it is not going to be installed
                   Depends: python-aptdaemon.gtk3widgets but it is not going to be installed
                   Depends: python-dbus but it is not going to be installed
                   Depends: python-defer but it is not going to be installed
                   Depends: python-xdg but it is not going to be installed
                   Depends: python-lazr.restfulclient but it is not going to be installed
                   Depends: ubuntu-sso-client (>= 0.99.6) but it is not going to be installed
                   Depends: python-piston-mini-client (>= 0.1+bzr29) but it is not going to be installed
                   Depends: oneconf (>= 0.2.6) but it is not going to be installed
                   Recommends: lsb-release but it is not going to be installed
                   Recommends: apt-xapian-index (>= 0.38ubuntu1) but it is not going to be installed
                   Recommends: update-notifier but it is not going to be installed
                   Recommends: software-properties-gtk but it is not going to be installed
                   Recommends: sessioninstaller but it is not going to be installed
                   Recommends: zeitgeist-core but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Please anybody help me out with this!!

---

### Post by touches on 2012-10-24
> And as you are using 11.10  and you messed up so much your system (I guess a breakage of python here) I will easily  suggest you to make a new install of 12.04 (LTS). 

As i seem to be a newbie here are there any steps showing how to install to the newer version? I have a dual boot OS with Win Xp and Ubuntu 11.10, so if i have to re-install to a newer version how do i remove the older one and install the new version?

---

### Post by NikTh on 2012-10-24
> **touches said:**
> As i seem to be a newbie here are there any steps showing how to install to the newer version? I have a dual boot OS with Win Xp and Ubuntu 11.10, so if i have to re-install to a newer version how do i remove the older one and install the new version?

Download the 12.04 from here : [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

Create a bootable CD (burn it in lower speed) 
or 
bootable USB => [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
and boot from the CD or USB and "Install Ubuntu" . 

At the installer window you will see some options , select the most appropriate .. 

I don't remember them exactly .. If I recall correctly .. 

1) Upgrade 11.10 to 12.04 

2) Erase everything and install 12.04 

3) Something Else 

You can select the first option and your files : Documents - Pictures - etc .. will be untouched  
or 
you can select the Something Else option but this option is not for newbies .. there you can delete the / root partition with Ubuntu 11.10 completely and install 12.04 in the same partition. 

I suggest the Upgrade option. 

I would suggest to use the update manager from your current installation , but as I guess the system is corrupted , I'm afraid the Release Upgrade will not go as it should.

Good Luck

---

### Post by touches on 2012-10-24
I am now downloading and will burn it into a DVD, if i choose the upgrade option will it mean that the older version gets removed and the newer version gets installed in the same partition/hard disk space used by the old one?

---

### Post by NikTh on 2012-10-24
> **touches said:**
> I am now downloading and will burn it into a DVD, if i choose the upgrade option will it mean that the older version gets removed and the newer version gets installed in the same partition/hard disk space used by the old one?

Yes , something like that. Old packages will be upgraded and system files (corrupted) will be replaced with new ones. I have a feeling that everything will go smooth. :)

---

### Post by touches on 2012-10-24
I will try that post it here once i install the newer Ubuntu.. I hope i get to learn and install python in the new one without messing it up!!

---

### Post by NikTh on 2012-10-24
> **touches said:**
> .I hope i get to learn and install python in the new one without messing it up!!

Python is installed by default in Ubuntu , version 2.7.3 
I am not completely sure but I think python 3.2.3 is pre-installed too. Check it with this command ```
python3 --version
```If is not , install it with this simple command in terminal ```
sudo apt-get install python3.2
```If you want development packages and documentation ```
sudo apt-get install python3.2-dev python3.2-doc
```All are in Ubuntu Official repositories.. you don't need to install anything from external sites.

**Tip:** Here is a good e-book to starting with Python :  [http://www.swaroopch.com/notes/python/](http://www.swaroopch.com/notes/python/)

Thanks

---

### Post by touches on 2012-10-26
@Nikth
I have upgraded to Ubuntu 12.04 just like you said and it has completely fixed the errors.

Now i checked for python 3 and it said it's not available and it can be downloaded from Ubuntu's repo's.
So i am going to download it by giving the command you have shown.

For pygame installation can i follow the steps given in this link?
[http://pythonfun.wordpress.com/2011/...-ubuntu-11-04/](http://pythonfun.wordpress.com/2011/...-ubuntu-11-04/)

---

