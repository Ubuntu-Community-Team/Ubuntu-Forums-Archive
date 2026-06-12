---
title: "Unmet Dependencies Problem"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by andydovey on 2014-05-01
Hi, I installed 14.04 after using 12.04. I was very impressed and all went well for such a new version.
 I wanted to try out Google Drive as an alternative to Ubuntu 1. I've been unable to install Grive Tools.
 I used:  
 sudo add-apt-repository ppa:thefanclub/grive-tools
 sudo apt-get update
 sudo apt-get install grive-tools
 It went ok and Grive, and Grive Tools appeared in Synaptic Package Manager, however, when I try to install them, I get the following:
 [COLOR=#000000]“The following packages have unmet dependencies:[/COLOR]
 

 [COLOR=#000000]grive-tools: Depends: libyajl2 (>= 2) but 2.0.4-4 is to be installed[/COLOR]
 [COLOR=#000000]             Depends: libyajl-dev (>= 2) but 2.0.4-4 is to be installed”[/COLOR]
 [COLOR=#000000]I've uninstalled everything including the ppa and tried again, I've installed the latest updates, I've tried:[/COLOR]
 [COLOR=#000000] “sudo apt-get remove grive-tools[/COLOR]
 [COLOR=#000000]sudo apt-get clean[/COLOR]
 [COLOR=#000000]sudo apt-get autoclean”, then re installed.[/COLOR]
 [COLOR=#000000]I've come to the conclusion that I'd better stop tinkering before I cause even more problems.[/COLOR]
 [COLOR=#000000]What should I do to fix the unmet dependencies and install Grive Tools?
Thanks
Andy
[/COLOR]

---

### Post by su:bhatta on 2014-05-01
> **andydovey said:**
> 
 sudo apt-get install grive-tools
 It went ok and Grive, and Grive Tools appeared in Synaptic Package Manager, however, when I try to install them, I get the following:
 [COLOR=#000000]&#8220;The following packages have unmet dependencies[/COLOR][COLOR=#000000]
[/COLOR]

After you did 
> sudo apt-get install grive-tools

you dont have to install Grive again from Synaptic, it has already been installed.
Follow the instructions on [Fanclub]("http://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools") website. 

Once Grive-tools is installed just open Grive setup and follow instructions.

I just installed Grive, no problems.

---

### Post by andydovey on 2014-05-02
Hi Bhatta, thanks for that! I used the fanclub website for the (attempted) install, so I searched the dash when I first tried to install grive. It's not there, the only places I can find it are Synaptic and the Software Center. What am I doing wrong?

---

### Post by ranger1021994 on 2014-05-02
Try this:
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```

I guess you have 64bit Ubuntu
Please take a look at this site
[http://www.thefanclub.co.za/node/151](http://www.thefanclub.co.za/node/151)

You need to manually install libyajl and libjson

---

### Post by su:bhatta on 2014-05-02
Hi,
Did you upgrade from 12.04 to 14.04.
 I am using Ubuntu 14.04 64bit and did not face any problems in installing it following the Fanclub instructions.

Try and see if ranger1021994's instruction page gives any clues.

---

### Post by andydovey on 2014-05-02
Hi, thanks very much for all the help, very much appreciated.
I've tried everything, uninstalled and reinstalled, installed libyajl and libjson, but it keeps telling me that I have Broken Packages and Unmet Dependencies.
No one else seems to have this problem so I think it must be something I've done, although I haven't really done very much apart from install all the usual things.
I did a fresh install, I'm using 32 bit 14.04.
Someone suggested that I re install the Desktop, would that help?
Thanks again.
Andy

Everything else that I installed went smoothly

---

### Post by ian-weisser on 2014-05-03
It seems rather silly to reinstall the entire desktop to fix a simple little package conflict.

Please try **sudo apt-get install -f**
If there is an error, please show us the _complete_ output. Use [code] tags.

This kind of conflict pops up with PPAs. One reason I'm not a fan of PPAs for general use.

---

### Post by andydovey on 2014-05-03
Hi Ian, thanks for your help. This is the entirety of what I got:
andy@andy-eM250:~$ sudo apt-get install -f
[sudo] password for andy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apparmor-easyprof at cmake cmake-data dctrl-tools dh-apparmor
  distro-info-data dput libboost-filesystem1.54.0
  libboost-program-options1.54.0 libboost-test1.54.0 libcommon-sense-perl
  libdistro-info-perl liberror-perl libexpat1-dev libexporter-lite-perl
  libgcrypt11-dev libgpg-error-dev libio-stringy-perl libjson-c-dev
  libjson-perl libjson-xs-perl libjson0-dev libmail-sendmail-perl
  libparse-debcontrol-perl libsys-hostname-long-perl libtie-ixhash-perl
  libyajl-dev po-debconf python3-magic
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
andy@andy-eM250:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
andy@andy-eM250:~$ 
I am working from Root. What should I do?

---

### Post by ian-weisser on 2014-05-03
> **andydovey said:**
> andy@andy-eM250:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

The root prompt is usually #, not $.
Looks to me like you were not working from root, and merely forgot to use sudo.

---

### Post by andydovey on 2014-05-04
Hi Ian, you're absolutely right, I added sudo and ran it again, some things were deleted, no errors showed. What do I need to do now?

---

### Post by Ubi_one_2014 on 2014-05-04
> **andydovey said:**
> Hi Ian, thanks for your help. This is the entirety of what I got:
andy@andy-eM250:~$ sudo apt-get install -f
[sudo] password for andy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apparmor-easyprof at cmake cmake-data dctrl-tools dh-apparmor
  distro-info-data dput libboost-filesystem1.54.0
  libboost-program-options1.54.0 libboost-test1.54.0 libcommon-sense-perl
  libdistro-info-perl liberror-perl libexpat1-dev libexporter-lite-perl
  libgcrypt11-dev libgpg-error-dev libio-stringy-perl libjson-c-dev
  libjson-perl libjson-xs-perl libjson0-dev libmail-sendmail-perl
  libparse-debcontrol-perl libsys-hostname-long-perl libtie-ixhash-perl
  libyajl-dev po-debconf python3-magic
Use 'apt-get autoremove' to remove them. **<----**
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
andy@andy-eM250:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
andy@andy-eM250:~$ 
I am working from Root. What should I do?

pls read what i point to

---

### Post by andydovey on 2014-05-04
Hi Ubi, thanks for your help. I did that (with sudo in front as pointed out by Ian). It deleted some things and gave no errors.

---

### Post by Ubi_one_2014 on 2014-05-04
solved?

---

### Post by andydovey on 2014-05-04
Hi Ubi, thanks again for your time and help.
No, I tried again with this result:
Reading package lists... Done
andy@andy-eM250:~$ sudo apt-get install grive-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 grive-tools : Depends: binutils-dev but it is not going to be installed
               Depends: libcurl4-openssl-dev but it is not going to be installed
               Depends: grive (>= 0.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
Pretty much the same as before, any advice as to what to do?
Thanks again
Andy

---

### Post by Ubi_one_2014 on 2014-05-04
apt-get -f install

and post the complete output here, pls

---

### Post by Ubi_one_2014 on 2014-05-04
i tried the same as you, based on this:
[http://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools](http://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools)

sudo apt-get install grive-tools gets me:

```
$ sudo apt-get install grive-tools
The following extra packages will be installed:
  expect grive libappindicator1 libboost-filesystem-dev libboost-filesystem1.54-dev libboost-program-options-dev libboost-program-options1.54-dev libboost-system1.54-dev libboost-test-dev libboost-test1.54-dev
  libboost-test1.54.0 libboost1.54-dev libcurl4-openssl-dev libindicator7 libjson-c-dev libjson0-dev libnotify-bin libyajl-dev
Recommended packages:
  libboost1.54-doc libboost-atomic1.54-dev libboost-chrono1.54-dev libboost-context1.54-dev libboost-coroutine.54-dev libboost-date-time1.54-dev libboost-exception1.54-dev libboost-graph1.54-dev
  libboost-graph-parallel1.54-dev libboost-iostreams1.54-dev libboost-locale1.54-dev libboost-log.54-dev libboost-math1.54-dev libboost-mpi1.54-dev libboost-mpi-python1.54-dev libboost-python1.54-dev libboost-random1.54-dev
  libboost-regex1.54-dev libboost-serialization1.54-dev libboost-signals1.54-dev libboost-thread1.54-dev libboost-timer1.54-dev libboost-wave1.54-dev libboost1.54-tools-dev libmpfrc++-dev libntl-dev libcurl4-doc
  libcurl3-dbg
The following packages will be REMOVED:
  libcurl4-gnutls-dev
The following NEW packages will be installed:
  expect grive grive-tools libappindicator1 libboost-filesystem-dev libboost-filesystem1.54-dev libboost-program-options-dev libboost-program-options1.54-dev libboost-system1.54-dev libboost-test-dev libboost-test1.54-dev
  libboost-test1.54.0 libboost1.54-dev libcurl4-openssl-dev libindicator7 libjson-c-dev libjson0-dev libnotify-bin libyajl-dev
105 MB of additional disk space will be used.
Continue? [J/n] 


```
i assume your sources.list needs attention

---

### Post by ian-weisser on 2014-05-04
> **andydovey said:**
> The following packages have unmet dependencies.
 grive-tools : Depends: binutils-dev but it is not going to be installed
               Depends: libcurl4-openssl-dev but it is not going to be installed
               Depends: grive (>= 0.3) but it is not going to be installed

You have two packages that *conflict* with the PPA package requirements: binutils-dev and libcurl-openssl-dev.
You can see what applications rely upon those conflicting packages with
```
sudo apt-get remove **--simulate** binutils-dev libcurl4-openssl-dev
```
And you can see the sources of those conflicting packages with:
```
apt-cache policy binutils-dev libcurl4-openssl-dev
```
Please show us the output of both commands.

---

### Post by andydovey on 2014-05-05
Hi, thanks again for all the time you're spending on this.

The results of those commands were:

andy@andy-eM250:~$ sudo apt-get remove --simulate binutils-dev libcurl-openssl-dev
[sudo] password for andy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libcurl-openssl-dev
andy@andy-eM250:~$ sudo apt-cache binutils-dev libcurl-openssl-dev policy
E: Invalid operation binutils-dev
andy@andy-eM250:~$ 

Andy

---

### Post by ian-weisser on 2014-05-05
Very sorry about my typos above (now corrected):

Try:
```
sudo apt-get remove **--simulate** binutils-dev libcurl**4**-openssl-dev
apt-cache **policy** binutils-dev libcurl**4**-openssl-dev
```

Again, these commands will give us more information about where the conflicting packages come from, and how difficult the repair will be.

---

### Post by andydovey on 2014-05-06
Hi Ian, ran the commands with this result:

andy@andy-eM250:~$ sudo apt-get remove --simulate binutils-dev libcurl4-openssl-dev
[sudo] password for andy: 
Sorry, try again.
[sudo] password for andy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'binutils-dev' is not installed, so not removed
Package 'libcurl4-openssl-dev' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
andy@andy-eM250:~$ sudo apt-cache policy binutils-dev libcurl4-openssl-dev
binutils-dev:
  Installed: (none)
  Candidate: 2.24-2ubuntu3
  Version table:
     2.24-2ubuntu3 0
        500 [http://ubuntu.skybroadband.com.ph/ubuntu/](http://ubuntu.skybroadband.com.ph/ubuntu/) trusty/main i386 Packages
libcurl4-openssl-dev:
  Installed: (none)
  Candidate: 7.34.0-1ubuntu1
  Version table:
     7.34.0-1ubuntu1 0
        500 [http://ubuntu.skybroadband.com.ph/ubuntu/](http://ubuntu.skybroadband.com.ph/ubuntu/) trusty/main i386 Packages
andy@andy-eM250:~$ Reading state information... Done
Hope that helps!
Thanks again
Andy

---

### Post by ian-weisser on 2014-05-06
Okay, next let's see the errors from:
```
sudo apt-get install binutils-dev libcurl4-openssl-dev
```

---

### Post by andydovey on 2014-05-06
Hi Ian,

andy@andy-eM250:~$ sudo apt-get install binutils-dev libcurl4-openssl-dev
[sudo] password for andy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 binutils-dev : Depends: binutils (= 2.24-2ubuntu3) but 2.24-5ubuntu3 is to be installed
 libcurl4-openssl-dev : Depends: libcurl3 (= 7.34.0-1ubuntu1) but 7.35.0-1ubuntu2 is to be installed
                        Depends: libkrb5-dev but it is not going to be installed
                        Depends: libldap2-dev but it is not going to be installed
                        Depends: librtmp-dev but it is not going to be installed
                        Depends: libssl-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
Thanks again for your help
Andy

---

### Post by Ubi_one_2014 on 2014-05-06
pls do:
sudo su -[enter]
cd /etc/apt
mv sources.list sources.list.old[enter]
go to:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
and create a new sources.list
pls mark/check all ubuntu branches repo ( not the souces)
as well for Ubuntu update

and choose some repo's you maybe want
kate sources.list[enter]
and post the created sources.list text into kate
save
apt-get -f install[enter]
and post the output

---

### Post by ian-weisser on 2014-05-06
> **andydovey said:**
> 
 binutils-dev : Depends: binutils (= 2.24-2ubuntu3) but 2.24-5ubuntu3 is to be installed
 libcurl4-openssl-dev : Depends: libcurl3 (= 7.34.0-1ubuntu1) but 7.35.0-1ubuntu2 is to be installed
                        

Are you running *sudo apt-get update* before package management operations?
It looks like your dpkg database is simply out of date.

Try:
```
sudo apt-get update
sudo apt-get install binutils-dev libcurl4-openssl-dev
```

---

### Post by andydovey on 2014-05-06
Hi Ian,
I ran the above but it made no difference, below is the end of the print out (I have cut off most of the top).

Ign [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty-backports/universe Translation-en_US
Ign [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty-security/main Translation-en_GB
Ign [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty-security/main Translation-en_US
Ign [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty-security/multiverse Translation-en_GB
Ign [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty-security/multiverse Translation-en_US
Ign [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty-security/restricted Translation-en_GB
Ign [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty-security/restricted Translation-en_US
Ign [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty-security/universe Translation-en_GB
Ign [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty-security/universe Translation-en_US
Reading package lists... Done
andy@andy-eM250:~$ sudo apt-get install binutils-dev libcurl4-openssl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 binutils-dev : Depends: binutils (= 2.24-2ubuntu3) but 2.24-5ubuntu3 is to be installed
 libcurl4-openssl-dev : Depends: libcurl3 (= 7.34.0-1ubuntu1) but 7.35.0-1ubuntu2 is to be installed
                        Depends: libkrb5-dev but it is not going to be installed
                        Depends: libldap2-dev but it is not going to be installed
                        Depends: librtmp-dev but it is not going to be installed
                        Depends: libssl-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
andy@andy-eM250:~$ 
Shall I try Ubi_one's suggestion? I don't want to confuse things even more! 
Thanks very much for your input Ubi_one, I'll definitely have a look at that.
Thanks again for your help
Andy

---

### Post by ian-weisser on 2014-05-06
Next, let's see the output of:
```
apt-cache show grive-tools
```

---

### Post by andydovey on 2014-05-07
Hi Ian,

I ran that with this result:

[sudo] password for andy: 
Package: grive-tools
Priority: optional
Section: utils
Installed-Size: 418
Maintainer: The Fan Club <info@thefanclub.co.za>
Architecture: all
Version: 1.10
Depends: dconf-gsettings-backend | gsettings-backend, libnotify-bin, python, python-pyinotify, gksu, zenity, expect, libjson0-dev (>= 0.10), libyajl2 (>= 2), libyajl-dev (>= 2), libboost-test-dev, binutils-dev, libboost-program-options-dev, libboost-filesystem-dev, libexpat1-dev, libcurl4-openssl-dev, libgcrypt11-dev, grive (>= 0.3), libappindicator1, libappindicator3-1, gir1.2-appindicator3-0.1
Filename: pool/main/g/grive-tools/grive-tools_1.10_all.deb
Size: 114336
MD5sum: fb2015795eb85f2a6ee4a60f8a590900
SHA1: 77297b184c6292e945183a30398a6212dee0518d
SHA256: bf31d1b4a6360e356866899cf08848afa97f48013f9201162b8eafdc361b06a7
Description: Ubuntu Google Drive Client with Grive and Grive Tools
 Ubuntu Google Drive desktop integration made easy.
Description-md5: 83cfd45c23dcccbbb7cc1fe3dcdc9278

Does that mean that it's actually installed?
Thanks again
Andy

---

### Post by ian-weisser on 2014-05-07
No.
It means you have some non-Ubuntu package installed that has a version conflict with grive-tools.
It's not an Ubuntu problem. It's not really a package manager problem.

You, the user, have told your system to do the impossible.
You told your system to install something that requires version A of a package.
Then, later, you told your system to install something else that requires version B of the same package.
The package manager can't install both versions at the same time. One must be uninstalled.
Your system _can_ use multiple versions of the same software...you just can't use the package manager to do that.
That part's not your fault. You had no way to know about the conflict.

The problem seems to be that you installed non-Ubuntu software, and haven't kept track if it.
And now that non-Ubuntu software has broken your package manager.

Here's the critical data so far:
> binutils-dev : Depends: binutils (= 2.24-2ubuntu3) but 2.24-5ubuntu3 is to be installed
 libcurl4-openssl-dev : Depends: libcurl3 (= 7.34.0-1ubuntu1) but 7.35.0-1ubuntu2 is to be installed
Your original non-Ubuntu package requires a specific version of the binutils package (2.24-2ubuntu3) that is now obsolete...but you're stuck there until you uninstall that non-Ubuntu package. Meanwhile, grive-tools requires a later version (2.24-5ubuntu3) of the same package. Same with libcurl3.

This is why I uninstall all PPA software, and disable all PPA repos before upgrading.

Unfortunately, binutils and libcurl3 are dependencies of a _lot_ of applications. The brute-force approach is to uninstall _all_
applications that depend upon them. The non-Ubuntu package will be included in there somewhere. The you can reinstall all the Ubuntu packages. 

If you know which PPAs you installed, this process can go a lot faster and easier. Then it's merely uninstalling that one package, and the system will update the rest.

There are cleverer ways, like grepping the dpkg database to find the offending package, too. Let's try that:
```
 cat /var/lib/dpkg/status | grep -B12 2.24-2ubuntu3
```
The output may be long. Post it all, and please use [code] tags.

---

### Post by andydovey on 2014-05-07
Hi Ian, thanks for that, I thought it would be something I'd done!
I will post here of course but what are [code] tags?
Andy

---

### Post by Ubi_one_2014 on 2014-05-07
between ##

---

### Post by Ubi_one_2014 on 2014-05-07
code /code, but then between []

---

### Post by andydovey on 2014-05-07
Hi, I' think I'm being particularly thick this morning! I still don't understand  what [code] tags are.
Andy

---

### Post by Iowan on 2014-05-07
> **andydovey said:**
> ... but what are ```
 tags?
AndyCode tags format output - for example:

[noparse][code]sudo lshw  -C network
```[/noparse] 
 displays as:
```
sudo lshw  -C network
```

---

### Post by andydovey on 2014-05-07
Hi Iowan,

Thanks for that, I still don't understand what Ian wants me to do. I can run the command that he gave me but I don't understand where the [code] tags go.
Thanks again
Andy

---

### Post by grumblebum2 on 2014-05-07
To add code blocks, you highlight your text with left mouse and then hit the "#"  icon to wrap
in code blocks
```
Paste ouput
```

---

### Post by andydovey on 2014-05-09
Hi Ian,

Thanks again for all your help and apologies for the delay.

Here is a result of running the most recent command, I couldn't get it to work as one command and I couldn't get the second half of it to work at all so I hope it is of some help. I still have no idea what [code] means:

 and control system-wide power management. Any application can access the
 org.freedesktop.UPower service on the system message bus. Some
 operations (such as suspending the system) are restricted using PolicyKit.
Homepage: http://upower.freedesktop.org/
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>

Package: libnfnetlink0
Status: install ok installed
Priority: extra
Section: libs
Installed-Size: 60
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Multi-Arch: same
Source: libnfnetlink
Version: 1.0.1-2
Depends: libc6 (>= 2.4)
Pre-Depends: multiarch-support
Description: Netfilter netlink library
 libnfnetlink is the low-level library for netfilter related
 kernel/userspace communication. It provides a generic messaging
 infrastructure for in-kernel netfilter subsystems (such as
 nfnetlink_log, nfnetlink_queue, nfnetlink_conntrack) and their
 respective users and/or management tools in userspace.
Original-Maintainer: Alexander Wirt <formorer@debian.org>

Package: unity-scope-gourmet
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 78
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 0.1+13.10.20130723-0ubuntu1
Depends: python3, python3-gi, gir1.2-unity-5.0 (>= 7), gir1.2-dee-1.0 (>= 1.2.5), unity-scopes-runner, gir1.2-glib-2.0
Description: Gourmet Recipe Manager scope for Unity
 This package contains the "gourmet" scope which allows Unity
 to search Gourmet Recipe Manager recipes.
Original-Maintainer: Mark Tully <markjtully@gmail.com>
Homepage: https://launchpad.net/unity-scope-gourmet

Package: pptp-linux
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 143
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 1.7.2-7
Depends: libc6 (>= 2.4), ppp (>= 2.4.2), binutils
Conffiles:
 /etc/ppp/options.pptp 4ec8c474813c3d1e52969493c35c652f
Description: Point-to-Point Tunneling Protocol (PPTP) Client
 Client for the proprietary Microsoft Point-to-Point Tunneling
 Protocol, PPTP.  Allows connection to a PPTP based VPN as used
 by employers and some cable and ADSL service providers.
Original-Maintainer: Ola Lundqvist <opal@debian.org>

Package: libslv2-9
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 96
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: slv2
Version: 0.6.6+dfsg1-2
Depends: libc6 (>= 2.4), libraptor2-0 (>= 2.0.6), librdf0 (>= 1.0.15)
Suggests: slv2-jack
Description: library for simple use of LV2 plugins
 SLV2 is a library geared towards music and audio applications
 which makes the use of LV2 plugins as simple as possible.
 LV2 is a standard for plugins and matching host applications,
 mainly targeted at audio processing and generation.
 .
 This package contains the shared library for libslv2.
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Homepage: http://drobilla.net/software/slv2

Package: libcupsimage2
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 159
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Multi-Arch: same
Source: cups
Version: 1.7.2-0ubuntu1
Depends: libc6 (>= 2.4), libcups2 (= 1.7.2-0ubuntu1), libcupsfilters1 (>= 1.0~b1)
Pre-Depends: multiarch-support
Description: Common UNIX Printing System(tm) - Raster image library
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and
 general replacement for lpd and the like.  It supports the Internet
 Printing Protocol (IPP), and has its own filtering driver model for
 handling various document types.
 .
 This package provides the image libraries for handling the CUPS
 raster format.
Homepage: http://www.cups.org
Original-Maintainer: Debian Printing Team <debian-printing@lists.debian.org>

Package: growisofs
Status: install ok installed
Priority: optional
Section: video
Installed-Size: 206
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: dvd+rw-tools
Version: 7.1-10build1
Replaces: dvd+rw-tools (<< 7.1-9)
Depends: libc6 (>= 2.4), libstdc++6 (>= 4.1.1)
Breaks: dvd+rw-tools (<< 7.1-9)
Description: DVD+-RW/R recorder
 growisofs is a general purpose DVD recording program that supports:
 .
  * random-access media (DVD+RW, DVD-RAM, plain files, hard disk partitions)
  * mastering multisession DVD media (DVD+R, DVD-R/-RW, and Blu-ray Disc)
  * first-/single-session recording of arbitrary pre-mastered image
    (formatted as UDF, ISO9660 or any other file system, if formatted at
    all) to all supported DVD media types.
 .
 growisofs is able to either write pre-created ISO images or create them
 on-the-fly (by calling genisoimage).
 .
 This package also contains dvd+rw-format, a utility to format a DVD+RW media.
Original-Maintainer: Optical Media Tools Team <pkg-opt-media-team@lists.alioth.debian.org>
Homepage: http://fy.chalmers.se/~appro/linux/DVD+RW/

Package: usbmuxd
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 125
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 1.0.8-2ubuntu1
Depends: libc6 (>= 2.4), libplist1 (>= 0.16), libusb-1.0-0 (>= 2:1.0.8), libusbmuxd2 (>= 1.0.0), adduser
Description: USB multiplexor daemon for iPhone and iPod Touch devices
 usbmuxd, the USB multiplexor daemon, is in charge of coordinating
 access to iPhone and iPod Touch services over USB. Synchronization and
 management applications for the iPhone and iPod Touch need this daemon
 to communicate with such devices concurrently.
 .
 This package includes udev rules to start the daemon when a supported
 device is plugged in, and stop it when all devices are removed.
Homepage: http://marcansoft.com/blog/iphonelinux/usbmuxd/
Original-Maintainer: gtkpod Maintainers <pkg-gtkpod-devel@lists.alioth.debian.org>

Package: libjson-glib-1.0-common
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 128
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Multi-Arch: foreign
Source: json-glib
Version: 0.16.2-1ubuntu1
Description: GLib JSON manipulation library (common files)
 JSON-GLib is a library for parsing, generating and manipulating JavaScript
 Object Notation (JSON) data streams using the GLib type system. It allows
 manipulating JSON data types with a Document Object Model API. It also
 allows serializing and deserializing simple or complex GObjects to and
 from JSON data types.
 .
 This package contains the translations files.
Homepage: https://wiki.gnome.org/JsonGlib
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>

Package: libwrap0
Status: install ok installed
Priority: standard
Section: libs
Installed-Size: 120
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Multi-Arch: same
Source: tcp-wrappers
Version: 7.6.q-25
Replaces: tcpd (<< 7.6.q-20)
Depends: libc6 (>= 2.11)
Pre-Depends: multiarch-support
Recommends: tcpd
Breaks: tcpd (<< 7.6.q-20)
Description: Wietse Venema's TCP wrappers library
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

Package: cups
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 806
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Multi-Arch: foreign
Version: 1.7.2-0ubuntu1
Replaces: ghostscript-cups (<< 9.02~)
Depends: libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libc6 (>= 2.16), libcups2 (= 1.7.2-0ubuntu1), libcupscgi1 (>= 1.4.2), libcupsimage2 (>= 1.4.0), libcupsmime1 (>= 1.4.0), libcupsppdc1 (>= 1.4.0), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.1.1), libusb-1.0-0 (>= 2:1.0.8), debconf (>= 1.2.9) | debconf-2.0, libc-bin (>= 2.13), cups-core-drivers (>= 1.7.2-0ubuntu1), cups-daemon (>= 1.7.2-0ubuntu1), poppler-utils (>= 0.12), procps, ghostscript (>= 9.02~), lsb-base (>= 3.2-14~), cups-common (>= 1.7.2-0ubuntu1), cups-server-common (>= 1.7.2-0ubuntu1), cups-client (>= 1.7.2-0ubuntu1), cups-ppdc, cups-filters (>= 1.0.24-3~)
Recommends: avahi-daemon, colord, cups-filters (>= 1.0.42) | foomatic-filters (>= 4.0), printer-driver-gutenprint, cups-filters (>= 1.0.36) | ghostscript-cups (>= 9.02~)
Suggests: cups-bsd, foomatic-db-compressed-ppds | foomatic-db, printer-driver-hpcups, hplip, cups-pdf, udev, smbclient
Breaks: foomatic-filters (<< 4.0), ghostscript-cups (<< 9.02~)
Conffiles:
 /etc/cups/snmp.conf 55baa060a50f48f9dbb99c6eb60dc04c
Description: Common UNIX Printing System(tm) - PPD/driver support, web interface
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and
 general replacement for lpd and the like.  It supports the Internet
 Printing Protocol (IPP), and has its own filtering driver model for
 handling various document types.
 .
 This package provides the parts of CUPS which are needed for using printer
 drivers.
Homepage: http://www.cups.org
Original-Maintainer: Debian Printing Team <debian-printing@lists.debian.org>

Package: activity-log-manager
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 709
Maintainer: Siegfried-Angel Gevatter Pujals <rainct@ubuntu.com>
Architecture: i386
Version: 0.9.7-0ubuntu14
Replaces: activity-log-manager-common, activity-log-manager-control-center (<< 0.9.6)
Depends: libc6 (>= 2.3.6-6~), libcairo2 (>= 1.2.4), libgdk-pixbuf2.0-0 (>= 2.22.0), libgee-0.8-2 (>= 0.8.3), libglib2.0-0 (>= 2.37.3), libgnome-control-center1 (>= 1:2.91.2), libgtk-3-0 (>= 3.5.12), libpango-1.0-0 (>= 1.22.0), libpolkit-gobject-1-0 (>= 0.99), libunity-control-center1 (>= 14.04.0), libwhoopsie-preferences0 (>= 0.9), libzeitgeist-2.0-0 (>= 0.9.9), zeitgeist-core (>= 0.8~) | zeitgeist (>= 0.8~), whoopsie-preferences
Breaks: activity-log-manager-control-center (<< 0.9.6)
Conflicts: activity-log-manager-common
Description: blacklist configuration user interface for Zeitgeist
 Zeitgeist is a service which logs the user's activities and events (files
 opened, websites visited, conversations held with other people, etc.) and
 makes the relevant information available to other applications.
 .
 It serves as a comprehensive activity log and also makes it possible to
 determine relationships between items based on usage patterns.
 .
 This package contains Activity Log Manager, a graphical user interface which
 lets you control what gets logged by Zeitgeist. It supports setting up
 blacklists according to several criteria (such as application or file types),
 temporarily stopping all logging as well as deleting recent events.
Homepage: https://launchpad.net/activity-log-manager

Package: libkrb5-3
Status: install ok installed
Priority: standard
Section: libs
Installed-Size: 934
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Multi-Arch: same
Source: krb5
Version: 1.12+dfsg-2ubuntu4
Depends: libc6 (>= 2.16), libcomerr2 (>= 1.34), libk5crypto3 (>= 1.9+dfsg~beta1), libkeyutils1, libkrb5support0 (= 1.12+dfsg-2ubuntu4)
Pre-Depends: multiarch-support
Recommends: krb5-locales
Suggests: krb5-doc, krb5-user
Breaks: libsmbclient (<= 2:3.6.1-2), sssd (<= 1.2.1-4.3)
Conflicts: libkrb53
Description: MIT Kerberos runtime libraries
 Kerberos is a system for authenticating users and services on a network.
 Kerberos is a trusted third-party service.  That means that there is a
 third party (the Kerberos server) that is trusted by all the entities on
 the network (users and services, usually called "principals").
 .
 This is the MIT reference implementation of Kerberos V5.
 .
 This package contains the runtime library for the main Kerberos v5 API
 used by applications and Kerberos clients.
Homepage: http://web.mit.edu/kerberos/
Original-Maintainer: Sam Hartman <hartmans@debian.org>

Package: lsof
Status: install ok installed
Priority: standard
Section: utils
Installed-Size: 455
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 4.86+dfsg-1ubuntu2
Depends: libc6 (>= 2.11)
Description: Utility to list open files
 Lsof is a Unix-specific diagnostic tool.  Its name stands
 for LiSt Open Files, and it does just that.  It lists
 information about any files that are open, by processes
 currently running on the system.
Homepage: http://people.freebsd.org/~abe/
Original-Maintainer: Norbert Tretkowski <nobse@debian.org>

Package: pulseaudio-module-bluetooth
Status: install ok installed
Priority: extra
Section: sound
Installed-Size: 272
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: pulseaudio
Version: 1:4.0-0ubuntu11
Depends: libbluetooth3 (>= 4.91), libc6 (>= 2.15), libcap2 (>= 2.10), libdbus-1-3 (>= 1.0.2), libpulse0, libsbc1, pulseaudio
Conflicts: pulseaudio (<< 0.9.14-2)
Description: Bluetooth module for PulseAudio sound server
 PulseAudio, previously known as Polypaudio, is a sound server for POSIX and
 WIN32 systems. It is a drop in replacement for the ESD sound server with
 much better latency, mixing/re-sampling quality and overall architecture.
 .
 This module enables PulseAudio to work with bluetooth devices, like headset
 or audio gateway.
 .
 The module is called module-bluetooth
Homepage: http://www.pulseaudio.org
Original-Maintainer: Pulseaudio maintenance team <pkg-pulseaudio-devel@lists.alioth.debian.org>

Package: libpython2.7-minimal
Status: install ok installed
Priority: standard
Section: python
Installed-Size: 2497
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Multi-Arch: same
Source: python2.7
Version: 2.7.6-8
Replaces: libpython2.7-stdlib (<< 2.7.4-2), python2.7 (<< 2.7.4-2), python2.7-minimal (<< 2.7.3-10)
Recommends: libpython2.7-stdlib
Breaks: python2.7-minimal (<< 2.7.4~rc1-1~)
Conflicts: binfmt-support (<< 1.1.2)
Conffiles:
 /etc/python2.7/sitecustomize.py d6b276695157bde06a56ba1b2bc53670
Description: Minimal subset of the Python language (version 2.7)
 This package contains some essential modules. It is normally not
 used on it's own, but as a dependency of python2.7-minimal.
Original-Maintainer: Matthias Klose <doko@debian.org>

Package: liblockfile1
Status: install ok installed
Priority: standard
Section: libs
Installed-Size: 56
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Multi-Arch: same
Source: liblockfile
Version: 1.09-6ubuntu1
Depends: libc6 (>= 2.4), liblockfile-bin (>= 1.09-6ubuntu1)
Pre-Depends: multiarch-support
Description: NFS-safe locking library
 Liblockfile is a shared library with NFS-safe locking functions.
Original-Maintainer: Miquel van Smoorenburg <miquels@cistron.nl>

Package: libxau6
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 46
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Multi-Arch: same
Source: libxau
Version: 1:1.0.8-1
Depends: libc6 (>= 2.4)
Pre-Depends: multiarch-support
Description: X11 authorisation library
 This package provides the main interface to the X11 authorisation handling,
 which controls authorisation for X connections, both client-side and
 server-side.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This module can be found at
 git://anongit.freedesktop.org/git/xorg/lib/libXau
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>

Package: libssh2-1
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 255
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Multi-Arch: same
Source: libssh2
Version: 1.4.3-2
Depends: libc6 (>= 2.4), libgcrypt11 (>= 1.5.1), zlib1g (>= 1:1.1.4)
Pre-Depends: multiarch-support
Description: SSH2 client-side library
 libssh2 is a client-side C library implementing the SSH2 protocol.
 It supports regular terminal, SCP and SFTP sessions; port forwarding;
 password, key-based and keyboard-interactive authentication.
 .
 This package contains the runtime library.
Original-Maintainer: Mikhail Gusarov <dottedmag@debian.org>
Homepage: http://libssh2.org/

Package: libio-string-perl
Status: install ok installed
Priority: optional
Section: perl
Installed-Size: 58
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 1.08-3
Depends: perl
Description: Emulate IO::File interface for in-core strings
 The IO::String module provide the IO::File interface for in-core
 strings.  An IO::String object can be attached to a string, and
 will make it possible to use the normal file operations for reading or
 writing data, as well as seeking to various locations of the string.
 The main reason you might want to do this, is if you have some other
 library module that only provide an interface to file handles, and you
 want to keep all the stuff in memory.
 .
 The IO::String module provide an interface compatible with
 IO::File as distributed with IO-1.20, but the following methods
 are not available; new_from_fd, fdopen, format_write,
 format_page_number, format_lines_per_page, format_lines_left,
 format_name, format_top_name.
Original-Maintainer: Debian Perl Group <pkg-perl-maintainers@lists.alioth.debian.org>
Homepage: https://metacpan.org/release/IO-String/

Package: qtdeclarative5-qtfeedback-plugin
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 110
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Multi-Arch: same
Source: qtfeedback-opensource-src
Version: 5.0~git20130529-0ubuntu3
Depends: libqt5feedback5, libc6 (>= 2.4), libqt5core5a (>= 5.0.2), libqt5qml5 (>= 5.0.2), libstdc++6 (>= 4.1.1)
Pre-Depends: multiarch-support
Description: Qt Feedback module - QML plugin
 Qt is a cross-platform C++ application framework. Qt's primary feature
 is its rich set of widgets that provide standard GUI functionality.
 .
 This package contains the Qt Feedback QML plugin for Qt Declarative.
 .
 WARNING: This module is not an official part of Qt 5, but instead a git
 snapshot of an ongoing development. The package is very likely to
 change in a binary incompatible way, and no guarantees are given.
Homepage: http://qt-project.org/

Package: gnome-power-manager
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 364
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 3.8.2-1ubuntu2
Depends: libc6 (>= 2.4), libcairo2 (>= 1.2.4), libglib2.0-0 (>= 2.37.3), libgtk-3-0 (>= 3.4.0), libpango-1.0-0 (>= 1.18.0), libpangocairo-1.0-0 (>= 1.14.0), libupower-glib1 (>= 0.9.1), dconf-gsettings-backend | gsettings-backend, notification-daemon, dbus-x11, upower, gnome-settings-daemon-schemas (>= 3.2)
Suggests: policykit-1
Breaks: gnome-session (<< 2.28)
Description: power management tool for the GNOME desktop
 GNOME Power Manager is a session daemon for the GNOME desktop
 that takes care of system or desktop events related to power, and
 triggers actions accordingly. Its philosophy is to completely hide
 these complex tasks and only show some settings important to the user.
 .
 GNOME power manager displays and manages battery status, power plug
 events, display brightness, CPU, graphics card and hard disk drive
 power saving, and can trigger suspend-to-RAM, hibernate or shutdown
 events, all integrated to other components of the GNOME desktop.
Homepage: http://www.gnome.org/projects/gnome-power-manager/
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>

andy@andy-eM250:~$ sudo grep -B12 2.24-2ubuntu3

---

### Post by ian-weisser on 2014-05-10
> **andydovey said:**
> Here is a result of running the most recent command, I couldn't get it to work as one command and I couldn't get the second half of it to work at all so I hope it is of some help.

Unfortunately, it appears to be of no help that I can see.
You should be able to copy-and-paste the entire command at any shell prompt.
What _exactly_ do you mean by "couldn't get it to work"? Was there some kind of error? No output at all?

I don't see much more we can do without more information from your end. We can't tell you what package you installed that caused the problem without that output.

There are also more intrusive ways to tackle the problem. If you want to get out the sledgehammer, just let us know.

---

### Post by andydovey on 2014-05-11
Hi Ian,
When I paste the entire command, this is the outcome:
andy@andy-eM250:~$ sudo cat /var/lib/dpkg/status | grep -B12 2.24-2ubuntu3
[sudo] password for andy: 
andy@andy-eM250:~$ cat /var/lib/dpkg/status | grep -B12 2.24-2ubuntu3
andy@andy-eM250:~$ 
I tried it with and without sudo, perhaps it will be easier if I re install and try not to do whatever it was again.
Thanks again
Andy

---

### Post by Ubi_one_2014 on 2014-05-11
pls give an update when doing:
apt-get update && apt-get dist-upgrade

copy and paste the complete output here

---

### Post by andydovey on 2014-05-12
Hi Ubi,
Thanks for your help, here is the result of running that command, I think I may be better off re installing!

andy@andy-eM250:~$ sudo apt-get update && apt-get dist-upgrade
[sudo] password for andy: 
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_GB              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_US              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Err [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty InRelease                         
  
Err [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty-updates InRelease
  
Err [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty-backports InRelease
  
Err [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty-security InRelease
  
Err [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty Release.gpg
  Could not resolve 'ubuntu.skybroadband.com.ph'
Err [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty-updates Release.gpg
  Could not resolve 'ubuntu.skybroadband.com.ph'
Err [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty-backports Release.gpg
  Could not resolve 'ubuntu.skybroadband.com.ph'
Err [http://ubuntu.skybroadband.com.ph](http://ubuntu.skybroadband.com.ph) trusty-security Release.gpg
  Could not resolve 'ubuntu.skybroadband.com.ph'
Fetched 72 B in 40s (1 B/s)
Reading package lists... Done
W: Failed to fetch [http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty/InRelease](http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty/InRelease)  

W: Failed to fetch [http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty-updates/InRelease](http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty-updates/InRelease)  

W: Failed to fetch [http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty-backports/InRelease](http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty-backports/InRelease)  

W: Failed to fetch [http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty-security/InRelease](http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty-security/InRelease)  

W: Failed to fetch [http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty/Release.gpg](http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'ubuntu.skybroadband.com.ph'

W: Failed to fetch [http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty-updates/Release.gpg](http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty-updates/Release.gpg)  Could not resolve 'ubuntu.skybroadband.com.ph'

W: Failed to fetch [http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty-backports/Release.gpg](http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty-backports/Release.gpg)  Could not resolve 'ubuntu.skybroadband.com.ph'

W: Failed to fetch [http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty-security/Release.gpg](http://ubuntu.skybroadband.com.ph/ubuntu/dists/trusty-security/Release.gpg)  Could not resolve 'ubuntu.skybroadband.com.ph'

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
andy@andy-eM250:~$

---

### Post by Ubi_one_2014 on 2014-05-14
it's still not clear for me if you are still dealling with the dependecy issues?

---

### Post by andydovey on 2014-05-15
Hi Ubi, thanks for your time. I've no idea if I'm dealing with dependency issues! I still can't get the thing to work. This weekend I'll re install 14.04 and try not to mess up again!
Thanks every one for your time and help, whatever I did to stop Grive from working will have to remain a mystery. I have, as always, learned some stuff about Ubuntu which is as much a hobby as an operating system!
Andy

---

### Post by andydovey on 2014-05-15
As I'm going to re install, I'll mark this as solved.

---

### Post by ian-weisser on 2014-05-15
Generally you don't need to reinstall to solve such trivial issues as a non-Ubuntu package preventing subsequent package manager actions.
And a reinstall won't help if you happen to promptly reinstall the same non-Ubuntu package - the same problem will recur.

It's usually *much* easier and faster to simply identify the troublesome package and remove it.
Considering all the PPA and other Non-Ubuntu repositories that you are trying to update from, and that you don't seem to know what you are installing from them, I'm not surprised you are having problems. I suspect you have the same again sooner or later.

Advice: Do the most basic admin work. Simply write down what Non-Ubuntu software you installed, and when. When the package manager complains, work your way backwards through the list until the package manager works again. The tiniest text file and 10 seconds can save you an hour of reinstalling.

---

