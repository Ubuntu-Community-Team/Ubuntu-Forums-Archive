---
title: "upgrade to 13.04"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by shakthi90 on 2013-05-07
I have ubuntu 11.10 in my PC. I want to upgrade it to 13.04 directly.
When I open update manager the only possible option is to to upgrade to 12.04.
Please tell me a method to upgrade my Ubuntu fron 11.10 to 13.04 directly?

---

### Post by claracc on 2013-05-07
Not possible update directly from ubuntu 11.10 to 13.04 through update manager (you will have to do a step by step upgrading: 11.10 --> 12.04 --> 12.10 --> 13.04).

The only possibility is to do a fresh install of ubuntu 13.04 through the live CD.

---

### Post by pqwoerituytrueiwoq on 2013-05-07
there is none, you have to go through the other versions to get there or clean install
you could try editing your sources list and tell the system to update and upgrade, odds are this will severally break your system in ways no one knows how to fix without reinstalling
```
[COLOR=#ff0000]# Will probably break system
[/COLOR]sudo sed -i "s/$(lsb_release -sc)/raring/" /etc/apt/sources.list;sudo apt-get update;sudo apt-get dist-upgrade
```
if you really want to try that backup your system 1st, you will probably regret it if you don't
if you try it tell me what happens i am curious

---

### Post by fantab on 2013-05-07
> **shakthi90 said:**
> I have ubuntu 11.10 in my PC. I want to upgrade it to 13.04 directly.
When I open update manager the only possible option is to to upgrade to 12.04.
Please tell me a method to upgrade my Ubuntu fron 11.10 to 13.04 directly?

Back up all your important DATA. Download Ubuntu 13.04. Burn it to a Disk, DVD or USB. Remove 11.10 by formatting the partition and install 13.04. I don't think there is anything more direct.

---

### Post by holycow131415 on 2013-05-07
> **pqwoerituytrueiwoq said:**
> there is none, you have to go through the other versions to get there or clean install
you could try editing your sources list and tell the system to update and upgrade, odds are this will severally break your system in ways no one knows how to fix without reinstalling
```
[COLOR=#ff0000]# Will probably break system
[/COLOR]sudo sed -i "s/$(lsb_release -sc)/raring/" /etc/apt/sources.list;sudo apt-get update;sudo apt-get dist-upgrade
```
if you really want to try that backup your system 1st, you will probably regret it if you don't
if you try it tell me what happens i am curious

This does not work... as expected lol. It errors out while processing. I was curious enough to try it in a VM. Just letting others know before they try on real systems.

---

### Post by shakthi90 on 2013-06-06
[FONT=verdana]Backuped my data in a hardisk. Then I tried in terminal[/FONT]

sudo sed -i "s/$(lsb_release -sc)/raring/" /etc/apt/sources.list;sudo apt-get update;sudo apt-get dist-upgrade
[FONT=verdana]
The system got totally crashed [/FONT]:([FONT=verdana]. Do not use the above stuff. It is not working [/FONT]:confused:[FONT=verdana] .

Atlast, I Installed ubuntu 13.04 using my 4GB pendrive :)[/FONT]

---

### Post by 3rdalbum on 2013-06-06
> **shakthi90 said:**
> [FONT=verdana]Backuped my data in a hardisk. Then I tried in terminal[/FONT]

sudo sed -i "s/$(lsb_release -sc)/raring/" /etc/apt/sources.list;sudo apt-get update;sudo apt-get dist-upgrade
[FONT=verdana]
The system got totally crashed [/FONT]:([FONT=verdana]. Do not use the above stuff. It is not working [/FONT]:confused:[FONT=verdana] .

Atlast, I Installed ubuntu 13.04 using my 4GB pendrive :)[/FONT]

The guy did say that it would most likely break your system. This has not been a workable method of upgrading since about 2008, and never across so many versions of Ubuntu.

---

