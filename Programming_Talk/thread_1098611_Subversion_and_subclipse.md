---
title: "Subversion and subclipse"
date: 2009-03-17
forum: Programming Talk
---

### Post by tenmilez on 2009-03-17
I'm running 64bit Intrepid, Eclipse 3.4 Ganymede with Subversion 1.5(.1?) via apt-get and Subclipse via the Software Updates menu within Eclipse using [http://subclipse.tigris.org/update_1.4.x](http://subclipse.tigris.org/update_1.4.x).

To configure Subversion I... 
```
mkdir ~/.repos
svnadmin create ~/.repos

gedit ~/.repos/conf/passwd
``` 
Added:
christopher = christopher 
```
gedit ~/.repos/conf/svnserve.conf
```
Uncommented:
[general]
password-db = passwd
```
svnserve -d -r /home/christopher/.repos
```

When I try to connect via subclipse using svn://christopher@localhost/ I get an error saying the connection was refused by the server (I'm at work so I can't type out the exact message)

Other variations I've tried: 
svnserve **-i** so that I can close and restart easier. 
adding a subfolder, ~/.repos/apps after removing ~/.repos to make sure that I started fresh. Then trying the same svn://... with and without /apps at the end. 
Changing the permissions of ~/.repos to a new svn group and added myself to the group (and restarted the computer)

It's not exactly a fresh install, but I just installed Sunday night so I can't have done too much damage so far (mostly been getting flash sound to work).

I had it working on 32bit Intrepid, but I'm not sure if there's some firewall or something setup in the 64 bit version or if I'm just missing something stupid. I know I've read through about 20 guides so far though.

---

### Post by tenmilez on 2009-03-17
Might also be worth mentioning that I had my repos folder from before the reinstall of Ubuntu (/home is on a second drive) and I had tried to startup svnserve the same way I did before and it didn't work anymore. I don't think there any configurations that occur outside of the repos folder so it should've stayed the same, right?

---

### Post by tenmilez on 2009-03-17
Well, I finally got it working, though I'm not 100% sure why. I thought that what I just tried (that worked) I had tried last night, but I must not have. It's either something I screwed up with the permissions or using svnserve -i. I'll have to look up what exactly it is.

---

### Post by zarthon on 2009-08-10
I am running:
Ubuntu 9.04 64-bit  without back-ports repository enabled
Eclipse SDK Version: 3.2.2 Build id: M20070212-1330 (Ubuntu version: 3.2.2-5ubuntu3)
Which seems to be the latest version in the Ubuntu Jaunty repository.

Are others using a back-ports version or are you installing a version downloaded from the project?
Are you running the version that runs on the Java JRE or a gcj version?

I can't get subclipse to install using instructions fromt the subclipse project website. I added the site to the places eclipse looks for plug-ins and updates and it finds nothing that applies to my system.

---

