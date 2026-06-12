---
title: "problem installing perl modules"
date: 2006-08-03
forum: Programming Talk
---

### Post by raspberryh on 2006-08-03
Hi,
I'm trying to install some Perl modules, and I'm having some problems (FYI, I'm VERY new to Linux)...
I am root, btw...
When I had Fedora installed, I installed the modules with no problem... But now on Ubuntu I can't. Well here is basically what is happening:
> heather@alien-lifeform:~/Desktop/perl modules/DB_File-1.814$ perl Makefile.PL
Parsing config.in...
Looks Good.
Note (probably harmless): No library found for -ldb
Writing Makefile for DB_File
heather@alien-lifeform:~/Desktop/perl modules/DB_File-1.814$ make
bash: make: command not found
I was basically following the instructions that I found on a website for installing Perl modules. It said to type "perl Makefile.PL", then "make", then "make test", then "make install".
Thanks!
Heather

---

### Post by cantormath on 2006-08-03
> **raspberryh said:**
> Hi,
I'm trying to install some Perl modules, and I'm having some problems (FYI, I'm VERY new to Linux)...
I am root, btw...
When I had Fedora installed, I installed the modules with no problem... But now on Ubuntu I can't. Well here is basically what is happening:

I was basically following the instructions that I found on a website for installing Perl modules. It said to type "perl Makefile.PL", then "make", then "make test", then "make install".
Thanks!
Heather

Hi 
Firstly,do you have make installed?
Secondly, you shouldnt be root, just sudo whatever command you want.  You certainly dont want to login as root, just open the terminal as sudo -i to get it to flip to root permanently.
what perl mods are you trying to install?

---

### Post by raspberryh on 2006-08-03
> **cantormath said:**
> Hi 
Firstly,do you have make installed?
Secondly, you shouldnt be root, just sudo whatever command you want.  You certainly dont want to login as root, just open the terminal as sudo -i to get it to flip to root permanently.
what perl mods are you trying to install?
Do I have make installed? I don't know, I don't even know what that is. Like I said, I'm VERY new to Linux. Anyways, doesn't that already come with Linux, whatever it is?
Why can't I su root? It's annoying have to type sudo every time. Can't I just super-user to root? What is wrong with that?
The perl mods that I'm trying to install are:

HTML::LinkExtor
LWP::Simple
HTML::Parse
HTML::Element
DB_File
Tree::Binary::Search
Thread::Queue
Digest::MD5

Thanks

---

### Post by cantormath on 2006-08-03
> **raspberryh said:**
> Do I have make installed? I don't know, I don't even know what that is. Like I said, I'm VERY new to Linux. Anyways, doesn't that already come with Linux, whatever it is?
Why can't I su root? It's annoying have to type sudo every time. Can't I just super-user to root? What is wrong with that?
The perl mods that I'm trying to install are:

HTML::LinkExtor
LWP::Simple
HTML::Parse
HTML::Element
DB_File
Tree::Binary::Search
Thread::Queue
Digest::MD5

Thanks

Thats totally cool, at least you are using linux.  Thats the biggest step ::grin::.
I believe the modules are in the repositories (online), but I am currently updating my kernel as we speak, so I am unable to search the repositories when I am downloading from them.  I will check when I am done.

---

### Post by raspberryh on 2006-08-03
Well I did get the modules off of that CPAN website...
What did you mean by not having make installed? Do I need to do something for that?

---

### Post by cantormath on 2006-08-03
> **raspberryh said:**
> Well I did get the modules off of that CPAN website...
What did you mean by not having make installed? Do I need to do something for that?

What I am suggesting about that repositories is that if they (the modules) are in the repositories, then you could simply apt-get install whatever module package you want, and you wouldnt have to make anything.

ie) in a terminal
cantormath-laptop:~# sudo apt-get update
cantormath-laptop:~# sudo apt-cache search HTML::LinkExtor
you should get:
libhtml-linkextractor-perl - Perl module used to extract links from HTML documents
so let install it:
cantormath-laptop:~# sudo apt-get install libhtml-linkextractor-perl
if prompted (y/n), type y.

again

cantormath@cantormath-laptop:~$ apt-cache search HTML::Element
libhtml-element-extended-perl - extended HTML::Element classes
cantormath-laptop:~# sudo apt-get install libhtml-element-extended-perl

If you want more information on the packages or if you want to search this way using a gui interface, goto 
System>Administration>Synaptic.

You can search for packages in synaptic, ie perl modules, HTML::Elements or CPAN in the search bar and install them by clicking on the item.  If you are prompted that some other packages are going to be install, that should be fine, they are dependencies of whatever you choose.  Be careful though if you are prompted with something say it packages are going to be removed, ie) ubuntu-desktop.


Regarding my make comment, you said that the error was that the make command was not found, that probably means that it is not installed.

its easy to check, open a terminal and type:

cantormath-laptop:~# sudo -i
cantormath-laptop:~# find / -name make

if you get something like:
/usr/bin/make
/usr/share/doc/make
/usr/share/lintian/overrides/make

you have it installed, and there is another problem.
if you get nothing, you need to install make.

you can install make, but I would just go ahead and install the [build-essential]("http://packages.ubuntu.com/dapper/devel/build-essential"), its all most people need, and it include make.
open terminal:

cantormath-laptop:~#sudo apt-get install build-essential

if prompted (y/n) say y.

If you still need to make the perl mods, you should be able to now.

---

### Post by raspberryh on 2006-08-03
Wow, thanks for all your help! I really appreciate it.
I am kind of confused though, because when I used the search, it didn't give any results...
> root@alien-lifeform:/home/heather# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Fetched 3B in 10s (0B/s)
Reading package lists... Done
root@alien-lifeform:/home/heather# apt-cache search HTML::LinkExtor
root@alien-lifeform:/home/heather# apt-cache search HTML::Element


:(

---

### Post by ifokkema on 2006-08-04
> **cantormath said:**
> cantormath-laptop:~# find / -name make
A slightly faster way is to do:
```
which make
```
(checks if the 'make' command is in your path)
or
```
dpkg -l make
```
(checks if the 'make' package is installed)
If it returns nothing, you don't have it :)

> **raspberryh said:**
> Wow, thanks for all your help! I really appreciate it.
I am kind of confused though, because when I used the search, it didn't give any results...
The package repositories have different lists. The package you want is in the universe repository, and that's not enabled by default.
Please see [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more info and a how-to about how to add this repository.

---

### Post by raspberryh on 2006-08-04
Hey thanks so much ifokkema!!!
I added the universal repository and most of the perl modules showed up in the search after that. But some of them didn't. Do I need to add more repositories? How do I know which ones I need to add for a specific perl module?
Again, thanks SO much for your help! :D 
Heather

---

### Post by ifokkema on 2006-08-04
> **raspberryh said:**
> Hey thanks so much ifokkema!!!
You're welcome :)

> **raspberryh said:**
> I added the universal repository and most of the perl modules showed up in the search after that. But some of them didn't. Do I need to add more repositories?
I think that's basically it. There's multiverse, but that doesn't contain any perl modules, I believe. Universe contains lots, though.

If there's no result to your search, I think Perl's CPAN would be the other option...

> **raspberryh said:**
> How do I know which ones I need to add for a specific perl module?
That's a good question, and actually, I wouldn't know. If you've got everything enabled, you're getting all packages that are in Ubuntu. There are a few repositories on the Ubuntu servers: In the 'dapper' lists there is main, restricted, universe and multiverse. And then there's the 'dapper-security' (bug fixes) and 'dapper-backports' (newer versions of the software packages) lists and those two have main, restricted, universe and multiverse as well.

There are people or certain software packages that have their own repositories online, which can be found by googling... And if no-one has any repositories... it comes down to the plain old downloading the source/compiling stuff... Or, in the case of Perl, CPAN.

---

### Post by cantormath on 2006-08-04
> **raspberryh said:**
> Hey thanks so much ifokkema!!!
I added the universal repository and most of the perl modules showed up in the search after that. But some of them didn't. Do I need to add more repositories? How do I know which ones I need to add for a specific perl module?
Again, thanks SO much for your help! :D 
Heather

After you get what you can out of the universe repository, it is safest to go back into the sources.list (/etc/apt/sources.list) and recomment the universe repos.  You run a risk of stability if you update from the universe without being careful.

---

### Post by ifokkema on 2006-08-05
> **cantormath said:**
> You run a risk of stability if you update from the universe without being careful.
Why? What are you afraid of?
I'm not sure if the universe packages have been tested as extensively as the main ones, but I'm not sure if you're referring to that.

I've never had any form of stability problems with packages from the universe repositories. Ubuntu is way more stable than Debian Sid anyway :)

---

### Post by cantormath on 2006-08-05
> **ifokkema said:**
> Why? What are you afraid of?
I'm not sure if the universe packages have been tested as extensively as the main ones, but I'm not sure if you're referring to that.

I've never had any form of stability problems with packages from the universe repositories. Ubuntu is way more stable than Debian Sid anyway :)

that is indeed what Im refering too.  Just a warning, Im not sure what they are doing so I don't how safe they want to be.

---

### Post by cantormath on 2006-08-05
> **raspberryh said:**
> Hey thanks so much ifokkema!!!
I added the universal repository and most of the perl modules showed up in the search after that. But some of them didn't. Do I need to add more repositories? How do I know which ones I need to add for a specific perl module?
Again, thanks SO much for your help! :D 
Heather

if you want to make those modules from cpan
just
 install the build-essential 
```
sudo apt-get install build-essential
```
 download the gz and 
```
tar zxvf <thingDownloaded>.tar.gz
```
then go into the folder and 
```
sudo perl Makefile.PL
sudo make
sudo make install

```

---

### Post by raspberryh on 2006-08-05
> **cantormath said:**
> if you want to make those modules from cpan
just
 install the build-essential 
```
sudo apt-get install build-essential
```
 download the gz and 
```
tar zxvf <thingDownloaded>.tar.gz
```
then go into the folder and 
```
sudo perl Makefile.PL
sudo make
sudo make install

```
Oh yeah I did end up doing that for the ones that weren't found in the repository. Thanks though!

---

### Post by Gigabyte on 2006-08-08
> **cantormath said:**
> What I am suggesting about that repositories is that if they (the modules) are in the repositories, then you could simply apt-get install whatever module package you want, and you wouldnt have to make anything.

ie) in a terminal
cantormath-laptop:~# sudo apt-get update
cantormath-laptop:~# sudo apt-cache search HTML::LinkExtor
you should get:
libhtml-linkextractor-perl - Perl module used to extract links from HTML documents
so let install it:
cantormath-laptop:~# sudo apt-get install libhtml-linkextractor-perl
if prompted (y/n), type y.

again

cantormath@cantormath-laptop:~$ apt-cache search HTML::Element
libhtml-element-extended-perl - extended HTML::Element classes
cantormath-laptop:~# sudo apt-get install libhtml-element-extended-perl

If you want more information on the packages or if you want to search this way using a gui interface, goto 
System>Administration>Synaptic.

You can search for packages in synaptic, ie perl modules, HTML::Elements or CPAN in the search bar and install them by clicking on the item.  If you are prompted that some other packages are going to be install, that should be fine, they are dependencies of whatever you choose.  Be careful though if you are prompted with something say it packages are going to be removed, ie) ubuntu-desktop.


Wow! That's great! I had a very similar problem with some Perl modules (LWP::UserAgent, Crypt::SSLeay and MIME::Lite) and it works perfectly now. I'm new to Ubuntu but used Red Hat before; I was used to the 'perl CPAN install ...' method (which failed earlier today) and find Ubuntu so clever and easy to use. I got all my missing modules installed in no time and perfectly working right after my first attempt!

Many thanks! :-)

---

