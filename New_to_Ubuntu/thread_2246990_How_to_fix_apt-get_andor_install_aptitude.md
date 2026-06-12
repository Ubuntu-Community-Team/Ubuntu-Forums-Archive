---
title: "How to fix apt-get and/or install aptitude"
date: 2014-10-04
forum: New to Ubuntu
---

### Post by PsiDog on 2014-10-04
**The short version: **
apt-get is failing me, and I can't install aptitude, even manually. Please advise.

**The long story?** 
Well...
Today is my first day on ubuntu, and the 1st thing I did was to check my OpenGL version to ensure the proper graphic drivers were installed. Thats when the trouble started.

```
me@my-iMac:~$ glxinfo|more
The program 'glxinfo' is currently not installed. You can install it by typing:
sudo apt-get install mesa-utils

[2]+  Stopped                 glxinfo | more
me@my-iMac:~$ sudo apt-get install mesa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mesa-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'mesa-utils' has no installation candidate

```

The universal internet suggestions were to:
a) update/upgrade apt-get
or
b) use aptitude

sudo apt-get update resulted in alternating blocks of 'Ign <location>' and 'Err <location> 404 Not Found [IP: <location>]'
This was followed by a list of 'W: Failed to fetch <location> 404 Not Found'

 sudo apt-get upgrade reported 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sudo apt-get install aptitude gave the results as sudo apt-get install mesa-utils.


Next I went to [http://packages.ubuntu.com/trusty/aptitude](http://packages.ubuntu.com/trusty/aptitude) and tried to install manually.
The package downloaded, and Ubuntu Software Center complained that aptitude-common dependency was not satisfiable.
So I downloaded the aptitude-common package, which worked, but when going back to aptitude was then told 
```
Depenency is not satisfiable: libapt-pkg4.12 (>=0.9.11)
```
Fine. Downloading libapt-pkg4.12

**Package operation failed**
v Details
```
dpkg: regarding .../libapt-pkg4.12_1.0.1ubuntu2.4.1_amd64.deb containing libapt-pkg4.12:amd64: 
 libapt-pkg4.12:amd64 breaks libapt-inst1.5 (<< 0.9.9~) 
  libapt-inst1.5:amd64 (version 0.9.7.7ubuntu4) is present and installed. 
 
dpkg: error processing /home/paul/Downloads/libapt-pkg4.12_1.0.1ubuntu2.4.1_amd64.deb (--install): 
 installing libapt-pkg4.12:amd64 would break libapt-inst1.5:amd64, and 
 deconfiguration is not permitted (--auto-deconfigure might help)
```



So... what is the best way to get either apt-get or aptitude working?

---

### Post by deadflowr on 2014-10-04
Neither will be of any use until you fix the underlying "Failed to Fetch" problem.
So, post the output first of the apt-get update command.

I will also guess that you are posting from the machine in question.
Is this right?

Another question would be, is the machine connecting to the internet through a proxy?

---

### Post by Bashing-om on 2014-10-04
PsiDog; Hello

see deadflowr's ^ advise.
In addition, insure the universe repository is enabled in Software Sources;
```

sysop@1404mini:~$ apt-cache show mesa-utils
Package: mesa-utils
Priority: extra
Section: [color=green]universe[/color]/graphics
Installed-Size: 130
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: amd64
Source: mesa-demos
Version: 8.1.0-2
<snip>

```
As you can see the package is available .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by PsiDog on 2014-10-04
@deadflowr: Correct, I am posting from the ubuntu OS on the macine in question. I did not set up a proxy connection.

The error list is kind of long, but here it is:
```
me@my-iMac:~$ sudo apt-get update
Ign http://security.ubuntu.com raring-security Release.gpg
Ign http://security.ubuntu.com raring-security Release                    
Ign http://us.archive.ubuntu.com raring Release.gpg                            
Ign http://us.archive.ubuntu.com raring-updates Release.gpg                    
Ign http://us.archive.ubuntu.com raring-backports Release.gpg              
Ign http://us.archive.ubuntu.com raring Release                            
Ign http://extras.ubuntu.com raring Release.gpg
Ign http://us.archive.ubuntu.com raring-updates Release
Ign http://extras.ubuntu.com raring Release    
Ign http://us.archive.ubuntu.com raring-backports Release
Err http://extras.ubuntu.com raring/main Sources                     
  404  Not Found
Err http://extras.ubuntu.com raring/main amd64 Packages              
  404  Not Found
Err http://extras.ubuntu.com raring/main i386 Packages
  404  Not Found
Ign http://extras.ubuntu.com raring/main Translation-en_US
Ign http://extras.ubuntu.com raring/main Translation-en
Err http://security.ubuntu.com raring-security/main Sources
  404  Not Found [IP: 91.189.88.153 80]
Err http://security.ubuntu.com raring-security/restricted Sources
  404  Not Found [IP: 91.189.88.153 80]
Err http://security.ubuntu.com raring-security/universe Sources
  404  Not Found [IP: 91.189.88.153 80]
Err http://security.ubuntu.com raring-security/multiverse Sources
  404  Not Found [IP: 91.189.88.153 80]
Err http://security.ubuntu.com raring-security/main amd64 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err http://security.ubuntu.com raring-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err http://security.ubuntu.com raring-security/universe amd64 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err http://security.ubuntu.com raring-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err http://security.ubuntu.com raring-security/main i386 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err http://security.ubuntu.com raring-security/restricted i386 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err http://security.ubuntu.com raring-security/universe i386 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err http://security.ubuntu.com raring-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.153 80]
Ign http://security.ubuntu.com raring-security/main Translation-en_US
Ign http://security.ubuntu.com raring-security/main Translation-en
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US
Ign http://security.ubuntu.com raring-security/multiverse Translation-en
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US
Ign http://security.ubuntu.com raring-security/restricted Translation-en
Ign http://security.ubuntu.com raring-security/universe Translation-en_US
Ign http://security.ubuntu.com raring-security/universe Translation-en
Err http://us.archive.ubuntu.com raring/main Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring/restricted Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring/main amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring/universe amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Ign http://us.archive.ubuntu.com raring/main Translation-en_US
Ign http://us.archive.ubuntu.com raring/main Translation-en
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring/restricted Translation-en
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring/universe Translation-en
Err http://us.archive.ubuntu.com raring-updates/main Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-updates/restricted Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-updates/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-updates/main amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en
Err http://us.archive.ubuntu.com raring-backports/main Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-backports/restricted Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-backports/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-backports/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-backports/main amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-backports/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-backports/universe amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-backports/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-backports/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-backports/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com raring-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Ign http://us.archive.ubuntu.com raring-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/main Translation-en
Ign http://us.archive.ubuntu.com raring-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com raring-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com raring-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/universe Translation-en
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-amd64/Packages  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.88.153 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

@Bashing-om
```
me@my-iMac:~$ apt-cache show mesa-utils
N: Can't select versions from package 'mesa-utils' as it is purely virtual
N: No packages found
```

---

### Post by Bashing-om on 2014-10-04
PsiDog: UUoohh ...

'raring' release 13.04 is End-Of-Life and has no direct access to the required software repository. as with EOL it no longer exists.
> 
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release  


Rcommended most highly to install a current release:
ubuntu:
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[INDENT][INDENT]that is one solution
[/INDENT][/INDENT]

---

### Post by oldos2er on 2014-10-04
Raring (13.04) is no longer supported, which is why some of its repositories are showing 404 errors. Please install a supported version; 14.04 would be a good choice.

---

### Post by PsiDog on 2014-10-04
Oh... ok.

Is there any way to do this from within ubuntu or will I need to erase the partition and try again from scratch?

In theory the Software Updater should be able to do this, but mine keeps giving me a "Failed to download repository information" notice.

EDIT: The updater finaly figured out I had an old version and has started the update process. Hopefully this will eventually take me to v14.

---

### Post by Impavidus on 2014-10-05
As this is your first (or by now maybe second) day on Ubuntu, you can't have done a lot yet. Starting from scratch is the best option.

---

### Post by PsiDog on 2014-10-05
Thank you everyone for identifying the core problem. (old version) I thought I had the latest version the first time through, and never would have suspected Ubuntu would be so version sensitive.

For anyone else with this problem, follow Impavidus's advice and start over from scratch. Going through the update application to go from 13.04 to 13.10 to 14.04 ended up taking me 3x longer than the original download/DVD burn/installation.

---

### Post by oldos2er on 2014-10-05
Thank you for marking the thread 'Solved.'

You can keep an eye on the release and EOL (end-of-life) schedule [here]("https://wiki.ubuntu.com/Releases"); as you can see 14.04 is an LTS release and will be supported for several years, so you won't need to worry about upgrading again for awhile.

---

