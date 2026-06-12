---
title: "Cannot access Synaptic or Ubuntu Software"
date: 2014-12-15
forum: New to Ubuntu
---

### Post by kindafunnylookin on 2014-12-15
So far I have found out that part of my problem is:

```
E: Malformed line 57 in sources.list (dist parse)
E: The list of sources could not be read.
```

Now I am stumped, how do I fix this? When I try ```
sudo apt-get update
``` or upgrade i get stuck because the list cannot be read.

---

### Post by slickymaster on 2014-12-15
Can you please post back the output, using code tags for the effect, of:```
cat /etc/apt/sources.list
```

---

### Post by kindafunnylookin on 2014-12-15
This is a new install on a new computer and I just found out that I am unable to cut and paste to and from terminal. I can cut and paste to the word processer but not the terminal, can you help with that?

---

### Post by slickymaster on 2014-12-15
> **kindafunnylookin said:**
> This is a new install on a new computer and I just found out that I am unable to cut and paste to and from terminal. I can cut and paste to the word processer but not the terminal, can you help with that?
You can redirect the output of the cat command into a .txt file by using the ">" character. The results will be written in the said .txt and no results will appear on the display.
So, in the terminal run```
cat /etc/apt/sources.list > list.txt
```You'll see the list.txt file in your home directory, just attach it to the thread.

---

### Post by kindafunnylookin on 2014-12-15
WOW. That's a great thing to know. Here's what I got:


```
# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://ubuntu.p2-next.org/trusty](http://ubuntu.p2-next.org/trusty) main
# deb-src [http://ubuntu.p2-next.org/trusty](http://ubuntu.p2-next.org/trusty) main
```

---

### Post by slickymaster on 2014-12-15
> **kindafunnylookin said:**
> WOW. That's a great thing to know. Here's what I got:


# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
[B][SIZE=3][COLOR=#ff0000]deb [/COLOR][[COLOR=#ff0000]http://ubuntu.p2-next.org/trusty[/COLOR]]("http://ubuntu.p2-next.org/trusty")[COLOR=#ff0000] main
# deb-src [/COLOR][[COLOR=#ff0000]http://ubuntu.p2-next.org/trusty[/COLOR]]("http://ubuntu.p2-next.org/trusty")[COLOR=#ff0000] main[/COLOR][/SIZE][/B]

Those lines I've mark in red/bold (the last two of your sources list) are the culprits. You just have to comment them, by adding '##' at the beginning of each line.

Again in your terminal, run the following:```
sudo nano /etc/apt/sources.list
```you'll be asked for your password
After entering your password you'll be presented with your sources list file in nano text editor with right permissions, so be careful doing the following steps.
Navigate to the end of the file, either by using the cursor keys or PageDown, and add **##** to the beginning of the two last lines so they'll read like this:```
## deb http://ubuntu.p2-next.org/trusty main
## deb-src http://ubuntu.p2-next.org/trusty main
```Once that done press Ctrl+X and you'll be asked to "Save modified buffer ....?", press Y and you'll get another question: "File Name to Write: /etc/apt/sources.lisy", just hit the enter key. After that you'll be again at your normal prompt where you must run```
sudo apt-get update
sudo apt-get upgrade
```
If you get some more errors, please post them back in the thread.

---

### Post by kindafunnylookin on 2014-12-15
All is well. Thank you for your help.

---

### Post by JKyleOKC on 2014-12-15
Quick note slightly off topic. To paste into a terminal window, use shift-control-V rather than just control-V. The shift key has to be added since the terminal command processor already has other actions for control-C and control-V.

---

