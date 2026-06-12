---
title: "Help installing wine on a 64bit system"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by dresnu on 2012-07-16
Hello, I can't seem to be able to install wine on my 64bit ubuntu box. If I type```
sudo apt-get install wine1.4
``` I get ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4-0ubuntu4)
E: Unable to correct problems, you have held broken packages.
```

Then ```
sudo apt-get install wine1.4-i386
``` provides this result ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4-i386:i386 : Depends: libgl1-mesa-glx:i386 but it is not going to be installed or
                              libgl1:i386
                     Depends: libglu1-mesa:i386 but it is not going to be installed or
                              libglu1:i386
                     Recommends: gettext:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Trying to install these packages gives errors too. In particular I'm unable to install package libdrm2:i386.

---

### Post by sanderj on 2012-07-16
You have to solve "E: Unable to correct problems, you have held broken packages." first.

So Google 'Ubuntu "E: Unable to correct problems, you have held broken packages."'.

HTH

---

### Post by prshah on 2012-07-16
> **dresnu said:**
> ```
sudo apt-get install wine1.4
``` I get [CODE]

You should not have a problem installing either wine or wine1.4 on 64bit.

You should not need to attempt to install parts of the meta package manually (eg wine1.4-i386). Note that on a 64 bit system, you are looking at a multi-arch install, so the correct package specification should be wine1.4-i386:i386

Please first attempt an apt-get update, and post back errors/warnings, if any.

---

### Post by Paqman on 2012-07-16
> **dresnu said:**
> Hello, I can't seem to be able to install wine on my 64bit ubuntu box. If I type```
sudo apt-get install wine1.4
```

Try:
```
sudo apt-get install wine
```

If it's still complaining about broken packages, install [Synaptic]("apt:synaptic"), go to Custom Filters > Broken and reinstall the broken package(s). If you get errors post them here.

---

### Post by dresnu on 2012-07-16
> **Paqman said:**
> Try:
```
sudo apt-get install wine
```

Results in```
The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

> **Paqman said:**
> If it's still complaining about broken packages, install [Synaptic]("apt:synaptic"), go to Custom Filters > Broken and reinstall the broken package(s). If you get errors post them here.

Actually I don't have a "Custom Filters" menu selection but there is "Edit > Fix broken packages" that results in to nothing. Also if I "-f install" with apt-get I get no errors or broken packages.

---

### Post by dresnu on 2012-07-16
I found an open bug report on the issue [https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/994309]("https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/994309")

***WARNING THE FOLLOWING SOLUTION MESSES UP APT PRETTY BAD***
I have temporarily solved it following indications on comment #7, it's the "dirty" way though.

Thanks to all who replied.

---

### Post by ernstp on 2012-08-04
sudo apt-get install wine  --no-install-recommends works fine for me.

---

### Post by baijea on 2012-09-23
I had a similar problem with broken dependencies when trying to install **wine** and **acroread**, just after upgrading to **12.04** from **11.04** (passing over 11.10). It seems that some ppa's I had in 11.04 installed **newer versions of applications** in the system. After upgrading, the remains of these apps seemed to do some mess in the dependencies.

The solution that seems to work (until now), was found on a german ubuntu board ([http://forum.ubuntuusers.de]("http://forum.ubuntuusers.de/topic/paketabhaengigkeit-mit-ia32-libs-kann-nicht-au/2/"), posts from user Lasall):

First a downgrade is required and done with the following:
create the 'preferences' file:
```
sudo vi /etc/apt/preferences
```
and insert the following lines:
```

Package: *       
Pin: release a=precise*
Pin-Priority: 2012

```
Pin-Priority must be greater than 1000.

Then you may downgrade the programs with:
```
sudo apt-get dist-upgrade
```
Then you may install packages that complained about dependencies, like
```
sudo apt-get install ia32-libs-multiarch
```, or ```
sudo apt-get install ia32-libs
```

Finally, you should remove the file you just created:
```
rm /etc/apt/preferences
```
because else no new updates would be found.

Hope this helps you too!

---

### Post by dresnu on 2012-09-24
Thank you very much! The steps you point out finally solved the problem for me.

Cheers!

---

### Post by marseille on 2013-06-09
:KS:KS:KS

Thx, this switch worked for me after running into problems with both software center and apt-get:

> $ ...   --no-install-recommends 

---

### Post by Baldrick_NZ on 2013-06-10
> **Paqman said:**
> Try:
```
sudo apt-get install wine
```

If it's still complaining about broken packages, install [Synaptic]("apt:synaptic"), go to Custom Filters > Broken and reinstall the broken package(s). If you get errors post them here.

Nooooooooooooooooooo! I wouldn't advise this at all. Installing 'wine' on it's own would only attempt to install the unstable (in my case, unusable) development version, wine1.5. Chances are, if you successfully installed that you'd have way more problems. In my opinion, until 1.5 becomes stable (1.6), stick with trying to get wine1.4 going.

Speaking of which, I've found downloading and installing 'synaptic' from the repos has always been a great aid in solving wine dependency issues. I usually just type 'wine' in the search bar and then click 'remove completely' any files that refer to wine, of which there are only a handful. Apply, then re-install 'wine1.4'. Usually works for me. 

Hope that helps!

---

### Post by todorakiggg on 2013-06-10
Download and install **PlayOnLinux**!
It gets the proper version of wine and installs whenever is needed. After a lot of problems as you mentioned, I finally got to this answer. It works flawlessly for me.

---

