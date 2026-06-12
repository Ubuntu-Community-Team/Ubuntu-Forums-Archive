---
title: "Update Manager:  Failed to download repository information"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by squigles1 on 2011-09-14
```
W:Failed to fetch http://ppa.launchpad.net/tsbarnes/indicatio-keylock/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/tsbarnes/indicatio-keylock/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/ie.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```

Having trouble when running update manager, when checking for updates keep getting above error code. 
Keep getting message "The package information last update 122days ago"
Such a newbie I don't know what this means and cannot figure out a solution from other similar threads.

---

### Post by Rex Bouwense on 2011-09-14
Try running:
sudo apt-get update
sudo apt-get upgrade
from the terminal.  You will be asked for your password.  Just type it in and enter.

---

### Post by squigles1 on 2011-09-14
Thanks Rex,
On sudo apt-get update I had along sting of jobs done followed by:
```
W: Failed to fetch gzip:/var/lib/apt/lists/partial/ie.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch http://ppa.launchpad.net/tsbarnes/indicatio-keylock/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/tsbarnes/indicatio-keylock/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```
Sudo apt-get upgrade then resulted in:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Does this mean all is fine and I should ignore issues with update?

---

### Post by 2F4U on 2011-09-14
I would suggest you try a different mirror and see if the problem still exists.

---

### Post by raja.genupula on 2011-09-14
open update-manager--> settings-->other software
uncheck those error sources and then try to update again

---

### Post by Rex Bouwense on 2011-09-14
No.  There have been many updates issued in the last four months.  Check your software sources to make sure that the sources are checked.  You also might want to try a different server.  That option can be found under the first tab.

---

### Post by snowpine on 2011-09-14
Please re-read the error message carefully as it's actually giving you some useful information. 

There are actually two separate problems here:

1.

```
W:Failed to fetch http://ppa.launchpad.net/tsbarnes/indicatio-keylock/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/tsbarnes/indicatio-keylock/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
, 
```

This is **not** an official, default Ubuntu software source--this is an unofficial software source that **you** added for some reason. Therefore I refer you [to this page]("https://launchpad.net/~tsbarnes/+archive/indicator-keylock") in particular the "For questions and bugs with software in this PPA please contact..." link.

2.

```
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/ie.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources  Hash Sum mismatch

```

I have not experienced this problem, personally, but a quick forum Search shows me that other users have successfully solved it, for example: [http://ubuntuforums.org/showthread.php?t=1729381](http://ubuntuforums.org/showthread.php?t=1729381)

---

### Post by Rex Bouwense on 2011-09-14
I must admit that I didn't read the whole error report so I was Googling the wrong stuff.  Today was a good day.  I learned something.

---

### Post by squigles1 on 2011-09-14
> **2F4U said:**
> I would suggest you try a different mirror and see if the problem still exists.

I am sorry but what do you mean by a different mirror?

> **raja.genupula said:**
> open update-manager--> settings-->other software
uncheck those error sources and then try to update again

I have done this and received the below message when I tried to run update checker again:
```
W:Failed to fetch gzip:/var/lib/apt/lists/partial/ie.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

> **snowpine said:**
> Please re-read the error message carefully as it's actually giving you some useful information. 

There are actually two separate problems here:

1.

```
W:Failed to fetch http://ppa.launchpad.net/tsbarnes/indicatio-keylock/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/tsbarnes/indicatio-keylock/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
, 
```This is **not** an official, default Ubuntu software source--this is an unofficial software source that **you** added for some reason. Therefore I refer you [to this page]("https://launchpad.net/%7Etsbarnes/+archive/indicator-keylock") in particular the "For questions and bugs with software in this PPA please contact..." link.
I think this is the code for a Caps Lock display I downloaded through the software centre.

> **snowpine said:**
> 
2.

```
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/ie.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources  Hash Sum mismatch

```I have not experienced this problem, personally, but a quick forum Search shows me that other users have successfully solved it, for example: [http://ubuntuforums.org/showthread.php?t=1729381](http://ubuntuforums.org/showthread.php?t=1729381)

Will try these two suggestions!
Thank you every one for your help!
I feel like an I dont know where to start looking for solutions most of the time.  Learning curve I guess ;)

---

### Post by Rex Bouwense on 2011-09-14
The very best place to start when you have a problem/question is Google.  There is a lot of information out there.  You can also use the search feature on these forums and as you have already discovered you can post a thread.  I have been reading these forums just to "enlighten" myself for a while. There is a learning curve but 99.9% of the folks on these forums are super and will help if they can.  No one is paid and many (if not most) have a job that requires their efforts.  Volunteers one and all and we love Linux and wish to help.

---

### Post by snowpine on 2011-09-14
> **squigles1 said:**
> Thank you every one for your help!
I feel like an I dont know where to start looking for solutions most of the time.  Learning curve I guess ;)

No worries, Linux is a big learning curve, and it's good to ask lots of questions. :)

---

### Post by JD8182 on 2011-09-14
Open a Terminal and type: [QUOTE]sudo gedit /etc/apt/sources.list[/QUOTE, please post the outcome of your source file, sometimes the values get entered in wrong.





> **squigles1 said:**
> ```
W:Failed to fetch http://ppa.launchpad.net/tsbarnes/indicatio-keylock/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/tsbarnes/indicatio-keylock/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/ie.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```

Having trouble when running update manager, when checking for updates keep getting above error code. 
Keep getting message "The package information last update 122days ago"
Such a newbie I don't know what this means and cannot figure out a solution from other similar threads.

---

### Post by squigles1 on 2011-09-14
OK Thanks for all the kind help and support!

I followed Snowpines lead and checked out  [http://ubuntuforums.org/showthread.php?t=1729381](http://ubuntuforums.org/showthread.php?t=1729381)

Where the advice was to run sudo rm -rf /var/lib/apt/lists/partial/*I was a little cautious about this after reading in the help section that entering rm  -rf codes where a bad idea.
So I looked around for a few more threads before I was brave enough to try it.
Entered the code -> then asked for my password.  
Then done nothing else.

Exited out of Terminal,
Re-ran update problem appears resolved!

Snowpines & Rex I suggest you are fantastic teachers and motivators!

Just two more questions:

[LIST=1]
[*]Should I change the status of this thread to "Solved" I am waiting to here more from the designer about the other bug.
[*]Could you explain (or guide me to where I can find) what parts of the code mean?
[/LIST]

[LIST]
[*]I Guess SUDO means go do this
[*]is rm  -rf Remove then Reformat?
[*]does the rest of the code tell the computer (Kernal?) where to find the file?
[*]is lib something to to with the LibreOffice products?
[/LIST]
Thanks again!
A very re-leaved learner!

---

### Post by squigles1 on 2011-09-14
> **JD8182 said:**
> Open a Terminal and type: > sudo gedit /etc/apt/sources.list[/QUOTE, please post the outcome of your source file, sometimes the values get entered in wrong.

I just tried this and got:
```

(gedit:8121): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.V6781V': No such file or directory

(gedit:8121): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```A side window then opened with this information:```

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ie.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ie.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ie.archive.ubuntu.com/ubuntu/ natty universe
deb http://ie.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ie.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://ie.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ie.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://ie.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu natty main
# deb-src http://extras.ubuntu.com/ubuntu natty main
```Kind of scares me a little what does this actually mean?

---

### Post by Rex Bouwense on 2011-09-14
sudo = super user do
lib  = a shared library
rm   = remove
Enjoy.
Here are a couple of command line references for you to peruse:
[http://ss64.com/bash/](http://ss64.com/bash/)
[http://mally.stanford.edu/~sr/computing/basic-unix.html](http://mally.stanford.edu/~sr/computing/basic-unix.html)
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by snowpine on 2011-09-14
> **squigles1 said:**
> OK Thanks for all the kind help and support!

I followed Snowpines lead and checked out  [http://ubuntuforums.org/showthread.php?t=1729381](http://ubuntuforums.org/showthread.php?t=1729381)

Where the advice was to run sudo rm -rf /var/lib/apt/lists/partial/*I was a little cautious about this after reading in the help section that entering rm  -rf codes where a bad idea.
So I looked around for a few more threads before I was brave enough to try it.
Entered the code -> then asked for my password.  
Then done nothing else.

Exited out of Terminal,
Re-ran update problem appears resolved!

Snowpines & Rex I suggest you are fantastic teachers and motivators!

Just two more questions:

[LIST=1]
[*]Should I change the status of this thread to "Solved" I am waiting to here more from the designer about the other bug.
[*]Could you explain (or guide me to where I can find) what parts of the code mean?
[/LIST]

[LIST]
[*]I Guess SUDO means go do this
[*]is rm  -rf Remove then Reformat?
[*]does the rest of the code tell the computer (Kernal?) where to find the file?
[*]is lib something to to with the LibreOffice products?
[/LIST]
Thanks again!
A very re-leaved learner!

Yeah! So to recap the current status: You can update your list of available packages with:

```
sudo apt-get update
```

Any errors?

Now have you tried upgrading your system:

```
sudo apt-get upgrade
```

If you are still getting the error about "failed to fetch http://ppa.launchpad.net..." then let us know and I'll try to help.

ps It is always very good to understand what commands mean, don't blindly follow instructions, I salute your willingness and effort to learn!

You can find out more info Linux commands with "man" for "manual:"

```
man rm
```

The - symbol sets options or "flags" for example "sandwich -blt" hypothetically means "make me a sandwich with the bacon, lettuce, and tomato options." In the context of the "rm" command, "-r" means "recursive" (applies to all the specified files and sub-folders) and "-f" means "force" or "don't prompt y/n for each file." 

Now you can understand why people tell you to be cautious with "rm -rf" commands. If you specify the wrong folder, then you will lose everything in that folder and its subfolders. If you were to accidentally specify the root or / folder, then you would lose everything!

In your example the rm -rf command is limited to the folder /var/lib/apt/lists/partial/ (the * symbol is a wildcard meaning "all files in the specified folder"). 

/var is the "variable" folder where the system stores logs, temporary files, etc. and /var/lib/apt stores temporary data for apt and apt-get. I don't know the exact significance, but in layman's terms, you deleted a corrupt data file(s) which forced apt-get to rebuild its cache. 

So in the future you'll know how devastating a mistake here can be, in fact it's a good idea to copy & paste commands from the forum to the terminal, rather than run the risk of a typo.

You will also notice  the use of "sudo" at the beginning of the command, that makes the rest of the line execute as "super user." This is necessary to perform any system administration tasks or edit/delete files outside of your /home folder.

---

