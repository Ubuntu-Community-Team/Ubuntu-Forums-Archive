---
title: "How to fix broken packages?"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by viladkarab on 2008-10-31
I am new to linux. I started upgrade to 8.10, but by mistake I shut offed my laptop in between. Now when I start Update Manager, I get a message regarding fixing of broken packages / files. How to do this? Can I revert back to my previous system settings / condition of 8.04? Or I have to fresh re-install 8.04?

---

### Post by ciscosurfer on 2008-10-31
Go to System > Administration > Synaptic Package Manager and click Edit > Fix Broken Packages.

or in a terminal (Applications > Accessories > Terminal)```
sudo apt-get -f install
```

---

### Post by Sef on 2008-10-31
> Go to System > Administration > Synaptic Package Manager and click Edit > Fix Broken Packages.


That should work.  If it does not, then open the Terminal (Applications > Accessories > Terminal) and paste or type in this command:

```
sudo apt-get update && sudo apt-get upgrade
```

Paste any error messages here.

---

### Post by viladkarab on 2008-10-31
I did that, but no use. I am getting messages as below: - 

When I log on, after inputting my username and password, before proceeding, I get following: - 

   User's $Home/.dmrc file is being ignored. This prevents default session and language from being saved. Should be owned by user and have 644 permissions. User's $Home directory must be owned by user and not writable by other users. 

After I OK this, system proceeds further. 

When I start Updat Manager, before proceeding further, I get following: - 

Not all updates can be installed. 
Run a partial upgrade,to install as many updates as possible. 
This can be caused by: 
*A previous upgrade which didn't complete. 
*Problems with some of the installed software.
*Unofficial software packages not provided by Ubuntu.
*Normal changes of a pre-release version of Ubuntu. 

In my case, this problem could be from first and last bullets. "A previous upgrade...." and "Normal changes...."

Also,when I proceed further I get a message: 

"Could not apply changes.Fix broken packages first."


Also, when I try to load Software Sources, it does not start. 

Please help me to restore my system to original state.

---

### Post by Crafty Kisses on 2008-11-01
Try running the following commands:
```

sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update

```

---

### Post by Jeff Seager on 2008-11-01
My experience isn't very extensive, but I do know that the Synaptic Package Manager isn't always the best solution. Did you try the command line "apt-get" solution described above? It's a very good suggestion, and you should try that before seeking to restore everything to the way it was (which might not be possible at this point, in part because of the unfortunate mid-upgrade shutdown).

If you're more comfortable with a GUI than a command line, try opening a Terminal screen (Applications > Accessories > Terminal) and typing this:

sudo aptitude [Enter or Return key]
[type your password] [Enter or Return key]

Aptitude will start, and after it stops churning ...

Under the View menu, select Audit Recommendations. Wait. Accept the audit recommendations, and that should fix it.

Ubuntu is well worth enduring a little trouble like this! Don't give up!

---

### Post by RamboGT on 2010-04-15
> **Crafty Kisses said:**
> Try running the following commands:
```

sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update

```

Tried this, and here is the errors:

dpkg: dependency problems prevent configuration of lame:
 lame depends on libmp3lame0; however:
  Package libmp3lame0 is not installed.
dpkg: error processing lame (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lame

Here is how I tried to fix this:

sudo aptitude install libmp3lame0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  libmp3lame0 
The following packages will be REMOVED:
  akonadi-server{u} cdrdao{u} dkms{u} fakeroot{u} freepats{u} k3b-data{u} 
  kdebase-workspace-bin{u} kdebase-workspace-data{u} 
  kdebase-workspace-kgreet-plugins{u} kdebase-workspace-libs4+5{u} 
  kdepim-runtime{u} kdepim-runtime-data{u} kdepim-runtime-libs4{u} 
  libao2{u} libk3b6{u} libkcddb4{u} libmagick++2{u} libmikmod2{u} 
  libpolkit-dbus2{u} libpolkit-grant2{u} libpolkit-qt0{u} libpolkit2{u} 
  libsdl-mixer1.2{u} libsdl-net1.2{u} libsmpeg0{u} 
  libstrigiqtdbusclient0{u} linux-headers-2.6.31-14{u} 
  mysql-server-core-5.1{u} nvidia-185-kernel-source{u} 
  nvidia-185-libvdpau{u} patch{u} plasma-dataengines-workspace{u} 
  plasma-widgets-workspace{u} policykit{u} prboom{u} python-kde4{u} 
  timidity{u} timidity-daemon{u} 
The following partially installed packages will be configured:
  lame 
0 packages upgraded, 1 newly installed, 38 to remove and 1 not upgraded.
Need to get 251kB of archives. After unpacking 231MB will be freed.

Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse libmp3lame0 3.98.2+debian-0ubuntu2 [251kB]
Fetched 251kB in 1s (194kB/s)      
(Reading database ... 154494 files and directories currently installed.)
Unpacking libmp3lame0 (from .../libmp3lame0_3.98.2+debian-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmp3lame0_3.98.2+debian-0ubuntu2_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libmp3lame.so.0.0.0', which is also in package liblame0 0:3.96.1-1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmp3lame0_3.98.2+debian-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of lame:
 lame depends on libmp3lame0; however:
  Package libmp3lame0 is not installed.
dpkg: error processing lame (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lame
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Any ideas?

Thanks.

---

### Post by DeanoCYM on 2010-04-15
Maybe try:
```
 sudo dpkg --configure -a --force-all 
```
I had a similar problem a long time ago after a dist-upgrade and that fixed it if I remember correctly.

Rhys

---

### Post by Mohsen_cia on 2011-03-21
> **ciscosurfer said:**
> Go to System > Administration > Synaptic Package Manager and click Edit > Fix Broken Packages.

or in a terminal (Applications > Accessories > Terminal)```
sudo apt-get -f install
```


Hi,

I just wanna thank you,
It works brilliant for me!!

Actually I had clear Ubuntu 10.10 installed,
When I tried to install desktop4shared-1.2_1-all.deb everything messed up and I got errors when i tried to install anything in Synaptic. It had 21 dependencies broken !!

And when I click on fix errors it come up with an error in half-way!!

but your. works great ;)

---

### Post by IMayNeed on 2011-07-01
I hope I am typing in a right forum, if not, forgive me.

Mint 9 update is telling me the same thing, fix broken packages first,

but when I try to fix the packages from Package Manager, I don't know which packages are broken.
And from the terminal, I am receiving errors such as posted below

How can I know which packages are broken?
And how can I fix them?
Thanks!


Compiling /usr/share/xemacs21/site-lisp/anjsp/anjsp.el...
While compiling toplevel forms in file /usr/share/xemacs21/site-lisp/anjsp/anjsp.el:
  !! Wrong number of arguments ((require 3))
>>Error occurred processing anjsp.el: 
Wrong number of arguments: require, 3


Done
emacs-install: /usr/lib/emacsen-common/packages/install/anjsp xemacs21 emacs-snapshot emacs22 emacs23 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 31.
dpkg: error processing xemacs21-nomule (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 xemacs21-nomule
E: Sub-process /usr/bin/dpkg returned an error code (1)



Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
  404  Not Found
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Fetched 32.6kB in 2s (14.3kB/s)
W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8
W: Failed to fetch [http://ppa.launchpad.net/calumlind/deluge/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/calumlind/deluge/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Compiling /usr/share/xemacs21/site-lisp/anjsp/anjsp.el...
While compiling toplevel forms in file /usr/share/xemacs21/site-lisp/anjsp/anjsp.el:
  !! Wrong number of arguments ((require 3))
>>Error occurred processing anjsp.el: 
Wrong number of arguments: require, 3


Done
emacs-install: /usr/lib/emacsen-common/packages/install/anjsp xemacs21 emacs-snapshot emacs22 emacs23 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 31.
dpkg: error processing xemacs21-nomule (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 xemacs21-nomule


Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages          
  404  Not Found
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Fetched 32.6kB in 2s (15.9kB/s)
W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8
W: Failed to fetch [http://ppa.launchpad.net/calumlind/deluge/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/calumlind/deluge/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


Compiling /usr/share/xemacs21/site-lisp/anjsp/anjsp.el...
While compiling toplevel forms in file /usr/share/xemacs21/site-lisp/anjsp/anjsp.el:
  !! Wrong number of arguments ((require 3))
>>Error occurred processing anjsp.el: 
Wrong number of arguments: require, 3


Done
emacs-install: /usr/lib/emacsen-common/packages/install/anjsp xemacs21 emacs-snapshot emacs22 emacs23 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 31.
dpkg: error processing xemacs21-nomule (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 xemacs21-nomule

---

### Post by srisailamg on 2012-01-09
hi 

my suggestion re-install ur ubuntu using USB pendrive or cd etc and never choose to update ubuntu using update manager.

i tried this and nw my ubuntu working fine.


try to backup ur files before reinstall.

---

### Post by oldos2er on 2012-01-09
Closed, necromancy.

---

