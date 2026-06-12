---
title: "Uninstall gcc 4.4 and install gcc 3.4 for Qemu ?"
date: 2010-11-21
forum: Packaging and Compiling Programs
---

### Post by QT embedded on 2010-11-21
i want build Qemu for MIPS but i cant install gcc 3.4 like this instruction: [http://manio.org/sesc-tutorial-1-instaall-whole-sesc-step-by-step-577.html](http://manio.org/sesc-tutorial-1-instaall-whole-sesc-step-by-step-577.html)

it message error: 
> 
[SIZE=4][COLOR=Red]**sudo apt-get install gcc-3.4**[/COLOR][/SIZE]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc-3.4 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  g++-3.4: Depends: gcc-3.4 (= 3.4.6-6ubuntu3) but 3.4.6-8ubuntu2 is to  be installed
           Depends: gcc-3.4-base (= 3.4.6-6ubuntu3) but 3.4.6-8ubuntu2  is to be installed
  libstdc++6-dev: Depends: gcc-3.4-base (= 3.4.6-6ubuntu3) but  3.4.6-8ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or  specify a solution).
hieunt@hieunt-laptop:~$ sudo apt-get update
Ign file: ./ Release.gpg
Ign file:/home/hieunt/Desktop/gcc3.4/ ./ Translation-en_US
Ign file: ./ Release
Ign file: ./ Packages
Ign file: ./ Packages
Err file: ./ Packages
  File not found
Get:1 [http://dl.google.com]("http://dl.google.com/")  stable Release.gpg [197B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/)  stable/main Translation-en_US
Get:2 [http://dl.google.com]("http://dl.google.com/")  stable Release [1,347B]
Get:3 [http://dl.google.com]("http://dl.google.com/")  stable/main Packages [1,088B]
Fetched 2,632B in 0s (8,658B/s)
W: Failed to fetch file:/home/hieunt/Desktop/gcc3.4/./Packages.gz  File  not found

E: Some index files failed to download, they have been ignored, or old  ones used instead.
hieunt@hieunt-laptop:~$ sudo gedit /etc/apt/sources.list
hieunt@hieunt-laptop:~$ sudo apt-get update
Ign file: ./ Release.gpg
Ign file:/home/hieunt/gcc3.4/ ./ Translation-en_US
Ign file: ./ Release             
Ign file: ./ Packages            
Ign file: ./ Packages            
Err file: ./ Packages            
  File not found
Get:1 [http://dl.google.com]("http://dl.google.com/")  stable Release.gpg [197B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/)  stable/main Translation-en_US
Get:2 [http://dl.google.com]("http://dl.google.com/")  stable Release [1,347B]
Get:3 [http://dl.google.com]("http://dl.google.com/")  stable/main Packages [1,088B]
Fetched 2,632B in 1s (1,445B/s)
W: Failed to fetch file:/home/hieunt/gcc3.4/./Packages.gz  File not  found

E: Some index files failed to download, they have been ignored, or old  ones used instead.
hieunt@hieunt-laptop:~$ 

---

### Post by mc4man on 2010-11-22
well you're mixing (or rather attempting to) versions.
The previously installed gcc,cpp and base packages are from most likely one of the recent end of life ubuntu's (intrepid or jaunty

So either track down the same version #'s for g++ and libstdc++6-dev (3.4.6-8ubuntu2) in the old-release repo's or just use the hardy (3.4.6-6ubuntu3) or better yet the hardy-updates (3.4.6-6ubuntu5) versions for ALL 5 packages

Ex
> ~/Desktop/gcc3$ ls
cpp-3.4_3.4.6-6ubuntu5_i386.deb  gcc-3.4-base_3.4.6-6ubuntu5_i386.deb
g++-3.4_3.4.6-6ubuntu5_i386.deb  libstdc++6-dev_3.4.6-6ubuntu5_i386.deb
gcc-3.4_3.4.6-6ubuntu5_i386.deb

> gcc3$ sudo dpkg -i *.deb
[sudo] password for doug: 
Selecting previously deselected package cpp-3.4.
(Reading database ... 192342 files and directories currently installed.)
Unpacking cpp-3.4 (from cpp-3.4_3.4.6-6ubuntu5_i386.deb) ...
Selecting previously deselected package g++-3.4.
Unpacking g++-3.4 (from g++-3.4_3.4.6-6ubuntu5_i386.deb) ...
Selecting previously deselected package gcc-3.4.
Unpacking gcc-3.4 (from gcc-3.4_3.4.6-6ubuntu5_i386.deb) ...
Selecting previously deselected package gcc-3.4-base.
Unpacking gcc-3.4-base (from gcc-3.4-base_3.4.6-6ubuntu5_i386.deb) ...
Selecting previously deselected package libstdc++6-dev.
Unpacking libstdc++6-dev (from libstdc++6-dev_3.4.6-6ubuntu5_i386.deb) ...
Setting up gcc-3.4-base (3.4.6-6ubuntu5) ...
Setting up cpp-3.4 (3.4.6-6ubuntu5) ...
Processing triggers for man-db ...
Setting up gcc-3.4 (3.4.6-6ubuntu5) ...
Setting up libstdc++6-dev (3.4.6-6ubuntu5) ...
Setting up g++-3.4 (3.4.6-6ubuntu5) ...

If going hardy-updates route start collecting here
[http://packages.ubuntu.com/hardy-updates/gcc-3.4](http://packages.ubuntu.com/hardy-updates/gcc-3.4)

---

