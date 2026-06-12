---
title: "unable to install muon update -manager"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by AmitSinha on 2013-10-18
Hi All , 

I am new to the Ubuntu environment,and I am loving it. I am unable to install muon update-manager or any other software updater.

* I was using the Ubuntu Software Center for the installation initially.
* When it didn't work , I did some search on the internet ,and then tried the Synaptic Package Manager - which didn't work too.

I am getting the following errors :

* Error when using the Ubuntu Software Center :

-----------------------------------------------------------------------------------------------------------------------------
Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time

Details :

The following packages have unmet dependencies:


muon-updater: Depends: libc6 (>= 2.3.4) but 2.17-0ubuntu5 is to be installed
              Depends: libkdecore5 (>= 4:4.4.0) but 4:4.10.5-0ubuntu0.1 is to be installed
              Depends: libkdeui5 (>= 4:4.7.0) but 4:4.10.5-0ubuntu0.1 is to be installed
              Depends: libkio5 (>= 4:4.3.4) but 4:4.10.5-0ubuntu0.1 is to be installed
              Depends: libmuonprivate1 (= 1.9.80-0ubuntu1) but 1.9.80-0ubuntu1 is to be installed
              Depends: libqtcore4 (>= 4:4.7.0~beta2) but 4:4.8.4+dfsg-0ubuntu9.4 is to be installed
              Depends: libqtgui4 (>= 4:4.5.3) but 4:4.8.4+dfsg-0ubuntu9.4 is to be installed
              Depends: libsolid4 (>= 4:4.3.4) but 4:4.10.5-0ubuntu0.1 is to be installed
              Depends: libstdc++6 (>= 4.1.1) but 4.7.3-1ubuntu1 is to be installed

-----------------------------------------------------------------------------------------------------------------------------


* Error with the Synaptic Package Manager :

Could not apply changes!
Fix broken packages first.




-----------------------------------------------------------------------------------------------------------------------------

I have already tried the following commands from the terminal , but did't work :


 
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade



Please help !

Thanks.

---

### Post by ibjsb4 on 2013-10-18
Muon update-manager is for Kubuntu (KDE).  Are you running Ubuntu or Kubuntu?

If your running Ubuntu try this in terminal:

```
sudo apt-get install synaptic
```

Please post the errors.

---

### Post by oldos2er on 2013-10-18
Which version of Ubuntu are you using?

Use Synaptic to fix broken packages, menu Edit, Fix Broken Packages.

---

### Post by AmitSinha on 2013-10-18
Thanks for the replay.

I am using Ubuntu 13.04
I don't have any Software Updater installed on my system.As advised , I tried using the Synaptic Package Manager , to fix the broken packages , but I am getting the below error :

--------------------------------------------------------------------------------------------------------------
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
--------------------------------------------------------------------------------------------------------------

---

### Post by AmitSinha on 2013-10-18
Hi Ann ,

Thanks for the reply . I tried using the Synaptic Package Manager , to fix the broken packages , but I am getting the below error :

--------------------------------------------------------------------------------------------------------------
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
--------------------------------------------------------------------------------------------------------------

---

### Post by oldos2er on 2013-10-18
Try ```
sudo apt-get update

sudo apt-get -u dist-upgrade
``` If there are errors, please copy and paste the full terminal output here.

---

### Post by AmitSinha on 2013-10-19
> **oldos2er said:**
> Try ```
sudo apt-get update

sudo apt-get -u dist-upgrade
``` If there are errors, please copy and paste the full terminal output here.


Errors after running ```
sudo apt-get update
``` ```
&#8203;Fetched 7,132 B in 2min 0s (59 B/s)Reading package lists... Done
W: GPG error: http://archive.canonical.com raring Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com raring Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>


W: GPG error: http://dl.google.com stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
W: GPG error: http://ppa.launchpad.net raring Release: The following signatures were invalid: BADSIG 77589CABF0B5D826 Launchpad antigone
W: GPG error: http://ppa.launchpad.net raring Release: The following signatures were invalid: BADSIG 8FC2C0DC77296259 Launchpad PPA for ffDiaporama Team
W: GPG error: http://singo.ub.ac.id raring Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ppa.launchpad.net raring Release: The following signatures were invalid: BADSIG D530E028F59EAE4D Launchpad PPA for NoobsLab
W: GPG error: http://ppa.launchpad.net raring Release: The following signatures were invalid: BADSIG D530E028F59EAE4D Launchpad PPA for NoobsLab
W: GPG error: http://singo.ub.ac.id raring-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://singo.ub.ac.id raring-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://singo.ub.ac.id raring-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://singo.ub.ac.id raring-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/Release  


W: Failed to fetch http://ppa.launchpad.net/noobslab/swar-themes/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found


W: Some index files failed to download. They have been ignored, or old ones used instead.
amit@amit-desktop:~$ 



```

Terminal O/P on running  ```
sudo apt-get dist upgrade
``` ```
 amit@amit-desktop:~$ sudo apt-get -u dist-upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  google-chrome-stable
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
amit@amit-desktop:~$ 


 
```


Thanks !

---

### Post by ibjsb4 on 2013-10-19
> W: Failed to fetch [http://ppa.launchpad.net/noobslab/swar-themes/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/noobslab/swar-themes/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

This package not available in Raring, remove it.

[http://ppa.launchpad.net/noobslab/swar-themes/ubuntu/dists/](http://ppa.launchpad.net/noobslab/swar-themes/ubuntu/dists/)

> W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures were invalid: BADSIG 77589CABF0B5D826 Launchpad antigone W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures were invalid: BADSIG 8FC2C0DC77296259 Launchpad PPA for ffDiaporama Team W: GPG error: [http://singo.ub.ac.id](http://singo.ub.ac.id) raring Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures were invalid: BADSIG D530E028F59EAE4D Launchpad PPA for NoobsLab W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures were invalid: BADSIG D530E028F59EAE4D Launchpad PPA for NoobsLab W: GPG error: [http://singo.ub.ac.id](http://singo.ub.ac.id) raring-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com> W: GPG error: [http://singo.ub.ac.id](http://singo.ub.ac.id) raring-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com> W: GPG error: [http://singo.ub.ac.id](http://singo.ub.ac.id) raring-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com> W: GPG error: [http://singo.ub.ac.id](http://singo.ub.ac.id) raring-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

[GPG error BADSIG]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+BADSIG&sa=Search&cof=FORID:9")

---

### Post by newb85 on 2013-10-19
As ibjsb4 points out, the noobslab swar-themes PPA isn't available for any release after Precise, so it needs to be removed.  (You *could* change it to the Precise branch of the PPA, but that can be very problematic and isn't recommended.)

More importantly, your GPG BADSIG error can be taken care of thus:
```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

---

### Post by AmitSinha on 2013-10-19
> **newb85 said:**
> As ibjsb4 points out, the noobslab swar-themes PPA isn't available for any release after Precise, so it needs to be removed.  (You *could* change it to the Precise branch of the PPA, but that can be very problematic and isn't recommended.)

More importantly, your GPG BADSIG error can be taken care of thus:
```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

Thanks for the replay.I ran the commands , and the terminal O/P after running all the commands is : ```
Fetched 11.6 MB in 2min 21s (82.0 kB/s)W: Failed to fetch http://ppa.launchpad.net/noobslab/swar-themes/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
amit@amit-desktop:/var/lib/apt$ 

```

After this I tried to install the Update Manager from Ubuntu Software Center , but again the same error :

```
Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Details :
The following packages have unmet dependencies:


update-manager: Depends: update-manager-core (= 1:0.180) but 1:0.186.2 is to be installed

```


Also,tried the Synaptic Package Manager , but got the following error :



An error occurred.

The following details are provided:

E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies



Please help !

Thanks

---

### Post by AmitSinha on 2013-10-20
Can this not be resolved ?
:-(

---

### Post by oldos2er on 2013-10-20
Did you remove the swar-themes PPA? Also if you have any other PPAs I would remove or disable them until we can get your APT problem solved.

Can you post your sources.list file? ```
cat /etc/apt/sources.list
```

---

### Post by AmitSinha on 2013-10-20
> **oldos2er said:**
> Did you remove the swar-themes PPA? Also if you have any other PPAs I would remove or disable them until we can get your APT problem solved.

Can you post your sources.list file? ```
cat /etc/apt/sources.list
```

When I try to remove_ swar-themes_ I get the following _error_ :

```
 amit@amit-desktop:~$ sudo apt-get remove swar-themesReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package swar-themes


 
```

here is the _/etc/apt/sources.list_ file :


```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb http://singo.ub.ac.id/ubuntu/ raring main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://singo.ub.ac.id/ubuntu/ raring-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://singo.ub.ac.id/ubuntu/ raring universe
deb http://singo.ub.ac.id/ubuntu/ raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://singo.ub.ac.id/ubuntu/ raring multiverse
deb http://singo.ub.ac.id/ubuntu/ raring-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://singo.ub.ac.id/ubuntu/ raring-backports main restricted universe multiverse


deb http://singo.ub.ac.id/ubuntu/ raring-security main restricted
deb http://singo.ub.ac.id/ubuntu/ raring-security universe
deb http://singo.ub.ac.id/ubuntu/ raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
# deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://singo.ub.ac.id/ubuntu/ raring-proposed restricted main multiverse universe


~
~
~
~
~
~
~
~
(END)



```


Thanks

---

### Post by newb85 on 2013-10-20
There are no PPAs listed in your sources.list file, but they may have their own files.

```
ls /etc/apt/sources.list.d
```
should show any PPA files that have been added.  You can then cat those files and post their contents.

---

### Post by oldos2er on 2013-10-21
> **AmitSinha said:**
> When I try to remove_ swar-themes_ I get the following _error_ :

```
 amit@amit-desktop:~$ sudo apt-get remove swar-themesReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package swar-themes

```

To remove the PPA you need to run ```
sudo add-apt-repository -r ppa:noobslab/swar-themes
``` and then ```
sudo apt-get update
```.

I'm not familiar with the [http://singo.ub.ac.id/ubuntu/](http://singo.ub.ac.id/ubuntu/) mirror you're using, and I wonder if changing to the main server would solve the unmet dependencies issue. If you are able to open Software Center, click the Edit menu, Software Sources, on the Ubuntu software tab check Download from main server.

---

### Post by AmitSinha on 2013-10-21
> **oldos2er said:**
> To remove the PPA you need to run ```
sudo add-apt-repository -r ppa:noobslab/swar-themes
``` and then ```
sudo apt-get update
```.

I'm not familiar with the [http://singo.ub.ac.id/ubuntu/](http://singo.ub.ac.id/ubuntu/) mirror you're using, and I wonder if changing to the main server would solve the unmet dependencies issue. If you are able to open Software Center, click the Edit menu, Software Sources, on the Ubuntu software tab check Download from main server.

After running _sudo add-apt-repository -r ppa:noobslab/swar-themes_ :
```


amit@amit-desktop:~$ sudo add-apt-repository -r ppa:noobslab/swar-themesYou are about to remove the following PPA from your system:
 Transparent Swar Themes for Ubuntu/Linux Mint/Ubuntu based Distributions.
Support GTK-2 and GTK-3.
For Transparency Visit http://www.NoobsLab.com
 More info: https://launchpad.net/~noobslab/+archive/swar-themes
Press [ENTER] to continue or ctrl-c to cancel removing it


amit@amit-desktop:~$ 



```

I am able to open the Software Center , but the "Software Resources" option in the Edit Menu , is disabled !

Here is the O/P of _ls -lrt /etc/apt/sources.list.d_ :

```


amit@amit-desktop:~$ ls -lrt /etc/apt/sources.list.d
total 256
-rw-r--r-- 1 root root 210 Nov  5  2012 google-earth.list.distUpgrade
-rw-r--r-- 1 root root 210 Feb 25  2013 google-earth.list.save
-rw-r--r-- 1 root root 130 Apr 27 02:36 tualatrix-ppa-quantal.list.distUpgrade
-rw-r--r-- 1 root root 157 Apr 27 02:36 private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list.distUpgrade
-rw-r--r-- 1 root root 146 Apr 27 02:36 noobslab-malys-themes-quantal.list.distUpgrade
-rw-r--r-- 1 root root 136 Apr 27 02:36 webupd8team-java-quantal.list.distUpgrade
-rw-r--r-- 1 root root 140 Apr 27 02:36 upubuntu-com-icons-quantal.list.distUpgrade
-rw-r--r-- 1 root root 138 Apr 27 02:36 upubuntu-com-gtk3-quantal.list.distUpgrade
-rw-r--r-- 1 root root  91 Apr 27 02:36 ubuntu-wine-ppa-quantal.list.distUpgrade
-rw-r--r-- 1 root root  95 Apr 27 02:36 tiheum-equinox-quantal.list.distUpgrade
-rw-r--r-- 1 root root 228 Apr 27 02:36 stebbins-handbrake-releases-precise.list.distUpgrade
-rw-r--r-- 1 root root 144 Apr 27 02:36 scopes-packagers-ppa-quantal.list.distUpgrade
-rw-r--r-- 1 root root  82 Apr 27 02:36 oneiric-partner.list.distUpgrade
-rw-r--r-- 1 root root 134 Apr 27 02:36 noobslab-themes-quantal.list.distUpgrade
-rw-r--r-- 1 root root 180 Apr 27 02:36 google-talkplugin.list.distUpgrade
-rw-r--r-- 1 root root 176 Apr 27 02:36 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 156 Apr 27 02:36 fyrmir-livewallpaper-daily-quantal.list.distUpgrade
-rw-r--r-- 1 root root 134 Apr 27 02:36 atareao-atareao-quantal.list.distUpgrade
-rw-r--r-- 1 root root   0 Oct 10 23:46 noobslab-noobslab-conky-raring.list.save
-rw-r--r-- 1 root root   0 Oct 10 23:46 noobslab-noobslab-conky-raring.list
-rw-r--r-- 1 root root 196 Oct 22 00:10 tualatrix-ppa-quantal.list.save
-rw-r--r-- 1 root root 228 Oct 22 00:10 stebbins-handbrake-releases-precise.list.save
-rw-r--r-- 1 root root 188 Oct 22 00:10 private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list.save
-rw-r--r-- 1 root root  70 Oct 22 00:10 noobslab-themes-raring.list.save
-rw-r--r-- 1 root root 212 Oct 22 00:10 noobslab-malys-themes-quantal.list.save
-rw-r--r-- 1 root root 148 Oct 22 00:10 ffdiaporamateam-stable-raring.list.save
-rw-r--r-- 1 root root 136 Oct 22 00:10 alecive-antigone-raring.list.save
-rw-r--r-- 1 root root 202 Oct 22 00:10 webupd8team-java-quantal.list.save
-rw-r--r-- 1 root root 146 Oct 22 00:10 videolan-stable-daily-raring.list.save
-rw-r--r-- 1 root root 122 Oct 22 00:10 ubuntu-wine-ppa-quantal.list.save
-rw-r--r-- 1 root root  95 Oct 22 00:10 tiheum-equinox-quantal.list.save
-rw-r--r-- 1 root root 156 Oct 22 00:10 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save
-rw-r--r-- 1 root root  81 Oct 22 00:10 oneiric-partner.list.save
-rw-r--r-- 1 root root 198 Oct 22 00:10 noobslab-themes-quantal.list.save
-rw-r--r-- 1 root root 142 Oct 22 00:10 noobslab-screenlets-raring.list.save
-rw-r--r-- 1 root root 180 Oct 22 00:10 google-talkplugin.list.save
-rw-r--r-- 1 root root 222 Oct 22 00:10 fyrmir-livewallpaper-daily-quantal.list.save
-rw-r--r-- 1 root root 200 Oct 22 00:10 atareao-atareao-quantal.list.save
-rw-r--r-- 1 root root 202 Oct 22 00:10 webupd8team-java-quantal.list
-rw-r--r-- 1 root root 206 Oct 22 00:10 upubuntu-com-icons-quantal.list.save
-rw-r--r-- 1 root root 206 Oct 22 00:10 upubuntu-com-icons-quantal.list
-rw-r--r-- 1 root root 204 Oct 22 00:10 upubuntu-com-gtk3-quantal.list.save
-rw-r--r-- 1 root root 228 Oct 22 00:10 stebbins-handbrake-releases-precise.list
-rw-r--r-- 1 root root 210 Oct 22 00:10 scopes-packagers-ppa-quantal.list.save
-rw-r--r-- 1 root root   0 Oct 22 00:10 noobslab-swar-themes-raring.list.save
-rw-r--r-- 1 root root   0 Oct 22 00:10 noobslab-swar-themes-raring.list
-rw-r--r-- 1 root root 134 Oct 22 00:10 noobslab-icons2-raring.list.save
-rw-r--r-- 1 root root 134 Oct 22 00:10 noobslab-icons2-raring.list
-rw-r--r-- 1 root root 176 Oct 22 00:10 google-chrome.list.save
-rw-r--r-- 1 root root 222 Oct 22 00:10 fyrmir-livewallpaper-daily-quantal.list
-rw-r--r-- 1 root root 200 Oct 22 00:10 atareao-atareao-quantal.list
-rw-r--r-- 1 root root 146 Oct 22 00:10 videolan-stable-daily-raring.list
-rw-r--r-- 1 root root 204 Oct 22 00:10 upubuntu-com-gtk3-quantal.list
-rw-r--r-- 1 root root 122 Oct 22 00:10 ubuntu-wine-ppa-quantal.list
-rw-r--r-- 1 root root 196 Oct 22 00:10 tualatrix-ppa-quantal.list
-rw-r--r-- 1 root root  95 Oct 22 00:10 tiheum-equinox-quantal.list
-rw-r--r-- 1 root root 210 Oct 22 00:10 scopes-packagers-ppa-quantal.list
-rw-r--r-- 1 root root 156 Oct 22 00:10 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list
-rw-r--r-- 1 root root 188 Oct 22 00:10 private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list
-rw-r--r-- 1 root root  81 Oct 22 00:10 oneiric-partner.list
-rw-r--r-- 1 root root  70 Oct 22 00:10 noobslab-themes-raring.list
-rw-r--r-- 1 root root 198 Oct 22 00:10 noobslab-themes-quantal.list
-rw-r--r-- 1 root root 142 Oct 22 00:10 noobslab-screenlets-raring.list
-rw-r--r-- 1 root root 212 Oct 22 00:10 noobslab-malys-themes-quantal.list
-rw-r--r-- 1 root root 180 Oct 22 00:10 google-talkplugin.list
-rw-r--r-- 1 root root 176 Oct 22 00:10 google-chrome.list
-rw-r--r-- 1 root root 148 Oct 22 00:10 ffdiaporamateam-stable-raring.list
-rw-r--r-- 1 root root 136 Oct 22 00:10 alecive-antigone-raring.list
amit@amit-desktop:~$ 




```


Issue still persists :-(

Thanks

---

### Post by oldos2er on 2013-10-21
Wow, that's quite a load of PPAs! And for several different versions of Ubuntu--no wonder your package manager's confused. Let's clean that up. Run ```
sudo mv /etc/apt/sources.list.d/* /home/amit/
``` This will put them all in your home folder for the time being, where APT can't find them. Now ```
sudo apt-get update && sudo apt-get dist-upgrade
``` which should get you up-to-date.

Hopefully this will clear any errors, but if not, please post back. If you wish to add back your PPAs, do so only one at a time, and *only* if they are for your current Ubuntu version (the others I would simply delete). You should always run ```
sudo apt-get update
``` after each change such as adding or removing a PPA or other repository.

---

### Post by AmitSinha on 2013-10-21
> **oldos2er said:**
> Wow, that's quite a load of PPAs! And for several different versions of Ubuntu--no wonder your package manager's confused. Let's clean that up. Run ```
sudo mv /etc/apt/sources.list.d/* /home/amit/
``` This will put them all in your home folder for the time being, where APT can't find them. Now ```
sudo apt-get update && sudo apt-get dist-upgrade
``` which should get you up-to-date.

Hopefully this will clear any errors, but if not, please post back. If you wish to add back your PPAs, do so only one at a time, and *only* if they are for your current Ubuntu version (the others I would simply delete). You should always run ```
sudo apt-get update
``` after each change such as adding or removing a PPA or other repository.

Did as advised,still not able to install "Software Updater" :-(

Here is the Error Message from the Ubuntu Software Centre :
```

 Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Details :

The following packages have unmet dependencies:


update-manager: Depends: update-manager-core (= 1:0.180) but 1:0.186.2 is to be installed




```

Please help further.
Thanks !

---

### Post by oldos2er on 2013-10-22
Can you post all the output from ```
sudo apt-get update
```

---

### Post by AmitSinha on 2013-10-22
> **oldos2er said:**
> Can you post all the output from ```
sudo apt-get update
```


Here is the Output for ```

``` :

```
 

sudoamit@amit-desktop:~$ sudo apt-get update
[sudo] password for amit: 
Get:1 http://extras.ubuntu.com raring Release.gpg [72 B]               
Hit http://singo.ub.ac.id raring Release.gpg                           
Hit http://extras.ubuntu.com raring Release    
Hit http://singo.ub.ac.id raring-updates Release.gpg                     
Hit http://singo.ub.ac.id raring-backports Release.gpg                   
Hit http://extras.ubuntu.com raring/main i386 Packages                  
Hit http://singo.ub.ac.id raring-security Release.gpg                   
Hit http://singo.ub.ac.id raring-proposed Release.gpg                   
Hit http://singo.ub.ac.id raring Release                                
Hit http://singo.ub.ac.id raring-updates Release                               
Hit http://singo.ub.ac.id raring-backports Release                             
Hit http://singo.ub.ac.id raring-security Release                              
Ign http://extras.ubuntu.com raring/main Translation-en_IN                     
Hit http://singo.ub.ac.id raring-proposed Release                              
Ign http://extras.ubuntu.com raring/main Translation-en
Hit http://singo.ub.ac.id raring/main i386 Packages                      
Hit http://singo.ub.ac.id raring/restricted i386 Packages                
Hit http://singo.ub.ac.id raring/universe i386 Packages                  
Hit http://singo.ub.ac.id raring/multiverse i386 Packages
Hit http://singo.ub.ac.id raring/main Translation-en
Hit http://singo.ub.ac.id raring/multiverse Translation-en
Hit http://singo.ub.ac.id raring/restricted Translation-en                     
Hit http://singo.ub.ac.id raring/universe Translation-en                       
Hit http://singo.ub.ac.id raring-updates/main i386 Packages                    
Hit http://singo.ub.ac.id raring-updates/restricted i386 Packages              
Hit http://singo.ub.ac.id raring-updates/universe i386 Packages                
Hit http://singo.ub.ac.id raring-updates/multiverse i386 Packages              
Hit http://singo.ub.ac.id raring-updates/main Translation-en                   
Hit http://singo.ub.ac.id raring-updates/multiverse Translation-en             
Hit http://singo.ub.ac.id raring-updates/restricted Translation-en             
Hit http://singo.ub.ac.id raring-updates/universe Translation-en               
Hit http://singo.ub.ac.id raring-backports/main i386 Packages                  
Hit http://singo.ub.ac.id raring-backports/restricted i386 Packages            
Hit http://singo.ub.ac.id raring-backports/universe i386 Packages              
Hit http://singo.ub.ac.id raring-backports/multiverse i386 Packages
Hit http://singo.ub.ac.id raring-backports/main Translation-en
Hit http://singo.ub.ac.id raring-backports/multiverse Translation-en
Hit http://singo.ub.ac.id raring-backports/restricted Translation-en
Hit http://singo.ub.ac.id raring-backports/universe Translation-en
Hit http://singo.ub.ac.id raring-security/main i386 Packages
Hit http://singo.ub.ac.id raring-security/restricted i386 Packages
Hit http://singo.ub.ac.id raring-security/universe i386 Packages
Hit http://singo.ub.ac.id raring-security/multiverse i386 Packages
Hit http://singo.ub.ac.id raring-security/main Translation-en
Hit http://singo.ub.ac.id raring-security/multiverse Translation-en
Hit http://singo.ub.ac.id raring-security/restricted Translation-en
Hit http://singo.ub.ac.id raring-security/universe Translation-en
Hit http://singo.ub.ac.id raring-proposed/restricted i386 Packages
Hit http://singo.ub.ac.id raring-proposed/main i386 Packages
Hit http://singo.ub.ac.id raring-proposed/multiverse i386 Packages
Hit http://singo.ub.ac.id raring-proposed/universe i386 Packages
Hit http://singo.ub.ac.id raring-proposed/main Translation-en
Hit http://singo.ub.ac.id raring-proposed/multiverse Translation-en
Hit http://singo.ub.ac.id raring-proposed/restricted Translation-en
Hit http://singo.ub.ac.id raring-proposed/universe Translation-en
Ign http://singo.ub.ac.id raring/main Translation-en_IN
Ign http://singo.ub.ac.id raring/multiverse Translation-en_IN
Ign http://singo.ub.ac.id raring/restricted Translation-en_IN
Ign http://singo.ub.ac.id raring/universe Translation-en_IN
Ign http://singo.ub.ac.id raring-updates/main Translation-en_IN
Ign http://singo.ub.ac.id raring-updates/multiverse Translation-en_IN
Ign http://singo.ub.ac.id raring-updates/restricted Translation-en_IN
Ign http://singo.ub.ac.id raring-updates/universe Translation-en_IN
Ign http://singo.ub.ac.id raring-backports/main Translation-en_IN
Ign http://singo.ub.ac.id raring-backports/multiverse Translation-en_IN
Ign http://singo.ub.ac.id raring-backports/restricted Translation-en_IN
Ign http://singo.ub.ac.id raring-backports/universe Translation-en_IN
Ign http://singo.ub.ac.id raring-security/main Translation-en_IN
Ign http://singo.ub.ac.id raring-security/multiverse Translation-en_IN
Ign http://singo.ub.ac.id raring-security/restricted Translation-en_IN
Ign http://singo.ub.ac.id raring-security/universe Translation-en_IN
Ign http://singo.ub.ac.id raring-proposed/main Translation-en_IN
Ign http://singo.ub.ac.id raring-proposed/multiverse Translation-en_IN
Ign http://singo.ub.ac.id raring-proposed/restricted Translation-en_IN
Ign http://singo.ub.ac.id raring-proposed/universe Translation-en_IN
Fetched 72 B in 1min 14s (0 B/s)
Reading package lists... Done
amit@amit-desktop:~$  

```

Thanks !

---

### Post by oldos2er on 2013-10-22
Have you tried changing to the main server like I suggested in post #15?

Also try ```
sudo apt-get clean

sudo apt-get autoclean

sudo apt-get autoremove
```

---

### Post by AmitSinha on 2013-10-23
:-(

---

### Post by AmitSinha on 2013-10-23
> **AmitSinha said:**
> :-(
I ran the commands :

```
 

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove


```


Still not able to install any 'Software Updater" from the Software Center.Here is the O/P after running :

```
 
/home/amit > sudo apt-get clean
/home/amit > sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
/home/amit > sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

Please help me !
:-(

Thanks..

---

### Post by AmitSinha on 2013-10-23
> **AmitSinha said:**
> I ran the commands :

```
 

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove


```


Still not able to install any 'Software Updater" from the Software Center.Here is the O/P after running :

```
 
/home/amit > sudo apt-get clean
/home/amit > sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
/home/amit > sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

Please help me !
:-(

Thanks..


I tried to change to the Main Server,from the Edit Menu in the Software Center , but the Option is disabled.Please note this similar problem here :
[http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies)

Now,as per the solution provided, I tried to locate ```
 [FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace]software-properties-gtk 
``` , but am not able to. Seems it is not there in my system.Can it be the reason ? If yes,how do I install in ?
[/FONT]
Also,I am getting a time-out error(highlighted below in bold) when connecting to the Software Download server(which in my case is not from the main server).

```


amit@amit-desktop:~$ sudo apt-get -f install software-properties-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  software-properties-gtk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 42.2 kB of archives.
After this operation, 369 kB of additional disk space will be used.
0% [Connecting to singo.ub.ac.id (175.45.184.39)]y
**Err http://singo.ub.ac.id/ubuntu/ raring/main software-properties-gtk all 0.92.13**
**  Could not connect to singo.ub.ac.id:80 (175.45.184.39), connection timed out**
Failed to fetch http://singo.ub.ac.id/ubuntu/pool/main/s/software-properties/software-properties-gtk_0.92.13_all.deb  Could not connect to singo.ub.ac.id:80 (175.45.184.39), connection timed out
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```

Thanks !

---

### Post by newb85 on 2013-10-23
You should be still be able to edit your /etc/apt/sources.list file.  Replace all the instances of "http://singo.ub.ac.id/ubuntu/" with "http://archive.ubuntu.com/ubuntu".  Then run 
```
sudo apt-get update
```
again.

---

### Post by AmitSinha on 2013-10-24
> **newb85 said:**
> You should be still be able to edit your /etc/apt/sources.list file.  Replace all the instances of "http://singo.ub.ac.id/ubuntu/" with "http://archive.ubuntu.com/ubuntu".  Then run 
```
sudo apt-get update
```
again.



It worked ! Thanks a lot...
Ubuntu Community rocks :-)

---

