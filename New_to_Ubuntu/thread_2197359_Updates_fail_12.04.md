---
title: "Updates fail 12.04"
date: 2014-01-03
forum: New to Ubuntu
---

### Post by chemgrl08 on 2014-01-03
Hi all. I have been searching the forums for several months off and on trying to find a solution to this problem.
When I run my updater, it always fails. (Needless to say, the number of updates I neeed continues to increase!) I have tried changing the repository from US to Main. I feel like there's some kind of file missing. I also can't install new programs, such as skype. I have attached screenshots of the errors I'm getting.[ATTACH=CONFIG]249154[/ATTACH][ATTACH=CONFIG]249155[/ATTACH]
Please give very basic instructions for the fix; I can use the terminal, but when I get vague instructions like, "yeah just change the repository," I don't know how to do that one my own yet.
Thanks for any help you can offer; surely others have had this problem.

---

### Post by Bucky Ball on 2014-01-03
Is there anything more to that second screen shot? At the end it says 'Error in Function:' but then nothing. Is there anything after that?

Open a terminal and:

```
sudo apt-get autoremove
```

Agree if it offers to autoremove anything. Then try:

```
sudo apt-get update
```

Errors? Report them here, then:

```
sudo apt-get -f install
```

Again, report any errors. If none, then these two one after another with return in between:
```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by bapoumba on 2014-01-03
Please open a terminal and post the output to :
```
sudo apt-get update
cat /etc/apt/sources.list
```

The first command will ask for your user password. Type it, there will be no feedback in the terminal, that is normal.

Edit : ninja'd by BB ;)

---

### Post by chemgrl08 on 2014-01-04
Bucky Ball: No, there is no additional information after that screen- that is scrolled all the way to the bottom of that message box.
After typing your commands, the output did indeed show an error.
Do you want to continue [Y/n]? Y
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-headers-3.8.0-33': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
melissa@ObsidianOrder:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

I'm not clear on how to report an error; could you refer me to the proper page? I'm just not sure what to report; for example, it says "unrecoverable fatal error"... what would I do to report that?


bapoumba: here is the output from the commands you asked me to input...  Um, I don't know what it means. ^_^'

melissa@ObsidianOrder:~$ sudo apt-get update
[sudo] password for melissa: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg [198 B]
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release [49.6 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources [430 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources [7,039 B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources [101 kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources [8,468 B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [747 kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [11.5 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [230 kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.4 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources [94.7 kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources [2,494 B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources [29.9 kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources [1,792 B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages [375 kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages [91.1 kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages [2,642 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en
Fetched 2,250 kB in 16s (136 kB/s)                  
Reading package lists... Done
melissa@ObsidianOrder:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

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


Thank you for your help.It's like it's missing some final file to install things...

---

### Post by Bucky Ball on 2014-01-04
Run:
```

sudo dpkg --configure -a
sudo apt-get update
```

PS: Don't worry about reporting the error. You mean reporting a bug and that's not what this is I wouldn't think. ;)

---

### Post by chemgrl08 on 2014-01-09
I ran the code and it didn't seem to show any problems. However, when I try to run update manager, I still have over a hundred updates showing that need to be updated (they keep accumulating.) I am also still unable to install programs (such as Skype.) Other ideas?

---

### Post by sandyd on 2014-01-09
try
```

cd /var/lib/dpkg
sudo cp status status.bak
sudo nano status

```
Press control +w, type in ```
Package: linux-headers-3.8.0-33
```
remove all the lines from that line onwards (including that line) up until the next entry that starts with "Package"

then
```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Old_Grey_Wolf on 2014-01-09
Run the command ```
sudo apt-get update && sudo apt-get dist-upgrade
``` and post the output if there are errors.

---

### Post by chemgrl08 on 2014-01-11
sandyd:
after many updates, I got this
..."(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-headers-3.8.0-33': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2) "

---

### Post by chemgrl08 on 2014-01-11
Wolf:
I got
" Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-headers-3.8.0-33': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2) "

Hmm... deja vu.

---

### Post by deadflowr on 2014-01-11
Try running the
```
sudo apt-get -f install
```
command again.
If it buggers like before, redo the dpkg --configure -a command.

---

