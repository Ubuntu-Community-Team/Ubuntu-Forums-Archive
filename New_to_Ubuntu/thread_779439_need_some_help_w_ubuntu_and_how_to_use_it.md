---
title: "need some help w/ ubuntu and how to use it"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by fignig on 2008-05-02
so i finally switched over from windows xp to ubuntu dapper 6.06LTS and i wanted to know the following:

-how do i install wine, english plz.

-how to i upgrade the version to 8.08 or w/e

-how do i install programs in general

-wtf to do. lol.

---

### Post by teaker1s on 2008-05-02
applications-add/remove
or terminal
```
sudo synaptic
```
search click install. you may want to uncomment extra repositories, for more programs

---

### Post by MattBD on 2008-05-02
Best way to upgrade to Hardy in my opinion is to just do a fresh install. As for installing, you need to use Synaptic to install programs, or you can use the command line.

Hate to blatantly plug it, but I have a blog that you might find useful at [http://easierbuntu.blogspot.com/](http://easierbuntu.blogspot.com/) - if you look at some of the entries from January 2008, these explain how you can install software from the command line easily.

---

### Post by fignig on 2008-05-02
i'm not really sure how to use this ubuntu, and how to install programs, and such

i feel when you guys talk about how to install programs and to do simple tasks that you speak in jargon that i cannot simply understand.

i am a windows users from DOS to XP. i've used windows and windows only my whole life. i feel it very necessary to cut off my dependancy on such a vile OS/company.

i just want to learn how to:

-upgrade from my now, 6.06LTS dapper to the 8.08 w/e. i have the iso image and i usually mount the image w/ daemon tools or alcohol150, but i am not in windows so i don't know how to mount iso images

-install programs, espeically wine. this seems to be the most elusive of them all, i've already tried to look on this "synaptic package manager" and cannot find a single trace of it. i already d/l'd the newest version from the winehq.com and i have no idea how to implement it.


plz help.

---

### Post by fignig on 2008-05-02
i have no idea how to use any of this. they might as well have put it all in french...

---

### Post by fignig on 2008-05-02
so to #1, ty for not helping, and #2 do u have any links to such posts?

---

### Post by frup on 2008-05-02
If you want to upgrade from CD/Iso you need to download the Ubuntu alternate CD.

Otherwise you should be able to upgrade from 6.06 to 8.**04** via the internet directly.

If you don't want to upgrade and would prefer to do a clean install (can be easier in some ways, a lot of people seem to prefer it although I personally am neutral) you can use the plain i386 desktop liveCD for 8.04

As for wine, the best place to get that is from winehq.org They have a repo there which you can to download the latest version of wine when ever it comes out. The instructions should be simple to follow, especially if you already have ubuntu experience.

---

### Post by aysiu on 2008-05-02
> **teaker1s said:**
> applications-add/remove
or terminal
```
sudo synaptic
```
search click install. you may want to uncomment extra repositories, for more programs
It would be *gksudo synaptic*, actually, but why do that when you can go to System > Administration > Synaptic Package Manager?

To the OP, there is no Ubuntu 8.08. The latest version is 8.04.

Instructions for upgrading Ubuntu:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Instructions for installing software (applies to Wine also):
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Tatty on 2008-05-02
I am not totally sure about upgrading from 6.06 to 8.04.  You can only upgrade one distro at a time normally ie 6.06->6.10->7.04 etc.  

I am not sure if there are any exceptions when it comes to upgrading LTS -> LTS versions, but I imagine not.  So unless someone posts with better information on this then i suggest the best method for you to upgrade will be a clean install.


wine should be in the repos, or at least it is in hardy, i am not sure about dapper.

To install from the winehq site use this page: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)  In short its simply two lines which you need to copy and paste into the terminal.
You will need to update this after an upgrade though.

---

### Post by MattBD on 2008-05-02
[This post explains apt-get]("http://easierbuntu.blogspot.com/2008/01/apt-get.html"), which is used to install software. You might also want to read [this one about apt-cache]("http://easierbuntu.blogspot.com/2008/01/apt-cache.html"), which is used to find software you want.
For newbies, Add/Remove Applications is a good way of installing applications. Synaptic is better for installing particular packages - I'm surprised you're having difficulty with it, it's normally pretty good, though I personally prefer Adept in Kubuntu.

---

### Post by RiceMonster on 2008-05-02
If you want to install Wine, there's two ways you can do it:

1) In a Terminal

Go to Applications > Accessories > Terminal
and type
```
sudo apt-get install wine
```

2) OR, if you want to get a nice graphical interface, go to Applications > Add/Remove... Then click on Office, and scroll down to the bottom. Click on Wine Windows Emulator then click Apply changes

Make sure where it says show at the top you have it set to "All available applications".

---

### Post by fignig on 2008-05-02
all i want to know right now is how to upgrade from 6.06LTS to the newst version of ubuntu. i need plain and simple english directions. i have the 8.04 iso file, but i do not know how to mount it. i do not have any programs installed b/c i do not know how to install programs. stop replying in such a manner that is unfamiliar to me, SIMPLE DIRECTIONS PLZ.

---

### Post by |{urse on 2008-05-02
in order to mount and browse iso's 

> sudo mkdir /media/iso
sudo mount -t iso9660 filename.iso /media/iso -o loop
sudo nautilus /media/iso

though i definitely would suggest you do not upgrade in this manner.

---

### Post by |{urse on 2008-05-02
Also i would add not to bpther running daemon tools in wine. The linux equivalent to daemon tools is Kiso you can get it thru apt

> 
sudo apt-get install kiso

^^

---

### Post by teaker1s on 2008-05-02
your welcome:twisted:

[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by |{urse on 2008-05-02
Also Also LOL don't mean to triple post but heres a nice script someone wrote you can cut, paste, make executable (sudo chmod +x filename) and run (sudo filename) that will do the same thing. Thank them if it helps.

[http://ubuntuforums.org/showthread.php?t=87369](http://ubuntuforums.org/showthread.php?t=87369)

---

### Post by kansasnoob on 2008-05-02
I'm surprised you started with 6.06 (aka Dapper) right now, but the good news is that you can upgrade directly from Dapper to Hardy.

That's assuming that your hardware supports Hardy.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Oldsoldier2003 on 2008-05-02
> **fignig said:**
> all i want to know right now is how to upgrade from 6.06LTS to the newst version of ubuntu. i need plain and simple english directions. i have the 8.04 iso file, but i do not know how to mount it. i do not have any programs installed b/c i do not know how to install programs. stop replying in such a manner that is unfamiliar to me, SIMPLE DIRECTIONS PLZ.

if you want to do a cd based upgrade you need to download and burn the alternate install cd. then just put it in your cd drive and it will prompt you to upgrade.

---

### Post by frup on 2008-05-02
Here is a screenshot of where synaptic package mananger should be. I can't quite remember 6.06 properly but I believe it was in a similar place with a similar name. I'm pretty sure the icon was different.

Another thought was, you are using Ubuntu and not the KDE version Kubuntu right?

---

### Post by frup on 2008-05-02
Can a mod merge users two threads.

---

### Post by frup on 2008-05-02
Hey man, that's 3 threads you've made asking basically the same questions. Just read the replies in the threads you have already made and ask questions in them. If you spam the forums people might be more reluctant to help you.

---

### Post by monkeymoo on 2008-05-02
You either use the Alternate CD. Or upgrade via update manager. 

If you want to use the update manager then: Press Alt-F2 and type ```
gksu "update-manager -d"
``` and run. 

Your update manager should come up. First click "check" to check for new updates, then click install updates. After that's finished you can then click the "upgrade" button at the top where it should be offering to upgrade you to 8.04. 
Then you just follow the on screen instructions. The whole process will take a few hours. 

The alternate cd method is as the other poster said. Download the iso, burn it to CD, put it in the drive and follow the instructions.

---

### Post by Sef on 2008-05-02
[Duplicate post]("http://ubuntuforums.org/showthread.php?p=4865925#post4865925").  Locked.

---

### Post by Sef on 2008-05-02
[Duplicate Post]("http://ubuntuforums.org/showthread.php?p=4865925#post4865925").  Locked.

---

### Post by aysiu on 2008-05-02
> **fignig said:**
> all i want to know right now is how to upgrade from 6.06LTS to the newst version of ubuntu. i need plain and simple english directions. i have the 8.04 iso file, but i do not know how to mount it. i do not have any programs installed b/c i do not know how to install programs. stop replying in such a manner that is unfamiliar to me, SIMPLE DIRECTIONS PLZ.

> **aysiu said:**
> 
Instructions for upgrading Ubuntu:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

> **kansasnoob said:**
> I'm surprised you started with 6.06 (aka Dapper) right now, but the good news is that you can upgrade directly from Dapper to Hardy.

That's assuming that your hardware supports Hardy.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) I don't see how more plain and simple the directions can be. I'll explain a bit more, then.

Do you see that link that has the word *upgrading* at the end (the link both kansasnoob and I referred to earlier in the thread)? Hover your mouse over the link and press the mouse button. Clicking the link will take you to a screenshot-laden webpage with instructions on upgrading to Ubuntu 8.04.

If you get stuck on any of those directions, let us know where you're stuck, and we will help you.

---

