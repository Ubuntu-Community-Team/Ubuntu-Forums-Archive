---
title: "Error with update manager"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by PatronSaint on 2008-05-24
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--20:20:07--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

Any help would be awesome...thanks in advance.

---

### Post by drs305 on 2008-05-24
There is an error with your medibuntu listing in /etc/apt/sources.list

Please post the results of:

```
cat /etc/apt/sources.list
```

Alternatively, you can open your sources.list and uncheck medibuntu until you get it resolved. Do this by opening synaptic, then Settings, Respositories, Third Party and uncheck the medibutu sources.

---

### Post by PatronSaint on 2008-05-24
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
home@home-laptop:~$                                                       

I tried to open my synaptics but it won't open...

---

### Post by drs305 on 2008-05-24
At first glance I don't see anything wrong with the sources.list.

What happened when you tried to open synaptic? Any error messages?

Since the problem may have been with something wrong in the medibuntu folder, lets temporarily rename that folder. Then try to open synaptic again. If it still doesn't open, run the second command to restore the original name of the folder.

```
sudo mv /etc/apt/sources.list.d/ /etc/apt/sources.list.d-old
```

If synaptic still won't open, restore folder name:
```
sudo mv /etc/apt/sources.list.d-old/ /etc/apt/sources.list.d
```

---

### Post by PatronSaint on 2008-05-24
I typed in the first code you gave me and it all seems to work, thank you very much!

This is my 3rd Ubuntu install on people's computers (I'm trying to convert everyone ;D) and I was trying to install the code to let DVD's and so forth run on the machine. Well, hopefully it all works now. 

Thanks again, 
PatronSaint

---

### Post by drs305 on 2008-05-24
Okay, we should now restore your medibuntu source to a working condition. This is not required, but here are the commands that should restore it.

```

sudo mkdir /etc/apt/sources.list.d/
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Finally, if everything works, you can delete the renamed old folder. Before deleting it, you might want to see if there are any other files in it, such as any wine files. If there are you can move them to the new medibuntu folder if you wish. I would do both these things later once you are sure everything is ok.
```
sudo rm /etc/apt/sources.list.d-old
```

---

