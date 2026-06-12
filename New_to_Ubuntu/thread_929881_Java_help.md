---
title: "Java help"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by realunreal on 2008-09-25
Hi, 

I'm trying to get onto one of my regular chat sites which uses Java,  I've been onto add remove programs and added what I believe to be Java runtime 5 yet the applet still reports missing plugin.

I click install missing plugin and all I get is a link to a webpage for a manual install and I have no clue what to do !

---

### Post by Therion on 2008-09-25
From the desktop:

    * In the main desktop menu, choose "Add/Remove ..."
    * In the "Show" toggle box, select "All Open Source Applications"
    * Search for "OpenJDK"
    * Select the "OpenJDK Java Runtime" (openjdk-6-jre)
    * Confirm the installation of community maintained software
    * Press the "Apply Changes" button

---

### Post by realunreal on 2008-09-25
Nope can't find it

I have show unsuported apps & show comercial apps

I highlighted all and put OpenJDK in search box and I get couldn't find a matching application

---

### Post by Teamgeist on 2008-09-25
Try in a Terminal ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by realunreal on 2008-09-25
Couldn't find package ubuntu-restricted-extras

---

### Post by Ryadt on 2008-09-25
> **realunreal said:**
> Couldn't find package ubuntu-restricted-extras
Go in Software sources (System > Administration > Software Sources) and check the multiverse box.
Then re-run the command for ubuntu-restricted-extras.

---

### Post by realunreal on 2008-09-25
still no lick

about to give up with this

---

### Post by realunreal on 2008-09-25
This is so F*****G annoying I want this to work,  I don't want to go back to windows

---

### Post by Ryadt on 2008-09-25
Did ubuntu-restricted-extras get installed?

---

### Post by realunreal on 2008-09-25
No i get >

realunreal@realunreal-desktop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ubuntu-restricted-extras
realunreal@realunreal-desktop:~$

---

### Post by Teamgeist on 2008-09-25
> **Ryadt said:**
> Go in Software sources (System > Administration > Software Sources) and check the multiverse box.
Then re-run the command for ubuntu-restricted-extras.

Have you done this?

Afterwards type ```
sudo apt-get update
``` and ```
sudo apt-get install ubuntu-restricted-extras 
```

---

### Post by Therion on 2008-09-25
OP should, if he's reading his PM's, be installing the additional repos in Software Sources -- even as I type this.  Once that's done, and he's reloaded, he should be able to install the Java JDK and so forth with no problem.

---

### Post by scorp123 on 2008-09-25
> **realunreal said:**
> No i get >

E: Couldn't find package ubuntu-restricted-extras Can you please type this into a terminal and post the output here:
```
cat /etc/apt/sources.list
```

And then please post the output of this command: ```
uname -a
```

This would show us the "sources.list" file which tells Ubuntu where it can find stuff it's supposed to install and the other command will tell us which version you installed, e.g. 32-bit or 64-bit.

---

### Post by realunreal on 2008-09-25
I have checked everything in software repository and still no luck
last command read out if your interested

realunreal@realunreal-desktop:~$ sudo apt-get update
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Fetched 5B in 0s (7B/s)
Reading package lists... Done
realunreal@realunreal-desktop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ubuntu-restricted-extras
realunreal@realunreal-desktop:~$

---

### Post by Ryadt on 2008-09-25
> **realunreal said:**
> No i get >

realunreal@realunreal-desktop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ubuntu-restricted-extras
realunreal@realunreal-desktop:~$

Do you have internet connection? If you have, there maybe issues with the server. Try a bit later.
Try ```
sudo apt-get update
```
Post back any errors.

---

### Post by realunreal on 2008-09-25
read post above bud

---

### Post by Ryadt on 2008-09-25
It seems that you are using Dapper Drake. Dapper is not supported anymore.
Upgrade to Hardy.

---

### Post by Ryadt on 2008-09-25
> **realunreal said:**
> read post above bud
I can't read while typing.

---

### Post by Therion on 2008-09-25
Oh... You're using Dapper Dan (Ubuntu version 6.06)???  

Have you considered upgrading?  Because you're going to need to...

---

### Post by realunreal on 2008-09-25
lol

where do i get it from

---

### Post by Therion on 2008-09-25
[http://releases.ubuntu.com/releases/8.04/](http://releases.ubuntu.com/releases/8.04/)

Fresh install time.

---

### Post by Teamgeist on 2008-09-25
OK, since you're using Dapper (Ubuntu 6.06) there is no ubuntu-restricted-extras Package. It was introduced in Ubuntu 7.10 I believe.

Is there any reason you are using 6.06? This version of Ubuntu is over 2 years old and 8.04 (Hardy) will have a lot more features and will make life easier for you in Ubuntu A LOT.

Since you are just starting you Linux experience I would reccomend an Upgrade. Eitehr via the update-manager or as a new fresh install.

To get java working on Dapper type ```
sudo apt-get install sun-java5-plugin
``` 


Note: In order to get java6 you will need to enable the Dapper-Backports Repository.

edit: You can get Hardy (Ubuntu 8.04) directly from [ftp://ftp.rrzn.uni-hannover.de/pub/mirror/linux/ubuntu-releases/hardy/ubuntu-8.04.1-desktop-i386.iso](ftp://ftp.rrzn.uni-hannover.de/pub/mirror/linux/ubuntu-releases/hardy/ubuntu-8.04.1-desktop-i386.iso)

or do an online-upgrade from 6.06 via ```
sudo update-manager -c
```

---

### Post by Ryadt on 2008-09-25
Safest thing to do is to download it from the Ubuntu hompage and do a clean install.
You can also upgrade it directly if you choose so.[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by realunreal on 2008-09-25
kk,

I'm downloading the new version now,  where will i find the download on this computer and how do i burn it to a disk

thanx guys you have been so patient with me and I still have thousands of questions !

---

### Post by realunreal on 2008-09-25
I'm gonna do another fresh install with ubuntu-8.04.1-desktop-i286,

How do i find and burn it on linux

---

### Post by Ryadt on 2008-09-25
> **realunreal said:**
> kk,

I'm downloading the new version now,  where will i find the download on this computer and how do i burn it to a disk

thanx guys you have been so patient with me and I still have thousands of questions !
If you haven't change any settings. The download should be on your desktop.
Have a look here for burning iso: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by realunreal on 2008-09-25
Lol @ 286 typo

---

### Post by Therion on 2008-09-25
Since I'm fairly certain it's going to come up: 

How to Burn an .iso to make a bootable CD:
[http://railstech.blogspot.com/2007/12/burn-iso-files-on-ubuntu-linux.html](http://railstech.blogspot.com/2007/12/burn-iso-files-on-ubuntu-linux.html)

and

How to Install Hardy Heron Step by Step:
[http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml)

---

### Post by Teamgeist on 2008-09-25
> **realunreal said:**
> How do i find and burn it on linux

Right click--> burn to cd  :)

---

### Post by HittingSmoke on 2008-09-25
> **Teamgeist said:**
> Right click--> burn to cd  :)

I heart Ubuntu =D>

---

### Post by Dhannigan on 2008-09-27
I just upgraded to 8.4 trying to install jre and keep getting authorization failure

---

### Post by gandaran on 2008-09-27
> **Dhannigan said:**
> I just upgraded to 8.4 trying to install jre and keep getting authorization failure
how are you trying to install, command line or synaptic? 
and which java package?

---

### Post by Dhannigan on 2008-09-27
> **gandaran said:**
> how are you trying to install, command line or synaptic? 
and which java package?

Im trying to install jre. Im a neophyte

---

### Post by gandaran on 2008-09-28
32-bit ubuntu user- sun java
just open synaptic package manager, scroll down to **sun-java6-plugin** mark for install and click the apply button, that's all, it'll install the jre and firefox plugin 

64-bit ubuntu user 
install the ubuntu-restricted-extras, this meta package installs open java, 32-bits users can also install this package but I recommend the sun-java.

---

### Post by Dhannigan on 2008-09-28
Well Im thanking you in advance. Ill be back ranting, raving, and generally making an *** of myself if no- worky.

---

