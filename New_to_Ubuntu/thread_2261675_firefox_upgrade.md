---
title: "firefox upgrade"
date: 2015-01-20
forum: New to Ubuntu
---

### Post by dave6 on 2015-01-20
The time has come to upgrade or some thng like that to a newer version of firefox as evey thing / book-marks now tell me that this version 22 is no longer supported

I did try the following
sudo upgrade firefox using the terminal window, but I don't know what I am doiing

any help would be welcome

Dave

---

### Post by grahammechanical on 2015-01-20
It is possible to upgrade Firefox from within Firefox but note this limitation

> **Note:** If you use your Linux distribution's packaged version of Firefox, you will need to wait for an updated package to be released to its package repository. This article only applies if you installed Firefox manually (without using your distribution's package manager).

[https://support.mozilla.org/en-US/kb/update-firefox-latest-version](https://support.mozilla.org/en-US/kb/update-firefox-latest-version)

It is my understanding that Firefox is one of those few Ubuntu default applications that are upgraded throughout the support life of the Ubuntu version. Other applications get upgraded when a new release of Ubuntu is released. Certainly I have seen upgrades to Firefox. I run the development version (Ubuntu 15.04) and that has upgraded Firefox to version 35 just by doing the normal update process.

I am wondering what version of Ubuntu you are using. I suspect that it is now an unsupported version. You may need to download and install Firefox from the Mozilla web site to get an updated version of Firefox on an out of life version of Ubuntu.

Regards.

---

### Post by sandyd on 2015-01-20
Hi, can you post the output of the following commands?
It will allow us to determine why your firefox is not updating.
```

cat /etc/apt/sources.list
sudo apt-get update
lsb_release -a
```

---

### Post by dave6 on 2015-01-20
daboss@daboss-desktop:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
daboss@daboss-desktop:~$ sudo apt-get update
[sudo] password for daboss: 
Sorry, try again.
[sudo] password for daboss: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en_GB [5,492 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Fetched 5,492 B in 0s (9,628 B/s)
Reading package lists... Done
daboss@daboss-desktop:~$

---

### Post by newbie13 on 2015-01-20
What I do to update any software is this, if it helps..

```
sudo apt-get update
```

Then

```
sudo apt-get upgrade
```

---

### Post by dave6 on 2015-01-20
Point of note
I always have to type in my password twice ??
newbie13 
daboss@daboss-desktop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Reading package lists... Done
daboss@daboss-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Dave

---

### Post by sandyd on 2015-01-20
Ok, it seems that your sources.list is not formatted right and are missing a ton of entries

Run the following
```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo nano /etc/apt/sources.list

```
Paste the following```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner


```

Press Control+X to save.
Press 'Y' after that, and then enter key

Run the following
```

sudo apt-get update 
sudo apt-get upgrade
```

---

### Post by newbie13 on 2015-01-20
Sudo means you want to execute that command as a root user. So to confirm that you are the admin of the pc, it asks the password whenever you use sudo.
But it does not ask if the time interval between two 'sudo commands' is less.

And about your problem, it seems I can't help you more. I am a newbie too.

---

### Post by dave6 on 2015-01-20
> **sandyd said:**
> Ok, it seems that your sources.list is not formatted right and are missing a ton of entries

Run the following
```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo nano /etc/apt/sources.list

```
Paste the following```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner


```

Press Control+X to save.

Run the following
```

sudo apt-get update 
sudo apt-get upgrade
```

I get all this
```
  GNU nano 2.2.6          File: /etc/apt/sources.list                 Modified  

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security main restricted universe$
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe $
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe$
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted univers$
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security main restricted univ$
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted unive$
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-proposed main restricted univ$
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted uni$

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner





Save file under DIFFERENT NAME ?                                                
 Y Yes
 N No           ^C Cancel
```

sandyd
Is there some thing I ain't doing right with the above codes?

Dave

---

### Post by sandyd on 2015-01-20
> **dave6 said:**
> sandyd
Is there some thing I ain't doing right with the above codes?

Dave

Forgot about that - press 'Y'

---

### Post by dave6 on 2015-01-20
Re-ran the codes again, and on the 3rd attempt, it is now updatting you can sort-a tell my key-brd is sticking

Dave

Thanks sandyd aka Emma ?

All up and running, don't like this new look version 35 of firefox............ just don't like change

Dave

Just 1 last thing, how do I mark this as sloved ?

Thanks all
Dave

---

### Post by ajgreeny on 2015-01-20
> **dave6 said:**
> Just 1 last thing, how do I mark this as sloved ?

Thanks all
Dave
Go to **Thread Tools** menu at the top of the page and mark as Solved from that.

With regard to the new "look" of FF, that is the Australis GUI, which a lot of users do not like, so an extension is available to revert the look to the classic look.
Go to [https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/?src=ss](https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/?src=ss) to see it and add it to your FF if you want to try it.

I use that, and also the "Hide Caption Titlebar Plus" to get FF looking as you see it in the attached screenshot of the top of the FF window.

---

