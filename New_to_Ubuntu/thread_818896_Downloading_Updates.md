---
title: "Downloading Updates"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Springy2 on 2008-06-04
A few days ago I started to get this triangle with an exclamation mark saying my update info is out dated

When I run the  Update Manager after downloading the packages info it gives this message:

[I]"Could not download all repository indexes

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead."
[/I]

Same message shows when I reload the Synaptic packages manager

What do I do? if anything

---

### Post by tamoneya on 2008-06-04
go into synaptic and select preferences -> repositories.  Then there is a drop down that allows you to change the mirror.  See if this soves anything.

---

### Post by Joeb454 on 2008-06-04
Install a newer version of Ubuntu.

Edgy Eft isn't supported anymore. You will need to upgrade to 7.04 or later for a currently supported version.

Support for the versions end as such:

7.04 ends in October 2008
7.10 ends in April 2009
8.04 ends in April 2011 (it's an LTS)

---

### Post by Springy2 on 2008-06-04
Sorry I forgot to mention I am using Ubuntu 8.04

> **tamoneya said:**
> go into synaptic and select preferences -> repositories.  Then there is a drop down that allows you to change the mirror.  See if this soves anything.

I don't see such option there
There is a Download From option in Software Sources, I selected main server and some other servers across the world, same error appears

---

### Post by Joeb454 on 2008-06-04
Oh, well that could also be your issue then - [HTML]http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz[/HTML]

As you can see above - your system seems to be trying to download from the Edgy Eft repo's, which are no longer enabled.

---

### Post by Springy2 on 2008-06-04
So I just ignore it?

---

### Post by iaculallad on 2008-06-04
Navigate to System->Administration->Software Sources, On the "Ubuntu Software" tab, select/change to "Main Server" from the Download from: Close the window.

Go to terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Joeb454 on 2008-06-04
Try commenting it out?

```
gksudo gedit /etc/apt/sources.list
``` provided they don't all say edgy - you just put a # at the start of the line :)

---

### Post by drs305 on 2008-06-04
> **Springy2 said:**
> So I just ignore it?


Delete the following line after making a backup of sources.list:
```

sudo cp /etc/sources.list /etc/sources.list.bak
gksudo gedit /etc/sources.list

```

Find this line, delete it, and save the file. If you see a lot of lines with *edgy* then tell us.
```

http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz
```

then run:
```

sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Springy2 on 2008-06-04
> **iaculallad said:**
> Navigate to System->Administration->Software Sources, On the "Ubuntu Software" tab, select/change to "Main Server" from the Download from: Close the window.

Go to terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

Did that, it didn't fix it

> **Joeb454 said:**
> Try commenting it out?

```
gksudo gedit /etc/apt/sources.list
``` provided they don't all say edgy - you just put a # at the start of the line :)

Which line do I comment out, this?

```
deb http://us.archive.ubuntu.com/ubuntu edgy universe
```

---

### Post by drs305 on 2008-06-04
> **Springy2 said:**
> Did that, it didn't fix it



Which line do I comment out, this?

```
deb http://us.archive.ubuntu.com/ubuntu edgy universe
```

Yes, but you have now quoted 2 lines mentioning edgy. There are probably more. There should be no references to edgy. If you aren't sure you can post the contents for us to look at:
```
cat /etc/apt/sources.list
```

---

### Post by Springy2 on 2008-06-04
From what I see thats the only line in that file that mentions edgy, anyway just to be safe and clear its content is:

```

# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse

#AUTOMATIX REPOS START

# deb http://www.getautomatix.com/apt gutsy main

deb http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu edgy universe

#AUTOMATIX REPOS END
# deb http://ppa.launchpad.net/fta/ubuntu hardy main
```

---

### Post by drs305 on 2008-06-04
Delete or comment the 3 lines in bold. Save the file, run an update and you should be good.

```
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
**deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse**
**deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse**

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse

#AUTOMATIX REPOS START

# deb http://www.getautomatix.com/apt gutsy main

deb http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

**deb http://us.archive.ubuntu.com/ubuntu edgy universe**

#AUTOMATIX REPOS END
# deb http://ppa.launchpad.net/fta/ubuntu hardy main
```

Just a note. The first two lines of the file refer to your feisty Cdrom. Should you ever try to use a CD as a source by checking it in StartUp-Manager, you will be asked to insert the cd. It will be asking for your FEISTY cd - even if you are updating Hardy. You can leave those lines commented or delete them. If you no longer have the feisty cd, you might as well get rid of the lines.

Please mark this solved if editing the sources.list file works.

---

### Post by Springy2 on 2008-06-04
Indeed it's all good now

Thanks allot all :)

---

### Post by MudRacer on 2008-09-06
I am running Ubuntu 8.04 as well. 

Whenever i ran the update manager. I got the same error. Also that triangle would appear every once in a while. 

I followed the directions above and removed those two lines. They have fixed the problem!

Thanks!!

---

