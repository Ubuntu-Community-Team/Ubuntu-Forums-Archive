---
title: "can't install google earth in 12.10"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by cabz on 2013-01-02
well i have tried but failed to install eithe rthe older 6.02? or the newer beta 7.0 google earth on my laptop. i have tried both 32 & 64 bit versions (I am running a 64 bit 12.10) and it will not work. I have tried the downloaded package and I have tried to install through a terminal window  , no go if i try in synaptic it tells me it cannot install because of a broken or missing dependany ia32-libs. which is a 32bit file that I cannot install . any ideas? because i am out :(

---

### Post by oldos2er on 2013-01-02
Try ```
sudo apt-get update && sudo apt-get install ia32-libs-multiarch
``` then retry installing Google Earth.

---

### Post by cabz on 2013-01-02
> **oldos2er said:**
> Try ```
sudo apt-get update && sudo apt-get install ia32-libs-multiarch
``` then retry installing Google Earth.
I just tried that and got this at    
"Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs-multiarch is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ia32-libs-multiarch' has no installation candidate
cabz@ubuntu:~$ 

the end

---

### Post by fdrake on 2013-01-02
> **cabz said:**
> I just tried that and got this at    
"Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs-multiarch is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ia32-libs-multiarch' has no installation candidate
cabz@ubuntu:~$ 

the end
check that all your repo are marked
```

sudo synaptic

```close;
then run again the prev command

---

### Post by cabz on 2013-01-02
> **fdrake said:**
> check that all your repo are marked
```

sudo synaptic

```close;
then run again the prev command
I cannot find anything not checked  what am i looking for?

---

### Post by oldos2er on 2013-01-03
> **cabz said:**
> Package ia32-libs-multiarch is not available, but is referred to by another package.

Check your software sources and make sure the universe repository is enabled.

---

### Post by cabz on 2013-01-03
> **oldos2er said:**
> Check your software sources and make sure the universe repository is enabled.
you mean these?

[ATTACH]229524[/ATTACH]

---

### Post by oldos2er on 2013-01-03
Yes. Can you run ```
sudo apt-get install -f
``` and post the output?

---

### Post by cabz on 2013-01-03
> **oldos2er said:**
> Yes. Can you run ```
sudo apt-get install -f
``` and post the output?


here it is

cabz@ubuntu:~$ sudo apt-get install -f
[sudo] password for cabz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cabz@ubuntu:~$

---

### Post by oldos2er on 2013-01-03
I don't really understand why it's not picking up ia32-libs-multiarch. Try ```
sudo apt-get clean

sudo apt-get update

sudo apt-get install google-earth-stable
``` That last command assumes you have Google's repository enabled. Also, could you post ```
cat /etc/apt/sources.list
``` ?

---

### Post by cabz on 2013-01-03
> **oldos2er said:**
> I don't really understand why it's not picking up ia32-libs-multiarch. Try ```
sudo apt-get clean

sudo apt-get update

sudo apt-get install google-earth-stable
``` That last command assumes you have Google's repository enabled. Also, could you post ```
cat /etc/apt/sources.list
``` ?
Me neither I am totaly stumped
here is the results

cabz@ubuntu:~$ sudo apt-get install google-earth-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 google-earth-stable : Depends: ia32-libs but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
cabz@ubuntu:~$ 


cabz@ubuntu:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse
cabz@ubuntu:~$ 

and is software sources i have an entry for [http://dl.google.com/linux/earth/deb/stable](http://dl.google.com/linux/earth/deb/stable) main

---

### Post by fdrake on 2013-01-03
you can just doewnload it from here : [http://packages.ubuntu.com/precise/ia32-libs-multiarch](http://packages.ubuntu.com/precise/ia32-libs-multiarch)

and install it with "sudo dpkg -i ia32-libs-multiarch_20090808ubuntu35_i386.deb"



edit: the dependencies is a 32-multiarch package , which won't be see  by the package manager for installation since you are running a 64 sys. You have to install it manually. After the install try to reinstall google-earth again.

edit #2: 
[https://wiki.ubuntu.com/MultiarchSpec](https://wiki.ubuntu.com/MultiarchSpec)
[https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch)

---

### Post by cabz on 2013-01-03
> **fdrake said:**
> you can just doewnload it from here : [http://packages.ubuntu.com/precise/ia32-libs-multiarch](http://packages.ubuntu.com/precise/ia32-libs-multiarch)

and install it with "sudo dpkg -i ia32-libs-multiarch_20090808ubuntu35_i386.deb"



edit: the dependencies is a 32-multiarch package , which won't be see  by the package manager for installation since you are running a 64 sys. You have to install it manually. After the install try to reinstall google-earth again.

edit #2: 
[https://wiki.ubuntu.com/MultiarchSpec](https://wiki.ubuntu.com/MultiarchSpec)
[https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch) I tried these and got nothing but these messages

cabz@ubuntu:~$ sudo dpkg -i ia32-libs-multiarch_20090808ubuntu35_i386.deb
[sudo] password for cabz: 
dpkg: error processing ia32-libs-multiarch_20090808ubuntu35_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ia32-libs-multiarch_20090808ubuntu35_i386.deb
cabz@ubuntu:~$ 
[ATTACH]229532[/ATTACH]

---

### Post by fdrake on 2013-01-03
> **cabz said:**
> I tried these and got nothing but these messages

cabz@ubuntu:~$ sudo dpkg -i ia32-libs-multiarch_20090808ubuntu35_i386.deb
[sudo] password for cabz: 
dpkg: error processing ia32-libs-multiarch_20090808ubuntu35_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ia32-libs-multiarch_20090808ubuntu35_i386.deb
cabz@ubuntu:~$ 
[ATTACH]229532[/ATTACH]
try this:
```

 sudo dpkg -i ~/Downloads/ia32-libs-multiarch_20090808ubuntu35_i386.deb

```


edit: beside being a multiarch, the package itself presents a  bug [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/971761](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/971761)

---

### Post by cabz on 2013-01-03
> **fdrake said:**
> try this:
```

 sudo dpkg -i ~/Downloads/ia32-libs-multiarch_20090808ubuntu35_i386.deb

```edit: beside being a multiarch, the package itself presents a  bug [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/971761](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/971761)
I tried the code and got nothing but
cabz@ubuntu:~$ sudo dpkg -i ~/Downloads/ia32-libs-multiarch_20090808ubuntu35_i386.deb
[sudo] password for cabz: 
dpkg: error processing /home/cabz/Downloads/ia32-libs-multiarch_20090808ubuntu35_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 /home/cabz/Downloads/ia32-libs-multiarch_20090808ubuntu35_i386.deb

then I found a site that loisted the amd64 file and got this
[ATTACH]229537[/ATTACH] it seems the amd64 version is a bit elusive

---

### Post by fdrake on 2013-01-03
> **cabz said:**
> I tried the code and got nothing but
cabz@ubuntu:~$ sudo dpkg -i ~/Downloads/ia32-libs-multiarch_20090808ubuntu35_i386.deb
[sudo] password for cabz: 
dpkg: error processing /home/cabz/Downloads/ia32-libs-multiarch_20090808ubuntu35_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 /home/cabz/Downloads/ia32-libs-multiarch_20090808ubuntu35_i386.deb

then I found a site that loisted the amd64 file and got this
[ATTACH]229537[/ATTACH] it seems the amd64 version is a bit elusive

I am running ubuntu 12.04 - 64 bit and I am able to install ia32-libs-multiarch right the way from the repositories. Maybe it's due to the ubuntu version you are using. The only think I can tell you is to try the 12.04 and always stick with the long term releases; it's the fastest way to get bug support.

---

### Post by cabz on 2013-01-03
> **fdrake said:**
> I am running ubuntu 12.04 - 64 bit and I am able to install ia32-libs-multiarch right the way from the repositories. Maybe it's due to the ubuntu version you are using. The only think I can tell you is to try the 12.04 and always stick with the long term releases; it's the fastest way to get bug support. and heres the kicker and probably the issue? the PC i am trying to install it on is a laptop dual booted w win 7 and a fresh wubi install or 12.10
I have an old busted laptop in the garage that was a fresh install of 12.04 and upgraded to 12.10 and i just installed and ran google earth flawlessly.

---

### Post by fdrake on 2013-01-03
> **cabz said:**
> and heres the kicker and probably the issue? the PC i am trying to install it on is a laptop dual booted w win 7 and a fresh wubi install or 12.10
I have an old busted laptop in the garage that was a fresh install of 12.04 and upgraded to 12.10 and i just installed and ran google earth flawlessly.

No comment! :D

---

### Post by cabz on 2013-01-03
> **fdrake said:**
> No comment! :D
:D well that being said , can i copy the la32-libs files from one pc to another? and how will the destination pc find the files ? is there a log to update ?

---

### Post by fdrake on 2013-01-03
> **cabz said:**
> :D well that being said , can i copy the la32-libs files from one pc to another? and how will the destination pc find the files ? is there a log to update ?

well probably a developer here can guide you to a better solution , but you can always give it a try:

command to update library "ldconfig" ("L" not "i")

shared libraries:  /usr/lib/

good luck.

edit: Why dont't you search for the files with the name  "la32-libs" and copy them into their repective folders into the othe pc

```
sudo find / -name la32 | less
```
just a hint

---

### Post by oldos2er on 2013-01-04
> **cabz said:**
> cabz@ubuntu:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse
cabz@ubuntu:~$ 


Your sources.list is quite short. Here's mine: 

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal universe
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
deb http://security.ubuntu.com/ubuntu quantal-security universe
deb-src http://security.ubuntu.com/ubuntu quantal-security universe
deb http://security.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main
```

Make a backup copy of your sources: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
``` Copy and paste the text above as a file in your home folder, call it new.sources.list, then copy it over your old one ```
sudo cp new.sources.list /etc/apt/sources.list

sudo apt-get update

sudo apt-get install google-earth-stable
``` Let me know if this works.

---

### Post by cabz on 2013-01-04
> **oldos2er said:**
> Your sources.list is quite short. Here's mine: 

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal universe
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
deb http://security.ubuntu.com/ubuntu quantal-security universe
deb-src http://security.ubuntu.com/ubuntu quantal-security universe
deb http://security.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main
```Make a backup copy of your sources: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
``` Copy and paste the text above as a file in your home folder, call it new.sources.list, then copy it over your old one ```
sudo cp new.sources.list /etc/apt/sources.list

sudo apt-get update

sudo apt-get install google-earth-stable
``` Let me know if this works.cabz@ubuntu:~$ sudo apt-get install google-earth-stable
[sudo] password for cabz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 google-earth-stable : Depends: ia32-libs but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
cabz@ubuntu:~$

---

### Post by cabz on 2013-01-04
I have also noticed that i cannot install wine or skype ,I get the same broken package / unmet dependancy errors.

---

### Post by oldos2er on 2013-01-04
I'm running out of ideas. Open Synaptic and try Fix Broken Packages under the Edit menu, if you haven't already done that.

---

### Post by cabz on 2013-01-04
> **oldos2er said:**
> I'm running out of ideas. Open Synaptic and try Fix Broken Packages under the Edit menu, if you haven't already done that.
yup did that too. affter all this though I am still wondering why there is not a la32-libs-multiarch amd64 package? everytime i try and get it I get the " not availible in your sources list and it is unattainable through any of the multiarch pages . it's like it was just pulled off the internet. and for some reason the 12.04 files will  not work in 12.10.  there has to be a fix somewhere  but i cant find it!.

---

### Post by cabz on 2013-01-04
well after reading just about everything i can on this I am begining to think it'is a lost cause. 
I have dug around in synaptic and found this.
[ATTACH]229590[/ATTACH]
there seems to be no way to fix the package and it is the latest one . Also i found this in the changelogs.

[ATTACH]229591[/ATTACH] by reading the change log it appears that the la32-libs-multiarch files are removed on pupose?.

---

### Post by s1baker on 2013-01-05
Did you go directly to the Google website to download the install from them, or from the Ubuntu repositories?
 I had problems when I first went to install GE from the repos. Then went and downloaded GE directly from Google and went ok.

---

### Post by cabz on 2013-01-05
> **s1baker said:**
> Did you go directly to the Google website to download the install from them, or from the Ubuntu repositories?
 I had problems when I first went to install GE from the repos. Then went and downloaded GE directly from Google and went ok.
i have tried both ways

---

### Post by fdrake on 2013-01-05
what about this post.
[http://ubuntuforums.org/showthread.php?t=1966013](http://ubuntuforums.org/showthread.php?t=1966013)
 [http://ubuntuforums.org/showpost.php?p=12246372&postcount=7](http://ubuntuforums.org/showpost.php?p=12246372&postcount=7)

it looks like the same package is source of different problem for google earth and wine installations.

---

### Post by cabz on 2013-01-05
> **fdrake said:**
> what about this post.
[http://ubuntuforums.org/showthread.php?t=1966013](http://ubuntuforums.org/showthread.php?t=1966013)
 [http://ubuntuforums.org/showpost.php?p=12246372&postcount=7](http://ubuntuforums.org/showpost.php?p=12246372&postcount=7)

it looks like the same package is source of different problem for google earth and wine installations.

i found this refrence, i do not have the" multiarch with foreign architecturei386" file how do i create it? can someone send me a copy of it?
                                                        Quote:
                                                                      Originally Posted by **Sworddragon**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11879749#post11879749")                 
                 *Yes, on 64 bit systems you have to  enable multiarch to get the needed packages. Check if  /etc/dpkg/dpkg.cfg.d/multiarch with the content "foreign-architecture  i386" exists. If not create it and try again (you have to run "apt-get  update" again).*

---

### Post by cabz on 2013-01-05
fdrake , the second link you posted was one I had looked at before, unfortunatly i didnt upgrade from 12.-04 . i did a fresh install of 12.10 alone.

---

### Post by oldos2er on 2013-01-05
> **cabz said:**
> i found this refrence, i do not have the" multiarch with foreign architecturei386" file how do i create it? can someone send me a copy of it?
                                                        Quote:
                                                                      Originally Posted by **Sworddragon**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11879749#post11879749")                 
                 *Yes, on 64 bit systems you have to  enable multiarch to get the needed packages. Check if  /etc/dpkg/dpkg.cfg.d/multiarch with the content "foreign-architecture  i386" exists. If not create it and try again (you have to run "apt-get  update" again).*

```
sudo nano /etc/dpkg/dpkg.cfg.d/multiarch
``` Copy & paste in the text **foreign-architecture  i386** 
Ctrl-x, "y" to save changes.

---

### Post by cabz on 2013-01-05
HOOOTIE WHOOO , I got it. I found this launchpad page

[https://launchpad.net/ubuntu/+source/ia32-libs/20090808ubuntu36/+build/3497127](https://launchpad.net/ubuntu/+source/ia32-libs/20090808ubuntu36/+build/3497127)

and got the file installed after the above help on the "[I]etc/dpkg/dpkg.cfg.d/multiarch with the content "foreign-architecture   i386" exists. If not create it and try again (you have to run "apt-get   update" again)." after that and the lb32 install  google earth is now working .
Thanks to everyone who helped me! 

On a side note , during the install i got a message that the "foreign-archetecture.i386" is going to cause a hard error later and that i should remove it . if i do that will google earth still work?.

and again thanks .:cool:
[/I]

---

### Post by cabz on 2013-01-08
> **cabz said:**
> HOOOTIE WHOOO , I got it. I found this launchpad page

[https://launchpad.net/ubuntu/+source/ia32-libs/20090808ubuntu36/+build/3497127](https://launchpad.net/ubuntu/+source/ia32-libs/20090808ubuntu36/+build/3497127)

and got the file installed after the above help on the "[I]etc/dpkg/dpkg.cfg.d/multiarch with the content "foreign-architecture   i386" exists. If not create it and try again (you have to run "apt-get   update" again)." after that and the lb32 install  google earth is now working .
Thanks to everyone who helped me! 

On a side note , during the install i got a message that the "foreign-archetecture.i386" is going to cause a hard error later and that i should remove it . if i do that will google earth still work?.

and again thanks .:cool:
[/I] just an update, i renamed the "foregin archetecture.i386" to " add-archetecture.i386" as instructed in the terminal window. google erath still worked .
BUT upon doing a software update the system tried to undo all of the changes i made, it wanted to uninstall ia32-libs files and google earth. in the end I switched back to the "foreign arch" wording and I am gonna leave it at that. so all iin all it looks like this might just be a temporary fix until 13.04 is released..

---

### Post by oldos2er on 2013-01-08
cabz, glad you got this working. Could you please mark the thread as 'Solved' under the Thread Tools menu? It will help others who might be having the same problem.

---

### Post by cabz on 2013-01-08
> **oldos2er said:**
> cabz, glad you got this working. Could you please mark the thread as 'Solved' under the Thread Tools menu? It will help others who might be having the same problem.
 wiil do

---

### Post by wwwilkison on 2013-02-25
> **oldos2er said:**
> Try ```
sudo apt-get update && sudo apt-get install ia32-libs-multiarch
``` then retry installing Google Earth.

well, this is just great - but WHERE do you type in this code - please walk me through step by step from the Ubuntu desktop since I am a "know nothing" when it comes to geek speak.

thanks ..........

---

### Post by wwwilkison on 2013-02-25
> **cabz said:**
> fdrake , the second link you posted was one I had looked at before, unfortunatly i didnt upgrade from 12.-04 . i did a fresh install of 12.10 alone.

I just installed the latest version of 12 - then downloaded Google Earth packager installer - ran the package installer - went OK - but, now, where do I find an icon or other indicator to Launch Google Earth?  It appears to have installed Google Earth Stable, but there is no indication of any kind on how to launch the software.

---

### Post by cabz on 2013-02-25
> **wwwilkison said:**
> well, this is just great - but WHERE do you type in this code - please walk me through step by step from the Ubuntu desktop since I am a "know nothing" when it comes to geek speak.

thanks .......... open a terminal window, then copy and paste the command from this post into the window and hit enter

sudo apt-get update && sudo apt-get install ia32-libs-multiarch

---

### Post by cabz on 2013-02-25
> **wwwilkison said:**
> I just installed the latest version of 12 - then downloaded Google Earth packager installer - ran the package installer - went OK - but, now, where do I find an icon or other indicator to Launch Google Earth?  It appears to have installed Google Earth Stable, but there is no indication of any kind on how to launch the software.
go to the dash and type in google earth it should show up, once it is launched right click the icon and choose " lock to taskbar " to keep it handy.

---

