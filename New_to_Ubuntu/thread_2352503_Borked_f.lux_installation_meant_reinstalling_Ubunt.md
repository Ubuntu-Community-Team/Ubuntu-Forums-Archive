---
title: "Borked f.lux installation meant reinstalling Ubuntu - how to prevent happening again?"
date: 2017-02-13
forum: New to Ubuntu
---

### Post by lysander6662 on 2017-02-13
Hi all,

My first post on the forums and I am new to Ubuntu having been meaning to install it for about... nine years. I always held back from installing any Linux distro because Windows was better for gaming. But now that there is more support [and I have a little more time], I was able to do so yesterday.

Anyway, so the first install [16.04] from the flash drive went correctly. Things were fine until I tried to install f.lux. I don't know what I did but I made some changes in the terminal maybe, it didn't work and on rebooting it would freeze and the screen would tear on log-in. I tried rebooting another three times with the same result until I bit the bullet and had to reinstall.

Second reinstall didn't work either, I just had a black screen and blinking cursor on reboot. Third one has worked fine so far. I have three hard drives and I pulled out the SATA leads on the two backup drives so Ubuntu was just installed on the main one with no shadow of doubt! After install I plugged them back in and it's all fine and Ubuntu can see them.

My question is, why would a borked install screw up the OS so much that I had to do a reinstall? Or did I? What can I do in the future when/if this happens again. I am very cautious to install new software now [though Opera/Synaptic were fine, Redshift misbehaved and I uninstalled].

By the way, I'm using a quad core intel 64 bit CPU [Q660 2.4 Ghz], 5GB RAM and HD5870 gfx card. I read that Ubuntu is quite graphically intensive. Are these specs OK? It seems to be holding up all right.

---

### Post by howefield on 2017-02-13
> **lysander6662 said:**
> What can I do in the future when/if this happens again. I am very cautious to install new software now [though Opera/Synaptic were fine, Redshift misbehaved and I uninstalled

Increase your tolerance for fixing something when it "borks" ;)

You should be cautious as to which software you install, or more specifically where it comes from and whether or not it was built for your specific version/distribution, the further away you go from the official repositories the higher the chance of breakage. 

I'd suggest learning how to use Clonezilla, a free imaging program which will take a restorable image of your partition/disk, meaning that if you bork your system you can be up and running again in a few minutes rather than installing from scratch. I'd also suggest putting /home on a separate partition if you haven't already or better still.. a data partition where you store your data. 

> By the way, I'm using a quad core intel 64 bit CPU [Q660 2.4 Ghz], 5GB RAM and HD5870 gfx card. I read that Ubuntu is quite graphically intensive. Are these specs OK?

Seems more than adequate although the graphics card might be a bit suspect in certain conditions, given that it won't support the newer drivers. This might be the reason that redshift/f.lux struggles to work correctly.

---

### Post by lysander6662 on 2017-02-13
Thank you, I haven't partitioned the drive, but I can certainly do so, seeing as I have the space. f.lux came from the official site but I see what you mean, since it's not in Synaptic or the Software repository. I am being a lot more careful now and don't really want to install stuff that isn't on the repositories [though Opera didn't come from there]. 

And yes, you reminded me that I haven't installed the drivers for the gfx card so it's been running without them at the moment. Not really sure how to do it or it the ATI drivers would be in Synaptic. I just haven't read up on it yet.

---

### Post by howefield on 2017-02-13
> **lysander6662 said:**
> Thank you, I haven't partitioned the drive, but I can certainly do so, seeing as I have the space. f.lux came from the official site but I see what you mean, since it's not in Synaptic or the Software repository. I am being a lot more careful now and don't really want to install stuff that isn't on the repositories [though Opera didn't come from there]. 

Yes, of course not all "third party" software will behave badly. 

> And yes, you reminded me that I haven't installed the drivers for the gfx card so it's been running without them at the moment. Not really sure how to do it or it the ATI drivers would be in Synaptic. I just haven't read up on it yet.

The Additional Drivers application will give you any proprietary drivers that are available, you'll probably only find a microcode driver for your processor though. Since 16.04 the proprietary ATI drivers (fglrx) are no longer available - on installation the system will automatically decide whether the AMDGPU driver can be used and if not it will use the default Radeon driver.

---

### Post by lysander6662 on 2017-02-13
> **howefield said:**
> The Additional Drivers application will give you any proprietary drivers that are available, you'll probably only find a microcode driver for your processor though. Since 16.04 the proprietary ATI drivers (fglrx) are no longer available - on installation the system will automatically decide whether the AMDGPU driver can be used and if not it will use the default Radeon driver.

Ah OK, so I install the Additional Drivers application and it runs a check to see what's available can be used. Thank you very much. How big would you say a data partition should be?

---

### Post by howefield on 2017-02-13
> **lysander6662 said:**
> Ah OK, so I install the Additional Drivers application and it runs a check to see what's available can be used.

That's about it except the Additional Drivers application is already installed, you only need to load it up :)

> Thank you very much. How big would you say a data partition should be?

Well, that's personal to you. To give you an example this machine I am on has 4 primary partitions as follows..

One 40GB partition for / which includes /home, one 30GB partition for testing other installations, one Swap partition equal in size to installed RAM and the rest of the disk as a "Data" partition.

The Data partition has my Documents, Downloads, Music, Pictures and Videos folders symlinked to the /home folder on the installation partition. This makes reinstallation easy and allows each of the installs to access the Data partition. You probably don't want less than 20GB devoted to the root install partition.

---

### Post by lysander6662 on 2017-02-13
This is great information. I have about 70GB on my SSD which is my main hard drive. So I should have two partitions? Maybe 40GB/30GB? Do I really need 30GB for testing at this point?

Sorry for the qs but you know how these things go - questions lead to more questions. I take it symlinked means the partition can 'talk' to each other, for wont of a better expression [maybe you know a more technical one!].

---

### Post by howefield on 2017-02-13
> **lysander6662 said:**
> This is great information. I have about 70GB on my SSD which is my main hard drive. So I should have two partitions? Maybe 40GB/30GB? Do I really need 30GB for testing at this point?

I'd probably use a little less than 40GB for the root install if I only had 70GB to play with - you don't ned a second install partition at all, I only gave you my setup as an example. The Data partition doesn't even need to be on the 70GB SSD, it can be on a separate disk altogether. 

> I take it symlinked means the partition can 'talk' to each other, for wont of a better expression [maybe you know a more technical one!].

I delete the default folders (Documents, Downloads, Music, Pictures and Videos) from /home and create symlinks to the folders on the Data partition so that anything saved to /home/$USER/Documents (or any other folder) is actually saved to the symlinked folder on the Data partition. Not sure if it helps but you can see on the attached image that the Documents folder in /home (which has an arrow on the icon indicating a symlink) is actually linked to the Documents folder on the Data partition. 

[ATTACH=CONFIG]273680[/ATTACH] 

The same is true for each of the folders with the arrow on it.

---

### Post by lysander6662 on 2017-02-13
> **howefield said:**
> 


The Additional Drivers application will give you any proprietary drivers that are available, you'll probably only find a microcode driver for your processor though. Since 16.04 the proprietary ATI drivers (fglrx) are no longer available - on installation the system will automatically decide whether the AMDGPU driver can be used and if not it will use the default Radeon driver.

Yes, there's no driver that it comes up with apart from a microcode driver as you said.

I managed to get f.lux installed through following YouTube instructions but it still doesn't work properly. Is there nothing I can do for this/Redshift?

---

### Post by howefield on 2017-02-13
> **lysander6662 said:**
> I managed to get f.lux installed through following YouTube instructions but it still doesn't work properly. Is there nothing I can do for this/Redshift?

Not sure how you installed f.lux but a quick search to the projects github page tells me to use this ppa : [https://launchpad.net/~nathan-renniewaldock/+archive/ubuntu/flux](https://launchpad.net/~nathan-renniewaldock/+archive/ubuntu/flux)

Seems to work well and has builds for all supported version of Ubuntu.

```
sudo add-apt-repository ppa:nathan-renniewaldock/flux
[sudo] password for hugh: 
 GUI for f.lux
https://justgetflux.com/

Bugs/feature requests should be directed to: https://github.com/xflux-gui/xflux-gui
I do not develop this, only provide a PPA.
 More info: https://launchpad.net/~nathan-renniewaldock/+archive/ubuntu/flux
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keybox '/tmp/tmpbmgjm_8r/pubring.gpg' created
gpg: /tmp/tmpbmgjm_8r/trustdb.gpg: trustdb created
gpg: key 4CDB129629A4B41A: public key "Launchpad PPA for Nathan Rennie-Waldock" imported
gpg: Total number processed: 1
gpg:               imported: 1
OK
```
```
sudo apt update
Hit:1 http://archive.canonical.com/ubuntu yakkety InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu yakkety InRelease                                      
Get:3 http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu yakkety InRelease [17.5 kB]      
Get:4 http://gb.archive.ubuntu.com/ubuntu yakkety-updates InRelease [102 kB]                                                            
Get:5 http://security.ubuntu.com/ubuntu yakkety-security InRelease [102 kB]                                                                
Get:6 http://gb.archive.ubuntu.com/ubuntu yakkety-backports InRelease [102 kB]     
Get:7 http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu yakkety/main i386 Packages [540 B]
Get:8 http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu yakkety/main amd64 Packages [540 B]
Get:9 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 Packages [182 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/main i386 Packages [179 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 DEP-11 Metadata [114 kB]           
Get:12 http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu yakkety/main Translation-en [276 B]              
Get:13 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/main DEP-11 64x64 Icons [64.7 kB]                                      
Get:14 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/universe i386 Packages [101 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/universe amd64 Packages [103 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/universe Translation-en [56.0 kB]
Get:17 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/universe amd64 DEP-11 Metadata [95.7 kB]
Get:18 http://security.ubuntu.com/ubuntu yakkety-security/main amd64 DEP-11 Metadata [8,272 B]   
Get:19 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/universe DEP-11 64x64 Icons [118 kB]                      
Get:20 http://gb.archive.ubuntu.com/ubuntu yakkety-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:21 http://security.ubuntu.com/ubuntu yakkety-security/main DEP-11 64x64 Icons [9,967 B] 
Get:22 http://security.ubuntu.com/ubuntu yakkety-security/universe amd64 DEP-11 Metadata [9,736 B]
Fetched 1,370 kB in 1s (1,072 kB/s)                                       
Reading package lists... Done
Building dependency tree       
Reading state information... Done
6 packages can be upgraded. Run 'apt list --upgradable' to see them.
```
```
sudo apt install fluxgui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libglade2-0 python-gconf python-glade2 python-pexpect python-ptyprocess python-xdg
Suggested packages:
  python-gnome2-doc python-gtk2-doc python-pexpect-doc
The following NEW packages will be installed
  fluxgui libglade2-0 python-gconf python-glade2 python-pexpect python-ptyprocess python-xdg
0 to upgrade, 7 to newly install, 0 to remove and 6 not to upgrade.
Need to get 177 kB of archives.
After this operation, 994 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://gb.archive.ubuntu.com/ubuntu yakkety/main amd64 libglade2-0 amd64 1:2.6.4-2 [44.6 kB]
Get:2 http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu yakkety/main amd64 fluxgui all 1.1.9~20170116-gaaeae23-1~yakkety [15.5 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu yakkety/main amd64 python-glade2 amd64 2.24.0-4ubuntu1 [9,078 B]
Get:4 http://gb.archive.ubuntu.com/ubuntu yakkety/universe amd64 python-gconf amd64 2.28.1+dfsg-1.1 [22.3 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu yakkety/universe amd64 python-xdg all 0.25-4 [31.4 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu yakkety/universe amd64 python-ptyprocess all 0.5.1-1 [12.6 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu yakkety/universe amd64 python-pexpect all 4.2.0-1 [41.2 kB]
Fetched 177 kB in 0s (648 kB/s)           
Selecting previously unselected package libglade2-0:amd64.
(Reading database ... 212851 files and directories currently installed.)
Preparing to unpack .../0-libglade2-0_1%3a2.6.4-2_amd64.deb ...
Unpacking libglade2-0:amd64 (1:2.6.4-2) ...
Selecting previously unselected package python-glade2.
Preparing to unpack .../1-python-glade2_2.24.0-4ubuntu1_amd64.deb ...
Unpacking python-glade2 (2.24.0-4ubuntu1) ...
Selecting previously unselected package python-gconf.
Preparing to unpack .../2-python-gconf_2.28.1+dfsg-1.1_amd64.deb ...
Unpacking python-gconf (2.28.1+dfsg-1.1) ...
Selecting previously unselected package python-xdg.
Preparing to unpack .../3-python-xdg_0.25-4_all.deb ...
Unpacking python-xdg (0.25-4) ...
Selecting previously unselected package python-ptyprocess.
Preparing to unpack .../4-python-ptyprocess_0.5.1-1_all.deb ...
Unpacking python-ptyprocess (0.5.1-1) ...
Selecting previously unselected package python-pexpect.
Preparing to unpack .../5-python-pexpect_4.2.0-1_all.deb ...
Unpacking python-pexpect (4.2.0-1) ...
Selecting previously unselected package fluxgui.
Preparing to unpack .../6-fluxgui_1.1.9~20170116-gaaeae23-1~yakkety_all.deb ...
Unpacking fluxgui (1.1.9~20170116-gaaeae23-1~yakkety) ...
Setting up python-gconf (2.28.1+dfsg-1.1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu1) ...
Processing triggers for sgml-base (1.28) ...
Processing triggers for bamfdaemon (0.5.3+16.10.20160929-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up libglade2-0:amd64 (1:2.6.4-2) ...
Setting up python-ptyprocess (0.5.1-1) ...
Setting up python-glade2 (2.24.0-4ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu4) ...
Processing triggers for hicolor-icon-theme (0.15-1) ...
Setting up python-xdg (0.25-4) ...
Setting up python-pexpect (4.2.0-1) ...
Setting up fluxgui (1.1.9~20170116-gaaeae23-1~yakkety) ...

Downloading xflux...
--2017-02-13 18:36:28--  https://justgetflux.com/linux/xflux64.tgz
Resolving justgetflux.com (justgetflux.com)... 216.176.200.22
Connecting to justgetflux.com (justgetflux.com)|216.176.200.22|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 339845 (332K) [application/octet-stream]
Saving to: ‘xflux64.tgz’

xflux64.tgz                        100%[================================================================>] 331.88K   640KB/s    in 0.5s    

2017-02-13 18:36:29 (640 KB/s) - ‘xflux64.tgz’ saved [339845/339845]

Download done.

Adding 'diversion of /usr/bin/xflux to /usr/bin/xflux.distrib by fluxgui'
Processing triggers for libc-bin (2.24-3ubuntu2) ...
```

---

### Post by lysander6662 on 2017-02-13
Yes you are right! That's the one.

OK, so I just restarted the computer [I was about to call it a PC but is 'PC' just a Windows related term?] and it works. Looks great.

So does restarting often help these kind of things for Ubuntu/Linux?

---

### Post by howefield on 2017-02-13
> **lysander6662 said:**
> Yes you are right! That's the one.

Cool :)

> OK, so I just restarted the computer [I was about to call it a PC but is 'PC' just a Window's related term?] and it works. Looks great.

I didn't have to restart but I guess different hardware might have different requirements to these sorts of things.

> So does restarting often help these kind of things for Ubuntu/Linux?

Well, I wouldn't say it was normal to have to restart, but it isn't unknown. I doubt you'll need to resort to a restart too often. Perhaps a logout/log back in would have sufficed.

---

### Post by lysander6662 on 2017-02-13
Thank you very much for all your help. I'm interested to know exactly what I did to cause the crash I did. It was something to do with trying to install xflux64.tgz here

[https://justgetflux.com/linux/xflux64.tgz](https://justgetflux.com/linux/xflux64.tgz)

Anyway, I will be careful to know what I'm doing with these things in the future. I've installed quite a bit of stuff tonight through Synaptic and the terminal, it all seems fine. I think I just have to be careful at this point about doing things with no guidance [which is what I did with the tgz file].

---

### Post by lysander6662 on 2017-02-14
I'm going to mark this as solved. Although I don't really know *how* I caused the problem, I know *what *caused it, and f.lux works now. That's enough for the moment. Thanks for the great advice.

---

