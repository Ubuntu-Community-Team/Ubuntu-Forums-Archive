---
title: "how to install pygame in feisty"
date: 2007-06-13
forum: Programming Talk
---

### Post by getuk_telo on 2007-06-13
can some body tell me how to install pygame in feisty

i have dowload these all packages required 

python-pygame_1.7.1release-4.1_i386.deb      
and 
    * debhelper (>= 5.0.38)
    * libsdl-image1.2-dev (>= 1.2.0-1.1)
    * libsdl-mixer1.2-dev (>= 1.2.0-1.1)
    * libsdl-ttf2.0-dev (>= 1.2.2-1.1)
    * libsdl1.2-dev (>= 1.2.2-3.1)
    * libsmpeg-dev (>= 0.4.5+cvs20030824-1.3)
    * python-all-dev (>= 2.3.5-11)
    * python-central (>= 0.5.6)
    * python-numeric (>= 24.2-3)
    * sharutils

from launchpad 

but when i use dpkg - i *.deb , i got some error

---

### Post by slimdog360 on 2007-06-13
```
sudo apt-get install python-pygame
```

if you wanted to do it your way you would probably have to tell everyone this error.

---

### Post by getuk_telo on 2007-06-14
> **slimdog360 said:**
> ```
sudo apt-get install python-pygame
```

if you wanted to do it your way you would probably have to tell everyone this error.

thank for reply ,

this when i tried you suggestion

Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-pygame is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libsdl-image1.2-dev: Depends: libsdl-image1.2 (= 1.2.5-2) but it is not installable
                       Depends: libc6-dev but it is not installable
                       Depends: libjpeg62-dev but it is not installable
                       Depends: libpng12-dev but it is not installable
                       Depends: libtiff4-dev but it is not installable
                       Depends: zlib1g-dev but it is not installable
  libsdl-mixer1.2-dev: Depends: libsdl-mixer1.2 (= 1.2.6-1.1build1) but it is not installable
                       Depends: libc6-dev but it is not installable
                       Depends: libogg-dev but it is not installable
                       Depends: libvorbis-dev but it is not installable
  libsdl-ttf2.0-dev: Depends: libsdl-ttf2.0-0 (= 2.0.8-3build1) but it is not installable
                     Depends: libc6-dev but it is not installable
                     Depends: libfreetype6-dev but it is not installable
  libsdl1.2-dev: Depends: libx11-dev but it is not installable
                 Depends: libglu1-xorg-dev but it is not installable or
                          libglu-dev but it is not installable
  libsmpeg-dev: Depends: libsmpeg0 (= 0.4.5+cvs20030824-1.9build1) but it is not installable
  python-all-dev: Depends: python-all (= 2.5.1~rc1-0ubuntu3) but it is not installable
                  Depends: python-dev (= 2.5.1~rc1-0ubuntu3) but it is not installable
                  Depends: python2.4-dev but it is not installable
                  Depends: python2.5-dev but it is not installable
  python-pygame: Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
                 Depends: libsdl-mixer1.2 (>= 1.2.6) but it is not installable
                 Depends: libsdl-ttf2.0-0 but it is not installable
                 Depends: libsmpeg0 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

and when i use [B]sudo apt-get -f install python-pygame
[/B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-pygame is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libsdl-image1.2-dev: Depends: libsdl-image1.2 (= 1.2.5-2) but it is not installable
                       Depends: libc6-dev but it is not installable
                       Depends: libjpeg62-dev but it is not installable
                       Depends: libpng12-dev but it is not installable
                       Depends: libtiff4-dev but it is not installable
                       Depends: zlib1g-dev but it is not installable
  libsdl-mixer1.2-dev: Depends: libsdl-mixer1.2 (= 1.2.6-1.1build1) but it is not installable
                       Depends: libc6-dev but it is not installable
                       Depends: libogg-dev but it is not installable
                       Depends: libvorbis-dev but it is not installable
  libsdl-ttf2.0-dev: Depends: libsdl-ttf2.0-0 (= 2.0.8-3build1) but it is not installable
                     Depends: libc6-dev but it is not installable
                     Depends: libfreetype6-dev but it is not installable
  libsdl1.2-dev: Depends: libx11-dev but it is not installable
                 Depends: libglu1-xorg-dev but it is not installable or
                          libglu-dev but it is not installable
  libsmpeg-dev: Depends: libsmpeg0 (= 0.4.5+cvs20030824-1.9build1) but it is not installable
  python-all-dev: Depends: python-all (= 2.5.1~rc1-0ubuntu3) but it is not installable
                  Depends: python-dev (= 2.5.1~rc1-0ubuntu3) but it is not installable
                  Depends: python2.4-dev but it is not installable
                  Depends: python2.5-dev but it is not installable
  python-pygame: Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
                 Depends: libsdl-mixer1.2 (>= 1.2.6) but it is not installable
                 Depends: libsdl-ttf2.0-0 but it is not installable
                 Depends: libsmpeg0 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

and i try this **sudo apt-get -f install**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev libsdl1.2-dev libsmpeg-dev
  python-all-dev python-pygame
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7340kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 88693 files and directories currently installed.)
Removing libsdl-image1.2-dev ...
Removing libsdl-mixer1.2-dev ...
Removing libsdl-ttf2.0-dev ...
Removing libsmpeg-dev ...
Removing libsdl1.2-dev ...
Removing python-all-dev ...
Removing python-pygame ...

and when i try again  **sudo apt-get install python-pygame**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-pygame is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-pygame has no installation candidate

do yo have any sugesstion from there?

thanks

---

### Post by getuk_telo on 2007-06-14
the problem has been solved , 

i just try  to update my package with **sudo aptitude** and use **G** for update
after update was finished, i try again this **sudo apt-get install python-pygame**

and it work

this the result
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libsdl-image1.2 libsdl-mixer1.2 libsdl-ttf2.0-0 libsmpeg0
The following NEW packages will be installed:
  libsdl-image1.2 libsdl-mixer1.2 libsdl-ttf2.0-0 libsmpeg0 python-pygame
0 upgraded, 5 newly installed, 0 to remove and 52 not upgraded.
Need to get 1091kB of archives.
After unpacking 3346kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) feisty/main libsdl-image1.2 1.2.5-2 [29.2kB]
Get:2 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) feisty/main libsmpeg0 0.4.5+cvs20030824-1.9build1 [102kB]     
Get:3 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) feisty/main libsdl-mixer1.2 1.2.6-1.1build1 [136kB]           
Get:4 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) feisty/main libsdl-ttf2.0-0 2.0.8-3build1 [14.9kB]            
Get:5 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) feisty/universe python-pygame 1.7.1release-4.1 [808kB]        
Fetched 1091kB in 1m56s (9356B/s)                                                                
Selecting previously deselected package libsdl-image1.2.
(Reading database ... 88033 files and directories currently installed.)
Unpacking libsdl-image1.2 (from .../libsdl-image1.2_1.2.5-2_i386.deb) ...
Selecting previously deselected package libsmpeg0.
Unpacking libsmpeg0 (from .../libsmpeg0_0.4.5+cvs20030824-1.9build1_i386.deb) ...
Selecting previously deselected package libsdl-mixer1.2.
Unpacking libsdl-mixer1.2 (from .../libsdl-mixer1.2_1.2.6-1.1build1_i386.deb) ...
Selecting previously deselected package libsdl-ttf2.0-0.
Unpacking libsdl-ttf2.0-0 (from .../libsdl-ttf2.0-0_2.0.8-3build1_i386.deb) ...
Selecting previously deselected package python-pygame.
Unpacking python-pygame (from .../python-pygame_1.7.1release-4.1_i386.deb) ...
Setting up libsdl-image1.2 (1.2.5-2) ...

Setting up libsmpeg0 (0.4.5+cvs20030824-1.9build1) ...

Setting up libsdl-mixer1.2 (1.2.6-1.1build1) ...

Setting up libsdl-ttf2.0-0 (2.0.8-3build1) ...

Setting up python-pygame (1.7.1release-4.1) ...


> **getuk_telo said:**
> thank for reply ,

this when i tried you suggestion

Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-pygame is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libsdl-image1.2-dev: Depends: libsdl-image1.2 (= 1.2.5-2) but it is not installable
                       Depends: libc6-dev but it is not installable
                       Depends: libjpeg62-dev but it is not installable
                       Depends: libpng12-dev but it is not installable
                       Depends: libtiff4-dev but it is not installable
                       Depends: zlib1g-dev but it is not installable
  libsdl-mixer1.2-dev: Depends: libsdl-mixer1.2 (= 1.2.6-1.1build1) but it is not installable
                       Depends: libc6-dev but it is not installable
                       Depends: libogg-dev but it is not installable
                       Depends: libvorbis-dev but it is not installable
  libsdl-ttf2.0-dev: Depends: libsdl-ttf2.0-0 (= 2.0.8-3build1) but it is not installable
                     Depends: libc6-dev but it is not installable
                     Depends: libfreetype6-dev but it is not installable
  libsdl1.2-dev: Depends: libx11-dev but it is not installable
                 Depends: libglu1-xorg-dev but it is not installable or
                          libglu-dev but it is not installable
  libsmpeg-dev: Depends: libsmpeg0 (= 0.4.5+cvs20030824-1.9build1) but it is not installable
  python-all-dev: Depends: python-all (= 2.5.1~rc1-0ubuntu3) but it is not installable
                  Depends: python-dev (= 2.5.1~rc1-0ubuntu3) but it is not installable
                  Depends: python2.4-dev but it is not installable
                  Depends: python2.5-dev but it is not installable
  python-pygame: Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
                 Depends: libsdl-mixer1.2 (>= 1.2.6) but it is not installable
                 Depends: libsdl-ttf2.0-0 but it is not installable
                 Depends: libsmpeg0 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

and when i use [B]sudo apt-get -f install python-pygame
[/B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-pygame is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libsdl-image1.2-dev: Depends: libsdl-image1.2 (= 1.2.5-2) but it is not installable
                       Depends: libc6-dev but it is not installable
                       Depends: libjpeg62-dev but it is not installable
                       Depends: libpng12-dev but it is not installable
                       Depends: libtiff4-dev but it is not installable
                       Depends: zlib1g-dev but it is not installable
  libsdl-mixer1.2-dev: Depends: libsdl-mixer1.2 (= 1.2.6-1.1build1) but it is not installable
                       Depends: libc6-dev but it is not installable
                       Depends: libogg-dev but it is not installable
                       Depends: libvorbis-dev but it is not installable
  libsdl-ttf2.0-dev: Depends: libsdl-ttf2.0-0 (= 2.0.8-3build1) but it is not installable
                     Depends: libc6-dev but it is not installable
                     Depends: libfreetype6-dev but it is not installable
  libsdl1.2-dev: Depends: libx11-dev but it is not installable
                 Depends: libglu1-xorg-dev but it is not installable or
                          libglu-dev but it is not installable
  libsmpeg-dev: Depends: libsmpeg0 (= 0.4.5+cvs20030824-1.9build1) but it is not installable
  python-all-dev: Depends: python-all (= 2.5.1~rc1-0ubuntu3) but it is not installable
                  Depends: python-dev (= 2.5.1~rc1-0ubuntu3) but it is not installable
                  Depends: python2.4-dev but it is not installable
                  Depends: python2.5-dev but it is not installable
  python-pygame: Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
                 Depends: libsdl-mixer1.2 (>= 1.2.6) but it is not installable
                 Depends: libsdl-ttf2.0-0 but it is not installable
                 Depends: libsmpeg0 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

and i try this **sudo apt-get -f install**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev libsdl1.2-dev libsmpeg-dev
  python-all-dev python-pygame
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7340kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 88693 files and directories currently installed.)
Removing libsdl-image1.2-dev ...
Removing libsdl-mixer1.2-dev ...
Removing libsdl-ttf2.0-dev ...
Removing libsmpeg-dev ...
Removing libsdl1.2-dev ...
Removing python-all-dev ...
Removing python-pygame ...

and when i try again  **sudo apt-get install python-pygame**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-pygame is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-pygame has no installation candidate

do yo have any sugesstion from there?

thanks

---

