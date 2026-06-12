---
title: "Many bugs after trying to install Skype."
date: 2013-10-18
forum: New to Ubuntu
---

### Post by Edgar_Sarmento_Bezerra on 2013-10-18
Hi, people!
I was trying to install Skype today and searching for a tutorial I founded one. There was three command lines to execute on terminal.
First: sudo add-apt-repository "deb http://archive.canonical.com/$(lsb_release -sc) partner";
Second: sudo apt-get update;
Third: sudo apt-get install Skype;

Typing this that's what happened.
[I]"edgar@edgar-RV411-RV511-E3511-S3511-RV711-E3411:~$ sudo add-apt-repository "deb http://archive.canonical.com/$(lsb_release -sc) partner"
[sudo] password for edgar: 
edgar@edgar-RV411-RV511-E3511-S3511-RV711-E3411:~$ sudo apt-get updateE: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
edgar@edgar-RV411-RV511-E3511-S3511-RV711-E3411:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
E: Unable to locate package skype
edgar@edgar-RV411-RV511-E3511-S3511-RV711-E3411:~$ "[/I]

Now, neither Ubuntu Software Center nor Ubuntu Tweak works anymore. The former just doesn't open and the latter the function of apps doesn't work also.
Hope somebody help me.

---

### Post by sandyd on 2013-10-19
> **Edgar_Sarmento_Bezerra said:**
> Hi, people!
I was trying to install Skype today and searching for a tutorial I founded one. There was three command lines to execute on terminal.
First: sudo add-apt-repository "deb http://archive.canonical.com/$(lsb_release -sc) partner";
Second: sudo apt-get update;
Third: sudo apt-get install Skype;

Typing this that's what happened.
[I]"edgar@edgar-RV411-RV511-E3511-S3511-RV711-E3411:~$ sudo add-apt-repository "deb http://archive.canonical.com/$(lsb_release -sc) partner"
[sudo] password for edgar: 
edgar@edgar-RV411-RV511-E3511-S3511-RV711-E3411:~$ sudo apt-get updateE: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
edgar@edgar-RV411-RV511-E3511-S3511-RV711-E3411:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
E: Unable to locate package skype
edgar@edgar-RV411-RV511-E3511-S3511-RV711-E3411:~$ "[/I]

Now, neither Ubuntu Software Center nor Ubuntu Tweak works anymore. The former just doesn't open and the latter the function of apps doesn't work also.
Hope somebody help me.Can you post the output of
```

cat /etc/apt/sources.list

```
thanks

---

### Post by Edgar_Sarmento_Bezerra on 2013-10-19
edgar@edgar-RV411-RV511-E3511-S3511-RV711-E3411:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise universe
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

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
deb hrrp://archive.canonical.com/precise partner
deb-src hrrp://archive.canonical.com/precise partner
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
edgar@edgar-RV411-RV511-E3511-S3511-RV711-E3411:~$

---

### Post by Albert_Levin on 2013-10-19
**You should probably get Skype from the website if it doesn't work, [http://www.skype.com/en/](http://www.skype.com/en/)** and then a popup window may pop up saying to "Install it from the package".

---

### Post by Edgar_Sarmento_Bezerra on 2013-10-19
> **Albert_Levin said:**
> **You should probably get Skype from the website if it doesn't work, [http://www.skype.com/en/](http://www.skype.com/en/)** and then a popup window may pop up saying to "Install it from the package".

None window poped up.

---

### Post by deadflowr on 2013-10-19
You're going to need to do a couple things here.
The bottom of your sources/list is all messed up and for intents and purposes will need several of the end entries at the end removed.

Firstly, though, let's get the partner repos enabled.
In a terminal run this
```
gksu gedit /etc/apt/sources.list
```
Enter your password

A text editor window will open with the sources.list file.
go down to the entry

```
[COLOR=#000000]## Uncomment the following two lines to add software from Canonical's[/COLOR]
[COLOR=#000000]## 'partner' repository.[/COLOR]
[COLOR=#000000]## This software is not part of Ubuntu, but is offered by Canonical and the[/COLOR]
[COLOR=#000000]## respective vendors as a service to Ubuntu users.[/COLOR]
[COLOR=#000000]# deb [/COLOR][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)[COLOR=#000000] precise partner[/COLOR]
[COLOR=#000000]# deb-src [/COLOR][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)[COLOR=#000000] precise partner[/COLOR]
```
and remove the # symbol from the lines
```
[COLOR=#000000]# deb [/COLOR][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)[COLOR=#000000] precise partner[/COLOR]
[COLOR=#000000]# deb-src [/COLOR][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)[COLOR=#000000] precise partner[/COLOR]
```
to
```
[COLOR=#000000]deb [/COLOR][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)[COLOR=#000000] precise partner[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)[COLOR=#000000] precise partner[/COLOR]
```

Then while still in the gedit window go down to the last section you have and delete everything after

```
[COLOR=#000000]## This software is not part of Ubuntu, but is offered by third-party[/COLOR]
[COLOR=#000000]## developers who want to ship their latest software.[/COLOR]
[COLOR=#000000]deb [/COLOR][http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu)[COLOR=#000000] precise main[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu)[COLOR=#000000] precise main[/COLOR]
```

So remove these lines

```
[COLOR=#000000]deb hrrp://archive.canonical.com/precise partner[/COLOR]
[COLOR=#000000]deb-src hrrp://archive.canonical.com/precise partner[/COLOR]
[COLOR=#000000]deb [/COLOR][http://archive.canonical.com/precise](http://archive.canonical.com/precise)[COLOR=#000000] partner[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://archive.canonical.com/precise](http://archive.canonical.com/precise)[COLOR=#000000] partner[/COLOR]
```

The lines you added are wrong anyway.
When you finish this save and exit gedit.
Then while the terminal is still open, run
```
sudo apt-get update
```
If no errors appear, then try installing skype again.

If errors do appear, post them.

---

### Post by Edgar_Sarmento_Bezerra on 2013-10-20
Hey deadflowr! Thank you so much. Everything is working again and I've installed skype. My problem is solved. :D

---

### Post by Lars Noodén on 2013-10-20
Now that it is working for the time being you might also look into SIP-based options.  Ekiga, Jitsi, Linphone and Blink can all call each other and the sound quality is better than Skype usually.  The big advantage with them is that not only are they open source, the protocol they use is an open standard.  You can install any of them along side Skype without disturbing anything and as your SIP network grows, you can eventually drop Skype before it drops you.

---

