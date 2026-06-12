---
title: "help error on adding and removing applications menu"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by puleo1333774 on 2008-09-29
when im opening my add and remove applications this error messages are popping out, can you help me with this??? 

[ATTACH][ATTACH]86732[/ATTACH][/ATTACH]



E: Type 'echo' is not known on line 66 in source list /etc/apt/sources.list
E: Unable to lock the list directory:(

---

### Post by drs305 on 2008-09-29
There is an error in your sources.list.
Backup sources.list and open for editing (it will open to line 66 where the error is reported):
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksudo gedit +66 /etc/apt/sources.list

```

If you have a line with only "echo", delete it and save the file.
Probably a user tried to add a repository with the 'echo' command but it wasn't input correctly. If the line starts with "echo" and then continues normally, just delete "echo". 

If you don't know how to correct sources.list, just post it here and we can help.

If you think you corrected it, run "sudo apt-get update" and "sudo apt-get upgrade" and see if the problem is resolved.

---

### Post by Elfy on 2008-09-29
You need to fix your sourcs list, please post it here. Open a terminal from accessories menu and run this command ```
cat /etc/apt/sources.list
``` copy the resulting output into a new post please.

---

### Post by puleo1333774 on 2008-09-29
> **drs305 said:**
> There is an error in your sources.list.
Backup sources.list and open for editing (it will open to line 66 where the error is reported):
```

cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksudo gedit +66 /etc/apt/sources.list

```

If you have a line with only "echo", delete it and save the file.
Probably a user tried to add a repository with the 'echo' command but it wasn't input correctly. If the line starts with "echo" and then continues normally, just delete "echo". 

If you don't know how to correct sources.list, just post it here and we can help.

If you think you corrected it, run "sudo apt-get update" and "sudo apt-get upgrade" and see if the problem is resolved.

it says:
[ATTACH]86734[/ATTACH]

---

### Post by puleo1333774 on 2008-09-29
> **forestpixie said:**
> You need to fix your sourcs list, please post it here. Open a terminal from accessories menu and run this command ```
cat /etc/apt/sources.list
``` copy the resulting output into a new post please.

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main' 

sudo tee -a /etc/apt/sources.list


echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main'
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
andrew@andrew-desktop:~$

---

### Post by drs305 on 2008-09-29
Yes, you need to be root, so run it as:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

If you just post the results as forestpixie asked we can fix it for you.

---

### Post by Elfy on 2008-09-29
Any line in the sources list should look *similar* to either of these - anything else is wrong

deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) hardy main

What have you done recently to cause the problem, have you tried to add a repository?

---

### Post by Elfy on 2008-09-29
Delete lines

echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main' 

sudo tee -a /etc/apt/sources.list


echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main'
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main

save file and rerun sudo apt-get update

---

### Post by drs305 on 2008-09-29
At the bottom of the file, replace this:
```

echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'

sudo tee -a /etc/apt/sources.list


echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main'
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

With this:
```

deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main

```

---

### Post by puleo1333774 on 2008-09-29
> **forestpixie said:**
> Any line in the sources list should look *similar* to either of these - anything else is wrong

deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) hardy main

What have you done recently to cause the problem, have you tried to add a repository?

im trying to add this application
'avant-window-navigator_0.2.1.orig.tar.gz'

i'm  sorry cause im only a beginner here in ubuntu

---

### Post by puleo1333774 on 2008-09-29
> **drs305 said:**
> At the bottom of the file, replace this:
```

echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'

sudo tee -a /etc/apt/sources.list


echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main'
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

With this:
```

deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main

```

thank you this solved my problem :)

---

### Post by Elfy on 2008-09-29
Ok if you want to add the awn stuff to the file open the file to edit it once more

Add this to the end of the file

#AWN Repos
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main

Run ```
sudo apt-get update
``` once more, awn is available from the repos with ```
sudo apt-get install  avant-window-navigator
``` if that is what you were trying to achieve

---

### Post by puleo1333774 on 2008-09-29
> **forestpixie said:**
> Ok if you want to add the awn stuff to the file open the file to edit it once more

Add this to the end of the file

#AWN Repos
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main

Run ```
sudo apt-get update
``` once more, awn is available from the repos with ```
sudo apt-get install  avant-window-navigator
``` if that is what you were trying to achieve

thank you very much :)

---

