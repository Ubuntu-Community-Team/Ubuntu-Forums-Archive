---
title: "[SOLVED] Package Manager works one day, then fails the next."
date: 2008-10-15
forum: New to Ubuntu
---

### Post by danebramaged on 2008-10-15
...and I quote:

"An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.  The error message was:'Error: Opening the cache (E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-1386_Packages, E:The package lists or status file could not be parsed or opened.)'  This usually means that your installed packages have unmet dependencies"

So, I ran apt-get check in a terminal window and this is what I get:

isaac@Monolith:~$ apt-get check
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I then type:

isaac@Monolith:~$ sudo apt-get check
[sudo] password for isaac: 
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Should I try building dependancies? or something?  I just started messing around with linux and currently have no way of backing stuff up, so I thought maybe I'd better ask before getting too far ahead of myself.  

Please Help and Thanks.

---

### Post by hyper_ch on 2008-10-15
you can have only one package manager running at the same time... that's either adept or apt-get or aptitude or synaptic or ....

---

### Post by frankleeee on 2008-10-15
I have a problem with update manager at times but I just kill it and run reload in synaptic or apt-get, but I noticed in this part of your post a misspelling of Hardy.
repoubuntusoftware.info_dists_harty_all_binary-1386_Packages,
[http://ubuntuforums.org/showthread.php?t=948153](http://ubuntuforums.org/showthread.php?t=948153)
This thread will maybe help in the future.

---

### Post by jemate18 on 2008-10-15
> saac@Monolith:~$ sudo apt-get check
[sudo] password for isaac:
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_***[COLOR="Red"]harty[/COLOR]***_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Change harty to hardy

Thats the problem

---

### Post by mick222 on 2008-10-15
do you have the ULTAMATIX repos installed if so disable them from system - admin-software sources  The repos seem to be causing problems. Check Frankielees link

---

### Post by danebramaged on 2008-10-15
> **frankleeee said:**
> I have a problem with update manager at times but I just kill it and run reload in synaptic or apt-get, but I noticed in this part of your post a misspelling of Hardy.
repoubuntusoftware.info_dists_harty_all_binary-1386_Packages,
[http://ubuntuforums.org/showthread.php?t=948153](http://ubuntuforums.org/showthread.php?t=948153)
This thread will maybe help in the future.

synaptic has the same problem as package manager.  I see that Hardy is misspelled but, how can that be?  I copy and pasted the output text from the terminal window.  Wouldn't everybody who got the same updates end up having the same problem?

Anyway, I will checkout the thread and see where that leads me.

---

### Post by danebramaged on 2008-10-15
> **jemate18 said:**
> Change harty to hardy

Thats the problem

...of course I never bothered to check for typos because I was copy and pasting the output of a command from the terminal window...

The question would then be, "How do I change harty to hardy?".  If is all I have to do is find the file and rename it, then I think I can probably figure that out on my own.

It makes me wonder how many other people are having the same problem when there is a typo in an automated process.

---

### Post by noppie on 2008-10-15
Hello
I am having the same problem and i can not remember where to go to change the harty to hardy..any help would be great


noppie



> 
'W:Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy-security_restricted_binary-i386_Packages), W:Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy-security_multiverse_binary-i386_Packages), E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists[COLOR="Red"]_harty_[/COLOR]all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by danebramaged on 2008-10-15
> **frankleeee said:**
> I have a problem with update manager at times but I just kill it and run reload in synaptic or apt-get, but I noticed in this part of your post a misspelling of Hardy.
repoubuntusoftware.info_dists_harty_all_binary-1386_Packages,
[http://ubuntuforums.org/showthread.php?t=948153](http://ubuntuforums.org/showthread.php?t=948153)
This thread will maybe help in the future.

o.k., I am back from the thread and, here's what I've got.

isaac@Monolith:~$ sudo dpkg --configure -a
isaac@Monolith:~$ sudo apt-get install -f
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
isaac@Monolith:~$ sudo apt-get autoremove
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

So I took the advice to rename "harty" to "hardy" and this is what I got.

isaac@Monolith:/var/lib/apt/lists$ rename repoubuntusoftware.info_dists_harty_all_binary-i386_Packages repoubuntusoftware.info_dists_hardy_all_binary-i386_Packages
Bareword "repoubuntusoftware" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "info_dists_harty_all_binary" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "i386_Packages" not allowed while "strict subs" in use at (eval 1) line 1.
isaac@Monolith:/var/lib/apt/lists$ 

So now what do I do?  Is there some sort of maintenance mode I can get to during boot in which "strict subs" would NOT be in use?

pease hep me ...

---

### Post by VitaminBB on 2008-10-15
I had this same problem, fixed it but then the next day it comes back, this has happened three times now ...

I have renamed the file, saved it and it reverts or is overwritten to ...harty... causing an error again.

Any ideas how to solve this problem for good??

Should I or can I just delete the offending file?

---

### Post by VitaminBB on 2008-10-15
The location of the funked up file (for me) is ... [B]/var/lib/apt/lists 
[/B]
Dont forget to "***show hidden files***" as well or you wont see it ...

Also I went from terminal **sudo nautilus /var/lib/apt/lists **

This will open nautilus with root power, show hidden files, rename, then exit ...

The problem is the spelling error will reappear in a day or so, I havent figured out that part yet.

---

### Post by danebramaged on 2008-10-15
I found this here:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/283541](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/283541)


"Michael Vogt wrote 14 hours ago: (permalink)

Here is what is causing the error:

Package: btnx
Version: 0.4.4-1
Architecture: i386
Maintainer: Olli Salonen <email address hidden>
Installed-Size: 108
Depends:
Filename: ./btnx_0.4.4-1_i386.deb
Size: 17130
MD5sum: 6fb749892407120459f3ce57d750dcac
Section: checkinstall
Priority: extra
Description: A daemon for routing mouse button events as keyboard and mouse button combos

The depends line there is empty, that makes it crash."


That makes sense I guess HOWEVER, until I can get apt-get or synaptic package manager to actually work, how can I d/l a version of anything that might solve the problem?  (rhetorical question, I'm just in fowl mood)


I will try the above suggestion from VitaminBB running nautilis as root and check back in a bit.

tayl

---

### Post by danebramaged on 2008-10-15
> **VitaminBB said:**
> The location of the funked up file (for me) is ... [B]/var/lib/apt/lists 
[/B]
Dont forget to "***show hidden files***" as well or you wont see it ...

Also I went from terminal **sudo nautilus /var/lib/apt/lists **

This will open nautilus with root power, show hidden files, rename, then exit ...

The problem is the spelling error will reappear in a day or so, I havent figured out that part yet.

Keep taking your vitamins.  IT WORKED.  Yeah.  Now I can get my security fixes and I no longer have to look at that RED EYE staring at me from the task bar.

Thanx.

---

