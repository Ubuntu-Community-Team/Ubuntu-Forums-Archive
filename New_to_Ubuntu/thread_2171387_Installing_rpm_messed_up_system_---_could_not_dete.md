---
title: "Installing rpm messed up system --- could not determine package or source name"
date: 2013-08-30
forum: New to Ubuntu
---

### Post by raequin on 2013-08-30
First off, I don't know what I'm doing.  Therefore if you read the following list of operations expecting them to make sense it could be confusing.  After using rpm, alien, and yum (more on that below) Software Center crashes and Update Manager says

```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'repomd' is not known on line 4 in source list /etc/apt/sources.list.d/rpmforge.list'
```

The intent of my modifications was to run a perl script that requires "the Crypt::Tea_JS module" (here's the explanation [http://placeshiftingenthusiasts.com/forum/general-sling-box-discussions/how-to-record-slingbox-pro-hd-stream-in-high-definition-720-or-1080/#p7528](http://placeshiftingenthusiasts.com/forum/general-sling-box-discussions/how-to-record-slingbox-pro-hd-stream-in-high-definition-720-or-1080/#p7528)).  I referred to the following instructions to install this module

> 

1.    Download the latest rpmforge-release rpm from

    [http://apt.sw.be/redhat/el6/en/i386/rpmforge/RPMS/](http://apt.sw.be/redhat/el6/en/i386/rpmforge/RPMS/)

2.    Install rpmforge-release rpm:

    # rpm -Uvh rpmforge-release*rpm

3.    Install perl-Crypt-Tea rpm package:

    # yum install perl-Crypt-Tea

I put the rpm's in my Downloads directory.  Step #2 says

```

raequin@raequin-T530:~/Downloads$ rpm -Uvh rpmforge-release-0.5.3-1.el6.rf.i686.rpm
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
warning: rpmforge-release-0.5.3-1.el6.rf.i686.rpm: Header V3 DSA/SHA1 Signature, key ID 6b8d79e6: NOKEY
error: Failed dependencies:
	/bin/sh is needed by rpmforge-release-0.5.3-1.el6.rf.i686

```

Since that did not seem to work I tried

```

raequin@raequin-T530:~/Downloads$ sudo dpkg -i rpmforge-release_0.5.3-2_i386.deb

```

I guess that went okay so I went to step #3 (after installing yum).  It went as follows.

```

raequin@raequin-T530:~/Downloads$ sudo yum install perl-Crypt-Tea-2.12-1.el6.rf.noarch.rpm 
[sudo] password for raequin: 
Setting up Install Process
Examining perl-Crypt-Tea-2.12-1.el6.rf.noarch.rpm: perl-Crypt-Tea-2.12-1.el6.rf.noarch
Marking perl-Crypt-Tea-2.12-1.el6.rf.noarch.rpm to be installed
Resolving Dependencies
--> Running transaction check
---> Package perl-Crypt-Tea.noarch 0:2.12-1.el6.rf set to be updated
--> Processing Dependency: /usr/bin/perl for package: perl-Crypt-Tea-2.12-1.el6.rf.noarch
--> Processing Dependency: perl(Exporter) for package: perl-Crypt-Tea-2.12-1.el6.rf.noarch
--> Processing Dependency: perl(integer) for package: perl-Crypt-Tea-2.12-1.el6.rf.noarch
--> Processing Dependency: /usr/bin/perl for package: perl-Crypt-Tea-2.12-1.el6.rf.noarch
--> Finished Dependency Resolution
perl-Crypt-Tea-2.12-1.el6.rf.noarch from /perl-Crypt-Tea-2.12-1.el6.rf.noarch has depsolving problems
  --> Missing Dependency: /usr/bin/perl is needed by package perl-Crypt-Tea-2.12-1.el6.rf.noarch (/perl-Crypt-Tea-2.12-1.el6.rf.noarch)
perl-Crypt-Tea-2.12-1.el6.rf.noarch from /perl-Crypt-Tea-2.12-1.el6.rf.noarch has depsolving problems
  --> Missing Dependency: perl(Exporter) is needed by package perl-Crypt-Tea-2.12-1.el6.rf.noarch (/perl-Crypt-Tea-2.12-1.el6.rf.noarch)
perl-Crypt-Tea-2.12-1.el6.rf.noarch from /perl-Crypt-Tea-2.12-1.el6.rf.noarch has depsolving problems
  --> Missing Dependency: perl(integer) is needed by package perl-Crypt-Tea-2.12-1.el6.rf.noarch (/perl-Crypt-Tea-2.12-1.el6.rf.noarch)
Error: Missing Dependency: perl(integer) is needed by package perl-Crypt-Tea-2.12-1.el6.rf.noarch (/perl-Crypt-Tea-2.12-1.el6.rf.noarch)
Error: Missing Dependency: /usr/bin/perl is needed by package perl-Crypt-Tea-2.12-1.el6.rf.noarch (/perl-Crypt-Tea-2.12-1.el6.rf.noarch)
Error: Missing Dependency: perl(Exporter) is needed by package perl-Crypt-Tea-2.12-1.el6.rf.noarch (/perl-Crypt-Tea-2.12-1.el6.rf.noarch)
 You could try using --skip-broken to work around the problem
 You could try running: package-cleanup --problems
                        package-cleanup --dupes
                        rpm -Va --nofiles --nodigest
The program package-cleanup is found in the yum-utils package.

```

I have not installed Exporter or Integer, but it seems weird to me that /usr/bin/perl comes up under missing dependencies.  Since I did not know what dpkg did and thought ... well, it doesn't matter what I thought.  What I did next was to install alien and enter

```
sudo alien rpmforge-release-0.5.3-1.el6.rf.i686.rpm
```

Then I tried the above yum again and got the same missing dependencies messages.  So that's what I did and something is wrong with the system packages list or whatever.  I want to know how to fix my system so that update manager will function.  I also want to know how to get the perl script to run (the one that requires Crypt::Tea_JS).

---

### Post by deadflowr on 2013-08-30
I'm guessing you could post the output for [COLOR=#000000][FONT=Ubuntu Mono]/etc/apt/sources.list.d/rpmforge.list
Seeing as there's a problem with line 4.

My guess is that the package manager is clueless about rpm sources.[/FONT][/COLOR]

---

### Post by raequin on 2013-08-30
> ... post the output for /etc/apt/sources.list.d/rpmforge.list

### Name: RPMforge RPM Repository for RHEL 6 - dag
### URL: [http://rpmforge.net/](http://rpmforge.net/)
#rpm [http://apt.sw.be](http://apt.sw.be) redhat/el$(VERSION)/en/$(ARCH) dag
repomd [http://apt.sw.be](http://apt.sw.be) redhat/el$(VERSION)/en/$(ARCH)/rpmforge

---

### Post by Werne on 2013-08-30
Apt/aptitude can't use RPM repositories, the apt sources (/etc/apt/sources.list and /etc/apt/sources.list.d/*.list) have this structure:
```
<package_type>    <repository_link>    <release>    <repositories>
```
And yum repos don't, hence why update-manager is crashing, it's likely that apt/aptitude will blurp out errors as well. It's never a good idea to have more than one package manager on a single system, stuff like this happens if you do. You can convert an .rpm package into .deb with alien (read alien's man page for instructions), there's no need for yum/rpm in order to install them. Even if alien can't do that, you can repackage it yourself into .deb and install it. But keeping two different package managers is just asking for trouble.

---

### Post by raequin on 2013-08-30
On this task I used rpm, dpkg, yum, and alien.  Can you tell me how to undo all that mess?  Brief comments on how to install Crypt::Tea_JS would be nice, too.

---

### Post by Werne on 2013-08-30
First purge rpm and yum with apt
```
apt-get remove --purge rpm yum && apt-get autoremove
```
Then make sure the yum repos are removed from apt repo lists
```
rm -rf /etc/apt/sources.list.d/rpmforge.list && apt-get update
```
You need to execute the above commands as root (meaning you need to use root shell as sudo -i or su). That should take care of it, you could install no packages using yum/rpm since it thought you have no packages installed on your system (hence the fact that you shouldn't mix two package managers, they don't know what the other one is doing), meaning it couldn't resolve any dependencies.

As for Crypt::Tea_JS, you can try and use alien for converting to DEB (do read it's man page first and check the DEB package afterwards), I can't find it for Ubuntu/Debian or any other distribution except RHEL and RHEL-based distros, can't even find the source code for compiling. I would advise against using it on Ubuntu (since RHEL is ancient compared to it) but you can try.

---

### Post by Jonathan Precise on 2013-08-30
> **raequin said:**
> On this task I used rpm, dpkg, yum, and alien.  Can you tell me how to undo all that mess?  Brief comments on how to install Crypt::Tea_JS would be nice, too.

Open a terminal and type:
```
sudo -i
rm -rf /etc/apt/sources.list.d/rpmforge.list && apt-get update && apt-get upgrade && exit
exit
```
This will remove the repository :( (Debian/Ubuntu/Linux-Mint based systems do not support rpm repositories), update the package lists, install available updates, exit the root shell if all goes well (the root shell, when not used with care, can be dangerous:!:), and exit the terminal.

---

### Post by raequin on 2013-09-01
Per the instructions above I removed yum and rpm and also deleted rpmforge.list (and updated the system).  Update Manager and Ubuntu Software Center both work again but at startup I'm getting a popup saying "System program problem detected".  It's not rich in information.  Everything seems to be working okay.  Any suggestions on how to track down this error and get it fixed?

---

### Post by Jonathan Precise on 2013-09-02
> **raequin said:**
> Per the instructions above I removed yum and rpm and also deleted rpmforge.list (and updated the system).  Update Manager and Ubuntu Software Center both work again but at startup I'm getting a popup saying "System program problem detected".  It's not rich in information.  Everything seems to be working okay.  Any suggestions on how to track down this error and get it fixed?

Click yes, type your password, then click on details (sometimes you just click on details). That should tell you what program it is.

---

### Post by raequin on 2013-09-10
The "System program problem detected" popup no longer appears at start up.  I just installed Perl and the Crypt-Tea_JS package in Windows.  Thanks for helping me get my Ubuntu install back to normal.

---

