---
title: "qt designer"
date: 2005-12-23
forum: Programming Talk
---

### Post by grim918 on 2005-12-23
im teaching myself qt3/c++ programming and i have a book that says that there is a qt designer. it says that on unix platforms to type in designer and that qt designer should launch. i have qt3 set up and running and i am having no problems so far. but when i try to run the designer command to get the qt3 designer i get a message that the command is not recognized.

i installed qt3 with:
sudo apt-get install qt3-dev-tools
sudo apt-get install libqt3-mt-dev

does anyone know if qt designer is included with these packages. and if so where is it located because i cant find it in any file.
thank you.

---

### Post by darth_vector on 2005-12-23
sudo apt-cache search qt designer brought up the following:

qt3-designer - Qt3 Designer

that looks like what your after.

---

### Post by asimon on 2005-12-23
You may also want to install qt3-assistant and qt3-doc to be able to access the documentation from designer (or by starting assistant). There is also qt3-examples which contains the examples.

---

### Post by grim918 on 2005-12-23
ok thank you i got it working.

---

### Post by grim918 on 2005-12-24
ok i had qt designer working but when i tried to compile my first program that i created i found out that the qmake command had been taken away.
when i installed designer with

sudo apt-get install qt3-designer

it said that the following packages were removed
qt3-dev-tools
libqt3-mt-dev

i didnt think much of it because i thought that they would be reinstalled with the qt designer installation. but like i said when i tried using qmake to compile my program i get a command not recognized. i tried to just reinstall 
qt3-dev-tools and libqt3-mt-dev
but when i did that it uninstalled qt designer which is not what i wanted.
does anyone know if qt designer comes with a different name for qmake. or how do you compile programs on qt designer.

---

### Post by asimon on 2005-12-25
[QUOTE=grim918]when i installed designer with

sudo apt-get install qt3-designer

it said that the following packages were removed
qt3-dev-tools
libqt3-mt-dev[/quote]
This is is definitely not right. They should be all installable together and I have no problems doing so:
```
# apt-get install qt3-designer libqt3-mt-dev qt3-dev-tools
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  libqt3-i18n
Recommended packages:
  libqt3-compat-headers
The following NEW packages will be installed:
  libqt3-mt-dev qt3-designer qt3-dev-tools
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 5301kB of archives.
After unpacking 12.0MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com dapper/main qt3-dev-tools 3:3.3.5-1ubuntu5 [1224kB]
Get:2 http://archive.ubuntu.com dapper/main libqt3-mt-dev 3:3.3.5-1ubuntu5 [51.1kB]
Get:3 http://archive.ubuntu.com dapper/universe qt3-designer 3:3.3.5-1ubuntu5 [4025kB]
Fetched 4373kB in 35s (123kB/s)
Selecting previously deselected package qt3-dev-tools.
(Reading database ... 131232 files and directories currently installed.)
Unpacking qt3-dev-tools (from .../qt3-dev-tools_3%3a3.3.5-1ubuntu5_i386.deb) ...
Selecting previously deselected package libqt3-mt-dev.
Unpacking libqt3-mt-dev (from .../libqt3-mt-dev_3%3a3.3.5-1ubuntu5_i386.deb) ...
Selecting previously deselected package qt3-designer.
Unpacking qt3-designer (from .../qt3-designer_3%3a3.3.5-1ubuntu5_i386.deb) ...
Setting up qt3-dev-tools (3.3.5-1ubuntu5) ...

Setting up libqt3-mt-dev (3.3.5-1ubuntu5) ...
Setting up qt3-designer (3.3.5-1ubuntu5) ...
```
Okay, that was for Dapper, but I don't remember having problems with the designer under Breezy.

Is your repository up-to-date? I.e. did you run 'apt-get update' or the respective action under synaptic or adept?

[QUOTE=grim918]
i didnt think much of it because i thought that they would be reinstalled with the qt designer installation. but like i said when i tried using qmake to compile my program i get a command not recognized. i tried to just reinstall 
qt3-dev-tools and libqt3-mt-dev
but when i did that it uninstalled qt designer which is not what i wanted.
does anyone know if qt designer comes with a different name for qmake. or how do you compile programs on qt designer.[/QUOTE]
qt3-designer doesn't come with any different name for qmake etc. qmake comes from qt3-dev-tools and the needed header files from libqt3-mt-dev. Therefore it would be a big fat bug if those three packages can not be installed together.

Can you post the output of
```
sudo apt-get install libqt3-mt-dev qt3-designer qt3-dev-tools
```
from a konsole? Before that make sure you also run 'sudo apt-get update'.

---

### Post by grim918 on 2005-12-25
i ran sudo apt-get update , and everything went well on that.
then i tried to run the following and this is what i get:

grim@localhost:/$ sudo apt-get install libqt3-mt-dev qt3-designer qt3-dev-tools
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: libqt3-mt (= 3:3.3.4-8ubuntu5) but it is not going to be installed
  qt3-dev-tools: Depends: libqt3-mt (>= 3:3.3.4) but it is not going to be installed
E: Broken packages


i would appreciate any help that you can give me. thank you.

---

### Post by asimon on 2005-12-25
[QUOTE=grim918]The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: libqt3-mt (= 3:3.3.4-8ubuntu5) but it is not going to be installed
  qt3-dev-tools: Depends: libqt3-mt (>= 3:3.3.4) but it is not going to be installed
[/QUOTE]
And if you do 'sudo apt-get install libqt3-mt' does it then want to uninstall something?

---

### Post by grim918 on 2005-12-25
after i ran sudo apt-get install libqt3-mt , this is what happened

grim@localhost:/$ sudo apt-get install libqt3-mt
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc
The following packages will be REMOVED:
  libqt3c102-mt mysqlcc qt3-designer
The following NEW packages will be installed:
  libqt3-mt
0 upgraded, 1 newly installed, 3 to remove and 472 not upgraded.
Need to get 3290kB of archives.
After unpacking 7553kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libqt3-mt 3:3.3.4-8ubuntu5 [3290kB]
Fetched 3290kB in 9s (331kB/s)

Preconfiguring packages ...
(Reading database ... 59154 files and directories currently installed.)
Removing qt3-designer ...
Removing mysqlcc ...
Removing libqt3c102-mt ...
Selecting previously deselected package libqt3-mt.
(Reading database ... 58915 files and directories currently installed.)
Unpacking libqt3-mt (from .../libqt3-mt_3%3a3.3.4-8ubuntu5_i386.deb) ...
Setting up libqt3-mt (3.3.4-8ubuntu5) ...

grim@localhost:/$

as you can see it completely removed qt3-designer as well as mysqlcc which i am now going to have to reinstall. do you think it will work properly if i just switch to ubuntu 5.04
im using 5.10.

---

### Post by asimon on 2005-12-25
From your output I think that qt3-designer and mysqlcc depend on libqt3c102-mt but qt3-dev-tools and of course libqt3-mt-dev depend on libqt3-mt. libqt3c102-mt and libqt3-mt conflict with each other (that is known and right so).

But I wonder were this package libqt3c102-mt (and packages which still depend on it) comes from. libqt3c102-mt was the name of the qt3-library package of Hoary. But for Breezy it was renamed to libqt3-mt. Breezy doesn't contain libqt3c102-mt anymore.

Do you by any chance have additional repositories enabled or mix hoary and breezy repositories?

---

### Post by grim918 on 2005-12-26
i dont know if im mixing repositories. here is a list of the repositories.

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by asimon on 2005-12-27
[QUOTE=grim918]i dont know if im mixing repositories. here is a list of the repositories.[/quote]
Yes, you're mixing hoary with breezy, no wonder you get dependency problems.

Just change your sources.list to this and you should be fine:

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

## Backports
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports main universe multiverse restricted
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
```

Then doing a
```
$ sudo apt-get update
$ sudo apt-get dist-upgrade

```
should remove any old hoary stuff and update everything to breezy. The dependency problems you have should then be gone.

---

### Post by grim918 on 2005-12-29
here is a list of my repositories. i dont know if i am mixing them though.

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

thank you for the help.

---

### Post by grim918 on 2005-12-29
nevermind the above post. dont know what i was thinking. ill go and change my repositories. i will let you know how it goes. thank you

---

### Post by grim918 on 2005-12-29
yes that did take care of the program. thank you for the help. now i can go do some programming.

---

