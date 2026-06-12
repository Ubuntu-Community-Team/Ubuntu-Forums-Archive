---
title: "fix broken package"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by thomsebastin on 2012-03-09
i'm not able to install few applications from the apt-get,ubuntu software centre or the synaptic package manger.why is this happening so??any help ??
tried sudo apt-get install -f ,auto clean,clean,dis-upgrade,update everything but still somewhere something is wrong..pls help.:):)
here this pic shows an example..

[IMG]http://img267.imageshack.us/img267/5994/screenshotguake1.png[/IMG]

---

### Post by winh8r on 2012-03-09
Which release of Ubuntu are you using? (11.04,11.10 etc)

---

### Post by thomsebastin on 2012-03-09
> **winh8r said:**
> Which release of Ubuntu are you using? (11.04,11.10 etc)
11.04 natty narwhal ....thnx for the response bro...

---

### Post by winh8r on 2012-03-09
Go to Software Centre

click Edit > Software sources

make sure all repositories are enabled

universe

multiverse

restricted


run 

```
sudo updatedb
```

```
sudo apt-get update
```

then try to install again.

---

### Post by thomsebastin on 2012-03-09
> **winh8r said:**
> Go to Software Centre

click Edit > Software sources

make sure all repositories are enabled

universe

multiverse

restricted


run 

```
sudo updatedb
``````
sudo apt-get update
```then try to install again.
that is already enabled bro....anyway i tried with the other two commands with no positive results.....any other workout?#-o#-o#-o#-o

---

### Post by Scott Baker on 2012-03-09
Quick question. Have you tried to install other packages with synaptic / software center recently? If so, what were the results? Did you succeed, or were the results the same? I ask because I just recently tried for a VERY new version of vitualbox, from the manufacturers website and my old version REALLY croaked, plus the new did not install, but gave a VERY similar message. The results were a couple of hours of headaches. ](*,)

---

### Post by NikTh on 2012-03-09
Hello . 
I know that you can fix broken packages (if you have) from Synaptic. Open in and go to edit --> fix broken packages . 
Alternatively you can run on terminal 
```
sudo apt-get -f install
```

---

### Post by thomsebastin on 2012-03-09
> **Scott Baker said:**
> Quick question. [COLOR=Lime]Have you tried to install other packages with synaptic / software center recently? If so, what were the results? Did you succeed, or were the results the same?[/COLOR] I ask because[COLOR=Red] I just recently tried for a VERY new version of vitualbox, from the manufacturers website and my old version REALLY croaked, plus the new did not install, but gave a VERY similar message.[/COLOR] The results were a couple of hours of headaches. ](*,)
[COLOR=Lime]s scott i'm able to install other softwares.even now i tried to install an application n it was succeeded look this pic..[/COLOR]
[IMG]http://img208.imageshack.us/img208/6424/screenshotubuntusoftwar.jpg[/IMG]
[COLOR=Lime]so that is not the problem.[/COLOR]
[COLOR=Red]s i have had the same experience when i tried to install a newer version of audacious which even now i couldn't solve.(i'm using clementine now](*,)](*,)).i think the problem would be somewhat closely related to the conflicting of various packages.... i really miss pidgin..[/COLOR]:cry::-x

---

### Post by thomsebastin on 2012-03-09
> **NikTh said:**
> Hello . 
I know that you can fix broken packages (if you have) from Synaptic. Open in and go to edit --> fix broken packages . 
Alternatively you can run on terminal 
```
sudo apt-get -f install
```
no bro that wont solve it either 
[IMG]http://img577.imageshack.us/img577/3690/selection025.png[/IMG]

---

### Post by winh8r on 2012-03-09
try running 

```
sudo apt-get upgrade
```

that might clear up the dependency problems.

---

### Post by thomsebastin on 2012-03-09
> **winh8r said:**
> try running 

```
sudo apt-get upgrade
```that might clear up the dependency problems.
that won't help since i had already tried that ..but i wanna know y few packages are kept back.does that relate to this issue anyway?

[IMG]http://img804.imageshack.us/img804/9571/screenshotguake.jpg[/IMG]any solution so as to keep them upgrading??:p:p

---

### Post by winh8r on 2012-03-10
run

```
sudo apt-get dist-upgrade
```

and check whether it will upgrade them then.

---

### Post by thomsebastin on 2012-03-10
> **winh8r said:**
> run

```
sudo apt-get dist-upgrade
```and check whether it will upgrade them then.
that i had already done bro....that dint help either..:roll::roll:

---

### Post by winh8r on 2012-03-10
I think I forgot.....

```
sudo dpkg --configure -a
```

then

```

sudo apt-get -f install
```

then

```
sudo apt-get dist-upgrade
```

---

### Post by thomsebastin on 2012-03-10
still those packages r kept back....:P:P:confused:

---

### Post by raja.genupula on 2012-03-10
hi just say yes to upgrade then it will run upgrade process , if dependency issues raised then type 
```
sudo apt-get install -f
```

let us know what you got.

small suggestion: please copy the terminal code my friend , dont attach the images , just take the terminal text and place it between code tags.  Thank you . 


all the best .

---

### Post by thomsebastin on 2012-03-10
> **raja.genupula said:**
> hi just say yes to upgrade then it will run upgrade process , if dependency issues raised then type 
```
sudo apt-get install -f
```let us know what you got.

small suggestion: please copy the terminal code my friend , dont attach the images , just take the terminal text and place it between code tags.  Thank you . 


all the best .
k boss here is the result 
```
thomas@thomas:~$ sudo apt-get install -f
[sudo] password for thomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

```

---

### Post by raja.genupula on 2012-03-10
I think i havent understand properly , you are getting some dependencies issues right ?

go to the situation what giving you that dependencies problem and then do what i suggested above? 

If i not properly understand your issue please explain .
Thank you .

---

### Post by matt_symes on 2012-03-10
Hi

(I, like Raja, i still assuming dependency issues as i am a bit confused).

One of your missing dependencies is perlapi-5.12.4 listed in the screenshot on your first post. That version of perlapi is for Oneiric.

[http://packages.ubuntu.com/oneiric/perlapi-5.12.4](http://packages.ubuntu.com/oneiric/perlapi-5.12.4)

> 11.04 natty narwhal

You are on Natty 

[http://packages.ubuntu.com/natty/perlapi-5.10.1](http://packages.ubuntu.com/natty/perlapi-5.10.1)

Have you a problem with your sources ?

Please post the output of

```
cat /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Copy and paste the output from the terminal by highlighting it -> right click -> copy.

Paste it into your next post between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

Kind regards

---

### Post by NikTh on 2012-03-10
Hi , 
Please install Synaptic 
```
 sudo apt-get install synaptic
``` 
Then go to Synapric --> Mark all Upgrades --> Apply. 
Thanks

---

### Post by thomsebastin on 2012-03-10
> **matt_symes said:**
> Hi

(I, like Raja, i still assuming dependency issues as i am a bit confused).

One of your missing dependencies is perlapi-5.12.4 listed in the screenshot on your first post. That version of perlapi is for Oneiric.

[http://packages.ubuntu.com/oneiric/perlapi-5.12.4](http://packages.ubuntu.com/oneiric/perlapi-5.12.4)



You are on Natty 

[http://packages.ubuntu.com/natty/perlapi-5.10.1](http://packages.ubuntu.com/natty/perlapi-5.10.1)

Have you a problem with your sources ?

Please post the output of

```
cat /etc/apt/sources.list /etc/apt/sources.list.d/*
```Copy and paste the output from the terminal by highlighting it -> right click -> copy.

Paste it into your next post between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```Kind regards
```
thomas@thomas:~$ cat /etc/apt/sources.list /etc/apt/sources.list.d/*
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu natty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu natty multiverse
deb http://packages.dotdeb.org stable all
deb-src http://packages.dotdeb.org stable all

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu natty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu natty-security universe
deb http://archive.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://archive.getdeb.net/ubuntu oneiric-getdeb apps
deb-src http://archive.getdeb.net/ubuntu oneiric-getdeb apps
deb http://www.geekconnection.org/remastersys/repository karmic/
deb-src http://www.geekconnection.org/remastersys/repository karmic/
deb http://archive.ubuntu.com/ubuntu natty-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu natty-updates restricted main multiverse universe #Added by software-properties
deb http://ppa.launchpad.net/alexeftimie/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/alexeftimie/ppa/ubuntu natty main
deb http://ppa.launchpad.net/alexeftimie/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/alexeftimie/ppa/ubuntu natty main
deb http://ppa.launchpad.net/atareao/atareao/ubuntu natty main
deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu natty main
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu natty main
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu natty main
deb http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu natty main
deb http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu natty main
deb http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu natty main
deb http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu natty main
deb http://ppa.launchpad.net/elementaryart/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/elementaryart/ppa/ubuntu natty main
deb http://ppa.launchpad.net/elementaryart/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/elementaryart/ppa/ubuntu natty main
deb http://ppa.launchpad.net/exaile-devel/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/exaile-devel/ppa/ubuntu natty main
deb http://ppa.launchpad.net/exaile-devel/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/exaile-devel/ppa/ubuntu natty main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main
deb http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu natty main
deb http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu natty main
deb http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu natty main
deb-src http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu natty main
deb http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu natty main
deb-src http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu natty main
deb http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu natty main
deb http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu natty main
deb http://ppa.launchpad.net/madnessmike/madnessmike/ubuntu natty main
deb-src http://ppa.launchpad.net/madnessmike/madnessmike/ubuntu natty main
deb http://ppa.launchpad.net/madnessmike/madnessmike/ubuntu natty main
deb-src http://ppa.launchpad.net/madnessmike/madnessmike/ubuntu natty main
deb http://ppa.launchpad.net/malteworld/compiz/ubuntu natty main
deb-src http://ppa.launchpad.net/malteworld/compiz/ubuntu natty main
deb http://ppa.launchpad.net/malteworld/compiz/ubuntu natty main
deb-src http://ppa.launchpad.net/malteworld/compiz/ubuntu natty main
deb http://archive.getdeb.net/ubuntu oneiric-getdeb games
deb http://archive.getdeb.net/ubuntu oneiric-getdeb games
deb http://ppa.launchpad.net/philip5/extra/ubuntu natty main
deb-src http://ppa.launchpad.net/philip5/extra/ubuntu natty main
deb http://ppa.launchpad.net/rednotebook/stable/ubuntu natty main
deb-src http://ppa.launchpad.net/rednotebook/stable/ubuntu natty main
deb http://ppa.launchpad.net/rednotebook/stable/ubuntu natty main
deb-src http://ppa.launchpad.net/rednotebook/stable/ubuntu natty main
deb http://ppa.launchpad.net/screenlets/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/screenlets/ppa/ubuntu natty main
deb http://ppa.launchpad.net/screenlets/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/screenlets/ppa/ubuntu natty main
deb http://ppa.launchpad.net/speed-dreams/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/speed-dreams/ppa/ubuntu natty main
deb http://ppa.launchpad.net/speed-dreams/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/speed-dreams/ppa/ubuntu natty main
deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu natty main
deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu natty main
deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu natty main
deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu natty main
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu natty main
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu natty main
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu natty main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu natty main
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu natty main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu natty main
deb http://ppa.launchpad.net/webupd8team/themes/ubuntu natty main
deb-src http://ppa.launchpad.net/webupd8team/themes/ubuntu natty main
deb http://ppa.launchpad.net/webupd8team/themes/ubuntu natty main
deb-src http://ppa.launchpad.net/webupd8team/themes/ubuntu natty main
deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu natty main
deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu natty main
deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu natty main
deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu natty main
thomas@thomas:~$ 

```

---

### Post by thomsebastin on 2012-03-10
> **NikTh said:**
> Hi , 
Please install Synaptic 
```
 sudo apt-get install synaptic
```Then go to Synapric --> Mark all Upgrades --> Apply. 
Thanks
r u sure that i need to proceed???
[IMG]http://img444.imageshack.us/img444/1782/87599509.png[/IMG]
ther s a small warning -(doing this could allow a malicious individual to cause damage to the system)....should i ignore this?

---

### Post by thomsebastin on 2012-03-10
> **raja.genupula said:**
> I think i havent understand properly , you are getting some dependencies issues right ?

go to the situation what giving you that dependencies problem and then do what i suggested above? 

If i not properly understand your issue please explain .
Thank you .
k brother sorry for making you get confused..my basic problem is that i am not able to install few applications when i try to install, for example say, if i try to install pidgin i get these output
```
The following packages have unmet dependencies:
 pidgin : Depends: libpurple0 (>= 1:2.8.0-1) but it is not going to be installed
          Depends: perl-base (>= 5.12.4-4) but 5.10.1-17ubuntu4.1 is to be installed
          Depends: perlapi-5.12.4 but it is not installable

```here matt told that perlapi-5.12.4 was for onieric but i'm using natty.then why am i left with a package which is for another version of linux?if i can sort out that,i think we can solve the problem....any idea??

---

### Post by raja.genupula on 2012-03-10
what i am looking there is pkg's of Mysql  . actually when you're installing third party software you gonna get asking like that and you can accept that as yes. look at the list that including along with Mysql pkgs is there any other pkg installing . 100% nothing wrong will be there but better to check once .

---

### Post by raja.genupula on 2012-03-11
> **thomsebastin said:**
> k brother sorry for making you get confused..my basic problem is that i am not able to install few applications when i try to install, for example say, if i try to install pidgin i get these output
```
The following packages have unmet dependencies:
 pidgin : Depends: libpurple0 (>= 1:2.8.0-1) but it is not going to be installed
          Depends: perl-base (>= 5.12.4-4) but 5.10.1-17ubuntu4.1 is to be installed
          Depends: perlapi-5.12.4 but it is not installable

```here matt told that perlapi-5.12.4 was for onieric but i'm using natty.then why am i left with a package which is for another version of linux?if i can sort out that,i think we can solve the problem....any idea??


yeah my friend we can, open synaptic pkg manager and in the search box look for those dependencies with required versions and you can install from there . if they are not found there  then go to ubuntu packages and download and install from there .

actually in maximum cases synaptic will have all . so i hope those are in synaptic .  

try it my friend , all the best .

---

### Post by thomsebastin on 2012-03-11
> **raja.genupula said:**
> what i am looking there is pkg's of Mysql  . actually when you're installing third party software you gonna get asking like that and you can accept that as yes. look at the list that including along with Mysql pkgs is there any other pkg installing . 100% nothing wrong will be there but better to check once .
the packages are 
------------------------------
NOT AUTHENTICATED
mysql-server-5.1
mysql-client-5.1
mysql-common
mysql-server-core-5.1
php5-curl
libmysqlclient16
php5-mysql
php5-cli
libapache2-mod-php5
php5-common
php5-suhosin
TO BE INSTALLED
bsd-mailx
libonig2
libqdbm14
php5-suhosin
TO BE UPGRADED
google-chrome-stable
libapache2-mod-php5
libmysqlclient16
mysql-client-5.1
mysql-common
mysql server-5.1
mysql-server-core-5.1
php5-cli
php5-common
php5-curl
php5-mysql
tzdata
lzdata-java
----------------------------
shall i proceed?

---

### Post by raja.genupula on 2012-03-11
> **thomsebastin said:**
> the packages are 
------------------------------
NOT AUTHENTICATED
mysql-server-5.1
mysql-client-5.1
mysql-common
mysql-server-core-5.1
php5-curl
libmysqlclient16
php5-mysql
php5-cli
libapache2-mod-php5
php5-common
php5-suhosin
TO BE INSTALLED
bsd-mailx
libonig2
libqdbm14
php5-suhosin
TO BE UPGRADED
google-chrome-stable
libapache2-mod-php5
libmysqlclient16
mysql-client-5.1
mysql-common
mysql server-5.1
mysql-server-core-5.1
php5-cli
php5-common
php5-curl
php5-mysql
tzdata
lzdata-java
----------------------------
shall i proceed?

yup my friend and after this look at my above post .

---

### Post by thomsebastin on 2012-03-11
> **raja.genupula said:**
> yeah my friend we can, open synaptic pkg manager and in the search box look for those dependencies with required versions and you can install from there . if they are not found there  then go to ubuntu packages and download and install from there .

actually in maximum cases synaptic will have all . so i hope those are in synaptic .  

try it my friend , all the best .
bro those packages r not there in synaptic....and see the output which says they r not installable and they are not goin to be installed....shall i try for those .deb packages from package sites??but will they get installed since it's telling that it's not goin to be installed....:confused:

---

### Post by thomsebastin on 2012-03-11
> **raja.genupula said:**
> yup my friend and after this look at my above post .
k gimme some time i'll come back soon after upgrading them.....

---

### Post by raja.genupula on 2012-03-11
> **thomsebastin said:**
> bro those packages r not there in synaptic....and see the output which says they r not installable and they are not goin to be installed....shall i try for those .deb packages from package sites??but will they get installed since it's telling that it's not goin to be installed....:confused:

look for them , if they are not avaliable then get the main pkgs from ubuntu pkgs and try to install then with ```
sudo dpkg -i filename.deb
``` if any dependency issue raised then at that do ```
sudo apt-get install -f
```

like that install all those required three .

---

### Post by thomsebastin on 2012-03-11
> **raja.genupula said:**
> look for them , if they are not avaliable then get the main pkgs from ubuntu pkgs and try to install then with ```
sudo dpkg -i filename.deb
``` if any dependency issue raised then at that do ```
sudo apt-get install -f
```like that install all those required three .
bro downloaded all those updates but one package is not gettin installed (gettin some error)...i tried your code and here is the result
```
thomas@thomas:~$ sudo apt-get install -f
[sudo] password for thomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mysql-client-5.1
The following packages will be upgraded:
  mysql-client-5.1
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0 B/9,147 kB of archives.
After this operation, 622 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  mysql-client-5.1
Install these packages without verification [y/N]? y
(Reading database ... 334759 files and directories currently installed.)
Preparing to replace mysql-client-5.1 5.1.54-1ubuntu4 (using .../mysql-client-5.1_5.1.61-2~dotdeb.0_i386.deb) ...
Unpacking replacement mysql-client-5.1 ...
dpkg: error processing /var/cache/apt/archives/mysql-client-5.1_5.1.61-2~dotdeb.0_i386.deb (--unpack):
 trying to overwrite '/usr/bin/mysql', which is also in package mysql-client-core-5.1 5.1.54-1ubuntu4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-client-5.1_5.1.61-2~dotdeb.0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
thomas@thomas:~$ 

```

---

### Post by thomsebastin on 2012-03-11
and 6 packages are kept back....(those from getdeb)

---

### Post by matt_symes on 2012-03-11
Hi

From your sources.list and sources.list.d/* files..

> deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
deb-src [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
<snip>
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games

You have sources pointing to different releases of Ubuntu. 

I would suggest that one of these is referencing packages for a different version of Ubuntu (Oneiric) that either are not in your main Ubuntu repositories for Natty or cannot be installed as they conflict with existing packages. That is why they are not availabe when you use synaptic.

The first thing i would do is remove these sources from your lists as it's a bad idea to mix sources from different version of Ubuntu. It can cause the problems you are having. Then i would clear all the dpkg and apt caches.

Then i would update again and, depending on error messages from the update, you can remove the references to them in dpkg.

Kind regards

---

### Post by thomsebastin on 2012-03-11
> **matt_symes said:**
> Hi

From your sources.list and sources.list.d/* files..



You have sources pointing to different releases of Ubuntu. 

I would suggest that one of these is referencing packages for a different version of Ubuntu that either are not in your main Ubuntu repositories for Natty or cannot be installed as they conflict with existing packages. That is why they are not availabe when you use synaptic.

The first thing i would do is moved these sources from your lists as it's a bad idea to mix sources from different version of Ubuntu as it can cause the problems you are having.

Then i would update again. After that you can remove the references to them.

Kind regards
wow thnx matt....shall i delete those lines???will that be okay??

---

### Post by matt_symes on 2012-03-11
Hi

> and 6 packages are kept back....(those from getdeb)

There you go. Those are repositories for Oneiric. Maybe you can change them for Natty ? I don't know if they exist for Natty.

Kind regards

---

### Post by matt_symes on 2012-03-11
Hi

I may be possible to change the sources from

```
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
deb-src [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
<snip>
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games
```

to

```
deb http://archive.getdeb.net/ubuntu **natty-getdeb** apps
deb-src http://archive.getdeb.net/ubuntu natty-getdeb apps
deb http://www.geekconnection.org/remastersys/repository karmic/
deb http://archive.getdeb.net/ubuntu natty-getdeb games
deb http://archive.getdeb.net/ubuntu natty-getdeb games
```

If the natty repository exists then that may help. Clear all your dpkg and apt-get caches and then update. 

If these repos for Natty do not exist then remove them, clear caches again and update.

```
deb-src http://www.geekconnection.org/remastersys/repository karmic/
```

The above line need to go as it's for Karmic.

Post back errors.

Kind regards

---

### Post by thomsebastin on 2012-03-11
> **matt_symes said:**
> Hi

I may be possible to change the sources from

```
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
deb-src [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
<snip>
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games
```to

```
deb http://archive.getdeb.net/ubuntu **natty-getdeb** apps
deb-src http://archive.getdeb.net/ubuntu natty-getdeb apps
deb http://www.geekconnection.org/remastersys/repository karmic/
deb http://archive.getdeb.net/ubuntu natty-getdeb games
deb http://archive.getdeb.net/ubuntu natty-getdeb games
```If the natty repository exists then that may help. Clear all your dpkg and apt-get caches and then update. 

If these repos for Natty do not exist then remove them, clear caches again and update.

```
deb-src http://www.geekconnection.org/remastersys/repository karmic/
```The above line need to go as it's for Karmic.

Post back errors.

Kind regards
matt :popcorn::popcorn: guess wat.....thats it....problem has been solved.....thnx raja bro,matt n all others who helped me throughout this....it was real fun solving this....installed pidgin successfully....n here is the successful output```
thomas@thomas:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
thomas@thomas:~$ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libpurple0 pidgin-data pidgin-libnotify
Suggested packages:
  tk8.4
The following NEW packages will be installed:
  libpurple0 pidgin pidgin-data pidgin-libnotify
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,424 kB of archives.
After this operation, 10.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ natty-security/main libpurple0 i386 1:2.7.11-1ubuntu2.1 [1,743 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ natty-security/main pidgin-data all 1:2.7.11-1ubuntu2.1 [1,110 kB]                                                             
Get:3 http://archive.ubuntu.com/ubuntu/ natty-security/main pidgin i386 1:2.7.11-1ubuntu2.1 [553 kB]                                                                   
Get:4 http://archive.ubuntu.com/ubuntu/ natty/main pidgin-libnotify i386 0.14-4ubuntu4 [17.8 kB]                                                                       
Fetched 3,424 kB in 7min 39s (7,444 B/s)                                                                                                                               
Selecting previously deselected package libpurple0.
(Reading database ... 334593 files and directories currently installed.)
Unpacking libpurple0 (from .../libpurple0_1%3a2.7.11-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package pidgin-data.
Unpacking pidgin-data (from .../pidgin-data_1%3a2.7.11-1ubuntu2.1_all.deb) ...
Selecting previously deselected package pidgin.
Unpacking pidgin (from .../pidgin_1%3a2.7.11-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package pidgin-libnotify.
Unpacking pidgin-libnotify (from .../pidgin-libnotify_0.14-4ubuntu4_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for menu ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.utf8.cache...
Processing triggers for gconf2 ...
Processing triggers for python-support ...
Setting up libpurple0 (1:2.7.11-1ubuntu2.1) ...
Setting up pidgin-data (1:2.7.11-1ubuntu2.1) ...
Setting up pidgin (1:2.7.11-1ubuntu2.1) ...
Setting up pidgin-libnotify (0.14-4ubuntu4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...

```....once again thnx..it wouldn't have been possible without u all....\\:D/\\:D/=D>=D>:lol:

---

### Post by matt_symes on 2012-03-11
Hi

No worries. I'm glad it's fixed :D

The other posters in this thread did all the hard work and eliminated everything else. After that it was just a case of looking at what was left.

A good job by everybody.

Kind regards

---

### Post by NikTh on 2012-03-12
> **matt_symes said:**
> Hi



The other posters in this thread did all the hard work and eliminated everything else. After that it was just a case of looking at what was left.

A good job by everybody.

Kind regards
+1 

YEA... That's  the spirit 
  ):P

---

