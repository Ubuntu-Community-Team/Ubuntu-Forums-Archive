---
title: "Unable to add plugin for GIMP... apt-install not installing some packages"
date: 2015-05-13
forum: New to Ubuntu
---

### Post by gde061-www on 2015-05-13
Hi - I installed Ubutu 14.04 LTS a few months ago. I previously used GIMP for Windows, and now am trying to use it with my Ubuntu setup.  

Specifically I need to install the fourier transform plug-in. It seems a bit overly complicated (For Windows there was just a file you dropped into a directory and done.)  I'm not afraid of the command terminal, so I downloaded the package from here [http://registry.gimp.org/node/19596](http://registry.gimp.org/node/19596) (I guess it's called a tarball), unzipped it and attempted to install per the readme.  

The readme says:  You will need the fftw3 package, and the development packages of gimp, fftw3, and glib  
    (debian/ubuntu : sudo apt-get install libfftw3-dev libgimp2.0-dev)

I try to install those packages libfftw3-dev libgimp2.0-dev and end up with the following fail message:

The following packages have unmet dependencies:
 libgimp2.0-dev : Depends: libgtk2.0-dev (>= 2.12.5) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

From there I managed to find someone's post who had a similar error with libgtk2.0, here [http://ubuntuforums.org/archive/index.php/t-728232.html](http://ubuntuforums.org/archive/index.php/t-728232.html)

So I follow along that troubleshooting, which is pushing the limits of what I know, and I get: 

The following packages have unmet dependencies:
 libgtk2.0-dev : Depends: libgtk2.0-0 (= 2.24.23-0ubuntu1) but 2.24.23-0ubuntu1.1 is to be installed
                 Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.6.4-6.1) but it is not going to be installed
                 Recommends: debhelper but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

From there I am pretty much lost until at the end of the post they solve the issue by adding a gutsy-update repository to the apt sources.list file.  But that doesn't seem to work for me.  I try to add the indicated three lines to my sources.list: 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
[http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=libpango1.0-dev](http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=libpango1.0-dev)

But after I save that and try sudo apt-get update my system barfs on gutsy-updates saying it can't find the deb and deb-src reposotiries, and then the last line (that starts with the http:// ... ) returns some kind of "unexpected" fatal error.    Worth noting that the post I'm using for the solution is about 8 years old, but that's what I could find...

I post this in the "New to Ubuntu" forum even though it's a little technical because, being new to this OS, I don't understand APT or what the problem is with my package sources. I really could use from "beginner tutorial" type help with this.  The the sources.list file on my system is what came with the distribution when I installed (I think it was from a live-cd).  The only thing I changed was that I uncommented the repository:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner 48a49,53

(I don't know what that repository is for, or what application I needed it for, but it was in the original sources.list with a # in front of it)

Thanks in advance for your help!

---

### Post by QIII on 2015-05-13
Hello!

Gutsy is a very old and long unsupported release.  Its repos have been moved, explaining why they can't be used.

The first thing to do would be to remove that from your sources then update and upgrade to get things cleaned up.  When you are done, let us know and we'll see what we can do.

---

### Post by gde061-www on 2015-05-13
OK thanks.  I got rid of the gutsy lines but that just leaves me with the sources.list file I started out with when libgtk2.0-dev wouldn't install in the first place.  I ran the apt-get dist-upgrade, and then tried to install libgtk2.0-dev again, but it gave me the same errors:

> The following packages have unmet dependencies:
 libgtk2.0-dev : Depends: libgtk2.0-0 (= 2.24.23-0ubuntu1) but 2.24.23-0ubuntu1.1 is to be installed
                 Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.6.4-6.1) but it is not going to be installed
                 Recommends: debhelper but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Still stuck

---

### Post by ajgreeny on 2015-05-13
Let's see your sources.list file with ```
cat /etc/apt/sources.list
``` as I have just tried and there was no problem installing libgtk2.0-dev, so I believe you must have some problem in that file, or some repositories are not enabled.  
It may also help if you show the output of ```
sudo apt-get update
```

Please show these outputs from terminal in Code-tags (see my signature for a "How-to")

---

### Post by gde061-www on 2015-05-13
Here's my sources.list:

```

gdeangel@TP-E530-laptop:~$cat /etc/sources.list

# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

## Updates. Needed to get the GIMP forierer plugin to compile?
# deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
#http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=libpango1.0-dev

```

And the result of apt-get update
```

gdeangel@TP-E530-laptop:~$sudo apt-get update 
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://us.archive.ubuntu.com trusty InRelease
Hit http://security.ubuntu.com trusty-security Release.gpg
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://security.ubuntu.com trusty-security Release
Hit http://us.archive.ubuntu.com trusty Release
Hit http://security.ubuntu.com trusty-security/main Sources
Hit http://us.archive.ubuntu.com trusty/main Sources
Ign http://extras.ubuntu.com trusty InRelease
Ign http://archive.canonical.com trusty InRelease
Hit http://deb.opera.com stable InRelease
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://security.ubuntu.com trusty-security/universe Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://security.ubuntu.com trusty-security/multiverse Sources
Hit http://archive.canonical.com trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://extras.ubuntu.com trusty Release.gpg
Hit http://deb.opera.com stable/non-free amd64 Packages
Hit http://security.ubuntu.com trusty-security/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://archive.canonical.com trusty Release
Hit http://deb.opera.com stable/non-free i386 Packages
Hit http://extras.ubuntu.com trusty Release
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://security.ubuntu.com trusty-security/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://archive.canonical.com trusty/partner Sources
Hit http://extras.ubuntu.com trusty/main Sources
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://archive.canonical.com trusty/partner amd64 Packages
Hit http://extras.ubuntu.com trusty/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://archive.canonical.com trusty/partner i386 Packages
Hit http://extras.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://archive.canonical.com trusty/partner Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Ign https://private-ppa.launchpad.net trusty InRelease
Ign http://deb.opera.com stable/non-free Translation-en_US
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://deb.opera.com stable/non-free Translation-en
Hit https://private-ppa.launchpad.net trusty Release.gpg
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Hit https://private-ppa.launchpad.net trusty Release
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Hit https://private-ppa.launchpad.net trusty/main i386 Packages
Ign http://extras.ubuntu.com trusty/main Translation-en
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US
Ign https://private-ppa.launchpad.net trusty/main Translation-en
Reading package lists...Done

```
Seems like everything is updated?  

```

gdeangel@TP-E530-laptop:~/GimpFFT$ sudo apt-get install libfftw3-dev libgimp2.0-dev
[sudo] password for gdeangel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgimp2.0-dev : Depends: libgtk2.0-dev (>= 2.12.5) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
gdeangel@TP-E530-laptop:~/GimpFFT$ 


```

---

### Post by cariboo on 2015-05-13
Run the following commands first before trying to install any more packages:

```
sudo apt-get clean
```

Then

```
sudo apt-get purge libgimp2.0-dev
```

and

```
sudo apt-get purge libfftw3-dev
```

making sure that both packages are completely removed should help solve your problem.

I'm not sure what guide you are following, but I've found [this one]("http://en.wikibooks.org/wiki/GIMP/Installing_Plugins") works for me.

---

### Post by ajgreeny on 2015-05-13
I have just had a look at the plugin download site you linked to and noted the following regarding a problem installing that plugin.  It's a pity they do not mention what the problem is but it may be worth seeing if it helps to follow the link to the previous 0.4.1 version

Perhaps you did not see that and react accordingly?  If not try again.
>        Hi, it seems a bug prevents updating plugins so I post this as a comment for now.

 Here is a link for version 0.4.3 : [URL="http://people.via.ecp.fr/%7Eremi/soft/gimp/fourier-0.4.3.tar.gz"]http://people.via.ecp.fr/~remi/soft/gimp/fourier-0.4.3.tar.gz
[/URL] 

 This version fixes installation problems on Ubuntu. No change has  been made on the plugin since 0.4.1 so if you have a working 0.4.1  installation you are not concerned with this update.
 


          


I don't know if this will help but there is a gimp-plugin-registry package in the repos for 14.04 that might also solve your problem and make the plugin you need available more easily.  I don't use any gimp plugins so I do not really know enough to help more.

---

### Post by mc4man on 2015-05-13
> **gde061-www said:**
> OK thanks.  I got rid of the gutsy lines but that just leaves me with the sources.list file I started out with when libgtk2.0-dev wouldn't install in the first place.  I ran the apt-get dist-upgrade, and then tried to install libgtk2.0-dev again, but it gave me the same errors:
Still stuck

You currently have probably have libgtk2.0-0  (2.24.23-0ubuntu1.1) installed & the -dev package must match that exactly. However the current version in 14.04 for both should be 2.24.23-0ubuntu1.2 (trusty-updates
So - 
open Software & Updates > Updates tab & make sure the first 2 are enabled, in particular the 2nd one - Recommended (trusty-updates
Then reload your source & you should get an update to libgtk2.0-0  ( to 2.24.23-0ubuntu1.2) & be able to install libgtk2.0-dev ,ect.

---

### Post by abrianb on 2015-05-14
I second installing the gimp-plugin-registry package. It should install all available plugins.

---

### Post by gde061-www on 2015-05-14
Thanks so much! I first followed mc4man's advice and enabled the Recommended repo in the Software & Update GUI, then closed it and reopened it (since I didn't see any other way to reload the thing).  At that point I could search for libgtk2.0-0-dev in the GUI, and it was not installed, so I closed that down, went to through the clean &amp; purge commands as per cariboo's advice and installed it via the command line with apt-get install and success! Looks like I didn't need the gimp-plugin-registry package but good to know and I'll probably install it anyway.

This being a new user thread, I guess it's fair to ask... what's the difference between what was in sources.list (which has lots of "trusty" repository names); and what the checkbox in the SC GUI accomplish when you check the Recommended Updates (trusty-updates)?

---

### Post by adam-denoon on 2015-10-25
> **mc4man said:**
> open Software & Updates > Updates tab & make sure the first 2 are enabled, in particular the 2nd one - Recommended (trusty-updates
Then reload your source & you should get an update to libgtk2.0-0  ( to 2.24.23-0ubuntu1.2) & be able to install libgtk2.0-dev ,ect.

THANK YOU!! After reading many posts on many forums, your solution worked for me :p:p:p:p

---

