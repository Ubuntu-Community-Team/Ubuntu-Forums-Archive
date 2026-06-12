---
title: "Update Manager: &quot;The package system is broken.&quot;"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by CardioStriptease on 2012-04-01
This is kind of a strange one, I think. I downloaded and installed Linux yesterday, from the LiveUSB. The install went fine, but when I try to run the update manager, I get an error. Like so:

> The package system is broken.
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Details:
[QUOTE]
The following packages have unmet dependencies:

libc6: Depends: libc-bin (= 2.13-20ubuntu5) but 2.13-20ubuntu5.1 is installed
libc6-dev: Depends: libc6 (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5 is installed
           Depends: libc-dev-bin (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5.1 is installed
[/QUOTE]I don't know what a repository is, so I doubt I'm using any third-party ones. The thing that catches my eye, though, is that the above error looks like it's contradicting itself. I don't know if that's normal.

After running that command in Terminal:
> 
god@god-Inspiron-530s:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
god@god-Inspiron-530s:~$ sudo apt-get install -f
[sudo] password for god: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 0 to remove and 396 not upgraded.
1 not fully installed or removed.
Need to get 0 B/3,800 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 153204 files and directories currently installed.)
Preparing to replace libc6 2.13-20ubuntu5 (using .../libc6_2.13-20ubuntu5.1_i386.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.13-20ubuntu5.1_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.13-20ubuntu5.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
god@god-Inspiron-530s:~$ 
I'll post my system specs when I find them, but I've yet to do that. In the meantime, any advice would be appreciated.

---

### Post by ngubk on 2012-04-01
For the first one, a repository, in simple term, is the source where ubuntu download your update. To disable any third party repository, open "Software Source" ( press Super button and type software source if you're using 11.04 or 11.10) 
Untick anything that doesn't have Canonical , CD rom or Ubuntu with it.
After that, close the app, open terminal and run : sudo apt-get update

For the second, it is simply because you are open Software Center or Synaptic Package manager, close them all and run the command again

---

### Post by CardioStriptease on 2012-04-01
I did both of those things, but I'm still getting the same error. What does apt-get install -f do, or what is it supposed to do?

---

### Post by jerrrys on 2012-04-01
> **CardioStriptease said:**
> I did both of those things, but I'm still getting the same error. What does apt-get install -f do, or what is it supposed to do?

install -f attempts to fix broken packages

you should try:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

### Post by CardioStriptease on 2012-04-01
Nope. I ran both commands; same error. The lines:
> 
dpkg: error processing /var/cache/apt/archives/libc6_2.13-20ubuntu5.1_i386.deb (--unpack):
corrupted filesystem tarfile - corrupted package archive

are sticking out at me. Is it possible to get that package from somewhere else? I see that it's possible to install updates from the liveCD; can the same be done with a liveUSB?

---

### Post by jerrrys on 2012-04-01
sudo apt-get clean

sudo apt-get autoremove

sudo apt-get update

any errors?

---

### Post by CardioStriptease on 2012-04-05
I did all of those things. No errors. I tried sudo apt-get install, and I got the same error.

---

### Post by mörgæs on 2012-04-05
> **CardioStriptease said:**
> I downloaded and installed Linux yesterday

If we are dealing with a new system without configuration and user files, why don't you just delete it and reinstall?

---

### Post by CardioStriptease on 2012-04-05
It's an option, I guess; I'm mainly worried about it not being fixed by a simple reinstall.

---

### Post by QIII on 2012-04-05
If you do choose to reinstall (maybe not such a bad idea, but I really don't like the "Nuke 'em from orbit" approach), consider the possibility that either your downloaded .iso or the burn to disk was flawed in some very minor way that did not keep it from being installed.

Did you md5sum the downloaded .iso?  Choose to check disk integrity?

If you encounter the same behavior on the next install, you could download the image again, md5sum, check disk integrity and try with that disk.

---

### Post by benedictbrown on 2012-05-26
> **jerrrys said:**
> sudo apt-get clean

sudo apt-get autoremove

sudo apt-get update

any errors?

I'm trying to upgrade from 11.04 to 11.10 (then 12.04).  The upgrade to 11.10 failed on libc6, leaving my system with a broken package system.  It seems to be the same errors as on this thread.  I can still use most non-gnome applications, although I dare not reboot.

At present I've update my sources.list to point to natty rather than oneiric, just to try and get things back into a usable state.  Even after following the directions in this post, any attempts to install or fix anything, including apt-get autoremove, give the following errors:

> 
% autoremove -f

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 cups : Depends: libgnutls26 (>= 2.9.11-0) but 2.8.6-1ubuntu2.1 is installed
        Depends: ghostscript (>= 9.02~) but 9.01~dfsg-1ubuntu5 is installed
        Depends: cups-common (>= 1.5.0) but 1.4.6-5ubuntu1.4 is installed
        Depends: cups-client (>= 1.5.0-8ubuntu6) but 1.4.6-5ubuntu1.4 is installed
        Recommends: colord but it is not installable
 gtk2-engines-pixbuf : Depends: libgtk2.0-0 (= 2.24.6-0ubuntu5) but 2.24.4-0ubuntu2 is installed
 libc6 : Depends: libc-bin (= 2.13-0ubuntu13.1)
         Breaks: libc6:i386 (!= 2.13-0ubuntu13.1) but 2.13-20ubuntu5.1 is installed
 libc6:i386 : Breaks: libc6 (!= 2.13-20ubuntu5.1) but 2.13-0ubuntu13.1 is installed
 libc6-dev : Depends: libc6 (= 2.13-20ubuntu5.1) but 2.13-0ubuntu13.1 is installed
 libc6-i386 : Depends: libc6 (= 2.13-20ubuntu5.1) but 2.13-0ubuntu13.1 is installed
 libcups2 : Depends: libgnutls26 (>= 2.9.11-0) but 2.8.6-1ubuntu2.1 is installed
 libgail18 : Depends: libgtk2.0-0 (= 2.24.6-0ubuntu5) but 2.24.4-0ubuntu2 is installed
 libgl1-mesa-dev : Depends: libgl1-mesa-glx (= 7.11-0ubuntu3.2) but 7.10.2-0ubuntu2.1 is installed
 libgnutlsxx26 : Depends: libgnutls26 (= 2.10.5-1ubuntu3.1) but 2.8.6-1ubuntu2.1 is installed
 libldap-2.4-2 : Depends: libgnutls26 (>= 2.9.11-0) but 2.8.6-1ubuntu2.1 is installed
 libperl5.12 : Depends: perl-base (= 5.12.4-4) but 5.10.1-17ubuntu4.1 is installed
 libuuid-perl : Depends: perl-base (>= 5.12.3-6ubuntu4) but 5.10.1-17ubuntu4.1 is installed
                Depends: perlapi-5.12.3 but it is not installable
 samba : Depends: samba-common (= 2:3.5.11~dfsg-1ubuntu2.3) but 2:3.5.8~dfsg-1ubuntu2.5 is installed
 winbind : Depends: samba-common (= 2:3.5.11~dfsg-1ubuntu2.3) but 2:3.5.8~dfsg-1ubuntu2.5 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


As far as I can tell, there are no held packages.  Any suggestions would be greatly appreciated.

---

### Post by benedictbrown on 2012-05-26
As a followup to my previous post, I've switched my source back to oneiric, commented disabled the security updates (to see if that resulted in an earlier libc6 package), deleted all my apt caches, run apt-get upgrade.  At that point I get back to my original error when I run apt-get -f install:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  menu-xdg libprocesscore4b elementary-icon-theme libkwineffects1a libppl7 libqtscript4-network libsolidcontrolifaces4a libqtscript4-gui leafpad libunity-misc0 libtag-extras1 libqtscript4-sql poppler-data libqtscript4-xml
  libmenu-cache1 arj xmms2-plugin-id3v2 libppl-c2 amarok-utils giblib1 amarok-common xmms2-plugin-alsa libcloog-ppl0 libxmmsclient6 kinfocenter xmms2-core gpicview python-xklavier libboost-serialization1.42.0 libgmpxx4ldbl
  xmms2-plugin-vorbis libxmmsclient-glib1 xmms2-plugin-mad libqtscript4-uitools liblastfm0 scrot libimlib2 libqtscript4-core python-wsgi-intercept xarchiver
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cups-bsd cups-client cups-common ghostscript ghostscript-x libalgorithm-diff-xs-perl libapparmor-perl libapparmor1 libapt-pkg-perl libapt-pkg4.11 libasync-interrupt-perl libc6 libcairo-perl libdigest-sha1-perl
  libevent-perl libgl1-mesa-glx libglib-perl libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl libgnutls-dev libgnutls26 libgs9 libgtk2-perl libgtk2.0-0 libhtml-parser-perl libio-pty-perl liblocale-gettext-perl
  libnet-dbus-perl libnet-dns-perl libnet-libidn-perl libnet-ssleay-perl libpam-smbpass libpango-perl libpurple0 libsnmp-base libsnmp15 libsub-name-perl libterm-readkey-perl libtext-charwidth-perl libtext-iconv-perl
  libxml-parser-perl libyaml-syck-perl nvidia-current perl perl-base perl-modules pidgin pidgin-data samba-common smbclient
Suggested packages:
  xpp glibc-doc libfont-freetype-perl gnutls-doc gnutls-bin guile-gnutls libgtk2-perl-doc libdata-dump-perl libio-socket-inet6-perl snmp-mibs-downloader libterm-readline-gnu-perl libterm-readline-perl-perl cifs-utils
Recommended packages:
  libswitch-perl libpod-plainer-perl libclass-isa-perl
The following packages will be REMOVED:
  libperl5.10
The following NEW packages will be installed:
  libapt-pkg4.11
The following packages will be upgraded:
  cups-bsd cups-client cups-common ghostscript ghostscript-x libalgorithm-diff-xs-perl libapparmor-perl libapparmor1 libapt-pkg-perl libasync-interrupt-perl libc6 libcairo-perl libdigest-sha1-perl libevent-perl
  libgl1-mesa-glx libglib-perl libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl libgnutls-dev libgnutls26 libgs9 libgtk2-perl libgtk2.0-0 libhtml-parser-perl libio-pty-perl liblocale-gettext-perl libnet-dbus-perl
  libnet-dns-perl libnet-libidn-perl libnet-ssleay-perl libpam-smbpass libpango-perl libpurple0 libsnmp-base libsnmp15 libsub-name-perl libterm-readkey-perl libtext-charwidth-perl libtext-iconv-perl libxml-parser-perl
  libyaml-syck-perl nvidia-current perl perl-base perl-modules pidgin pidgin-data samba-common smbclient
50 upgraded, 1 newly installed, 1 to remove and 1594 not upgraded.
261 not fully installed or removed.
Need to get 0 B/103 MB of archives.
After this operation, 31.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 535622 files and directories currently installed.)
Preparing to replace libc6 2.13-0ubuntu13.1 (using .../libc6_2.13-20ubuntu5.1_amd64.deb) ...
Killed
dpkg: error processing /var/cache/apt/archives/libc6_2.13-20ubuntu5.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 137
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.13-20ubuntu5.1_amd64.deb
Error org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program /lib/dbus-1.0/dbus-daemon-launch-helper: Success
E: Sub-process /usr/bin/dpkg returned an error code (1)


Also, for the record, all third-party repositories and backports are currently disabled.

> **benedictbrown said:**
> I'm trying to upgrade from 11.04 to 11.10 (then 12.04).  The upgrade to 11.10 failed on libc6, leaving my system with a broken package system.  It seems to be the same errors as on this thread.  I can still use most non-gnome applications, although I dare not reboot.

At present I've update my sources.list to point to natty rather than oneiric, just to try and get things back into a usable state.  Even after following the directions in this post, any attempts to install or fix anything, including apt-get autoremove, give the following errors:



As far as I can tell, there are no held packages.  Any suggestions would be greatly appreciated.

---

### Post by benedictbrown on 2012-05-29
I seemed to have solved my problems, although it wasn't pretty.  From another thread I found the command-line do-release-upgrade, which fingered various 32-bit binary packages (googleearth, acroread, skype, etc.) as the culprits that caused problems with libc6.  I uninstalled those, then a cascade of other packages that caused problems, then ran do-release-upgrade to oneiric and to precise.

Somewhere in this process dkpg got updated to rely on the new libc6 version that wasn't installed, so I booted a precise USB key, copied the correct libc6 over under another name (you can't install the correct libc6 package if the .so already exists), updated the libc.so.6 symlink (which you can only do when booted from another partition).  Then I chroot'ed to my hard drive's partition, and ran apt-get -f install a few times.  Finally I rebooted properly, and did that a few more times until things stabilized.

Like I said, not pretty.  But at least it determined that dpkg had updated itself without updated the underlying libc6.  Anyone else with this problem, a reinstall will almost certainly be less painful.

---

### Post by MateaMatt on 2012-08-21
I had a similar issue to benedictbrown (segfaulting on trying to install the latest versions of libc6 in oneiric, even manually with dpkg -i).  I manually (i.e. with dpkg -r) removed all 32bit packages from the system.  I removed oneiric updates and security from the software sources.  Then I manually installed matching versions of libc-bin and libc6 from oneiric:

[https://launchpad.net/ubuntu/oneiric/amd64/libc6/2.13-0ubuntu13](https://launchpad.net/ubuntu/oneiric/amd64/libc6/2.13-0ubuntu13)
[https://launchpad.net/ubuntu/oneiric/amd64/libc-bin/2.13-0ubuntu13](https://launchpad.net/ubuntu/oneiric/amd64/libc-bin/2.13-0ubuntu13)

Then I was able to get apt-get install -f to run and fix broken packages.  

It was also important to delete the files from the failed libc6 installs:

sudo rm -r /lib64.eglibc-new/

before reboot I ran 

sudo update-initramfs

After reboot, ubuntu failed to load a session, but ctrl+alt+1 to a terminal was possible and I then was able to successfully run

do-release-upgrade

The key seems to be getting the same version of libc-bin and libc6 installed (referenced above), which allows the broken packages to be fixed and then rebooting and running the upgrade from the command-line.

---

### Post by guirdianv on 2012-11-05
This happened to me after trying to use Pidgin for FB messaging. I simply looked in /usr for the folder that corresponded to the program, and used (as root) apt-get remove <folder name> and was able to update, and install new content. Try that if you can. Thanks for the help it took me a few hours tooling around to find that this works. Now to reboot.:guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar:

---

### Post by black veils on 2012-12-05
the moderators wont like you posting a problem in another person's thread. but all i can say is the problem looks to be some 3rd party repositories.

open update manager >> ***settings*** >> ***other software*** tab >> un-check the items in the list starting with:
[I][B]
[http://ppa.launchpad.net/ailurus](http://ppa.launchpad.net/ailurus)[/B][/I]

and

***[http://ppa.launchpad.net/mozillateam](http://ppa.launchpad.net/mozillateam)***


then ***close***. click ***check*** to refresh the repositories, it should no longer have that error, but you also wont have those ppa's activated. think about if you really need them, or if you can get them from somewhere else.

---

### Post by ibjsb4 on 2012-12-05
@siddi

[http://ppa.launchpad.net/mozillateam/ppa/ubuntu/dists/](http://ppa.launchpad.net/mozillateam/ppa/ubuntu/dists/)

[http://ppa.launchpad.net/ailurus/ppa/ubuntu/dists/](http://ppa.launchpad.net/ailurus/ppa/ubuntu/dists/)

They have not be upgraded for quite a while, remove them.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by siddi on 2012-12-05
Hi,
Sorry to gate crash another thread. But i can't open my sotware center or my update manager.

---

### Post by Noor1101 on 2012-12-05
Siddi, you'd better open your own thread and explain the problems you're encountering there. Posting your problem in another thread makes replying to the different issues very confusing.

Good luck

---

### Post by Noor1101 on 2012-12-05
> **ibjsb4 said:**
> @siddi
....[]("https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories")

Wow, ibjsb4, how did you manage to reply to siddi 5.5 hours before (s)he posted the issue!?

=D>

---

### Post by ibjsb4 on 2012-12-05
> **Noor1101 said:**
> Wow, ibjsb4, how did you manage to reply to siddi 5.5 hours before (s)he posted the issue!?

=D>

Black veils posted the answer an hour before me.

---

