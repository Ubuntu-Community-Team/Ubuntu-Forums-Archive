---
title: "Update problem"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by shobuz992 on 2013-07-31
hello,
I, too have a persistent problem that I have been trying to solve that resembles JiraiyaSenjou's post here.
When I run the Update Manager for Ubuntu 10.04 LTS,
I get an "update complete" message; but the updates have failed.

The message is in the attached png.

I have tried some suggestions I found on other boards that did not help; 
but I don't know how to proceed further and whether I will break something
without getting the correct instructions from someone here on Ubuntu Forums

Here (below) is the output of what I tried in terminal mode
```


  @-desktop:~$ dpkg --audit
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 wine-compholio       The Compholio Edition is a special build of the popular WINE

@-desktop:~$ sudo dpkg --configure --pending
[sudo] password for rick: 
dpkg: status database area is locked by another process
@-desktop:~$ sudo dpkg --configure --pending
@-desktop:~$ dpkg -l base-files
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  base-files     5.0.0ubuntu20. Debian base system miscellaneous files
@-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libopal3.6.6 libxml++2.6-2 python-twisted-mail ubufox
  python-twisted-lore python-twisted-news libfile-find-rule-perl
  python-twisted-conch python-twisted-words libslv2-9 python-twisted rtkit
  libffado2 libtext-glob-perl libgnomecanvasmm-2.6-1c2a libpt2.6.5 liblo7
  libaubio2 python-twisted-runner liblrdf0 python-pyasn1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine-compholio
Recommended packages:
  libjpeg8 libssl1.0.0
The following packages will be upgraded:
  wine-compholio
1 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
Need to get 0B/15.7MB of archives.
After this operation, 2,064kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wine-compholio' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre-headless' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
@-desktop:~$ apt-get autoremove wine-compholio
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
@-desktop:~$ sudo apt-get autoremove wine-compholio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cvs gettext libaubio2 libcapi20-3 libffado2 libfile-find-rule-perl libgnomecanvasmm-2.6-1c2a liblo7 liblrdf0 libnumber-compare-perl libopal3.6.6
  libosmesa6 libpt2.6.5 libslv2-9 libtext-glob-perl libxml++2.6-2 netflix-desktop odbcinst odbcinst1debian1 python-pyasn1 python-twisted
  python-twisted-conch python-twisted-lore python-twisted-mail python-twisted-news python-twisted-runner python-twisted-words rtkit ubufox unixodbc
  wine-browser-installer wine-compholio
0 upgraded, 0 newly installed, 32 to remove and 8 not upgraded.
1 not fully installed or removed.
After this operation, 193MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wine-compholio' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre-headless' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
@-desktop:~$ sudo dpkg --configure --pending
@-desktop:~$                                    
```


As you can see, I cannot update ANY packages or remove ANY packages.
I've tried this in "Synaptic Pkg Manager", too and it will not remove or update. I also cannot "unselect" the "wine-compholio"
package in Update Manager. 

@Blazemore Will the solution you gave @JiraiyaSenjou work for me as well,
or do i need to do something different?

Thank you for your help.
BTW.. I am glad to see Ubuntu Forums back on-line. I do appreciate this site very much.

Shobuz99

---

### Post by Bashing-om on 2013-07-31
@shobuz992 ( as you are now known as) Hi !

Here is the deal in your situation:
Version 10.04 had reached End Of Life for the desktop and no longer has support.
see:
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

The easier solution IMHO, is to back up your data and do a fresh install of a current supported version. Updating from 10.04 is fraught with possible mishaps.
There is a learning curve for a new desktop and many options exist. It will be in your best interest to research and make an informed decision to meet your desires for a desk top environment..... unity is great, but it is different.

[INDENT][INDENT]change can be good
[/INDENT][/INDENT]

---

### Post by shobuz992 on 2013-07-31
> **Bashing-om said:**
> @shobuz992 ( as you are now known as) Hi !

Here is the deal in your situation:
Version 10.04 had reached End Of Life for the desktop and no longer has support.
see:
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

The easier solution IMHO, is to back up your data and do a fresh install of a current supported version. Updating from 10.04 is fraught with possible mishaps.
There is a learning curve for a new desktop and many options exist. It will be in your best interest to research and make an informed decision to meet your desires for a desk top environment..... unity is great, but it is different.[INDENT][INDENT]change can be good
[/INDENT]
[/INDENT]


Trust me when I say that I appreciate your reply and advice to upgrade....However, I have 10.04 LTS 32 bit on my laptop (Dell Latitude D630) and
I have had NO problems updating ANYTHING. 
The two differences between machines are thus: My desktop (the one with the problem) is a 64bit machine and I'm NOT using Wine-Compholio on my laptop.
This issue of the package update failure, is somehow related to the wine-compholio pkg, in my humble opinion.
Again, I appreciate the advice to upgrade to 12.04 or whatever, on my Desktop....but until I do, I need to resolve the issue there currently
before I backup ANYTHING. Isn't there any advice on how to fix this???
Thanks for your reply, too.
Shobuz99 (and Shobuz992)

---

### Post by Bashing-om on 2013-07-31
shobuz992;

Welp, we can try and fix 10.04 ... not a good security measure to say the least, but ->
As a starting point to do so... will have to edit the sources.list files ( /etc/apt/sources.list ) to point to the archived repository and see if we can (re-)install the old openjdk-6-jre-XXX files ... Wine,-> will just have to play than one by ear .. see what results.
See:
[http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release)

As I no longer have 10.04 installed I have no access to the repository and thus totally dependent on you for all relevant info ( communications time lag is going to be significant).

If that is your desire, I am here to help - maybe a learning experience for all

---

### Post by shobuz992 on 2013-07-31
> **Bashing-om said:**
> shobuz992;

Welp, we can try and fix 10.04 ... not a good security measure to say the least, but ->
As a starting point to do so... will have to edit the sources.list files ( /etc/apt/sources.list ) to point to the archived repository and see if we can (re-)install the old openjdk-6-jre-XXX files ... Wine,-> will just have to play than one by ear .. see what results.
See:
[http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release)

As I no longer have 10.04 installed I have no access to the repository and thus totally dependent on you for all relevant info ( communications time lag is going to be significant).

If that is your desire, I am here to help - maybe a learning experience for all

Thank you for your help, and thank you for sticking with me, on this.
I will assume that you will need me to edit the "/etc/apt/sources.list" based on the advice in the link you provided, correct?
If so, then I will carefully do that and post my work.
It will take me some time to read the link contents you sent and look through my existing /etc/apt/sources.list and
then edit it to point to the archives. I'll be back on here after I complete that.
At this point, I'm not so concerned about the wine-compholio pkg, as long as I don't immediately lose the entire WINE capability.
I use a very old Dreamweaver version that will not install unless I have WINE installed.

Thank you very much, again.

shobuz99 (and shobuz992)

---

### Post by Bashing-om on 2013-07-31
shobuz992;
Yeah, make the edits to /etc/apt/sources.list ... and do the update/upgrade routine as per that referenced thread.

Be advised I have no experience per se with "wine" and I may be flying by the seat of our pants to get it back up... 

[INDENT][INDENT]what will be will be
[/INDENT][/INDENT]

bk

as an aside, if it is needed to get your old account back ...make your desires known in the resolution center subforum ... a moderator will attend to your needs ... given time !

---

### Post by Shobuz99 on 2013-08-01
Ok. tried what the link said. I used the command in terminal:

```

sudo sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list

```

Then I ran the next command:

```

sudo apt-get update && sudo apt-get dist-upgrade

```

then I got a ton of errors:

```

rick@rick-desktop:~$ sudo apt-get update && sudo apt-get dist-upgrade
Err http://us.old-releases.ubuntu.com lucid Release.gpg
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Get:1 http://old-releases.ubuntu.com lucid-security Release.gpg [198B]   
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Hit http://ppa.launchpad.net lucid Release.gpg                      
Ign http://ppa.launchpad.net/ehoover/compholio/ubuntu/ lucid/main Translation-en_US
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Get:2 http://old-releases.ubuntu.com lucid-security Release [57.3kB]
Hit http://ppa.launchpad.net lucid Release                                     
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Hit http://ppa.launchpad.net lucid/main Packages                               
Err http://us.old-releases.ubuntu.com lucid-updates Release.gpg                
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-backports Release.gpg
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Get:3 http://old-releases.ubuntu.com lucid-security/main Packages [499kB]
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-proposed Release.gpg            
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://us.old-releases.ubuntu.com lucid Release                        
Ign http://us.old-releases.ubuntu.com lucid-updates Release
Ign http://us.old-releases.ubuntu.com lucid-backports Release
Ign http://us.old-releases.ubuntu.com lucid-proposed Release
Ign http://us.old-releases.ubuntu.com lucid/main Packages
Ign http://us.old-releases.ubuntu.com lucid/restricted Packages
Ign http://us.old-releases.ubuntu.com lucid/universe Packages              
Ign http://us.old-releases.ubuntu.com lucid/multiverse Packages                
Get:4 http://old-releases.ubuntu.com lucid-security/restricted Packages [2,829B]
Ign http://us.old-releases.ubuntu.com lucid-updates/main Packages              
Get:5 http://old-releases.ubuntu.com lucid-security/universe Packages [179kB]  
Ign http://us.old-releases.ubuntu.com lucid-updates/restricted Packages        
Ign http://us.old-releases.ubuntu.com lucid-updates/universe Packages          
Ign http://us.old-releases.ubuntu.com lucid-updates/multiverse Packages
Ign http://us.old-releases.ubuntu.com lucid-backports/main Packages            
Ign http://us.old-releases.ubuntu.com lucid-backports/restricted Packages   
Get:6 http://old-releases.ubuntu.com lucid-security/multiverse Packages [5,373B]
Ign http://us.old-releases.ubuntu.com lucid-backports/universe Packages        
Ign http://us.old-releases.ubuntu.com lucid-backports/multiverse Packages
Ign http://us.old-releases.ubuntu.com lucid-proposed/restricted Packages
Ign http://us.old-releases.ubuntu.com lucid-proposed/main Packages  
Ign http://us.old-releases.ubuntu.com lucid-proposed/multiverse Packages
Ign http://us.old-releases.ubuntu.com lucid-proposed/universe Packages
Ign http://us.old-releases.ubuntu.com lucid/main Packages
Ign http://us.old-releases.ubuntu.com lucid/restricted Packages
Ign http://us.old-releases.ubuntu.com lucid/universe Packages
Ign http://us.old-releases.ubuntu.com lucid/multiverse Packages
Ign http://us.old-releases.ubuntu.com lucid-updates/main Packages
Ign http://us.old-releases.ubuntu.com lucid-updates/restricted Packages
Ign http://us.old-releases.ubuntu.com lucid-updates/universe Packages
Ign http://us.old-releases.ubuntu.com lucid-updates/multiverse Packages
Ign http://us.old-releases.ubuntu.com lucid-backports/main Packages
Ign http://us.old-releases.ubuntu.com lucid-backports/restricted Packages
Ign http://us.old-releases.ubuntu.com lucid-backports/universe Packages
Ign http://us.old-releases.ubuntu.com lucid-backports/multiverse Packages
Ign http://us.old-releases.ubuntu.com lucid-proposed/restricted Packages
Ign http://us.old-releases.ubuntu.com lucid-proposed/main Packages
Ign http://us.old-releases.ubuntu.com lucid-proposed/multiverse Packages
Ign http://us.old-releases.ubuntu.com lucid-proposed/universe Packages
Err http://us.old-releases.ubuntu.com lucid/main Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid/restricted Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid/universe Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid/multiverse Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-updates/main Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-updates/restricted Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-updates/universe Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-updates/multiverse Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-backports/main Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-backports/restricted Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-backports/universe Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-backports/multiverse Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-proposed/restricted Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-proposed/main Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-proposed/multiverse Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-proposed/universe Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Fetched 743kB in 3s (213kB/s)
W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/Release.gpg  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/restricted/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/universe/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/Release.gpg  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/restricted/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/multiverse/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/universe/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/main/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/restricted/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/universe/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/restricted/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/main/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/multiverse/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/universe/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
rick@rick-desktop:~$ 

```

I checked out the link: [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) 
I got a 404 error and it would not connect.
What now?

BTW... I have restored my shobuz99 acct. anyway. I'd be glad to delete the shobuz992 acct. 
          if that's the right thing to do. Let me know. Not a priority right now, though.

Thank you for your continued support.

shobuz99

---

### Post by Bashing-om on 2013-08-01
Shobuz99; Not all bad ...

show me what we are working with, post back the output of terminal codes:
```

cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d/

```
See if I can find where the problem originates; hey, like, if the system can not find it, can not fix it, huh .


Edit: the focus of our attention I expect to be within "/etc/apt/sources.list.d/" directory as "wine" is a 3rd party software. --as advised, flying by the seat of our pants.... expect pucker marks ! 

[INDENT]we be look'n for that light at the end of the tunnel
[/INDENT]

---

### Post by Shobuz99 on 2013-08-01
ok. here's the output for the "cat" command:

```

rick@rick-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.old-releases.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.old-releases.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.old-releases.ubuntu.com/ubuntu/ lucid universe
deb http://us.old-releases.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.old-releases.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.old-releases.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.old-releases.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.old-releases.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://old-releases.ubuntu.com/ubuntu lucid-security main restricted
deb http://old-releases.ubuntu.com/ubuntu lucid-security universe
deb http://old-releases.ubuntu.com/ubuntu lucid-security multiverse
deb http://us.old-releases.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
# deb http://wine.budgetdedicated.com/apt karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" disabled on upgrade to karmic

```

And the output for the "ls" command:

```

rick@rick-desktop:~$ ls -la /etc/apt/sources.list.d/
total 16
drwxr-xr-x 2 root root 4096 2013-06-29 16:26 .
drwxr-xr-x 6 root root 4096 2013-08-01 12:54 ..
-rw-r--r-- 1 root root   65 2013-02-09 15:20 ehoover-compholio-lucid.list
-rw-r--r-- 1 root root  176 2013-02-09 15:20 google-chrome.list.save 
```

uh...that one looks suspicious.. no?

shobuz99

---

### Post by Bashing-om on 2013-08-01
Shobuz99;

Lemme have a bit to look it over.... at first glance I had expected to see an entry for the "wine" ppa in "/etc/apt/sources.list.d/ " directory... not seen yet ... hummm...

[INDENT][INDENT]I be look'n
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-01
ok. BTw the "ehoover-compholio-lucid.list" is WINE-Compholio related, right?

Thanks

shobuz99

---

### Post by Bashing-om on 2013-08-01
Shobuz99; Yikes !

We are going to do this slowly and with great care ... only one thing at a time.... upgrades from version 8.04 ..; "wine" is from version 9.04 ! ...
1st prior to attending to the 3rd party files elsewhere.... let us straighten up the primary file "/etc/apt/sources.list"
To that end:
look at :
[http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) with your browser... this from your current "/etc/apt/sources.list" file....

Gonna hafta do a lot of work to get rid of that old entry, prepare for a new entry.....put on our think'n caps !
at this time ....SAVE ... all you want from what you have in current "wine" ap install ... it is going to be history.

in "/etc/apt/sources.list" is an entry that I think should be enabled:
this one:
> # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
Remove the "#" comment character at the start of the line, and:
make it point to " us.old-releases.ubuntu.com/ubuntu/ lucid".

When you are in agreement, and ready to proceed to next stage... holler at me ... I will be around ...
else others will pick up my slack.

[INDENT][INDENT]ain't nothing but a thing 
[/INDENT][/INDENT]

---

### Post by shobuz992 on 2013-08-01
ok. I found two incidences of that line, in /etc/apt/sources.list:

```

# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

```

Should I replace them both with the "us.old-releases.ubuntu.com/ubuntu/ lucid" link?

Also, I found this on the bottom of the /etc/apt/sources.list file:

```

# deb http://wine.budgetdedicated.com/apt karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" disabled on upgrade to karmic

```

Should I un-comment and replace that with "us.old-releases.ubuntu.com/ubuntu/ lucid"  too???

Let me know...
thank you..
shobuz99

---

### Post by Bashing-om on 2013-08-01
shobuz992; Hey ..

> # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner is of no interest in this case, only if one wants to obtain source code should this type of "get" be enabled.
The:
> wine.budgetdedicated.com/apt karmic main  line I am considering doing away with it entirely, as well as that old PPA, and installing the current PPA ...to update wine. And yes the contents of "/etc/apt/sources.list.d" directory is of relevance,,, and we will look at what is contained directly.


Now consider - I will not be offended, nor my feelings hurt if you seek the opinion/guidance of greater experience; open another thread in the "wine subforum" in this respect.... there likely could be a better alternative than what I have in mind. There exist a lot of experience in that subforum that I am certainly lacking. It would be nice if there were a way to update current wine install without drastic surgery method.

Get their opinion on "wine" and then continue here (????)

[INDENT][INDENT]you'r the man[/INDENT][/INDENT]

---

### Post by shobuz992 on 2013-08-01
Ok. I'm not sure if I care to go to the WINE forum and ask for a "better" solution.
Not that I'm in a hurry; but I guess I'm not sure what questions to ask, so as to get
the best solution to the WINE-Compholio issue.
As I said previously, I do admit that I must upgrade to at least 12.04 for my 64 bit desktop;
however, my immediate concern is to get the other updates, get rid of WINE-Compholio and
keep whatever WINE basics I can so I can continue using my old Dreamweaver web design software.

I know that change is good; however, I'm not financially able to purchase an upgrade to Dreamweaver
that will work in 12.04 and still allow me to do my web design/maintenance work on a daily basis.
I know I sound a bit fearful of that kind of change and that kind of expense.
I guess it's because I'm an old geek that does things as long as they work for me.
FYI....I'm an old IBMer (retired). I'm 63 yrs old and am also an IEEE tech from the 1990's.

Obviously, Ubuntu 10.04 and Dreamweaver MX 2004 will not be able to work for me anymore.
I have to change. I know this. I want to try 12.04 and use it; but I'm unsure of how long
my learning curve/"get used to it" period will be, and what I will replace DWMX 2004 with.

All that being said, my question is this: As long as I don't destroy the WINE itself, during the
process of removing WINE-Compholio then I am ok with what you propose.
Do you think it's possible that WINE would be destroyed during the "surgery"?

Otherwise, I'll proceed to edit the /etc/apt/sources.list as you instructed and wait for your reply.

I appreciate your time and your continued support.

Shobuz99

---

### Post by Bashing-om on 2013-08-01
shobuz992;

I do appreciate the position that you are in .. and require to keep 10.04 as it works with your application within wine.
Now this is the fact of the matter:
The wine PPA to fix that current wine install no longer exist and some one with the knowledge of wine can certainly fix your wine using what is provided in the wine archive... but that ain't me, as I have zero zilch experience with wine.... and if we do take my drastic solution ... that will work to get wine up and running ... there is no doubt in my mind that the current wine install and all that it contains is gone.

Tell ya what ... lemme go to the wine subforum ... see who all frequents it .. and see if maybe one of my comrades-in-arms frequent there and get em to meet us here on this thread for advisement on any other alternative (???)

[INDENT][INDENT]it is broke, and we gotta fix it[/INDENT][/INDENT]

---

### Post by shobuz992 on 2013-08-01
Ok. I really appreciate the extra effort on your part.
Just so we're on the same page, Dreamweaver and WINE are still working fine, on my 64 bit desktop. 

My problem is that WINE-Compholio just won't update, and I can't uninstall it.
I recall installing it so that I could "stream" Netflix...which failed and then I never uninstalled WINE-Compholio afterward.
I truly regret that dumbass procrastination now, because it stung me. :-(

Anyway, I will hang loose and see if any WINE experts will come to my aid and your consultation.

Once again, thank you so much for all you are doing. I sincerely appreciate it :-)

Shobuz99

---

### Post by Bashing-om on 2013-08-01
shobuz992; Hey,
No big deal, glad to do what I can .. 
I have asked for aid in this situation ... will see what is advised...

I do have a workable plan that we can discuss at a later time ...how 'bout installing lubuntu as a dual boot,
install the latest version of wine on lubuntu ; and copy across from 10.04 install all that you want from the 10.04 wine straight across and see if wine and your Windows' aps work in the new environment ? Again I have not done this, I have no idea what directories would require copying... not to even think about the libraries; ... but all that is lost in trying is a bit of time and effort.

My wife was most adamant that she was not going to give up her ubuntu 10.04 ... she is now a happy camper with Lubuntu 13.04. The adjustment to Lubuntu is quite easy.

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by shobuz992 on 2013-08-02
Lol. Your wife has a good husband; especially if you convinced her to go to 13.04. :-)

The dual boot idea would be good if I had a single drive situation...but I don't.
I am already dual-booting with another drive that happens to be a Windows XP drive.
I don't use it to boot from anymore, because there is something wrong with the system32 folder
and it won't boot to Windows XP, from Grub. 
However, I can still access data files from that drive, that have several iterations of web design clients files. 
I am a poor housekeeper and haven't sat down and transferred those files
to another drive so I can use it for something else. 
It's only 20GB anyway, so it isn't worth dealing with as a drive to function with any distro. 

I appreciate the idea to use lunbuntu. Maybe that is the solution for me after we attempt to fix 10.04.
Once that''s done, moving over to lubuntu 13.04 might be the right move for me.
Additionally, my current Ubuntu drive is 80GB and is almost full. 
So in order to install a clean version of Ubuntu 13.04 on that drive, I will need to backup all the data files (excluding libs that work only on 10.04)
on the existing Ubuntu drive. So basically I'm dual-booting from 2 separate HDDs. 
I was using EXT 3 on the Windows drive and the boot grub was setup to swap sda1 with sdb1... I think...it's been a while. :-)

Again, I appreciate your suggestions and will definitely consider lubuntu 13.04 as the ultimate solution.
Thank you, my friend, for all you do and are doing.

Shobuz99

---

### Post by Bashing-om on 2013-08-02
shobuz992;

Hey ... it is like unto this, I am a firm advocate of open source in general, ubuntu in particular... whatever I can do to promote either and/or both ... is what needs to be done... so I am working to get you happy !

To the situation at hand ... I presently do not have a solution that I am comfortable with... that insures you do not loose programs and your data. This is a real challenge ... and I have asked for help ... and we will get help ... just takes a bit to find those who have the knowledge. Those who do have the skill set are out of my field of interest. After Given a reasonable amount of time I will resort to inquiring of a forum moderator (right now they have their hands full) for advise on who to contact.

[INDENT][INDENT]patience is a virtue
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-02
> **Bashing-om said:**
> shobuz992;

Hey ... it is like unto this, I am a firm advocate of open source in general, ubuntu in particular... whatever I can do to promote either and/or both ... is what needs to be done... so I am working to get you happy !

To the situation at hand ... I presently do not have a solution that I am comfortable with... that insures you do not loose programs and your data. This is a real challenge ... and I have asked for help ... and we will get help ... just takes a bit to find those who have the knowledge. Those who do have the skill set are out of my field of interest. After Given a reasonable amount of time I will resort to inquiring of a forum moderator (right now they have their hands full) for advise on who to contact.

[INDENT][INDENT]patience is a virtue
[/INDENT][/INDENT]

Thank you for that. I am very patient, because I know you are sincere about helping me fix this.
In the meantime, I will do some of my own thinking about how I can backup data files from both drives
and then use the 20GB drive for simple storage of data files.
I have available several "spare" HDD's to choose from; but none are larger than 40GB.
They are all IDE drives. I have one SATA 160GB drive that I am using for a "music" only external USB storage drive.
My Desktop is IDE with SATA capability; but I have never enabled that capability to use with a SATA drive.

As you can see I'm thinking about a lot of options to my current situation.
But my focus is what I came to you for in the first place.

I'm hangin' in, my friend. :-)

Shobuz99

---

### Post by Bashing-om on 2013-08-05
Shobuz99; Morning,

I have made the inquiries; no one has the experience of updating in this situation and do not know what might happen.
I am as prepared to proceed as I am ever going to be ... with some trepidation. 
So:
We are going to remove/purge Netfilx to start with ... that in of it's self I do not expect any problems, but I do anticipate that there may be some breakage in wine with any co-dependencies that are removed when Netfix is removed. That in and of it's self is no big deal ... as we are going to update Wine... now comes the rub ! What breakage is going to occur with the Window's applications within Wine ? Do not know ...and none have advised, I do not have the resources to fix any Window's applications if the chain of dependencies is broken and not re-established when Wine is updated.

To this time we have done nothing that prevents reverting your system back to where we started. The next step when done, no going back.
show me the contents:
```

cat /etc/apt/sources.list.d/ehoover-compholio-lucid.list

```
Which I expect is the source for Netflix. 
The terminal command to purge Netflix then is forthcoming. -> then test Wine prior to proceeding to update it.
At that point your system may be in good enough state to suite your needs ... 
We can try at that time to update/upgrade ... and see what MUST then be done. -> small steps, see what happens.

[INDENT][INDENT]all we can do is try
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-06
Ok. Here's the results of the command you asked me to run:

```

rick@rick-desktop:~$ cat /etc/apt/sources.list.d/ehoover-compholio-lucid.list
deb http://ppa.launchpad.net/ehoover/compholio/ubuntu lucid main
rick@rick-desktop:~$ 

```

Thanks

Shobuz99

---

### Post by Bashing-om on 2013-08-06
Shobuz99; Hey ....

Looks right ... fingers crossed, let's to this.
This Terminal Command:
```
sudo apt-get update && sudo apt-get install ppa-purge && sudo ppa-purge ppa:ehoover/compholio
```
- copy and paste to preclude transition errors -
Will remove Netflix, and all it's config files.

I do not expect at this point for "sudo apt-get update" to respond with any errors ... but if so, we stop and deal with the errors before proceeding.
When the "ppa-purge" completes -> reboot, and play with Wine, hopefully all is OK at this point ...
Consider now if we want to attempt to update Wine (????).

Small steps, but getting somewhere.

---

### Post by Shobuz99 on 2013-08-06
Ok. Not good news:

```

rick@rick-desktop:~$ sudo apt-get update && sudo apt-get install ppa-purge && sudo ppa-purge ppa:ehoover/compholio
[sudo] password for rick: 
Err http://us.old-releases.ubuntu.com lucid Release.gpg
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/ehoover/compholio/ubuntu/ lucid/main Translation-en_US
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Hit http://old-releases.ubuntu.com lucid-security Release.gpg                  
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Hit http://ppa.launchpad.net lucid Release                          
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Hit http://old-releases.ubuntu.com lucid-security Release                      
Err http://us.old-releases.ubuntu.com lucid-updates Release.gpg                
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Hit http://ppa.launchpad.net lucid/main Packages                               
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Hit http://old-releases.ubuntu.com lucid-security/main Packages     
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Packages 
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-backports Release.gpg
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-proposed Release.gpg
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://us.old-releases.ubuntu.com lucid Release
Ign http://us.old-releases.ubuntu.com lucid-updates Release
Ign http://us.old-releases.ubuntu.com lucid-backports Release
Ign http://us.old-releases.ubuntu.com lucid-proposed Release
Ign http://us.old-releases.ubuntu.com lucid/main Packages
Ign http://us.old-releases.ubuntu.com lucid/restricted Packages
Ign http://us.old-releases.ubuntu.com lucid/universe Packages
Ign http://us.old-releases.ubuntu.com lucid/multiverse Packages
Ign http://us.old-releases.ubuntu.com lucid-updates/main Packages
Ign http://us.old-releases.ubuntu.com lucid-updates/restricted Packages
Ign http://us.old-releases.ubuntu.com lucid-updates/universe Packages
Ign http://us.old-releases.ubuntu.com lucid-updates/multiverse Packages
Ign http://us.old-releases.ubuntu.com lucid-backports/main Packages
Ign http://us.old-releases.ubuntu.com lucid-backports/restricted Packages
Ign http://us.old-releases.ubuntu.com lucid-backports/universe Packages
Ign http://us.old-releases.ubuntu.com lucid-backports/multiverse Packages
Ign http://us.old-releases.ubuntu.com lucid-proposed/restricted Packages
Ign http://us.old-releases.ubuntu.com lucid-proposed/main Packages
Ign http://us.old-releases.ubuntu.com lucid-proposed/multiverse Packages
Ign http://us.old-releases.ubuntu.com lucid-proposed/universe Packages
Ign http://us.old-releases.ubuntu.com lucid/main Packages
Ign http://us.old-releases.ubuntu.com lucid/restricted Packages
Ign http://us.old-releases.ubuntu.com lucid/universe Packages
Ign http://us.old-releases.ubuntu.com lucid/multiverse Packages
Ign http://us.old-releases.ubuntu.com lucid-updates/main Packages
Ign http://us.old-releases.ubuntu.com lucid-updates/restricted Packages
Ign http://us.old-releases.ubuntu.com lucid-updates/universe Packages
Ign http://us.old-releases.ubuntu.com lucid-updates/multiverse Packages
Ign http://us.old-releases.ubuntu.com lucid-backports/main Packages
Ign http://us.old-releases.ubuntu.com lucid-backports/restricted Packages
Ign http://us.old-releases.ubuntu.com lucid-backports/universe Packages
Ign http://us.old-releases.ubuntu.com lucid-backports/multiverse Packages
Ign http://us.old-releases.ubuntu.com lucid-proposed/restricted Packages
Ign http://us.old-releases.ubuntu.com lucid-proposed/main Packages
Ign http://us.old-releases.ubuntu.com lucid-proposed/multiverse Packages
Ign http://us.old-releases.ubuntu.com lucid-proposed/universe Packages
Err http://us.old-releases.ubuntu.com lucid/main Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid/restricted Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid/universe Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid/multiverse Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-updates/main Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-updates/restricted Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-updates/universe Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-updates/multiverse Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-backports/main Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-backports/restricted Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-backports/universe Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-backports/multiverse Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-proposed/restricted Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-proposed/main Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-proposed/multiverse Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.old-releases.ubuntu.com lucid-proposed/universe Packages
  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/Release.gpg  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/restricted/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/universe/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/Release.gpg  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/restricted/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/multiverse/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/universe/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/main/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/restricted/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/universe/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/restricted/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/main/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/multiverse/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-proposed/universe/binary-amd64/Packages.gz  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
rick@rick-desktop:~$ 

```

It doesn't appear to correct anything. What now?

Shobuz99

---

### Post by Bashing-om on 2013-08-06
Shobuz99;

Lemme have a bit to review /etc/apt/souces.list. See what problems now exist...
Back in a bit.

[INDENT][INDENT]trials troubles and tribulations[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-08-06
Shobuz99; Ok !

I am much wiser now...
Apparently "us.old-releases.ubuntu.com" url is invalid... Hey I tested ... not valid ! Hummm...
What I find to be valid:
> 
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid main

So... I suggest making the edits the slow tedious way - that way we know what we are looking at and doing.
fire up gedit in superuser mode:
--If you have not backed up that original sources.list file .. would not hurt to do so now in the least... never can tell what might perchance.--
```

gksudo gedit /etc/apt/sources.list

```
and remove "us." from each and every line it appears in;
save the file, exiting back to the terminal;
in terminal do:
```

sudo apt-get update

```
Let's see that goes well before proceeding with the purge application.
Now I intend to use a different tool to update the installed packages ... want to know if "aptitude" is installed on your system (no longer installed by default in later systems) do:
```

dpkg -l aptitude

```

[INDENT][INDENT]a small step, in the right direction
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-07
Alright! here's the results, and they look good:

```

rick@rick-desktop:~$ gksudo gedit /etc/apt/sources.list
rick@rick-desktop:~$ sudo apt-get update
Get:1 http://old-releases.ubuntu.com lucid Release.gpg [189B]
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/ehoover/compholio/ubuntu/ lucid/main Translation-en_US
Get:2 http://old-releases.ubuntu.com lucid-updates Release.gpg [198B]
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Get:3 http://old-releases.ubuntu.com lucid-backports Release.gpg [198B]
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Hit http://ppa.launchpad.net lucid Release
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:4 http://old-releases.ubuntu.com lucid-proposed Release.gpg [198B]
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
Hit http://ppa.launchpad.net lucid/main Packages
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Get:5 http://old-releases.ubuntu.com lucid Release [57.2kB]
Get:6 http://old-releases.ubuntu.com lucid-updates Release [58.3kB]
Get:7 http://old-releases.ubuntu.com lucid-backports Release [57.3kB]
Hit http://old-releases.ubuntu.com lucid-security Release
Get:8 http://old-releases.ubuntu.com lucid-proposed Release [58.3kB]
Get:9 http://old-releases.ubuntu.com lucid/main Packages [1,383kB]
Get:10 http://old-releases.ubuntu.com lucid/restricted Packages [6,193B]
Get:11 http://old-releases.ubuntu.com lucid/universe Packages [5,430kB]
Get:12 http://old-releases.ubuntu.com lucid/multiverse Packages [176kB]
Get:13 http://old-releases.ubuntu.com lucid-updates/main Packages [694kB]
Get:14 http://old-releases.ubuntu.com lucid-updates/restricted Packages [4,624B]
Get:15 http://old-releases.ubuntu.com lucid-updates/universe Packages [329kB]
Get:16 http://old-releases.ubuntu.com lucid-updates/multiverse Packages [11.5kB]
Get:17 http://old-releases.ubuntu.com lucid-backports/main Packages [16.6kB]
Get:18 http://old-releases.ubuntu.com lucid-backports/restricted Packages [14B]
Get:19 http://old-releases.ubuntu.com lucid-backports/universe Packages [55.7kB]
Get:20 http://old-releases.ubuntu.com lucid-backports/multiverse Packages [1,378B]
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Packages
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Get:21 http://old-releases.ubuntu.com lucid-proposed/restricted Packages [14B]
Get:22 http://old-releases.ubuntu.com lucid-proposed/main Packages [131kB]
Get:23 http://old-releases.ubuntu.com lucid-proposed/multiverse Packages [14B]
Get:24 http://old-releases.ubuntu.com lucid-proposed/universe Packages [18.8kB]
Fetched 8,489kB in 8s (1,019kB/s)                                              
Reading package lists... Done
W: Duplicate sources.list entry http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_lucid_multiverse_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
rick@rick-desktop:~$  
```

Should I run apt-get update to correct the "W: Duplicate sources.list entry http://old-releases.ubuntu.com/ubuntu/..." problem?

Here's the results for dpkg:

```

rick@rick-desktop:~$ dpkg -l aptitude
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  aptitude       0.4.11.11-1ubu terminal-based package manager
rick@rick-desktop:~$ 

```

Thank you. So far so good.
Shobuz99

---

### Post by Bashing-om on 2013-08-07
Shobuz99;

Yeah, looks much better ..making progress -- bit at a time ... but progress !........
Ok .. let me have abit to see where that duplication occurs ... fix that and then do the next step ... as "aptitude" is available ... in this situation ... I prefer to use it's abilities.

[INDENT][INDENT]be back soonest
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-08-07
Shobuz99;

I am back .. I see nothing amiss in the "sources.list" file from your post #11 ... before doing surgery lets look at the current file.
show me the output of:
```

cat /etc/apt/sources.list

```

[INDENT]still clearing the deck for action
[/INDENT]

---

### Post by Shobuz99 on 2013-08-07
Ok. here's results:

```

rick@rick-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://old-releases.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://old-releases.ubuntu.com/ubuntu/ lucid universe
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://old-releases.ubuntu.com/ubuntu/ lucid multiverse
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://old-releases.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://old-releases.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://old-releases.ubuntu.com/ubuntu/ lucid multiverse


deb http://old-releases.ubuntu.com/ubuntu lucid-security main restricted
deb http://old-releases.ubuntu.com/ubuntu lucid-security universe
deb http://old-releases.ubuntu.com/ubuntu lucid-security multiverse
deb http://old-releases.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
# deb http://wine.budgetdedicated.com/apt karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" disabled on upgrade to karmic

```

back to the upper deck.. :-)

Shobuz99

---

### Post by Bashing-om on 2013-08-07
Shobuz99; Got it !
Surgery avoided for now.

> 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid multiverse

remove that last line "deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid multiverse" as it is duplicated - another same line in the file.
ok ... do once more:
```

sudo apt-get update

``` all will run good now ...
then: fingers crossed, hold your breath .. lets see what happens to wine !
```

sudo aptitude update
sudo apt-get install ppa-purge
sudo ppa-purge ppa:ehoover/compholio
sudo aptitude safe-upgrade

```
Netflix should be gone and "safe-upgrade" updating only what it can of currently installed packages.

Play with Wine now and let's see where we stand.

[INDENT][INDENT][INDENT]firing for effect ?
[/INDENT][/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-07
Ok. first this step results:

```

rick@rick-desktop:~$ gksudo gedit /etc/apt/sources.list
rick@rick-desktop:~$ sudo apt-get update
Hit http://old-releases.ubuntu.com lucid Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-updates Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/ehoover/compholio/ubuntu/ lucid/main Translation-en_US
Hit http://old-releases.ubuntu.com lucid-backports Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-proposed Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Hit http://old-releases.ubuntu.com lucid Release
Hit http://old-releases.ubuntu.com lucid-updates Release
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://old-releases.ubuntu.com lucid-backports Release
Hit http://old-releases.ubuntu.com lucid-security Release
Hit http://old-releases.ubuntu.com lucid-proposed Release
Hit http://old-releases.ubuntu.com lucid/main Packages
Hit http://old-releases.ubuntu.com lucid/restricted Packages
Hit http://old-releases.ubuntu.com lucid/universe Packages
Hit http://old-releases.ubuntu.com lucid/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-updates/main Packages
Hit http://old-releases.ubuntu.com lucid-updates/restricted Packages
Hit http://old-releases.ubuntu.com lucid-updates/universe Packages
Hit http://old-releases.ubuntu.com lucid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-backports/main Packages
Hit http://old-releases.ubuntu.com lucid-backports/restricted Packages
Hit http://old-releases.ubuntu.com lucid-backports/universe Packages
Hit http://old-releases.ubuntu.com lucid-backports/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Packages
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/restricted Packages
Hit http://old-releases.ubuntu.com lucid-proposed/main Packages
Hit http://old-releases.ubuntu.com lucid-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/universe Packages
Reading package lists... Done
rick@rick-desktop:~$ 

```

looks good!!

now this step: sudo aptitude update

```

rick@rick-desktop:~$ sudo aptitude update
Writing extended state information... Done
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/ehoover/compholio/ubuntu/ lucid/main Translation-en_US
Hit http://old-releases.ubuntu.com lucid Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-updates Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://ppa.launchpad.net lucid Release     
Hit http://old-releases.ubuntu.com lucid-backports Release.gpg
Hit http://ppa.launchpad.net lucid/main Packages                               
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-proposed Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Hit http://old-releases.ubuntu.com lucid Release
Hit http://old-releases.ubuntu.com lucid-updates Release
Hit http://old-releases.ubuntu.com lucid-backports Release
Hit http://old-releases.ubuntu.com lucid-security Release
Hit http://old-releases.ubuntu.com lucid-proposed Release
Hit http://old-releases.ubuntu.com lucid/main Packages
Hit http://old-releases.ubuntu.com lucid/restricted Packages
Hit http://old-releases.ubuntu.com lucid/universe Packages
Hit http://old-releases.ubuntu.com lucid/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-updates/main Packages
Hit http://old-releases.ubuntu.com lucid-updates/restricted Packages
Hit http://old-releases.ubuntu.com lucid-updates/universe Packages
Hit http://old-releases.ubuntu.com lucid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-backports/main Packages
Hit http://old-releases.ubuntu.com lucid-backports/restricted Packages
Hit http://old-releases.ubuntu.com lucid-backports/universe Packages
Hit http://old-releases.ubuntu.com lucid-backports/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Packages
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/restricted Packages
Hit http://old-releases.ubuntu.com lucid-proposed/main Packages
Hit http://old-releases.ubuntu.com lucid-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/universe Packages
Reading package lists... Done             

rick@rick-desktop:~$ 

```

ok.

Next step: sudo apt-get install ppa-purge

```

rick@rick-desktop:~$ sudo apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libopal3.6.6 libxml++2.6-2 python-twisted-mail ubufox
  python-twisted-lore python-twisted-news libfile-find-rule-perl
  python-twisted-conch python-twisted-words libslv2-9 python-twisted rtkit
  libffado2 libtext-glob-perl libgnomecanvasmm-2.6-1c2a libpt2.6.5 liblo7
  libaubio2 python-twisted-runner liblrdf0 python-pyasn1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine-compholio
Recommended packages:
  libjpeg8 libssl1.0.0
The following NEW packages will be installed:
  ppa-purge
The following packages will be upgraded:
  wine-compholio
1 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 4,632B/15.7MB of archives.
After this operation, 2,122kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe ppa-purge 0+bzr46.1~lucid1 [4,632B]
Fetched 4,632B in 0s (19.1kB/s)    
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wine-compholio' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre-headless' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
rick@rick-desktop:~$ 
```

oh oh...something went wrong here... looks like square one!! Yikes! I will not continue. What happened?

shobuz99

---

### Post by Bashing-om on 2013-08-07
Shobuz99; Well, not all bad ..
Needless to say .. I am surprised at what has taken place .. 
Let's remove the "list" database -> repopulate the database, look at what is ... and do it again.
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
dpkg -l ppa-purge

``` show me the output of "dpkg -l ppa-purge" ...and we will take off again.

[INDENT][INDENT]was that last a misfire or a dud

[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-08
Hmmmm... interesting...results of all 4 commands:

```

rick@rick-desktop:~$ sudo rm -fr /var/lib/apt/lists
[sudo] password for rick: 
rick@rick-desktop:~$ sudo mkdir -pv /var/lib/apt/lists/partial
mkdir: created directory `/var/lib/apt/lists'
mkdir: created directory `/var/lib/apt/lists/partial'
rick@rick-desktop:~$ sudo apt-get update
Get:1 http://old-releases.ubuntu.com lucid Release.gpg [189B]
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:2 http://old-releases.ubuntu.com lucid-updates Release.gpg [198B]
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Get:3 http://ppa.launchpad.net lucid Release.gpg [316B]
Ign http://ppa.launchpad.net/ehoover/compholio/ubuntu/ lucid/main Translation-en_US
Get:4 http://old-releases.ubuntu.com lucid-backports Release.gpg [198B]
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Get:5 http://old-releases.ubuntu.com lucid-security Release.gpg [198B]
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Get:6 http://ppa.launchpad.net lucid Release [13.9kB]
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:7 http://old-releases.ubuntu.com lucid-proposed Release.gpg [198B]
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Get:8 http://old-releases.ubuntu.com lucid Release [57.2kB]
Get:9 http://ppa.launchpad.net lucid/main Packages [4,327B]
Get:10 http://old-releases.ubuntu.com lucid-updates Release [58.3kB]
Get:11 http://old-releases.ubuntu.com lucid-backports Release [57.3kB]
Get:12 http://old-releases.ubuntu.com lucid-security Release [57.3kB]
Get:13 http://old-releases.ubuntu.com lucid-proposed Release [58.3kB]
Get:14 http://old-releases.ubuntu.com lucid/main Packages [1,383kB]
Get:15 http://old-releases.ubuntu.com lucid/restricted Packages [6,193B]
Get:16 http://old-releases.ubuntu.com lucid/universe Packages [5,430kB]
Get:17 http://old-releases.ubuntu.com lucid/multiverse Packages [176kB]
Get:18 http://old-releases.ubuntu.com lucid-updates/main Packages [694kB]
Get:19 http://old-releases.ubuntu.com lucid-updates/restricted Packages [4,624B]
Get:20 http://old-releases.ubuntu.com lucid-updates/universe Packages [329kB]
Get:21 http://old-releases.ubuntu.com lucid-updates/multiverse Packages [11.5kB]
Get:22 http://old-releases.ubuntu.com lucid-backports/main Packages [16.6kB]
Get:23 http://old-releases.ubuntu.com lucid-backports/restricted Packages [14B]
Get:24 http://old-releases.ubuntu.com lucid-backports/universe Packages [55.7kB]
Get:25 http://old-releases.ubuntu.com lucid-backports/multiverse Packages [1,378B]
Get:26 http://old-releases.ubuntu.com lucid-security/main Packages [499kB]
Get:27 http://old-releases.ubuntu.com lucid-security/restricted Packages [2,829B]
Get:28 http://old-releases.ubuntu.com lucid-security/universe Packages [179kB]
Get:29 http://old-releases.ubuntu.com lucid-security/multiverse Packages [5,373B]
Get:30 http://old-releases.ubuntu.com lucid-proposed/restricted Packages [14B]
Get:31 http://old-releases.ubuntu.com lucid-proposed/main Packages [131kB]
Get:32 http://old-releases.ubuntu.com lucid-proposed/multiverse Packages [14B]
Get:33 http://old-releases.ubuntu.com lucid-proposed/universe Packages [18.8kB]
Fetched 9,251kB in 7s (1,254kB/s)                                              
Reading package lists... Done
rick@rick-desktop:~$ dpkg -l ppa-purge
No packages found matching ppa-purge.
rick@rick-desktop:~$ 

```

Does it mean it was a "misfire" like you said?

I'm a bit lost here. If you don't mind, could you tell me the basics
of what happened and why these new results seem to be corrected?
I'm just curious about the logic and how it works, basically.

By all means let's carry on, too

shobuz99

---

### Post by Bashing-om on 2013-08-08
Shobuz99;
So far look'n good ... did not really expect that the ppa-purge application had been installed ... just checking... as to what is going on with removing the data base ...well that is indeed a complex subject ..in that package management is an involved operations. Several data bases are maintained by the system.. "dpkg"  being the base - backend - for several up front applications .. as in apt or apt-get. What we did here was remove one of those control data bases -that had become corrupted at some point in the past -  and "apt-get update" rebuilds it in accordance with the present installation state of all packages ( as you are presently aware, there are other controls in place). It is, in my case, sometimes a trial to determine what database of files is in control in a particular process. 
I dislike slowing things down at this point .. but I think we should take a look at what "dpkg" thinks of the state of the packages on the system at this time. Then install "ppa-purge" and carry forth.

```

dpkg -C

```
Yeah, we will call that a misfire ... check the firing pin, getting ready to pull the hammer back once more !

[INDENT][INDENT]range and elevation is set
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-08
ok. Only one issue that dpkg - C didn't like:

```

rick@rick-desktop:~$ dpkg -C
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 wine-compholio       The Compholio Edition is a special build of the popular W

rick@rick-desktop:~$ 

```

Ok. That appears to be the issue to fix. thanks for the explanation.
Let's carry on, shall we?

Shobuz99

---

### Post by Bashing-om on 2013-08-08
Shobuz99; look'n much better than what I was expecting...
next: try again ->
```

sudo apt-get install ppa-purge

```
and IF that goes well ....
```

sudo ppa-purge ppa:ehoover/compholio

```
and see where we stand ...

Gonna go do yard work ... be a bit before I get back to the keyboard.

[INDENT][INDENT]half cocked and raring to go
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-08
Nope:
```

rick@rick-desktop:~$ sudo apt-get install ppa-purge
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libopal3.6.6 libxml++2.6-2 python-twisted-mail ubufox
  python-twisted-lore python-twisted-news libfile-find-rule-perl
  python-twisted-conch python-twisted-words libslv2-9 python-twisted rtkit
  libffado2 libtext-glob-perl libgnomecanvasmm-2.6-1c2a libpt2.6.5 liblo7
  libaubio2 python-twisted-runner liblrdf0 python-pyasn1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine-compholio
Recommended packages:
  libjpeg8 libssl1.0.0
The following NEW packages will be installed:
  ppa-purge
The following packages will be upgraded:
  wine-compholio
1 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/15.7MB of archives.
After this operation, 2,122kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wine-compholio' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre-headless' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
rick@rick-desktop:~$ 

```

I think some specific surgery must be in order, no?

Shobuz99

---

### Post by Bashing-om on 2013-08-08
Shobuz99; well ,, well 

Not real sure what is going on ... what results from:
```

sudo apt-get install --reinstall openjdk-6-jre-headless
sudo apt-get install --reinstall icedtea-6-jre-cacao

```
a quick look at the others .. maybe if "-headless" and "-cacao" are installed the others will fall into line (  apt-cache show openjdk-6-jre-cacao ) seems to indicate so.

If this is surgery it is minor ...

[INDENT][INDENT]try'n to charge the chamber
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-09
It seems to not matter if those are installed or not...
I tried both, one after the other and the same error message occurs:

```

rick@rick-desktop:~$ sudo apt-get install --reinstall openjdk-6-jre-headless
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libopal3.6.6 libxml++2.6-2 python-twisted-mail ubufox
  python-twisted-lore python-twisted-news libfile-find-rule-perl
  python-twisted-conch python-twisted-words libslv2-9 python-twisted rtkit
  libffado2 libtext-glob-perl libgnomecanvasmm-2.6-1c2a libpt2.6.5 liblo7
  libaubio2 python-twisted-runner liblrdf0 python-pyasn1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine-compholio
Recommended packages:
  libjpeg8 libssl1.0.0
The following packages will be upgraded:
  wine-compholio
1 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 25.5MB/41.1MB of archives.
After this operation, 2,064kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main openjdk-6-jre-headless 6b27-1.12.5-0ubuntu0.10.04.1 [25.5MB]
Fetched 25.5MB in 16s (1,517kB/s)                                              
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wine-compholio' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre-headless' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
rick@rick-desktop:~$ sudo apt-get install --reinstall icedtea-6-jre-cacao
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libopal3.6.6 libxml++2.6-2 python-twisted-mail ubufox
  python-twisted-lore python-twisted-news libfile-find-rule-perl
  python-twisted-conch python-twisted-words libslv2-9 python-twisted rtkit
  libffado2 libtext-glob-perl libgnomecanvasmm-2.6-1c2a libpt2.6.5 liblo7
  libaubio2 python-twisted-runner liblrdf0 python-pyasn1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine-compholio
Recommended packages:
  libjpeg8 libssl1.0.0
The following packages will be upgraded:
  wine-compholio
1 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 812kB/16.5MB of archives.
After this operation, 2,064kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main icedtea-6-jre-cacao 6b27-1.12.5-0ubuntu0.10.04.1 [812kB]
Fetched 812kB in 1s (528kB/s)              
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wine-compholio' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre-headless' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
rick@rick-desktop:~$ 

```

Should I be using 'apt-get autoremove' to remove the packages,
that were automatically installed and are no longer required, as listed above??

Otherwise, I'm baffled. :-(

Shobuz99

---

### Post by Bashing-om on 2013-08-09
Shobuz99; Deeper and deeper... Well, as:
It seems that some of the files in the directory /var/lib/dpkg/info got lost.
Among others that directory contains *.list files with a per-package information of the files that belong to that package. If these files are missing dpkg (called by apt-get or aptitude) complains about that when installing or upgrading packages.
Let's try this: and yeah .. be a good thing to rid our self  of the overhead of those obsolete files.
```

sudo apt-get clean
sudo apt-get autoremove
sudo dpkg --clear-avail
sudo apt-get update
sudo apt-get upgrade

```

see where this gets us.

---

### Post by Shobuz99 on 2013-08-09
I just don't get it. We seem to be "looping" back to the same result.
Even running autoremove shows that 22 pkgs were removed, including wine-compholio.
Then it ends up back where we started...

```

rick@rick-desktop:~$ sudo apt-get clean
[sudo] password for rick: 
rick@rick-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  wine-compholio
Recommended packages:
  libjpeg8 libssl1.0.0
The following packages will be REMOVED:
  libaubio2 libffado2 libfile-find-rule-perl libgnomecanvasmm-2.6-1c2a liblo7
  liblrdf0 libnumber-compare-perl libopal3.6.6 libpt2.6.5 libslv2-9
  libtext-glob-perl libxml++2.6-2 python-pyasn1 python-twisted
  python-twisted-conch python-twisted-lore python-twisted-mail
  python-twisted-news python-twisted-runner python-twisted-words rtkit ubufox
The following packages will be upgraded:
  wine-compholio
1 upgraded, 0 newly installed, 22 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 15.7MB of archives.
After this operation, 24.8MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/ehoover/compholio/ubuntu/ lucid/main wine-compholio 1.6~lucid [15.7MB]
Fetched 15.7MB in 15s (991kB/s)                                                
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wine-compholio' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre-headless' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
rick@rick-desktop:~$ 

```

back to you...

Shobuz99

---

### Post by Bashing-om on 2013-08-09
Shobuz99; Yuk .. Going round and round .. trying not to mess with the ppa .. that might be obsolete and give us more problems than we have now ...
I am aware of a method to remove a ppa manually ...but that too has risks. I do not want to risk getting into a situation we can not back out of....

It may come down to having to install Netflix fully functional - if we can at all - in order to remove it !

Still attacking this directly head on; try:
```

sudo dpkg -i /var/cache/apt/archives/openjdk-6-jre-lib

```
See if that gives us any satisfaction.

[INDENT][INDENT]a piece here and a piece there
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-09
```

rick@rick-desktop:~$ sudo dpkg -i /var/cache/apt/archives/openjdk-6-jre-lib
[sudo] password for rick: 
dpkg: error processing /var/cache/apt/archives/openjdk-6-jre-lib (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-6-jre-lib
rick@rick-desktop:~$ 

```

Hmmm... this means what?

BTW.... I appreciate your diligence and persistence to solve this. I really do.
This is an enigma, wrapped in a dilemma and covered in a riddle!

Shobuz99

---

### Post by Bashing-om on 2013-08-09
Shobuz99; 'Tis a puzzle indeed ..
Making me think and putting a smile on my face, and a pain in my heart. 
That last output makes no sense to me at all .. that directory contains info on every file installed on the system ,,, what in the world is not going on ?
I am getting heartburn, trying to understand this !
example: my tiny system:
> 
sysop@1304mini:~$ ls -la /var/cache/apt/archives/
total 502836

what results do you get from:
```

ls -la /var/cache/apt/archives/ ## a huge file, do not need to see it, just to know that the directory does exist.
ls -la /var/cache/apt/archives/openjdk-* ## this output I do want to see.

```
If these returns are favorable .. will see what apt-get has to say about installing that one library ...

Looking about .. and the Netflix PPA looks to me to still be valid .. hummm ... we might though still go ahead and disable it and see what results from trying to install "ppa-purge" (????)

[INDENT][INDENT][INDENT]it is a computer, they are reasonable people
[/INDENT][/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-10
Surprise... not a big file..
```

rick@rick-desktop:~$ ls -la /var/cache/apt/archives
total 15576
drwxr-xr-x 3 root root   233472 2013-08-09 15:40 .
drwxr-xr-x 3 root root     4096 2013-08-07 11:13 ..
-rw-r----- 1 root root        0 2008-11-16 23:33 lock
drwxr-xr-x 2 root root     4096 2013-08-09 15:40 partial
-rw-r--r-- 1 root root 15680868 2013-07-22 14:30 wine-compholio_1.6~lucid_amd64.deb

```

and here's Johnny! Not...
```

rick@rick-desktop:~$ ls -la /var/cache/apt/archives/openjdk-*
ls: cannot access /var/cache/apt/archives/openjdk-*: No such file or directory
rick@rick-desktop:~$ 

```
I am perplexed now.... ??????

shobuz99

---

### Post by Bashing-om on 2013-08-10
Shobuz99; Yeah .. that totally blows me away ... gonna have to scratch my head .. and tinker about .. see what it is going to take to (re)build that database.


Edit: Ok My think'n was corrupted ! ..."apt-get clean" clears out that database as it is supposed to.
Back to the drawing board, why can not we install those libraries ...Why is the package manager hollering about (????)
> 
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-6-jre-lib


You must have gotten up real early to eat your Wheaties and take a look at this slopyation. Still not beyond hope, the more we mess with it, actually, the more doable it appears.

[INDENT][INDENT]once more:
[INDENT][INDENT][INDENT][INDENT]sometimes I wonder, other times I do not know[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-08-10
Shobuz99;

Going round and around .. looking at one small piece of the puzzle, trying to fit it into the whole.
Let's get a fresh look at it.
How bout this approach;
In the Software Center -> other software; disable the "wine-compholio" ppa and,
in terminal see what the package manager has to say now about "openjdk-6-jre-lib".
```

sudo apt-get install openjdk-6-jre-lib

```

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-10
Not sure what you mean by "Software Center -> other software"...
So I tried 'unmarking' wine-compholio in Synaptic Package, under installed.
It WILL NOT let me unmark it. I tried to "download pkg only"....no go.
I thought about a "force" but I didn't want to break something permanently, or dig the hole deeper.

I also could not "unselect" wine-compholio in the Update Manager.
Of course i do know that Update Manager is the same as the Synaptic Package Manager, essentially.

So unless you mean something different than the Package managing,
I can't disable wine-compholio and proceed.
I hope there is a way to disable or unmark that stupid package.

Shobuz99

---

### Post by Bashing-om on 2013-08-10
Shobuz99;
I honestly can not recall back to 10.04 GUI ... let's try this: from terminal:
```

sudo mv /etc/apt/sources.list.d/ehoover-compholio-lucid.list /etc/apt/sources.list.d/ehoover-compholio-lucid.list-orig

```
Hopefully that will move (mv) it out of our way and still be able to restore when we want it.

And then try and install that library.

where there is a will there is a way

---

### Post by Shobuz99 on 2013-08-10
```

rick@rick-desktop:~$ sudo mv /etc/apt/sources.list.d/ehoover-compholio-lucid.list /etc/apt/sources.list.d/ehoover-compholio-lucid.list-orig
[sudo] password for rick: 
rick@rick-desktop:~$ sudo apt-get install openjdk-6-jre-lib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
rick@rick-desktop:~$ 

```

I think we made some progress.... I think!!

---

### Post by Bashing-om on 2013-08-10
Shobuz99; Yeah .. a bit of progress...
Sure wish I understood what I now know... anyway ... moving on:

```

sudo apt-get update
sudo apt-get install icedtea-6-jre-cacao
sudo apt-get install -f ##just for general purposes see if the package manager is still happy
sudo apt-get dist-upgrade ##for now, without Netflix in the mix, see what haps.

```

[INDENT]are we primed now ?[/INDENT]

---

### Post by Shobuz99 on 2013-08-11
I got up to let the dog out. I figured I'd check in and see what you suggested.
I tried it and here's the results:

```

rick@rick-desktop:~$ sudo apt-get update
[sudo] password for rick: 
Hit http://old-releases.ubuntu.com lucid Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-updates Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-backports Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-proposed Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Hit http://old-releases.ubuntu.com lucid Release
Hit http://old-releases.ubuntu.com lucid-updates Release
Hit http://old-releases.ubuntu.com lucid-backports Release
Hit http://old-releases.ubuntu.com lucid-security Release
Hit http://old-releases.ubuntu.com lucid-proposed Release
Hit http://old-releases.ubuntu.com lucid/main Packages
Hit http://old-releases.ubuntu.com lucid/restricted Packages
Hit http://old-releases.ubuntu.com lucid/universe Packages
Hit http://old-releases.ubuntu.com lucid/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-updates/main Packages
Hit http://old-releases.ubuntu.com lucid-updates/restricted Packages
Hit http://old-releases.ubuntu.com lucid-updates/universe Packages
Hit http://old-releases.ubuntu.com lucid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-backports/main Packages
Hit http://old-releases.ubuntu.com lucid-backports/restricted Packages
Hit http://old-releases.ubuntu.com lucid-backports/universe Packages
Hit http://old-releases.ubuntu.com lucid-backports/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Packages
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/restricted Packages
Hit http://old-releases.ubuntu.com lucid-proposed/main Packages
Hit http://old-releases.ubuntu.com lucid-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/universe Packages
Reading package lists... Done
rick@rick-desktop:~$ sudo apt-get install icedtea-6-jre-cacao
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
rick@rick-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
rick@rick-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
rick@rick-desktop:~$ 
```

One question: the "dist-upgrade" command. Does that mean upgrade Ubuntu to 10.10,
or just update the existing packages without wine-compholio and netflix in the mix for 10.04?

ok. now I'm going back to bed...
Thanks for sticking with me. :-) 
Shobuz99

---

### Post by Bashing-om on 2013-08-11
Shobuz99; Hey ...

So far so good !
"dist-upgrade" Basically it boils down to this ... the package manager is to use a "smart mode" to look at and resolve conflicts, as it can. Mostly in a situation where files have been held back, and not installed ..-> advisory such that you are aware that there may be a problem and needs direction on what you want to do, for various reasons. Just another tool to install updates the package manager is unsure of how to handle.

Ok, we are at a think-about-it stage. Netflix, what now do you want to do ... either fix Netflix or remove it ? ... Keep in mind I know nothing in particular about the application specifically .. but with the package manager's direction, we should be able to work through it to get it functional, if you want to.

[INDENT][INDENT]one more step in a long process
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-11
Ok. I'd rather get rid of Netflix altogether. I don't need it for anything anymore.
I bought an LG "Smart TV", earlier this year and if I want Netflix, I'll view it on my TV..not my computers.
I only had Netflix installed on my desktop. My laptop is 10.04 LTS; but I have no issues with it whatsoever.
Also, as I recall, when I initially installed Netflix on my desktop, Wine-Compholio came with it
as a package dependency, I think....not sure.

So, I'm hoping that once we get rid of Netflix; Wine-Compholio should also go with it or
be removed next. At least that is the plan I had in mind originally...before I realized that 
version 10.04 LTS had ended it's **L**ong **T**erm **S**upport!

So far you've helped me a great deal, regardless of the roller coaster bumpy ride...
I expected that and it has no reflection on your skills and abilities; which I respect.
So, let's continue and see if we can at least get my desktop to a point where I can start
to develop a "backup plan" for my data and then upgrade to what ever will allow me to install
my old Dreamweaver applications for my web work. Whatever the flavor, i think the 13.04 version
should be my goal...don't you?

Carry on Garth!!! 

Shobuz99

---

### Post by Bashing-om on 2013-08-11
Shobuz99; You the man .. let's do this !

Ok, roll "ehoover-compholio-lucid.list" back in place:
```

sudo mv /etc/apt/sources.list.d/ehoover-compholio-lucid.list-orig /etc/apt/sources.list.d/ehoover-compholio-lucid.list
sudo apt-get install ppa-purge

```
and lets see what happens -> prepping to remove Netflix !

As to a version upgrade... I place a high value on stability .. therefore I do have the current Long Term Support version installed as my backup - whatever goes south, I have a backup. That version 12.04 has support until the year 2017.
A lot depends on your hardware if it can run the resource hog that the high end ubuntu has become, which is why I highly recommend lubuntu... but that does not enjoy LTS, and must be version updated quite regularly.
Now, IF you have attained competence with the ubunto operating system and are aware of what apps are available for ubuntu and you are comfortable with what you want on your operating system -> roll your own ! From binaries it is a piece of cake for the experienced and/or adventuresome. Which is what I have done and I am tickled pink with the results overall .. a few minor issues yet to work out as I had expected. The point is that there exist many many options.

We will cross that bridge when you get there. 

Let's see if this bird will fly

---

### Post by Shobuz99 on 2013-08-12
ok. I didn't expect to to the last error message:

```

rick@rick-desktop:~$ sudo mv /etc/apt/sources.list.d/ehoover-compholio-lucid.list-orig /etc/apt/sources.list.d/ehoover-compholio-lucid.list
[sudo] password for rick: 
rick@rick-desktop:~$ sudo apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
rick@rick-desktop:~$ 

``` 

What does this mean?

Shobuz99

---

### Post by Bashing-om on 2013-08-12
Shobuz99; Shucks...
Not surprised .. just means I have to do my homework and figure out how to manually install "ppa-purge".
Looks like all the snakes except Netflix are stomped out ...

[INDENT][INDENT]I will be back
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-08-12
Shobuz99; Hey !

See what I ran across ... Directions are nice to have.


> 
If the package installed from a PPA doesn't exist in official Ubuntu repositories then using PPA Purge is not recommended, because there's nothing to be downgraded and PPA Purge wouldn't delete it either. To remove a PPA and installed packages run the following commands: (Ignore the first command if you don't want to remove the installed packages)

sudo apt-get autoremove --purge package-name
sudo add-apt-repository --remove ppa:someppa/ppa
sudo apt-get autoclean

Let's try this:
```

sudo apt-get autoremove --purge ehoover/compholio
sudo add-apt-repository --remove ppa:ehoover/compholio
sudo apt-get autoclean

```

edit: However, this was supposed to have worked !
> 
 sudo apt-get update && sudo apt-get install ppa-purge && sudo ppa-purge ppa:ehoover/compholio

makes me wonder even more ... what is not up ?

[INDENT][INDENT]as I live and learn !
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-12
```

rick@rick-desktop:~$ sudo apt-get autoremove --purge ehoover/compholio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ehoover
rick@rick-desktop:~$ sudo add-apt-repository --remove ppa:ehoover/compholio
Usage: add-apt-repository sourceline

add-apt-repository is a script for adding apt sources.list entries. 
It can be used to add any repository and also provides a shorthand 
synatax for Launchpad PPA (Personal Package Archive) repositories via
ppa:user/repository

add-apt-repository: error: no such option: --remove
rick@rick-desktop:~$ 

```

Why doesn't the --remove option exist and work?

Shobuz99

---

### Post by Bashing-om on 2013-08-12
Shobuz99; Humm .. 
Maybe I am not passing the proper argument to the command ?


> 
rick@rick-desktop:~$ cat /etc/apt/sources.list.d/ehoover-compholio-lucid.list
deb [http://ppa.launchpad.net/ehoover/compholio/ubuntu](http://ppa.launchpad.net/ehoover/compholio/ubuntu) lucid main
rick@rick-desktop:~$

lets try:
```

sudo apt-get autoremove --purge ehoover/compholio/ubuntu

```

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-12
```

rick@rick-desktop:~$ sudo apt-get autoremove --purge ehoover/compholio/ubuntu
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ehoover
rick@rick-desktop:~$ 

```

uh...should we go back to a previous point and start over...or can we Not go back now?

---

### Post by Bashing-om on 2013-08-12
Shobuz99' 

Quite frankly .. I am at a loss presently ..still look'n about .. see what I can learn.

are these files present ?
```

ls -ls ~/.netflix-desktop
ls -la ~/.wine-browser

```

We have not done much .. as much as we have tried ...there is nothing "to go back to"; still trying to find a means to (un)install netflix with out compromising Wine.
Think'n 'bout trying to find old documentation on how Netflix may have been installed ... reverse engineer it ? 

[INDENT]gotta be a way to do it[/INDENT]

---

### Post by Shobuz99 on 2013-08-12
```
 rick@rick-desktop:~$ ls -ls ~/.netflix-desktop
ls: cannot access /home/rick/.netflix-desktop: No such file or directory
rick@rick-desktop:~$ ls -ls ~/.wine-browser
total 1060
  4 drwxr-xr-x 2 rick rick   4096 2013-02-09 16:00 dosdevices
  4 drwxr-xr-x 6 rick rick   4096 2013-02-09 16:00 drive_c
  4 -rw-r--r-- 1 rick rick    105 2013-02-09 16:00 profile-settings
980 -rw-r--r-- 1 rick rick 997081 2013-02-17 10:01 system.reg
  4 -rw-r--r-- 1 rick rick   2131 2013-02-09 16:00 userdef.reg
 56 -rw-r--r-- 1 rick rick  50699 2013-02-17 10:01 user.reg
  4 -rw-r--r-- 1 rick rick    384 2013-02-09 16:00 wine-browser.sha256sums
  4 -rw-r--r-- 1 rick rick      1 2013-02-09 16:00 wine-version
rick@rick-desktop:~$ 

```

Ok. No Netflix... I'm confused...now

Shobuz99

---

### Post by Bashing-om on 2013-08-12
Shobuz99;

Sorta stumped right now ...as Netflix is not a ubuntu package, highly doubtful that dpkg tracks it or will have any info on what related packages might be installed... how to look and see what the dependencies are - is on my mind - ....

My research to this time has not yielded a better solution than what has already been tried ...

How bout we remove the ppa entry from /etc/sources.list.d/ directory ... and run the update/upgrade routine -> see what results and what effects happen to Wine ??... Sure do not want to mess around with "~/.wine-browser"; That is Wine.

Removing that source may get a stable operating system ... just do not know what orphan files would be left laying around. I can not see any harm in removing that source, particularly with the thought of (re)installing Netflix.
OR
(re)install Netflix and then remove Netflix with "ppa-purge" ?? The way it is supposed to work ...

[INDENT][INDENT]I am tired and going to sleep on it !
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-13
Ok. here's what I did:

1) I created a tmp folder named /Downloads/ehoovertmp.
    Then I copied the "ehoover-compholio-lucid.list" file to that folder, just in case I need to put it back.
2) I deleted the "ehoover-compholio-lucid.list" from the /etc/apt/sources.list.d by using this command:
    ```
 sudo rm /etc/apt/sources.list.d/ehoover-compholio-lucid.list 
```
3) Then I ran the update command. Here's those results:

```
 rick@rick-desktop:~$ sudo rm /etc/apt/sources.list.d/ehoover-compholio-lucid.list
rick@rick-desktop:~$ sudo apt-get update
Hit http://old-releases.ubuntu.com lucid Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-updates Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-backports Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-proposed Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Hit http://old-releases.ubuntu.com lucid Release
Hit http://old-releases.ubuntu.com lucid-updates Release
Hit http://old-releases.ubuntu.com lucid-backports Release
Hit http://old-releases.ubuntu.com lucid-security Release
Hit http://old-releases.ubuntu.com lucid-proposed Release
Hit http://old-releases.ubuntu.com lucid/main Packages
Hit http://old-releases.ubuntu.com lucid/restricted Packages
Hit http://old-releases.ubuntu.com lucid/universe Packages
Hit http://old-releases.ubuntu.com lucid/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-updates/main Packages
Hit http://old-releases.ubuntu.com lucid-updates/restricted Packages
Hit http://old-releases.ubuntu.com lucid-updates/universe Packages
Hit http://old-releases.ubuntu.com lucid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-backports/main Packages
Hit http://old-releases.ubuntu.com lucid-backports/restricted Packages
Hit http://old-releases.ubuntu.com lucid-backports/universe Packages
Hit http://old-releases.ubuntu.com lucid-backports/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Packages
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/restricted Packages
Hit http://old-releases.ubuntu.com lucid-proposed/main Packages
Hit http://old-releases.ubuntu.com lucid-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/universe Packages
Reading package lists... Done
rick@rick-desktop:~$ 
```

No errors! This is good correct?
Now as an extra added step, I tried running Update Manager to see if there were any problems.
The result was the attached image.

My question is, should I select a "Partial Upgrade"??

Thanks
Shobuz99

---

### Post by Bashing-om on 2013-08-13
Shobuz99; Morning !

I am thinking about how best to proceed ... and yeah .. that last is a positive thing overall.. specifically however.. partial upgrades are to be avoided, until such time as we know what is involved.
To that end... you have a old source file for google-chrome in the /etc/apt/sources.list.d/ directory . Is that another failed install or are you using google-chrome ? 

For now let's see what the package manager has to say about what it wants to update;
```

sudo apt-get upgrade

```
and tell the package manager  NO  when asked to "continue" ... will get a good indication of what the package manager is going to do.
Post the output back and we will see what we might be able to do.

In the mean time, I am still seeking a reason why Netflix is being such a problem to remove.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-13
ok. The google-chrome source file can be removed. I actually un-installed Google Chrome, a while ago..
hmmm.. maybe that's part of the problem...??? I think I used Synaptic to uninstall it...I hope I did. Geesh!
Anyway, I want to remove it, so should I proceed to do that?
I'll use:
```
sudo rm /etc/apt/sources.list.d/google-chrome.list.save
```

Ok?

Here's the results of the upgrade attempt:
```

rick@rick-desktop:~$ sudo apt-get upgrade
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
rick@rick-desktop:~$ 

```

Shobuz99

---

### Post by Bashing-om on 2013-08-13
Shobuz99; Yeah...

try:
```

sudo apt-get purge google-chrome-stable
##and then
sudo apt-get autoremove

``` assuming that "stable" is what was initially installed.
 - and then delete that google-chrome file -

And -> still going round and round with Netflix, huh ??.. still appears to be the only hold up. I continue to look for an alternative rather than installing it .. just so we can use the recommended manner to remove it ... 
I have found that the "wine" associated with Netflix is not associated with the normal install of Wine.... that to me a good thing and relieves a lot of pressure.

In the event I do not come up with that better solution .. prior to (re)installing, there are a few thing to find out about your system /// again will cross that bridge when we come to it. 

Not in bad shape at all .. 
[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-13
```

rick@rick-desktop:~$ sudo apt-get purge google-chrome-stable
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
rick@rick-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
rick@rick-desktop:~$ sudo rm /etc/apt/sources.list.d/google-chrome.list.save
rick@rick-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
rick@rick-desktop:~$ 

```

Ok. that's done

Over to you...

shobuz99

---

### Post by Bashing-om on 2013-08-13
Shobuz99; Hey ..

I am about ready to finally remove " package wine-compholio " lemme have a bit to research what exactly "~/.wine-browser" really is ... I have indications that that directory is only in respect to Netflix. I am in the process of checking at this time .. more back soonest...

You are looking good now .. if we can only remove Netflix ,, I think then you will be in good shape.

[INDENT][INDENT]progress made, more to do
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-08-13
Shobuz99; Ok !

Let's try this:
```

sudo apt-get remove netflix-desktop
sudo rm -Rf ~/.wine-browser
##Edit: check here if  "ehoover-compholio-lucid.list" was removed !
sudo apt-get update
sudo apt-get upgrade

```
Be very cautious with "rm -Rf" ... copy and paste preferably ... one little bitty error .. and the system is hosed up maybe beyond repair. What is removed is removed .. and no getting it back .. make sure and doubly sure that what is to be removed is what we want removed ! Only want that one particular directory and its contents gone ...copy and paste to insure this is so. syntax counts !
Take a look now at "/etc/apt/sources.list.d/ directory .. of that file "ehoover-compholio-lucid.list" .. if it still exist .. remove it too.
```

sudo apt-get update
sudo apt-get upgrade

```

[INDENT][INDENT]standing pretty ?[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-13
ok. It's not pretty yet; but it seems better:
```
rick@rick-desktop:~$ sudo apt-get remove netflix-desktop
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
rick@rick-desktop:~$ sudo rm -Rf ~/.wine-browser

rick@rick-desktop:~$ sudo apt-get update
Hit http://old-releases.ubuntu.com lucid Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-updates Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-backports Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-proposed Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Hit http://old-releases.ubuntu.com lucid Release
Hit http://old-releases.ubuntu.com lucid-updates Release
Hit http://old-releases.ubuntu.com lucid-backports Release
Hit http://old-releases.ubuntu.com lucid-security Release
Hit http://old-releases.ubuntu.com lucid-proposed Release
Hit http://old-releases.ubuntu.com lucid/main Packages
Hit http://old-releases.ubuntu.com lucid/restricted Packages
Hit http://old-releases.ubuntu.com lucid/universe Packages
Hit http://old-releases.ubuntu.com lucid/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-updates/main Packages
Hit http://old-releases.ubuntu.com lucid-updates/restricted Packages
Hit http://old-releases.ubuntu.com lucid-updates/universe Packages
Hit http://old-releases.ubuntu.com lucid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-backports/main Packages
Hit http://old-releases.ubuntu.com lucid-backports/restricted Packages
Hit http://old-releases.ubuntu.com lucid-backports/universe Packages
Hit http://old-releases.ubuntu.com lucid-backports/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Packages
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/restricted Packages
Hit http://old-releases.ubuntu.com lucid-proposed/main Packages
Hit http://old-releases.ubuntu.com lucid-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/universe Packages
Reading package lists... Done

rick@rick-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
rick@rick-desktop:~$ 

```

How is it possible that "...wine-compholio needs to be reinstalled"???
I'm afraid to look at Update Manager or Synaptic...
Well..I checked Update manager and the message is the same as the image i sent you..
I checked Synaptic Pkg Manager and the message said this:

"E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report." 
If I close, Synaptic closes... so my package manager is broken..
how do I fix that?

Shobuz99

---

### Post by Bashing-om on 2013-08-13
Shobuz99; Shheesshh.. 
This is really starting to get my goat .. where in the world I too ask is the package manager able to see that there even exist a need to reinstall "The package wine-compholio" ??? over and over and over !
Four means to remove it and it is still present from some source somewhere... I sure was hopeful the last was the answer. Lemme look around some more .. see what I can find .. starting again with your /etc/apt/sources.list file ... maybe I missed something .. I can at times be real blind.
Do not even know what to search for ... but I will know better next time !

[INDENT][INDENT]I'll be back
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-08-13
Shobuz99;

What results:
```

ls -la ${HOME}/wine-compholio
ls -la /etc/apt/sources.list.d/
ls -la /opt/wine-compholio/bin/wine
ls -la /home/<username>/ehoover/.wine-browser

```
I will add to this as I find other things in question.
[INDENT]still look'n[/INDENT]

---

### Post by Shobuz99 on 2013-08-14
ok. this got some interesting results:

```

rick@rick-desktop:~$ ls -la ${HOME}/wine-compholio
ls: cannot access /home/rick/wine-compholio: No such file or directory
rick@rick-desktop:~$ ls -la /etc/apt/sources.list.d/
total 8
drwxr-xr-x 2 root root 4096 2013-08-13 15:57 .
drwxr-xr-x 6 root root 4096 2013-08-07 21:39 ..
rick@rick-desktop:~$ ls -la /opt/wine-compholio/bin/wine
-rwxr-xr-x 2 root root 9604 2013-05-12 08:06 [COLOR="#00FF00"]**/opt/wine-compholio/bin/win**e[/COLOR]
rick@rick-desktop:~$ ls -la /home/rick/ehoover/.wine-browser
ls: cannot access /home/rick/ehoover/.wine-browser: No such file or directory
rick@rick-desktop:~$ 

```

Looks like the /opt/wine-compholio/bin/wine is where it is residing...but Why??
Maybe you understand it; but I don't.
Now the question is, what happens if I remove that folder??? Will I break something?

I did a further search:

```

rick@rick-desktop:~$ ls /opt/wine-compholio/bin/wine
[COLOR="#00FF00"]/opt/wine-compholio/bin/wine[/COLOR]
rick@rick-desktop:~$ cd /opt/wine-compholio/bin/wine
bash: cd: /opt/wine-compholio/bin/wine: Not a directory
rick@rick-desktop:~$ cd /opt/wine-compholio/bin/
rick@rick-desktop:/opt/wine-compholio/bin$ dir
function_grep.pl	   winebuild.dpkg-new	 winegcc.dpkg-tmp
function_grep.pl.dpkg-new  winebuild.dpkg-tmp	 winemaker
function_grep.pl.dpkg-tmp  winecfg		 winemaker.dpkg-new
msiexec			   winecfg.dpkg-new	 winemaker.dpkg-tmp
msiexec.dpkg-new	   winecfg.dpkg-tmp	 winemine
msiexec.dpkg-tmp	   wineconsole		 winemine.dpkg-new
notepad			   wineconsole.dpkg-new  winemine.dpkg-tmp
notepad.dpkg-new	   wineconsole.dpkg-tmp  winepath
notepad.dpkg-tmp	   winecpp		 winepath.dpkg-new
regedit			   winedbg		 winepath.dpkg-tmp
regedit.dpkg-new	   winedbg.dpkg-new	 wine-preloader
regedit.dpkg-tmp	   winedbg.dpkg-tmp	 wine-preloader.dpkg-new
regsvr32		   wine.dpkg-new	 wine-preloader.dpkg-tmp
regsvr32.dpkg-new	   wine.dpkg-tmp	 wineserver
regsvr32.dpkg-tmp	   winedump		 wineserver.dpkg-new
widl			   winedump.dpkg-new	 wineserver.dpkg-tmp
widl.dpkg-new		   winedump.dpkg-tmp	 wmc
widl.dpkg-tmp		   winefile		 wmc.dpkg-new
wine			   winefile.dpkg-new	 wmc.dpkg-tmp
wineboot		   winefile.dpkg-tmp	 wrc
wineboot.dpkg-new	   wineg++		 wrc.dpkg-new
wineboot.dpkg-tmp	   winegcc		 wrc.dpkg-tmp
winebuild		   winegcc.dpkg-new
rick@rick-desktop:/opt/wine-compholio/bin$ cd /
rick@rick-desktop:/$ cd /opt/wine-compholio
rick@rick-desktop:/opt/wine-compholio$ dir
[COLOR="#40E0D0"]bin  include  lib32  share[/COLOR]
rick@rick-desktop:/opt/wine-compholio$ 
```

I attached an image of the "Opt" directory... it shows Google-Chrome has one file in there, too

hmmmm...

shobuz99

---

### Post by Bashing-om on 2013-08-14
Shobuz99;

I semi comprehend the why of that directory ... I found the Make file for "wine-compholio" .. the reason I suspected it might still be around. Now my thinking is that the file regarding google is but a hook into the browser and removing that directory will not affect google-chrome.
I have given this a bit of thought and my conclusion is to remove that directory ! I believe from what I have been able to determine that anything "wine-compholio" is only in relation to Netflix; that it is entirely separate from the standard install of Wine, I expect to be able to remove anything "wine-compholio" and not have a direct affect on any thing else. What I can not say is what orphan files may still be around, not that would have any direct effects in that event . Worth putting some thought into how to make sure things are cleaned up.
```

sudo rm -Rf /opt/wine-compholio/
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```
hope now it runs clean ! And does it's thing.

[INDENT][INDENT]that is my thoughts
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-14
```

rick@rick-desktop:~$ sudo rm -Rf /opt/wine-compholio/
[sudo] password for rick: 
rick@rick-desktop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del wine-compholio 1.6~lucid [15.7MB]
Del wine-compholio 1.7.0~lucid [16.0MB]
rick@rick-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
rick@rick-desktop:~$ sudo apt-get clean
rick@rick-desktop:~$ sudo apt-get update
Hit http://old-releases.ubuntu.com lucid Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-updates Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-backports Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-proposed Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Hit http://old-releases.ubuntu.com lucid Release
Hit http://old-releases.ubuntu.com lucid-updates Release
Hit http://old-releases.ubuntu.com lucid-backports Release
Hit http://old-releases.ubuntu.com lucid-security Release
Hit http://old-releases.ubuntu.com lucid-proposed Release
Hit http://old-releases.ubuntu.com lucid/main Packages
Hit http://old-releases.ubuntu.com lucid/restricted Packages
Hit http://old-releases.ubuntu.com lucid/universe Packages
Hit http://old-releases.ubuntu.com lucid/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-updates/main Packages
Hit http://old-releases.ubuntu.com lucid-updates/restricted Packages
Hit http://old-releases.ubuntu.com lucid-updates/universe Packages
Hit http://old-releases.ubuntu.com lucid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-backports/main Packages
Hit http://old-releases.ubuntu.com lucid-backports/restricted Packages
Hit http://old-releases.ubuntu.com lucid-backports/universe Packages
Hit http://old-releases.ubuntu.com lucid-backports/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Packages
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/restricted Packages
Hit http://old-releases.ubuntu.com lucid-proposed/main Packages
Hit http://old-releases.ubuntu.com lucid-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/universe Packages
Reading package lists... Done
rick@rick-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
rick@rick-desktop:~$ 
```

What???? 
After I ran "autoclean" it clearly showed that wine-compholio was deleted!
As soon as I ran "autoremove", it's back???....somewhere...but where?

Shobuz99

---

### Post by Shobuz99 on 2013-08-14
Ok. I found something.
attached is the image.
It's in Software Services. Shall I "remove" it?

Shobuz99

---

### Post by Bashing-om on 2013-08-14
Shobuz99; I have the same reaction !
OK, let's go looking:
```

sudo rm -Rf /opt/wine-compholio
sudo find / -name wine-compholio
sudo find / -name ehoover
sudo find / -name compholio
sudo find / -name "*netflix*"

```
the find command searches the entire file system and takes a long time in each instance .. patience.
Let's see if there are any hits on any of these subjects.

Gotta be something some where calling "wine-compholio"; to this time we have removed everything I can think of in every means I can think of.
So ..... it is back to look'n and think'n as to how Netflix installs !
Bear in mind that we can always try (re-)installing Netflix to be fully functional .. and then remove it with the conventional means -> "sudo ppa-purge ppa:ehoover/compholio" ...
Nother thought in respect to installing ... are we not stuck; in that  that we can not install anything at all until this "wine-compholio" situation is resolved ??

[INDENT][INDENT]some where some how !
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-14
Before I proceed, did you see the attached file I sent regarding Software Services?
It had a Launchpad Compholio entry in the list.
My question was, should I remove that first from the Software Services list through
that dialog box that i sent you the image of?

Shobuz99

---

### Post by Shobuz99 on 2013-08-14
Well well well well well...."Guess what day it is? It's HUMP day! woohoo!!"  lol...
Sorry I had to say that...lol I think we found the contents of the "hump"
```

rick@rick-desktop:~$ sudo rm -Rf /opt/wine-compholio
[sudo] password for rick: 
rick@rick-desktop:~$ sudo find / -name wine-compholio
/usr/share/doc/wine-compholio
rick@rick-desktop:~$ sudo find / -name ehoover
rick@rick-desktop:~$ sudo find / -name compholio
rick@rick-desktop:~$ sudo find / -name "*netflix*"
/var/lib/dpkg/info/netflix-desktop.md5sums
/var/lib/dpkg/info/netflix-desktop.preinst
/var/lib/dpkg/info/netflix-desktop.list
/var/lib/dpkg/info/netflix-desktop.postinst
/var/lib/dpkg/info/netflix-desktop.prerm
/var/lib/dpkg/info/netflix-desktop.postrm
/home/rick/.config/chromium/Default/Local Storage/http_movies.netflix.com_0.localstorage-journal
/home/rick/.config/chromium/Default/Local Storage/http_movies.netflix.com_0.localstorage
/home/rick/.local/share/applications/netflix-desktop.desktop
/usr/bin/netflix-desktop
/usr/share/wine-browser-installer/netflix-desktop.menu
/usr/share/wine-browser-installer/netflix-desktop.install-files
/usr/share/wine-browser-installer/netflix-desktop.sha256sums
/usr/share/applications/netflix-desktop.desktop
/usr/share/locale/bs/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/ja/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/en_US/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/ms/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/ast/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/tr/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/pt_BR/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/my/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/en_CA/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/en/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/ca/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/ug/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/pl/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/da/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/en_GB/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/fr/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/es/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/de/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/eu/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/en_AU/LC_MESSAGES/netflix-desktop.mo
/usr/share/locale/bg/LC_MESSAGES/netflix-desktop.mo
/usr/share/doc/netflix-desktop
/usr/share/package-data-downloads/netflix-desktop
rick@rick-desktop:~$  
```

I'm just hoping that we can clear this out and get Synaptic Pkg Manager working again.
It is very broke, at this point. I have an error icon in the upper right of my top panel bar.
It is a round red ball with a white dash in it. The error message says 'Unknown Error:' <type 'exceptions.SystemError'>' 
And it complains of "unmet dependencies".

Shobuz99

---

### Post by Bashing-om on 2013-08-14
Shobuz99; Nope I had not seen the "attached file I sent regarding Software Services" !
It does check out to be the signing key for "wine-compholio" !

I know of no way to see into that file to see what it is doing .. so yes it is possible it is calling home .. and it is trusted -  so, if so no harm.
I suggest to go ahead and delete it ... and I maybe fixing to learn something new (if then we do not get the "wine-compholio" reinstall request).
remember also to make sure the "/opt/wine-compholio" does not exist after deleting that signing key.

Hope this time it is not a false light at the end of that tunnel !

---

### Post by Shobuz99 on 2013-08-14
> **Bashing-om said:**
> Shobuz99; Nope I had not seen the "attached file I sent regarding Software Services" !
It does check out to be the signing key for "wine-compholio" !

I know of no way to see into that file to see what it is doing .. so yes it is possible it is calling home .. and it is trusted -  so, if so no harm.
I suggest to go ahead and delete it ... and I maybe fixing to learn something new (if then we do not get the "wine-compholio" reinstall request).
remember also to make sure the "/opt/wine-compholio" does not exist after deleting that signing key.

Hope this time it is not a false light at the end of that tunnel !

What about all the "*netflix*" references in various folders,
that showed up on that search command you told me to run?
What command will delete all those?
Should I reboot my machine, once we have determined what is to be deleted and delete it?

Shobuz99

---

### Post by Bashing-om on 2013-08-14
Shobuz99;
Had not expected at this point that the find command would return with any result ....show me what you are looking at so I may make an educated guess as to what might be the case.
In any case .. prior to rebooting ... lets make sure the package manager is happy with the update/upgrade routine.

[INDENT][INDENT]hopes are high
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-08-14
Shobuz99;
Just seen your prior post with the requested find "*netflix*" info ... Wow .. gets deeper and deeper, huh .."almost" all of that is safe to delete. let's see if this helps windrow thing up for us.
```

apt-get remove wine-browser-installer
apt-get purge wine-browser-installer

```
And I be looking at what I think is safe and should be deleted.

[INDENT][INDENT]look'n !
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-14
> **Bashing-om said:**
> Shobuz99;
Just seen your prior post with the requested find "*netflix*" info ... Wow .. gets deeper and deeper, huh .."almost" all of that is safe to delete. let's see if this helps windrow thing up for us.
```

apt-get remove wine-browser-installer
apt-get purge wine-browser-installer

```
And I be looking at what I think is safe and should be deleted.

[INDENT][INDENT]look'n !
[/INDENT][/INDENT]

Ok. I had to use sudo in each case of your command suggestions.
Otherwise it asked me if I was root.
So here's the results:
```

rick@rick-desktop:~$ apt-get remove wine-browser-installer
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
rick@rick-desktop:~$ sudo apt-get remove wine-browser-installer
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
rick@rick-desktop:~$ sudo apt-get purge wine-browser-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.
rick@rick-desktop:~$  
```

Like Yogi said..."It ain't over 'till it's over.."

Shobuz99

---

### Post by Bashing-om on 2013-08-15
Shobuz99; Yeah ,,,
I am almost to the point of agreeing to manually delete ALL those Netflix files, still some very slight reservations about the files in /usr/share/local/XXXX
Which I think are but desktop aps for Netflix and should also be deleted .. still looking to find out what they actually are.
I can not see how it would worsen the situation if ALL the files were removed;
- check that the key is gone
- verify that the "get" file from  "/etc/apt/sources.list.d" does not exist
- the directory "/opt/wine-compholio/" has not been recreated
- one-by-one manually delete the Netflix files.

Presently I am tired and not think'n too clear, will re-think this, for what I may be missing, in my morrow.

[INDENT]2 steps forward and three back .. does not get us very far[/INDENT]

---

### Post by Shobuz99 on 2013-08-15
Ok. You've stuck with me for over a week. 
This is more than I could have asked for.
I detect a penchant for perseverance on your part; much like me.
I don't think I will do anything more, until I hear from you again.
My main concern now, is that Synaptic Pkg Manager is broken
and I want to get it fixed, ultimately. 

I think removing ALL files related to Netflix must be done.
After that, I'm not sure what to think if the results do not finally clear the problem.
I can function with a broken Synaptic, but it hampers my ability to start backing up
my files so I can reformat the drive and install lubuntu 13.04 or whatever and
hope that my old DWMX 2004 will still function on that platform.

These are all my hopes. I wouldn't have any of them, if it weren't for you and
your dedication to my cause. Once again, I must say that I appreciate your help
and all that you are doing to figure this out, and fix it.
    
Shobuz99

---

### Post by Bashing-om on 2013-08-15
Shobuz99; Back to this on my AM ..

seeking why there may be a reason not to remove those "/usr/share/locale/XXXX" files. At this time I know of no better way to proceed than manually deleting ALL those files...As a general rule .. one should never ever mess with a system file. This I am beginning to think is an exception to that rule.

I have in mind a recipe that I expect will get  "that Synaptic Pkg Manager is broken
and I want to get it fixed, ultimately." resolved .. after we get rid of Netflix and keep it from calling home to be restored !

I have learned a lot about Netflix during this odysey that I will be able to apply at some future time. The Wife sometimes hints she would like to try Netflix; so this problem resolution is a two way street. 

[INDENT][INDENT]back to look'n and think'n
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-08-15
Shobuz99; Ready to proceed;
This:
> 
Note: It may be preferable that each package have its own unique domain to keep things simple and maintainable.

A domain corresponds to the relevant set of binary translation files, each named <domain>.mo, for example, galculator.mo
For each translation, there's a separate <domain>.mo file. These reside in the system's locale directories: /usr/share/locale/<locale>/LC_MESSAGES. For example, if galculator has translations for Chinese/China and French/Canada, it would have the following two .mo files;
/usr/share/locale/zh_CN/LC_MESSAGES/galculator.mo
/usr/share/locale/fr_CA/LC_MESSAGES/galculator.mo
 re-enforces my believe that those file are delete-able. Any adverse effects and I have a command to rebuild the database.

First though, let's take a look and see what the package manager sees overall for "Netflix".
```

dpkg -l | grep netflix

```
[INDENT][INDENT]aiming to fire[/INDENT][/INDENT]

---

### Post by philinux on 2013-08-15
You guys have also managed to hijack the op's thread with a totally different problem.  Hope the op sorted it out with the help 3 weeks ago as he's not posted since.

---

### Post by Shobuz99 on 2013-08-15
Philinux,
I apologize. It's my fault. I should have created a separate/new thread.
I also hope that the original thread creator has solved his issue.
Bashing-om has been working OT trying to help me fix this. I sincerely appreciate it too.

Hopefully we can figure this out. 
Is it a thread violation if we continue with this issue in this thread? 
I don't want to cause any trouble at all.
Please let me know.
Thanks

Shobuz99

---

### Post by Bashing-om on 2013-08-15
@ philinux .. I should have directed Shobuz99 to start another thread ... I generally do try to adhere to the set policy. I got involved beyond the initial advisement and just carried on . A slip of the mind .. will try to be more mindful in future relations.

Agreed this thread no longer serves the original purpose but perhaps now this situation can be terminated successfully and the thread left open for the OP.

Glad you are looking at this .. reassuring to know others are at my back.

---

### Post by bapoumba on 2013-08-15
Moved to its own thread.

---

### Post by Shobuz99 on 2013-08-15
```
rick@rick-desktop:~$ dpkg -l | grep netflix
ri  netflix-desktop                                          0.7.0~lucid                                       provides a convient tool that downloads and 
rick@rick-desktop:~$ 
```

This is weird. It isn't displaying properly and I don't know where it is!!
I have to tell you that I *think* I have a malware problem.
I've run Clamtk 4.45, 2 times and let it run unattended. 
When I got back, the machine had shut down by itself.
Clamtk didn't even acknowledge that a scan had been run...
This just doesn't look right, and obviously, I can't see where it's located
because it's not on my desktop...unless it's a hidden file or something.

This is our problem I think. Even so, I do want to delete all files related to Netflix..regardless

Thanks Bashing-om. Sorry I got you in trouble with the moderator

Shobuz99

---

### Post by Bashing-om on 2013-08-15
Shobuz99;
Well the output of dpkg looks acceptable to me, We know the location as "user/bin/" from the find command. And that is all dpkg is interested in.
the "ri" => r, marked for removal; i, still installed.
see:
[http://linuxprograms.wordpress.com/2010/05/14/dpkg-tutorial/](http://linuxprograms.wordpress.com/2010/05/14/dpkg-tutorial/)

Malware on your computer, possible but highly unlikely less you got something in the real "wine" install .. and that should not affect the operating system at large.

Deleting netflix files: You may not need the pointers, but if it were me I would ->
open two terminals; terminal one with the output of post #83 "sudo find / -name "*netflix*""
terminal 2 is the working terminal, copy and paste the files names from terminal one to terminal 2, one file at a time and execute ->
in terminal 2, insert, before the <file name>, "sudo rm". This is crucial and tedious to the point I would stay with using sudo (rather than root access) and copy paste for accuracy ... no room for error here.
When all the removing is done; Do:
```

sudo update-desktop-database
sudo apt-get update
sudo dpkg --clear-avail
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update #again !
sudo apt-get dist-upgrade

```

And  -> will see what is, after all the firing is done.

---

### Post by Shobuz99 on 2013-08-16
ok. this is done except for two folders/directories that I could not delete,
because I don't know the command for deleting directories:
```
rick@rick-desktop:~$ sudo rm /var/lib/dpkg/info/netflix-desktop.md5sums
[sudo] password for rick: 
rick@rick-desktop:~$ sudo rm /var/lib/dpkg/info/netflix-desktop.preinst
rick@rick-desktop:~$ sudo rm /var/lib/dpkg/info/netflix-desktop.list
rick@rick-desktop:~$ sudo rm /var/lib/dpkg/info/netflix-desktop.postinst
rick@rick-desktop:~$ sudo rm /var/lib/dpkg/info/netflix-desktop.prerm
rick@rick-desktop:~$ sudo rm /var/lib/dpkg/info/netflix-desktop.postrm
rick@rick-desktop:~$ sudo rm /home/rick/.local/share/applications/netflix-desktop.desktop
rick@rick-desktop:~$ sudo rm /usr/bin/netflix-desktop
rick@rick-desktop:~$ sudo rm /usr/share/wine-browser-installer/netflix-desktop.menu
rick@rick-desktop:~$ sudo rm /usr/share/wine-browser-installer/netflix-desktop.install-files
rick@rick-desktop:~$ sudo rm /usr/share/wine-browser-installer/netflix-desktop.sha256sums
rick@rick-desktop:~$ sudo rm /usr/share/applications/netflix-desktop.desktop
rick@rick-desktop:~$ sudo rm /usr/share/locale/bs/LC_MESSAGES/netflix-desktop.mo
[sudo] password for rick: 
rick@rick-desktop:~$ sudo rm /usr/share/locale/ja/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/en_US/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/ms/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/ast/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/tr/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/pt_BR/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/my/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/en_CA/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/en/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/ca/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/ug/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/pl/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/da/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/en_GB/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/fr/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/es/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/de/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/eu/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/en_AU/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/locale/bg/LC_MESSAGES/netflix-desktop.mo
rick@rick-desktop:~$ sudo rm /usr/share/doc/netflix-desktop
rm: cannot remove `/usr/share/doc/netflix-desktop': Is a directory
rick@rick-desktop:~$ sudo rm /usr/share/package-data-downloads/netflix-desktop
rick@rick-desktop:~$ sudo rm /var/lib/dpkg/info/wine-compholio.postinst
rick@rick-desktop:~$ sudo rm /var/lib/dpkg/info/wine-compholio.md5sums
rick@rick-desktop:~$ sudo rm /var/lib/dpkg/info/wine-compholio.postrm
rick@rick-desktop:~$ sudo rm /var/lib/dpkg/info/wine-compholio.conffiles
rick@rick-desktop:~$ sudo rm /var/lib/dpkg/info/wine-compholio.shlibs
rick@rick-desktop:~$ sudo rm /var/lib/dpkg/info/wine-compholio.prerm
rick@rick-desktop:~$ sudo rm /usr/share/doc/wine-compholio
rm: cannot remove `/usr/share/doc/wine-compholio': Is a directory
rick@rick-desktop:~$ 
```

On a hunch I searched for '*wine-compholio*' with the same "find" command as the '*netflix*'.
When I found that directory I deleted the contents, one at a time, in the same manner.
However, I couldn't remove that directory either:

```
rick@rick-desktop:/usr/share/doc$ sudo find / -name "*netflix*"
/usr/share/doc/netflix-desktop
rick@rick-desktop:/usr/share/doc$ sudo find / -name "*wine-compholio*"
/var/lib/dpkg/info/wine-compholio.postinst
/var/lib/dpkg/info/wine-compholio.md5sums
/var/lib/dpkg/info/wine-compholio.postrm
/var/lib/dpkg/info/wine-compholio.conffiles
/var/lib/dpkg/info/wine-compholio.shlibs
/var/lib/dpkg/info/wine-compholio.prerm
/usr/share/doc/wine-compholio
rick@rick-desktop:/usr/share/doc$ cd 
rick@rick-desktop:~$ sudo find / -name "*netflix*"
/usr/share/doc/netflix-desktop
rick@rick-desktop:~$ sudo find / -name "*wine-compholio*"
/usr/share/doc/wine-compholio
rick@rick-desktop:~$ 
```

Please tell me the command to delete a dir. 
Does the directory have to be "empty", and do I need to delete it from the directory above it?

I will continue after I hear from you.

Shobuz99

---

### Post by Bashing-om on 2013-08-16
Shobuz99; Morning to ya !
Commnad to remove directory and all it's contents:
"rm -Rf <directory_name>" .. with it's path .. so the command can find that directory. As in:
> 
sudo rm -rf /var/lib/apt/lists
From the manual:
By default, rm does not remove directories.  Use the --recursive (-r or
       -R) option to remove each listed directory, too, along with all of  its
       contents.

The example removes the directory "list" and all it's contents.
Explicitly in our case:
```

sudo rm -rf /usr/share/doc/wine-compholio

```

Fire away !

[INDENT][INDENT]a process of learning
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-16
Ok. Bashing-om, I removed those two directories, without incident. Yay!! :)

Next I tried the first command in your recommended list of steps:

```
rick@rick-desktop:~$ **[COLOR="#B22222"]sudo update-desktop-database[/COLOR]**
Warning in file "/usr/share/applications/thunderbird.desktop": **usage of MIME type "x-scheme-handler/mailto" is discouraged** (the use of "x-scheme-handler" as media type is strongly discouraged in favor of a subtype of the "application" media type)
Warning in file "/usr/share/applications/firefox.desktop": **usage of MIME type "x-scheme-handler/http" is discouraged** (the use of "x-scheme-handler" as media type is strongly discouraged in favor of a subtype of the "application" media type)
Warning in file "/usr/share/applications/firefox.desktop": **usage of MIME type "x-scheme-handler/https" is discouraged** (the use of "x-scheme-handler" as media type is strongly discouraged in favor of a subtype of the "application" media type)
Warning in file "/usr/share/applications/firefox.desktop": **usage of MIME type "x-scheme-handler/ftp" is discouraged** (the use of "x-scheme-handler" as media type is strongly discouraged in favor of a subtype of the "application" media type)
Warning in file "/usr/share/applications/firefox.desktop": u**sage of MIME type "x-scheme-handler/chrome" is discouraged** (the use of "x-scheme-handler" as media type is strongly discouraged in favor of a subtype of the "application" media type)
rick@rick-desktop:~$ 

```

Why did this happen to ONLY the firefox.desktop and the thunderbird.desktop?? #-o

i think I should stop here and wait for your advice. I don't want to continue, pending any other error messages
for the rest of the commands:

```
**[COLOR="#B22222"]sudo update-desktop-database[/COLOR]**
sudo apt-get update
sudo dpkg --clear-avail
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update #again !
sudo apt-get dist-upgrade
```

Agree?

shobuz99

---

### Post by Bashing-om on 2013-08-16
Shobuz99;
First I have encountered that "warning" -not an error- not real happy about some preference setting in FireFox .. let's ignore that one for the time being.
Continue on as you are ... one command at a time and see where we stand.

keep firing away !

---

### Post by Shobuz99 on 2013-08-16
Uh...I don't get it! :mad:

```
rick@rick-desktop:~[COLOR="#008000"]**$ sudo apt-get update**[/COLOR]
[sudo] password for rick: 
Hit http://old-releases.ubuntu.com lucid Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-updates Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-backports Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-proposed Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Hit http://old-releases.ubuntu.com lucid Release
Hit http://old-releases.ubuntu.com lucid-updates Release
Hit http://old-releases.ubuntu.com lucid-backports Release
Hit http://old-releases.ubuntu.com lucid-security Release
Hit http://old-releases.ubuntu.com lucid-proposed Release
Hit http://old-releases.ubuntu.com lucid/main Packages
Hit http://old-releases.ubuntu.com lucid/restricted Packages
Hit http://old-releases.ubuntu.com lucid/universe Packages
Hit http://old-releases.ubuntu.com lucid/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-updates/main Packages
Hit http://old-releases.ubuntu.com lucid-updates/restricted Packages
Hit http://old-releases.ubuntu.com lucid-updates/universe Packages
Hit http://old-releases.ubuntu.com lucid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-backports/main Packages
Hit http://old-releases.ubuntu.com lucid-backports/restricted Packages
Hit http://old-releases.ubuntu.com lucid-backports/universe Packages
Hit http://old-releases.ubuntu.com lucid-backports/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Packages
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/restricted Packages
Hit http://old-releases.ubuntu.com lucid-proposed/main Packages
Hit http://old-releases.ubuntu.com lucid-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/universe Packages
Reading package lists... Done
rick@rick-desktop:~$ **[COLOR="#008000"]sudo dpkg --clear-avail[/COLOR]**
rick@rick-desktop:~$ **[COLOR="#008000"]sudo dpkg --configure -a[/COLOR]**
rick@rick-desktop:~$ **[COLOR="#B22222"]sudo apt-get install -f[/COLOR]**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**[COLOR="#A52A2A"]E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.[/COLOR]**
rick@rick-desktop:~$ 

```

How is this possible???

Shobuz99

---

### Post by Bashing-om on 2013-08-16
Shobuz99; Presently I do not have the foggiest notion left ...
1. The get file is deleted from /etc/apt/sources.list.d/ directory
2. The signing key has been removed within "software sources"
3. several attempts with various methods using the package manager tools have not "purged" netfix
4. Manually removed ALL files in relation to netflix
All to the result:
> 
E: The package wine-compholio needs to be reinstalled, but I can't find an archive for it.


Never in all my time have I encountered such a situation - never, though, in all my time have I encountered Netflix.

Probably discouraging to you for me to say .. but -> back to the drawing board .. see what I can find out about the installation process and what file names are what, and where they are installed to ... and go hunt for them again ! Even though I thought I had that nailed down !

For sure in my learning mode!

---

### Post by bapoumba on 2013-08-16
Please try  **sudo dpkg --remove --force-remove-reinstreq wine-compholio**

---

### Post by Bashing-om on 2013-08-16
not to mind presently .. 
let's see what results form bapoumba's advise (thanks heaps !).

---

### Post by Shobuz99 on 2013-08-16
ok. Tried bapoumba's advice:

```
rick@rick-desktop:~$ **[COLOR="#B22222"]sudo dpkg --remove --force-remove-reinstreq wine-compholio[/COLOR]**
[sudo] password for rick: 
[B]dpkg: dependency problems prevent removal of wine-compholio:
 wine-browser-installer depends on wine-compholio (>= 1.5.19~lucid1).
 wine-browser-installer depends on wine-compholio (>= 1.5.19~lucid1).
dpkg: error processing wine-compholio (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 wine-compholio[/B]
rick@rick-desktop:~$ 

```

Thank you bapoumba for helping. 
I decided to search for wine-browser-installer:
```
rick@rick-desktop:~$ sudo find / -name "*wine-browser-installer*"
/var/lib/dpkg/info/wine-browser-installer.list
/var/lib/dpkg/info/wine-browser-installer.postrm
/var/lib/dpkg/info/wine-browser-installer.md5sums
/var/lib/dpkg/info/wine-browser-installer.prerm
/var/lib/dpkg/info/wine-browser-installer.preinst
/var/lib/dpkg/info/wine-browser-installer.postinst
/usr/share/wine-browser-installer
/usr/share/wine-browser-installer/wine-browser-installer.install-files
/usr/share/wine-browser-installer/wine-browser-installer.sha256sums
/usr/share/doc/wine-browser-installer
/usr/share/package-data-downloads/wine-browser-installer
rick@rick-desktop:~$ 

```

So...do I proceed to remove wine-browser-installer, like I did netflix and wine-compholio??

or use bapoumba's command and replace with the wine-browser-installer directory???

```
sudo dpkg --remove --force-remove-reinstreq wine-browser-installer
```

I pensively await your instructions.

Shobuz99

---

### Post by bapoumba on 2013-08-16
No, do not use the command if the other process has worked so far. It is recommended to use it when dpkg complains it cannot find the archive for the file. Or at least, that is the only situation I've used it or recommended to use it.

---

### Post by Bashing-om on 2013-08-16
'nother thought ..
What results from:
```

dpkg -l netflix-desktop
sudo find / -name Netflix ##note this time with upper case "N"

```

AND
As netflix IS dependent on "Wine" .. and .. I see no ppa's at this time for "Wine" -> do we dare risk installing the latest Wine ppa and updating Wine ... see if that is the source of  dpkg wanting to (re)install wine-compholio (???)
Updating Wine ---will it break the locks on the installed Windows' applications ?
> ok. Tried bapoumba's advice:
still in wine-compholio hell.

[INDENT][INDENT]to far of a grasp ?
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-16
> **Bashing-om said:**
> 'nother thought ..
What results from:
```

dpkg -l netflix-desktop
sudo find / -name Netflix ##note this time with upper case "N"

```

AND
As netflix IS dependent on "Wine" .. and .. I see no ppa's at this time for "Wine" -> do we dare risk installing the latest Wine ppa and updating Wine ... see if that is the source of  dpkg wanting to (re)install wine-compholio (???)
Updating Wine ---will it break the locks on the installed Windows' applications ?

still in wine-compholio hell.

[INDENT][INDENT]too far of a grasp ?
[/INDENT][/INDENT]

Well here's the first result:

```
rick@rick-desktop:~$ dpkg -l netflix-desktop
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ri  netflix-deskto 0.7.0~lucid    provides a convient tool that downloads and 
rick@rick-desktop:~$ 

```

And the 2nd result:
```
rick@rick-desktop:~$ sudo find / -name Netflix
[sudo] password for rick: 
rick@rick-desktop:~$ 

```

Nada.

My question still is: do I proceed to remove wine-browser-installer, like I did netflix and wine-compholio??
i.e., One line at a time, before we try the re-install of anything???

```
rick@rick-desktop:~$ sudo find / -name "*wine-browser-installer*"
/var/lib/dpkg/info/wine-browser-installer.list
/var/lib/dpkg/info/wine-browser-installer.postrm
/var/lib/dpkg/info/wine-browser-installer.md5sums
/var/lib/dpkg/info/wine-browser-installer.prerm
/var/lib/dpkg/info/wine-browser-installer.preinst
/var/lib/dpkg/info/wine-browser-installer.postinst
/usr/share/wine-browser-installer
/usr/share/wine-browser-installer/wine-browser-installer.install-files
/usr/share/wine-browser-installer/wine-browser-installer.sha256sums
/usr/share/doc/wine-browser-installer
/usr/share/package-data-downloads/wine-browser-installer
rick@rick-desktop:~$
```

Shobuz99

---

### Post by Bashing-om on 2013-08-16
Shobuz99;

Yes .. I do suggest that you do go ahead and remove -one item at a time - all the "wine-browser" files ..
also: I thought that the "netflix-desktop" was also history ... looks to still be around .. need to go back to that find command and see where it is installed and "sudo rm" it too .

As there is currently no satisfaction I continue the hunt for what and where .. see what I can find out.

[INDENT][INDENT]I'll be back next intermission[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-16
Ok. I did all that. No difference. 

It's back to square 1 or we need another method to search for dependencies
and any other files that could be connected with wine-compholio, wine-browser-installer, and netflix.
Outside of those possibilities, what other files could be 'calling home', as you say?

I am totally without any ideas. 

Shobuz99

---

### Post by Bashing-om on 2013-08-16
Shobuz99; Coming up most totally blank ...less
look and see if this one exist:
```

ls -la /opt/wine-compholio/bin/
ls -la /usr/bin/netflix-desktop

```
but, not giving up ... gotta be a way to find/remove Netflix manually ... apparently we are the very first to attempt to do this !

[INDENT]keep strok'n 'till we make butter[/INDENT]

---

### Post by Bashing-om on 2013-08-16
Shobuz99;

I am done for the night .. will continue this in my 'morrow ..

[INDENT][INDENT]read ya then
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-17
> **Bashing-om said:**
> Shobuz99; Coming up most totally blank ...less
look and see if this one exist:
```

ls -la /opt/wine-compholio/bin/
ls -la /usr/bin/netflix-desktop

```
but, not giving up ... gotta be a way to find/remove Netflix manually ... apparently we are the very first to attempt to do this !

[INDENT]keep strok'n 'till we make butter[/INDENT]

Nope:
```
rick@rick-desktop:~$ ls -la /opt/wine-compholio/bin/
ls: cannot access /opt/wine-compholio/bin/: No such file or directory
rick@rick-desktop:~$ ls -la /usr/bin/netflix-desktop
ls: cannot access /usr/bin/netflix-desktop: No such file or directory
rick@rick-desktop:~$ 
```

Shobuz99

---

### Post by raja.genupula on 2013-08-17
lets findout where we have those terms . I mean use > locate netflix That will show where you have the netflix files and folders. so that we can make sure about those locations.

---

### Post by Shobuz99 on 2013-08-17
> **raja.genupula said:**
> lets findout where we have those terms . I mean use  That will show where you have the netflix files and folders. so that we can make sure about those locations.

```
rick@rick-desktop:~$ locate netflix
rick@rick-desktop:~$ 

```

Nada. I tried ```
rick@rick-desktop:~$ locate wine-compholio 
rick@rick-desktop:~$
``` and 
```
rick@rick-desktop:~$ locate wine-browser-installer
rick@rick-desktop:~$
``` as well and got the same result. Nada.

It's important to note that I continue to see something listed when I run the command:
```
rick@rick-desktop:~$ dpkg -l | grep netflix
ri  netflix-desktop                            0.7.0~lucid                                       provides a [COLOR="#B22222"]convient[/COLOR] tool that downloads and 
rick@rick-desktop:~$  
```

Where on earth is this 'thing'??? BTW...the spelling of "[COLOR="#B22222"]convenient[/COLOR]" is incorrect and makes me suspicious, as well as,
the long spacing between the output of this 'thing'.

Bashing-om has told me that it is assumed to be in /usr/bin; but why can't it be removed?
Is it already marked for removal and the "mark" is what is being referenced; Even though it doesn't exist?
Is this why Synaptic Pkg Manager and Update Manager continue to give error messages and remain broken?

To me, as a low level experienced Ubuntu user, there seems to be a circular event occurring
that is reporting something that cannot be resolved without the mechanism to remove it; 
but the mechanism to fix it, is itself, broke. Is that a fair observation?

Shobuz99

---

### Post by Bashing-om on 2013-08-17
Shobuz99; dpkg tools, yes.. going round and round...
Let's look at this from the package manager's point of view.
Baseline files ->
what shows up:
```

lsof /var/lib/dpkg/lock ##to make sure nothing is locked.
ls -la /var/lib/dpkg/info
ls -la /var/lib/dpkg/updates/
ls -la /var/cache/apt/archives/
cat /var/lib/dpkg/status

```

Maybe the PM is all confused and needs a bit of direction ?

[INDENT][INDENT]we all need help sometimes
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-17
> **Bashing-om said:**
> Shobuz99; dpkg tools, yes.. going round and round...
Let's look at this from the package manager's point of view.
Baseline files ->
what shows up:
```

lsof /var/lib/dpkg/lock ##to make sure nothing is locked.
ls -la /var/lib/dpkg/info
ls -la /var/lib/dpkg/updates/
ls -la /var/cache/apt/archives/
cat /var/lib/dpkg/status

```

Maybe the PM is all confused and needs a bit of direction ?

[INDENT][INDENT]we all need help sometimes
[/INDENT][/INDENT]

Ok. The output for 
```
rick@rick-desktop:~$ lsof /var/lib/dpkg/lock
rick@rick-desktop:~$ ls -la /var/lib/dpkg/updates/
total 8
drwxr-xr-x 2 root root 4096 2013-08-16 17:31 .
drwxr-xr-x 8 root root 4096 2013-08-16 17:31 ..
rick@rick-desktop:~$ ls -la /var/cache/apt/archives/
total 240
drwxr-xr-x 3 root root 233472 2013-08-14 15:28 .
drwxr-xr-x 3 root root   4096 2013-08-16 17:32 ..
-rw-r----- 1 root root      0 2008-11-16 23:33 lock
drwxr-xr-x 2 root root   4096 2013-08-12 17:38 partial
rick@rick-desktop:~$ 

```
However I can't post all the output from 
```
ls -la /var/lib/dpkg/info
``` 
Because it fills up the terminal screen. I can't scroll back all the way..
What would be the switch to port the output of that command to a text file?
I don't remember... I only remember DOS commands... x > yz.txt or something like that...
I know it's embarrassing.... lol. I'm a waaaaay too old geek.
I need to also do that with the 
```
rick@rick-desktop:~$ cat /var/lib/dpkg/status

``` 
because it scrolls for quite a distance. Lots of output...

Thanks
shobuz99

---

### Post by Bashing-om on 2013-08-17
Shobuz99; Not to be that-a-way ( embarrassing);

When one has no need to know ... one does not know... always fixable !
Situation at hand is looking for files in relation to Netflix and it's aliases ...
I hope the package manager IS holding out on us .. 
for that long output of a command .. just to look -> do:
```

ls -la /var/lib/dpkg/info | less
cat /var/lib/dpkg/status | less

```
which takes the output of the "ls" command and inputs that into the paging utility "less".
There are other means to search for strings within a file .. but;
Seeing as how we have nothing definite to search for, best means I know of, -- take a slow gander at   all of it ..
Unless you see something that you do not understand .. there is no need at this time to post it back ... now if you do find Netflix/wine-compholio or others of interest .. I do intend to remove that entire stanza (in the status file) ,, if it is in "/var/lib/dpkg/info" will have to think about what action to recommend.

[INDENT][INDENT]believe me I have been intent on finding a solution and remain committed to this end
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-18
> **Bashing-om said:**
> Shobuz99; Not to be that-a-way ( embarrassing);

When one has no need to know ... one does not know... always fixable !
Situation at hand is looking for files in relation to Netflix and it's aliases ...
I hope the package manager IS holding out on us .. 
for that long output of a command .. just to look -> do:
```

ls -la /var/lib/dpkg/info | less
cat /var/lib/dpkg/status | less

```
which takes the output of the "ls" command and inputs that into the paging utility "less".
There are other means to search for strings within a file .. but;
Seeing as how we have nothing definite to search for, best means I know of, -- take a slow gander at   all of it ..
Unless you see something that you do not understand .. there is no need at this time to post it back ... now if you do find Netflix/wine-compholio or others of interest .. I do intend to remove that entire stanza (in the status file) ,, if it is in "/var/lib/dpkg/info" will have to think about what action to recommend.

[INDENT][INDENT]believe me I have been intent on finding a solution and remain committed to this end
[/INDENT][/INDENT]

Thank you for the words of encouragement.
I tried the "ls -la /var/lib/dpkg/info | less" command first. 
I looked for "netflix" "wine-compholio" and "wine-browser-installer".
Did not see any of them...however, I wasn't aware of the search option.
Then I tried the "cat /var/lib/dpkg/status | less" command. 
At first I was frustrated by the amount of packages to sort through...
Then I discovered the search option and searched for netflix... JACKPOT!:

```
Package: netflix-desktop
Status: **[COLOR="#B22222"]deinstall ok installed[/COLOR]**
Priority: optional
Section: video
Installed-Size: 88
Maintainer: Erich E. Hoover <ehoover@mines.edu>
Architecture: all
Version: 0.7.0~lucid
Depends: wine-browser-installer
Pre-Depends: dpkg (>= 1.14.12ubuntu3)
Description: provides a convient tool that downloads and installs all of the components necessary to run Netflix Desktop under Wine.
 This includes the Windows version of Mozilla Firefox and Microsoft Silverlight v4. The package also includes some convience settings to integrate  into Firefox in such a way that everything feels like a native Ubuntu application.
 .
 Neither this package or its author is affliated with, endorsed, provided, or supported in any way by
 .
 Netflix Desktop is a trademark of
 Mozilla and Mozilla Firefox are trademarks of the Mozilla Corporation.
 Microsoft and Microsoft Silverlight are trademarks of the Microsoft Corporation.

```

Next I searched for Wine-Browser-Installer:

```
Package: wine-browser-installer
Status: **[COLOR="#B22222"]install ok installed[/COLOR]**
Priority: optional
Section: video
Installed-Size: 980
Maintainer: Erich E. Hoover <ehoover@mines.edu>
Architecture: amd64
Source: netflix-desktop
Version: 0.7.0~lucid
Replaces: netflix-desktop (<< 0.6.0~)
Depends: wine-compholio (>= 1.5.19~lucid1), ttf-mscorefonts-installer, mesa-utils, wget, zenity
Pre-Depends: dpkg (>= 1.14.12ubuntu3)
Breaks: netflix-desktop (<< 0.6.0~)
Description: The Wine Browser Installer provides a tool for multiple packages to provide access to web services that can be run with Mozilla Firefox under Wine.
 .
 Mozilla and Mozilla Firefox are trademarks of the Mozilla Corporation.
Multi-Arch: allowed


```

Next I searched for wine-compholio:

```
Package: wine-compholio
Status: **[COLOR="#B22222"]deinstall reinstreq half-installed[/COLOR]**
Priority: optional
Section: otherosfs
Installed-Size: 140672
Maintainer: Erich E. Hoover <ehoover@mines.edu>
Architecture: amd64
Version: 1.5.30~lucid
Config-Version: 1.5.30~lucid
Provides: wine-compholio
Depends: ia32-libs (>= 1.6), lib32asound2 (>> 1.0.14), libc6-i386 (>= 2.6-1), lib32nss-mdns (>= 0.10-3), libasound2-plugins, libncurses5
Pre-Depends: dpkg (>= 1.14.12ubuntu3)
Recommends: gettext, libcapi20-3, libcups2, libdbus-1-3, libfontconfig1 | libfontconfig, libfreetype6, libgif4, libgnutls26, libgphoto2-2 (>= 2.4.6), libgphoto2-port0 (>= 2.4.6), libjpeg8, libopenal1 (>= 1:1.12), libosmesa6, libpng12-0, libpulse0, libsane, libssl1.0.0, libtiff4, libv4l-0, libxcomposite1, libxcursor1, libxi6, libxinerama1, libxrandr2, libxrender1, libxslt1.1, libxt6, libxxf86vm1, unixodbc
Description: The Compholio Edition is a special build of the popular Wine software
 with patches representing my current staging tree for Wine.
 Currently these patches fix:
  * Netflix on Firefox hangs with loading bar at 100% (Bug 31993).
  * Netflix on Firefox fails with Internet Connection Problem when loading bar is
 at 99% (Bug 31858).
 .
 Microsoft Windows Compatibility Layer (Binary Emulator and Library)
 Wine is a compatibility layer for running Windows applications on Linux.
 Applications are run at full speed without the need of cpu emulation. Wine
 does not require Microsoft Windows, however it can use native system dll
 files in place of its own if they are available.
 .
 This package includes a program loader for running unmodified Windows executables
 as well as the Wine project's free version of the Windows API for running programs
 ported from Windows.
 .
 This package is based on a recent Wine beta.  While many more applications will
 work, there may be some loss of functionality compared with the stable release
 provided by the regular wine package.
Multi-Arch: foreign
Original-Maintainer: Scott Ritchie <scottritchie@ubuntu.com>

```


So then I went back to the "info" command and did a search.
And to my surprise, NONE of those 3 packages were listed in the "info" list.
I searched through it for each package. Results: "**Pattern not found. (press RETURN)**"

So... What does that mean? I am intrigued now!!

Shobuz99

---

### Post by Bashing-om on 2013-08-18
Shobuz99; OK !

We are going to say that things got done behind the package manager's back .. such that the package manager was not aware of what had changed; thus the data base does not reflect what is true.
So, let's fix that data base !
Make sure - once more - that none of those packages/files exist on the system .. then:
Edit the file /var/lib/dpkg/status , look for the listing for the removed package/files, remove the entire info stanza for those packages.
Save the file "/var/lib/dpkg/status" ...->
Now let us see if the package manager is happy;
```

sudo apt-get update
sudo apt-get upgrade

```
AND see about any further cleanup to be done,

[INDENT][INDENT][INDENT]are we there yet
[/INDENT][/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-18
You give me way too much credit. :-)

1) What command do I use to once again,*"Make sure - once more - that none of those packages/files exist on the system .."*
2) I assume I edit the "Status" file using gedit; "sudo gedit /var/lib/dpkg/status" correct?
3) **What do I change in the Status file as I edit it**?

I want to do this gently and not make any mistakes. 
I've dealt with DB's before and editing them can be tricky!

So please indulge me with some commands to get going.
I'll do the work and get the results.
I don't want to guess what to do, at this point, though.

thanks
Shobuz99

---

### Post by philinux on 2013-08-18
OT.

Robert Fripp is an awesome guitarist.  Still love 21st century schizoid man. I got the vinyl.

---

### Post by Bashing-om on 2013-08-18
Shobuz99; Hey .. credit .. you are doing well, you have come a long way and we have learned a lot ...
Now we know that    "/var/lib/dpkg/status" data base is not true ... for a fact .. we know all those files are gone bye-bye.
Edit the file: yes with "gedit" -> always make it a habit to make a backup first of any file you are editing .. Murphy's Law always applies !
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-old
gksudo gedit  /var/lib/dpkg/status

```
you get admin rights to change a system file .."gksudo" is the graphical equivalent to do so in a GUI application.
As an example, for every file in that database that you find relating to Netflix .. remove that whole paragraph (stanza)
- highlight it and choose "cut" from the context right click options-
> 
[email]x@lists.debian.org[/email]>

Package: tcpd
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 111
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Source: tcp-wrappers
Version: 7.6.q-24
Replaces: libwrap0 (<< 7.6-8)
Depends: libc6 (>= 2.4), libwrap0 (>= 7.6-4~)
Description: Wietse Venema's TCP wrapper utilities
 Wietse Venema's network logger, also known as TCPD or LOG_TCP.
 .
 These programs log the client host name of incoming telnet,
 ftp, rsh, rlogin, finger etc. requests.
 .
 Security options are:
  - access control per host, domain and/or service;
  - detection of host name spoofing or host address spoofing;
  - booby traps to implement an early-warning system.
Original-Maintainer: Marco d'Itri <md@linux.it>

Package: libnotify-bin
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 68

Let's say the package we are interested in "fixing" is tcpd ....we would "cut" out everything from the end of  "x@lists.debian.org>" starting at "Package: tcpd" removing all until the start of the next package info section, in this case -" Package: libnotify-bin".

Do this for each and every instance of a reference to any files associated with Netflix. As those files no longer exist on the system, manually updating the data base is the thing to do.
In a separate terminal just do a find for that instance of the "filename" to make positive sure it is gone gone - or make it so - and delete that stanza !

Slow, tedious and time consuming ... but it gets the job done ... one item at a time.

[INDENT][INDENT]progressing toward the end
 [/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-18
> **philinux said:**
> OT.

Robert Fripp is an awesome guitarist.  Still love 21st century schizoid man. I got the vinyl.

OT reply: 
Cool! I bought the vinyl shortly after it came out. 
Then lost it and didn't get another copy until that late 1970's.
I also bought the 2nd album "In The_Wake_of_Poseidon" also in the late 1970's.

"In The_Wake_of_Poseidon" has a similar theme and structure to 21st Century Schizoid Man, musically.
I was always enamoured by the fusion of rock, jazz, and folk in these two albums.
Being a musician and lead vocalist myself (since 1964), I had wanted to perform a cover of some of those tunes
with some competent players....but never found anyone good enough to do that music. 
I mean who can copy Robert Fripp? Seriously.
So I stuck with Rock_&_Roll, R&B, and Classic Rock.

Thanks for the OT comment. :-)   And for your help with this predicament of mine.
I must acknowledge Bashing-Om as a real life saver here. He's stuck with me for 2 weeks!!!!
This is unprecedented. I sincerely appreciate his help and knowledge, as an old geek from the days
of the "planet IBM mainframe" Pre-PC era (1974)...

Shobuz99

---

### Post by Shobuz99 on 2013-08-18
Ok. Here is what I did.
I created a backup of 'Status', as Status-old.
I edited Status and I followed your instructions and successfully removed ALL packages that referred to Netflix.
There were only 3: NetFlix-desktop, Wine-Compholio, and Wine-Browser-Installer.

Next I ran "sudo apt-get update" All went well.
Next I ran:

```
rick@rick-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnome-terminal: Depends: gnome-terminal-data (>= 2.30) but it is not installed
                  Depends: gnome-terminal-data (< 2.31) but it is not installed
  libgnomevfs2-common: Depends: gnome-mime-data but it is not installed
E: Unmet dependencies. Try using -f. 
```

I decided to continue and run:

```
rick@rick-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libopal3.6.6 libxml++2.6-2 python-twisted-mail ubufox
  python-twisted-lore odbcinst1debian1 python-twisted-news
  libfile-find-rule-perl python-twisted-conch python-twisted-words libslv2-9
  libcapi20-3 odbcinst python-twisted unixodbc gettext rtkit libosmesa6 cvs
  libffado2 libtext-glob-perl libgnomecanvasmm-2.6-1c2a libpt2.6.5 liblo7
  libaubio2 python-twisted-runner liblrdf0 python-pyasn1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-mime-data gnome-terminal-data
The following NEW packages will be installed:
  gnome-mime-data gnome-terminal-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 452kB of archives.
After this operation, 14.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://old-releases.ubuntu.com/ubuntu/ lucid/main gnome-mime-data 2.18.0-1 [362kB]
Get:2 http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main gnome-terminal-data 2.30.2-0ubuntu1 [90.1kB]
Fetched 452kB in 1s (381kB/s)               
Selecting previously deselected package gnome-mime-data.
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre-headless' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
rick@rick-desktop:~$  
```

I assumed that icedtea was "missing", so I ran a search in 'Status' where I found:
```
Package: icedtea-netx
Status: install ok installed
Priority: extra
Section: java
Installed-Size: 768
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: icedtea-web
Version: 1.2.3-0ubuntu0.10.04.1
Replaces: openjdk-6-jre (<< 6b21.2~pre1-1~), openjdk-6-jre-headless (<< 6b18-1.8.7-3)
Depends: openjdk-6-jre (>= 6b23~pre10~) | openjdk-7-jre
Conflicts: openjdk-6-jre (<< 6b21.2~pre1-1~), openjdk-6-jre-headless (<< 6b18-1.8.7-3)
Conffiles:
 /etc/icedtea-web/javaws.policy 01f40304afd5978f8cae1f891190ec17
Description: NetX - implementation of the Java Network Launching Protocol (JNLP)
 NetX provides a drop-in replacement for javaws (Java Web Start). Since
 upstream NetX is dormant, IcedTea is hosting and modifying the sources
 in the IcedTea-Web directory.
 .
 IcedTea's NetX currently supports verification of signed jars, trusted
 certificate storing, system certificate store checking, and provides
 the services specified by the jnlp API.
Homepage: http://icedtea.classpath.org/wiki/IcedTea-Web
Original-Maintainer: OpenJDK Team <openjdk@lists.launchpad.net> 
```

I also searched for "openjdk" in 'status':

```
Package: icedtea-netx
Status: install ok installed
Priority: extra
Section: java
Installed-Size: 768
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: icedtea-web
Version: 1.2.3-0ubuntu0.10.04.1
Replaces: openjdk-6-jre (<< 6b21.2~pre1-1~), openjdk-6-jre-headless (<< 6b18-1.8.7-3)
Depends: openjdk-6-jre (>= 6b23~pre10~) | openjdk-7-jre
Conflicts: openjdk-6-jre (<< 6b21.2~pre1-1~), openjdk-6-jre-headless (<< 6b18-1.8.7-3)
Conffiles:
 /etc/icedtea-web/javaws.policy 01f40304afd5978f8cae1f891190ec17
Description: NetX - implementation of the Java Network Launching Protocol (JNLP)
 NetX provides a drop-in replacement for javaws (Java Web Start). Since
 upstream NetX is dormant, IcedTea is hosting and modifying the sources
 in the IcedTea-Web directory.
 .
 IcedTea's NetX currently supports verification of signed jars, trusted
 certificate storing, system certificate store checking, and provides
 the services specified by the jnlp API.
Homepage: http://icedtea.classpath.org/wiki/IcedTea-Web
Original-Maintainer: OpenJDK Team <openjdk@lists.launchpad.net> 
```

Next I looked in 'info' for openjdk:

```
-rw-r--r-- 1 root root    872 2013-04-25 12:53 openjdk-6-jre-headless.conffiles
-rw-r--r-- 1 root root   9116 2013-05-08 14:53 openjdk-6-jre-headless.list
-rw-r--r-- 1 root root   6555 2013-04-25 12:53 openjdk-6-jre-headless.md5sums
-rwxr-xr-x 1 root root   3652 2013-04-25 12:53 openjdk-6-jre-headless.postinst
-rwxr-xr-x 1 root root    319 2013-04-25 12:53 openjdk-6-jre-headless.postrm
-rwxr-xr-x 1 root root    721 2013-04-25 12:53 openjdk-6-jre-headless.preinst
-rwxr-xr-x 1 root root    668 2013-04-25 12:53 openjdk-6-jre-headless.prerm
-rwxr-xr-x 1 root root    265 2013-05-12 08:06 openjdk-6-jre-lib.md5sums
-rw-r--r-- 1 root root      0 2013-05-11 16:54 openjdk-6-jre-lib.postinst
-rw-r--r-- 1 root root   2276 2013-05-08 14:53 openjdk-6-jre.list
-rw-r--r-- 1 root root   1594 2013-04-25 12:53 openjdk-6-jre.md5sums
-rwxr-xr-x 1 root root   1678 2013-04-25 12:53 openjdk-6-jre.postinst
-rwxr-xr-x 1 root root    160 2013-04-25 12:53 openjdk-6-jre.postrm
-rwxr-xr-x 1 root root    832 2013-04-25 12:53 openjdk-6-jre.preinst
-rwxr-xr-x 1 root root    226 2013-04-25 12:53 openjdk-6-jre.prerm

```

and icedtea:

```

-rwxr-xr-x 1 root root    574 2013-05-12 08:06 icedtea-6-jre-cacao.md5sums
-rw-r--r-- 1 root root     31 2013-04-17 19:28 icedtea-netx.conffiles
-rw-r--r-- 1 root root   1964 2013-04-19 19:34 icedtea-netx.list
-rw-r--r-- 1 root root   1649 2013-04-17 19:28 icedtea-netx.md5sums
-rwxr-xr-x 1 root root   1904 2013-04-17 19:28 icedtea-netx.postinst
-rwxr-xr-x 1 root root    765 2013-04-17 19:28 icedtea-netx.preinst
-rwxr-xr-x 1 root root    357 2013-04-17 19:28 icedtea-netx.prerm

```

So...Both pkgs exist in both places info and status...
Why is there an error and an "empty filename" error, too???

I bet you have an answer.... I hope you have an answer!!
..... so close but yet so far away.... :-(
Shobuz99

[COLOR="#0000CD"][B]UPDATE: Update manager WORKS!!!!! No Error!!! 

It asks me to install two pkgs: "gnome-terminal-data" and "gnome-mime-data"
The weird thing is that the download size says "0 KB"

I will wait for your instructions before I "install" those packages from Update Manager!!!  [/B][/COLOR]

---

### Post by Bashing-om on 2013-08-18
Shobuz99; Hey hey !

Install those suckers ! Letting the Package Manager do it's thing ... taking care of the dependencies.
as to why we are back to the package manager hollering about 
icedtea-6-jre-cacao
openjdk-6-jre-lib
presently do not know .. as we took care of them some time back .. 

[INDENT][INDENT]now, are we there yet[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-18
> **Bashing-om said:**
> Shobuz99; Hey hey !

Install those suckers ! Letting the Package Manager do it's thing ... taking care of the dependencies.
as to why we are back to the package manager hollering about 
icedtea-6-jre-cacao
openjdk-6-jre-lib
presently do not know .. as we took care of them some time back .. 

[INDENT][INDENT]now, are we there yet[/INDENT][/INDENT]

ok. It won't install. here are the two images of the error messages:

1 image is from Synaptic and 1 is from Update mgr.

I recall that we fixed those, right????

Shobuz99

---

### Post by Bashing-om on 2013-08-18
Shobuz99; Well .. 
I do wonder how come those are coming back to haunt us ... try:
```

sudo dpkg-reconfigure openjdk-6-jre-lib

```
See what results .. before taking 1 next step.

[INDENT][INDENT]4 steps forward and 2 back[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-18
> **Bashing-om said:**
> Shobuz99; Well .. 
I do wonder how come those are coming back to haunt us ... try:
```

sudo dpkg-reconfigure openjdk-6-jre-lib

```
See what results .. before taking 1 next step.

[INDENT][INDENT]4 steps forward and 2 back[/INDENT][/INDENT]

```
rick@rick-desktop:~$ sudo dpkg-reconfigure openjdk-6-jre-lib
[sudo] password for rick: 
rick@rick-desktop:~$

```
I tried running Update Manager and still get the "broken package" message previously.

No steps forward or back...just in place.

Shobuz99

---

### Post by Bashing-om on 2013-08-18
Shobuz99; HUH ?? -> no hints !

let's see what apt-get has to convey
```

sudo apt-get install --reinstall openjdk-6-jre-lib

```

[INDENT][INDENT]too close to quit now
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-18
```
rick@rick-desktop:~$ sudo apt-get install --reinstall openjdk-6-jre-lib
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome-terminal: Depends: gnome-terminal-data (>= 2.30) but it is not going to be installed
                  Depends: gnome-terminal-data (< 2.31) but it is not going to be installed
  libgnomevfs2-common: Depends: gnome-mime-data but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
rick@rick-desktop:~$  
```

This looks to me, like a catch-22. Gnome won't install because there are broken pkgs,
and the broken packages can't be fixed until gnome is installed..... Have i got that right?


Shobuz99

---

### Post by Bashing-om on 2013-08-18
Shobuz99; Uhmm..
let's look at what it is hollering about:
```

dpkg -l gnome-terminal-data
apt-cache show gnome-terminal-data

``` and think about forcing the installation (???)

Also what results trying to --reconfigure and re-install "icedtea-6-jre-cacao" .. can not imagine it so .. but is there something in common here with the terminal emulator (as above ) ???????/

[INDENT][INDENT]we be look'n once more
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-18
Ok. here goes:

```
rick@rick-desktop:~$ dpkg -l gnome-terminal-data
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  gnome-terminal <none>         (no description available)
rick@rick-desktop:~$ 
```

Next:
```
rick@rick-desktop:~$ apt-cache show gnome-terminal-data
Package: gnome-terminal-data
Priority: optional
Section: gnome
Installed-Size: 9256
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Original-Maintainer: Guilherme de S. Pastore <gpastore@debian.org>
Architecture: all
Source: gnome-terminal
Version: 2.30.2-0ubuntu1
Depends: gconf2 (>= 2.10.1-2)
Recommends: gnome-terminal
Filename: pool/main/g/gnome-terminal/gnome-terminal-data_2.30.2-0ubuntu1_all.deb
Size: 90134
MD5sum: 50345a8545a5358bd593f2241bd61317
SHA1: 74b267669b57cb9faac7217dcf0c1ffa98ae3312
SHA256: 8f7ce8cc40249e6f86d79ecc628c17b177f3ea6dc730ebccb39715b1b98e9b8b
Description: Data files for the GNOME terminal emulator
 GNOME Terminal is a terminal emulation application that you can use to
 perform the following actions:
  - Access a UNIX shell in the GNOME environment.
  - Run any application that is designed to run on VT102, VT220, and xterm
 terminals.
 .
 This package contains data, help files and localization settings for
 gnome-terminal, the GNOME terminal emulator application.
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: ubuntu-desktop, edubuntu-desktop, ubuntu-netbook

Package: gnome-terminal-data
Priority: optional
Section: gnome
Installed-Size: 9088
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Original-Maintainer: Guilherme de S. Pastore <gpastore@debian.org>
Architecture: all
Source: gnome-terminal
Version: 2.29.6-0ubuntu5
Depends: gconf2 (>= 2.10.1-2)
Recommends: gnome-terminal
Filename: pool/main/g/gnome-terminal/gnome-terminal-data_2.29.6-0ubuntu5_all.deb
Size: 89756
MD5sum: c1194efd2c14951061a1cbfd66284f7f
SHA1: fbb8acafe0cb07c0c59f446ca365a3960a8e143c
SHA256: 7e18951069f1378ee25fe5b11c4c8750fe8a3c6fb179a07b3bb66fa2590db67f
Description: Data files for the GNOME terminal emulator
 GNOME Terminal is a terminal emulation application that you can use to
 perform the following actions:
  - Access a UNIX shell in the GNOME environment.
  - Run any application that is designed to run on VT102, VT220, and xterm
 terminals.
 .
 This package contains data, help files and localization settings for
 gnome-terminal, the GNOME terminal emulator application.
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: ubuntu-desktop, edubuntu-desktop, ubuntu-netbook

rick@rick-desktop:~$ 

```

Ok. Next?

shobuz99

---

### Post by Bashing-om on 2013-08-18
Shobuz99; try ->

```

sudo apt-get install gnome-terminal

```
see what results .. got a coverall tucked away ..may have to resort to it. 
[INDENT]try'n to stay within the PM[/INDENT]

---

### Post by Shobuz99 on 2013-08-18
Ok.
```
rick@rick-desktop:~$ sudo apt-get install gnome-terminal
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-terminal is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome-terminal: Depends: gnome-terminal-data (>= 2.30) but it is not going to be installed
                  Depends: gnome-terminal-data (< 2.31) but it is not going to be installed
  libgnomevfs2-common: Depends: gnome-mime-data but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
rick@rick-desktop:~$ 

```

Will apt-get -f install really work now, even though there was an error last time?

I'm feelin' loopy...lol 

Shobuz99

---

### Post by Bashing-om on 2013-08-18
Shobuz99; try ->

```

sudo apt-get --fix-missing install

```

still do not want to force the issue ...

---

### Post by Bashing-om on 2013-08-19
Shobuz99;

Done for the night .. and .. on the AM I must climb onto my tractor and do some disk work .. be later before I get back to the keyboard.

Will take this back up at that time.

[INDENT][INDENT]we will, we will
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-19
> **Bashing-om said:**
> Shobuz99; try ->

```

sudo apt-get --fix-missing install

```

still do not want to force the issue ...

Ok. well, we might have to "force" it after all...

```
rick@rick-desktop:~$ sudo apt-get --fix-missing install
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnome-terminal: Depends: gnome-terminal-data (>= 2.30) but it is not installed
                  Depends: gnome-terminal-data (< 2.31) but it is not installed
  [COLOR="#B22222"]libgnomevfs2-common[/COLOR]: Depends: gnome-mime-data but it is not installed
E: Unmet dependencies. Try using -f.

```

[B]Update: I searched for the file: [COLOR="#B22222"]libgnomevfs2-common[/COLOR] using the same commands for "info" and "status".
I found it listed as a package, in "status", and the files were listed in the "info" search.
So...I don't understand why Update Manager has such an issue? Do you?[/B]

---

### Post by Bashing-om on 2013-08-19
Shobuz99;

Let's see if we can help the package manager make up it's mind.

```

sudo apt-get install gnome-terminal-data_2.30.2-0ubuntu1

```
seems to fit the requirements:

gnome-terminal-data (>= 2.30)
gnome-terminal-data (< 2.31)
[INDENT]small steps, again ... but getting there[/INDENT]

---

### Post by Shobuz99 on 2013-08-19
> **Bashing-om said:**
> Shobuz99;

Let's see if we can help the package manager make up it's mind.

```

sudo apt-get install gnome-terminal-data_2.30.2-0ubuntu1

```
seems to fit the requirements:

gnome-terminal-data (>= 2.30)
gnome-terminal-data (< 2.31)
[INDENT]small steps, again ... but getting there[/INDENT]

Uh...:
```
rick@rick-desktop:~$ sudo apt-get install gnome-terminal-data_2.30.2-0ubuntu1
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-terminal-data_2.30.2-0ubuntu1
rick@rick-desktop:~$  
```

Hmmm? 

Shobuz99

---

### Post by Bashing-om on 2013-08-19
Shobuz99; -???-

Not making any sense to me either !
What results:
```

apt-cache search gnome-terminal-data_2.30.2-0ubuntu1
apt-cache search gnome-terminal-data
apt-cache show gnome-terminal-data

```
Maybe (?) that version _2.30.2-0ubuntu1 is not available, though this: "Filename: pool/main/g/gnome-terminal/gnome-terminal-data_2.30.2-0ubuntu1_all.deb" says otherwise !

round and around we go, hopefully a spiral; we will get to the end of it.

---

### Post by Shobuz99 on 2013-08-19
> **Bashing-om said:**
> Shobuz99; -???-

Not making any sense to me either !
What results:
```

apt-cache search gnome-terminal-data_2.30.2-0ubuntu1
apt-cache search gnome-terminal-data
apt-cache show gnome-terminal-data

```
Maybe (?) that version _2.30.2-0ubuntu1 is not available, though this: "Filename: pool/main/g/gnome-terminal/gnome-terminal-data_2.30.2-0ubuntu1_all.deb" says otherwise !

round and around we go, hopefully a spiral; we will get to the end of it.

Ok. First:
```
rick@rick-desktop:~$ apt-cache search gnome-terminal-data_2.30.2-0ubuntu1
rick@rick-desktop:~$ 

```

Next:
```
rick@rick-desktop:~$ apt-cache search gnome-terminal-data
gnome-terminal-data - Data files for the GNOME terminal emulator
rick@rick-desktop:~$ 

```

and 3rd:

```
rick@rick-desktop:~$ apt-cache show gnome-terminal-data
Package: gnome-terminal-data
Priority: optional
Section: gnome
Installed-Size: 9256
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Original-Maintainer: Guilherme de S. Pastore <gpastore@debian.org>
Architecture: all
Source: gnome-terminal
Version: 2.30.2-0ubuntu1
Depends: gconf2 (>= 2.10.1-2)
Recommends: gnome-terminal
Filename: pool/main/g/gnome-terminal/gnome-terminal-data_2.30.2-0ubuntu1_all.deb
Size: 90134
MD5sum: 50345a8545a5358bd593f2241bd61317
SHA1: 74b267669b57cb9faac7217dcf0c1ffa98ae3312
SHA256: 8f7ce8cc40249e6f86d79ecc628c17b177f3ea6dc730ebccb39715b1b98e9b8b
Description: Data files for the GNOME terminal emulator
 GNOME Terminal is a terminal emulation application that you can use to
 perform the following actions:
  - Access a UNIX shell in the GNOME environment.
  - Run any application that is designed to run on VT102, VT220, and xterm
 terminals.
 .
 This package contains data, help files and localization settings for
 gnome-terminal, the GNOME terminal emulator application.
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: ubuntu-desktop, edubuntu-desktop, ubuntu-netbook

Package: gnome-terminal-data
Priority: optional
Section: gnome
Installed-Size: 9088
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Original-Maintainer: Guilherme de S. Pastore <gpastore@debian.org>
Architecture: all
Source: gnome-terminal
Version: 2.29.6-0ubuntu5
Depends: gconf2 (>= 2.10.1-2)
Recommends: gnome-terminal
Filename: pool/main/g/gnome-terminal/gnome-terminal-data_2.29.6-0ubuntu5_all.deb
Size: 89756
MD5sum: c1194efd2c14951061a1cbfd66284f7f
SHA1: fbb8acafe0cb07c0c59f446ca365a3960a8e143c
SHA256: 7e18951069f1378ee25fe5b11c4c8750fe8a3c6fb179a07b3bb66fa2590db67f
Description: Data files for the GNOME terminal emulator
 GNOME Terminal is a terminal emulation application that you can use to
 perform the following actions:
  - Access a UNIX shell in the GNOME environment.
  - Run any application that is designed to run on VT102, VT220, and xterm
 terminals.
 .
 This package contains data, help files and localization settings for
 gnome-terminal, the GNOME terminal emulator application.
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: ubuntu-desktop, edubuntu-desktop, ubuntu-netbook

rick@rick-desktop:~$ 
```

---

### Post by Bashing-om on 2013-08-19
Shobuz99; Sorry for the delay;
Did not timely see your response !

Still not making any sense to me .. I can be blind and terribly afflicted with "tunnel vision" .. but,

What results:
```

dpkg -l gnome-terminal-data
dpkg -l "gnome-terminal-data*"

```
see if that gives me an inkling of what is not going on .. and some direction to the process of thought.

[INDENT][INDENT]sometimes I do wonder, others I just do not know
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-20
> **Bashing-om said:**
> Shobuz99; Sorry for the delay;
Did not timely see your response !

Still not making any sense to me .. I can be blind and terribly afflicted with "tunnel vision" .. but,

What results:
```

dpkg -l gnome-terminal-data
dpkg -l "gnome-terminal-data*"

```
see if that gives me an inkling of what is not going on .. and some direction to the process of thought.

[INDENT][INDENT]sometimes I do wonder, others I just do not know
[/INDENT][/INDENT]

Ok. here's the results of both:

```
rick@rick-desktop:~$ dpkg -l gnome-terminal-data
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
**un  gnome-terminal <none>         (no description available)**
rick@rick-desktop:~$ dpkg -l "gnome-terminal-data*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
**un  gnome-terminal <none>         (no description available)**
rick@rick-desktop:~$ 

```

Ok. Let me first say how much I respect your efforts and your wisdom, because I do.

I am losing patience now, and I thought I'd recommend an idea,
and see if you agree or if not, tell what I would break if I do it.

First, The "openjdk" and "icedtea" issues have come back, as far as I can see.
Why? I don't know.
What I would like to do, since Synaptic and Update Manager are at least functioning to some degree,
is to "Mark those packages for Complete Removal" using Synaptic.

Second, I want to include "gnome-terminal-data" in that group that gets removed.
In my opinion, I should be able to install them from scratch once I reboot and open Synaptic Pkg manager.

Problem: I don't have the experience to know if those two actions will break something beyond fixing.
So, I DON'T want to do either thing if I will suffer irrecoverable damage to 10.04 LTS, 
before I have had a chance to backup the data on this drive and install 13.04 Lubuntu or whatever.

Please indulge my overly simplified questions and plans, and let me know if I'm going down the wrong path, ok?

I apologize if this all sounds critical toward you... It's absolutely NOT. I completely trust what you have done for me, so far.
I am just running out of patience. I want to fix this and get busy with backups and moving up.

Honestly and sincerely,

Shobuz99

---

### Post by bapoumba on 2013-08-20
I have not read the whole thread, followed it by notifications.

Do you have ubuntu-desktop installed ?

---

### Post by Shobuz99 on 2013-08-20
> **bapoumba said:**
> I have not read the whole thread, followed it by notifications.

Do you have ubuntu-desktop installed ?

What would be the best way to confirm that? 
Is it a specific package? If so, I could search the status or info output and look for it.

I'm sure it must be obvious, but I don't know if I have ubuntu-desktop installed..

Let me examine it and I'll write back, or edit an update to this post.

UPDATE: I could not find "ubuntu-desktop" installed as a package when I searched through "status" or "info"
using these commands: ```
cat /var/lib/dpkg/status | less
``` OR ```
ls -la /var/lib/dpkg/info | less
```
                                 





Shobuz99

---

### Post by bapoumba on 2013-08-20
It is a meta package :
**apt-cache show ubuntu-desktop**

---

### Post by Shobuz99 on 2013-08-20
> **bapoumba said:**
> It is a meta package :
**apt-cache show ubuntu-desktop**

Apparently, I DO have ubuntu-desktop installed:

```
Package: ubuntu-desktop
Priority: optional
Section: metapackages
Installed-Size: 60
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Architecture: amd64
Source: ubuntu-meta
Version: 1.197
Depends: alacarte, alsa-base, alsa-utils, anacron, bc, ca-certificates, checkbox-gtk, cups, cups-bsd, cups-client, dc, desktop-file-utils, doc-base, eog, evince, file-roller, foomatic-db, foomatic-db-engine, foomatic-filters, gcalctool, gconf-editor, gdebi, gdm, gedit, genisoimage, ghostscript-x, gnome-about, gnome-applets, gnome-control-center, gnome-icon-theme, gnome-media, gnome-menus, gnome-nettool, gnome-panel, gnome-power-manager, gnome-session, gnome-session-canberra, gnome-system-monitor, gnome-system-tools, gnome-terminal, gnome-themes-selected, gnome-themes-ubuntu, gnome-utils, gstreamer0.10-alsa, gstreamer0.10-plugins-base-apps, gstreamer0.10-pulseaudio, gtk2-engines, gtk2-engines-pixbuf, gucharmap, indicator-applet-session, inputattach, language-selector, launchpad-integration, lftp, libgd2-xpm, libgl1-mesa-glx, libgnome2-perl, libpam-ck-connector, libsasl2-modules, libsdl1.2debian, libsdl1.2debian-pulseaudio, libxp6, metacity, nautilus, nautilus-sendto, notify-osd, openprinting-ppds, pnm2ppa, pulseaudio, pulseaudio-esound-compat, rarian-compat, screen, screensaver-default-images, seahorse, smbclient, software-center, software-properties-gtk, ssh-askpass-gnome, synaptic, system-config-printer-gnome, ttf-dejavu-core, ttf-freefont, ubuntu-artwork, ubuntu-sounds, unzip, update-manager, update-notifier, wireless-tools, wpasupplicant, x-ttcidfont-conf, xdg-user-dirs, xdg-user-dirs-gtk, xkb-data, xorg, xscreensaver-data, xscreensaver-gl, xterm, yelp, zenity, zip
Recommends: acpi-support, aisleriot, app-install-data-partner, apport-gtk, avahi-autoipd, avahi-daemon, bluez, bluez-alsa, bluez-cups, bluez-gstreamer, bogofilter, branding-ubuntu, brasero, brltty, brltty-x11, cdparanoia, compiz, computer-janitor-gtk, dvd+rw-tools, empathy, espeak, evolution, evolution-couchdb, evolution-exchange, evolution-indicator, evolution-plugins, evolution-webcal, example-content, f-spot, firefox, firefox-gnome-support, foo2zjs, gbrainy, gcc, gdm-guest-session, gnome-accessibility-themes, gnome-bluetooth, gnome-codec-install, gnome-disk-utility, gnome-mag, gnome-mahjongg, gnome-orca, gnome-screensaver, gnome-sudoku, gnome-user-guide, gnomine, gvfs-fuse, hplip, ibus, ibus-gtk, ibus-m17n, ibus-table, im-switch, indicator-messages, jockey-gtk, kerneloops-daemon, laptop-detect, libgail-gnome-module, libgl1-mesa-dri, libnss-mdns, libpam-gnome-keyring, libwmf0.2-7-gtk, linux-headers-generic, make, min12xxw, mousetweaks, nautilus-share, network-manager-gnome, network-manager-pptp, network-manager-pptp-gnome, onboard, openoffice.org-calc, openoffice.org-gnome, openoffice.org-help-en-us, openoffice.org-impress, openoffice.org-math, openoffice.org-style-human, openoffice.org-writer, pcmciautils, pitivi, plymouth-theme-ubuntu-logo, plymouth-x11, pm-utils-powersave-policy, policykit-desktop-privileges, pulseaudio-module-bluetooth, pulseaudio-module-gconf, pulseaudio-module-x11, pxljr, quadrapassel, rhythmbox, rhythmbox-ubuntuone-music-store, simple-scan, speech-dispatcher, splix, telepathy-idle, tomboy, totem, totem-mozilla, transmission-gtk, tsclient, ttf-indic-fonts-core, ttf-kacst-one, ttf-khmeros-core, ttf-lao, ttf-liberation, ttf-punjabi-fonts, ttf-takao-pgothic, ttf-thai-tlwg, ttf-unfonts-core, ttf-wqy-microhei, ubufox, ubuntu-docs, ubuntuone-client-gnome, usb-creator-gtk, vinagre, vino, wodim, xcursor-themes, xdg-utils
Filename: pool/main/u/ubuntu-meta/ubuntu-desktop_1.197_amd64.deb
Size: 31876
MD5sum: 65a745ef6456347d9271036bb47eb5ae
SHA1: 5bccc5fe6d85b059090c35a03161cf840a2ff565
SHA256: 35141b62e136ce5c71fa3578e4a209f38a436709daf45f428adc431f85e6075c
Description: The Ubuntu desktop system
 This package depends on all of the packages in the Ubuntu desktop system
 .
 It is also used to help ensure proper upgrades, so it is recommended that
 it not be removed.
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: ubuntu-desktop, edubuntu-desktop

rick@rick-desktop:~$ 

```

ok. what next?

Shobuz99

---

### Post by bapoumba on 2013-08-20
Ok, I've skimmed over the whole thread and if I try to summarize a little, you have 10.04, 32-bits install and got problems with wine. Is your sources.list still the same as in post #9 ? If not, please post it again.

Just so that there is a fresh pic of the problematic packages, what is the output to **sudo apt-get update** and **sudo apt-get dist-upgrade** ? Thanks.

---

### Post by Shobuz99 on 2013-08-20
> **bapoumba said:**
> Ok, I've skimmed over the whole thread and if I try to summarize a little, you have 10.04, 32-bits install and got problems with zwine. Is your sources.list still the same as in post #9 ? If not, please post it again.

Just so that there is a fresh pic of the problematic packages, what is the output to **sudo apt-get update** and **sudo apt-get dist-upgrade** ? Thanks.

Ok. you missed a key point: It's Ubuntu 10.04 LTS **64-bits**, installed, not 32-bits. 
I don't have problems with WINE.
As a matter of fact the problem was with Netflix/Wine-Compholio/Wine-Browser-Installer.
I wanted to remove it because it wouldn't update. That was the original reason for the request for help.
Initially i was told that 10.04 LTS had reached EOL in April or May, and that I should just upgrade.
Bashing-Om decided to help me repair things first, before I upgrade. 
He also helped me fix Synaptic Package Mgr so it will run.
It was hung up on errors with the "Netflix/Wine-Compholio/Wine-Browser-Installer" issue that has been resolved.

The problem now is that Pkg manager complains about "2 broken pkgs" and also tries to update 
the Gnome-terminal-data, etc. but fails.
WINE itself has been working fine. Am I confusing you? if so, that's not my intention, honestly.

Do you mean page #9? I don't see a sources.list On page 9. 
But here it is now:
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://old-releases.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://old-releases.ubuntu.com/ubuntu/ lucid universe
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://old-releases.ubuntu.com/ubuntu/ lucid multiverse
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://old-releases.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://old-releases.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb-src http://archive.canonical.com/ubuntu hardy partner


deb http://old-releases.ubuntu.com/ubuntu lucid-security main restricted
deb http://old-releases.ubuntu.com/ubuntu lucid-security universe
deb http://old-releases.ubuntu.com/ubuntu lucid-security multiverse
deb http://old-releases.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
# deb http://wine.budgetdedicated.com/apt karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" disabled on upgrade to karmic

```

```
 rick@rick-desktop:~$ sudo apt-get update
Hit http://old-releases.ubuntu.com lucid Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-updates Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-backports Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-proposed Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Hit http://old-releases.ubuntu.com lucid Release
Hit http://old-releases.ubuntu.com lucid-updates Release
Hit http://old-releases.ubuntu.com lucid-backports Release
Hit http://old-releases.ubuntu.com lucid-security Release
Hit http://old-releases.ubuntu.com lucid-proposed Release
Hit http://old-releases.ubuntu.com lucid/main Packages
Hit http://old-releases.ubuntu.com lucid/restricted Packages
Hit http://old-releases.ubuntu.com lucid/universe Packages
Hit http://old-releases.ubuntu.com lucid/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-updates/main Packages
Hit http://old-releases.ubuntu.com lucid-updates/restricted Packages
Hit http://old-releases.ubuntu.com lucid-updates/universe Packages
Hit http://old-releases.ubuntu.com lucid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-backports/main Packages
Hit http://old-releases.ubuntu.com lucid-backports/restricted Packages
Hit http://old-releases.ubuntu.com lucid-backports/universe Packages
Hit http://old-releases.ubuntu.com lucid-backports/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Packages
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/restricted Packages
Hit http://old-releases.ubuntu.com lucid-proposed/main Packages
Hit http://old-releases.ubuntu.com lucid-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/universe Packages
Reading package lists... Done
rick@rick-desktop:~$ 

```

```
rick@rick-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnome-terminal: Depends: gnome-terminal-data (>= 2.30) but it is not installed
                  Depends: gnome-terminal-data (< 2.31) but it is not installed
  libgnomevfs2-common: Depends: gnome-mime-data but it is not installed
E: Unmet dependencies. Try using -f.
rick@rick-desktop:~$   
```

Thanks
shobuz99

---

### Post by Bashing-om on 2013-08-20
Shobuz99; I have a plan..

While we await the esteemed bapoumba for his most welcome input and advisement.

I have been looking about in an install that I have "gnome-terminal" available .. and I have an approach, not that your idea to use synaptic is not good and viable - I trust synaptic -- just more accustomed to the command line. I prefer to know what is going on.
Working to resolve those dependencies let's look at the major one first. Show us:
```

apt-cache policy gnome-terminal-data

```
and then we will see what "/dpkg/status" has to relate ..

[INDENT][INDENT]so close, we can taste it[/INDENT][/INDENT]

---

### Post by bapoumba on 2013-08-20
Hello again !

Sorry I sneaked in but as I had separated your thread from the other one and posted in, I was subscribed and got a few of your exchanges. I have not all followed, that is why I asked for a little summary. I have no intention to step on Bashing-om toes, just trying to get a picture with the tools I'm used to :)

Please try
[B]sudo apt-get clean all
sudo apt-get dist-upgrade[/B]

If it asks for it at the end (like previously), run ```
sudo apt-get -f install
```

It will probably ask to run autoremove :
**sudo apt-get autoremove**

All the packages that give you trouble in the last 2 pages, I could find them in lucid repos, so you should have a way out.

---

### Post by Shobuz99 on 2013-08-20
> **Bashing-om said:**
> Shobuz99; I have a plan..

While we await the esteemed bapoumba for his most welcome input and advisement.

I have been looking about in an install that I have "gnome-terminal" available .. and I have an approach, not that your idea to use synaptic is not good and viable - I trust synaptic -- just more accustomed to the command line. I prefer to know what is going on.
Working to resolve those dependencies let's look at the major one first. Show us:
```

apt-cache policy gnome-terminal-data

```
and then we will see what "/dpkg/status" has to relate ..

[INDENT][INDENT]so close, we can taste it[/INDENT][/INDENT]

Results:

```
rick@rick-desktop:~$ apt-cache policy gnome-terminal-data
gnome-terminal-data:
  Installed: (none)
  Candidate: 2.30.2-0ubuntu1
  Version table:
     2.30.2-0ubuntu1 0
        500 http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Packages
     2.29.6-0ubuntu5 0
        500 http://old-releases.ubuntu.com/ubuntu/ lucid/main Packages
rick@rick-desktop:~$ 
```

This tells me what I suspected. I think the "openjdk" and the "icedtea" issues need to be resolved 
before we try to actually update gnome-terminal-data and gnome-mime-data, or whatever..
What do you think?

Shobuz99

---

### Post by Shobuz99 on 2013-08-20
> **bapoumba said:**
> Hello again !

Sorry I sneaked in but as I had separated your thread from the other one and posted in, I was subscribed and got a few of your exchanges. I have not all followed, that is why I asked for a little summary. I have no intention to step on Bashing-om toes, just trying to get a picture with the tools I'm used to :)

Please try
[B]sudo apt-get clean all
sudo apt-get dist-upgrade[/B]

If it asks for it at the end (like previously), run ```
sudo apt-get -f install
```

It will probably ask to run autoremove :
**sudo apt-get autoremove**

All the packages that give you trouble in the last 2 pages, I could find them in lucid repos, so you should have a way out.

As you instructed with results:

```
rick@rick-desktop:~$ **[COLOR="#008000"]sudo apt-get clean all[/COLOR]**
[sudo] password for rick: 
rick@rick-desktop:~$ **[COLOR="#B22222"]sudo apt-get dist-upgrade[/COLOR]**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnome-terminal: Depends: gnome-terminal-data (>= 2.30) but it is not installed
                  Depends: gnome-terminal-data (< 2.31) but it is not installed
  libgnomevfs2-common: Depends: gnome-mime-data but it is not installed
E: Unmet dependencies. Try using -f.
rick@rick-desktop:~$ **[COLOR="#B22222"]sudo apt-get -f install[/COLOR]**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libopal3.6.6 libxml++2.6-2 python-twisted-mail ubufox python-twisted-lore odbcinst1debian1 python-twisted-news
  libfile-find-rule-perl python-twisted-conch python-twisted-words libslv2-9 libcapi20-3 odbcinst python-twisted unixodbc gettext rtkit libosmesa6 cvs
  libffado2 libtext-glob-perl libgnomecanvasmm-2.6-1c2a libpt2.6.5 liblo7 libaubio2 python-twisted-runner liblrdf0 python-pyasn1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-mime-data gnome-terminal-data
The following NEW packages will be installed:
  gnome-mime-data gnome-terminal-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 452kB of archives.
After this operation, 14.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://old-releases.ubuntu.com/ubuntu/ lucid/main gnome-mime-data 2.18.0-1 [362kB]
Get:2 http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main gnome-terminal-data 2.30.2-0ubuntu1 [90.1kB]
Fetched 452kB in 1s (396kB/s)               
Selecting previously deselected package gnome-mime-data.

**[COLOR="#B22222"]This is the area where things go wrong...reading the DB:[/COLOR]**

[B][COLOR="#2F4F4F"](Reading database ... 
dpkg: warning: files list file for package `[COLOR="#B22222"]icedtea-6-jre-cacao[/COLOR]' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `[COLOR="#B22222"]openjdk-6-jre-lib' missing[/COLOR], assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `[COLOR="#B22222"]openjdk-6-jre-headless[/COLOR]' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
rick@rick-desktop:~$ **[COLOR="#B22222"]sudo apt-get autoremove[/COLOR]**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnome-terminal: Depends: gnome-terminal-data (>= 2.30) but it is not installed
                  Depends: gnome-terminal-data (< 2.31) but it is not installed
  libgnomevfs2-common: Depends: gnome-mime-data but it is not installed
E: Unmet dependencies. Try using -f[/COLOR].[/B]
rick@rick-desktop:~$ 

```

See what I mean? Bashing-Om had me fix those issues a while back.
How is it that they returned???

Shobuz99

---

### Post by Bashing-om on 2013-08-20
Shobuz99; Welp .. entirely possible.
Once we do get "gnome-terminal" satisfied ... I think a lot of the problems will be behind us...
What gets me presently .. we have tried to install "gnome-terminal-data" with the proper version ... no will do ..humm..
Maybe the status file is not representing the truth once more ??
let's look and see what the dependencies are:
```

sudo apt-cache depends gnome-terminal-data

```
And ->bapoumba's advise  is a variant we have not tried to get the package manager to manage our work for us. Her perspective might be just what we need ! We are only attempting to resolve a few dependencies !

@ bapoumba; A fresh perspective is often a good thing ! ... All assistance (and instruction)  is appreciated.

Impatience: understood ... and frustration ! .. though I am engaged in several threads .. this one takes priority over all. We are so close !

[INDENT][INDENT]something is gonna give
[/INDENT][/INDENT]

---

### Post by bapoumba on 2013-08-20
What are the outputs to :
```
apt-cache policy gnome-mime-data
apt-cache policy gnome-terminal-data
```

Edit : @Bashing-om yes :)

---

### Post by Shobuz99 on 2013-08-20
> **Bashing-om said:**
> Shobuz99; Welp .. entirely possible.
Once we do get "gnome-terminal" satisfied ... I think a lot of the problems will be behind us...
What gets me presently .. we have tried to install "gnome-terminal-data" with the proper version ... no will do ..humm..
Maybe the status file is not representing the truth once more ??
let's look and see what the dependencies are:
```

sudo apt-cache depends gnome-terminal-data

```
And ->bapoumba's advise  is a variant we have not tried to get the package manager to manage our work for us. Her perspective might be just what we need ! We are only attempting to resolve a few dependencies !

@ bapoumba; A fresh perspective is often a good thing ! ... All assistance (and instruction)  is appreciated.

Impatience: understood ... and frustration ! .. though I am engaged in several threads .. this one takes priority over all. We are so close !

[INDENT][INDENT]something is gonna give
[/INDENT][/INDENT]

Ok. Results:

```
rick@rick-desktop:~$ sudo apt-cache depends gnome-terminal-data
[sudo] password for rick: 
gnome-terminal-data
  Depends: gconf2
  Recommends: gnome-terminal
rick@rick-desktop:~$  
```

@bapoumba  Please know that I appreciate your help and support a great deal.
I apologize if my remarks sounded critical of your efforts. 
That's not what I meant at all. Thank you for your very gracious input. :)

Shobuz99

---

### Post by bapoumba on 2013-08-20
> **Shobuz99 said:**
> 
@bapoumba  Please know that I appreciate your help and support a great deal.
I apologize if my remarks sounded critical of your efforts. 
That's not what I meant at all. Thank you for your very gracious input. :)

Shobuz99
No worries :)
At some point you'll need to take care of this too:
```
files list file for package `openjdk-6-jre-headless' contains empty filename
```
Hopefully not a failing hardware..

---

### Post by Bashing-om on 2013-08-20
@ Shobuz99;

> 
gnome-terminal-data
  Depends: gconf2

does not seem to help us much in finding out why "gnome-terminal-data" does not want to install ... but let's look at the state anyway:
```

apt-cache policy gconf2
dpkg -l gconf2

```
There is a reason ... I just do not see it at this time !. Are we to the point to try and (un-)install it --see what errors we get  (??) and then try and (re-)install "gnome-terminal-data 2.30.2-0ubuntu1" // Is my syntax invalid; if we attempt to install as " gnome-terminal-data-2.30.20ubuntu1" ???
(note the added dash preceding the 2 in the version ...maybe I best do some home work ...grasping at straws for howcome why ! 

@ bapoumba ;
as  Shobuz99 has related;
We had that "`openjdk-6-jre-headless'" snake stomped out at one point .. do not know why it has come back to bite us ! As well as "`icedtea-6-jre-cacao'" ..

[INDENT][INDENT]off to do homework ![/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-20
> **Bashing-om said:**
> @ Shobuz99;


does not seem to help us much in finding out why "gnome-terminal-data" does not want to install ... but let's look at the state anyway:
```

apt-cache policy gconf2
dpkg -l gconf2

```
There is a reason ... I just do not see it at this time !. Are we to the point to try and (un-)install it --see what errors we get  (??) and then try and (re-)install "gnome-terminal-data 2.30.2-0ubuntu1" // Is my syntax invalid; if we attempt to install as " gnome-terminal-data-2.30.20ubuntu1" ???
(note the added dash preceding the 2 in the version ...maybe I best do some home work ...grasping at straws for howcome why ! 

@ bapoumba ;
as  Shobuz99 has related;
We had that "`openjdk-6-jre-headless'" snake stomped out at one point .. do not know why it has come back to bite us ! As well as "`icedtea-6-jre-cacao'" ..

[INDENT][INDENT]off to do homework ![/INDENT][/INDENT]

ok this baffles me!

```
rick@rick-desktop:~$ apt-cache policy gconf2
gconf2:
  Installed: 2.28.1-0ubuntu1
  Candidate: 2.28.1-0ubuntu1
  Version table:
 *** 2.28.1-0ubuntu1 0
        500 http://old-releases.ubuntu.com/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
rick@rick-desktop:~$ dpkg -l gconf2
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  gconf2         2.28.1-0ubuntu GNOME configuration database system (support
rick@rick-desktop:~$ 

```

How can "Installed: 2.28.1-0ubuntu1" also be a "Candidate: 2.28.1-0ubuntu1" for installation???

I'm really starting to slam my head against the wall ](*,)

shobuz99

---

### Post by Bashing-om on 2013-08-20
Shobuz99; Me Too ! ..only because of my own ineptitude (fixable !)

The outputs for "gconf2" ..merely says that the latest versions available are installed ...that means to me that as a dependency for "gnome-terminal-data" this is not an issue. It is there and good .. "gnome-terminal-data" by golly should install !

I am presently attempting to VERIFY that the syntax-version I directed you to use to install is correct. I have some small amount of reservation that the "=" character vice "_" may should be used (??) but do not know where I get that assumption from ---Too many operating systems' syntax under my belt ???. I have got to verify that the directive to the operating system for the installation of "gnome-terminal-data_<version>" is correct !

To move things along ... I see no harm in purging/reinstalling:
```

sudo apt-get purge gnome-terminal gnome-terminal-data
sudo apt-get update
sudo apt-get install gnome-terminal gnome-terminal-data

```
and see what the package manager has to say about that !

[INDENT]when stuck, right wrong or otherwise - do something ![/INDENT]

---

### Post by Shobuz99 on 2013-08-21
> **Bashing-om said:**
> Shobuz99; Me Too ! ..only because of my own ineptitude (fixable !)

The outputs for "gconf2" ..merely says that the latest versions available are installed ...that means to me that as a dependency for "gnome-terminal-data" this is not an issue. It is there and good .. "gnome-terminal-data" by golly should install !

I am presently attempting to VERIFY that the syntax-version I directed you to use to install is correct. I have some small amount of reservation that the "=" character vice "_" may should be used (??) but do not know where I get that assumption from ---Too many operating systems' syntax under my belt ???. I have got to verify that the directive to the operating system for the installation of "gnome-terminal-data_<version>" is correct !

To move things along ... I see no harm in purging/reinstalling:
```

sudo apt-get purge gnome-terminal gnome-terminal-data
sudo apt-get update
sudo apt-get install gnome-terminal gnome-terminal-data

```
and see what the package manager has to say about that !

[INDENT]when stuck, right wrong or otherwise - do something ![/INDENT]

Hmm.. This looks to me like an exercise in futility:

```
rick@rick-desktop:~$ sudo apt-get purge gnome-terminal gnome-terminal-data
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-terminal-data is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libgnomevfs2-common: Depends: gnome-mime-data but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
rick@rick-desktop:~$ sudo apt-get update
Hit http://old-releases.ubuntu.com lucid Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-updates Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-backports Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-proposed Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Hit http://old-releases.ubuntu.com lucid Release
Hit http://old-releases.ubuntu.com lucid-updates Release
Hit http://old-releases.ubuntu.com lucid-backports Release
Hit http://old-releases.ubuntu.com lucid-security Release
Hit http://old-releases.ubuntu.com lucid-proposed Release
Hit http://old-releases.ubuntu.com lucid/main Packages
Hit http://old-releases.ubuntu.com lucid/restricted Packages
Hit http://old-releases.ubuntu.com lucid/universe Packages
Hit http://old-releases.ubuntu.com lucid/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-updates/main Packages
Hit http://old-releases.ubuntu.com lucid-updates/restricted Packages
Hit http://old-releases.ubuntu.com lucid-updates/universe Packages
Hit http://old-releases.ubuntu.com lucid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-backports/main Packages
Hit http://old-releases.ubuntu.com lucid-backports/restricted Packages
Hit http://old-releases.ubuntu.com lucid-backports/universe Packages
Hit http://old-releases.ubuntu.com lucid-backports/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Packages
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/restricted Packages
Hit http://old-releases.ubuntu.com lucid-proposed/main Packages
Hit http://old-releases.ubuntu.com lucid-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/universe Packages
Reading package lists... Done
rick@rick-desktop:~$ sudo apt-get install gnome-terminal gnome-terminal-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-terminal is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libgnomevfs2-common: Depends: gnome-mime-data but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
rick@rick-desktop:~$ 

```

Shobuz99

---

### Post by Bashing-om on 2013-08-21
Shobuz99;
Surprise surprise !

What results :
```

sudo apt-get install gnome-mime-data

```

[INDENT][INDENT]are we there yet
[/INDENT][/INDENT]

---

### Post by bapoumba on 2013-08-21
> **Bashing-om said:**
> 
[INDENT]are we there yet
[/INDENT]
Bashing-om, just to say I just love your little words at the end of your posts :)

---

### Post by Bashing-om on 2013-08-21
off topic ::

@ bapoumba... Thanks;
Appreciate that you notice.

Well, my "quips" like this: My communications skills reek .. even after all these years of working on them. These little quips I started using many many years ago as a means to relate better, what I can not find the words for concisely ! Lots of emotion in only a few words. Works well with my concept of the "KISS" principal !

Wait for what I have in mind for the closure of this thread !

[INDENT]always, reduce to simplest terms[/INDENT]

---

### Post by Shobuz99 on 2013-08-21
> **Bashing-om said:**
> Shobuz99;
Surprise surprise !

What results :
```

sudo apt-get install gnome-mime-data

```

[INDENT][INDENT]are we there yet
[/INDENT][/INDENT]

Results:

```
 rick@rick-desktop:~$ sudo apt-get install gnome-mime-data
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome-terminal: Depends: gnome-terminal-data (>= 2.30) but it is not going to be installed
                  Depends: gnome-terminal-data (< 2.31) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
rick@rick-desktop:~$  
```

This is deja vu all over again... I'm beginning to get dizzy going in these circles.
I recall trying this command about 2 pages back...

....so where are we now?

shobuz99

---

### Post by Bashing-om on 2013-08-21
Shobuz99; n Hi !

Yeah ! at least that far back ... I admit there are lots of things I do not understand about the circle jerk. It does have my full attention.
I am back to;
A bad /archive/ listing ?
```

sudo rm /var/cache/apt/archives/gnome-terminal-data
sudo apt-get update
sudo apt-get install --reinstall --no-install-recommends gnome-terminal-data

```

If that runs with no errors .. then we look at those dependencies !

[INDENT][INDENT]The buck stops here ?
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-21
> **Bashing-om said:**
> Shobuz99; n Hi !

Yeah ! at least that far back ... I admit there are lots of things I do not understand about the circle jerk. It does have my full attention.
I am back to;
A bad /archive/ listing ?
```

sudo rm /var/cache/apt/archives/gnome-terminal-data
sudo apt-get update
sudo apt-get install --reinstall --no-install-recommends gnome-terminal-data

```

If that runs with no errors .. then we look at those dependencies !

[INDENT][INDENT]The buck stops here ?
[/INDENT][/INDENT]

```
 rick@rick-desktop:~$ sudo rm /var/cache/apt/archives/gnome-terminal-data
[sudo] password for rick: 
rm: cannot remove `/var/cache/apt/archives/gnome-terminal-data': No such file or directory
rick@rick-desktop:~$ 
```

I probably should have stopped there, but I kept going:

```
 rick@rick-desktop:~$ sudo apt-get update
Hit http://old-releases.ubuntu.com lucid Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-updates Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-backports Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-proposed Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Hit http://old-releases.ubuntu.com lucid Release
Hit http://old-releases.ubuntu.com lucid-updates Release
Hit http://old-releases.ubuntu.com lucid-backports Release
Hit http://old-releases.ubuntu.com lucid-security Release
Hit http://old-releases.ubuntu.com lucid-proposed Release
Hit http://old-releases.ubuntu.com lucid/main Packages
Hit http://old-releases.ubuntu.com lucid/restricted Packages
Hit http://old-releases.ubuntu.com lucid/universe Packages
Hit http://old-releases.ubuntu.com lucid/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-updates/main Packages
Hit http://old-releases.ubuntu.com lucid-updates/restricted Packages
Hit http://old-releases.ubuntu.com lucid-updates/universe Packages
Hit http://old-releases.ubuntu.com lucid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-backports/main Packages
Hit http://old-releases.ubuntu.com lucid-backports/restricted Packages
Hit http://old-releases.ubuntu.com lucid-backports/universe Packages
Hit http://old-releases.ubuntu.com lucid-backports/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Packages
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/restricted Packages
Hit http://old-releases.ubuntu.com lucid-proposed/main Packages
Hit http://old-releases.ubuntu.com lucid-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/universe Packages
Reading package lists... Done
rick@rick-desktop:~$
```

Well, that went as expected. Why not continue, eh?
```

rick@rick-desktop:~$ sudo apt-get install --reinstall --no-install-recommends gnome-terminal-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libgnomevfs2-common: Depends: gnome-mime-data but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
rick@rick-desktop:~$ 
```

And here we are, back at square 1 or somewhere...
Sorry. I'm getting very tired. It's been 3 weeks now, that we've been going back and forth.
I'm wearing down. Especially, when my laptop that runs 10.04 LTS 32-bit has not made a noise about anything.
It's true that I never installed Netflix or Wine-Compholio on my laptop...
but the Update Manager on my laptop has stopped notifying me of updates; which is what it SHOULD do if the OS is at EOL.

I took a look at Synaptic and viewed the "2 broken pkgs" under the "broken dependencies" section.
Two were listed:
libgnomevfs2-common 1:2.24.2-1ubuntu2 (lucid)
gnome-terminal          2.30.2-0ubuntu1 (lucid updates) 
                                2.29.6-0ubuntu5 (lucid

I've attached an image for the libgnomevfs2-common and for gnome-terminal.

I see there are "conflicts" in the libgnomevfs2-common dependencies list. 
Is this our problem??

Also, would "forcing" an install through synaptic cause further troubles?

Just asking...

shobuz99

---

### Post by Bashing-om on 2013-08-21
Shobuz99; 

Synaptic is smart .. very smart .. and rarely will it do anything that will damage the package manager ..I see no harm at all in seeing if synaptic will fix the broken packages .. anything to try so we can move on past this !.. It would be a big help to compare files on a working 10.04 install and see what the difference are in the "list" and "status" files ...just to rule out corruption as a root cause.

Will await your advisement on what synaptic does.

[INDENT][INDENT]there is reason
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-22
> **Bashing-om said:**
> Shobuz99; 

Synaptic is smart .. very smart .. and rarely will it do anything that will damage the package manager ..I see no harm at all in seeing if synaptic will fix the broken packages .. anything to try so we can move on past this !.. It would be a big help to compare files on a working 10.04 install and see what the difference are in the "list" and "status" files ...just to rule out corruption as a root cause.

Will await your advisement on what synaptic does.

[INDENT][INDENT]there is reason
[/INDENT][/INDENT]

ok. I guess we've covered this ground before. 
The first thing I did was try the "fix broken pkgs" option in Synaptic.
When I clicked "Apply" it started to work; but failed once again, because of the details on the image attached.
That is basically what needs to be fixed, before I can proceed to install the "gnome" updates.

We've been here before. Please explain to me how to correct the "icedtea-6-jre-caca0" and the "openjdk-6-jre-lib"
and "openjdk-6-jre-headless" errors. I think we have done some editing in the DB while trying to rid it of Netflix, correct?

If we can do that, then it WILL BE SOLVED...in my opinion...how about yours?

[COLOR="#800000"]BTW.. I toyed with the idea of "complete removal" of the "gnome" package, BUT...
I saw how many dependencies existed, including "Evolution" and may many others, and decided against it.[/COLOR]

shobuz99


**UPDATE:** [COLOR="#800000"]Apparently when I tried uninstalling the "icedtea-6-jre-caca0" and the "openjdk-6-jre-lib" packages
with synaptic, I discovered that the same dependencies that exist for the "gnome" pkgs also exist for the "icedtea-6-jre-caca0" and the "openjdk-6-jre-lib".
This means I risk destroying something regardless of what I do. Have any recommends?[/COLOR]

---

### Post by Bashing-om on 2013-08-22
Shobuz99; Regret that there was a delay in responding...lubuntu grub update broke my custom boot. Took me a bit to check my config files and restore grub properly. Back up now and operational !

I too am tired of this chasing our tails to no satisfaction...Doing my homework .. see if I can determine where the failure in the install/purge process lies .. and how to really see the point of failure. Seems 6 files applications are affecting "gnome terminal".

I do not want to do -hit or miss - any longer .. I do want to know why all of them fail to install ! 

[INDENT][INDENT]meanwhile, back at the ranch[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-08-23
Shobuz99;

I have not abandoned you or this situation . I continue to seek a means to find the cause that those dependencies will not install.

[INDENT][INDENT]if at 3rd you do not succeed -> try try again
[/INDENT][/INDENT]

---

### Post by bapoumba on 2013-08-23
> **Shobuz99 said:**
> Results:

```
 rick@rick-desktop:~$ sudo apt-get install gnome-mime-data
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  [COLOR="#FF0000"]gnome-terminal: Depends: gnome-terminal-data (>= 2.30) but it is not going to be installed
                  Depends: gnome-terminal-data (< 2.31) but it is not going to be installed[/COLOR]
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
rick@rick-desktop:~$  
```

This is deja vu all over again... I'm beginning to get dizzy going in these circles.
I recall trying this command about 2 pages back...

....so where are we now?

shobuz99
Quoting from last page.

I looked the gnome-terminal-data package version for lucid : [http://packages.ubuntu.com/search?keywords=gnome-terminal-data&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=gnome-terminal-data&searchon=names&suite=lucid&section=all)
Lucid version is 1:2.24.2-1ubuntu2 and apt-get says it needs >= 2.30. This particular version I cannot find in lucid, even in backports.

I think that is the problem. Did you install at some point some packages from a ppa or some other repo ? You may already have answer that somewhere in the thread.

---

### Post by Shobuz99 on 2013-08-23
> **bapoumba said:**
> Quoting from last page.

I looked the gnome-terminal-data package version for lucid : [http://packages.ubuntu.com/search?keywords=gnome-terminal-data&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=gnome-terminal-data&searchon=names&suite=lucid&section=all)
Lucid version is 1:2.24.2-1ubuntu2 and apt-get says it needs >= 2.30. This particular version I cannot find in lucid, even in backports.

I think that is the problem. Did you install at some point some packages from a ppa or some other repo ? You may already have answer that somewhere in the thread.

@bapoumba and bashing-om

Good point. Thanks for searching. Here's what I found (on the internet) when I searched for "gnome-terminal-data 2.30"
and found this link: [http://packages.debian.org/squeeze/gnome-terminal-data](http://packages.debian.org/squeeze/gnome-terminal-data)
.
I also searched and found this link:[http://pkgs.org/ubuntu-10.04/ubuntu-updates-main-i386/gnome-desktop-data_2.30.2-0ubuntu1_all.deb.html](http://pkgs.org/ubuntu-10.04/ubuntu-updates-main-i386/gnome-desktop-data_2.30.2-0ubuntu1_all.deb.html)

I don't recall downloading and installing this outside of Synaptic...however, It is possible. 
I can't seem to reason WHY I would do that.
I have used and been downloading debian pkgs outside Synaptic whenever it wasn't offered there; such as ClamTK.
I don't know if there are dependencies for ClamTK that include gnome-terminal-data... I doubt it, though.

What does this mean? If I go to the link that offers the debian gnome-terminal-data 2.30 and download it
and install it through the Debian package installer, will I be able to solve this problem??

BTW... I also found a thread on this very forum regarding gnome-terminal:
[http://ubuntuforums.org/showthread.php?t=1494709](http://ubuntuforums.org/showthread.php?t=1494709)

I await your advice before I proceed.

[COLOR="#006400"]**UPDATE: I found the Gnome-Terminal package installed on my 32-bit laptop, 386 system:**[/COLOR]

Package: gnome-terminal
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 380
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
[B][COLOR="#006400"]Version: 2.30.2-0ubuntu1
[/COLOR][/B]Replaces: gnome-terminal-data (<< 2.28.1-1ubuntu1)
Provides: x-terminal-emulator
Depends: libatk1.0-0 (>= 1.29.3), libc6 (>= 2.4), libdbus-glib-1-2 (>= 0.78), libgconf2-4 (>= 2.27.0), libglib2.0-0 (>= 2.23.5), libgtk2.0-0 (>= 2.18.0), libice6 (>= 1:1.0.0), liblaunchpad-integration1 (>= 0.1.17), libpango1.0-0 (>= 1.14.0), libsm6, libvte9 (>= 1:0.22.0), libx11-6 (>= 0), gnome-terminal-data (>= 2.30), gnome-terminal-data (<< 2.31)
Recommends: yelp, gvfs
Description: The GNOME terminal emulator application
 GNOME Terminal is a terminal emulation application that you can use to
 perform the following actions:
  - Access a UNIX shell in the GNOME environment.
  - Run any application that is designed to run on VT102, VT220, and xterm
 terminals.
 .
 GNOME Terminal features the ability to use multiple terminals in a single
 window (tabs) and profiles support.
Original-Maintainer: Guilherme de S. Pastore <gpastore@debian.org>



Shobuz99

---

### Post by bapoumba on 2013-08-23
It's quite late here, what do you mean by "I found the Gnome-Terminal package installed on my 32-bit laptop, 386 system:" ?

---

### Post by Bashing-om on 2013-08-23
@bapoumba -> fantastic ! Maybe on to something !

I have spent 2 solid days on research in this respect ... I have found nothing to add to what has been done ... less maybe I have made an error in the procedure order ..
I am slapped in the face with - if I want an increased understanding of the apt-get system ... read the source code of apt-get.

@ Shobuz99 .. make sure you have read bapoumba's last post(s).
Meanwhile I will look at the links provided.

 
[INDENT][INDENT]reading is good; but, my comprehension is deficient [/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-23
> **bapoumba said:**
> It's quite late here, what do you mean by "I found the Gnome-Terminal package installed on my 32-bit laptop, 386 system:" ?

I mean exactly what I said. But let me re-phrase: 
A 32-bit version of the Gnome-Terminal package is installed on my 32-bit laptop...
The version is 2.30. (see my previous post from the "Status" for Gnome-Terminal package)

However, my **Desktop** (the source of my frustration) is an **AMD64 bit machine**; 
which means that the 32 bit gnome terminal pkg WILL NOT WORK on a 64 bit machine....correct?

My point is this: You stated that there isn't a more recent version of gnome-terminal than 2.29..isn't that what you said?
Well I found one and it's on my 32 bit machine. BUT THAT DOESN'T MEAN THAT THERE IS A 64 bit version, correct???

So what I think may have happened is that I might have something messed up on my Desktop that thinks I have 10.04 LTS 32-bit.
When it is clearly NOT a 32 bit version of 10.04 LTS but a **64 bit** version. 
Understand what I mean? I'm asking you if that is even possible...that's all.

shobuz99

---

### Post by Bashing-om on 2013-08-23
Shobuz99; Hey !

You also may be onto something. Multiarch was not available as default in 10.04. Let's see about the 32 bit architecture.
Maybe at some point the 32 bit libs have been broken.
Best I recall "wine" is a 32 bit ap .. such that the 32 bit architecture libs must be available.
```

dpkg --print-foreign-architectures
apt-cache policy libfreetype6
apt-cache policy libfreetype6:i386
ls -la /etc/dpkg/dpkg.cfg.d/multiarch

```

[INDENT][INDENT]should tell the tale
[/INDENT][/INDENT]

---

### Post by bapoumba on 2013-08-24
Wine and Skype as far as I know.

May be enable again the repos that brought these libs and try to remove them so that the package manager has an archivee for them ?

---

### Post by Shobuz99 on 2013-08-24
> **bapoumba said:**
> Wine and Skype as far as I know.

May be enable again the repos that brought these libs and try to remove them so that the package manager has an archive for them ?

I like this idea. It's what I was trying to say before, rather clumsily I guess. Simply put: 
***** I am wondering if some 32 bit version of Gnome got installed on my 64 bit machine?  ... **[COLOR="#B22222"]Or[/COLOR]**
****** Whether just switching back to the "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted"
              in my sources.list will correct the problem, once "sudo apt-get update" is run?

My **current** sources.list:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://old-releases.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://old-releases.ubuntu.com/ubuntu/ lucid universe
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://old-releases.ubuntu.com/ubuntu/ lucid multiverse
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://old-releases.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://old-releases.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb-src http://archive.canonical.com/ubuntu hardy partner


deb http://old-releases.ubuntu.com/ubuntu lucid-security main restricted
deb http://old-releases.ubuntu.com/ubuntu lucid-security universe
deb http://old-releases.ubuntu.com/ubuntu lucid-security multiverse
deb http://old-releases.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
# deb http://wine.budgetdedicated.com/apt karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" disabled on upgrade to karmic
```


**BTW... I looked at my [COLOR="#B22222"]/etc/apt/sources.list.d folder[/COLOR] and it is EMPTY!! What does that affect? **
          **[COLOR="#006400"]I DO have a /etc/apt/sources.list.save file:[/COLOR]**

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
# deb http://wine.budgetdedicated.com/apt karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" disabled on upgrade to karmic
```

Please advise.

shobuz99

---

### Post by bapoumba on 2013-08-24
> **bapoumba said:**
> No worries :)
At some point you'll need to take care of this too:
```
files list file for package `openjdk-6-jre-headless' contains empty filename
```
Hopefully not a failing hardware..
I'll add also the next line from the same error message 
```
files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.
```
From this post : [http://ubuntuforums.org/showthread.php?t=2167942&p=12763468#post12763468](http://ubuntuforums.org/showthread.php?t=2167942&p=12763468#post12763468)

I've been looking around for that error message which seems a root to the other problems.
[https://wiki.ubuntu.com/DebuggingInstallationIssues#files_list_file_missing_final_newline_.2BAC8_contains_empty_filename](https://wiki.ubuntu.com/DebuggingInstallationIssues#files_list_file_missing_final_newline_.2BAC8_contains_empty_filename)
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189)

Would you be ready to try the fixes ? I've checked, openjdk-6-jre-headless and icedtea-6-jre-cacao are in Lucid repos :
[http://packages.ubuntu.com/search?keywords=icedtea-6-jre-cacao&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=icedtea-6-jre-cacao&searchon=names&suite=lucid&section=all)
[http://packages.ubuntu.com/search?keywords=openjdk-6-jre-headless&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=openjdk-6-jre-headless&searchon=names&suite=lucid&section=all)

---

### Post by Shobuz99 on 2013-08-24
> **Bashing-om said:**
> Shobuz99; Hey !

You also may be onto something. Multiarch was not available as default in 10.04. Let's see about the 32 bit architecture.
Maybe at some point the 32 bit libs have been broken.
Best I recall "wine" is a 32 bit ap .. such that the 32 bit architecture libs must be available.
```

dpkg --print-foreign-architectures
apt-cache policy libfreetype6
apt-cache policy libfreetype6:i386
ls -la /etc/dpkg/dpkg.cfg.d/multiarch

```

[INDENT][INDENT]should tell the tale
[/INDENT][/INDENT]

Ok, Bashing-om, here are the results:

```
rick@rick-desktop:~$ dpkg --print-foreign-architectures
dpkg: unknown option --print-foreign-architectures

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
rick@rick-desktop:~$ dpkg --print foreign-architectures
dpkg: unknown option --print

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
rick@rick-desktop:~$ apt-cache policy libfreetype6
libfreetype6:
  Installed: 2.3.11-1ubuntu2.7
  Candidate: 2.3.11-1ubuntu2.7
  Version table:
 *** 2.3.11-1ubuntu2.7 0
        500 http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Packages
        500 http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Packages
        100 /var/lib/dpkg/status
     2.3.11-1ubuntu2 0
        500 http://old-releases.ubuntu.com/ubuntu/ lucid/main Packages
rick@rick-desktop:~$ apt-cache policy libfreetype6:i386
W: Unable to locate package libfreetype6:i386
rick@rick-desktop:~$ ls -la /etc/dpkg/dpkg.cfg.d/multiarch
ls: cannot access /etc/dpkg/dpkg.cfg.d/multiarch: No such file or directory
rick@rick-desktop:~$  
```

I tried the first command twice, because I thought there was a syntax error;
but the 2nd try didn't work either, after I removed a "-" after the word 'print'.

I guess I see your reasoning to understand the 32 bit....BUT
My question is whether there is a "mixed" situation of a 32 bit (laptop) Gnome on my 64 bit (Desktop) machine.
Is that what you're referring to as a "multiarch" issue???

Shobuz99

---

### Post by Bashing-om on 2013-08-24
Well, as I have remarked before, we could enable this old repository in /etc/apt/sources.list and see what results. I believe this repository is depreciated and I have no idea as to what would result. Nor, what the effect on "Wine" would be if we were to activate the current "Wine" ppa.
I also think this a a way forward .. just be aware there are risk ! /// Would of course have to edit "lucid" in place of "karmic" 
> 
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) karmic main


[INDENT]do something, right - wrong - or otherwise
[/INDENT]

---

### Post by Shobuz99 on 2013-08-24
> **bapoumba said:**
> I'll add also the next line from the same error message 
```
files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.
```
From this post : [http://ubuntuforums.org/showthread.php?t=2167942&p=12763468#post12763468](http://ubuntuforums.org/showthread.php?t=2167942&p=12763468#post12763468)

I've been looking around for that error message which seems a root to the other problems.
[https://wiki.ubuntu.com/DebuggingInstallationIssues#files_list_file_missing_final_newline_.2BAC8_contains_empty_filename](https://wiki.ubuntu.com/DebuggingInstallationIssues#files_list_file_missing_final_newline_.2BAC8_contains_empty_filename)
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189)

Would you be ready to try the fixes ? I've checked, openjdk-6-jre-headless and icedtea-6-jre-cacao are in Lucid repos :
[http://packages.ubuntu.com/search?keywords=icedtea-6-jre-cacao&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=icedtea-6-jre-cacao&searchon=names&suite=lucid&section=all)
[http://packages.ubuntu.com/search?keywords=openjdk-6-jre-headless&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=openjdk-6-jre-headless&searchon=names&suite=lucid&section=all)

For some reason. I missed this post previously, and posted the comment to Bashing-om.

Yes, I am willing to try the fixes you have recommended. I will need some time to read them over and make sure
I understand every step, in the correct order.
Even though I am opting to do this, I want to also keep in mind what Bashing-om has also suggested;
as a courtesy to bashing-om's persistent help and advice to get my problem solved.
I will come back on here tomorrow, after I have had more time to be certain of taking the steps you advise.
I very much appreciate and respect your efforts to get my issues resolved, as well.
Both of you have been extremely diligent and kind, to spend this much of your time to help me.

Thank you again, sincerely.
I'll be back tomorrow with some results of some kind.

shobuz99

---

### Post by bapoumba on 2013-08-25
> **Shobuz99 said:**
> For some reason. I missed this post previously, and posted the comment to Bashing-om.

Yes, I am willing to try the fixes you have recommended. I will need some time to read them over and make sure
I understand every step, in the correct order.
Even though I am opting to do this, I want to also keep in mind what Bashing-om has also suggested;
as a courtesy to bashing-om's persistent help and advice to get my problem solved.
I will come back on here tomorrow, after I have had more time to be certain of taking the steps you advise.
I very much appreciate and respect your efforts to get my issues resolved, as well.
Both of you have been extremely diligent and kind, to spend this much of your time to help me.

Thank you again, sincerely.
I'll be back tomorrow with some results of some kind.

shobuz99
shobuz99, no problem at all. As I said previously, I do not wish to step on Bashing-om toes. I was subscribed to your thread after moving it and if thing would have been solved or in the process of being solved, I would not have even posted.
Your issue interests me, I like package managers, and dpkg/apt even more than the other ones, except aptitude that has always been my favorite :)

---

### Post by Shobuz99 on 2013-08-25
> **bapoumba said:**
> shobuz99, no problem at all. As I said previously, I do not wish to step on Bashing-om toes. I was subscribed to your thread after moving it and if thing would have been solved or in the process of being solved, I would not have even posted.
Your issue interests me, I like package managers, and dpkg/apt even more than the other ones, except aptitude that has always been my favorite :)

ok. This is a bit daunting for me; however, I discovered that there are no ".deb" packages 
for "openjdk" or "icedtea" in a GZIP Archive or simply labeled as ".deb"
[COLOR="#006400"]**There ARE files listed for "openjdk"**[/COLOR] if I run the "[COLOR="#B22222"]**ls -la /var/lib/dpkg/info | less**[/COLOR]" command.
[COLOR="#B22222"]**However, there are NO files listed for "icedtea"**[/COLOR]

I assume they are NOT what you are talking about, correct?

Maybe I'm a bit thick, and misunderstand your recommendation.. :redface: Embarrassing for me.

Should I find these two packages by searching for them, downloading them and 
then proceed as the link instructions tell me?: 
[https://wiki.ubuntu.com/DebuggingInstallationIssues#files_list_file_missing_final_newline_.2BAC8_contains_empty_filename](https://wiki.ubuntu.com/DebuggingInstallationIssues#files_list_file_missing_final_newline_.2BAC8_contains_empty_filename)

Sorry for my slow comprehension of this task. :)

shobuz99

---

### Post by bapoumba on 2013-08-25
Yes, please find the files: /var/lib/dpkg/info/PACKAGE_NAME.list (changing PACKAGE_NAME accordingly) ans see if they are empty or full with other stuff.Here is what it should look like, from abiword which is the first one in my folder :
```
/.
/usr
/usr/share
/usr/share/applications
/usr/share/applications/abiword.desktop
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/abiword.1.gz
/usr/share/doc
/usr/share/doc/abiword
/usr/share/doc/abiword/AUTHORS.gz
/usr/share/doc/abiword/readme.abw.gz
/usr/share/doc/abiword/readme.txt.gz
/usr/share/doc/abiword/copyright
/usr/share/pixmaps
/usr/share/pixmaps/abiword.xpm
/usr/share/pixmaps/abiword.png
/usr/share/menu
/usr/share/menu/abiword
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/abiword
/usr/bin
/usr/bin/abiword
/usr/lib
/usr/lib/mime
/usr/lib/mime/packages
/usr/lib/mime/packages/abiword
/usr/lib/i386-linux-gnu
/usr/lib/i386-linux-gnu/abiword-2.9
/usr/lib/i386-linux-gnu/abiword-2.9/plugins
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/babelfish.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/mswrite.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/garble.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/xslfo.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/command.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/hancom.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/t602.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/applix.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/wikipedia.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/wmf.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/passepartout.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/mif.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/opml.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/ots.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/opendocument.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/aiksaurus.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/iscii.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/openwriter.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/google.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/pdf.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/collab.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/wml.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/mht.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/clarisworks.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/urldict.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/paint.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/loadbindings.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/docbook.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/eml.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/gimp.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/presentation.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/bmp.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/sdw.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/gdict.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/openxml.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/hrtext.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/freetranslation.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/latex.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/epub.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/wpg.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/wordperfect.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/pdb.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/s5.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/kword.so
/usr/share/doc/abiword/changelog.Debian.gz

```
Then we can see from there.

---

### Post by Bashing-om on 2013-08-25
@ bapoumba ..aiding and abetting in a time of need is not "stepping on toes". Thanks.
bk

I continue to monitor the activities as I have nothing constructive to add at this time; Will see what develops.
Keeping in mind unsatisfied conditions. 

[INDENT]what does it take to keep a "application" like you satisfied
[/INDENT]

---

### Post by Jonathan Precise on 2013-08-25
Hello there Shobuz99!
Sorry if I'm too late, but try the following:

Edit: Just tried it yesterday. Doesn't hurt if you try it, yet will not solve the problem (syntax error):

```
sudo apt-get install --reinstall --download-only openjdk-6-jre-headless
dpkg -c /var/cache/apt/archive/openjdk-6-jre-headless_6b27-1.12.6-1ubuntu0.10.04.2_amd64.deb | awk \
{if ($6 == "./") { print "/."; } \
else if (substr($6, length($6), 1) == "/") \
{print substr($6, 2, length($6) - 2); } \
else { print substr($6, 2, length($6) - 1);}}' \
> /var/lib/dpkg/info/openjdk-6-jre-headless.list
```

Then:

```
sudo apt-get install --reinstall --download-only icedtea-6-jre-cacao
dpkg -c /var/cache/apt/archive/icedtea-6-jre-cacao_6b27-1.12.6-1ubuntu0.10.04.2_amd64.deb | awk \
{if ($6 == "./") { print "/."; } \
else if (substr($6, length($6), 1) == "/") \
{print substr($6, 2, length($6) - 2); } \
else { print substr($6, 2, length($6) - 1);}}' \
> /var/lib/dpkg/info/icedtea-6-jre-cacao.list
```

Sorry again if I'm too late:wink:!

Edit: this is just an adapted version of the links bapoumpa made:
 
[FONT=Verdana]> **bapoumba said:**
> I'll add also the next line from the same error message:[/FONT]> **bapoumba said:**
> 
[FONT=Verdana]```
files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.
```[/FONT]
[FONT=Verdana]From this post : [/FONT][http://ubuntuforums.org/showthread.php?t=2167942&p=12763468#post12763468](http://ubuntuforums.org/showthread.php?t=2167942&p=12763468#post12763468)

[FONT=Verdana]I've been looking around for that error message which seems a root to the other problems.[/FONT]
[https://wiki.ubuntu.com/DebuggingInstallationIssues#files_list_file_missing_final_newline_.2BAC8_contains_empty_filename](https://wiki.ubuntu.com/DebuggingInstallationIssues#files_list_file_missing_final_newline_.2BAC8_contains_empty_filename)
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189)

[FONT=Verdana]Would you be ready to try the fixes ? I've checked, openjdk-6-jre-headless and icedtea-6-jre-cacao are in Lucid repos :[/FONT]
[http://packages.ubuntu.com/search?keywords=icedtea-6-jre-cacao&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=icedtea-6-jre-cacao&searchon=names&suite=lucid&section=all)
[http://packages.ubuntu.com/search?keywords=openjdk-6-jre-headless&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=openjdk-6-jre-headless&searchon=names&suite=lucid&section=all)

(in other words, I joined the commands and switched the program according to your problem)

Edit 2: Thanks bapoumpa for the links!

---

### Post by Shobuz99 on 2013-08-26
> **bapoumba said:**
> Yes, please find the files: /var/lib/dpkg/info/PACKAGE_NAME.list (changing PACKAGE_NAME accordingly) ans see if they are empty or full with other stuff.Here is what it should look like, from abiword which is the first one in my folder :
```
/.
/usr
/usr/share
/usr/share/applications
/usr/share/applications/abiword.desktop
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/abiword.1.gz
/usr/share/doc
/usr/share/doc/abiword
/usr/share/doc/abiword/AUTHORS.gz
/usr/share/doc/abiword/readme.abw.gz
/usr/share/doc/abiword/readme.txt.gz
/usr/share/doc/abiword/copyright
/usr/share/pixmaps
/usr/share/pixmaps/abiword.xpm
/usr/share/pixmaps/abiword.png
/usr/share/menu
/usr/share/menu/abiword
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/abiword
/usr/bin
/usr/bin/abiword
/usr/lib
/usr/lib/mime
/usr/lib/mime/packages
/usr/lib/mime/packages/abiword
/usr/lib/i386-linux-gnu
/usr/lib/i386-linux-gnu/abiword-2.9
/usr/lib/i386-linux-gnu/abiword-2.9/plugins
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/babelfish.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/mswrite.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/garble.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/xslfo.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/command.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/hancom.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/t602.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/applix.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/wikipedia.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/wmf.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/passepartout.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/mif.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/opml.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/ots.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/opendocument.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/aiksaurus.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/iscii.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/openwriter.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/google.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/pdf.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/collab.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/wml.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/mht.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/clarisworks.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/urldict.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/paint.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/loadbindings.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/docbook.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/eml.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/gimp.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/presentation.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/bmp.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/sdw.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/gdict.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/openxml.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/hrtext.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/freetranslation.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/latex.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/epub.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/wpg.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/wordperfect.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/pdb.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/s5.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/kword.so
/usr/share/doc/abiword/changelog.Debian.gz

```
Then we can see from there.

Ok. It didn't result in quite the same way that yours did. First, I used the commands as follows:
```
rick@rick-desktop:~$ **ls -la /var/lib/dpkg/info/openjdk*.list**
-rw-r--r-- 1 root root 9116 2013-05-08 14:53 /var/lib/dpkg/info/openjdk-6-jre-headless.list
-rw-r--r-- 1 root root 2276 2013-05-08 14:53 /var/lib/dpkg/info/openjdk-6-jre.list
rick@rick-desktop:~$ **ls -la /var/lib/dpkg/info/icedtea*.list**
-rw-r--r-- 1 root root 1964 2013-04-19 19:34 /var/lib/dpkg/info/icedtea-netx.list
rick@rick-desktop:~$ 

```

Then I tried them using the "find" command:
```
rick@rick-desktop:~$ find /var/lib/dpkg/info/openjdk*
/var/lib/dpkg/info/openjdk-6-jre-headless.conffiles
/var/lib/dpkg/info/openjdk-6-jre-headless.list
/var/lib/dpkg/info/openjdk-6-jre-headless.md5sums
/var/lib/dpkg/info/openjdk-6-jre-headless.postinst
/var/lib/dpkg/info/openjdk-6-jre-headless.postrm
/var/lib/dpkg/info/openjdk-6-jre-headless.preinst
/var/lib/dpkg/info/openjdk-6-jre-headless.prerm
/var/lib/dpkg/info/openjdk-6-jre-lib.md5sums
/var/lib/dpkg/info/openjdk-6-jre-lib.postinst
/var/lib/dpkg/info/openjdk-6-jre.list
/var/lib/dpkg/info/openjdk-6-jre.md5sums
/var/lib/dpkg/info/openjdk-6-jre.postinst
/var/lib/dpkg/info/openjdk-6-jre.postrm
/var/lib/dpkg/info/openjdk-6-jre.preinst
/var/lib/dpkg/info/openjdk-6-jre.prerm
rick@rick-desktop:~$ find /var/lib/dpkg/info/icedtea*
/var/lib/dpkg/info/icedtea-6-jre-cacao.md5sums
/var/lib/dpkg/info/icedtea-netx.conffiles
/var/lib/dpkg/info/icedtea-netx.list
/var/lib/dpkg/info/icedtea-netx.md5sums
/var/lib/dpkg/info/icedtea-netx.postinst
/var/lib/dpkg/info/icedtea-netx.preinst
/var/lib/dpkg/info/icedtea-netx.prerm
rick@rick-desktop:~$ 
```

I didn't actually look at the "/usr/lib/i386" contents to find the "openjdk" or "icedtea" listings
as you demonstrated in your previous post.

If you could suggest that actual command, I would be happy to run it and post the results.


Shobuz99

---

### Post by Shobuz99 on 2013-08-26
> **Jonathan Precise said:**
> Hello there Shobuz99!
Sorry if I'm too late, but try the following:

```
sudo apt-get install --reinstall --download-only openjdk-6-jre-headless
dpkg -c /var/cache/apt/archive/openjdk-6-jre-headless_6b27-1.12.6-1ubuntu0.10.04.2_amd64.deb | awk \{if ($6 == "./") { print "/."; } \
else if (substr($6, length($6), 1) == "/") \
{print substr($6, 2, length($6) - 2); } \
else { print substr($6, 2, length($6) - 1);}}' \
> /var/lib/dpkg/info/openjdk-6-jre-headless.list
```

Then:

```
sudo apt-get install --reinstall --download-only icedtea-6-jre-cacao
dpkg -c /var/cache/apt/archive/icedtea-6-jre-cacao_6b27-1.12.6-1ubuntu0.10.04.2_amd64.deb | awk \
{if ($6 == "./") { print "/."; } \
else if (substr($6, length($6), 1) == "/") \
{print substr($6, 2, length($6) - 2); } \
else { print substr($6, 2, length($6) - 1);}}' \
> /var/lib/dpkg/info/icedtea-6-jre-cacao.list
```

Sorry again if I'm too late:wink:!

Jonathan,
I appreciate your help and advice. It's not that you're too late, at all.
I want to continue with the advice I have been getting so far, from "Bashing-om" and "bapoumba".
I am interested in trying what you suggest, as long as both bashing-om and bapoumba agree that
it could be the solution if what they have advised doesn't work out, ok?
I'm not rejecting what you have suggested at all; I just want to see first what bashing-om and bapoumba have to say 
at this point. Ok? No offense to you, intended. :-)

shobuz99

---

### Post by Bashing-om on 2013-08-26
Shobuz99; Afternoon,

What bapoumba is investigating is possible corruption in the ".list" files:
for instance:
```

cat /var/lib/dpkg/info/openjdk-6-jre-headless.list

```
should show a list of </path-to/file> with no garbage characters in these files.

I also keep in mind there are other issues yet to be addressed.

[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-26
> **Bashing-om said:**
> Shobuz99; Afternoon,

What bapoumba is investigating is possible corruption in the ".list" files:
for instance:
```

cat /var/lib/dpkg/info/openjdk-6-jre-headless.list

```
should show a list of </path-to/file> with no garbage characters in these files.

I also keep in mind there are other issues yet to be addressed.

[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

Bashing-om,
I ran the command you suggested with these results:

```
rick@rick-desktop:~$ cat /var/lib/dpkg/info/openjdk-6-jre-headless.list
Package: xserver-xorg-input-vmmouse
Priority: optional
Section: x11
Installed-Size: 176
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: amd64
Version: 1:12.6.5-4ubuntu2
Replaces: mdetect (<< 0.5.2.2), xserver-xorg (<< 6.8.2-35)
Provides: xserver-xorg-input-7
Depends: libc6 (>= 2.7), xserver-xorg-core (>= 2:1.6.99.900), xserver-xorg-input-mouse, udev
Size: 30918
Description: X.Org X server -- VMMouse input driver to use with VMWare
 This package provides the driver for the X11 vmmouse input device.
 .
 The VMMouse driver enables support for the special VMMouse protocol
 that is provided by VMware virtual machines to give absolute pointer
 positioning.
 .
 The vmmouse driver is capable of falling back to the standard "mouse"
 driver if a VMware virtual machine is not detected. This allows for
 dual-booting of an operating system from a virtual machine to real hardware
 without having to edit xorg.conf every time.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This package is built from the X.org xf86-input-vmmouse driver module.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>

Package: libxml-libxml-perl
Priority: optional
Section: perl
Installed-Size: 1332
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 1.70.ds-1
Replaces: libxml-libxml-common-perl
Depends: perl (>= 5.10.0-24ubuntu4), perlapi-5.10.0, libc6 (>= 2.4), libxml2 (>= 2.7.4), zlib1g (>= 1:1.1.4), libxml-namespacesupport-perl, libxml-sax-perl
Conflicts: libxml-libxml-common-perl
Size: 419532
Description: Perl interface to the libxml2 library
 XML::LibXML is a Perl interface to the GNOME libxml2 library, which provides
 interfaces for parsing and manipulating XML files. This module allows Perl
 programmers to make use of the highly capable validating XML parser and the
 high performance Document Object Model (DOM) implementation. Additionally, it
 supports using the XML Path Language (XPath) to find and extract information.
Original-Maintainer: Debian Perl Group <pkg-perl-maintainers@lists.alioth.debian.org>
Homepage: http://search.cpan.org/dist/XML-LibXML/

Package: libexempi3
Priority: optional
Section: libs
Installed-Size: 1016
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: exempi
Version: 2.1.1-1build2
Depends: libc6 (>= 2.4), libexpat1 (>= 1.95.8), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.4.0), zlib1g (>= 1:1.1.4)
Size: 408476
Description: library to parse XMP metadata (Library)
 Exempi is a library to parse XMP metadata as defined by the
 specification.
 .
 XMP (Extensible Metadata Platform) facilitates embedding metadata in files
 using a subset of RDF. Most notably XMP supports embedding metadata in PDF
 and many image formats, though it is designed to support nearly any file type.
Original-Maintainer: Asheesh Laroia <asheesh@asheesh.org>
Homepage: http://libopenraw.freedesktop.org/wiki/Exempi

Package: linux-headers-2.6.31-14-generic
Priority: optional
Section: devel
Installed-Size: 8616
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux
Version: 2.6.31-14.48
Provides: linux-headers, linux-headers-2.6
Depends: coreutils | fileutils (>= 4.0), linux-headers-2.6.31-14, libc6 (>= 2.8)
Size: 692344
Description: Linux kernel headers for version 2.6.31 on x86/x86_64
 This package provides kernel header files for version 2.6.31 on
 x86/x86_64.
 .
 This is for sites that want the latest kernel headers.  Please read
 /usr/share/doc/linux-headers-2.6.31-14/debian.README.gz for details.

Package: libgtkspell0
Priority: optional
Section: libs
Installed-Size: 628
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: gtkspell
Version: 2.0.16-1
Depends: libatk1.0-0 (>= 1.29.3), libc6 (>= 2.2.5), libcairo2 (>= 1.2.4), libenchant1c2a (>= 1.5), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.8.0), libpango1.0-0 (>= 1.14.0), zlib1g (>= 1:1.1.4)
Size: 17508
Description: a spell-checking addon for GTK's TextView widget
 GtkSpell provides MSWord/MacOSX-style highlighting of misspelled words in a
 GtkTextView widget.  Right-clicking a misspelled word pops up a menu of
 suggested replacements.
Original-Maintainer: Ari Pollak <ari@debian.org>

Package: python-pkg-resources
Priority: optional
Section: python
Installed-Size: 208
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: distribute
Version: 0.6.10-4ubuntu1
Replaces: python2.3-setuptools, python2.4-setuptools
Provides: python2.6-setuptools
Depends: python (>= 2.6), python (<< 2.7), python-central (>= 0.6.11)
Suggests: python-distribute, python-distribute-doc
Conflicts: python-setuptools (<< 0.6c8-3), python2.3-setuptools (<< 0.6b2), python2.4-setuptools (<< 0.6b2)
Size: 64956
Description: Package Discovery and Resource Access using pkg_resources
 The pkg_resources module provides an API for Python libraries to
 access their resource files, and for extensible applications and
 frameworks to automatically discover plugins.  It also provides
 runtime support for using C extensions that are inside zipfile-format
 eggs, support for merging packages that have separately-distributed
 modules or subpackages, and APIs for managing Python's current
 "working set" of active packages.
Original-Maintainer: Matthias Klose <doko@debian.org>
Homepage: http://packages.python.org/distribute
Python-Version: 2.6

Package: tcpd
Priority: standard
Section: net
Installed-Size: 200
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: tcp-wrappers
Version: 7.6.q-18
Replaces: libwrap0 (<< 7.6-8)
Depends: libc6 (>= 2.4), libwrap0 (>= 7.6-4~)
Size: 71578
Description: Wietse Venema's TCP wrapper utilities
 Wietse Venema's network logger, also known as TCPD or LOG_TCP.
 .
 These programs log the client host name of incoming telnet,
 ftp, rsh, rlogin, finger etc. requests.
 .
 Security options are:
  - access control per host, domain and/or service;
  - detection of host name spoofing or host address spoofing;
  - booby traps to implement an early-warning system.
Original-Maintainer: Marco d'Itri <md@linux.it>

Package: python-twisted-conch
Priority: optional
Section: python
Installed-Size: 1496
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: twisted-conch
Version: 1:10.0.0-2ubuntu1
Replaces: python2.3-twisted (<< 2.2), python2.3-twisted-conch, python2.4-twisted-conch
Provides: conch
Depends: python, python-central (>= 0.6.11), python-crypto (>= 2.0.1+dfsg1-1.1), python-pyasn1, python-twisted-core (>= 10.0.0-2ubuntu1)
Conflicts: python2.3-twisted (<< 2.2), python2.3-twisted-conch, python2.4-twisted-conch
Size: 263976
Description: The Twisted SSH Implementation
 A client/server implementation of the SSH protocol, using the
 twisted framework.
Original-Maintainer: Matthias Klose <doko@debian.org>
Python-Version: all

Package: mysql-client-core-5.1
Priority: optional
Section: database
Installed-Size: 360
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: mysql-dfsg-5.1
Version: 5.1.69-0ubuntu0.10.04.1
Replaces: mysql-client (<< 5.1.69-0ubuntu0.10.04.1), mysql-client-5.0, mysql-client-5.1 (<< 5.1.41-3ubuntu12)
Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libmysqlclient16 (>= 5.1.69-0ubuntu0.10.04.1), libncurses5 (>= 5.6+20071006-3), libreadline6 (>= 6.0), libstdc++6 (>= 4.1.1), zlib1g (>= 1:1.1.4)
Conflicts: mysql-client (<< 5.1.69-0ubuntu0.10.04.1), mysql-client-5.0
Size: 169960
Description: MySQL database core client binaries
 MySQL is a fast, stable and true multi-user, multi-threaded SQL database
 server. SQL (Structured Query Language) is the most popular database query
 language in the world. The main goals of MySQL are speed, robustness and
 ease of use.
 .
 This package includes the core client files, as used by Akonadi.
Homepage: http://dev.mysql.com/
Original-Maintainer: Debian MySQL Maintainers <pkg-mysql-maint@lists.alioth.debian.org>

Package: libbonoboui2-0
Priority: optional
Section: libs
Installed-Size: 528
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: amd64
Source: libbonoboui
Version: 2.24.3-0ubuntu1
Replaces: libbonoboui2-common (<= 2.4.3-1)
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.29.3), libbonobo2-0 (>= 2.15.0), libc6 (>= 2.7), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgconf2-4 (>= 2.27.0), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.23.5), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgtk2.0-0 (>= 2.18.0), libice6 (>= 1:1.0.0), liborbit2 (>= 1:2.14.10), libpango1.0-0 (>= 1.14.0), libpopt0 (>= 1.15), libsm6, libx11-6 (>= 0), libxml2 (>= 2.7.4), zlib1g (>= 1:1.1.4), libbonoboui2-common (>= 2.24), libbonoboui2-common (<< 2.25)
Size: 193368
Description: The Bonobo UI library
 This package corick@rick-desktop:~$  
```

These results concern me! Especially because it lists things more like a "status" than an "info" output.
Also alarming is the last line of the results seems to be cut-off, before the command line, as though there is corruption!!
 
I tried your command twice, just to be sure that I didn't enter it incorrectly... Something is wrong here, don't you think?

shobuz99

---

### Post by Bashing-om on 2013-08-26
Shobuz99; That blows me away also !

for reference:
> 
sysop@1304mini:~$ cat /var/lib/dpkg/info/gedit.list
/.
/usr
/usr/bin
/usr/bin/gedit
/usr/lib
/usr/lib/gedit
/usr/lib/gedit/plugins
/usr/lib/gedit/plugins/docinfo.plugin
/usr/lib/gedit/plugins/libfilebrowser.so
/usr/lib/gedit/plugins/externaltools.plugin
/usr/lib/gedit/plugins/pythonconsole.plugin
/usr/lib/gedit/plugins/libchangecase.so
/usr/lib/gedit/plugins/quickopen
/usr/lib/gedit/plugins/quickopen/popup.py
/usr/lib/gedit/plugins/quickopen/__init__.py
/usr/lib/gedit/plugins/quickopen/virtualdirs.py
/usr/lib/gedit/plugins/snippets.plugin
<snip>

Should have had an out put similar.
 - not counting my reference package is "gedit"

How in the world this could have come about I have not a clue ... as earlier we had rebuilt the "list" index !

once more - with feeling- :
```

sudo apt-get clean
sudo cd /var/lib/apt
sudo mv lists lists.old2
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
cd ##to return to your your home directory as the Present Working Directory
sudo apt-get upgrade ##yeah yeah .. just to see and get a new status.

```

As to weather that will also rebuild "/var/lib/dpkg/info/" ... remains to be seen ... open to learning !

EDIT: 2nd thought ...
I had assumed that the whole index file was corrupt .. maybe take a look at a couple other files and see what they look like ??
I have an alternate plan in mind if this fails.

[INDENT][INDENT]what is will be seen
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-27
> **Bashing-om said:**
> Shobuz99; That blows me away also !

for reference:

Should have had an out put similar.
 - not counting my reference package is "gedit"

How in the world this could have come about I have not a clue ... as earlier we had rebuilt the "list" index !

once more - with feeling- :
```

sudo apt-get clean
sudo cd /var/lib/apt
sudo mv lists lists.old2
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
cd ##to return to your your home directory as the Present Working Directory
sudo apt-get upgrade ##yeah yeah .. just to see and get a new status.

```

As to weather that will also rebuild "/var/lib/dpkg/info/" ... remains to be seen ... open to learning !

EDIT: 2nd thought ...
I had assumed that the whole index file was corrupt .. maybe take a look at a couple other files and see what they look like ??
I have an alternate plan in mind if this fails.

[INDENT][INDENT]what is will be seen
[/INDENT][/INDENT]

Before I try running your command suggestions, I want to show you what I got with a hunch...

I ran the command "**[COLOR="#006400"]cat /var/lib/dpkg/info/icedtea*.list[/COLOR]**" using the * wildcard.
I tried this with the[COLOR="#B22222"] openjdk and got the aforementioned garbage.[/COLOR]
This result is much different and more in line with what we are seeking:

```
rick@rick-desktop:~$ **[COLOR="#006400"]cat /var/lib/dpkg/info/icedtea*.list[/COLOR]**
/.
/usr
/usr/lib
/usr/lib/jvm
/usr/lib/jvm/java-6-openjdk
/usr/lib/jvm/java-6-openjdk/jre
/usr/lib/jvm/java-6-openjdk/jre/man
/usr/lib/jvm/java-6-openjdk/jre/man/man1
/usr/lib/jvm/java-6-openjdk/jre/man/man1/javaws.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/itweb-settings.1.gz
/usr/lib/jvm/java-6-openjdk/jre/bin
/usr/lib/jvm/java-6-openjdk/jre/bin/javaws
/usr/lib/jvm/java-6-openjdk/jre/bin/itweb-settings
/usr/lib/jvm/java-6-openjdk/man
/usr/lib/jvm/java-6-openjdk/man/man1
/usr/lib/jvm/java-6-openjdk/bin
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/applications
/usr/share/applications/itweb-settings.desktop
/usr/share/applications/icedtea-netx-javaws.desktop
/usr/share/mime-info
/usr/share/mime-info/icedtea-netx-web-start.mime
/usr/share/mime-info/icedtea-netx-web-start.keys
/usr/share/icedtea-web
/usr/share/icedtea-web/about.jar
/usr/share/icedtea-web/netx.jar
/usr/share/icedtea-web/about.jnlp
/usr/share/doc
/usr/share/doc/icedtea-netx
/usr/share/doc/icedtea-netx/copyright
/usr/share/doc/icedtea-netx/NEWS.gz
/usr/share/doc/icedtea-netx/README.gz
/usr/share/doc/icedtea-netx/AUTHORS
/usr/share/doc/icedtea-netx/changelog.Debian.gz
/usr/share/icons
/usr/share/icons/hicolor
/usr/share/icons/hicolor/16x16
/usr/share/icons/hicolor/16x16/apps
/usr/share/icons/hicolor/16x16/apps/javaws.png
/usr/share/icons/hicolor/24x24
/usr/share/icons/hicolor/24x24/apps
/usr/share/icons/hicolor/24x24/apps/javaws.png
/usr/share/icons/hicolor/48x48
/usr/share/icons/hicolor/48x48/apps
/usr/share/icons/hicolor/48x48/apps/javaws.png
/usr/share/icons/hicolor/32x32
/usr/share/icons/hicolor/32x32/apps
/usr/share/icons/hicolor/32x32/apps/javaws.png
/usr/share/application-registry
/usr/share/application-registry/icedtea-netx-web-start.applications
/usr/bin
/etc
/etc/icedtea-web
/etc/icedtea-web/javaws.policy
/usr/lib/jvm/java-6-openjdk/man/man1/javaws.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/itweb-settings.gz
/usr/lib/jvm/java-6-openjdk/bin/javaws
rick@rick-desktop:~$ 
```

What clues, if any, does this result provide you?

I will run your suggested commands after your reply to this inquiry, ok?

BTW.. What do you think of Jonathan's suggested commands in his previous post?

Thank you very much for sticking with me..

shobuz99

---

### Post by Bashing-om on 2013-08-27
Shobuz99; Morning to you.

cat /var/lib/dpkg/info/icedtea*.list -> good output
cat /var/lib/dpkg/info/openjdk-6-jre-headless.list -> bad output

Tells me that at some point we have copied the "status" file of 'openjdk-6-jre-headless' to the "info" file by accident and in error.

If that is the only erroneous index file within "/var/lib/dpkg/info/" ; we can safely delete that entry and it will be re-inserted when we purge/(re)install.
But, there is the need to look about and see if perhaps any of the other entries are invalid. If all else is good there is no need to do my last advisement to rebuild that database.

As to Jonathan's advise. I am not conversant with "awk" -I do not have the ability to follow the variable assignments - and am not qualified in that respect to make a judgement. I look forward to Jonathan returning and explaining the sequence to us.

[INDENT][INDENT]we have a plan !
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-27
> **Bashing-om said:**
> Shobuz99; Morning to you.

cat /var/lib/dpkg/info/icedtea*.list -> good output
cat /var/lib/dpkg/info/openjdk-6-jre-headless.list -> bad output

Tells me that at some point we have copied the "status" file of 'openjdk-6-jre-headless' to the "info" file by accident and in error.

If that is the only erroneous index file within "/var/lib/dpkg/info/" ; we can safely delete that entry and it will be re-inserted when we purge/(re)install.
But, there is the need to look about and see if perhaps any of the other entries are invalid. If all else is good there is no need to do my last advisement to rebuild that database.

As to Jonathan's advise. I am not conversant with "awk" -I do not have the ability to follow the variable assignments - and am not qualified in that respect to make a judgement. I look forward to Jonathan returning and explaining the sequence to us.

[INDENT][INDENT]we have a plan !
[/INDENT][/INDENT]

Ok. I wasn't sure how to go about seeing if any other entries in the "info" folder are 'invalid'...
How do i do that without running the same "cat" command for each pkg that I may have? 
That could be labor intensive. 

I decided to try skimming through the info folder and finding the *.list files.
I changed dir to /var/lib/dpkg/info, first. Then I began searching for list files for "open*.list 

```
rick@rick-desktop:/var/lib/dpkg/info$ ls -la open*.list
[B]-rw-r--r-- 1 root root   9116 2013-05-08 14:53 openjdk-6-jre-headless.list
-rw-r--r-- 1 root root   2276 2013-05-08 14:53 openjdk-6-jre.list[/B]
-rw-r--r-- 1 root root    423 2010-09-21 08:04 openoffice.org-base-core.list
-rw-r--r-- 1 root root   3350 2010-09-21 08:04 openoffice.org-base.list
-rw-r--r-- 1 root root   3889 2010-09-21 08:04 openoffice.org-calc.list
-rw-r--r-- 1 root root 208661 2010-09-21 08:04 openoffice.org-common.list
-rw-r--r-- 1 root root  10786 2010-09-21 08:05 openoffice.org-core.list
-rw-r--r-- 1 root root   3501 2010-09-21 08:04 openoffice.org-draw.list
-rw-r--r-- 1 root root   1035 2010-09-21 08:04 openoffice.org-emailmerge.list
-rw-r--r-- 1 root root   4598 2010-09-21 08:04 openoffice.org-filter-binfilter.list
-rw-r--r-- 1 root root   1866 2010-09-21 08:05 openoffice.org-filter-mobiledev.list
-rw-r--r-- 1 root root    758 2010-09-21 08:04 openoffice.org-gnome.list
-rw-r--r-- 1 root root    780 2010-09-21 08:04 openoffice.org-gtk.list
-rw-r--r-- 1 root root   5360 2010-08-26 09:20 openoffice.org-help-en-gb.list
-rw-r--r-- 1 root root   5090 2010-08-26 09:20 openoffice.org-help-en-us.list
-rw-r--r-- 1 root root      0 2010-05-08 15:23 openoffice.org-hyphenation-en-us.list
-rw-r--r-- 1 root root   2886 2010-05-08 15:02 openoffice.org-hyphenation.list
-rw-r--r-- 1 root root   3849 2010-09-21 08:04 openoffice.org-impress.list
-rw-r--r-- 1 root root   3888 2010-09-21 08:04 openoffice.org-java-common.list
-rw-r--r-- 1 root root    568 2010-08-26 09:19 openoffice.org-l10n-common.list
-rw-r--r-- 1 root root  24388 2010-08-26 09:20 openoffice.org-l10n-en-gb.list
-rw-r--r-- 1 root root  26083 2010-08-26 09:19 openoffice.org-l10n-en-za.list
-rw-r--r-- 1 root root    185 2010-09-21 08:04 openoffice.org.list
-rw-r--r-- 1 root root   3125 2010-09-21 08:04 openoffice.org-math.list
-rw-r--r-- 1 root root    671 2010-09-21 08:04 openoffice.org-officebean.list
-rw-r--r-- 1 root root    562 2010-09-21 08:05 openoffice.org-report-builder-bin.list
-rw-r--r-- 1 root root    375 2010-09-21 08:04 openoffice.org-style-galaxy.list
-rw-r--r-- 1 root root    378 2010-09-21 08:04 openoffice.org-style-human.list
-rw-r--r-- 1 root root    479 2010-05-08 14:55 openoffice.org-thesaurus-en-au.list
-rw-r--r-- 1 root root    528 2010-07-15 08:45 openoffice.org-thesaurus-en-us.list
-rw-r--r-- 1 root root   4534 2010-09-21 08:04 openoffice.org-writer.list
-rw-r--r-- 1 root root  27735 2010-05-08 14:48 openprinting-ppds.list
-rw-r--r-- 1 root root   7624 2010-10-10 13:23 openshot-doc.list
-rw-r--r-- 1 root root  50865 2010-10-10 13:23 openshot.list
-rw-r--r-- 1 root root   1660 2011-06-17 12:59 openssh-client.list
-rw-r--r-- 1 root root   1115 2009-10-31 22:59 openssl-blacklist.list
-rw-r--r-- 1 root root   2453 2013-06-14 09:44 openssl.list
rick@rick-desktop:/var/lib/dpkg/info$ 
```

This tells me that there is a corruption of some kind, going on, because we got garbage previously for openjdk.
**Notice that the file date is August 8th 2013. Isn't that about when i started this thread?**
I then tried the same procedure for iced*.list

```
rick@rick-desktop:/var/lib/dpkg/info$ ls -la iced*.list
-rw-r--r-- 1 root root  587 2011-03-24 11:46 icedax.list
-rw-r--r-- 1 root root 1964 2013-04-19 19:34 icedtea-netx.list
```

This appears to be in order. However, I don't find these files when using the commands
that I used previously (a page or two back).

Part of my frustration is that I get a deja vu when searching and getting results from commands
that we've tried multiple times. I am also feeling like we should go through a list of commands
that one at a time, in logical order, can give us a clear picture of what we have.
Once that is done, I think we can start to narrow down whether there are any other damaged DB's or packages.
Does that sound reasonable?
If so, then would you put a list of commands together for what we have already tried, and then
let me run them, get the results and post them, so you can advise me what I should do?

Unless you have a solution or an idea that I am clueless to understand. I still respect your efforts
and your work thus far, and I don't want to be the director of this investigation.

Also, some new information.
I ran my "clamtk" anti-malware on my /home/rick directory, recursively.
It found a trojan in the [COLOR="#B22222"][I]/home/rick/.wine/drive_c/Program Files/Macromedia/Flash MX 2004/Players/Release/FlashLite1.0/SAFlashLite.exe      Win.Trojan.Downloader-26326 
[/I][/COLOR]

I don't know for certain that this had ANY effect at all on the problem at hand...
but I felt I should mention it, anyway, so as to rule it out or in at some point.

I hope I haven't clouded the issues at hand. I want to proceed and try to delete/remove the 
files or folder that is messing with our heads and then try restoring the DB to some semblance of normal.

Thank you, Bashing-om for your continued support.  
I also would like to revisit what bapoumba suggested and see if that too, aligns with what Jonathan suggested.


Shobuz99

---

### Post by Bashing-om on 2013-08-27
Shobuz99; Hey !

I also had the thought to clear our heads .. and start from square one once more .. I just did not want to needlessly add to your frustration level.

Your last:"-rw-r--r-- 1 root root   9116 2013-05-08 14:53 openjdk-6-jre-headless.list" -> we know that the file exist, however, the data contained in that existing file is invalid.

Let me have a bit to consider ... I am thinking that before we go back to square one .. to go ahead and rebuild both index database files, before that perhaps we should address the architecture (32 bit libraries required on your 64 bit system) situation ... maybe there are dependencies there that are interfering with what we are currently trying to resolve.

I need to do this step by step so I do not loose, in all the confusion, what the current focus is.

Let me see if perhaps that  openjdk-6-jre is not a part of the 32 bit libraries .. Like I cautioned at the start of this thread .. many times we are flying by the seat of our pants ..and having to feel our way in the dark ... not having access to a testing environment on my part complicates things.

inter-dependency -> chicken or the egg; does openjdk-6-jre depend on the 32 bit libs or do the libs depend on openjdk-6-jre ???

I need to find out before doing anything else at this point.

[INDENT]reducing to simplest terms, it really is not all that bad
 [/INDENT]

---

### Post by Bashing-om on 2013-08-27
Shobuz99; Here we go:
doing  "apt-cache depends openjdk-6-jre" and  "apt-cache depends icedtea-6-jre-cacao" says our focus in on openjdk,
openjdk-6-jre depends on openjdk-6-jre-headless ->
I find no direct dependency between openjdk and 32lib:
so, let us proceed as:
a) remove the offending file in /var/lib/dpkg/info/;
```

sudo rm /var/lib/dpkg/info/openjdk-6-jre-headless.list

```
b) check file integrity of openjdk-6-jre and icedtea-6-jre-cacao
```

cat /var/lib/dpkg/info/openjdk-6-jre ##is it in path filename structure , no garbage characters ??
less  /var/lib/dpkg/status/ ## search for the 3 files in question, must have a blank line between the stanzas,
##any blank lines within the stanza must have a "." period character within that stanza, and
##conform in syntax to the other stanzas present in that file. Do they all look good ??
sudo apt-get update
sudo apt-get install --reinstall openjdk-6-jre-headless ##as well as any others that have been found corrupted.

```
Now to deal with the 32 bit architecture ..
```

sudo dpkg --add-architecture i386
##to see if installed 32lib:
sudo dpkg --print-foreign-architectures

```

stop, pause, take a deep breath and see where we are now !

---

### Post by Jonathan Precise on 2013-08-27
> **Bashing-om said:**
> Shobuz99; Morning to you.

cat /var/lib/dpkg/info/icedtea*.list -> good output
cat /var/lib/dpkg/info/openjdk-6-jre-headless.list -> bad output

Tells me that at some point we have copied the "status" file of 'openjdk-6-jre-headless' to the "info" file by accident and in error.

If that is the only erroneous index file within "/var/lib/dpkg/info/" ; we can safely delete that entry and it will be re-inserted when we purge/(re)install.
But, there is the need to look about and see if perhaps any of the other entries are invalid. If all else is good there is no need to do my last advisement to rebuild that database.

As to Jonathan's advise. I am not conversant with "awk" -I do not have the ability to follow the variable assignments - and am not qualified in that respect to make a judgement. I look forward to Jonathan returning and explaining the sequence to us.
[INDENT][INDENT]we have a plan !
[/INDENT]
[/INDENT]


Did you read my last edit?

I just followed the links bapoumpa gave us, and just put it into two commands (adjusted the program name as well).

---

### Post by Bashing-om on 2013-08-27
@ Jonathan Precise;
No I had not caught up with the edits to your posting. Jonathan, my communications skills are horrible, and in no way is my intent to be a discredit to you or the efforts you put forth in our behalf.

I am not conversant with the utility "awk" and can not follow those variable assignments in the provided code. I will not pass onto another any code I do not completely understand.

We are in the Absolute Beginners section and this forum also functions as an institute of teaching, and though the problem may be deep and involved, keeping to a level that is simple and easier to understand is my philosophy.

[INDENT][INDENT]bad code has been passed in the past and I want not to be a party thereof presently 
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-27
> **Bashing-om said:**
> Shobuz99; Here we go:
doing  "apt-cache depends openjdk-6-jre" and  "apt-cache depends icedtea-6-jre-cacao" says our focus in on openjdk,
openjdk-6-jre depends on openjdk-6-jre-headless ->
I find no direct dependency between openjdk and 32lib:
so, let us proceed as:
a) remove the offending file in /var/lib/dpkg/info/;
```

sudo rm /var/lib/dpkg/info/openjdk-6-jre-headless.list

```
b) check file integrity of openjdk-6-jre and icedtea-6-jre-cacao
```

cat /var/lib/dpkg/info/openjdk-6-jre ##is it in path filename structure , no garbage characters ??
less  /var/lib/dpkg/status/ ## search for the 3 files in question, must have a blank line between the stanzas,
##any blank lines within the stanza must have a "." period character within that stanza, and
##conform in syntax to the other stanzas present in that file. Do they all look good ??
sudo apt-get update
sudo apt-get install --reinstall openjdk-6-jre-headless ##as well as any others that have been found corrupted.

```
Now to deal with the 32 bit architecture ..
```

sudo dpkg --add-architecture i386
##to see if installed 32lib:
sudo dpkg --print-foreign-architectures

```

stop, pause, take a deep breath and see where we are now !

Ok. I only went so far, because the results were not expected:

```
rick@rick-desktop:~$ sudo rm /var/lib/dpkg/info/openjdk-6-jre-headless.list
[sudo] password for rick: 
rick@rick-desktop:~$ cat /var/lib/dpkg/info/openjdk-6-jre
cat: /var/lib/dpkg/info/openjdk-6-jre: No such file or directory
rick@rick-desktop:~$ 

```

What's next for Step 3?

shobuz99

---

### Post by Bashing-om on 2013-08-27
Shobuz99;
Well.. not a major big deal at present that "cat: /var/lib/dpkg/info/openjdk-6-jre: No such file or directory" recon it saves the trouble to remove it.
What is the status of  "/var/lib/dpkg/info/icedtea-6-jre-cacao" and remove that file too .

Ok, what says /var/lib/dpkg/status about :
openjdk-6-jre
openjdk-6-jre-headless
icedtea-6-jre-cacao
and howbout we go ahead once more and delete the stanza'a (leave a blank line between the stanzas), once more make a backup .. just in case.
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-old2
##and (re-)install all
sudo apt-get update ##to refresh the databases
apt-get install --reinstall openjdk-6-jre-headless
apt-get install --reinstall openjdk-6-jre
apt-get install --reinstall icedtea-6-jre-cacao

```
in that order to keep the dependencies in line.
Hope we are not doing too much at one time .. we will see what is.

I have not forgotten the other issues you raised, for now this is what I can deal with; We will return to them.
Get these snakes stomped out once again and back to the 32 bit libs.

[INDENT][INDENT][INDENT]any steps forward is good
[/INDENT][/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-28
> **Bashing-om said:**
> Shobuz99;
Well.. not a major big deal at present that "cat: /var/lib/dpkg/info/openjdk-6-jre: No such file or directory" recon it saves the trouble to remove it.
What is the status of  "/var/lib/dpkg/info/icedtea-6-jre-cacao" and remove that file too .

Ok, what says /var/lib/dpkg/status about :
openjdk-6-jre
openjdk-6-jre-headless
icedtea-6-jre-cacao
and how about we go ahead once more and delete the stanza's (leave a blank line between the stanzas), once more make a backup .. just in case.
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-old2
##and (re-)install all
sudo apt-get update ##to refresh the databases
apt-get install --reinstall openjdk-6-jre-headless
apt-get install --reinstall openjdk-6-jre
apt-get install --reinstall icedtea-6-jre-cacao

```
in that order to keep the dependencies in line.
Hope we are not doing too much at one time .. we will see what is.

I have not forgotten the other issues you raised, for now this is what I can deal with; We will return to them.
Get these snakes stomped out once again and back to the 32 bit libs.

[INDENT][INDENT][INDENT]any steps forward is good
[/INDENT][/INDENT][/INDENT]

Ok. Your first question: 
> What is the status of  "/var/lib/dpkg/info/icedtea-6-jre-cacao" and remove that file too .

Answer:
```
rick@rick-desktop:~$ cat /var/lib/dpkg/info/icedtea-6-jre-cacao
cat: /var/lib/dpkg/info/icedtea-6-jre-cacao: No such file or directory
rick@rick-desktop:~$ 

```

Next:
> Ok, what says /var/lib/dpkg/status about :
openjdk-6-jre
openjdk-6-jre-headless
icedtea-6-jre-cacao

Did you mean ls -la /var/lib/dpkg/status?

I tried:
ls -la /var/lib/dpkg/status/openjdk-6-jre
ls -la /var/lib/dpkg/status/openjdk-6-jre-headless
ls -la /var/lib/dpkg/status/icedtea-6-jre-cacao

Results:
```
rick@rick-desktop:~$ ls -la /var/lib/dpkg/status/openjdk-6-jre
ls: cannot access /var/lib/dpkg/status/openjdk-6-jre: Not a directory
rick@rick-desktop:~$ ls -la /var/lib/dpkg/status/openjdk-6-jre-headless
ls: cannot access /var/lib/dpkg/status/openjdk-6-jre-headless: Not a directory
rick@rick-desktop:~$ ls -la /var/lib/dpkg/status/icedtea-6-jre-cacao
ls: cannot access /var/lib/dpkg/status/icedtea-6-jre-cacao: Not a directory
rick@rick-desktop:~$ 
```

So.. I continued on assuming everything was clear...guess not.
First, I ran 
> sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-old2

Next I ran:

> sudo apt-get update

```
Hit http://old-releases.ubuntu.com lucid Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-updates Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-backports Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-proposed Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Hit http://old-releases.ubuntu.com lucid Release
Hit http://old-releases.ubuntu.com lucid-updates Release
Hit http://old-releases.ubuntu.com lucid-backports Release
Hit http://old-releases.ubuntu.com lucid-security Release
Hit http://old-releases.ubuntu.com lucid-proposed Release
Hit http://old-releases.ubuntu.com lucid/main Packages
Hit http://old-releases.ubuntu.com lucid/restricted Packages
Hit http://old-releases.ubuntu.com lucid/universe Packages
Hit http://old-releases.ubuntu.com lucid/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-updates/main Packages
Hit http://old-releases.ubuntu.com lucid-updates/restricted Packages
Hit http://old-releases.ubuntu.com lucid-updates/universe Packages
Hit http://old-releases.ubuntu.com lucid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-backports/main Packages
Hit http://old-releases.ubuntu.com lucid-backports/restricted Packages
Hit http://old-releases.ubuntu.com lucid-backports/universe Packages
Hit http://old-releases.ubuntu.com lucid-backports/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Packages
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/restricted Packages
Hit http://old-releases.ubuntu.com lucid-proposed/main Packages
Hit http://old-releases.ubuntu.com lucid-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/universe Packages
Reading package lists... Done
rick@rick-desktop:
```

Next:
> sudo apt-get install --reinstall openjdk-6-jre-headless

Results
```
rick@rick-desktop:~$ **sudo apt-get install --reinstall openjdk-6-jre-headless**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome-terminal: Depends: gnome-terminal-data (>= 2.30) but it is not going to be installed
                  Depends: gnome-terminal-data (< 2.31) but it is not going to be installed
  libgnomevfs2-common: Depends: gnome-mime-data but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
rick@rick-desktop:~$ **sudo apt-get install --reinstall openjdk-6-jre**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome-terminal: Depends: gnome-terminal-data (>= 2.30) but it is not going to be installed
                  Depends: gnome-terminal-data (< 2.31) but it is not going to be installed
  libgnomevfs2-common: Depends: gnome-mime-data but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
rick@rick-desktop:~$ **sudo apt-get install --reinstall icedtea-6-jre-cacao**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome-terminal: Depends: gnome-terminal-data (>= 2.30) but it is not going to be installed
                  Depends: gnome-terminal-data (< 2.31) but it is not going to be installed
  libgnomevfs2-common: Depends: gnome-mime-data but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
rick@rick-desktop:~$ 
```

Ok. I'm pretty much ready to throw in the towel or try Jonathan Precise's solution.
We're still going in circles and frankly I can't keep track of what we've done anymore...
Sorry, Bashing-om but this is not working out.

Shobuz99

---

### Post by newb85 on 2013-08-28
The sources should be
```
deb http://old-releases.ubuntu.com lucid somerepo
```

not

```
deb http://*us.*old-releases.ubuntu.com lucid somerepo
```


As a side note, are you sure you've been receiving updates for all desktop packages, not just for the server packages?  If you're no longer receiving updates for your browser, for example, that should be a security concern...

---

### Post by Bashing-om on 2013-08-28
@ newb85 ...Thanks for the input, we caught the bad reference for the sourcelist.. got that fixed ... just stuck now on dependency issues. Going round and around .. have not got to the bottom of it yet !

@ Shobuz99; Let us take the package manager's directive and look at  "gnome-terminal-data" and for once find out why we can not get it to install.

For now I really want to get this 32 bit libraries out of the way .. now that might possibly be where the hang up is ...lots and lots of things have their fingers in the terminal.
do:
```

sudo dpkg --add-architecture i386
##to see if installed 32lib:
sudo dpkg --print-foreign-architectures

```

Won't take but a bit .. then see where we are at in regards to "gnome-terminal" starting that one from square 1 once more.
In respect to that possible virus in "Wine" ...I do not know, for a fact, but. I have yet to hear of a virus in "Wine" affecting ubuntu's operating system. I would not know how one would deal with it as I have never had that experience.

[INDENT][INDENT]In time, we will get to the bottom[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-28
> **Bashing-om said:**
> @ newb85 ...Thanks for the input, we caught the bad reference for the sourcelist.. got that fixed ... just stuck now on dependency issues. Going round and around .. have not got to the bottom of it yet !

@ Shobuz99; Let us take the package manager's directive and look at  "gnome-terminal-data" and for once find out why we can not get it to install.

For now I really want to get this 32 bit libraries out of the way .. now that might possibly be where the hang up is ...lots and lots of things have their fingers in the terminal.
do:
```

sudo dpkg --add-architecture i386
##to see if installed 32lib:
sudo dpkg --print-foreign-architectures

```

Won't take but a bit .. then see where we are at in regards to "gnome-terminal" starting that one from square 1 once more.
In respect to that possible virus in "Wine" ...I do not know, for a fact, but. I have yet to hear of a virus in "Wine" affecting ubuntu's operating system. I would not know how one would deal with it as I have never had that experience.

[INDENT][INDENT]In time, we will get to the bottom[/INDENT][/INDENT]

it's very confusing to me why this command doesn't work?

```
rick@rick-desktop:~$ sudo dpkg --add-architecture i386
[sudo] password for rick: 
dpkg: unknown option --add-architecture

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
rick@rick-desktop:~$ 
```

I can't proceed until the syntax of the command is correct.

shobuz99

---

### Post by Bashing-om on 2013-08-28
Don't know ... looks right ... lemme see what I can find out ... I agree the output is confusing.
Be back soonest

---

### Post by Jonathan Precise on 2013-08-28
Hello bashing-om and shobuz99!

I just made a Virtual machine (its ubuntu 10.10 though, I couldn't find my 10.04 LTS CD:sad:), and intentionally corrupted my openjdk-6-jre-headless.list (keeping a backup, of course).

So I tried running the code. However, it didn't do so well {bash: syntax error near unexpected token "(" }. So I decided to post my backup of openjdk-6-jre-headless.list. I hopen its the same for ubuntu 10.04 and 10.10:wink: (just in case it isn't, [SIZE=5]_**BACKUP YOUR OLD openjdk-6-jre-headless.list!!!!!!!!!**_[/SIZE] Do this by running ```
sudo cp /var/lib/dpkg/info/openjdk-6-jre-headless.list /var/lib/dpkg/info/openjdk-6-jre-headless-backup.list
```).

Edit: once backed up put the code into your real openjdk-6-jre-headless.list (as the upload of the file failed):

```
/.
/usr
/usr/share
/usr/share/binfmts
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/openjdk-6-jre-headless
/usr/share/doc
/usr/share/doc/openjdk-6-jre-headless
/usr/share/doc/openjdk-6-jre-headless/AUTHORS.IcedTea
/usr/share/doc/openjdk-6-jre-headless/copyright
/usr/share/doc/openjdk-6-jre-headless/NEWS.IcedTea.gz
/usr/share/doc/openjdk-6-jre-headless/README.alternatives
/usr/share/doc/openjdk-6-jre-headless/README.Debian
/usr/share/doc/openjdk-6-jre-headless/JAVA_HOME
/usr/share/doc/openjdk-6-jre-headless/README.IcedTea.gz
/usr/share/doc/openjdk-6-jre-headless/changelog.Debian.gz
/usr/lib
/usr/lib/jvm
/usr/lib/jvm/java-6-openjdk
/usr/lib/jvm/java-6-openjdk/bin
/usr/lib/jvm/java-6-openjdk/bin/java-rmi.cgi
/usr/lib/jvm/java-6-openjdk/jre
/usr/lib/jvm/java-6-openjdk/jre/bin
/usr/lib/jvm/java-6-openjdk/jre/bin/pack200
/usr/lib/jvm/java-6-openjdk/jre/bin/keytool
/usr/lib/jvm/java-6-openjdk/jre/bin/unpack200
/usr/lib/jvm/java-6-openjdk/jre/bin/java
/usr/lib/jvm/java-6-openjdk/jre/bin/orbd
/usr/lib/jvm/java-6-openjdk/jre/bin/rmiregistry
/usr/lib/jvm/java-6-openjdk/jre/bin/servertool
/usr/lib/jvm/java-6-openjdk/jre/bin/rmid
/usr/lib/jvm/java-6-openjdk/jre/bin/tnameserv
/usr/lib/jvm/java-6-openjdk/jre/man
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/unpack200.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/servertool.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/tnameserv.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/rmid.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/pack200.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/keytool.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/java.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/orbd.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/rmiregistry.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1
/usr/lib/jvm/java-6-openjdk/jre/man/man1/unpack200.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/servertool.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/tnameserv.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/rmid.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/pack200.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/keytool.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/java.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/orbd.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/rmiregistry.1.gz
/usr/lib/jvm/java-6-openjdk/jre/lib
/usr/lib/jvm/java-6-openjdk/jre/lib/i386
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libhprof.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnpt.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/jvm.cfg-default
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava_crw_demo.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsound.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/headless
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/headless/libmawt.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/Xusage.txt
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/server
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/Xusage.txt
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsig.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libunpack.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libmlib_image.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjaas_unix.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libattach.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2gss.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/librmi.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libmanagement.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libinstrument.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libdt_socket.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjdwp.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libsaproc.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pcsc.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
/usr/lib/jvm/java-6-openjdk/jre/lib/management
/usr/lib/jvm/java-6-openjdk/jre/lib/security
/usr/lib/jvm/java-6-openjdk/jre/lib/images
/usr/lib/jvm/java-6-openjdk/jre/lib/images/cursors
/usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
/usr/lib/jvm/java-6-openjdk/jre/lib/jexec
/usr/lib/jvm/java-6-openjdk/jre/lib/jar.binfmt
/usr/lib/jvm/java-6-openjdk/man
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1
/usr/lib/jvm/java-6-openjdk/man/man1
/usr/lib/jvm/.java-6-openjdk.jinfo
/etc
/etc/java-6-openjdk
/etc/java-6-openjdk/swing.properties
/etc/java-6-openjdk/logging.properties
/etc/java-6-openjdk/flavormap.properties
/etc/java-6-openjdk/psfontj2d.properties
/etc/java-6-openjdk/jvm.cfg
/etc/java-6-openjdk/management
/etc/java-6-openjdk/management/management.properties
/etc/java-6-openjdk/management/snmp.acl
/etc/java-6-openjdk/management/jmxremote.password
/etc/java-6-openjdk/management/jmxremote.access
/etc/java-6-openjdk/security
/etc/java-6-openjdk/security/nss.cfg
/etc/java-6-openjdk/security/java.policy
/etc/java-6-openjdk/security/java.security
/etc/java-6-openjdk/images
/etc/java-6-openjdk/images/cursors
/etc/java-6-openjdk/images/cursors/cursors.properties
/etc/java-6-openjdk/sound.properties
/etc/java-6-openjdk/fontconfig.bfc
/etc/java-6-openjdk/accessibility.properties
/etc/java-6-openjdk/calendars.properties
/etc/java-6-openjdk/psfont.properties.ja
/etc/java-6-openjdk/fontconfig.properties
/etc/java-6-openjdk/net.properties
/etc/java-6-openjdk/content-types.properties
/usr/lib/jvm/java-6-openjdk/bin/pack200
/usr/lib/jvm/java-6-openjdk/bin/keytool
/usr/lib/jvm/java-6-openjdk/bin/unpack200
/usr/lib/jvm/java-6-openjdk/bin/java
/usr/lib/jvm/java-6-openjdk/bin/orbd
/usr/lib/jvm/java-6-openjdk/bin/rmiregistry
/usr/lib/jvm/java-6-openjdk/bin/servertool
/usr/lib/jvm/java-6-openjdk/bin/rmid
/usr/lib/jvm/java-6-openjdk/bin/tnameserv
/usr/lib/jvm/java-6-openjdk/jre/man/ja
/usr/lib/jvm/java-6-openjdk/jre/lib/swing.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/logging.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/jvm.cfg
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjsig.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjsig.so
/usr/lib/jvm/java-6-openjdk/jre/lib/flavormap.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/psfontj2d.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/management/management.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/management/snmp.acl
/usr/lib/jvm/java-6-openjdk/jre/lib/management/jmxremote.password
/usr/lib/jvm/java-6-openjdk/jre/lib/management/jmxremote.access
/usr/lib/jvm/java-6-openjdk/jre/lib/security/nss.cfg
/usr/lib/jvm/java-6-openjdk/jre/lib/security/java.policy
/usr/lib/jvm/java-6-openjdk/jre/lib/security/java.security
/usr/lib/jvm/java-6-openjdk/jre/lib/security/cacerts
/usr/lib/jvm/java-6-openjdk/jre/lib/images/cursors/cursors.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/sound.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/fontconfig.bfc
/usr/lib/jvm/java-6-openjdk/jre/lib/accessibility.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/calendars.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/psfont.properties.ja
/usr/lib/jvm/java-6-openjdk/jre/lib/fontconfig.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/net.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/content-types.properties
/usr/lib/jvm/java-6-openjdk/docs
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/unpack200.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/servertool.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/tnameserv.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/rmid.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/pack200.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/keytool.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/java.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/orbd.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/rmiregistry.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/unpack200.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/servertool.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/tnameserv.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/rmid.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/pack200.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/keytool.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/java.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/orbd.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/rmiregistry.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja
/usr/lib/jvm/java-1.6.0-openjdk
```

---

### Post by Shobuz99 on 2013-08-29
> **Jonathan Precise said:**
> Hello bashing-om and shobuz99!

I just made a Virtual machine (its ubuntu 10.10 though, I couldn't find my 10.04 LTS CD:sad:), and intentionally corrupted my openjdk-6-jre-headless.list (keeping a backup, of course).

So I tried running the code. However, it didn't do so well {bash: syntax error near unexpected token "(" }. So I decided to post my backup of openjdk-6-jre-headless.list. I hopen its the same for ubuntu 10.04 and 10.10:wink: (just in case it isn't, [SIZE=5]_**BACKUP YOUR OLD openjdk-6-jre-headless.list!!!!!!!!!**_[/SIZE] Do this by running ```
sudo cp /var/lib/dpkg/info/openjdk-6-jre-headless.list /var/lib/dpkg/info/openjdk-6-jre-headless-backup.list
```).

Edit: once backed up put the code into your real openjdk-6-jre-headless.list (as the upload of the file failed):

```
/.
/usr
/usr/share
/usr/share/binfmts
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/openjdk-6-jre-headless
/usr/share/doc
/usr/share/doc/openjdk-6-jre-headless
/usr/share/doc/openjdk-6-jre-headless/AUTHORS.IcedTea
/usr/share/doc/openjdk-6-jre-headless/copyright
/usr/share/doc/openjdk-6-jre-headless/NEWS.IcedTea.gz
/usr/share/doc/openjdk-6-jre-headless/README.alternatives
/usr/share/doc/openjdk-6-jre-headless/README.Debian
/usr/share/doc/openjdk-6-jre-headless/JAVA_HOME
/usr/share/doc/openjdk-6-jre-headless/README.IcedTea.gz
/usr/share/doc/openjdk-6-jre-headless/changelog.Debian.gz
/usr/lib
/usr/lib/jvm
/usr/lib/jvm/java-6-openjdk
/usr/lib/jvm/java-6-openjdk/bin
/usr/lib/jvm/java-6-openjdk/bin/java-rmi.cgi
/usr/lib/jvm/java-6-openjdk/jre
/usr/lib/jvm/java-6-openjdk/jre/bin
/usr/lib/jvm/java-6-openjdk/jre/bin/pack200
/usr/lib/jvm/java-6-openjdk/jre/bin/keytool
/usr/lib/jvm/java-6-openjdk/jre/bin/unpack200
/usr/lib/jvm/java-6-openjdk/jre/bin/java
/usr/lib/jvm/java-6-openjdk/jre/bin/orbd
/usr/lib/jvm/java-6-openjdk/jre/bin/rmiregistry
/usr/lib/jvm/java-6-openjdk/jre/bin/servertool
/usr/lib/jvm/java-6-openjdk/jre/bin/rmid
/usr/lib/jvm/java-6-openjdk/jre/bin/tnameserv
/usr/lib/jvm/java-6-openjdk/jre/man
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/unpack200.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/servertool.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/tnameserv.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/rmid.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/pack200.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/keytool.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/java.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/orbd.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/ja_JP.eucJP/man1/rmiregistry.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1
/usr/lib/jvm/java-6-openjdk/jre/man/man1/unpack200.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/servertool.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/tnameserv.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/rmid.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/pack200.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/keytool.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/java.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/orbd.1.gz
/usr/lib/jvm/java-6-openjdk/jre/man/man1/rmiregistry.1.gz
/usr/lib/jvm/java-6-openjdk/jre/lib
/usr/lib/jvm/java-6-openjdk/jre/lib/i386
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libhprof.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnpt.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/jvm.cfg-default
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava_crw_demo.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsound.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/headless
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/headless/libmawt.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/Xusage.txt
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/server
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/Xusage.txt
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsig.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libunpack.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libmlib_image.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjaas_unix.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libattach.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2gss.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/librmi.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libmanagement.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libinstrument.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libdt_socket.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjdwp.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libsaproc.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pcsc.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
/usr/lib/jvm/java-6-openjdk/jre/lib/management
/usr/lib/jvm/java-6-openjdk/jre/lib/security
/usr/lib/jvm/java-6-openjdk/jre/lib/images
/usr/lib/jvm/java-6-openjdk/jre/lib/images/cursors
/usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
/usr/lib/jvm/java-6-openjdk/jre/lib/jexec
/usr/lib/jvm/java-6-openjdk/jre/lib/jar.binfmt
/usr/lib/jvm/java-6-openjdk/man
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1
/usr/lib/jvm/java-6-openjdk/man/man1
/usr/lib/jvm/.java-6-openjdk.jinfo
/etc
/etc/java-6-openjdk
/etc/java-6-openjdk/swing.properties
/etc/java-6-openjdk/logging.properties
/etc/java-6-openjdk/flavormap.properties
/etc/java-6-openjdk/psfontj2d.properties
/etc/java-6-openjdk/jvm.cfg
/etc/java-6-openjdk/management
/etc/java-6-openjdk/management/management.properties
/etc/java-6-openjdk/management/snmp.acl
/etc/java-6-openjdk/management/jmxremote.password
/etc/java-6-openjdk/management/jmxremote.access
/etc/java-6-openjdk/security
/etc/java-6-openjdk/security/nss.cfg
/etc/java-6-openjdk/security/java.policy
/etc/java-6-openjdk/security/java.security
/etc/java-6-openjdk/images
/etc/java-6-openjdk/images/cursors
/etc/java-6-openjdk/images/cursors/cursors.properties
/etc/java-6-openjdk/sound.properties
/etc/java-6-openjdk/fontconfig.bfc
/etc/java-6-openjdk/accessibility.properties
/etc/java-6-openjdk/calendars.properties
/etc/java-6-openjdk/psfont.properties.ja
/etc/java-6-openjdk/fontconfig.properties
/etc/java-6-openjdk/net.properties
/etc/java-6-openjdk/content-types.properties
/usr/lib/jvm/java-6-openjdk/bin/pack200
/usr/lib/jvm/java-6-openjdk/bin/keytool
/usr/lib/jvm/java-6-openjdk/bin/unpack200
/usr/lib/jvm/java-6-openjdk/bin/java
/usr/lib/jvm/java-6-openjdk/bin/orbd
/usr/lib/jvm/java-6-openjdk/bin/rmiregistry
/usr/lib/jvm/java-6-openjdk/bin/servertool
/usr/lib/jvm/java-6-openjdk/bin/rmid
/usr/lib/jvm/java-6-openjdk/bin/tnameserv
/usr/lib/jvm/java-6-openjdk/jre/man/ja
/usr/lib/jvm/java-6-openjdk/jre/lib/swing.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/logging.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/jvm.cfg
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjsig.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjsig.so
/usr/lib/jvm/java-6-openjdk/jre/lib/flavormap.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/psfontj2d.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/management/management.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/management/snmp.acl
/usr/lib/jvm/java-6-openjdk/jre/lib/management/jmxremote.password
/usr/lib/jvm/java-6-openjdk/jre/lib/management/jmxremote.access
/usr/lib/jvm/java-6-openjdk/jre/lib/security/nss.cfg
/usr/lib/jvm/java-6-openjdk/jre/lib/security/java.policy
/usr/lib/jvm/java-6-openjdk/jre/lib/security/java.security
/usr/lib/jvm/java-6-openjdk/jre/lib/security/cacerts
/usr/lib/jvm/java-6-openjdk/jre/lib/images/cursors/cursors.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/sound.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/fontconfig.bfc
/usr/lib/jvm/java-6-openjdk/jre/lib/accessibility.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/calendars.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/psfont.properties.ja
/usr/lib/jvm/java-6-openjdk/jre/lib/fontconfig.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/net.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/content-types.properties
/usr/lib/jvm/java-6-openjdk/docs
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/unpack200.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/servertool.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/tnameserv.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/rmid.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/pack200.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/keytool.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/java.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/orbd.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/rmiregistry.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/unpack200.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/servertool.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/tnameserv.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/rmid.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/pack200.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/keytool.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/java.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/orbd.1.gz
/usr/lib/jvm/java-6-openjdk/man/man1/rmiregistry.1.gz
/usr/lib/jvm/java-6-openjdk/man/ja
/usr/lib/jvm/java-1.6.0-openjdk
```

thanks Jonathan, but this is too late. I've already removed openjdk headless...I think.
Besides, i haven't tried your initial suggestion, yet (your first post). 
@Bashing-om has been perplexed, I'm confused and frustrated, and I haven't heard from @bapoumba in a while.
At this point I'm at a standstill and very depressed about being on merry-go-round.
 
I don't dare to try anything that I don't completely understand. No offense intended.
Convince me that the logical sequence of actions I need to take will solve my problem.
Then I'll use your suggestion.
BTW...My laptop is also 10.04 LTS and a 32 bit machine. 
Today I just got an Update Mgr notice on my laptop, for Linux kernel image for version 2.6.32-51 generic!!
Why is Ubuntu 10.04 LTS still updating??? I thought it was EOL. I thought the updates would stop when the version reached end of life??
Explain this to me... somebody.

shobuz99

---

### Post by Jonathan Precise on 2013-08-29
> **Shobuz99 said:**
> thanks Jonathan, but this is too late. I've already removed openjdk headless...I think.
Besides, i haven't tried your initial suggestion, yet (your first post). 
@Bashing-om has been perplexed, I'm confused and frustrated, and I haven't heard from @bapoumba in a while.
At this point I'm at a standstill and very depressed about being on merry-go-round.
 
I don't dare to try anything that I don't completely understand. No offense intended.
Convince me that the logical sequence of actions I need to take will solve my problem.
Then I'll use your suggestion.
BTW...My laptop is also 10.04 LTS and a 32 bit machine. 
Today I just got an Update Mgr notice on my laptop, for Linux kernel image for version 2.6.32-51 generic!!
Why is Ubuntu 10.04 LTS still updating??? I thought it was EOL. I thought the updates would stop when the version reached end of life??
Explain this to me... somebody.

shobuz99


It doesn't hurt to try my first post. However, it will not fix your problem (I tried it yesterday, returned a syntax error).

The reason that it will work is that it is the **_original, undamaged_** version of the openjdk-6-jre-headless.list.

As for the update-manager on the EOL, I might have an explanation:

Ubuntu 10.04 LTS is no longer supported on the **_desktop_**. However, there are still 2 years left on the **_server_**. So the update-manager might be looking on the **_server_** updates (Ubuntu Desktop is the same as Ubuntu Server, but with a GUI installed). Server updates include linux-kernels and other basic stuff ubuntu needs. Updates for stuff like gnome, firefox, GUI's, or other graphical programs are _**NOT GOING TO BE UPDATED**_ unless you change:

```
***us.archive.ubuntu.com/ubuntu*** lucid **_main_...**
```

to:

```
***old-releases.ubuntu.com/ubuntu*** lucid _**main**_**...**
```

Replace **...** with the rest that comes after _**main**_.

---

### Post by bapoumba on 2013-08-30
> **Shobuz99 said:**
> t
@Bashing-om has been perplexed, I'm confused and frustrated, and I haven't heard from @bapoumba in a while.
At this point I'm at a standstill and very depressed about being on merry-go-round.


Sorry, I've been out of town at the beginning of the week for work and will be out again today. Without any reliable internet connection other than my phone, it is not easy to follow, search and comment. Will be home late tonight, for the WE.

I can understand your feelings. Please do not get depressed :)

---

### Post by Bashing-om on 2013-08-30
Happy Friday to all !

Pleased to see all this support .. 5 minds beats 2 every time !

I remain focused on insuring that the 32 bit libraries are not at the heart of our problem.
In respect to "foreign-architectures" the command "sudo dpkg --add-architecture i386" is valid for multiarch enabled kernels. Version 10.04 is not multiarch and for the "foreign-architectures" ; It relies on "ia32-libs". 

To that end I want to look at their dependencies and make sure all is in place.
```

sudo apt-cache policy ia32-libs
dpkg -s ia32-libs
dpkg --listfiles ia32-libs

```
Then compare those out puts to what is supposed to be installed as per these docs:
[http://packages.ubuntu.com/lucid/libs/ia32-libs](http://packages.ubuntu.com/lucid/libs/ia32-libs)
[http://packages.ubuntu.com/lucid-updates/ia32-libs](http://packages.ubuntu.com/lucid-updates/ia32-libs)

We are just looking right now ... It concerns me deeply if intervention is required with system libraries. Will then proceed with the utmost caution. Horror stories abound when a thoughtless action has destroyed the operating system.

[INDENT][INDENT]erring on the side of caution
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-08-31
> **Bashing-om said:**
> Happy Friday to all !

Pleased to see all this support .. 5 minds beats 2 every time !

I remain focused on insuring that the 32 bit libraries are not at the heart of our problem.
In respect to "foreign-architectures" the command "sudo dpkg --add-architecture i386" is valid for multiarch enabled kernels. Version 10.04 is not multiarch and for the "foreign-architectures" ; It relies on "ia32-libs". 

To that end I want to look at their dependencies and make sure all is in place.
```

sudo apt-cache policy ia32-libs
dpkg -s ia32-libs
dpkg --listfiles ia32-libs

```
Then compare those out puts to what is supposed to be installed as per these docs:
[http://packages.ubuntu.com/lucid/libs/ia32-libs](http://packages.ubuntu.com/lucid/libs/ia32-libs)
[http://packages.ubuntu.com/lucid-updates/ia32-libs](http://packages.ubuntu.com/lucid-updates/ia32-libs)

We are just looking right now ... It concerns me deeply if intervention is required with system libraries. Will then proceed with the utmost caution. Horror stories abound when a thoughtless action has destroyed the operating system.

[INDENT][INDENT]erring on the side of caution
[/INDENT][/INDENT]

I'm sorry I haven't been on. Some personal tragedies have kept me busy.
Even so, I would like to get this resolved asap.
So...
Results of the first line of code that your provided, Bashing-om:
```
rick@rick-desktop:~$ sudo apt-cache policy ia32-libs
[sudo] password for rick: 
ia32-libs:
  Installed: 2.7ubuntu26.2
  Candidate: 2.7ubuntu26.2
  Version table:
 *** 2.7ubuntu26.2 0
        100 /var/lib/dpkg/status
     2.7ubuntu26.1 0
        500 http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Packages
        500 http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Packages
     2.7ubuntu25 0
        500 http://old-releases.ubuntu.com/ubuntu/ lucid/universe Packages
rick@rick-desktop:~$ 

```

Next:```
rick@rick-desktop:~$ dpkg -s ia32-libs
Package: ia32-libs
Status: install ok installed
Priority: extra
Section: libs
Installed-Size: 155952
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 2.7ubuntu26.2
Replaces: ia32-libs-dev (<< 1.6), ia32-libs-openoffice.org, nvidia-glx-ia32 (<< 1.0.8774-7)
Provides: ia32-libs-gtk, ia32-libs-sdl
Depends: lsb-release, lib32gcc1, libc6-i386 (>= 2.3.6-2), lib32z1, lib32stdc++6, lib32asound2, lib32bz2-1.0, lib32ncurses5, lib32v4l-0
Pre-Depends: dpkg (>= 1.14.12ubuntu3)
Conflicts: ia32-libs-dev (<< 1.6), lib32asound2-plugins, nvidia-glx-ia32 (<< 1.0.8774-7)
Description: ia32 shared libraries for use on amd64 and ia64 systems
 This package contains runtime libraries for the ia32/i386
 architecture, configured for use on an amd64 or ia64 Debian system running
 a 64-bit kernel.
Original-Maintainer: Debian ia32-libs Team <pkg-ia32-libs-maintainers@lists.alioth.debian.org>
rick@rick-desktop:~$ 
```

And last:
```
/.
/lib32
/lib32/libuuid.so.1.3.0
/lib32/libdrm_intel.so.1.0.0
/lib32/libpcre.so.3.12.1
/lib32/i686
/lib32/i686/cmov
/lib32/i686/cmov/libcrypto.so.0.9.8
/lib32/i686/cmov/libssl.so.0.9.8
/lib32/libpamc.so.0.82.1
/lib32/libdrm_radeon.so.1.0.0
/lib32/libusb-0.1.so.4.4.4
/lib32/libwrap.so.0.7.6
/lib32/libexpatw.so.1.5.2
/lib32/libudev.so.0.6.1
/lib32/libpng12.so.0.42.0
/lib32/libdrm.so.2.4.0
/lib32/libcap.so.2.17
/lib32/libacl.so.1.1.0
/lib32/libsepol.so.1
/lib32/libcom_err.so.2.1
/lib32/udev
/lib32/udev/check-mtp-device
/lib32/udev/rules.d
/lib32/udev/rules.d/90-pulseaudio.rules
/lib32/udev/rules.d/40-libsane.rules
/lib32/udev/rules.d/40-libgphoto2-2.rules
/lib32/libgpg-error.so.0.4.0
/lib32/i486
/lib32/i486/libcrypto.so.0.9.8
/lib32/i486/libssl.so.0.9.8
/lib32/libpam_misc.so.0.82.0
/lib32/libdbus-1.so.3.4.0
/lib32/libpopt.so.0.0.0
/lib32/libattr.so.1.1.0
/lib32/libgcrypt.so.11.5.2
/lib32/libpam.so.0.82.2
/lib32/i586
/lib32/i586/libcrypto.so.0.9.8
/lib32/i586/libssl.so.0.9.8
/lib32/libx86.so.1
/lib32/security
/lib32/security/pam_ldap.so
/lib32/libcrypto.so.0.9.8
/lib32/libnss_ldap-2.11.1.so
/lib32/libexpat.so.1.5.2
/lib32/libglib-2.0.so.0.2400.1
/lib32/libaio.so.1.0.1
/lib32/libkeyutils-1.2.so
/lib32/libselinux.so.1
/lib32/libdrm_nouveau.so.1.0.0
/lib32/libssl.so.0.9.8
/usr
/usr/share
/usr/share/doc
/usr/share/doc/ia32-libs
/usr/share/doc/ia32-libs/Manifest.ia32-libs.gz
/usr/share/doc/ia32-libs/changelog.gz
/usr/share/doc/ia32-libs/copyright
/usr/share/doc/ia32-libs/README.Debian
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/ia32-libs
/usr/lib32
/usr/lib32/jack
/usr/lib32/jack/jack_oss.so
/usr/lib32/jack/intime.so
/usr/lib32/jack/jack_dummy.so
/usr/lib32/jack/inprocess.so
/usr/lib32/jack/jack_alsa.so
/usr/lib32/jack/jack_net.so
/usr/lib32/libQtXmlPatterns.so.4.6.2
/usr/lib32/libkrb5.so.3.3
/usr/lib32/libodbcinst.so.1.0.0
/usr/lib32/libQtScript.so.4.6.2
/usr/lib32/libxslt.so.1.1.26
/usr/lib32/libSDL_ttf-2.0.so.0.6.3
/usr/lib32/libgstnet-0.10.so.0.24.1
/usr/lib32/libcspi.so.0.10.11
/usr/lib32/libgstpbutils-0.10.so.0.19.2
/usr/lib32/libIDL-2.so.0.0.0
/usr/lib32/libasyncns.so.0.1.0
/usr/lib32/libpulsecommon-0.9.21.so
/usr/lib32/libgdk-x11-2.0.so.0.2000.1
/usr/lib32/libexslt.so.0.8.15
/usr/lib32/libkrb5support.so.0.1
/usr/lib32/libXcomposite.so.1.0.0
/usr/lib32/krb5
/usr/lib32/krb5/plugins
/usr/lib32/krb5/plugins/krb5
/usr/lib32/krb5/plugins/preauth
/usr/lib32/krb5/plugins/preauth/encrypted_challenge.so
/usr/lib32/libvorbis.so.0.4.3
/usr/lib32/libatk-1.0.so.0.3009.1
/usr/lib32/libgdk_pixbuf-2.0.so.0.2000.1
/usr/lib32/libglade
/usr/lib32/libglade/2.0
/usr/lib32/libglade/2.0/libcanvas.so
/usr/lib32/gstreamer0.10
/usr/lib32/gstreamer0.10/gstreamer-0.10
/usr/lib32/gstreamer0.10/gstreamer-0.10/gst-plugin-scanner
/usr/lib32/libfltk_forms.so.1.1
/usr/lib32/libSDL_mixer-1.2.so.0.2.6
/usr/lib32/libpulsedsp.so
/usr/lib32/libvga.so.1.4.3
/usr/lib32/AuErrorDB
/usr/lib32/bonobo
/usr/lib32/bonobo/monikers
/usr/lib32/bonobo/monikers/libmoniker_std_2.so
/usr/lib32/bonobo/servers
/usr/lib32/bonobo/servers/Bonobo_CosNaming_NamingContext.server
/usr/lib32/bonobo/servers/Accessibility_Registry.server
/usr/lib32/bonobo/servers/Bonobo_Sample_Echo.server
/usr/lib32/bonobo/servers/Bonobo_Moniker_std.server
/usr/lib32/libXinerama.so.1.0.0
/usr/lib32/liblcms.so.1.0.18
/usr/lib32/libplc4.so
/usr/lib32/libssl3.so
/usr/lib32/gcc
/usr/lib32/gcc/i486-linux-gnu
/usr/lib32/gcc/i486-linux-gnu/4.4
/usr/lib32/libdirect-1.2.so.0.8.0
/usr/lib32/gtk-2.0
/usr/lib32/gtk-2.0/2.10.0
/usr/lib32/gtk-2.0/2.10.0/immodules
/usr/lib32/gtk-2.0/2.10.0/immodules/im-thai.so
/usr/lib32/gtk-2.0/2.10.0/immodules/im-ipa.so
/usr/lib32/gtk-2.0/2.10.0/immodules/im-ti-er.so
/usr/lib32/gtk-2.0/2.10.0/immodules/im-xim.so
/usr/lib32/gtk-2.0/2.10.0/immodules/im-ti-et.so
/usr/lib32/gtk-2.0/2.10.0/immodules/im-cyrillic-translit.so
/usr/lib32/gtk-2.0/2.10.0/immodules/im-viqr.so
/usr/lib32/gtk-2.0/2.10.0/immodules/im-cedilla.so
/usr/lib32/gtk-2.0/2.10.0/immodules/im-multipress.so
/usr/lib32/gtk-2.0/2.10.0/immodules/im-inuktitut.so
/usr/lib32/gtk-2.0/2.10.0/immodules/im-am-et.so
/usr/lib32/gtk-2.0/2.10.0/printbackends
/usr/lib32/gtk-2.0/2.10.0/printbackends/libprintbackend-cups.so
/usr/lib32/gtk-2.0/2.10.0/printbackends/libprintbackend-test.so
/usr/lib32/gtk-2.0/2.10.0/printbackends/libprintbackend-file.so
/usr/lib32/gtk-2.0/2.10.0/printbackends/libprintbackend-lpr.so
/usr/lib32/gtk-2.0/2.10.0/loaders
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-ico.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-tiff.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-qtif.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-jasper.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-ani.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-icns.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-pcx.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-bmp.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-wbmp.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-xbm.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-tga.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-ras.so
/usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-pnm.so
/usr/lib32/gtk-2.0/2.10.0/immodule-files.d
/usr/lib32/gtk-2.0/2.10.0/immodule-files.d/libgtk2.0-0.immodules
/usr/lib32/gtk-2.0/2.10.0/loader-files.d
/usr/lib32/gtk-2.0/2.10.0/loader-files.d/librsvg2-common.loaders
/usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
/usr/lib32/gtk-2.0/2.10.0/engines
/usr/lib32/gtk-2.0/2.10.0/engines/libindustrial.so
/usr/lib32/gtk-2.0/2.10.0/engines/libmurrine.so
/usr/lib32/gtk-2.0/2.10.0/engines/libclearlooks.so
/usr/lib32/gtk-2.0/2.10.0/engines/libglide.so
/usr/lib32/gtk-2.0/2.10.0/engines/libsvg.so
/usr/lib32/gtk-2.0/2.10.0/engines/libthinice.so
/usr/lib32/gtk-2.0/2.10.0/engines/libmist.so
/usr/lib32/gtk-2.0/2.10.0/engines/libpixmap.so
/usr/lib32/gtk-2.0/2.10.0/engines/libluaengine.so
/usr/lib32/gtk-2.0/2.10.0/engines/libredmond95.so
/usr/lib32/gtk-2.0/2.10.0/engines/libcrux-engine.so
/usr/lib32/gtk-2.0/2.10.0/engines/libhcengine.so
/usr/lib32/gtk-2.0/modules
/usr/lib32/gtk-2.0/modules/libgail.so
/usr/lib32/gtk-2.0/modules/libcanberra-gtk-module.so
/usr/lib32/gtk-2.0/modules/libferret.so
/usr/lib32/libXp.so.6.2.0
/usr/lib32/libpulse.so.0.12.2
/usr/lib32/libsmime3.so
/usr/lib32/libbonobo-activation.so.4.0.0
/usr/lib32/libgstapp-0.10.so.0.19.2
/usr/lib32/libmikmod.so.2.0.4
/usr/lib32/libgdbm.so.3.0.0
/usr/lib32/mesa
/usr/lib32/mesa/libGL.so.1.2
/usr/lib32/mesa/ld.so.conf
/usr/lib32/libXaw3d.so.6.1
/usr/lib32/libgnome-keyring.so.0.1.1
/usr/lib32/libgstfft-0.10.so.0.19.2
/usr/lib32/libcups.so.2
/usr/lib32/libgthread-2.0.so.0.2400.1
/usr/lib32/libXdamage.so.1.1.0
/usr/lib32/libjpeg.so.62.0.0
/usr/lib32/pm-utils
/usr/lib32/pm-utils/sleep.d
/usr/lib32/pm-utils/sleep.d/01PulseAudio
/usr/lib32/libgtk-x11-2.0.so.0.2000.1
/usr/lib32/libSDL-1.2.so.0.11.3
/usr/lib32/libORBit-2.so.0.1.0
/usr/lib32/libQtScriptTools.so.4.6.2
/usr/lib32/libgstreamer-0.10.so.0.24.1
/usr/lib32/libgphoto2_port
/usr/lib32/libgphoto2_port/0.8.0
/usr/lib32/libgphoto2_port/0.8.0/ptpip.so
/usr/lib32/libgphoto2_port/0.8.0/serial.so
/usr/lib32/libgphoto2_port/0.8.0/usb.so
/usr/lib32/libgphoto2_port/0.8.0/disk.so
/usr/lib32/libQtCLucene.so.4.6.2
/usr/lib32/libgnutls-openssl.so.26.14.12
/usr/lib32/libcanberra-gtk.so.0.1.5
/usr/lib32/libXxf86vm.so.1.0.0
/usr/lib32/liblber-2.4.so.2.5.4
/usr/lib32/libvgagl.so.1.4.3
/usr/lib32/libsane.so.1.0.20
/usr/lib32/libao.so.2.1.3
/usr/lib32/libXmu.so.6.2.0
/usr/lib32/libieee1284.so.3.2.2
/usr/lib32/libltdl.so.7.2.1
/usr/lib32/libXtst.so.6.1.0
/usr/lib32/libQtOpenGL.so.4.6.2
/usr/lib32/libhal.so.1.0.0
/usr/lib32/libgslcblas.so.0.0.0
/usr/lib32/libgconf2-4
/usr/lib32/libgconf2-4/gconfd-2
/usr/lib32/libgconf2-4/gconf-sanity-check-2
/usr/lib32/libgconf2-4/2
/usr/lib32/libgconf2-4/2/libgconfbackend-evoldap.so
/usr/lib32/libgconf2-4/2/libgconfbackend-oldxml.so
/usr/lib32/libgconf2-4/2/libgconfbackend-xml.so
/usr/lib32/libldap_r-2.4.so.2.5.4
/usr/lib32/libfreetype.so.6.3.22
/usr/lib32/libgstbase-0.10.so.0.24.1
/usr/lib32/libjackserver.so.0.0.28
/usr/lib32/pulse-0.9.21
/usr/lib32/pulse-0.9.21/modules
/usr/lib32/pulse-0.9.21/modules/module-pipe-source.so
/usr/lib32/pulse-0.9.21/modules/module-cork-music-on-phone.so
/usr/lib32/pulse-0.9.21/modules/module-alsa-card.so
/usr/lib32/pulse-0.9.21/modules/module-loopback.so
/usr/lib32/pulse-0.9.21/modules/libprotocol-simple.so
/usr/lib32/pulse-0.9.21/modules/module-console-kit.so
/usr/lib32/pulse-0.9.21/modules/module-mmkbd-evdev.so
/usr/lib32/pulse-0.9.21/modules/module-rescue-streams.so
/usr/lib32/pulse-0.9.21/modules/module-detect.so
/usr/lib32/pulse-0.9.21/modules/module-stream-restore.so
/usr/lib32/pulse-0.9.21/modules/module-http-protocol-tcp.so
/usr/lib32/pulse-0.9.21/modules/module-remap-sink.so
/usr/lib32/pulse-0.9.21/modules/module-native-protocol-fd.so
/usr/lib32/pulse-0.9.21/modules/module-simple-protocol-unix.so
/usr/lib32/pulse-0.9.21/modules/module-rtp-send.so
/usr/lib32/pulse-0.9.21/modules/module-device-manager.so
/usr/lib32/pulse-0.9.21/modules/module-device-restore.so
/usr/lib32/pulse-0.9.21/modules/module-augment-properties.so
/usr/lib32/pulse-0.9.21/modules/module-null-sink.so
/usr/lib32/pulse-0.9.21/modules/module-rtp-recv.so
/usr/lib32/pulse-0.9.21/modules/librtp.so
/usr/lib32/pulse-0.9.21/modules/module-tunnel-source.so
/usr/lib32/pulse-0.9.21/modules/module-esound-sink.so
/usr/lib32/pulse-0.9.21/modules/module-card-restore.so
/usr/lib32/pulse-0.9.21/modules/libprotocol-cli.so
/usr/lib32/pulse-0.9.21/modules/module-ladspa-sink.so
/usr/lib32/pulse-0.9.21/modules/module-oss.so
/usr/lib32/pulse-0.9.21/modules/module-pipe-sink.so
/usr/lib32/pulse-0.9.21/modules/module-sine-source.so
/usr/lib32/pulse-0.9.21/modules/libprotocol-http.so
/usr/lib32/pulse-0.9.21/modules/module-alsa-source.so
/usr/lib32/pulse-0.9.21/modules/module-volume-restore.so
/usr/lib32/pulse-0.9.21/modules/module-http-protocol-unix.so
/usr/lib32/pulse-0.9.21/modules/liboss-util.so
/usr/lib32/pulse-0.9.21/modules/libalsa-util.so
/usr/lib32/pulse-0.9.21/modules/module-cli-protocol-unix.so
/usr/lib32/pulse-0.9.21/modules/module-cli-protocol-tcp.so
/usr/lib32/pulse-0.9.21/modules/module-native-protocol-unix.so
/usr/lib32/pulse-0.9.21/modules/libcli.so
/usr/lib32/pulse-0.9.21/modules/module-combine.so
/usr/lib32/pulse-0.9.21/modules/module-tunnel-sink.so
/usr/lib32/pulse-0.9.21/modules/module-always-sink.so
/usr/lib32/pulse-0.9.21/modules/module-suspend-on-idle.so
/usr/lib32/pulse-0.9.21/modules/module-alsa-sink.so
/usr/lib32/pulse-0.9.21/modules/module-cli.so
/usr/lib32/pulse-0.9.21/modules/module-rygel-media-server.so
/usr/lib32/pulse-0.9.21/modules/module-position-event-sounds.so
/usr/lib32/pulse-0.9.21/modules/module-default-device-restore.so
/usr/lib32/pulse-0.9.21/modules/module-sine.so
/usr/lib32/pulse-0.9.21/modules/module-simple-protocol-tcp.so
/usr/lib32/pulse-0.9.21/modules/module-udev-detect.so
/usr/lib32/pulse-0.9.21/modules/module-intended-roles.so
/usr/lib32/pulse-0.9.21/modules/libprotocol-native.so
/usr/lib32/pulse-0.9.21/modules/module-match.so
/usr/lib32/pulse-0.9.21/modules/module-native-protocol-tcp.so
/usr/lib32/libgnutls.so.26.14.12
/usr/lib32/libQtWebKit.so.4.6.2
/usr/lib32/odbc
/usr/lib32/odbc/libmimerS.so
/usr/lib32/odbc/libodbcminiS.so
/usr/lib32/odbc/libesoobS.so
/usr/lib32/odbc/liboraodbcS.so
/usr/lib32/odbc/libtdsS.so
/usr/lib32/odbc/libodbcdrvcfg1S.so
/usr/lib32/odbc/libodbcpsqlS.so
/usr/lib32/odbc/libodbcnnS.so
/usr/lib32/odbc/libsapdbS.so
/usr/lib32/odbc/libodbcdrvcfg2S.so
/usr/lib32/odbc/liboplodbcS.so
/usr/lib32/odbc/libodbctxtS.so
/usr/lib32/odbc/libodbcmyS.so
/usr/lib32/libpulse-mainloop-glib.so.0.0.4
/usr/lib32/libQtNetwork.so.4.6.2
/usr/lib32/libfltk.so.1.1
/usr/lib32/libbluetooth.so.3.5.0
/usr/lib32/libcairo.so.2.10800.10
/usr/lib32/libplds4.so
/usr/lib32/directfb-1.2-0
/usr/lib32/directfb-1.2-0/interfaces
/usr/lib32/directfb-1.2-0/interfaces/IDirectFBImageProvider
/usr/lib32/directfb-1.2-0/interfaces/IDirectFBImageProvider/libidirectfbimageprovider_dfiff.so
/usr/lib32/directfb-1.2-0/interfaces/IDirectFBImageProvider/libidirectfbimageprovider_gif.so
/usr/lib32/directfb-1.2-0/interfaces/IDirectFBFont
/usr/lib32/directfb-1.2-0/interfaces/IDirectFBFont/libidirectfbfont_default.so
/usr/lib32/directfb-1.2-0/interfaces/IDirectFBFont/libidirectfbfont_dgiff.so
/usr/lib32/directfb-1.2-0/interfaces/IDirectFBVideoProvider
/usr/lib32/directfb-1.2-0/interfaces/IDirectFBVideoProvider/libidirectfbvideoprovider_gif.so
/usr/lib32/directfb-1.2-0/interfaces/IDirectFBVideoProvider/libidirectfbvideoprovider_v4l.so
/usr/lib32/directfb-1.2-0/inputdrivers
/usr/lib32/directfb-1.2-0/inputdrivers/libdirectfb_joystick.so
/usr/lib32/directfb-1.2-0/inputdrivers/libdirectfb_linux_input.so
/usr/lib32/directfb-1.2-0/inputdrivers/libdirectfb_sonypi.so
/usr/lib32/directfb-1.2-0/inputdrivers/libdirectfb_wm97xx_ts.so
/usr/lib32/directfb-1.2-0/inputdrivers/libdirectfb_lirc.so
/usr/lib32/directfb-1.2-0/inputdrivers/libdirectfb_mutouch.so
/usr/lib32/directfb-1.2-0/inputdrivers/libdirectfb_penmount.so
/usr/lib32/directfb-1.2-0/inputdrivers/libdirectfb_tslib.so
/usr/lib32/directfb-1.2-0/inputdrivers/libdirectfb_serialmouse.so
/usr/lib32/directfb-1.2-0/inputdrivers/libdirectfb_keyboard.so
/usr/lib32/directfb-1.2-0/inputdrivers/libdirectfb_ps2mouse.so
/usr/lib32/directfb-1.2-0/wm
/usr/lib32/directfb-1.2-0/wm/libdirectfbwm_default.so
/usr/lib32/directfb-1.2-0/wm/libdirectfbwm_unique.so
/usr/lib32/directfb-1.2-0/systems
/usr/lib32/directfb-1.2-0/systems/libdirectfb_fbdev.so
/usr/lib32/directfb-1.2-0/systems/libdirectfb_devmem.so
/usr/lib32/directfb-1.2-0/gfxdrivers
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_vmware.so
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_i830.so
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_ati128.so
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_cyber5k.so
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_unichrome.so
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_radeon.so
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_i810.so
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_matrox.so
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_savage.so
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_ep9x.so
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_nvidia.so
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_tdfx.so
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_mach64.so
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_neomagic.so
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_sis315.so
/usr/lib32/directfb-1.2-0/gfxdrivers/libdirectfb_nsc.so
/usr/lib32/libgstcdda-0.10.so.0.19.2
/usr/lib32/libmad.so.0.2.1
/usr/lib32/libX11.so.6.3.0
/usr/lib32/libQtCore.so.4.6.2
/usr/lib32/dri
/usr/lib32/dri/mach64_dri.so
/usr/lib32/dri/r200_dri.so
/usr/lib32/dri/i965_dri.so
/usr/lib32/dri/sis_dri.so
/usr/lib32/dri/r300_dri.so
/usr/lib32/dri/i810_dri.so
/usr/lib32/dri/r128_dri.so
/usr/lib32/dri/radeon_dri.so
/usr/lib32/dri/swrast_dri.so
/usr/lib32/dri/tdfx_dri.so
/usr/lib32/dri/savage_dri.so
/usr/lib32/dri/unichrome_dri.so
/usr/lib32/dri/r600_dri.so
/usr/lib32/dri/mga_dri.so
/usr/lib32/dri/i915_dri.so
/usr/lib32/libsmpeg-0.4.so.0.1.4
/usr/lib32/gvfs
/usr/lib32/gvfs/gvfsd-localtest
/usr/lib32/gvfs/gvfs-gdu-volume-monitor
/usr/lib32/gvfs/gvfsd-computer
/usr/lib32/gvfs/gvfsd
/usr/lib32/gvfs/gvfsd-trash
/usr/lib32/gvfs/gvfsd-metadata
/usr/lib32/bonobo-activation
/usr/lib32/bonobo-activation/bonobo-activation-server
/usr/lib32/libcurl.so.4.1.1
/usr/lib32/libFLAC.so.8.2.0
/usr/lib32/libodbccr.so.1.0.0
/usr/lib32/libxcb.so.1.1.0
/usr/lib32/libidn.la
/usr/lib32/libpango-1.0.so.0.2800.0
/usr/lib32/libpangocairo-1.0.so.0.2800.0
/usr/lib32/libspeexdsp.so.1.5.0
/usr/lib32/libgstcontroller-0.10.so.0.24.1
/usr/lib32/libnss3.so
/usr/lib32/ao
/usr/lib32/ao/plugins-2
/usr/lib32/ao/plugins-2/liboss.so
/usr/lib32/ao/plugins-2/libesd.so
/usr/lib32/ao/plugins-2/libpulse.so
/usr/lib32/ao/plugins-2/libalsa09.so
/usr/lib32/ao/plugins-2/libnas.so
/usr/lib32/libdbus-glib-1.so.2.1.0
/usr/lib32/libxcb-render-util.so.0.0.0
/usr/lib32/xorg
/usr/lib32/xorg/x11-extra-modules
/usr/lib32/libICE.so.6.3.0
/usr/lib32/libSM.so.6.0.1
/usr/lib32/libtdb.so.1.2.0
/usr/lib32/pkgconfig
/usr/lib32/pkgconfig/gtk-engines-2.pc
/usr/lib32/libuniquewm-1.2.so.0.8.0
/usr/lib32/libgdk_pixbuf_xlib-2.0.so.0.2000.1
/usr/lib32/libpangoft2-1.0.so.0.2800.0
/usr/lib32/libfltk_gl.so.1.1
/usr/lib32/libXdmcp.so.6.0.0
/usr/lib32/libXrender.so.1.3.0
/usr/lib32/libaudiofile.so.0.0.2
/usr/lib32/libXi.so.6.1.0
/usr/lib32/gio
/usr/lib32/gio/modules
/usr/lib32/gio/modules/libgiogconf.so
/usr/lib32/gio/modules/libgvfsdbus.so
/usr/lib32/gio/modules/libgioremote-volume-monitor.so
/usr/lib32/libSDL_image-1.2.so.0.8.2
/usr/lib32/libXpm.so.4.11.0
/usr/lib32/libgdbm_compat.so.3.0.0
/usr/lib32/libfontconfig.so.1.4.4
/usr/lib32/libgio-2.0.so.0.2400.1
/usr/lib32/libQtGui.so.4.6.2
/usr/lib32/libsndfile.so.1.0.21
/usr/lib32/libavahi-common.so.3.5.1
/usr/lib32/libgstdataprotocol-0.10.so.0.24.1
/usr/lib32/libogg.so.0.6.0
/usr/lib32/libwmf-0.2.so.7.1.0
/usr/lib32/libpulsecore-0.9.21.so
/usr/lib32/liboil-0.3.so.0.3.0
/usr/lib32/libpcreposix.so.3.12.1
/usr/lib32/libodbc.so.1.0.0
/usr/lib32/libdirectfb-1.2.so.0.8.0
/usr/lib32/libtiff.so.4.3.2
/usr/lib32/libpixman-1.so.0.16.4
/usr/lib32/libgsf-1.so.114.0.16
/usr/lib32/libmpg123.so.0.25.0
/usr/lib32/libpangox-1.0.so.0.2800.0
/usr/lib32/libcanberra-0.22
/usr/lib32/libcanberra-0.22/libcanberra-alsa.so
/usr/lib32/libgstinterfaces-0.10.so.0.19.2
/usr/lib32/libssh2.so.1.0.1
/usr/lib32/libcroco-0.6.so.3.0.1
/usr/lib32/libGLU.so.1.3.070701
/usr/lib32/libglade-2.0.so.0.0.7
/usr/lib32/libgstaudio-0.10.so.0.19.2
/usr/lib32/libgvfscommon-dnssd.so.0.0.0
/usr/lib32/gstreamer-0.10
/usr/lib32/gstreamer-0.10/libgstcoreindexers.so
/usr/lib32/gstreamer-0.10/libgstcoreelements.so
/usr/lib32/libgobject-2.0.so.0.2400.1
/usr/lib32/libQtSvg.so.4.6.2
/usr/lib32/libgstvideo-0.10.so.0.19.2
/usr/lib32/libXt.so.6.0.0
/usr/lib32/libk5crypto.so.3.1
/usr/lib32/sasl2
/usr/lib32/sasl2/libsasldb.a
/usr/lib32/sasl2/libsasldb.so.2.0.23
/usr/lib32/sasl2/libsasldb.la
/usr/lib32/libgphoto2_port.so.0.8.0
/usr/lib32/libvorbisenc.so.2.0.6
/usr/lib32/libxml2.so.2.7.6
/usr/lib32/libgstrtsp-0.10.so.0.19.2
/usr/lib32/libgstnetbuffer-0.10.so.0.19.2
/usr/lib32/libQtTest.so.4.6.2
/usr/lib32/libspi.so.0.10.11
/usr/lib32/libgnomecanvas-2.so.0.3000.1
/usr/lib32/libXext.so.6.4.0
/usr/lib32/libdb-4.7.so
/usr/lib32/libgssapi_krb5.so.2.2
/usr/lib32/libtasn1.so.3.1.7
/usr/lib32/libgailutil.so.18.0.1
/usr/lib32/libgnutls-extra.so.26.14.12
/usr/lib32/alsa-lib
/usr/lib32/alsa-lib/libasound_module_pcm_vdownmix.so
/usr/lib32/alsa-lib/libasound_module_ctl_bluetooth.so
/usr/lib32/alsa-lib/libasound_module_rate_samplerate.so
/usr/lib32/alsa-lib/libasound_module_pcm_pulse.so
/usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
/usr/lib32/alsa-lib/libasound_module_rate_speexrate.so
/usr/lib32/alsa-lib/libasound_module_conf_pulse.so
/usr/lib32/alsa-lib/libasound_module_ctl_oss.so
/usr/lib32/alsa-lib/libasound_module_pcm_usb_stream.so
/usr/lib32/alsa-lib/libasound_module_pcm_jack.so
/usr/lib32/alsa-lib/libasound_module_pcm_speex.so
/usr/lib32/alsa-lib/libasound_module_ctl_arcam_av.so
/usr/lib32/alsa-lib/libasound_module_pcm_oss.so
/usr/lib32/alsa-lib/libasound_module_pcm_upmix.so
/usr/lib32/alsa-lib/libasound_module_ctl_pulse.so
/usr/lib32/at-spi
/usr/lib32/at-spi/at-spi-registryd
/usr/lib32/libglut.so.3.9.0
/usr/lib32/libpangoxft-1.0.so.0.2800.0
/usr/lib32/libgtrtst.so.1.0.0
/usr/lib32/libpulse-browse.so.0.1.1
/usr/lib32/libQt3Support.so.4.6.2
/usr/lib32/sane
/usr/lib32/sane/libsane-agfafocus.so.1.0.20
/usr/lib32/sane/libsane-ibm.la
/usr/lib32/sane/libsane-dell1600n_net.so.1.0.20
/usr/lib32/sane/libsane-net.so.1.0.20
/usr/lib32/sane/libsane-matsushita.so.1.0.20
/usr/lib32/sane/libsane-hs2p.so.1.0.20
/usr/lib32/sane/libsane-sm3600.la
/usr/lib32/sane/libsane-gphoto2.la
/usr/lib32/sane/libsane-u12.so.1.0.20
/usr/lib32/sane/libsane-plustek.so.1.0.20
/usr/lib32/sane/libsane-mustek_usb.la
/usr/lib32/sane/libsane-sharp.so.1.0.20
/usr/lib32/sane/libsane-dmc.so.1.0.20
/usr/lib32/sane/libsane-snapscan.so.1.0.20
/usr/lib32/sane/libsane-umax1220u.so.1.0.20
/usr/lib32/sane/libsane-dc210.la
/usr/lib32/sane/libsane-xerox_mfp.so.1.0.20
/usr/lib32/sane/libsane-teco2.so.1.0.20
/usr/lib32/sane/libsane-snapscan.la
/usr/lib32/sane/libsane-leo.so.1.0.20
/usr/lib32/sane/libsane-pixma.so.1.0.20
/usr/lib32/sane/libsane-niash.la
/usr/lib32/sane/libsane-ibm.so.1.0.20
/usr/lib32/sane/libsane-hp5400.so.1.0.20
/usr/lib32/sane/libsane-st400.so.1.0.20
/usr/lib32/sane/libsane-coolscan2.la
/usr/lib32/sane/libsane-umax1220u.la
/usr/lib32/sane/libsane-hpljm1005.so.1.0.20
/usr/lib32/sane/libsane-sceptre.la
/usr/lib32/sane/libsane-v4l.la
/usr/lib32/sane/libsane-hp5590.so.1.0.20
/usr/lib32/sane/libsane-hpsj5s.so.1.0.20
/usr/lib32/sane/libsane-mustek_usb2.la
/usr/lib32/sane/libsane-ma1509.la
/usr/lib32/sane/libsane-xerox_mfp.la
/usr/lib32/sane/libsane-mustek.so.1.0.20
/usr/lib32/sane/libsane-abaton.so.1.0.20
/usr/lib32/sane/libsane-gt68xx.so.1.0.20
/usr/lib32/sane/libsane-pie.la
/usr/lib32/sane/libsane-qcam.so.1.0.20
/usr/lib32/sane/libsane-pie.so.1.0.20
/usr/lib32/sane/libsane-v4l.so.1.0.20
/usr/lib32/sane/libsane-as6e.so.1.0.20
/usr/lib32/sane/libsane-mustek.la
/usr/lib32/sane/libsane-stv680.so.1.0.20
/usr/lib32/sane/libsane-s9036.so.1.0.20
/usr/lib32/sane/libsane-bh.so.1.0.20
/usr/lib32/sane/libsane-sp15c.so.1.0.20
/usr/lib32/sane/libsane-net.la
/usr/lib32/sane/libsane-coolscan.la
/usr/lib32/sane/libsane-canon.so.1.0.20
/usr/lib32/sane/libsane-st400.la
/usr/lib32/sane/libsane-mustek_pp.la
/usr/lib32/sane/libsane-coolscan.so.1.0.20
/usr/lib32/sane/libsane-canon.la
/usr/lib32/sane/libsane-artec.la
/usr/lib32/sane/libsane-ricoh.la
/usr/lib32/sane/libsane-u12.la
/usr/lib32/sane/libsane-hp4200.so.1.0.20
/usr/lib32/sane/libsane-agfafocus.la
/usr/lib32/sane/libsane-abaton.la
/usr/lib32/sane/libsane-dc25.so.1.0.20
/usr/lib32/sane/libsane-umax_pp.la
/usr/lib32/sane/libsane-apple.la
/usr/lib32/sane/libsane-cardscan.la
/usr/lib32/sane/libsane-dc240.la
/usr/lib32/sane/libsane-coolscan2.so.1.0.20
/usr/lib32/sane/libsane-sm3840.la
/usr/lib32/sane/libsane-epson2.la
/usr/lib32/sane/libsane-niash.so.1.0.20
/usr/lib32/sane/libsane-rts8891.so.1.0.20
/usr/lib32/sane/libsane-canon_pp.so.1.0.20
/usr/lib32/sane/libsane-umax.la
/usr/lib32/sane/libsane-teco3.la
/usr/lib32/sane/libsane-canon630u.so.1.0.20
/usr/lib32/sane/libsane-hp.la
/usr/lib32/sane/libsane-coolscan3.la
/usr/lib32/sane/libsane-umax.so.1.0.20
/usr/lib32/sane/libsane-hp3500.so.1.0.20
/usr/lib32/sane/libsane-microtek.la
/usr/lib32/sane/libsane-sm3840.so.1.0.20
/usr/lib32/sane/libsane-hp5400.la
/usr/lib32/sane/libsane-hp3900.la
/usr/lib32/sane/libsane-epson.la
/usr/lib32/sane/libsane-hs2p.la
/usr/lib32/sane/libsane-plustek.la
/usr/lib32/sane/libsane-gt68xx.la
/usr/lib32/sane/libsane-hp.so.1.0.20
/usr/lib32/sane/libsane-canon_dr.la
/usr/lib32/sane/libsane-hpsj5s.la
/usr/lib32/sane/libsane-dell1600n_net.la
/usr/lib32/sane/libsane-gphoto2.so.1.0.20
/usr/lib32/sane/libsane-coolscan3.so.1.0.20
/usr/lib32/sane/libsane-fujitsu.la
/usr/lib32/sane/libsane-hpljm1005.la
/usr/lib32/sane/libsane-stv680.la
/usr/lib32/sane/libsane-sm3600.so.1.0.20
/usr/lib32/sane/libsane-teco3.so.1.0.20
/usr/lib32/sane/libsane-genesys.la
/usr/lib32/sane/libsane-epson.so.1.0.20
/usr/lib32/sane/libsane-test.so.1.0.20
/usr/lib32/sane/libsane-artec.so.1.0.20
/usr/lib32/sane/libsane-qcam.la
/usr/lib32/sane/libsane-ricoh.so.1.0.20
/usr/lib32/sane/libsane-sp15c.la
/usr/lib32/sane/libsane-hp4200.la
/usr/lib32/sane/libsane-cardscan.so.1.0.20
/usr/lib32/sane/libsane-teco2.la
/usr/lib32/sane/libsane-avision.so.1.0.20
/usr/lib32/sane/libsane-genesys.so.1.0.20
/usr/lib32/sane/libsane-mustek_pp.so.1.0.20
/usr/lib32/sane/libsane-fujitsu.so.1.0.20
/usr/lib32/sane/libsane-canon_dr.so.1.0.20
/usr/lib32/sane/libsane-nec.so.1.0.20
/usr/lib32/sane/libsane-mustek_usb2.so.1.0.20
/usr/lib32/sane/libsane-rts8891.la
/usr/lib32/sane/libsane-tamarack.so.1.0.20
/usr/lib32/sane/libsane-epjitsu.la
/usr/lib32/sane/libsane-ma1509.so.1.0.20
/usr/lib32/sane/libsane-matsushita.la
/usr/lib32/sane/libsane-bh.la
/usr/lib32/sane/libsane-lexmark.la
/usr/lib32/sane/libsane-leo.la
/usr/lib32/sane/libsane-plustek_pp.so.1.0.20
/usr/lib32/sane/libsane-plustek_pp.la
/usr/lib32/sane/libsane-sharp.la
/usr/lib32/sane/libsane-canon_pp.la
/usr/lib32/sane/libsane-microtek2.so.1.0.20
/usr/lib32/sane/libsane-dc240.so.1.0.20
/usr/lib32/sane/libsane-artec_eplus48u.la
/usr/lib32/sane/libsane-dc25.la
/usr/lib32/sane/libsane-as6e.la
/usr/lib32/sane/libsane-microtek2.la
/usr/lib32/sane/libsane-artec_eplus48u.so.1.0.20
/usr/lib32/sane/libsane-dmc.la
/usr/lib32/sane/libsane-dmc.la
/usr/lib32/sane/libsane-pixma.la
/usr/lib32/sane/libsane-tamarack.la
/usr/lib32/sane/libsane-nec.la
/usr/lib32/sane/libsane-hp3900.so.1.0.20
/usr/lib32/sane/libsane-epson2.so.1.0.20
/usr/lib32/sane/libsane-avision.la
/usr/lib32/sane/libsane-sceptre.so.1.0.20
/usr/lib32/sane/libsane-dc210.so.1.0.20
/usr/lib32/sane/libsane-epjitsu.so.1.0.20
/usr/lib32/sane/libsane-lexmark.so.1.0.20
/usr/lib32/sane/libsane-hp3500.la
/usr/lib32/sane/libsane-umax_pp.so.1.0.20
/usr/lib32/sane/libsane-apple.so.1.0.20
/usr/lib32/sane/libsane-s9036.la
/usr/lib32/sane/libsane-test.la
/usr/lib32/sane/libsane-microtek.so.1.0.20
/usr/lib32/sane/libsane-mustek_usb.so.1.0.20
/usr/lib32/sane/libsane-teco1.la
/usr/lib32/sane/libsane-hp5590.la
/usr/lib32/sane/libsane-teco1.so.1.0.20
/usr/lib32/sane/libsane-canon630u.la
/usr/lib32/libgsm.so.1.0.12
/usr/lib32/libgtk2.0-0
/usr/lib32/libgtk2.0-0/update-gdkpixbuf-loaders
/usr/lib32/libgtk2.0-0/gtk-update-icon-cache
/usr/lib32/libgtk2.0-0/update-gtk-immodules
/usr/lib32/libgtk2.0-0/gtk-query-immodules-2.0
/usr/lib32/libgtk2.0-0/gdk-pixbuf-query-loaders
/usr/lib32/libgconf-2.so.4.1.5
/usr/lib32/libjack.so.0.0.28
/usr/lib32/libgstcheck-0.10.so.0.24.1
/usr/lib32/libfusion-1.2.so.0.8.0
/usr/lib32/libnssutil3.so
/usr/lib32/libcupsimage.so.2
/usr/lib32/libsamplerate.so.0.1.7
/usr/lib32/libXrandr.so.2.2.0
/usr/lib32/libaudio.so.2.4
/usr/lib32/libopenal.so.1.12.854
/usr/lib32/libXaw7.so.7.0.0
/usr/lib32/libXv.so.1.0.0
/usr/lib32/libfltk_images.so.1.1
/usr/lib32/libgvfscommon.so.0.0.0
/usr/lib32/libXm.so.2.0.1
/usr/lib32/libgmodule-2.0.so.0.2400.1
/usr/lib32/libsmbios.so.2.1.0
/usr/lib32/sse2
/usr/lib32/sse2/libspeexdsp.so.1.5.0
/usr/lib32/libnspr4.so
/usr/lib32/libgphoto2.so.2.4.0
/usr/lib32/libsqlite3.so.0.8.6
/usr/lib32/libgstsdp-0.10.so.0.19.2
/usr/lib32/libgstriff-0.10.so.0.19.2
/usr/lib32/libORBit-imodule-2.so.0.0.0
/usr/lib32/libwmflite-0.2.so.7.0.1
/usr/lib32/libcapi20.so.3.0.4
/usr/lib32/libpulse-simple.so.0.0.3
/usr/lib32/orbit-2.0
/usr/lib32/orbit-2.0/Everything_module.so
/usr/lib32/orbit-2.0/Accessibility_LoginHelper_module.so
/usr/lib32/orbit-2.0/Accessibility_module.so
/usr/lib32/orbit-2.0/Bonobo_module.so
/usr/lib32/libQtSql.so.4.6.2
/usr/lib32/libsigc-2.0.so.0.0.0
/usr/lib32/libgstrtp-0.10.so.0.19.2
/usr/lib32/libgsttag-0.10.so.0.19.2
/usr/lib32/libsasl2.so.2.0.23
/usr/lib32/libidn.so.11.5.44
/usr/lib32/libxcb-render.so.0.0.0
/usr/lib32/libXcursor.so.1.0.2
/usr/lib32/libvorbisfile.so.3.3.2
/usr/lib32/libXmuu.so.1.0.0
/usr/lib32/liblzo2.so.2.0.0
/usr/lib32/libSDL_net-1.2.so.0.0.7
/usr/lib32/libXau.so.6.0.0
/usr/lib32/libQtXml.so.4.6.2
/usr/lib32/libcanberra.so.0.2.1
/usr/lib32/libavahi-client.so.3.2.5
/usr/lib32/libQtDBus.so.4.6.2
/usr/lib32/libcelt0.so.0.0.0
/usr/lib32/libXfixes.so.3.1.0
/usr/lib32/libsmbios_c.so.2.2.1
/usr/lib32/libORBitCosNaming-2.so.0.1.0
/usr/lib32/ssl
/usr/lib32/ssl/engines
/usr/lib32/ssl/engines/libchil.so
/usr/lib32/ssl/engines/libcswift.so
/usr/lib32/ssl/engines/lib4758cca.so
/usr/lib32/ssl/engines/libcapi.so
/usr/lib32/ssl/engines/libsureware.so
/usr/lib32/ssl/engines/libubsec.so
/usr/lib32/ssl/engines/libgmp.so
/usr/lib32/ssl/engines/libatalla.so
/usr/lib32/ssl/engines/libnuron.so
/usr/lib32/ssl/engines/libaep.so
/usr/lib32/libgsl.so.0.14.0
/usr/lib32/libbonobo-2.so.0.0.0
/usr/lib32/libXss.so.1.0.0
/usr/lib32/libart_lgpl_2.so.2.3.20
/usr/lib32/libexif.so.12.3.1
/usr/lib32/libpython2.6.so.1.0
/usr/lib32/pango
/usr/lib32/pango/1.6.0
/usr/lib32/pango/1.6.0/module-files.d
/usr/lib32/pango/1.6.0/module-files.d/libpango1.0-0.modules
/usr/lib32/pango/1.6.0/modules
/usr/lib32/pango/1.6.0/modules/pango-thai-fc.so
/usr/lib32/pango/1.6.0/modules/pango-khmer-fc.so
/usr/lib32/pango/1.6.0/modules/pango-hebrew-fc.so
/usr/lib32/pango/1.6.0/modules/pango-indic-lang.so
/usr/lib32/pango/1.6.0/modules/pango-arabic-fc.so
/usr/lib32/pango/1.6.0/modules/pango-indic-fc.so
/usr/lib32/pango/1.6.0/modules/pango-syriac-fc.so
/usr/lib32/pango/1.6.0/modules/pango-tibetan-fc.so
/usr/lib32/pango/1.6.0/modules/pango-basic-fc.so
/usr/lib32/pango/1.6.0/modules/pango-basic-x.so
/usr/lib32/pango/1.6.0/modules/pango-thai-lang.so
/usr/lib32/pango/1.6.0/modules/pango-hangul-fc.so
/usr/lib32/pango/1.6.0/modules/pango-arabic-lang.so
/usr/lib32/libloginhelper.so.0.0.0
/usr/lib32/libgphoto2
/usr/lib32/libgphoto2/2.4.8
/usr/lib32/libgphoto2/2.4.8/clicksmart310.so
/usr/lib32/libgphoto2/2.4.8/dimera3500.so
/usr/lib32/libgphoto2/2.4.8/kodak_dc120.so
/usr/lib32/libgphoto2/2.4.8/sipix_blink2.so
/usr/lib32/libgphoto2/2.4.8/stv0674.so
/usr/lib32/libgphoto2/2.4.8/mars.so
/usr/lib32/libgphoto2/2.4.8/fuji.so
/usr/lib32/libgphoto2/2.4.8/agfa_cl20.so
/usr/lib32/libgphoto2/2.4.8/sierra.so
/usr/lib32/libgphoto2/2.4.8/gsmart300.so
/usr/lib32/libgphoto2/2.4.8/ricoh_g3.so
/usr/lib32/libgphoto2/2.4.8/enigma13.so
/usr/lib32/libgphoto2/2.4.8/jl2005a.so
/usr/lib32/libgphoto2/2.4.8/panasonic_dc1000.so
/usr/lib32/libgphoto2/2.4.8/largan.so
/usr/lib32/libgphoto2/2.4.8/samsung.so
/usr/lib32/libgphoto2/2.4.8/dimagev.so
/usr/lib32/libgphoto2/2.4.8/barbie.so
/usr/lib32/libgphoto2/2.4.8/directory.so
/usr/lib32/libgphoto2/2.4.8/panasonic_coolshot.so
/usr/lib32/libgphoto2/2.4.8/polaroid_pdc320.so
/usr/lib32/libgphoto2/2.4.8/aox.so
/usr/lib32/libgphoto2/2.4.8/sipix_web2.so
/usr/lib32/libgphoto2/2.4.8/polaroid_pdc700.so
/usr/lib32/libgphoto2/2.4.8/casio_qv.so
/usr/lib32/libgphoto2/2.4.8/stv0680.so
/usr/lib32/libgphoto2/2.4.8/ricoh.so
/usr/lib32/libgphoto2/2.4.8/kodak_dc240.so
/usr/lib32/libgphoto2/2.4.8/jd11.so
/usr/lib32/libgphoto2/2.4.8/pccam600.so
/usr/lib32/libgphoto2/2.4.8/konica.so
/usr/lib32/libgphoto2/2.4.8/smal.so
/usr/lib32/libgphoto2/2.4.8/digigr8.so
/usr/lib32/libgphoto2/2.4.8/panasonic_l859.so
/usr/lib32/libgphoto2/2.4.8/toshiba_pdrm11.so
/usr/lib32/libgphoto2/2.4.8/sony_dscf55.so
/usr/lib32/libgphoto2/2.4.8/canon.so
/usr/lib32/libgphoto2/2.4.8/kodak_dc210.so
/usr/lib32/libgphoto2/2.4.8/sonix.so
/usr/lib32/libgphoto2/2.4.8/digita.so
/usr/lib32/libgphoto2/2.4.8/hp215.so
/usr/lib32/libgphoto2/2.4.8/konica_qm150.so
/usr/lib32/libgphoto2/2.4.8/jamcam.so
/usr/lib32/libgphoto2/2.4.8/sony_dscf1.so
/usr/lib32/libgphoto2/2.4.8/mustek.so
/usr/lib32/libgphoto2/2.4.8/iclick.so
/usr/lib32/libgphoto2/2.4.8/spca50x.so
/usr/lib32/libgphoto2/2.4.8/kodak_dc3200.so
/usr/lib32/libgphoto2/2.4.8/topfield.so
/usr/lib32/libgphoto2/2.4.8/soundvision.so
/usr/lib32/libgphoto2/2.4.8/ptp2.so
/usr/lib32/libgphoto2/2.4.8/lg_gsm.so
/usr/lib32/libgphoto2/2.4.8/kodak_ez200.so
/usr/lib32/libgphoto2/2.4.8/polaroid_pdc640.so
/usr/lib32/libgphoto2/2.4.8/panasonic_dc1580.so
/usr/lib32/libgphoto2/2.4.8/pccam300.so
/usr/lib32/libgphoto2/2.4.8/sx330z.so
/usr/lib32/libgphoto2/2.4.8/sq905.so
/usr/lib32/libgphoto2/2.4.8/adc65.so
/usr/lib32/libgphoto2/print-camera-list
/usr/lib32/qt4
/usr/lib32/qt4/plugins
/usr/lib32/qt4/plugins/designer
/usr/lib32/qt4/plugins/designer/libqt3supportwidgets.so
/usr/lib32/qt4/plugins/designer/libqwebview.so
/usr/lib32/qt4/plugins/inputmethods
/usr/lib32/qt4/plugins/inputmethods/libqimsw-multi.so
/usr/lib32/qt4/plugins/imageformats
/usr/lib32/qt4/plugins/imageformats/libqgif.so
/usr/lib32/qt4/plugins/imageformats/libqsvg.so
/usr/lib32/qt4/plugins/imageformats/libqmng.so
/usr/lib32/qt4/plugins/imageformats/libqtiff.so
/usr/lib32/qt4/plugins/imageformats/libqico.so
/usr/lib32/qt4/plugins/imageformats/libqjpeg.so
/usr/lib32/qt4/plugins/codecs
/usr/lib32/qt4/plugins/codecs/libqkrcodecs.so
/usr/lib32/qt4/plugins/codecs/libqcncodecs.so
/usr/lib32/qt4/plugins/codecs/libqtwcodecs.so
/usr/lib32/qt4/plugins/codecs/libqjpcodecs.so
/usr/lib32/qt4/plugins/accessible
/usr/lib32/qt4/plugins/accessible/libqtaccessiblecompatwidgets.so
/usr/lib32/qt4/plugins/accessible/libqtaccessiblewidgets.so
/usr/lib32/qt4/plugins/script
/usr/lib32/qt4/plugins/script/libqtscriptdbus.so
/usr/lib32/qt4/plugins/iconengines
/usr/lib32/qt4/plugins/iconengines/libqsvgicon.so
/usr/lib32/qt4/plugins/graphicssystems
/usr/lib32/qt4/plugins/graphicssystems/libqtracegraphicssystem.so
/usr/lib32/qt4/plugins/graphicssystems/libqglgraphicssystem.so
/usr/lib32/python2.6
/usr/lib32/python2.6/config
/usr/lib32/librsvg-2.so.2.26.3
/usr/lib32/nss
/usr/lib32/nss/libnssckbi.so
/usr/lib32/nss/libfreebl3.chk
/usr/lib32/nss/libsoftokn3.so
/usr/lib32/nss/libsoftokn3.chk
/usr/lib32/nss/libnssdbm3.so
/usr/lib32/nss/libnssdbm3.chk
/usr/lib32/nss/libfreebl3.so
/usr/lib32/libXft.so.2.1.13
/usr/lib32/libsane.la
/usr/lib32/libMrm.so.2.0.1
/usr/lib
/usr/lib/gtk-2.0
/usr/lib/gtk-2.0/2.10.0
/usr/lib/gio
/usr/lib/gio/modules
/lib32/libpamc.so
/lib32/libcap.so.2
/lib32/libselinux.so
/lib32/libattr.so.1
/lib32/libusb-0.1.so.4
/lib32/libuuid.so.1
/lib32/libpam.so
/lib32/libdrm_intel.so.1
/lib32/libexpat.so
/lib32/libdrm_nouveau.so.1
/lib32/libpng12.so
/lib32/libdbus-1.so
/lib32/libdrm.so.2
/lib32/libcom_err.so
/lib32/libexpatw.so
/lib32/libsepol.so
/lib32/libudev.so
/lib32/libssl.so
/lib32/libdrm_radeon.so.1
/lib32/libuuid.so
/lib32/libcom_err.so.2
/lib32/libpam_misc.so
/lib32/libdrm.so
/lib32/libx86.so
/lib32/libnss_ldap.so.2
/lib32/libpopt.so.0
/lib32/libaio.so
/lib32/libaio.so.1
/lib32/libudev.so.0
/lib32/libacl.so
/lib32/libwrap.so.0
/lib32/libpamc.so.0
/lib32/libdrm_nouveau.so
/lib32/libwrap.so
/lib32/libacl.so.1
/lib32/libpng12.so.0
/lib32/libglib-2.0.so.0
/lib32/libcrypto.so
/lib32/libdbus-1.so.3
/lib32/libpopt.so
/lib32/libpam_misc.so.0
/lib32/libpcre.so.3
/lib32/libdrm_radeon.so
/lib32/libglib-2.0.so
/lib32/libcap.so
/lib32/libgpg-error.so
/lib32/libusb-0.1.so
/lib32/libgpg-error.so.0
/lib32/libkeyutils.so.1
/lib32/libpcre.so
/lib32/libgcrypt.so.11
/lib32/libusb.so
/lib32/libexpat.so.1
/lib32/libattr.so
/lib32/libexpatw.so.1
/lib32/libgcrypt.so
/lib32/libpam.so.0
/lib32/libdrm_intel.so
/usr/lib32/libsasl2.so.2
/usr/lib32/libmikmod.so.2
/usr/lib32/libsigc-2.0.so
/usr/lib32/libXt.so
/usr/lib32/libdirectfb-1.2.so
/usr/lib32/libQtScriptTools.so.4
/usr/lib32/libssh2.so
/usr/lib32/libao.so
/usr/lib32/libvorbisenc.so
/usr/lib32/libXrandr.so
/usr/lib32/libQtNetwork.so
/usr/lib32/libkrb5.so
/usr/lib32/libXext.so
/usr/lib32/libQtOpenGL.so
/usr/lib32/libgstdataprotocol-0.10.so.0
/usr/lib32/libopenal.so
/usr/lib32/libgstrtsp-0.10.so
/usr/lib32/libgstcdda-0.10.so
/usr/lib32/libXxf86vm.so.1
/usr/lib32/libQtDBus.so
/usr/lib32/libldap-2.4.so.2
/usr/lib32/libgsl.so.0
/usr/lib32/libdirect-1.2.so.0
/usr/lib32/libcelt0.so.0
/usr/lib32/libgstbase-0.10.so.0
/usr/lib32/libbonobo-activation.so.4
/usr/lib32/libgvfscommon-dnssd.so.0
/usr/lib32/libusb-0.1.so.4
/usr/lib32/libcelt0.so
/usr/lib32/libgstaudio-0.10.so.0
/usr/lib32/libsamplerate.so.0
/usr/lib32/libQtWebKit.so.4.6
/usr/lib32/libgssapi_krb5.so.2
/usr/lib32/libgsm.so.1
/usr/lib32/libart_lgpl_2.so
/usr/lib32/libvgagl.so.1
/usr/lib32/libidn.so
/usr/lib32/liboil-0.3.so
/usr/lib32/libFLAC.so
/usr/lib32/libfltk_gl.so
/usr/lib32/libgnutls-extra.so
/usr/lib32/libQtCLucene.so.4
/usr/lib32/libXaw3d.so.6
/usr/lib32/libaudio.so
/usr/lib32/libxslt.so
/usr/lib32/libpangoft2-1.0.so
/usr/lib32/libxml2.so
/usr/lib32/libgtrtst.so
/usr/lib32/libpcreposix.so
/usr/lib32/libgslcblas.so
/usr/lib32/libgnutls.so.26
/usr/lib32/gcc/i486-linux-gnu/4.4.3
/usr/lib32/libogg.so
/usr/lib32/libXtst.so
/usr/lib32/libgstcontroller-0.10.so
/usr/lib32/libpulse-simple.so
/usr/lib32/libbonobo-activation.so
/usr/lib32/libgmodule-2.0.so
/usr/lib32/libgstsdp-0.10.so
/usr/lib32/libgstcheck-0.10.so
/usr/lib32/libpangoxft-1.0.so
/usr/lib32/libORBit-2.so
/usr/lib32/libdirect-1.2.so
/usr/lib32/libmikmod.so
/usr/lib32/libpango-1.0.so
/usr/lib32/libSDL_net-1.2.so
/usr/lib32/libgdbm.so.3
/usr/lib32/libSDL_net-1.2.so.0
/usr/lib32/libQtCore.so.4.6
/usr/lib32/libgssapi_krb5.so
/usr/lib32/libQtXmlPatterns.so.4
/usr/lib32/libcanberra-gtk.so
/usr/lib32/libsane.so
/usr/lib32/libwmflite-0.2.so
/usr/lib32/libkrb5support.so.0
/usr/lib32/libxcb-render.so.0
/usr/lib32/liblber-2.4.so.2
/usr/lib32/mesa/libGL.so.1
/usr/lib32/libSDL-1.2.so
/usr/lib32/libXinerama.so.1
/usr/lib32/libgtrtst.so.1
/usr/lib32/libgvfscommon-dnssd.so
/usr/lib32/libloginhelper.so.0
/usr/lib32/libXaw7.so.7
/usr/lib32/libodbcinst.so.1
/usr/lib32/libXmuu.so.1
/usr/lib32/libORBitCosNaming-2.so.0
/usr/lib32/libXrender.so.1
/usr/lib32/libvga.so
/usr/lib32/libXdamage.so.1
/usr/lib32/libGLU.so.1
/usr/lib32/libgstnet-0.10.so.0
/usr/lib32/libpng12.so
/usr/lib32/libgobject-2.0.so
/usr/lib32/libexslt.so
/usr/lib32/libgstpbutils-0.10.so
/usr/lib32/libuniquewm-1.2.so
/usr/lib32/libgio-2.0.so.0
/usr/lib32/libcspi.so.0
/usr/lib32/libXv.so
/usr/lib32/libXcomposite.so.1
/usr/lib32/libvorbisfile.so
/usr/lib32/libgailutil.so
/usr/lib32/libgstapp-0.10.so
/usr/lib32/libcapi20.so.3
/usr/lib32/libQtTest.so
/usr/lib32/libnss_ldap.so
/usr/lib32/libvga.so.1
/usr/lib32/libaudiofile.so
/usr/lib32/libldap_r-2.4.so
/usr/lib32/libxcb-render-util.so
/usr/lib32/libX11.so.6
/usr/lib32/libpixman-1.so.0
/usr/lib32/libgstapp-0.10.so.0
/usr/lib32/libgphoto2.so.2
/usr/lib32/libgstpbutils-0.10.so.0
/usr/lib32/libgnutls-extra.so.26
/usr/lib32/libGLU.so
/usr/lib32/libXv.so.1
/usr/lib32/libgstrtsp-0.10.so.0
/usr/lib32/libSDL_ttf-2.0.so
/usr/lib32/libSM.so
/usr/lib32/libavahi-common.so.3
/usr/lib32/libsigc-2.0.so.0
/usr/lib32/libORBitCosNaming-2.so
/usr/lib32/libMrm.so.2
/usr/lib32/libQtScript.so.4
/usr/lib32/libcapi20.so
/usr/lib32/libXpm.so
/usr/lib32/libXaw7.so
/usr/lib32/libSDL_mixer-1.2.so.0
/usr/lib32/libORBit-imodule-2.so.0
/usr/lib32/libplc4.so.0d
/usr/lib32/libao.so.2
/usr/lib32/libgconf-2.so
/usr/lib32/libgstcontroller-0.10.so.0
/usr/lib32/libgstaudio-0.10.so
/usr/lib32/libasyncns.so
/usr/lib32/libnss3.so.1d
/usr/lib32/liblcms.so
/usr/lib32/libXfixes.so.3
/usr/lib32/libXcursor.so.1
/usr/lib32/libdbus-glib-1.so.2
/usr/lib32/liblcms.so.1
/usr/lib32/libgnome-keyring.so
/usr/lib32/libgdk-x11-2.0.so
/usr/lib32/libcupsimage.so
/usr/lib32/libcairo.so
/usr/lib32/libpulse.so.0
/usr/lib32/libsmbios_c.so.2
/usr/lib32/libatk-1.0.so.0
/usr/lib32/libsmpeg-0.4.so
/usr/lib32/libQt3Support.so.4
/usr/lib32/libpangox-1.0.so
/usr/lib32/odbc/libodbctxt.so
/usr/lib32/odbc/libnn.so
/usr/lib32/libgsttag-0.10.so
/usr/lib32/libpulse-mainloop-glib.so
/usr/lib32/liblber-2.4.so
/usr/lib32/libgnutls.so
/usr/lib32/libgthread-2.0.so
/usr/lib32/libglut.so.3
/usr/lib32/libgsttag-0.10.so.0
/usr/lib32/libgstnetbuffer-0.10.so.0
/usr/lib32/libXp.so
/usr/lib32/libSDL_image-1.2.so
/usr/lib32/libQt3Support.so
/usr/lib32/libfontconfig.so
/usr/lib32/libtasn1.so
/usr/lib32/libFLAC.so.8
/usr/lib32/locale
/usr/lib32/libQtSql.so.4
/usr/lib32/libgstbase-0.10.so
/usr/lib32/libieee1284.so.3
/usr/lib32/libmad.so.0
/usr/lib32/libXpm.so.4
/usr/lib32/libcups.so
/usr/lib32/libXp.so.6
/usr/lib32/libgstnetbuffer-0.10.so
/usr/lib32/libpulse-browse.so.0
/usr/lib32/libQtSql.so
/usr/lib32/libsmime3.so.1d
/usr/lib32/libart_lgpl_2.so.2
/usr/lib32/libieee1284.so
/usr/lib32/libdirectfb-1.2.so.0
/usr/lib32/libgdk_pixbuf_xlib-2.0.so.0
/usr/lib32/libspi.so.0
/usr/lib32/libfontconfig.so.1
/usr/lib32/libgstriff-0.10.so.0
/usr/lib32/libIDL-2.so
/usr/lib32/libwmflite-0.2.so.7
/usr/lib32/libaudiofile.so.0
/usr/lib32/libXtst.so.6
/usr/lib32/libgsf-1.so
/usr/lib32/libgphoto2_port.so.0
/usr/lib32/libQtXml.so.4
/usr/lib32/libxcb-render.so
/usr/lib32/libQtTest.so.4.6
/usr/lib32/libgdbm.so
/usr/lib32/libXau.so.6
/usr/lib32/libavahi-client.so
/usr/lib32/libXcomposite.so
/usr/lib32/libSDL_image-1.2.so.0
/usr/lib32/libpython2.6.so.1
/usr/lib32/libmpg123.so
/usr/lib32/libsmbios.so.2
/usr/lib32/libgsf-1.so.114
/usr/lib32/libgdk-x11-2.0.so.0
/usr/lib32/libjpeg.so.62
/usr/lib32/libpulse-mainloop-glib.so.0
/usr/lib32/libopenal.so.1
/usr/lib32/libgdbm_compat.so
/usr/lib32/libspi.so
/usr/lib32/libpixman-1.so
/usr/lib32/libXft.so
/usr/lib32/libloginhelper.so
/usr/lib32/libtiff.so
/usr/lib32/libodbc.so.1
/usr/lib32/libXi.so.6
/usr/lib32/libcurl.so.3
/usr/lib32/libQtTest.so.4
/usr/lib32/libgtk-x11-2.0.so.0
/usr/lib32/libQtCLucene.so
/usr/lib32/libpulse-simple.so.0
/usr/lib32/libuniquewm-1.2.so.0
/usr/lib32/libfusion-1.2.so.0
/usr/lib32/libgsm.so
/usr/lib32/libssh2.so.1
/usr/lib32/libQtOpenGL.so.4
/usr/lib32/libxcb.so.1
/usr/lib32/libgstnet-0.10.so
/usr/lib32/libcroco-0.6.so
/usr/lib32/libQtWebKit.so.4
/usr/lib32/libSM.so.6
/usr/lib32/libgio-2.0.so
/usr/lib32/libwmf-0.2.so.7
/usr/lib32/libSDL_mixer-1.2.so
/usr/lib32/libpangoxft-1.0.so.0
/usr/lib32/libXss.so.1
/usr/lib32/libatk-1.0.so
/usr/lib32/libxcb-render-util.so.0
/usr/lib32/libsndfile.so
/usr/lib32/libnspr4.so.0d
/usr/lib32/libltdl.so
/usr/lib32/libXdmcp.so
/usr/lib32/libgphoto2.so
/usr/lib32/libfltk_forms.so
/usr/lib32/libpangoft2-1.0.so.0
/usr/lib32/libMrm.so
/usr/lib32/libcanberra.so
/usr/lib32/libldap_r.so
/usr/lib32/libodbcinst.so
/usr/lib32/libgstrtp-0.10.so.0
/usr/lib32/libXaw3d.so
/usr/lib32/libgnutls-openssl.so.26
/usr/lib32/libXau.so
/usr/lib32/libpango-1.0.so.0
/usr/lib32/libhal.so
/usr/lib32/libXrandr.so.2
/usr/lib32/libQtXml.so.4.6
/usr/lib32/libQtGui.so.4.6
/usr/lib32/libXaw.so.7
/usr/lib32/libssl3.so.1d
/usr/lib32/libxslt.so.1
/usr/lib32/libglade-2.0.so.0
/usr/lib32/libxml2.so.2
/usr/lib32/liboil-0.3.so.0
/usr/lib32/libQtDBus.so.4
/usr/lib32/libX11.so
/usr/lib32/libkrb5support.so
/usr/lib32/libXcursor.so
/usr/lib32/libgphoto2_port.so
/usr/lib32/libgtk-x11-2.0.so
/usr/lib32/libodbc.so
/usr/lib32/libsane.so.1
/usr/lib32/libXdmcp.so.6
/usr/lib32/libgthread-2.0.so.0
/usr/lib32/libaudio.so.2
/usr/lib32/libgstcheck-0.10.so.0
/usr/lib32/libgstfft-0.10.so
/usr/lib32/libgnome-keyring.so.0
/usr/lib32/libQtGui.so.4
/usr/lib32/libsqlite3.so.0
/usr/lib32/libsqlite3.so
/usr/lib32/libQtOpenGL.so.4.6
/usr/lib32/libfreetype.so.6
/usr/lib32/libQtSvg.so.4.6
/usr/lib32/libXmu.so.6
/usr/lib32/sasl2/libsasldb.so.2
/usr/lib32/sasl2/libsasldb.so
/usr/lib32/libcspi.so
/usr/lib32/libgdk_pixbuf_xlib-2.0.so
/usr/lib32/libQtXmlPatterns.so.4.6
/usr/lib32/libgstinterfaces-0.10.so
/usr/lib32/libgstreamer-0.10.so
/usr/lib32/libIDL-2.so.0
/usr/lib32/libpulse-browse.so
/usr/lib32/libQtScriptTools.so
/usr/lib32/libSDL-1.2.so.0
/usr/lib32/libQtSql.so.4.6
/usr/lib32/libGL.so
/usr/lib32/libtdb.so.1
/usr/lib32/libldap_r-2.4.so.2
/usr/lib32/libgstvideo-0.10.so
/usr/lib32/liblber.so
/usr/lib32/libnssutil3.so.1d
/usr/lib32/libpulse.so
/usr/lib32/libQtSvg.so
/usr/lib32/libavahi-common.so
/usr/lib32/libXi.so
/usr/lib32/libICE.so.6
/usr/lib32/libQtSvg.so.4
/usr/lib32/libodbccr.so.1
/usr/lib32/alsa-lib/libasound_module_rate_speexrate_best.so
/usr/lib32/alsa-lib/libasound_module_rate_speexrate_medium.so
/usr/lib32/alsa-lib/libasound_module_rate_samplerate_order.so
/usr/lib32/alsa-lib/libasound_module_rate_samplerate_linear.so
/usr/lib32/alsa-lib/libasound_module_rate_samplerate_medium.so
/usr/lib32/alsa-lib/libasound_module_rate_samplerate_best.so
/usr/lib32/libQtScriptTools.so.4.6
/usr/lib32/libk5crypto.so
/usr/lib32/libjack.so
/usr/lib32/libmad.so
/usr/lib32/libQt3Support.so.4.6
/usr/lib32/libcrypto.so.0.9.8
/usr/lib32/libgstreamer-0.10.so.0
/usr/lib32/libcurl.so.4
/usr/lib32/libtasn1.so.3
/usr/lib32/libfltk.so
/usr/lib32/sane/libsane-apple.so.1
/usr/lib32/sane/libsane-pixma.so.1
/usr/lib32/sane/libsane-niash.so.1
/usr/lib32/sane/libsane-s9036.so.1
/usr/lib32/sane/libsane-hs2p.so.1
/usr/lib32/sane/libsane-test.so.1
/usr/lib32/sane/libsane-net.so.1
/usr/lib32/sane/libsane-leo.so.1
/usr/lib32/sane/libsane-nec.so.1
/usr/lib32/sane/libsane-mustek_pp.so.1
/usr/lib32/sane/libsane-mustek_usb.so.1
/usr/lib32/sane/libsane-canon_pp.so.1
/usr/lib32/sane/libsane-umax.so.1
/usr/lib32/sane/libsane-v4l.so.1
/usr/lib32/sane/libsane-dc240.so.1
/usr/lib32/sane/libsane-as6e.so.1
/usr/lib32/sane/libsane-lexmark.so.1
/usr/lib32/sane/libsane-agfafocus.so.1
/usr/lib32/sane/libsane-hp4200.so.1
/usr/lib32/sane/libsane-coolscan2.so.1
/usr/lib32/sane/libsane-artec_eplus48u.so.1
/usr/lib32/sane/libsane-qcam.so.1
/usr/lib32/sane/libsane-mustek_usb2.so.1
/usr/lib32/sane/libsane-microtek.so.1
/usr/lib32/sane/libsane-hp3900.so.1
/usr/lib32/sane/libsane-dmc.so.1
/usr/lib32/sane/libsane-snapscan.so.1
/usr/lib32/sane/libsane-xerox_mfp.so.1
/usr/lib32/sane/libsane-hp.so.1
/usr/lib32/sane/libsane-plustek_pp.so.1
/usr/lib32/sane/libsane-hp3500.so.1
/usr/lib32/sane/libsane-gphoto2.so.1
/usr/lib32/sane/libsane-teco1.so.1
/usr/lib32/sane/libsane-pie.so.1
/usr/lib32/sane/libsane-plustek.so.1
/usr/lib32/sane/libsane-st400.so.1
/usr/lib32/sane/libsane-epson2.so.1
/usr/lib32/sane/libsane-epjitsu.so.1
/usr/lib32/sane/libsane-ma1509.so.1
/usr/lib32/sane/libsane-coolscan.so.1
/usr/lib32/sane/libsane-epson.so.1
/usr/lib32/sane/libsane-sharp.so.1
/usr/lib32/sane/libsane-canon630u.so.1
/usr/lib32/sane/libsane-u12.so.1
/usr/lib32/sane/libsane-artec.so.1
/usr/lib32/sane/libsane-ricoh.so.1
/usr/lib32/sane/libsane-umax1220u.so.1
/usr/lib32/sane/libsane-rts8891.so.1
/usr/lib32/sane/libsane-sm3600.so.1
/usr/lib32/sane/libsane-cardscan.so.1
/usr/lib32/sane/libsane-ibm.so.1
/usr/lib32/sane/libsane-bh.so.1
/usr/lib32/sane/libsane-hpsj5s.so.1
/usr/lib32/sane/libsane-dc25.so.1
/usr/lib32/sane/libsane-hpljm1005.so.1
/usr/lib32/sane/libsane-fujitsu.so.1
/usr/lib32/sane/libsane-mustek.so.1
/usr/lib32/sane/libsane-sm3840.so.1
/usr/lib32/sane/libsane-stv680.so.1
/usr/lib32/sane/libsane-coolscan3.so.1
/usr/lib32/sane/libsane-hp5400.so.1
/usr/lib32/sane/libsane-dc210.so.1
/usr/lib32/sane/libsane-sceptre.so.1
/usr/lib32/sane/libsane-teco3.so.1
/usr/lib32/sane/libsane-avision.so.1
/usr/lib32/sane/libsane-umax_pp.so.1
/usr/lib32/sane/libsane-abaton.so.1
/usr/lib32/sane/libsane-hp5590.so.1
/usr/lib32/sane/libsane-gt68xx.so.1
/usr/lib32/sane/libsane-canon.so.1
/usr/lib32/sane/libsane-sp15c.so.1
/usr/lib32/sane/libsane-matsushita.so.1
/usr/lib32/sane/libsane-microtek2.so.1
/usr/lib32/sane/libsane-genesys.so.1
/usr/lib32/sane/libsane-teco2.so.1
/usr/lib32/sane/libsane-dell1600n_net.so.1
/usr/lib32/sane/libsane-tamarack.so.1
/usr/lib32/sane/libsane-canon_dr.so.1
/usr/lib32/libfusion-1.2.so
/usr/lib32/libfreetype.so
/usr/lib32/libjackserver.so.0
/usr/lib32/libplds4.so.0d
/usr/lib32/libgdk_pixbuf-2.0.so
/usr/lib32/libsmbios.so
/usr/lib32/libbonobo-2.so
/usr/lib32/libgnomecanvas-2.so
/usr/lib32/libdbus-glib-1.so
/usr/lib32/libgslcblas.so.0
/usr/lib32/libcanberra-gtk.so.0
/usr/lib32/libcanberra.so.0
/usr/lib32/libORBit-2.so.0
/usr/lib32/libkrb5.so.3
/usr/lib32/libgstsdp-0.10.so.0
/usr/lib32/libICE.so
/usr/lib32/libgstvideo-0.10.so.0
/usr/lib32/libgdk_pixbuf-2.0.so.0
/usr/lib32/libsmbios_c.so
/usr/lib32/libgmodule-2.0.so.0
/usr/lib32/libtiff.so.4
/usr/lib32/libXext.so.6
/usr/lib32/libQtScript.so.4.6
/usr/lib32/libXt.so.6
/usr/lib32/libjackserver.so
/usr/lib32/libexslt.so.0
/usr/lib32/libwmf-0.2.so
/usr/lib32/libXft.so.2
/usr/lib32/libavahi-client.so.3
/usr/lib32/sse2/libspeexdsp.so.1
/usr/lib32/libvorbisenc.so.2
/usr/lib32/librsvg-2.so
/usr/lib32/libtdb.so
/usr/lib32/liblzo2.so.2
/usr/lib32/libQtCore.so.4
/usr/lib32/libltdl.so.7
/usr/lib32/libjpeg.so
/usr/lib32/libQtGui.so
/usr/lib32/libgdbm_compat.so.3
/usr/lib32/libgstriff-0.10.so
/usr/lib32/libXm.so.2
/usr/lib32/libvorbis.so.0
/usr/lib32/libcroco-0.6.so.3
/usr/lib32/libvorbis.so
/usr/lib32/libvgagl.so
/usr/lib32/libspeexdsp.so
/usr/lib32/librsvg-2.so.2
/usr/lib32/libORBit-imodule-2.so
/usr/lib32/libbluetooth.so
/usr/lib32/libXinerama.so
/usr/lib32/libsamplerate.so
/usr/lib32/libbluetooth.so.3
/usr/lib32/libpython2.6.so
/usr/lib32/libgvfscommon.so
/usr/lib32/libXm.so
/usr/lib32/libgconf-2.so.4
/usr/lib32/libgstdataprotocol-0.10.so
/usr/lib32/libQtNetwork.so.4.6
/usr/lib32/libQtXmlPatterns.so
/usr/lib32/libXxf86vm.so
/usr/lib32/libcairo.so.2
/usr/lib32/libpng.so
/usr/lib32/libxcb.so
/usr/lib32/libXdamage.so
/usr/lib32/libbonobo-2.so.0
/usr/lib32/libgstcdda-0.10.so.0
/usr/lib32/libidn.so.11
/usr/lib32/libQtScript.so
/usr/lib32/libk5crypto.so.3
/usr/lib32/libQtCore.so
/usr/lib32/libgstinterfaces-0.10.so.0
/usr/lib32/libmpg123.so.0
/usr/lib32/libexif.so.12
/usr/lib32/libgnomecanvas-2.so.0
/usr/lib32/libpangox-1.0.so.0
/usr/lib32/libspeexdsp.so.1
/usr/lib32/libgstfft-0.10.so.0
/usr/lib32/libgobject-2.0.so.0
/usr/lib32/libsasl2.so
/usr/lib32/libXmu.so
/usr/lib32/libgstrtp-0.10.so
/usr/lib32/liblzo2.so
/usr/lib32/libQtWebKit.so
/usr/lib32/libsndfile.so.1
/usr/lib32/libSDL_ttf-2.0.so.0
/usr/lib32/libpangocairo-1.0.so.0
/usr/lib32/libcurl.so
/usr/lib32/libasyncns.so.0
/usr/lib32/libXrender.so
/usr/lib32/libglut.so
/usr/lib32/libexif.so
/usr/lib32/libgnutls-openssl.so
/usr/lib32/libQtDBus.so.4.6
/usr/lib32/libgsl.so
/usr/lib32/libQtCLucene.so.4.6
/usr/lib32/libodbccr.so
/usr/lib32/libQtNetwork.so.4
/usr/lib32/libgvfscommon.so.0
/usr/lib32/libogg.so.0
/usr/lib32/libjack.so.0
/usr/lib32/libpcreposix.so.3
/usr/lib32/libfltk_images.so
/usr/lib32/libgailutil.so.18
/usr/lib32/libXss.so
/usr/lib32/libXfixes.so
/usr/lib32/python2.6/config/libpython2.6.so
/usr/lib32/libhal.so.1
/usr/lib32/libglade-2.0.so
/usr/lib32/libXmuu.so
/usr/lib32/libsmpeg-0.4.so.0
/usr/lib32/libQtXml.so
/usr/lib32/libpangocairo-1.0.so
/usr/lib32/libvorbisfile.so.3
/usr/lib32/libssl.so.0.9.8
/usr/lib/gtk-2.0/i686-pc-linux-gnu
/usr/lib/gtk-2.0/2.10.0/i686-pc-linux-gnu
/usr/lib/gtk-2.0/2.10.0/i486-pc-linux-gnu
/usr/lib/gtk-2.0/i486-pc-linux-gnu
/usr/lib/gio/modules/i686-pc-linux-gnu
/usr/lib/gio/modules/i486-pc-linux-gnu

```

This one is one hell of a long list. You should have warned me, Bashing-om.
I used the | more command and I should have used the | less.

Anyway, here we are..


shobuz99

---

### Post by whitesmith on 2013-08-31
Do you guys know what a triage nurse does? Her job is to allocate scarce resources in a mass medical emergency by classifying patients into 3 groups. Those in group 1 will get better on their own, so they get no attention. Group 2 patients will die if they do not receive immediate attention and will probably live afterward, so they get maximum effort. Group 3 people are going to die whether or not they get attention, so they are allowed to die. With a little imagination triage can be applied to computer problems. The OP's issue puts his computer problem solidly in Group 3. The very first answer posted in this thread is the correct approach. Reinstall the damn OS. Hopefully the OP will learn to keep /home in a separate partition for this very reason. Always bear one thing in mind in dealing with *nix: There be dragons.

---

### Post by newb85 on 2013-09-01
> **whitesmith said:**
> Hopefully the OP will learn to keep /home in a separate partition for this very reason.

Not to derail, but this is an obsession I've never understood.  In most cases, when the system is borked to the point of unusable or unbootable, it is still possible (and fairly easy, in fact) to recover the entire /home directory using a Live disc or by hooking the drive to another Linux system.  In the rare situations where this is not the case, a separate /home directory would almost always get borked, as well.  Moreover, dropping a /home directory (hidden files and all) into a new system is often not as clean an operation as it's made out to be.

---

### Post by Jonathan Precise on 2013-09-01
@bashing-om: Please read my last post in this thread. It contains the (untouched) openjdk-6-jre-headless.list.

--Hope it's of help!

---

### Post by Bashing-om on 2013-09-01
to all;
1. I have never encountered a situation in ubuntu that can not be repaired. Linux is a kernel - that is replaceable- and attached to this kernel are various modules that interact with the kernel. These processes are all repairable, replaceable. Though agreed it is often easier and quicker to (re-)install than to take the time to understand what and where the malfunction may lie. These are all just processes and the tools are provided to troubleshoot the issues. The problem is what tool to apply where. And agreed, linux expects one to know what they are doing at all times and if told to hose the system up totally ... it will do so !

2. This situation is NOW nothing more than a dependency issue. Required at this time is to find the base dependencies and satisfy the package manager. Yes it is trying .. and yes my understanding of the package management system has become clearer in trying to find these dependencies - that is one positively good thing. All of us have learned from this experience.

3. Separate partitions; /home. I see it as individual decision of each administrator. How they perceive their system and the thought processes to install/repair/remove/alter. There are pros and cons in my experience, I prefer separate partitions because it does aid my thinking processes as separated file systems promote my linear thinking. I also want control over the size of my partitons and therefore what is installed where. For the casual home user I can see little benefit to worry with the added complexity of separating the partitions. Good backup of files works in any respect.

-------------------------
Back on topic:

@shobuz99;
I am now of the opinion that the 32 bit libs are not a cause of a problem ..as all appears to be in place. Starting all over now from square one. What does the package manager report as problems (??):
```

sudo dpkg -C

```
and will begin the process of drilling down, attempt to install, and drill down some more on ONE issue at a time.

@Jonathan Precise, Believe me I do appreciate your input and help. In respect to the index files, "apt-get update" will replace any missing file. At some point it may be a benefit to compare this systems files with a known good index file ..but I see no reason to think that the (re)built indexes are corrupt. Again we just need to satisfy the base dependencies. I continue to learn the system relationships to these files -> gets deeper alla the time.


[INDENT][INDENT]time effort and frustration; but there will be an end
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-09-03
> **Bashing-om said:**
> to all;
1. I have never encountered a situation in ubuntu that can not be repaired. Linux is a kernel - that is replaceable- and attached to this kernel are various modules that interact with the kernel. These processes are all repairable, replaceable. Though agreed it is often easier and quicker to (re-)install than to take the time to understand what and where the malfunction may lie. These are all just processes and the tools are provided to troubleshoot the issues. The problem is what tool to apply where. And agreed, linux expects one to know what they are doing at all times and if told to hose the system up totally ... it will do so !

2. This situation is NOW nothing more than a dependency issue. Required at this time is to find the base dependencies and satisfy the package manager. Yes it is trying .. and yes my understanding of the package management system has become clearer in trying to find these dependencies - that is one positively good thing. All of us have learned from this experience.

3. Separate partitions; /home. I see it as individual decision of each administrator. How they perceive their system and the thought processes to install/repair/remove/alter. There are pros and cons in my experience, I prefer separate partitions because it does aid my thinking processes as separated file systems promote my linear thinking. I also want control over the size of my partitons and therefore what is installed where. For the casual home user I can see little benefit to worry with the added complexity of separating the partitions. Good backup of files works in any respect.

-------------------------
Back on topic:

@shobuz99;
I am now of the opinion that the 32 bit libs are not a cause of a problem ..as all appears to be in place. Starting all over now from square one. What does the package manager report as problems (??):
```

sudo dpkg -C

```
and will begin the process of drilling down, attempt to install, and drill down some more on ONE issue at a time.

@Jonathan Precise, Believe me I do appreciate your input and help. In respect to the index files, "apt-get update" will replace any missing file. At some point it may be a benefit to compare this systems files with a known good index file ..but I see no reason to think that the (re)built indexes are corrupt. Again we just need to satisfy the base dependencies. I continue to learn the system relationships to these files -> gets deeper alla the time.


[INDENT][INDENT]time effort and frustration; but there will be an end
[/INDENT][/INDENT]

ok.
```
rick@rick-desktop:~$ dpkg -C
rick@rick-desktop:~$ 

```

Next?

Shobuz99

---

### Post by philinux on 2013-09-03
This is only a personal opinion and not directed at anyone.

Faced with a similar situation and having my /home on it's own partition,  I would have taken the expeditious route and reinstalled as it would have taken less than an hour including installing all extra stuff. 8-)

---

### Post by Bashing-om on 2013-09-03
@ philinux; Great point ... maybe yet; still trying the hard way.

@Shobuz99; dpkg's output says all is well now, whereas formerly not(???) !
OK, what does apt advise ?
```

apt-get check

```

[INDENT][INDENT]sometimes I wonder, other times I do not know
[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-09-03
> **philinux said:**
> This is only a personal opinion and not directed at anyone.

Faced with a similar situation and having my /home on it's own partition,  I would have taken the expeditious route and reinstalled as it would have taken less than an hour including installing all extra stuff. 8-)

I appreciate and respect your choice...however, I don't have a live CD for 10.04 LTS. 
Is it possible to still download an iso for 10.04 LTS and create one?

shobuz99

---

### Post by Shobuz99 on 2013-09-03
```

```> **Bashing-om said:**
> @ philinux; Great point ... maybe yet; still trying the hard way.

@Shobuz99; dpkg's output says all is well now, whereas formerly not(???) !
OK, what does apt advise ?
```

apt-get check

```

[INDENT][INDENT]sometimes I wonder, other times I do not know
[/INDENT][/INDENT]

Please remember that I MUST use sudo for that command to work the first time.

```
rick@rick-desktop:~$ sudo apt-get check
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnome-terminal: Depends: gnome-terminal-data (>= 2.30) but it is not installed
                  Depends: gnome-terminal-data (< 2.31) but it is not installed
  libgnomevfs2-common: Depends: gnome-mime-data but it is not installed
E: Unmet dependencies. Try using -f.
rick@rick-desktop:~$ 

```

We've been here before many times...but anyway, what's next?

shobuz99

---

### Post by Bashing-om on 2013-09-03
Shobuz99; Yeah, old story revisiting now.
sorry that I forgot that the command required "sudo".
Now we are looking at 2 dependency issues ..
I presently do not understand the conflict with gnome-terminal-data, lets put that one off and deal with gnome-mime-data.
Start the process to isolate the dependency -of only this one -by trying to install it and see what direction the error points us in:
```

sudo apt-get install gnome-mime-data

```

[INDENT][INDENT]restart from square 1
[/INDENT][/INDENT]

---

### Post by philinux on 2013-09-03
> **Shobuz99 said:**
> I appreciate and respect your choice...however, I don't have a live CD for 10.04 LTS. 
Is it possible to still download an iso for 10.04 LTS and create one?

shobuz99

Ah yes you would have to get it from ubuntu's old releases site as it's reached end of life.

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by Shobuz99 on 2013-09-04
> **Bashing-om said:**
> Shobuz99; Yeah, old story revisiting now.
sorry that I forgot that the command required "sudo".
Now we are looking at 2 dependency issues ..
I presently do not understand the conflict with gnome-terminal-data, lets put that one off and deal with gnome-mime-data.
Start the process to isolate the dependency -of only this one -by trying to install it and see what direction the error points us in:
```

sudo apt-get install gnome-mime-data

```

[INDENT][INDENT]restart from square 1
[/INDENT][/INDENT]

Ok. here's the results:

```
rick@rick-desktop:~$ sudo apt-get install gnome-mime-data
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome-terminal: Depends: gnome-terminal-data (>= 2.30) but it is not going to be installed
                  Depends: gnome-terminal-data (< 2.31) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
rick@rick-desktop:~$ 

```

Question: Does this mean that gnome-mime-data is now installed?
It seems to me that it may not be; unless 
"Reading package lists... Done
Building dependency tree  
Reading state information... Done" 
mean that it IS actually installed.
I just don't come to that conclusion, based on the output error message after those messages.... 
Do you?
shobuz99

---

### Post by philinux on 2013-09-04
Deffo not installed.

---

### Post by Bashing-om on 2013-09-04
shobuz99; Well ...
Nope not installed .. but looks to be the end of that short chain, round robin'n back to "gnome-terminal-data".
Good thing  -> is looks like all the snakes except this one are stomped on !
A conflict in versions installed ?
```

apt-cache showpkg gnome-terminal-data
dpkg -l gnome-terminal-data

```
and see about getting it's dependencies satisfied in the next move.

[INDENT][INDENT]keep'n on keep'n on[/INDENT][/INDENT]

---

### Post by Shobuz99 on 2013-09-04
> **Bashing-om said:**
> shobuz99; Well ...
Nope not installed .. but looks to be the end of that short chain, round robin'n back to "gnome-terminal-data".
Good thing  -> is looks like all the snakes except this one are stomped on !
A conflict in versions installed ?
```

apt-cache showpkg gnome-terminal-data
dpkg -l gnome-terminal-data

```
and see about getting it's dependencies satisfied in the next move.

[INDENT][INDENT]keep'n on keep'n on[/INDENT][/INDENT]

All right. This looks new to me, as far as results:
```
rick@rick-desktop:~$ apt-cache showpkg gnome-terminal-data
Package: gnome-terminal-data
Versions: 
2.30.2-0ubuntu1 (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_lucid-updates_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_lucid-updates_main_binary-amd64_Packages
                  MD5: 9b9dc36a1c83dd9ce4cb3aedf50168f1

2.29.6-0ubuntu5 (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_lucid_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_lucid_main_binary-amd64_Packages
                  MD5: 9b9dc36a1c83dd9ce4cb3aedf50168f1


Reverse Depends: 
  gnome-terminal,gnome-terminal-data 2.28.1-1ubuntu1
  gnome-terminal,gnome-terminal-data 2.31
  gnome-terminal,gnome-terminal-data 2.30
  gnome-terminal,gnome-terminal-data 2.28.1-1ubuntu1
  gnome-terminal,gnome-terminal-data 2.30
  gnome-terminal,gnome-terminal-data 2.29
Dependencies: 
2.30.2-0ubuntu1 - gconf2 (2 2.10.1-2) gnome-terminal (0 (null)) 
2.29.6-0ubuntu5 - gconf2 (2 2.10.1-2) gnome-terminal (0 (null)) 
Provides: 
2.30.2-0ubuntu1 - 
2.29.6-0ubuntu5 - 
Reverse Provides: 
rick@rick-desktop:~$ 

```

Next results:

```
rick@rick-desktop:~$ dpkg -l gnome-terminal-data
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  gnome-terminal <none>         (no description available)
rick@rick-desktop:~$ 

```

??????????? ok. I'm listening.

shobuz99

---

### Post by Bashing-om on 2013-09-04
Shobuz99; Welp;

Here is my think'n;
"showpkg" is telling us there is a requirement for "gnome-terminal-data" version 2.30.2-0ubuntu1; However ->
There is a conflicting requirement for version 2.29.6-0ubuntu5 :
"dpkg" tells us "gnome-terminal-data" is not installed. Why, because the package manager does not know what we want to do.
" apt-cache rdepends gnome-terminal-data" - that is with an "R" - says we have to deal with  gnome-terminal:i386 .
I personally do not want to even think about downgrading the system to meet the version 2.29.6-0ubuntu5 requirement.

We have to update the application that presently requires the older version. Now all is updated on your system less ..... "Wine" !
Time to bite the bullet and TRY and update "Wine" and see what happens.

To that end; un-comment the old source in the file /etc/apt/sources.list, cross your fingers - hold your breath and:
```

sudo apt-get update
sudo apt-get upgrade

```
And we see if there is a catastrophic failure ... then see if maybe can upgrade "Wine" via the current PPA ???

It is my opinion, no matter what course is taken for restoration, "Wine" is going to have to be updated to current (10.04 latest) files .
So let's go for it !

[INDENT][INDENT]my opinion, 2nd and 3rd opinions are welcome
[/INDENT][/INDENT]

---

### Post by Jonathan Precise on 2013-09-05
> **Bashing-om said:**
> Shobuz99; Welp;

Here is my think'n;
"showpkg" is telling us there is a requirement for "gnome-terminal-data" version 2.30.2-0ubuntu1; However ->
There is a conflicting requirement for version 2.29.6-0ubuntu5 :
"dpkg" tells us "gnome-terminal-data" is not installed. Why, because the package manager does not know what we want to do.
" apt-cache rdepends gnome-terminal-data" - that is with an "R" - says we have to deal with  gnome-terminal:i386 .
I personally do not want to even think about downgrading the system to meet the version 2.29.6-0ubuntu5 requirement.
 
We have to update the application that presently requires the older version. Now all is updated on your system less ..... "Wine" !
Time to bite the bullet and TRY and update "Wine" and see what happens.

To that end; un-comment the old source in the file /etc/apt/sources.list, cross your fingers - hold your breath and:
```

sudo apt-get update
sudo apt-get upgrade

```
And we see if there is a catastrophic failure ... then see if maybe can upgrade "Wine" via the current PPA ???

It is my opinion, no matter what course is taken for restoration, "Wine" is going to have to be updated to current (10.04 latest) files .
So let's go for it !
[INDENT][INDENT]my opinion, 2nd and 3rd opinions are welcome
[/INDENT]
[/INDENT]


Try:
```
sudo apt-get install -f gnome-terminal-data gnome-mime-data
```
which forces the install of the packages.

Otherwise try:
```
sudo apt-get -f install
```
which takes care of the dependencies.

If the package manager still complains, then try:
```
sudo apt-get update
sudo apt-get -f upgrade
sudo apt-get -f install
```
forcing upgrades and fixing dependencies.

If it's dpkg that complains, then try:
```
sudo dpkg --configure --pending
```.

Otherwise, post all the results.

---

### Post by Jonathan Precise on 2013-09-05
> **Shobuz99 said:**
> 
```
rick@rick-desktop:~$ dpkg -l gnome-terminal-data
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  gnome-terminal <none>         (no description available)
rick@rick-desktop:~$ 

```

??????????? ok. I'm listening.

shobuz99

Shobuz99, :shock:!!!

Looks like gnome-terminal-data is half-installed!

Try my post above. That should fix everything.

---

### Post by Shobuz99 on 2013-09-05
> **Jonathan Precise said:**
> Shobuz99, :shock:!!!

Looks like gnome-terminal-data is half-installed!

Try my post above. That should fix everything.

Ok I took ALL the steps you listed in your first post:

```
rick@rick-desktop:~$ sudo apt-get install -f gnome-terminal-data gnome-mime-data
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libopal3.6.6 libxml++2.6-2 python-twisted-mail ubufox
  python-twisted-lore odbcinst1debian1 python-twisted-news
  libfile-find-rule-perl python-twisted-conch python-twisted-words libslv2-9
  libcapi20-3 odbcinst python-twisted unixodbc gettext rtkit libosmesa6 cvs
  libffado2 libtext-glob-perl libgnomecanvasmm-2.6-1c2a libpt2.6.5 liblo7
  libaubio2 python-twisted-runner liblrdf0 python-pyasn1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  gnome-mime-data gnome-terminal-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/452kB of archives.
After this operation, 14.0MB of additional disk space will be used.
Selecting previously deselected package gnome-mime-data.
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-headless' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2) 
rick@rick-desktop: 
```

Next:
```

rick@rick-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libopal3.6.6 libxml++2.6-2 python-twisted-mail ubufox
  python-twisted-lore odbcinst1debian1 python-twisted-news
  libfile-find-rule-perl python-twisted-conch python-twisted-words libslv2-9
  libcapi20-3 odbcinst python-twisted unixodbc gettext rtkit libosmesa6 cvs
  libffado2 libtext-glob-perl libgnomecanvasmm-2.6-1c2a libpt2.6.5 liblo7
  libaubio2 python-twisted-runner liblrdf0 python-pyasn1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-mime-data gnome-terminal-data
The following NEW packages will be installed:
  gnome-mime-data gnome-terminal-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/452kB of archives.
After this operation, 14.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package gnome-mime-data.
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-headless' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
rick@rick-desktop: 
```

Next:
```

rick@rick-desktop:~$ sudo apt-get update
Hit http://old-releases.ubuntu.com lucid Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-updates Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-backports Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-proposed Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Hit http://old-releases.ubuntu.com lucid Release
Hit http://old-releases.ubuntu.com lucid-updates Release
Hit http://old-releases.ubuntu.com lucid-backports Release
Hit http://old-releases.ubuntu.com lucid-security Release
Hit http://old-releases.ubuntu.com lucid-proposed Release
Hit http://old-releases.ubuntu.com lucid/main Packages
Hit http://old-releases.ubuntu.com lucid/restricted Packages
Hit http://old-releases.ubuntu.com lucid/universe Packages
Hit http://old-releases.ubuntu.com lucid/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-updates/main Packages
Hit http://old-releases.ubuntu.com lucid-updates/restricted Packages
Hit http://old-releases.ubuntu.com lucid-updates/universe Packages
Hit http://old-releases.ubuntu.com lucid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-backports/main Packages
Hit http://old-releases.ubuntu.com lucid-backports/restricted Packages
Hit http://old-releases.ubuntu.com lucid-backports/universe Packages
Hit http://old-releases.ubuntu.com lucid-backports/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Packages
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/restricted Packages
Hit http://old-releases.ubuntu.com lucid-proposed/main Packages
Hit http://old-releases.ubuntu.com lucid-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/universe Packages
Reading package lists... Done
rick@rick-desktop: 
```

Next:
```

rick@rick-desktop:~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed:
  gnome-mime-data gnome-terminal-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/452kB of archives.
After this operation, 14.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package gnome-mime-data.
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-headless' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
rick@rick-desktop: 
```

Next:
```

rick@rick-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libopal3.6.6 libxml++2.6-2 python-twisted-mail ubufox
  python-twisted-lore odbcinst1debian1 python-twisted-news
  libfile-find-rule-perl python-twisted-conch python-twisted-words libslv2-9
  libcapi20-3 odbcinst python-twisted unixodbc gettext rtkit libosmesa6 cvs
  libffado2 libtext-glob-perl libgnomecanvasmm-2.6-1c2a libpt2.6.5 liblo7
  libaubio2 python-twisted-runner liblrdf0 python-pyasn1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-mime-data gnome-terminal-data
The following NEW packages will be installed:
  gnome-mime-data gnome-terminal-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/452kB of archives.
After this operation, 14.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package gnome-mime-data.
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-headless' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
rick@rick-desktop: 
```
And finally:
```

rick@rick-desktop:~$ sudo dpkg --configure --pending
rick@rick-desktop:~$  
```

I have a question: What would happen if I switched the "sources list" back to the "archives" links
                          instead of the old.releases links???

Other than that, what else can be done, other than Bashing-om's idea (which I don't like) or 
I download 10.04 LTS 64 bit .iso file; burn a CD, and try to repair things from there if that's possible?

Incidentally, with all the attempts to fix the original problem with NetFlix and WINE Compholio;
My Dreamweaver MX 2004 appears to require set-up, as if it were just installed....
I installed that software YEARS AGO. Now it is acting like it was never set up and completely installed!!
Something is VERY broke, somewhere...

Anyway. Thanks again for your assistance.

BTW...I have not had a good Labor Day Weekend either. 
My 9 year old dog died of a brain tumor on Sunday Sept 1st.
My friend for 42 years is suffering from brain cancer and is in Hospice, 
and since June I've lost two other friends of mine to cancer and heart attack. 
This is not a good year for me, and this problem with Ubuntu's "dpkg" has badly exacerbated my whole emotional outlook.

I hope you can figure this out or I shall just give up. I'm serious.

Shobuz99

---

### Post by Jonathan Precise on 2013-09-05
> **Shobuz99 said:**
> Ok I took ALL the steps you listed in your first post:

```
rick@rick-desktop:~$ sudo apt-get install -f gnome-terminal-data gnome-mime-data
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libopal3.6.6 libxml++2.6-2 python-twisted-mail ubufox
  python-twisted-lore odbcinst1debian1 python-twisted-news
  libfile-find-rule-perl python-twisted-conch python-twisted-words libslv2-9
  libcapi20-3 odbcinst python-twisted unixodbc gettext rtkit libosmesa6 cvs
  libffado2 libtext-glob-perl libgnomecanvasmm-2.6-1c2a libpt2.6.5 liblo7
  libaubio2 python-twisted-runner liblrdf0 python-pyasn1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  gnome-mime-data gnome-terminal-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/452kB of archives.
After this operation, 14.0MB of additional disk space will be used.
Selecting previously deselected package gnome-mime-data.
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-headless' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2) 
rick@rick-desktop: 
```

Next:
```

rick@rick-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libopal3.6.6 libxml++2.6-2 python-twisted-mail ubufox
  python-twisted-lore odbcinst1debian1 python-twisted-news
  libfile-find-rule-perl python-twisted-conch python-twisted-words libslv2-9
  libcapi20-3 odbcinst python-twisted unixodbc gettext rtkit libosmesa6 cvs
  libffado2 libtext-glob-perl libgnomecanvasmm-2.6-1c2a libpt2.6.5 liblo7
  libaubio2 python-twisted-runner liblrdf0 python-pyasn1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-mime-data gnome-terminal-data
The following NEW packages will be installed:
  gnome-mime-data gnome-terminal-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/452kB of archives.
After this operation, 14.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package gnome-mime-data.
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-headless' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
rick@rick-desktop: 
```

Next:
```

rick@rick-desktop:~$ sudo apt-get update
Hit http://old-releases.ubuntu.com lucid Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-updates Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-backports Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-proposed Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Hit http://old-releases.ubuntu.com lucid Release
Hit http://old-releases.ubuntu.com lucid-updates Release
Hit http://old-releases.ubuntu.com lucid-backports Release
Hit http://old-releases.ubuntu.com lucid-security Release
Hit http://old-releases.ubuntu.com lucid-proposed Release
Hit http://old-releases.ubuntu.com lucid/main Packages
Hit http://old-releases.ubuntu.com lucid/restricted Packages
Hit http://old-releases.ubuntu.com lucid/universe Packages
Hit http://old-releases.ubuntu.com lucid/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-updates/main Packages
Hit http://old-releases.ubuntu.com lucid-updates/restricted Packages
Hit http://old-releases.ubuntu.com lucid-updates/universe Packages
Hit http://old-releases.ubuntu.com lucid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-backports/main Packages
Hit http://old-releases.ubuntu.com lucid-backports/restricted Packages
Hit http://old-releases.ubuntu.com lucid-backports/universe Packages
Hit http://old-releases.ubuntu.com lucid-backports/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Packages
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/restricted Packages
Hit http://old-releases.ubuntu.com lucid-proposed/main Packages
Hit http://old-releases.ubuntu.com lucid-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-proposed/universe Packages
Reading package lists... Done
rick@rick-desktop: 
```

Next:
```

rick@rick-desktop:~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed:
  gnome-mime-data gnome-terminal-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/452kB of archives.
After this operation, 14.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package gnome-mime-data.
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-headless' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
rick@rick-desktop: 
```

Next:
```

rick@rick-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libnumber-compare-perl libopal3.6.6 libxml++2.6-2 python-twisted-mail ubufox
  python-twisted-lore odbcinst1debian1 python-twisted-news
  libfile-find-rule-perl python-twisted-conch python-twisted-words libslv2-9
  libcapi20-3 odbcinst python-twisted unixodbc gettext rtkit libosmesa6 cvs
  libffado2 libtext-glob-perl libgnomecanvasmm-2.6-1c2a libpt2.6.5 liblo7
  libaubio2 python-twisted-runner liblrdf0 python-pyasn1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-mime-data gnome-terminal-data
The following NEW packages will be installed:
  gnome-mime-data gnome-terminal-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/452kB of archives.
After this operation, 14.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package gnome-mime-data.
(Reading database ... 
dpkg: warning: files list file for package `icedtea-6-jre-cacao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openjdk-6-jre-headless' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `openjdk-6-jre' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
rick@rick-desktop: 
```
And finally:
```

rick@rick-desktop:~$ sudo dpkg --configure --pending
rick@rick-desktop:~$  
```

I have a question: What would happen if I switched the "sources list" back to the "archives" links
                          instead of the old.releases links???

Other than that, what else can be done, other than Bashing-om's idea (which I don't like) or 
I download 10.04 LTS 64 bit .iso file; burn a CD, and try to repair things from there if that's possible?

Incidentally, with all the attempts to fix the original problem with NetFlix and WINE Compholio;
My Dreamweaver MX 2004 appears to require set-up, as if it were just installed....
I installed that software YEARS AGO. Now it is acting like it was never set up and completely installed!!
Something is VERY broke, somewhere...

Anyway. Thanks again for your assistance.

BTW...I have not had a good Labor Day Weekend either. 
My 9 year old dog died of a brain tumor on Sunday Sept 1st.
My friend for 42 years is suffering from brain cancer and is in Hospice, 
and since June I've lost two other friends of mine to cancer and heart attack. 
This is not a good year for me, and this problem with Ubuntu's "dpkg" has badly exacerbated my whole emotional outlook.

I hope you can figure this out or I shall just give up. I'm serious.

Shobuz99

This gets weirder every time! I personally never saw anything like this!!!!!

However, there has to be a solution:-k. Try:
```
cat /var/lib/dpkg/info/openjdk-6-jre.list | less
sudo mv /var/lib/dpkg/info/openjdk-6-jre.list /var/lib/dpkg/info/openjdk-6-jre-backup.list
sudo apt-get update
sudo apt-get -f install
```

Please post the outputs of everything.

As for Dreamweaver, I think I might know why. When Dreamweaver has installed, wine-compholio was too. Uninstalling wine-compholio might change circumstances that Dreamweaver was installed on, thus re-doing the setup process (don't worry if you don't understand;-)!)

BTW, I'm sorry to hear about that:cry:. I hope this gets fixed.

---

### Post by bapoumba on 2013-09-05
> **Shobuz99 said:**
> 

I have a question: What would happen if I switched the "sources list" back to the "archives" links
                          instead of the old.releases links???
You cannot, the repos for 10.04 are not on the main archives any more.
> **Shobuz99 said:**
> 
Other than that, what else can be done, other than Bashing-om's idea (which I don't like) or 
I download 10.04 LTS 64 bit .iso file; burn a CD, and try to repair things from there if that's possible?


Should work. Remember to change the sources.list to the old releases repos.

Sorry for the bad times, sending some sunshine over :KS

---

### Post by Shobuz99 on 2013-09-07
> **bapoumba said:**
> You cannot, the repos for 10.04 are not on the main archives any more.

Should work. Remember to change the sources.list to the old releases repos.

Sorry for the bad times, sending some sunshine over :KS

I received your sunshine yesterday, and I thank you for it. :-) It really does help.
I also read your advice and I think I will take it....
BUT, life lately, has been handing me some things that take my attention away from my little insignificant problems with Ubuntu.
So I've decided that I will suspend my efforts to "fix" my Desktop's issues for now.
I hope that there is a way to "save" this thread so that I can return to it at a later date.
I'd mark it "solved", but it really isn't solved and I don't want someone to think it is
and go through the process like I did, only to be disappointed that there's not a solution that is provable
by this thread... 
Would it be possible to suspend this for a couple weeks? 
I just don't know if I'll be able to return to this right away...

In the mean time, I must thank you very kindly for your help and your advice and your patience with me.
Although I'm not an "Absolute Beginner", I have greatly benefited from yours and Bashing-Om's wise counsel.

I sincerely appreciate it.
Thank you very much :-)
Rick White (sbobuz99)

---

### Post by bapoumba on 2013-09-07
No worries, just come back to the thread when you feel like it, it will be waiting for you.

Now, if you wish no one posts in it during that period, I can lock it. You'll have to ask it be reopened before you can post in this thread again. Best way would be to report it so that someone on Staff reopens (in case I'd not be around for a day or two).

---

### Post by Shobuz99 on 2013-09-07
> **bapoumba said:**
> No worries, just come back to the thread when you feel like it, it will be waiting for you.

Now, if you wish no one posts in it during that period, I can lock it. You'll have to ask it be reopened before you can post in this thread again. Best way would be to report it so that someone on Staff reopens (in case I'd not be around for a day or two).
That would be great!
Yes, please lock it. I will ask to have it reopened, when I get to it.
Thank you so much. 
I do appreciate it.

Sbobuz99

---

### Post by bapoumba on 2013-09-07
Closed per OP's request.

---

