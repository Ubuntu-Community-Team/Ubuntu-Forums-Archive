---
title: "Security update failed due to errors"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by LearningPerson on 2008-09-12
Hello,

I have had problems since I got a "notification error" and had to do a manual fsck.  First I couldn't install Gnucash (also a slib and guile error) and now this error appeared when I downloaded the latest security update:

E: slib: subprocess post-installation script returned error exit status 2

E: guile-1.6-slib: dependency problems - leaving unconfigured

E: libfreetype6-dev: subprocess post-installation 
script returned error exit status 2


Any help would be most appreciated.

Sharon

---

### Post by SunnyRabbiera on 2008-09-12
In a terminal can you give us the output of sudo apt-get update?

---

### Post by LearningPerson on 2008-09-12
> **SunnyRabbiera said:**
> In a terminal can you give us the output of sudo apt-get update?

Sunny,  Here it is:
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Reading package lists... Done
sharon@sharon-dan:~$ 

Thanks,

Sharon

---

### Post by SunnyRabbiera on 2008-09-12
well looks like apt is working.
as a experiment to make sure that apt is not at fault here in a terminal input:
sudo apt-get install Gnucash
and try to install the package via the terminal, lucky for you apt is easy enough to figure out even in command line.

---

### Post by LearningPerson on 2008-09-12
> **SunnyRabbiera said:**
> well looks like apt is working.
as a experiment to make sure that apt is not at fault here in a terminal input:
sudo apt-get install Gnucash
and try to install the package via the terminal, lucky for you apt is easy enough to figure out even in command line.

Here it is, Sunny:

sharon@sharon-dan:~$ sudo apt-get install Gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Gnucash
sharon@sharon-dan:~$ 

Thanks,
Sharon

---

### Post by SunnyRabbiera on 2008-09-12
woops, de capitalise that.
sudo apt-get install gnucash

sorry I have a habit of capitalizing the names of applications

---

### Post by LearningPerson on 2008-09-12
> **SunnyRabbiera said:**
> woops, de capitalise that.
sudo apt-get install gnucash

sorry I have a habit of capitalizing the names of applications

OK, Sunny,

sharon@sharon-dan:~$ sudo apt-get install Gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Gnucash
sharon@sharon-dan:~$ 
sharon@sharon-dan:~$ sudo apt-get gnucash
E: Invalid operation gnucash
sharon@sharon-dan:~$ sudo apt-get install gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnucash-common libgtkhtml3.8-15
Suggested packages:
  gnucash-sql libgtkhtml3.8-dbg
Recommended packages:
  gnucash-docs
The following NEW packages will be installed:
  gnucash gnucash-common libgtkhtml3.8-15
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
sharon@sharon-dan:~$ 

Thanks,
Sharon

---

### Post by SunnyRabbiera on 2008-09-12
ah, well there is your problem:
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

did you try a restart?
sometimes that fixes that kind of issue.

---

### Post by LearningPerson on 2008-09-12
> **SunnyRabbiera said:**
> ah, well there is your problem:
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

did you try a restart?
sometimes that fixes that kind of issue.

Hi Sunny,

I close down the PC each night and restart it in the morning....and have had "var/cache..." errors for a few days.  They all seem to center around "guile" and "slib".

If you think I should shut down again and hope for another outcome, I will but I suspect there is another problem - or possibly another problem as well.

Please advise.  Thanks,  

Sharon

---

### Post by SunnyRabbiera on 2008-09-12
> **LearningPerson said:**
> Hi Sunny,

I close down the PC each night and restart it in the morning....and have had "var/cache..." errors for a few days.  They all seem to center around "guile" and "slib".

If you think I should shut down again and hope for another outcome, I will but I suspect there is another problem - or possibly another problem as well.

Please advise.  Thanks,  

Sharon

well for measure yes try another restart as you never know, before you tried to install these packages in synaptic a bet so maybe trying apt was a good idea, sometimes it helps sometimes it doesnt.
If it doesnt work lucky for you there are fixes but first lets try that restart.

---

### Post by LearningPerson on 2008-09-12
> **SunnyRabbiera said:**
> ah, well there is your problem:
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

did you try a restart?
sometimes that fixes that kind of issue.

OK, Sunny, I restarted and I get the same as usual:
sharon@sharon-dan:~$ sudo apt-get gnucash
[sudo] password for sharon: 
E: Invalid operation gnucash
sharon@sharon-dan:~$ sudo apt-get gnucash
E: Invalid operation gnucash
sharon@sharon-dan:~$ civils
Sorry, command-not-found has crashed! Please file a bug report at:
[https://bugs.launchpad.net/ubuntu/+source/command-not-found](https://bugs.launchpad.net/ubuntu/+source/command-not-found)
Please include the following information with the report:
No module named CommandNotFound
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 10, in <module>
    from CommandNotFound import CommandNotFound
ImportError: No module named CommandNotFound
Python version: 2.5.2 final 0
bash: civils: command not found
sharon@sharon-dan:~$ sudo apt-get install gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnucash-common libgtkhtml3.8-15
Suggested packages:
  gnucash-sql libgtkhtml3.8-dbg
Recommended packages:
  gnucash-docs
The following NEW packages will be installed:
  gnucash gnucash-common libgtkhtml3.8-15
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/6579kB of archives.
After this operation, 27.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libgtkhtml3.8-15.
(Reading database ... 152893 files and directories currently installed.)
Unpacking libgtkhtml3.8-15 (from .../libgtkhtml3.8-15_1%3a3.13.5-1ubuntu1_i386.deb) ...
Selecting previously deselected package gnucash-common.
Unpacking gnucash-common (from .../gnucash-common_2.2.4-1ubuntu1_all.deb) ...
Selecting previously deselected package gnucash.
Unpacking gnucash (from .../gnucash_2.2.4-1ubuntu1_i386.deb) ...
Setting up slib (3a4-4) ...
Cannot open `/usr/share/doc-base/data/scrollkeeper.map' for reading: No such file or directory at /usr/share/perl5/Debian/DocBase/Programs/Scrollkeeper.pm line 60
dpkg: error processing slib (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of guile-1.6-slib:
 guile-1.6-slib depends on slib (>= 3a2-3); however:
  Package slib is not configured yet.
dpkg: error processing guile-1.6-slib (--configure):
 dependency problems - leaving unconfigured
Setting up libfreetype6-dev (2.3.5-1ubuntu4.8.04.1) ...
Cannot open `/usr/share/doc-base/data/scrollkeeper.map' for reading: No such file or directory at /usr/share/perl5/Debian/DocBase/Programs/Scrollkeeper.pm line 60
dpkg: error processing libfreetype6-dev (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libgtkhtml3.8-15 (1:3.13.5-1ubuntu1) ...

Setting up gnucash-common (2.2.4-1ubuntu1) ...
dpkg: dependency problems prevent configuration of gnucash:
 gnucash depends on guile-1.6-slib; however:
  Package guile-1.6-slib is not configured yet.
 gnucash depends on slib (>= 3a2-5); however:
  Package slib is not configured yet.
dpkg: error processing gnucash (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 slib
 guile-1.6-slib
 libfreetype6-dev
 gnucash
E: Sub-process /usr/bin/dpkg returned an error code (1)
sharon@sharon-dan:~$ 


What do you think?  

Thanks,
Sharon

---

### Post by SunnyRabbiera on 2008-09-12
alright, well now we can see if there are other issues.
try sudo dpkg --configure -a

---

### Post by LearningPerson on 2008-09-12
> **SunnyRabbiera said:**
> alright, well now we can see if there are other issues.
try sudo dpkg --configure -a

Here it is, Sunny,

Setting up slib (3a4-4) ...
Cannot open `/usr/share/doc-base/data/scrollkeeper.map' for reading: No such file or directory at /usr/share/perl5/Debian/DocBase/Programs/Scrollkeeper.pm line 60
dpkg: error processing slib (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of guile-1.6-slib:
 guile-1.6-slib depends on slib (>= 3a2-3); however:
  Package slib is not configured yet.
dpkg: error processing guile-1.6-slib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnucash:
 gnucash depends on guile-1.6-slib; however:
  Package guile-1.6-slib is not configured yet.
 gnucash depends on slib (>= 3a2-5); however:
  Package slib is not configured yet.
dpkg: error processing gnucash (--configure):
 dependency problems - leaving unconfigured
Setting up libfreetype6-dev (2.3.5-1ubuntu4.8.04.1) ...
Cannot open `/usr/share/doc-base/data/scrollkeeper.map' for reading: No such file or directory at /usr/share/perl5/Debian/DocBase/Programs/Scrollkeeper.pm line 60
dpkg: error processing libfreetype6-dev (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 slib
 guile-1.6-slib
 gnucash
 libfreetype6-dev
sharon@sharon-dan:~$ 

Sharon

---

### Post by SunnyRabbiera on 2008-09-12
lets try sudo apt-get update next.

---

### Post by LearningPerson on 2008-09-12
> **SunnyRabbiera said:**
> lets try sudo apt-get update next.

OK, Sunny:

sharon@sharon-dan:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Reading package lists... Done
sharon@sharon-dan:~$ 

Sharon

---

### Post by SunnyRabbiera on 2008-09-12
Hmm, quite strange, the error isnt consistent and is gone now according to apt-get update.
How about we experiment now, to be sure, close down your terminal and try synaptic and see if you can install a package...
try installing Celestia via synaptic, see if it spits out errors.

---

### Post by LearningPerson on 2008-09-12
> **SunnyRabbiera said:**
> Hmm, quite strange, the error isnt consistent and is gone now according to apt-get update.
How about we experiment now, to be sure, close down your terminal and try synaptic and see if you can install a package...
try installing Celestia via synaptic, see if it spits out errors.

OK Sunny, here goes:

E: slib: subprocess post-installation script returned error exit status 2
E: guile-1.6-slib: dependency problems - leaving unconfigured
E: libfreetype6-dev: subprocess post-installation script returned error exit status 2
E: gnucash: dependency problems - leaving unconfigured

Hmmm, what does that mean?

Sharon

---

### Post by SunnyRabbiera on 2008-09-12
do you have anything that is listed as broken?
does synaptic warn about broken packages?

---

### Post by LearningPerson on 2008-09-12
> **SunnyRabbiera said:**
> do you have anything that is listed as broken?
does synaptic warn about broken packages?


No, and in fact, Sunny, I clicked on "Edit, Fix Broken Packages" and that didn't do anything.

Sharon

---

### Post by SunnyRabbiera on 2008-09-12
well its obvious that your installation of gnucash is what goofed you up here.
How did you originally try to install it?

---

### Post by LearningPerson on 2008-09-12
> **SunnyRabbiera said:**
> well its obvious that your installation of gnucash is what goofed you up here.
How did you originally try to install it?

Well, Sunny, on starting up a few mornings ago, I first had a notification error that gave me a choice between deleting and not deleting.  Didn't look too closely and deleted.  Then I restarted and had to do a manual fsck to which I replied "Yes" to every question.  

Then since I used Synaptic to install Gnucash and went back and forth between Synaptic an the Terminal to completely uninstall it.  

I always got the "slib-guile" errors.

Thanks,

Sharon  PS I will head out to see a friend in about 10 minutes so may or may not get your reply....but will look for it anxiously upon my return!

---

### Post by SunnyRabbiera on 2008-09-12
> **LearningPerson said:**
> Well, Sunny, on starting up a few mornings ago, I first had a notification error that gave me a choice between deleting and not deleting.  Didn't look too closely and deleted.  Then I restarted and had to do a manual fsck to which I replied "Yes" to every question.  

Then since I used Synaptic to install Gnucash and went back and forth between Synaptic an the Terminal to completely uninstall it.  

I always got the "slib-guile" errors.

Thanks,

Sharon  PS I will head out to see a friend in about 10 minutes so may or may not get your reply....but will look for it anxiously upon my return!

yeh you screwed up somewhere, that is why its important to read through things before committing to them.

---

### Post by Yannick Le Saint kyncani on 2008-09-12
> **LearningPerson said:**
> Setting up libfreetype6-dev (2.3.5-1ubuntu4.8.04.1) ...
Cannot open `/usr/share/doc-base/data/scrollkeeper.map' for reading: No such file or directory at /usr/share/perl5/Debian/DocBase/Programs/Scrollkeeper.pm line 60
dpkg: error processing libfreetype6-dev (--configure):


Hi LearningPerson,

Could you try first to "sudo apt-get -f install", because it's always good to start with this, it fixes errors sometime.

Then "sudo apt-get install --reinstall doc-base" because this package provides scrollkeeper.map I think.

Then redo a "sudo apt-get -f install", just for the fun of it.

And post the output of all this. I hope this will work :)

---

### Post by SunnyRabbiera on 2008-09-12
> **Yannick Le Saint kyncani said:**
> Hi LearningPerson,

Could you try first to "sudo apt-get -f install", because it's always good to start with this, it fixes errors sometime.

Then "sudo apt-get install --reinstall doc-base" because this package provides scrollkeeper.map I think.

Then redo a "sudo apt-get -f install", just for the fun of it.

And post the output of all this. I hope this will work :)

this would have been next on my things to try.

---

### Post by LearningPerson on 2008-09-12
> **Yannick Le Saint kyncani said:**
> Hi LearningPerson,

Could you try first to "sudo apt-get -f install", because it's always good to start with this, it fixes errors sometime.

Then "sudo apt-get install --reinstall doc-base" because this package provides scrollkeeper.map I think.

Then redo a "sudo apt-get -f install", just for the fun of it.

And post the output of all this. I hope this will work :)

Hi Sunny,

Things look different now - dare I hope?!

sharon@sharon-dan:~$ sudo apt-get -f install

Reading package lists... Done

Building dependency tree       

Reading state information... Done

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

4 not fully installed or removed.

After this operation, 0B of additional disk space will be used.

Setting up slib (3a4-4) ...

Cannot open `/usr/share/doc-base/data/scrollkeeper.map' for reading: No such file or directory at /usr/share/perl5/Debian/DocBase/Programs/Scrollkeeper.pm line 60

dpkg: error processing slib (--configure):

 subprocess post-installation script returned error exit status 2

dpkg: dependency problems prevent configuration of guile-1.6-slib:

 guile-1.6-slib depends on slib (>= 3a2-3); however:

  Package slib is not configured yet.

dpkg: error processing guile-1.6-slib (--configure):

 dependency problems - leaving unconfigured

Setting up libfreetype6-dev (2.3.5-1ubuntu4.8.04.1) ...

Cannot open `/usr/share/doc-base/data/scrollkeeper.map' for reading: No such file or directory at /usr/share/perl5/Debian/DocBase/Programs/Scrollkeeper.pm line 60

dpkg: error processing libfreetype6-dev (--configure):

 subprocess post-installation script returned error exit status 2

dpkg: dependency problems prevent configuration of gnucash:

 gnucash depends on guile-1.6-slib; however:

  Package guile-1.6-slib is not configured yet.

 gnucash depends on slib (>= 3a2-5); however:

  Package slib is not configured yet.

dpkg: error processing gnucash (--configure):

 dependency problems - leaving unconfigured

Errors were encountered while processing:

 slib

 guile-1.6-slib

 libfreetype6-dev

 gnucash

E: Sub-process /usr/bin/dpkg returned an error code (1)

sharon@sharon-dan:~$ 


sharon@sharon-dan:~$ sudo apt-get install --reinstall doc-base

[sudo] password for sharon: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.

4 not fully installed or removed.

Need to get 57.7kB of archives.

After this operation, 0B of additional disk space will be used.

Do you want to continue [Y/n]? y

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main doc-base 0.8.7 [57.7kB]

Fetched 57.7kB in 3s (17.7kB/s)                        

(Reading database ... 154619 files and directories currently installed.)

Preparing to replace doc-base 0.8.7 (using .../doc-base_0.8.7_all.deb) ...

Cannot open `/usr/share/doc-base/data/scrollkeeper.map' for reading: No such file or directory at /usr/share/perl5/Debian/DocBase/Programs/Scrollkeeper.pm line 60

dpkg: warning - old pre-removal script returned error exit status 2

dpkg - trying script from the new package instead ...

dpkg: ... it looks like that went OK.

Unpacking replacement doc-base ...

Setting up slib (3a4-4) ...



Setting up guile-1.6-slib (1.6.8-6ubuntu1) ...



Setting up libfreetype6-dev (2.3.5-1ubuntu4.8.04.1) ...



Setting up gnucash (2.2.4-1ubuntu1) ...



Setting up doc-base (0.8.7) ...



sharon@sharon-dan:~$ 



sharon@sharon-dan:~$ sudo apt-get -f install

Reading package lists... Done

Building dependency tree       

Reading state information... Done

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sharon@sharon-dan:~$


Sharon

---

### Post by LearningPerson on 2008-09-12
> **SunnyRabbiera said:**
> this would have been next on my things to try.


Hi Sunny,  

I didn't realize someone new had come in on the help line.  Yannick?

Anyway, I tried this and it looks different - should I try Gnucash again?

sharon@sharon-dan:~$ sudo apt-get -f install

Reading package lists... Done

Building dependency tree       

Reading state information... Done

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

4 not fully installed or removed.

After this operation, 0B of additional disk space will be used.

Setting up slib (3a4-4) ...

Cannot open `/usr/share/doc-base/data/scrollkeeper.map' for reading: No such file or directory at /usr/share/perl5/Debian/DocBase/Programs/Scrollkeeper.pm line 60

dpkg: error processing slib (--configure):

 subprocess post-installation script returned error exit status 2

dpkg: dependency problems prevent configuration of guile-1.6-slib:

 guile-1.6-slib depends on slib (>= 3a2-3); however:

  Package slib is not configured yet.

dpkg: error processing guile-1.6-slib (--configure):

 dependency problems - leaving unconfigured

Setting up libfreetype6-dev (2.3.5-1ubuntu4.8.04.1) ...

Cannot open `/usr/share/doc-base/data/scrollkeeper.map' for reading: No such file or directory at /usr/share/perl5/Debian/DocBase/Programs/Scrollkeeper.pm line 60

dpkg: error processing libfreetype6-dev (--configure):

 subprocess post-installation script returned error exit status 2

dpkg: dependency problems prevent configuration of gnucash:

 gnucash depends on guile-1.6-slib; however:

  Package guile-1.6-slib is not configured yet.

 gnucash depends on slib (>= 3a2-5); however:

  Package slib is not configured yet.

dpkg: error processing gnucash (--configure):

 dependency problems - leaving unconfigured

Errors were encountered while processing:

 slib

 guile-1.6-slib

 libfreetype6-dev

 gnucash

E: Sub-process /usr/bin/dpkg returned an error code (1)

sharon@sharon-dan:~$ 


sharon@sharon-dan:~$ sudo apt-get install --reinstall doc-base

[sudo] password for sharon: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.

4 not fully installed or removed.

Need to get 57.7kB of archives.

After this operation, 0B of additional disk space will be used.

Do you want to continue [Y/n]? y

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main doc-base 0.8.7 [57.7kB]

Fetched 57.7kB in 3s (17.7kB/s)                        

(Reading database ... 154619 files and directories currently installed.)

Preparing to replace doc-base 0.8.7 (using .../doc-base_0.8.7_all.deb) ...

Cannot open `/usr/share/doc-base/data/scrollkeeper.map' for reading: No such file or directory at /usr/share/perl5/Debian/DocBase/Programs/Scrollkeeper.pm line 60

dpkg: warning - old pre-removal script returned error exit status 2

dpkg - trying script from the new package instead ...

dpkg: ... it looks like that went OK.

Unpacking replacement doc-base ...

Setting up slib (3a4-4) ...



Setting up guile-1.6-slib (1.6.8-6ubuntu1) ...



Setting up libfreetype6-dev (2.3.5-1ubuntu4.8.04.1) ...



Setting up gnucash (2.2.4-1ubuntu1) ...



Setting up doc-base (0.8.7) ...



sharon@sharon-dan:~$ 



sharon@sharon-dan:~$ sudo apt-get -f install

Reading package lists... Done

Building dependency tree       

Reading state information... Done

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sharon@sharon-dan:~$


Thanks,

Sharon

---

### Post by SunnyRabbiera on 2008-09-12
well personally I am out of ideas, anyone else up to the plate?

---

### Post by LearningPerson on 2008-09-12
> **SunnyRabbiera said:**
> well personally I am out of ideas, anyone else up to the plate?

Sunny, Doesn't my post of the 3 steps look clean now?  Did I miss something?  

It looks as though it took.

Sharon

---

### Post by LearningPerson on 2008-09-12
> **SunnyRabbiera said:**
> well personally I am out of ideas, anyone else up to the plate?

Thank you, thank you, Sunny, it worked!!!

Sharon

---

### Post by SunnyRabbiera on 2008-09-12
> **LearningPerson said:**
> Thank you, thank you, Sunny, it worked!!!

Sharon

ah so it did work, thought it didnt :lolflag:

---

### Post by Yannick Le Saint kyncani on 2008-09-12
> **LearningPerson said:**
> $ sudo apt-get -f install

Reading package lists... Done

Building dependency tree       

Reading state information... Done

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sharon@sharon-dan:~$

Yep, it's all fine now.

---

### Post by LearningPerson on 2008-09-12
> **Yannick Le Saint kyncani said:**
> Yep, it's all fine now.

Thanks so much, Yannick!

Do you enter my thank you to you or is there somewhere I should do it?

Sharon

---

### Post by Yannick Le Saint kyncani on 2008-09-13
> **LearningPerson said:**
> Thanks so much, Yannick!

Do you enter my thank you to you or is there somewhere I should do it?

Hi LearningPerson, there's an icon in each post that looks like a medal, if you fly your mouse over it, a tip say it's a "thank you" icon, that's the one :)

Just for information, the only thing that made it work was the "apt-get install --reinstall thing".

So next time you have a "file missing"-like message :

- Install apt-file
- Use apt-file to locate which package provide this file
- Install/reinstall the package

Of course none of this is not so newbie-like ...

---

