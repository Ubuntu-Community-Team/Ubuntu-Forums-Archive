---
title: "Draftsight for Ubuntu does not Install."
date: 2012-03-06
forum: New to Ubuntu
---

### Post by Grrruff on 2012-03-06
Ubuntu 11.10
Tried to Run & Install "Draftsight for Ubuntu".
From
[http://www.3ds.com/products/draftsight/download-draftsight/](http://www.3ds.com/products/draftsight/download-draftsight/)

I choose Open with Ubuntu Software Center and it stops trying to install after a few minutes with an error.

Is this the way to go about it?

Can I install it with "Open with Archive manager"?

Totally Confused here.  Draftsight is a great clone of AutoCad.
I would really like to get it intalled on Ubuntu as it is installed on my Windows PC and Mac.

---

### Post by Script Warlock on 2012-03-06
sudo dpkg -i draftsight.deb if an error ocurs sudo apt-get -f install

---

### Post by Grrruff on 2012-03-07
> **Script Warlock said:**
> sudo dpkg -i draftsight.deb if an error ocurs sudo apt-get -f install

Okay Tried that and i do not see draftsight listed anywhere.  Where would it be located if installed?

What happened when I entered your termianl commands

```

gruff@gruff-OptiPlex-170L:~$ sudo dpkg -i draftsight.deb
[sudo] password for gruff: 
dpkg: error processing draftsight.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 draftsight.deb
gruff@gruff-OptiPlex-170L:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libts-0.0-0 libdirectfb-extra libdirectfb-1.2-9 tsconf
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gruff@gruff-OptiPlex-170L:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
gruff@gruff-OptiPlex-170L:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libdirectfb-1.2-9 libdirectfb-extra libts-0.0-0 tsconf
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 2,478 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 168978 files and directories currently installed.)
Removing libdirectfb-extra ...
Removing libdirectfb-1.2-9 ...
Removing libts-0.0-0 ...
Removing tsconf ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
gruff@gruff-OptiPlex-170L:~$ draftsight
draftsight: command not found

```

---

### Post by Daveth on 2012-03-07
have you still got the draftsight.deb file saved? I'm not sure you installed it from running through that output.
Go to it, right click and under properties, tick "Allow executing file as program", then right click again and "Open with Gdebi package installer".
That will either load it up, tell you it has not met all the dependencies it needs, and either go and get them, or wait for you to source and install them before your next install attempt. It was compiled with version 9.10 in mind.

---

### Post by Script Warlock on 2012-03-07
apt-get install libdirectfb-extra
dpkg -i draftsight.deb

---

### Post by Just call me Oldmate on 2012-04-02
[Thanks Script Warlock.]("http://ubuntuforums.org/member.php?u=299765") It almost got the better of me until I found your directions. I almost had to reboot kruddy old Windows. Ya saved the day!
[]("http://ubuntuforums.org/member.php?u=299765")

---

### Post by Fraoch on 2012-04-11
For future reference of anyone coming across this later, I found the reason draftSight would not install using Ubuntu Software Centre is that Ubuntu Software Centre would not allow the draftSight licence acceptance/rejection box to appear.

The command-line dpkg command listed here does allow it to appear.  I'm not sure about other methods (gdebi?)

The licence window must appear because draftSight is proprietary.

---

### Post by Just call me Oldmate on 2012-04-28
I upgraded to 12.04 and now I cannot install DraftSight again.

---

### Post by Just call me Oldmate on 2012-04-29
A couple hours of research and this is what I've got for installing DraftSight to Ubuntu 12.04 (64bit).

sudo apt-get install libdirectfb-extra

sudo apt-get install libxcb-render-util0

sudo apt-get install libaudio2

move the draftSight.deb package out of your Downloads folder and into your Home folder

 sudo dpkg -i --force-architecture,depends ./draftSight.deb

---

### Post by 52rockwell on 2012-05-20
> **Just call me Oldmate said:**
> A couple hours of research and this is what I've got for installing DraftSight to Ubuntu 12.04 (64bit).

sudo apt-get install libdirectfb-extra

sudo apt-get install libxcb-render-util0

sudo apt-get install libaudio2

move the draftSight.deb package out of your Downloads folder and into your Home folder

 sudo dpkg -i --force-architecture,depends ./draftSight.deb

Thanks Oldmate..

---

### Post by aquascrotum on 2012-06-01
Just tried installing Draftsight using 12.04 defaults (open .deb in Software Centre) - installation failed.

Used Gdebi (after right clicking the deb, Open with other package, find package online) and installation flew through.

Is the issue with installation via Software Centre a Ubuntu bug (given it is ubuntus default) or a Draftsight bug?  Where would one go about reporting it?

---

### Post by Fraoch on 2012-06-02
> **aquascrotum said:**
> Just tried installing Draftsight using 12.04 defaults (open .deb in Software Centre) - installation failed.

Used Gdebi (after right clicking the deb, Open with other package, find package online) and installation flew through.

Is the issue with installation via Software Centre a Ubuntu bug (given it is ubuntus default) or a Draftsight bug?  Where would one go about reporting it?

As I indicated a few posts earlier, it's because the Software Centre will not allow the licence acceptance/decline box to come up.

Gdebi or apt-get install will.

It's a Software Centre bug in that Software Centre doesn't call up an additional dialog box not usually present in most .debs.

Bugs should be reported in [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) though for some reason it can't find "Software Centre" right now...?

More info: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by 00negative on 2012-06-09
> **Just call me Oldmate said:**
> A couple hours of research and this is what I've got for installing DraftSight to Ubuntu 12.04 (64bit).

sudo apt-get install libdirectfb-extra

sudo apt-get install libxcb-render-util0

sudo apt-get install libaudio2

move the draftSight.deb package out of your Downloads folder and into your Home folder

 sudo dpkg -i --force-architecture,depends ./draftSight.deb

This fixed the issue for me. Thanks.

---

### Post by pdipofi on 2012-06-10
I have tried everythingbut still get an error while attempting to install using Gdebi Package installer.  Any suggestions

---

### Post by viju on 2012-07-07
Daveth,
I followed your instruction and sucseessfully installed Draft Sight.I am using Ubuntu11.04.

---

### Post by viju on 2012-07-07
Draft Sight does not open if I am off line(ie.not connected with internet.

---

### Post by dusanyu on 2012-07-15
> **Just call me Oldmate said:**
> A couple hours of research and this is what I've got for installing DraftSight to Ubuntu 12.04 (64bit).

sudo apt-get install libdirectfb-extra

sudo apt-get install libxcb-render-util0

sudo apt-get install libaudio2

move the draftSight.deb package out of your Downloads folder and into your Home folder

 sudo dpkg -i --force-architecture,depends ./draftSight.deb

following these instructions installs draft sight but afterwords i get a message about broken dependacies and to run "apt-get install -f"

wich promptly removes draftsight

---

### Post by mungatsuma on 2012-07-31
> **Just call me Oldmate said:**
> A couple hours of research and this is what I've got for installing DraftSight to Ubuntu 12.04 (64bit).

sudo apt-get install libdirectfb-extra

sudo apt-get install libxcb-render-util0

sudo apt-get install libaudio2

move the draftSight.deb package out of your Downloads folder and into your Home folder

 sudo dpkg -i --force-architecture,depends ./draftSight.deb

Thanks for the code it works like a charm.

---

### Post by wolfris on 2012-08-07
> **dusanyu said:**
> following these instructions installs draft sight but afterwords i get a message about broken dependacies and to run "apt-get install -f"

wich promptly removes draftsight

Same happens to me...need to re-install draftsight each time I want to use it.

---

### Post by dwaindibbley65 on 2012-08-29
> **Just call me Oldmate said:**
> A couple hours of research and this is what I've got for installing DraftSight to Ubuntu 12.04 (64bit).

sudo apt-get install libdirectfb-extra

sudo apt-get install libxcb-render-util0

sudo apt-get install libaudio2

move the draftSight.deb package out of your Downloads folder and into your Home folder

 sudo dpkg -i --force-architecture,depends ./draftSight.deb
Worked for me... Thanks everso

---

### Post by apatrick on 2012-09-02
In the package installer, I'm getting:

Error: Dependency is not satisfiable:
libcomerr2 (>1.41.9-1)

Poking around in Terminal, libcomerr2's most current version is installed... Is the most current version 1.42.5? Do I need to go back and install an older version of libcomerr2?

Anybody else have this problem?

---

### Post by Nostronna on 2013-01-22
> **Daveth said:**
> have you still got the draftsight.deb file saved? I'm not sure you installed it from running through that output.
Go to it, right click and under properties, tick "Allow executing file as program", then right click again and "Open with Gdebi package installer".
That will either load it up, tell you it has not met all the dependencies it needs, and either go and get them, or wait for you to source and install them before your next install attempt. It was compiled with version 9.10 in mind.

Thanks to Davet! I had a problem installing draftsight and I solved it just using Gdebi on your instructions....Brilliant!

---

