---
title: "can't open synaptic package manager"
date: 2008-03-13
forum: Philippine Team
---

### Post by killer_d76 on 2008-03-13
E: Malformed line 77 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

.. these are are errors i got when i try to open synaptic package manager.. right after following an instruction on the net on how to install 915 driver!,, how can i fix this?

---

### Post by scragar on 2008-03-13
can you paste your /etc/apt/sources.list file, or at the very least lines 70-85 or so

---

### Post by killer_d76 on 2008-03-13
arvin@arvin-laptop:~$ /etc/apt/sources.list file
bash: /etc/apt/sources.list: Permission denied

.. thanks for the quick reply scargar i got permission denied!

---

### Post by scragar on 2008-03-13
my fault, should have specified:
```
sudo cat /etc/apt/sources.list
```
or to open it in text editor(far easier in my opinion:
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by linuxisfree on 2008-03-13
```
sudo gedit /etc/apt/sources.list
```
 
and then copy and paste the contents.

---

### Post by killer_d76 on 2008-03-13
here are the list..

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
#Beryl stuff

deb [http://ubuntu.beryl-project.org/feisty](http://ubuntu.beryl-project.org/feisty) main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

---

### Post by scragar on 2008-03-13
```
deb http://ubuntu.beryl-project.org/feisty main
``` needs replacing with:
```
deb http://ubuntu.beryl-project.org feisty main
```

---

### Post by killer_d76 on 2008-03-13
WWOOOOHHHOOO!!!!!.... thanks guys!.. if you can only see me now jumping! :guitar: :guitar: :guitar: you guys  ROCK!

---

### Post by anonimo3030 on 2008-05-24
I have the same problem, this is my source.list file

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates universe multiverse
#AUTOMATIX REPOS END

Thanks,

---

### Post by scragar on 2008-05-24
no chance of an error to acompany that to cut the work we need to do to find it is there?
```
sudo apt-get update
```
paste output back please(not all of it, just the last part when it displays any errors, if your not sure just use the last 10 lines or so).


EDIT: OK, I tried your sources.list file myself, and no errors... Best paste output of any errors you get, along with what messages you get when opening the package manager.

---

### Post by killer_d76 on 2008-05-24
by the way, scargar thanks for all your help! ;).. i believe that i forgot to mention that.. :guitar:

---

### Post by Thrasonic on 2010-02-23
Now I'm having a problem similar to this as well.  The error message I get is this:

E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Here's my sources.list:

# deb cdrom:[Kubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to                    
# newer versions of the distribution.                                                        

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any  
## review or updates from the Ubuntu security team.                        
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe                   
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe               
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe           
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe       

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports

I know it's that last line, but what I don't know how to do is edit it directly to remove it.  When I go through Dolphin to the file, hold down the Ctrl key and right-click, then choose to open it with Kate I can see everythinhg.  When I remove the line and click Save, however, I get this error:

For file /etc/apt/sources.list no backup copy could be created before saving. If an error occurs while saving, you might lose the data of this file. A reason could be that the media you write to is full or the directory of the file is read-only for you.

And when I click the button labeled "Try to save nevertheless" I get this error message:

The document could not be saved, as it was not possible to write to /etc/apt/sources.list.

Check that you have write access to this file or that enough disk space is available.

Help???  :confused:

---

### Post by scragar on 2010-02-24
Unless you are compiling things from source it's safe to completely remove that last line:

```
sudo sed '$d' -i /etc/apt/sources.list
```

Or to do it yourself graphically:

```
sudo kate /etc/apt/sources.list
```

You might also try editing the last line and inserting types of content after the distro(which is the error, the file has a set rule for the lines: package-type url release type1...)

```
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports **restricted main multiverse universe**
```

Again edit this in graphically, or using the command line like so:

```
# first remove the old last line
sudo sed '$d' -i /etc/apt/sources.list
# then add in the new one:
echo "deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports estricted main multiverse universe" | sudo tee -a /etc/apt/sources.list
```

---

### Post by ecj on 2010-02-25
hello guys/girls i'm new to the forums.

having this same problem with not being able to open the synaptic package manager along with any other system-admin etc...

heres what it looks like after i sudo apt-get update...  ends with this error. 

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.


-And my source list is this:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe multiverse deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe multiverse
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

please help... i can't do anything but go on the internet..

---

### Post by scragar on 2010-02-28
> **ecj said:**
> hello guys/girls i'm new to the forums.

having this same problem with not being able to open the synaptic package manager along with any other system-admin etc...

heres what it looks like after i sudo apt-get update...  ends with this error. 

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.


-And my source list is this:

----

please help... i can't do anything but go on the internet..

You've missed a new line when you copied it:

```

deb http://security.ubuntu.com/ubuntu  jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
# deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"

deb http://archive.ubuntu.com/ubuntu jaunty universe multiverse

deb-src http://archive.ubuntu.com/ubuntu jaunty universe multiverse

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```

---

### Post by samurai793 on 2011-02-02
This is the Error that I am getting.


[B]E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
[/B]




# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed restricted main multiverse universe
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

---

### Post by jepong on 2011-02-02
i think.. just simply remove...


> deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

i wonder why you're mixing lucid and maverick's packages?

---

### Post by samurai793 on 2011-02-06
Now that the errors have been spotted out, how do I remove that.  Do I go through my "Terminal"?  And if so, what do command do I type to remove it?

---

### Post by jepong on 2011-02-06
/etc/apt/sources.list is actually a text file :lolflag:

it either you delete it or comment it out

---

### Post by nmmanu215 on 2011-05-30
Can't open the synaptic package manager...
the error message displayed was

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

please help...:(

---

### Post by webofunni on 2011-05-30
```

sudo dpkg --configure -a

```

works ?

---

### Post by fendijr on 2011-08-01
and open sources also. Mine suppost to be ver 11.04 but....



# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://localhost:9977/localhost:9977...y/UpgradeNotes](http://localhost:9977/localhost:9977...y/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://localhost:9977/localhost:9977...tu.com/ubuntu/](http://localhost:9977/localhost:9977...tu.com/ubuntu/) maverick-backports main restricted universe multiverse
deb-src [http://localhost:9977/localhost:9977...tu.com/ubuntu/](http://localhost:9977/localhost:9977...tu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://localhost:9977/localhost:9977...cal.com/ubuntu](http://localhost:9977/localhost:9977...cal.com/ubuntu) maverick partner
deb-src [http://localhost:9977/localhost:9977...cal.com/ubuntu](http://localhost:9977/localhost:9977...cal.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://localhost:9977/localhost:9977...ntu.com/ubuntu](http://localhost:9977/localhost:9977...ntu.com/ubuntu) natty main
deb-src [http://localhost:9977/localhost:9977...ntu.com/ubuntu](http://localhost:9977/localhost:9977...ntu.com/ubuntu) natty main

# deb [http://localhost:9977/localhost:9977...ntu.com/ubuntu](http://localhost:9977/localhost:9977...ntu.com/ubuntu) maverick main universe restricted multiverse
# deb-src [http://localhost:9977/localhost:9977...ntu.com/ubuntu](http://localhost:9977/localhost:9977...ntu.com/ubuntu) maverick universe main multiverse restricted #Added by software-properties
deb [http://localhost:9977/localhost:9977...tu.com/ubuntu/](http://localhost:9977/localhost:9977...tu.com/ubuntu/) maverick-security universe main multiverse restricted
deb-src [http://localhost:9977/localhost:9977...tu.com/ubuntu/](http://localhost:9977/localhost:9977...tu.com/ubuntu/) maverick-security universe main multiverse restricted
deb [http://localhost:9977/localhost:9977...ntu.com/ubuntu](http://localhost:9977/localhost:9977...ntu.com/ubuntu) maverick-updates universe main multiverse restricted
deb-src [http://localhost:9977/localhost:9977...ntu.com/ubuntu](http://localhost:9977/localhost:9977...ntu.com/ubuntu) maverick-updates universe main multiverse restricted
deb [http://localhost:9977/localhost:9977...ntu.com/ubuntu](http://localhost:9977/localhost:9977...ntu.com/ubuntu) maverick-backports universe main multiverse restricted
deb-src [http://localhost:9977/localhost:9977...ntu.com/ubuntu](http://localhost:9977/localhost:9977...ntu.com/ubuntu) maverick-backports universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe


please help me bro..
tq so much.

---

### Post by syedyaqubali on 2011-10-05
I AM GETTING THIS ERROR WHEN I OPEN SYNAPTIC .IT WILL ASK PASSWORD .AFTER GIVING THE PASSWORD THESE ERRORS WILL BE DISPLAYED.
AND I CAN'T OPEN UPDATE MANAGER ALSO.


E: Type '&#8220;deb' is not known on line 61 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by Rubi1200 on 2011-10-05
> **syedyaqubali said:**
> I AM GETTING THIS ERROR WHEN I OPEN SYNAPTIC .IT WILL ASK PASSWORD .AFTER GIVING THE PASSWORD THESE ERRORS WILL BE DISPLAYED.
AND I CAN'T OPEN UPDATE MANAGER ALSO.


E: Type '“deb' is not known on line 61 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Post the output of the following command please:

```
cat /etc/apt/sources.list
```

---

### Post by solringel on 2011-11-26
im getting the same error dont know how i got it and im new to ubuntu just using it only a couple of days now 

here is the error i am getting 


pc@LG-Laptop:~$ sudo apt-get update
[sudo] password for pc: 
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/webupd8team-gnome3-precise.list
E: The list of sources could not be read.

my sources.list file

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha i386 (20111122)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free #Skype

dont know how to make it work as i am very new to using linux any help is appreciated thanks

---

### Post by kiminaiseah on 2011-11-26
dont upgrade dist version via online

download first cdimage or dvdimage then apt-cdrom add ; apt-get dist-upgrade

---

### Post by poojasaraff on 2012-01-13
synaptic package manager not opening

error: W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-amd64_Packages)

my /var/lib/apt/lists directories contents are:

pooja@pooja-laptop:/var/lib/apt/lists$ ls
archive.canonical.com_ubuntu_dists_natty_partner_binary-amd64_Packages
archive.canonical.com_ubuntu_dists_natty_partner_source_Sources
archive.canonical.com_ubuntu_dists_natty_Release
archive.canonical.com_ubuntu_dists_natty_Release.gpg
archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources
archive.ubuntu.com_ubuntu_dists_natty_multiverse_source_Sources
archive.ubuntu.com_ubuntu_dists_natty_Release
archive.ubuntu.com_ubuntu_dists_natty_Release.gpg
archive.ubuntu.com_ubuntu_dists_natty_restricted_source_Sources
archive.ubuntu.com_ubuntu_dists_natty-security_main_binary-amd64_Packages
archive.ubuntu.com_ubuntu_dists_natty-security_main_source_Sources
archive.ubuntu.com_ubuntu_dists_natty-security_multiverse_binary-amd64_Packages
archive.ubuntu.com_ubuntu_dists_natty-security_multiverse_source_Sources
archive.ubuntu.com_ubuntu_dists_natty-security_Release
archive.ubuntu.com_ubuntu_dists_natty-security_Release.gpg
archive.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-amd64_Packages
archive.ubuntu.com_ubuntu_dists_natty-security_restricted_source_Sources
archive.ubuntu.com_ubuntu_dists_natty-security_universe_binary-amd64_Packages
archive.ubuntu.com_ubuntu_dists_natty-security_universe_source_Sources
archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources
archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-amd64_Packages
archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources
archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_binary-amd64_Packages
archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_source_Sources
archive.ubuntu.com_ubuntu_dists_natty-updates_Release
archive.ubuntu.com_ubuntu_dists_natty-updates_Release.gpg
archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-amd64_Packages
archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources
archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-amd64_Packages
archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources
dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-amd64_Packages
dl.google.com_linux_talkplugin_deb_dists_stable_Release
dl.google.com_linux_talkplugin_deb_dists_stable_Release.gpg
extras.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
extras.ubuntu.com_ubuntu_dists_natty_Release
extras.ubuntu.com_ubuntu_dists_natty_Release.gpg
lock
partial
security.ubuntu.com_ubuntu_dists_natty-security_main_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_natty-security_main_source_Sources
security.ubuntu.com_ubuntu_dists_natty-security_multiverse_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_natty-security_multiverse_source_Sources
security.ubuntu.com_ubuntu_dists_natty-security_Release
security.ubuntu.com_ubuntu_dists_natty-security_Release.gpg
security.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_natty-security_restricted_source_Sources
security.ubuntu.com_ubuntu_dists_natty-security_universe_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_natty-security_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty_Release
us.archive.ubuntu.com_ubuntu_dists_natty_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty-updates_Release
us.archive.ubuntu.com_ubuntu_dists_natty-updates_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources

---

### Post by poojasaraff on 2012-01-13
the above issue solved :)

just deleted the duplicate lines from the sources.list file

---

### Post by giordy69 on 2012-02-03
Hello 
 I have made a mistake somewhere I am new to linux I was installing cairo dock and now I have these errors and nothing runs properly

When I try to open synaptic package manager the following errors show:

E: Type &#8216;sudo&#8217; is not known on line 49 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

I do apologize for my incompetence :(

---

### Post by giordy69 on 2012-02-03
[QUOTE=giordy69;11661034]Hello 
 I have made a mistake somewhere I am new to linux I was installing cairo dock and now I have these errors and nothing runs properly

When I try to open synaptic package manager the following errors show:

E: Type &#8216;sudo&#8217; is not known on line 49 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

I do apologize for my incompetence :( and now it give me this:


Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Type &#8216;sudo&#8217; is not known on line 49 in source list /etc/apt/sources.list, E:The list of sources could not be read.

Do I have re-install ubuntu all over again?

this is my source list:
# deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release amd64 (20110211.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiversedeb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock



sudo apt-get update 
sudo apt-get install cairo-dock cairo-dock-plug-ins
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid cairo-dock # For Ubuntu 10.04
wget -q [http://repository.glx-dock.org/cairo-dock.gpg](http://repository.glx-dock.org/cairo-dock.gpg) -O- | sudo apt-key add -

---

### Post by itagomo on 2012-02-07
try mo to:


sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update

---

### Post by alikuto on 2012-02-08
I am a newbie. I tried to open SMP by Alt+F2 and type synaptic. I cannot open it. This is my sources list. Please solve it for me. Thanks 

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110426)]/ natty main restricted

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110426)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

---

### Post by kiminaiseah on 2012-02-14
unplug mo network mo bago ka mag open ng synaptic or bago ka mag boot ng ubuntu mo

kasi may automatic daemon yang ubuntu , upon bootup mag automatic gather ng update,

---

### Post by Gurtej22 on 2013-03-25
E: Malformed line 1 in source list /etc/apt/sources.list.d/google.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.   
 please help me

---

### Post by matt_symes on 2013-03-25
Hi

Welcome to the forums :D

Press ALT + F2 (I assume that still works if not use the Dash) and type this in the run dialog.

```
gedit /etc/apt/sources.list.d/google.list
```

Copy and paste the text that is displayed into your next post.

Kind regards

---

### Post by Gurtej22 on 2013-03-25
thanks 
 gedit /etc/apt/sources.list.d/google.list
The program 'gedit' is currently not installed. You can install it by typing:
sudo apt-get install gedit

---

### Post by schragge on 2013-03-25
What Ubuntu flavour are you using? Kubuntu? Lubuntu? Xubuntu? Anyway, if you're doing it in a terminal window, please post the output of
```
cat /etc/apt/sources.list.d/google.list
```

---

### Post by matt_symes on 2013-03-25
Hi

> The program 'gedit' is currently not installed.

..and that is why i generally recommend the terminal even in the **absolute beginners** sub forum :popcorn:

Kind regards

---

### Post by Gurtej22 on 2013-03-25
now i installed gedit
and output is
deb [http://dl.google.com/linux/chrome/deb/stable](http://dl.google.com/linux/chrome/deb/stable) main

---

### Post by Gurtej22 on 2013-03-25
i am using linux mint

---

### Post by schragge on 2013-03-25
A space is missing before *stable*:
```
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
```

---

### Post by matt_symes on 2013-03-25
Hi

@Gurtej22. If you click on the link you posted (reposted below) you will see that you get a page not found error.

[http://dl.google.com/linux/chrome/deb]("http://dl.google.com/linux/chrome/deb/stable")

This is why you are getting the error (at least in part).

Open a terminal and type

```
sudo rm /etc/apt/sources.list.d/google.list
```

Enter your password. It will not be echoed to the screen.

Then type

```
sudo apt-get update
```

**EDIT:**

I don't use google earth so i don't know if there's a ppa for it but you can install it manually according to this site.

[http://www.ubuntukiller.com/2013/03/how-to-install-google-earth-in-ubuntu.html](http://www.ubuntukiller.com/2013/03/how-to-install-google-earth-in-ubuntu.html)

If there's a better way to install it then i am happy to be corrected.

Kind regards

---

### Post by Gurtej22 on 2013-03-26
thanks
now synaptic is opening



but there is one more problem 
when i start linux mint it give sound , but one i play any song or video it does not give sound
plese help me.............

---

### Post by matt_symes on 2013-03-26
Hi

@[**[COLOR=#000000]Gurtej22[/COLOR]**]("http://ubuntuforums.org/member.php?u=1803562").

Please start a new thread with your sound issues as it is totally off topic to this thread.

Please specify as much information about your sound problems as possible including which applications you are trying to play sound in and what you have tried to fix it such as checking alsamixer.

As this thread was started in 2008, i am going to close it in keeping with CoC guide lines.

Thread closed.

Kind regards

---

