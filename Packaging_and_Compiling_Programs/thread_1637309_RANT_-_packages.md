---
title: "RANT - packages"
date: 2010-12-04
forum: Packaging and Compiling Programs
---

### Post by nikkae on 2010-12-04
From my experience, allot of packages of applications are dependent on things. Isn't the purpose of a package to remove the head aches of compiling from source?

Recently, I tried to compile something from source on a computer that did not have internet access.. and as it happened, I was missing libraries that were required.. sure, ok.. so I jump on a computer with internet access and obtained the necessary packages of libraries it did require, only to get back to the computer and find that those packages required other libraries, and then THOSE packages needed libraries, and AGAIN!!!

This is absolutely stupid.. Windows developers never make installer packages that require dependencies to install! Its purpose defeating.. Most Debian developers need to cut this **** out.

---

### Post by oldsoundguy on 2010-12-04
> **nikkae said:**
> From my experience, allot of packages of applications are dependent on things. Isn't the purpose of a package to remove the head aches of compiling from source?

Recently, I tried to compile something from source on a computer that did not have internet access.. and as it happened, I was missing libraries that were required.. sure, ok.. so I jump on a computer with internet access and obtained the necessary packages of libraries it did require, only to get back to the computer and find that those packages required other libraries, and then THOSE packages needed libraries, and AGAIN!!!

This is absolutely stupid.. Windows developers never make installer packages that require dependencies to install! Its purpose defeating.. Most Debian developers need to cut this **** out.

Really?  Windows has an entire file that is full of dependencies .. it is called the .reg file and usually is full of obsolete, outdated and unused garbage that has to be removed at regular intervals or your computer will slow down.
When you change or remove a program in Windows, that crap is left behind .. not so with the majority of Linux programs .. (some minor exceptions but it does not take a third party program and a bunch of time to do a clean up as Linux comes with it's own cleaners that you do not have to download and keep updated!)

---

### Post by amauk on 2010-12-04
I think you misunderstand what packages are and the design differences between windows & Linux WRT how programs deal with library dependencies

Anyway, under Debian based distros, you can get all the build dependencies for package "foo" using:
```
apt-get build-dep foo
```

---

### Post by nikkae on 2010-12-04
> When you change or remove a program in Windows, that crap is left behind

Thats true, but I fail to see how that correlates with file dependencies of a package/removal of an application.

Also, I disagree strongly that most Linux programs do not leave 'residue' after being removed. From my experience half of them do.


> Anyway, under Debian based distros, you can get all the build dependencies for package "foo" using:

True, but what happens if I don't have an internet connection? Why can't the developer just make the package so it doesn't depend on anything to install??

---

### Post by nikkae on 2010-12-04
**** I replied to you guys posts, but it hasn't gone through.. anyway, my feedback to developers is stop making packages that depend on things to install.

---

### Post by SevenMachines on 2010-12-04
apt-offline is designed for this task

* run apt-offline on your offline machine to generate a signature file of required downloads for that machine, it has options for binary packages and dependencies and also for marking required build dependencies, whichever you want

* take the signature file generated to your online machine and get apt-offline to use the file to download all the needed files, i think you can even have them put into a handy archive

* transfer the packages/archive to the offline machine and install

---

### Post by SevenMachines on 2010-12-04
Quick example, hopefully helpful, and hopefully right, its not something i use much :)

Here I want to install abuse on a disconnected machine (--install-packages abuse), i also want the source(--install-src-packages abuse), and the build-deps i need to build it(--src-build-dep), obviously you can use whatever combination of these options you require, add extra packages, etc...

* On the non-networked machine
> $ sudo apt-offline set abuse-offline.sig --install-packages abuse --src-build-dep --install-src-packages abuse* take abuse-offline.sig to a networked machine, then...
> sudo apt-offline get abuse-offline.sig --no-checksum --bundle abuse-offline.zip* Take abuse-offline.zip to your offline machine, it should contain all you need, for example (yours may not match up exactly)

> $ unzip -l abuse-offline.zip 
Archive:  abuse-offline.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
  3309296  2010-12-04 16:48   abuse-frabs_2.11-1_all.deb
   330214  2010-12-04 16:48   abuse_1%3a0.7.1-1ubuntu1_i386.deb
     1273  2010-12-04 16:48   abuse-sdl_0.7.1-1ubuntu1.dsc
   719285  2010-12-04 16:48   abuse-sdl_0.7.1.orig.tar.gz
     5412  2010-12-04 16:48   abuse-sdl_0.7.1-1ubuntu1.diff.gz
   533798  2010-12-04 16:48   libslang2-dev_2.2.2-4ubuntu1_i386.deb
   139264  2010-12-04 16:48   libaa1-dev_1.4p5-38build1_i386.deb
   509054  2010-12-04 16:48   libasound2-dev_1.0.23-1ubuntu2.1_i386.deb
   121708  2010-12-04 16:48   libaudiofile-dev_0.2.6-8ubuntu1_i386.deb
   927092  2010-12-04 16:48   libcaca-dev_0.99.beta17-1_i386.deb
    26492  2010-12-04 16:48   libesd0-dev_0.2.41-7_i386.deb
   216662  2010-12-04 16:48   libglu1-mesa-dev_7.9~git20100924-0ubuntu2_i386.deb
   514984  2010-12-04 16:48   libaudio-dev_1.9.2-3_i386.deb
   841240  2010-12-04 16:48   libsdl1.2-dev_1.2.14-6ubuntu3_i386.deb
   319290  2010-12-04 16:48   quilt_0.48-7_all.deb
---------                     -------
  8515064                     15 files

---

### Post by KIAaze on 2010-12-04
Interesting.
Thanks SevenMachines. I had never heard of apt-offline before. :)

Anyway, here's some information for installation of packages on offline PCs:
[https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)

(I just added apt-offline. ;))

> From my experience, allot of packages of applications are dependent on things. Isn't the purpose of a package to remove the head aches of compiling from source?

Yes it is and the debian package system (as well as RPMs and all other package systems out there, including things like NSIS installers on Windows) do remove the headaches of compiling from source.
Installing dependencies does not mean compiling from source.
> 
Recently, I tried to compile something from source on a computer that did not have internet access.. and as it happened, I was missing libraries that were required.. sure, ok.. so I jump on a computer with internet access and obtained the necessary packages of libraries it did require, only to get back to the computer and find that those packages required other libraries, and then THOSE packages needed libraries, and AGAIN!!!

cf my link above about offline installations.

> 
This is absolutely stupid.. Windows developers never make installer packages that require dependencies to install! Its purpose defeating.. Most Debian developers need to cut this **** out. 
You never had to install DirectX for some games or GTK for Gimp and Pidgin?
However it is true that most installers for Windows do not require installation of additional packages.
This is either because they only use standard Windows libraries or bundle the libraries with their installer.

The consequences of this are that Windows comes with lots of libraries by default and that some libraries are installed multiple times.
So a default Windows install takes a lot of space (between 5 and 10 GB for XP after all Windows updates if I remember correctly), more than an Ubuntu install.
And for an equivalent number of programs/functionalities, you probably need more space too, each program coming with its own math, physics, graphics, encryption, etc libraries.

And then there's also the security problems that come with having multiple versions, not all updated, of similar libraries... And the problem of (sometimes badly) reinventing the wheel, but that's a general problem of the closed source world.

---

