---
title: "E: Malformed line 59 in source list /etc/apt/sources.list (URI parse)"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by zithe on 2008-04-29
I'm sorry I posted this in the wrong spot, but your permissions setup allowed me to post here but not the beginner's section for some reason...

I'm unable to access Add/Remove. I receive the following Message:

[I]Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.[/I]

Here is this other list I forget the name of but I know is important: [I]
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.[/I]

I'm using 7.10. All help is appreciated!

Thanks!
Josh

---

### Post by Sef on 2008-04-30
Could you please post your sources list? 

Open your terminal (Applications > Accessories > Terminal)

then type in this command:

```
gksudo gedit /etc/apt/sources.list
```

copy and paste your sources list in a new post.

---

### Post by zithe on 2008-04-30
> **Sef said:**
> Could you please post your sources list? 

Open your terminal (Applications > Accessories > Terminal)

then type in this command:

```
gksudo gedit /etc/apt/sources.list
```

copy and paste your sources list in a new post.

Oops. Sorry, here:


# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg)
sudo apt-key add -
sudo apt-key add -
sudo apt-get update

---

### Post by anantshri on 2008-04-30
IS the below listed lines in you sources.list

wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg)
sudo apt-key add -
sudo apt-key add -
sudo apt-get update


if yes please remove them and then use it.

this will solve your problem

---

### Post by Nepherte on 2008-04-30
> wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg)
sudo apt-key add -
sudo apt-key add -
sudo apt-get update
Those commands should be entered in a terminal and not in the sources.list file.

---

### Post by zithe on 2008-04-30
> **anantshri said:**
> IS the below listed lines in you sources.list

wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg)
sudo apt-key add -
sudo apt-key add -
sudo apt-get update


if yes please remove them and then use it.

this will solve your problem

I'm sorry? Delete those lines? Did nothing. Should I restart?

---

### Post by Nepherte on 2008-04-30
After you removed them, you should update again:
```
sudo apt-get update
```

---

### Post by zithe on 2008-04-30
> **Nepherte said:**
> After you removed them, you should update again:
```
sudo apt-get update
```

Put that in the terminal? got me "E: Malformed line 59 in source list /etc/apt/sources.list (URI parse)"

Should I add that somewhere else? No more ideas??

---

### Post by zithe on 2008-04-30
Aww. Nothing left?

---

### Post by PeterJS on 2008-04-30
I think the lack of responses might be related to the fact that you might not have successfully updated your sources list, take a look at it again. Are the bad entries still there? What exactly is on line 59?

---

### Post by forestpixie on 2008-04-30
Have you not edited the file to remove the 3 lines at the end ?


Edit - just counted down - remove the 

wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg)

line as well, save close and rerun the apt-get update command

Just so you know in future - all lines in sources files should start with deb or deb-src

---

### Post by oldos2er on 2008-04-30
If you don't edit /etc/apt/sources.list as root, your changes will not be saved. In a terminal, type "gksudo gedit /etc/apt/sources.list" then remove these lines:

wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg)
sudo apt-key add -
sudo apt-key add -
sudo apt-get update

 Save and exit the file. Then in a terminal, type "sudo aptitude update"

---

### Post by zithe on 2008-04-30
I did delete it and the problem persists.

Updated list:

# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main (<--line 59)
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main

I try to get the update and I get "E: Malformed line 59 in source list /etc/apt/sources.list (URI parse)"

---

### Post by forestpixie on 2008-04-30
Take the " from the end of the last line

---

### Post by zithe on 2008-04-30
> **forestpixie said:**
> Take the " from the end of the last line

Sorry, that was to quote the list. >.>

---

### Post by forestpixie on 2008-04-30
I think there is something wrong with the dfreer stuff - edit the file delete all three lines and save it.

Then in terminal run these 1 at a time

```
echo "deb http://packages.dfreer.org:8080 gutsy main" | sudo tee -a /etc/apt/sources.list 
wget http://packages.dfreer.org:8080/7572013D.gpg -O- | sudo apt-key add - 
sudo apt-get update
```

When you want to quote something put >  at the beginning and  at the end or use the tool in the toolbar, same with code

---

### Post by forestpixie on 2008-04-30
The buttons in question are these

---

### Post by zithe on 2008-04-30
than you all so much! it worked! Now I can install java.

:D

---

