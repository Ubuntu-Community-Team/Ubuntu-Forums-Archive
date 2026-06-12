---
title: "synaptic and medibuntu problems"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by Happycamper374 on 2008-10-27
Hi all,

I've just reinstalled hardy onto my laptop and tried to get the mediubuntu repository working. I screwed it up though. When I do the apt-get update and install and update command at the end, I get an error message which says 
E: type '--19:33:46--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

There have been at least 2 other posts on this issue and I've tried to follow the directions in them to fix a very similar problem. They all ended up with opening up a file and editing what I'm guessing was the repository information. I tried that and it didn't work. Any help?

Thanks

---

### Post by Happycamper374 on 2008-10-27
Also, since this seems to be the first step in both threads, here's what I get when I do this:

paul@paul-laptop:~$ cat /etc/apt/sources.list.d/medibuntu.list


## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

---

### Post by 32footsteps on 2008-10-27
I am having the same problem.  I wonder if the issue is with the link.  I have no problems when I intially add it to the repos, but once I go to add/remove anything I get the error...

---

### Post by Happycamper374 on 2008-10-27
Bump for the normal US daytime hours...

---

### Post by bapoumba on 2008-10-27
I just did it the old fashion way, adding this line to my /etc/apt/sources.list:
```
deb http://packages.medibuntu.org/ hardy free non-free
```

Then reload the file with:
```
sudo apt-get update
```

---

### Post by Happycamper374 on 2008-10-27
I still get the error message...

paul@paul-laptop:~$ sudo apt-get update

E: Type '--19:33:46--' is not known on line 1 in source list /etc/apt/sources.list.d/mediubuntu.list

I'm pretty new to rooting around with the terminal and playing with whatever it is we're playing with so we might need to go back a few steps and start from square one. Thanks for your help.

---

### Post by philinux on 2008-10-27
Well it's telling you that theres an error on line 1.

Post the full listing anyway.

cat /etc/apt/sources.list

---

### Post by Happycamper374 on 2008-10-27
K

paul@paul-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free


paul@paul-laptop:~$

---

### Post by zvacet on 2008-10-28
You can delete medibuntu lines(file)that you saved under /etc/apt/sources.list.d and add line to your source list as **bapoumba** adviced you.

---

### Post by bapoumba on 2008-10-28
> **zvacet said:**
> You can delete medibuntu lines(file)that you saved under /etc/apt/sources.list.d and add line to your source list as **bapoumba** adviced you.
zvacet, have you tried the recommended method from medibuntu site ? Did not work for me on several computers (Hardy and Intrepid).. 

To the OP: please post what is in /etc/apt/sources.list.d

---

### Post by zvacet on 2008-10-28
@ **bapoumba**

Recommended method work for me,but I was confused because I didn´t find line under sources.list.My sources.lst.d look exactly as in **Happycamper374** second post.

Can you tell me why I don´t see files in sys tray when I mimnimize them?I know it is off topic but it heppened right now when I checked my sources.list.d.

TNX

---

### Post by Happycamper374 on 2008-10-28
paul@paul-laptop:~$ ls /etc/apt/sources.list.d
medibuntu.list  medibuntu.list~  medibuntu.list.bak  mediubuntu.list


Thanks for being patient. I can't get on the interweb that often.

---

### Post by Happycamper374 on 2008-10-28
@ zvacet

I'm not quite sure how to do that. I didn't know the terminal commands so I navigated there using the gui and it won't let me delete the files in the /etc/apt/sources.list.d directory.

---

### Post by zvacet on 2008-10-29
```
cd /etc/apt/sources.list.d
```

Once inside type **ls** just to see content of the folder.

Still in that folder run 

```
sudo rm -f *
```

After that 

```
gksudo gedit /etc/apt/sources.list
```

and add the line

```
deb http://packages.medibuntu.org/ hardy free non-free
```

save and closee file.

```
sudo apt-get update
```

---

### Post by mc4man on 2008-10-29
The error seems to be referring to /etc/apt/sources.list.d/medibuntu.list. (post 1
This is where the medibuntu entry is made when you use wget ('the recommended method'. 
There usually won't be a sources.list entry when using wget

Maybe delete all the entries, files and start over (either manual entry(s) in sources.list or copy and paste wget command and get key command from medibuntu repo page

(2 files in sources.list.d, 2 entries in sources.list to delete

---

### Post by bapoumba on 2008-10-29
> **zvacet said:**
> @ **bapoumba**

Recommended method work for me,but I was confused because I didn´t find line under sources.list.My sources.lst.d look exactly as in **Happycamper374** second post.

Can you tell me why I don´t see files in sys tray when I mimnimize them?I know it is off topic but it heppened right now when I checked my sources.list.d.

TNX
In Happycamper374's post #2 (which I missed yesterday), looks like the first line may be blank or corrupted somehow. Happycamper374, please follow zvacet advice (remove the sources.list.d and add the line in sources.list) and it should work. This is the way I do it. But again, when a new Ubuntu version comes out, I do not upgrade but run a new install. Maybe medibuntu uses the sources.list.d not to mess up with online version upgrades ?

As far as the sys tray, is this with xfce or gnome?

---

### Post by Happycamper374 on 2008-10-29
Thanks guys, there wasn't an error message so I'm assuming that means it worked. 

Thanks for the help,

Happy

---

### Post by zvacet on 2008-10-29
@ **bapoumba**

It is a GNOME.Tnx for asking and willing to help me off topic.

---

### Post by NWSmart on 2008-11-04
Zavacet,
Thanks for your post - I had the same problem with a broken file and your instructions got this NOOB out of the pooh.

Thanks again

---

