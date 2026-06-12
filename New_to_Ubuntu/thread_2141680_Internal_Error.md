---
title: "Internal Error"
date: 2013-05-03
forum: New to Ubuntu
---

### Post by mrkey on 2013-05-03
Hi guys.. i am totally a noob with this ubuntu thingy.. when I tried to install adobe with this site as reference [http://www.etdot.com/2012/06/21/install-adobe-reader-in-ubuntu-12-04-lts/](http://www.etdot.com/2012/06/21/install-adobe-reader-in-ubuntu-12-04-lts/)  , the system started to act weird and is always giving me this error message "Sorry, Ubuntu 12.04 has experienced and internal error" "invalid problem report" "could not determine the package or source package name".. I can no longer open ubuntu software center..

---

### Post by ibjsb4 on 2013-05-03
Acroread is in the software center.  Why did you decide to use this site instead?

---

### Post by mrkey on 2013-05-03
i did tried to search acroread in the software center but it wasn't there so i look for another way of installing it.. and that website and the other one pointed on installation via the terminal with that commands.. first time to use ubuntu and bam!.. error..

---

### Post by ibjsb4 on 2013-05-03
All you needed to do in terminal is:

```
sudo apt-get install acroread
```

No big deal, just have to fix it.  Please post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by mrkey on 2013-05-03
with cat /etc/apt/sources.list command, it give me this information:

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/


# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

---

### Post by ibjsb4 on 2013-05-03
Ok, that looks good.  Please post the output of:

```
ls /etc/apt/sources.list.d
```

And if you use "code tags" it will stop your thread from becoming a mile long :)

[ATTACH=CONFIG]242135[/ATTACH]

```
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/


# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner 						
```

---

### Post by mrkey on 2013-05-03
with:
```
[COLOR=#000000][FONT=Ubuntu Mono]ls /etc/apt/sources.list.d[/FONT][/COLOR]
```

output:
```
google-chrome.list  google-chrome.list.save
```

---

### Post by ibjsb4 on 2013-05-03
Well thats ok too.  Im fishing for the problem and not finding it, so bare with me :)  In terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

Any errors?

---

### Post by mrkey on 2013-05-03
thank you for your help.. I really don't know how to get around with ubuntu.. it returns an error which is

```

E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)E: The list of sources could not be read.

```

---

### Post by ibjsb4 on 2013-05-03
Bingo :) I missed it the first time ..

The last two lines in your sources.list need to be commented (## or just one #) out.

deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner 
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

Make them read


#deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner 
#deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

And then a few lines above that you need to uncomment:

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner 
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

to read

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner 
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

To edit your sources.list, go to terminal and enter:

```
gksudo gedit /etc/apt/sources.list
```

Update after you make the changes.

Also be sure about what you edit, gksudo command gives you unlimited powers and will not ask you if you are sure :)

Post back if you have questions.

---

### Post by mrkey on 2013-05-03
i already change it and did try to update.. but there is still an error.. it reads "an error occurred, please run Package Manager from the right-click menu or apt-get in ta terminal to see what is wrong. The error message was: 'Error: Opening the cache (E:Malformed line 60 in source list /etc/apt/sources.list(dist parse), E:The package list or status file could not be parsed or opened.)'. This is usually means that your installed packages have unmet dependencies"


But what I did is erase all the information in the source.list thingy.. and now the error is gone.. what the heck is that? did I worsen the problem instead of solving it?

---

### Post by ibjsb4 on 2013-05-03
In terminal (one line at a time):
```

sudo rm -r /var/lib/apt/lists/* 
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by monkeybrain2012 on 2013-05-03
Your error message said that there is an error in line 60 in /etc/apt/sources.list

so open the list with 

```
 gksudo gedit /etc/apt/sources/list and see what it is in line 60  (in Edit > Preference > View check the box display line numnber)


```

Then post it back. 


To get acroread you need to enable the Canonical's Partner's repository. Open the Software Centre, go to Edit > Software Sources, open the tab "Other Software" and check the first box that says "Canonical Partners" then close Software Sources. Here are some screenshots [http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them](http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them)

Alternatively, open the sources.list with gedit as before 

```
gksudo gedit /etc/apt/sources.list

```

locate these lines (from your post 4)

```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

```

And uncomment (i.e. remove the # in front) the line "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner"
close the sources list

and then 
```
sudo apt-get update
```

You can then install acroread with either 

```
sudo apt-get install acroread
```

from the terminal

or install it in the Software Centre

**Aside** Though to be honest I don't know why you would want to install it. It is a bloated piece of junk. Ubuntu's default pdf reader is much more snappier.

---

### Post by mrkey on 2013-05-03
thank you very much i now did those command and all seems working fine now.. ^_^

---

### Post by mrkey on 2013-05-03
I also would not pursue installing it.. the default reader would be okay.. thanks for the help..

---

### Post by monkeybrain2012 on 2013-05-03
BTW, after you fix your problem install synaptic and use it to install and update software instead of using the Software Centre

```
sudo apt-get install synaptic
```

It is a lot more powerful and versatile, much faster too.

---

### Post by ibjsb4 on 2013-05-03
Yep, Synaptic is a very powerful tool and worth learning.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

Don't forget

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums :)

---

