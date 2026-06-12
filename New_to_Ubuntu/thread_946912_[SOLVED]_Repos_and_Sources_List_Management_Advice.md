---
title: "[SOLVED] Repos and Sources List Management Advice"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by maxuntu on 2008-10-13
Hi,

I'm quite new to Linux but I have a good (ish :)) understanding of how it works.

*Background*; I used Hardy for about 3 months and have recently upgraded to Intrepid, I can report I've not had a single issue yet! Great stuff. :guitar:
I do however have a big hole in my knowledge when it comes to repositories.:confused:

I get how they act as warehouses/containers for packages but from here on in I get a little lost. I've gone a bit mad and added repos (and keys for some) for Wine, dropbox, Google, etc and installed packages from them. Having upgraded to Intrepid I'm now left with all the repos referencing Hardy based packages. Thats ok, I can edit them to change distro to Intrepid. Question 1; will this work, can i just edit the distro for the repos or does it depend on the repo?

I'm also seeing some 404 errors (see below i) when updating (via synaptic) where some repos (or packages within those repos?) are unavailable.  Is is just that the repos have moved or gone down (I understand a 404 is just a 'not found').

I've posted my sources.list (see below ii) as hopefully someone will be able to see why this is happening and help me!? I guess I'm after a canned list of repos I can overwrite into my sources.list and be safe and happy knowing I've got the best and latest packages...?

Any help would be greatly appreciated and if anyone can provide a little insight into how repos work that would be great! I'm curious, if I add software from a repo then remove the repo does that just stop the package auto updating, are there any side effects etc? Apologies for any Windows terminology :mad:

i
```

Failed to fetch http://archive.ubuntu.com/dists/intrepid/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/intrepid/non-free/binary-i386/Packages.gz  404 Not found
Failed to fetch http://www.getdropbox.com/static/ubuntu/dists/intrepid/main/binary-i386/Packages.gz  404 Not Found [IP: 67.228.78.114 80]
Some index files failed to download, they have been ignored, or old ones used instead.

```

ii
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://www.getdropbox.com/static/ubuntu intrepid main
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
# deb http://ppa.launchpad.net/thielmann/ubuntu intrepid main
deb http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
# deb http://moblock-deb.sourceforge.net/debian intrepid main
# deb-src http://moblock-deb.sourceforge.net/debian intrepid main
deb http://archive.ubuntu.com intrepid main universe
# deb http://ppa.launchpad.net/conduit/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/conduit/ubuntu intrepid main
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports restricted main multiverse universe

```

Thanks in advance!!

---

### Post by kk0sse54 on 2008-10-13
Those repos that you're getting errors for I would go back to the sites where you found the repos and check that you have the right address since one either there is no intrepid repo for that site or you're looking for packages in the wrong directory.

---

### Post by k3lt01 on 2008-10-13
Many 3rd party repositories sources have not updated to Intrepid yet so this could be part of your issue. Another thing you could do for the official Ubuntu repositories is download them from the main server and see if this helps. Much of the problem is that Intrepid is still only in Beta.

There is one thing I did the other day to update my desktop system and that was to use the terminal when Update Manager wouldn't complete what it was doing. Use this code below

```
sudo apt-get update
```

then use

```
sudo apt-get upgrade
```
this will help to update the repositories that are working.

---

### Post by drs305 on 2008-10-13
maxuntu,

First, welcome to the ubuntu forums.

*Most of this is just background info, since you asked for some insight on the repositories.*

Something which I don't see discussed often concerning respository failures is how to interpret a 'failed to fetch' message. We will use one of the messages you received as an example:
```
Failed to fetch *http://archive.ubuntu.com/dists/intrepid/universe/binary-i386/Packages.gz*  404 Not Found
```

The message is saying that it went to the repository to fetch a package and couldn't locate it for some reason. 
Note: If an address is wrong and the repository list contains multiple entries on the same line (e.g. main, multiverse, universe, etc) a 'failed to fetch' error message will be generated for each entry (main, multiverse, etc).

To determine that reason, one thing you can do is to check the server address. We know it couldn't fetch (retrieve) *Packages.gz*. The problem may be with the package address or server.

In your web browser, start with the full address and back up until you get a positive result. Note - It would actually be faster to start at the base of [http://archive/ubuntu.com](http://archive/ubuntu.com) and go forward - take your pick:
```

http://archive.ubuntu.com/dists/intrepid/universe/binary-i386/Packages.gz  **404 Not Found** 
http://archive.ubuntu.com/dists/intrepid/universe/binary-i386/  **Not Found**
http://archive.ubuntu.com/dists/intrepid/universe/  **Not Found**
http://archive.ubuntu.com/dists/intrepid/  **Not Found**
http://archive.ubuntu.com/dists/  **Not Found**
http://archive.ubuntu.com/     ** Succcess **

or (going from the base address):

http://archive.ubuntu.com/     ** Succcess **
http://archive.ubuntu.com/dists/  **Not Found**

```
We now know **[http://archive.ubuntu.com/](http://archive.ubuntu.com/)** is valid and the server is working. If you get all the way to the top level and still get errors, it's probably a server error or a connection problem on your end.

Now that you have found a valid address, start checking the path to the subdirectories. Under the main address, we find the subfolder *dists/*

Click on ***dists*** to find:
Listings for dapper, feisty, gutsy, hardy, and ***intrepid***
You have now found the server's intrepid files at:
[http://archive.ubuntu.com/ubuntu/dists/intrepid/](http://archive.ubuntu.com/ubuntu/dists/intrepid/)
Inside the intrepid folder are subfolders for *main multiverse restricted and universe *, among others.

From here you could try to find a specific .deb package from within one of the folders.

You could probably also construct your own sources.list entry from what you have found. Modify the existing sources.list entry to reflect the proper path - in this case adding the extra '/ubuntu':
*[http://security.ubuntu.com/](http://security.ubuntu.com/)**ubuntu/***

To try to create your own path from the following entry:
[http://security.ubuntu.com/ubuntu/dists/intrepid/main/](http://security.ubuntu.com/ubuntu/dists/intrepid/main/)
Start the line with ***deb ***
[INDENT]*deb *[/INDENT]
Add the main address up to but not including the ***/dists*** folder:
[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
[INDENT]deb *[http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)*[/INDENT]
Add the version, assuming a folder for it exists:
[INDENT]deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) *intrepid*[/INDENT]
Add the names of any of the subfolders you want (which actually exist):
[INDENT]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid main multiverse[/INDENT]

Add it to your sources.list, update the repository list, and see if it produces errors or not. If not, you have successfully added/updated the repository. 

If you are trying to create a *new* repository you may not be able to access the packages until you import a 'key' from the server. You would have to check with the maintainer of the repository for the procedures to obtain this key.

Having said all this, remember that adding and using non-supported repositories may introduce additional risks to both security and the proper operation of your system.

Here are two links regarding repositories from the ubuntu community documentation:
[Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")
[Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine")

---

### Post by maxuntu on 2008-10-14
Thanks to all who have responded, especially drs305 (thanks for your time and welcome!).

I'll have a good read through your comments this evening and have a play with my sources.list, hopefully i'll get rid of those pesky errors!

Thanks again.

---

### Post by JSLR on 2010-12-09
> **maxuntu said:**
> Thanks to all who have responded, especially drs305 (thanks for your time and welcome!).

I'll have a good read through your comments this evening and have a play with my sources.list, hopefully i'll get rid of those pesky errors!

Thanks again.

Well, It's been two year's and I'm still waiting for an answer...

did it work?

---

### Post by maxuntu on 2010-12-09
:o

Unfortunately the machine in question is no longer with us :frown: 
Before the end (bad bios flash cooked the whole machine on next boot) I believe the issue was resolved... :p

My original question was quite lame but my understanding of repo's and their management was increased so \\:D/ thanks! Awesome community distributing free knowledge on a great subject!

Back then, I think I was looking for a spoon to feed to sources #-o 

My new rig has CrossfireX and doesn't seem to like the latest ubuntu so I've not been able to come back to it for a while now...:cry:
I will try harder..:)

---

