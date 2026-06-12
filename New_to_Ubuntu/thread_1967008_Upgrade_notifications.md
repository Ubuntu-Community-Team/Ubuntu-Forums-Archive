---
title: "Upgrade notifications"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by Spiritof76 on 2012-04-27
I have 1 desktop at 10.4 one net book at 10.4 1 netbook at 11.10 a server at 10.4, I want to do a network upgrade but I cant seem to get the notifications that 12.04 is ready.  The check for update Button returns with my system is up to date.

Edit update: 
The 11.10 netbook found the upgrade.

---

### Post by cryptotheslow on 2012-04-27
The common wisdom as regards updating LTS to LTS (e.g. 10.04 to 12.04) is to wait for the first point release to be available to make sure any glitches in the upgrade path have been ironed out. 

12.04.1 is due out on July 19th.

If you really need to get it done you can use this command:
```
do-release-upgrade
```

This will check to see if a release upgrade is available without actually installing it:
```
do-release-upgrade -c
```

Those should work on both desktop and server.

If you really want to use Update Manager to do the upgrade, take a looking in the Settings for it at the option "Notify me of a new Ubuntu version" and ensure it is set to "For long term support versions".

---

### Post by Frogs Hair on 2012-04-27
See the link for network sever upgrade . [https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

---

### Post by Spiritof76 on 2012-04-27
I tried the "sudo do-release-upgrade -c" thing and my console reported no upgrade found.  I then change  Prompt=lts to  Prompt=normal and my system found Maverick.  
```

ray@Spiritof76:~$ sudo do-release-upgrade -c
[sudo] password for ray: 
Checking for a new ubuntu release
No new release found

ray@Spiritof76:~$ sudo nano /etc/update-manager/release-upgrades
ray@Spiritof76:~$ sudo do-release-upgrade -c
Checking for a new ubuntu release
New release 'maverick' available.
Run 'do-release-upgrade' to upgrade to it.
ray@Spiritof76:~$ sudo nano /etc/update-manager/release-upgrades

```

---

### Post by sandyd on 2012-04-27
> **Spiritof76 said:**
> I tried the "sudo do-release-upgrade -c" thing and my console reported no upgrade found.  I then change  Prompt=lts to  Prompt=normal and my system found Maverick.  
```

ray@Spiritof76:~$ sudo do-release-upgrade -c
[sudo] password for ray: 
Checking for a new ubuntu release
No new release found

ray@Spiritof76:~$ sudo nano /etc/update-manager/release-upgrades
ray@Spiritof76:~$ sudo do-release-upgrade -c
Checking for a new ubuntu release
New release 'maverick' available.
Run 'do-release-upgrade' to upgrade to it.
ray@Spiritof76:~$ sudo nano /etc/update-manager/release-upgrades

```
its not safe todo a direct upgrade from 10.04 to 12.04. you have to go through version by version, i.e. 10.04 -> 10.10 -> 11.04 -> 11.10 -> 12.04

---

### Post by Spiritof76 on 2012-04-27
> **sandyd said:**
> you can't do a direct upgrade from 10.04 to 12.04. you have to go through version by version, i.e. 10.04 -> 10.10 -> 11.04 -> 11.10 -> 12.04
I was under the impression that I could do an upgrade from LTS to LTS.

---

### Post by cryptotheslow on 2012-04-27
Yes you should be able to go from LTS to LTS.

Make sure you have installed all available 10.04 updates first with:

```

sudo apt-get update

sudo apt-get upgrade

```

and if there is a new kernel update waiting:

```

sudo apt-get dist-upgrade

```

and then retry the release upgrade commands again,.

---

### Post by ptn107 on 2012-04-27
You certainly can do a 10.04 LTS to 12.04 LTS upgrade.

_[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS")_

---

### Post by Spiritof76 on 2012-04-27
> **cryptotheslow said:**
> Yes you should be able to go from LTS to LTS.

Make sure you have installed all available 10.04 updates first with:

```

sudo apt-get update

sudo apt-get upgrade

```

and if there is a new kernel update waiting:

```

sudo apt-get dist-upgrade

```

and then retry the release upgrade commands again,.

I did the dist-upgrade thing and i was sorta surprised to see the kernal upgrade ..  the server still didn't see that 12.04 is available.  I did a F2   update-manager -d on the desktop and it started the upgrade process although I was warned this is a beta.
update manager won't run in my server because I dont have a gnomes display set up for it.  ..  
Currently it looks like i should be able to upgrade my desktop and netbooks.  but its beggining to look like i will need to wait for 12.04.1 to upgrade my server

---

### Post by gordintoronto on 2012-04-28
It sounds like the mirror you are getting updates from, is not being kept up to date. Have a look at Software Sources.

---

### Post by mo79 on 2012-04-28
The first point release (12.04.1) will show up in update manager in mid/late July; this version is recommended for real play-safe upgraders as it will have any relevant bug fixes.
But if you want to jump in now, press Alt-F2 and type update-manager -d
You should now get the upgrade button.

---

### Post by grahammechanical on 2012-04-28
I tested the upgrade path from both 10.04 and 11.10 to 12.04 for the QA team prior to release. This was the test case I followed. Note the command used.

[http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade]("http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade")

>        -c, --check-dist-upgrades
              Check if a new distribution release is available

       -d, --devel-release
              Check if upgrading to the latest devel release is possible


It is possible to go from LTS to LTS. There is a setting for just that in Update Manager Settings.

But to go from 10.10 to 12.04 it is not possible without first going to 11.04 and then 11.10.

Regards.

---

### Post by Spiritof76 on 2012-04-29
Ok, 

I the 11.10 upgrade to start without issue on 1 netbook.
The desktop upgraded started when i installed and ran 
It worked this morning 
On the 
First I tried :
sudo do-release-upgrade -c

I was informed that there was no upgrade available.

I then tried :
sudo do-release-upgrade -d

it found the upgrade is is installing now.  I don't know why the install wouldn't work on Friday but works today on Sunday.

---

