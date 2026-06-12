---
title: "Apt-get doesn't install any program"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by darek_jestem on 2008-11-22
Hi everybody I have problem with apt-get install....
if I try to install any program always I have answer like this:
(for example ```
sudo apt-get install mplayer
```
```

dariusz@dariusz:~$ sudo apt-get install mplayer
[sudo] password for dariusz:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run âapt-get -f installâ to correct these:
The following packages have unmet dependencies.
  perl-modules: Depends: perl (>= 5.10.0-1) but 5.8.8-12 is to be installed
E: Unmet dependencies. Try âapt-get -f installâ with no packages (or specify a solution).

```
```
sudo apt-get -f install
```
doesn't work:/

---

### Post by SuperSonic4 on 2008-11-22
Have you updated your sources?```
sudo apt-get update
```
If that doesn't work can you post the output of your sources.list file
In terminal:
```
gksu gedit /etc/apt/sources.list
```

---

### Post by drs305 on 2008-11-22
What is the perl version in your synaptic listing? On my Intrepid 64-bit, perl 5.10.0 is available and installed, which is what your unmet dependency is. Have you updated your repositories?

---

### Post by handydan918 on 2008-11-22
> **darek_jestem said:**
> Hi everybody I have problem with apt-get install....
if I try to install any program always I have answer like this:
(for example ```
sudo apt-get install mplayer
```
```

dariusz@dariusz:~$ sudo apt-get install mplayer
[sudo] password for dariusz:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run âapt-get -f installâ to correct these:
The following packages have unmet dependencies.
  perl-modules: Depends: perl (>= 5.10.0-1) but 5.8.8-12 is to be installed
E: Unmet dependencies. Try âapt-get -f installâ with no packages (or specify a solution).

```
```
sudo apt-get -f install
```
doesn't work:/

What does "doesn't work" mean? Post error messages.

You might also try using aptitude. It often does a better job at some of the difficult dependency issues you run into.

---

### Post by darek_jestem on 2008-11-22
I have updated my repositories couple times and still the same problem...
For drs305:
I have not Synaptic...

My sources.list:

```
deb http://pl.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse 
deb-src http://pl.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse 

deb http://pl.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse 
deb-src http://pl.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse 
deb-src http://security.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu/ hardy partner

#deb http://kubuntu.org/packages/kde-latest  hardy main
#deb http://kubuntu.org/packages/amarok-latest hardy main
#deb http://kubuntu.org/packages/koffice-latest hardy main

deb http://wine.budgetdedicated.com/apt hardy main

deb http://download.skype.com/linux/repos/debian/ stable non-free
deb http://dl.google.com/linux/deb/ stable non-free

deb http://apt.wicd.net hardy extras

deb http://packages.medibuntu.org/ hardy free non-free

deb http://ppa.launchpad.net/patryk-prezu/ubuntu hardy main
deb http://ppa.launchpad.net/adamklobukowski/ubuntu/ hardy main
deb http://ppa.launchpad.net/claws-mail/ubuntu/ hardy main
deb http://ppa.launchpad.net/jussi01/ubuntu/ hardy main restricted universe multiverse
deb http://ppa.launchpad.net/kubuntu-members/ubuntu/ hardy main
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/ hardy main
deb http://ppa.launchpad.net/maarten-fonville/ubuntu/ hardy main
deb http://ppa.launchpad.net/misery/ubuntu/ hardy main
deb http://ppa.launchpad.net/secretlondon/ubuntu/ hardy main
deb http://ppa.launchpad.net/smarter/ubuntu hardy main
deb http://ppa.launchpad.net/tsimpson/ubuntu/ hardy main
deb http://ppa.launchpad.net/woodypl/ubuntu/ hardy main
deb http://ppa.launchpad.net/xmlich02/ubuntu/ hardy main
deb http://ppa.launchpad.net/ipod-touch/ubuntu/ hardy main 
deb http://ppa.launchpad.net/psyke83/ubuntu hardy main
deb http://ppa.launchpad.net/kwwii/ubuntu hardy main
deb http://ppa.launchpad.net/themuso/ubuntu hardy main

#deb http://mirror3.ubuntulinux.nl/ hardy-seveas all

deb http://morgoth.free.fr/ubuntu hardy-backports main

#deb http://archive.czessi.net/ubuntu hardy restricted universe multiverse preview

#deb http://repository.debuntu.org/ hardy multiverse

deb http://ubuntu.cafuego.net/ hardy-cafuego all

#deb http://apt.last.fm/ debian testing
deb http://pl.archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse

deb http://ppa.launchpad.net/fta/ubuntu hardy main
deb http://ppa.launchpad.net/jr/ubuntu/ hardy main
deb http://ppa.launchpad.net/motumedia/ubuntu hardy main
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb http://ppa.launchpad.net/project-neon/ubuntu/ hardy main
```

> **handydan918 said:**
> What does "doesn't work" mean? Post error messages.
As I said I have always the same error.
```
dariusz@dariusz:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
  perl-modules: Depends: perl (>= 5.10.0-1) but 5.8.8-12 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

---

### Post by darek_jestem on 2008-11-22
> **handydan918 said:**
> What does "doesn't work" mean? Post error messages.
As I said I have always the same error.
```
dariusz@dariusz:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
  perl-modules: Depends: perl (>= 5.10.0-1) but 5.8.8-12 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

---

### Post by jyaan on 2008-11-22
Maybe there is now some kind of inconsistency? Might as well try upgrading to Intrepid?

---

### Post by darek_jestem on 2008-11-22
> **jyaan said:**
> Maybe there is now some kind of inconsistency? Might as well try upgrading to Intrepid?

how?

---

### Post by darek_jestem on 2008-11-22
> **jyaan said:**
> Maybe there is now some kind of inconsistency? Might as well try upgrading to Intrepid?

How?

SORRY FOR DOUBLE POSTS!
CAN SOMEBODY DELETE ONE OF THESE?? BECOUSE I CAN'T

---

### Post by drs305 on 2008-11-22
darek_jestem,

If you are to the point of reinstalling, here is a 'hack' that might work before you resort to that. 
Open /var/lib/dpkg/status with "gksudo" and a text editor. **Make a backup copy.**
In the file, do a search for "Package: perl-modules". Delete that entire section (about 20 lines) and save the file. Then try sudo apt-get update and whatever else you are trying to do again. If it still doesn't work, delete /var/lib/dpkg/status and restore the original file.

I wouldn't recommend it except you are talking about reinstalling.

---

### Post by handydan918 on 2008-11-22
I can't recall if aptitude is installed by default, but you can install it with ```
sudo apt-get install aptitude
```

I have had remarkable success using aptitude to resolve dependency issues that apt could not. unfortunately, there is not a step-by-step for this. You sorta just gotta jump in....

---

### Post by darek_jestem on 2008-11-22
ok I did like you said and now:

```
sudo apt-get -f install
```

```
...(files list etc.)
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  perl-modules
The following NEW packages will be installed
  perl-modules
0 upgraded, 1 newly installed, 0 to remove and 279 not upgraded.
1 not fully installed or removed.
Need to get 0B/2300kB of archives.
After unpacking 12.0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up findutils (4.4.0-2ubuntu3) ...
Can't locate Pod/Usage.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/install-docs line 18.
Global symbol "$opt_rootdir" requires explicit package name at /usr/sbin/install-docs line 136.
Execution of /usr/sbin/install-docs aborted due to compilation errors.
dpkg: error processing findutils (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 findutils
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
it seems to be problem with findutils but what is this?

---

### Post by drs305 on 2008-11-22
> **darek_jestem said:**
> 
it seems to be problem with findutils but what is this?

If this is the result of eliminating the reference to perl-modules, I would delete the modified file and restore the original "status" file. If it worked you would not have received the new error message about findutils.

---

### Post by darek_jestem on 2008-11-22
Ok I did and I'm back to my old error.

---

### Post by darek_jestem on 2008-11-22
> **handydan918 said:**
> I can't recall if aptitude is installed by default, but you can install it with ```
sudo apt-get install aptitude
```

I have had remarkable success using aptitude to resolve dependency issues that apt could not. unfortunately, there is not a step-by-step for this. You sorta just gotta jump in....
Did you read my first post??
I can't install anything:/
apt-get install doesn't work

---

### Post by jyaan on 2008-11-22
There is no need to re-install to upgrade, if that is what was you meant.

By default, since Hardy is the Long Term Service release, it does not automatically show the update to Intrepid. 

Go to System > Administration > Software Sources, enter your password, then click the Updates tab in the window that pops up. Then select "Normal Releases"  from the drop-down list under "Release Upgrade". Hopefully this will do it if nothing else will.

But since the Update program is going to use apt-get... It's probably not going to work either.

It seems something really nasty happened somehow. I'll try looking for some answers, but I'm not an expert on apt-get. :S

Does dpkg work at all? You might want to try downloading the files from the Ubuntu repositories. And then
```
sudo dpkg -i file.deb
```
Maybe you could re-install Perl, apt-get and such this way. This is the most likely solution if dpkg works.

---

### Post by darek_jestem on 2008-11-23
```
dariusz@dariusz:~$ sudo dpkg -i file.deb
dpkg: error processing file.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 file.deb

```

---

### Post by -Zeus- on 2008-11-23
i think he expected you to replace file.deb with the actual filename??

---

### Post by drs305 on 2008-11-23
> **darek_jestem said:**
> ```
dariusz@dariusz:~$ sudo dpkg -i file.deb
dpkg: error processing file.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 file.deb

```

What he meant was for you to replace "file.deb" with any file you wanted to try to install, for example:
sudo dpkg -i thisisthepackagename.deb

Back to an earlier post about installing aptitude. It should be on your system. Also referring to one of the error messages:
```
[I]The following packages have unmet dependencies.
  perl-modules: Depends: perl (>= 5.10.0-1) but 5.8.8-12 is installed
E: Error, pkgProblemResolver::**Resolve generated breaks, this may be caused by held packages.**
[/I]
```

If you can run aptitude and there is a 'hold' on perl or perl-modules (preventing them from updating to 5.10), you might be able to remove it with:
```
sudo aptitude unhold perl perl-modules
```

---

### Post by darek_jestem on 2008-11-23
> **drs305 said:**
> 
If you can run aptitude and there is a 'hold' on perl or perl-modules (preventing them from updating to 5.10), you might be able to remove it with:
```
sudo aptitude unhold perl perl-modules
```
after this command
```
D...(files list etc.)
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Setting up findutils (4.4.0-2ubuntu3) ...
Can't locate Pod/Usage.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/install-docs line 18.
Global symbol "$opt_rootdir" requires explicit package name at /usr/sbin/install-docs line 136.
Execution of /usr/sbin/install-docs aborted due to compilation errors.
dpkg: error processing findutils (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 findutils
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of perl-modules:
 perl-modules depends on perl (>= 5.10.0-1); however:
  Version of perl on system is 5.8.8-12.
dpkg: error processing perl-modules (--configure):
 dependency problems - leaving unconfigured
Setting up findutils (4.4.0-2ubuntu3) ...
Can't locate Pod/Usage.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/install-docs line 18.
Global symbol "$opt_rootdir" requires explicit package name at /usr/sbin/install-docs line 136.
Execution of /usr/sbin/install-docs aborted due to compilation errors.
dpkg: error processing findutils (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 perl-modules
 findutils
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done

```

---

### Post by jyaan on 2008-11-23
Yes, that is what I meant. "file.deb" would be the name of whatever file you downloaded and were trying to install.

I would try each of these and hope that one will work:
```
gdebi file.deb
gdebi-gtk file.deb
dpkg -i file.deb
```

There is probably a way to restore the tools as well. Perhaps someone could even create an archive (eg. tar.gz or tar.bz2) file with the directories of apt or whatever you need and hope that extracting that into / would fix it.

Do you remember the last time you were able to install anything correctly? And do you remember what the last commands you did with apt were? I would like for you to attach/post your .bash_history file which is in your home directory. This file has a list of all the commands typed to the console recently. Hopefully it hasn't been too long since the problem occurred and we will be able to see what caused this to happen! It may not have been anything you did at all, though.

If you don't know how to do attachments: When you write your reply, underneath the "Submit Reply" button is a section called "Additional Options" (large red text). Click on "Manage Attachments", then click "Browse". Right-click in your Home directory (in that dialog) and make sure that "Show Hidden Files" is checked. Then look through and find **.bash_history**, click "Open", and finally click "Upload". Then submit your reply.

---

### Post by CatKiller on 2008-11-23
Can you not just remove the problem packages? ```
sudo apt-get remove perl perl-modules
```

---

### Post by darek_jestem on 2008-11-24
Ok thanks everyone;)
dpkg -i file.deb was helpful

---

### Post by Tomatz on 2008-11-24
> **drs305 said:**
> darek_jestem,

If you are to the point of reinstalling, here is a 'hack' that might work before you resort to that. 
Open /var/lib/dpkg/status with "gksudo" and a text editor. **Make a backup copy.**
In the file, do a search for "Package: perl-modules". Delete that entire section (about 20 lines) and save the file. Then try sudo apt-get update and whatever else you are trying to do again. If it still doesn't work, delete /var/lib/dpkg/status and restore the original file.

I wouldn't recommend it except you are talking about reinstalling.

Its probably the million repos he has. Something is conflicting along the way.

Comment all repos bar the official ubuntu repos.

Then do a **sudo apt-get update**.

---

