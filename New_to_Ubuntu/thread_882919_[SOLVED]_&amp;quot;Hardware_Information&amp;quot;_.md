---
title: "[SOLVED] &amp;quot;Hardware Information&amp;quot; Missing from Menu"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by new2ubun2linux on 2008-08-07
Hi everyone, can you help,

I don't have the "Hardware Information" entry in my "System > Preferences" menu. I discovered this while trying to sort out a hardware problem. It seems weird that it's not there, but searching previous posts I did find that someone else reported a similar problem, but the solutions were all about fixing his hardware problem and not about the missing menu entry. ( [http://ubuntuforums.org/showthread.php?t=804087&highlight=Hardware+Information+missing+menu](http://ubuntuforums.org/showthread.php?t=804087&highlight=Hardware+Information+missing+menu) )

My installation is new today - Ubuntu v 8.04.1 and I have included a screen shot of the offending menu to prove I am not being daft!

Please help!

---

### Post by drs305 on 2008-08-07
If you are looking for gnome's device manager, you can install it via Synaptic or run the following:
```

sudo aptitude install gnome-device-manager

```

Once it's installed, you access it via System Tools, Device Manager.

---

### Post by Victormd on 2008-08-07
This is something that was installed by default on older versions of ubuntu. In Hardy I think you have to install it yourself (someone please correct me if I'm wrong). Open a terminal and type
```
sudo apt-get install gnome-device-manager
```

Or search in Synaptic package manager for device manager and mark gnome-device-manager to install it...

After you install it, it should show up under Applications>System Tools>Device Manager

---

### Post by new2ubun2linux on 2008-08-07
Hi drs305,

Not sure I understood that! Was it meant for someone else?

For info I have looked in the "System > Preferences > Main Menu" and "hardware Information" doesn't appear as even an option to be ticked, and if I try "add new"  I don't know what the command is to run Hardware Information or Device manager or whatever it is called..

---

### Post by drs305 on 2008-08-07
> **new2ubun2linux said:**
> Hi drs305,
Not sure I understood that! Was it meant for someone else?


Yes, sorry. I posted in the wrong thread and corrected it saying I'd be back in a bit. I returned and provided the answer, apparently about the same time as Victormd answered. In any case, you have your answer and if you are satisfied please mark the thread solved. If you have more questions or the gnome-device-manager wasn't what you were looking for, let us know.

---

### Post by new2ubun2linux on 2008-08-07
Will try that when I get back to my Laptop and let you know. It sounds like that will sort it.

Hopefully someone will update the help file - I suppose its all a bit new with v8.04!

---

### Post by new2ubun2linux on 2008-08-11
Just to let anyone who checks this thread know - the above advice was correct. Device Manager is no longer installed by default in Hardy Heron, so the entry "System > Preferences > Hardware Information" is no longer present after a vanilla installation of v8.04.1 despite what the help documentation says!

I do not know about an upgrade from an earlier version.

I installed Gnome Device Manager using the Add/Remove... option and then Device Manager appears under "Applications > System Tools"

Hope that answers this question for all who come across this. I will now mark this as "Solved" :)

---

### Post by DThoma128 on 2008-12-31
What do you mean by "Add/Remove"? I tried the two commands spelled out about and neither worked.

sudo apt-get install gnome-device-manager yielded and error "package gnome-device-manager is not available, but is referred to by another package"

sudo aptitude install gnome-device-manager yielded "No candidate version found for gnome-device-manager"

Thanks in advance.

---

### Post by drs305 on 2008-12-31
> **DThoma128 said:**
> What do you mean by "Add/Remove"? I tried the two commands spelled out about and neither worked.

sudo apt-get install gnome-device-manager yielded and error "package gnome-device-manager is not available, but is referred to by another package"

sudo aptitude install gnome-device-manager yielded "No candidate version found for gnome-device-manager"

Thanks in advance.

gnome-device-manager is in the universe repository, which must be enabled. To do so, either open System > Administration > Software Sources or Synaptic. From there, Settings > Repositories > Ubuntu Software. Make sure the Community Maintained Open Source software (universe) is ticked. Then hit the Reload button and install gnome-device-manager.

Via command line after you have enabled the *universe* repository:
```

sudo apt-get update
sudo apt-get install gnome-device-manager

```

I just installed it via synaptic without problems.

---

### Post by unutbu on 2008-12-31
The gnome-device-manager is in the universe repository. The error message you received suggests you do not have the universe repository enabled. To enable it:

Go to System>Admin>Software Sources. Under the first tab, "Ubuntu Software", click the box which says "Community-maintained Open Source software (universe).

Close the window. Then try installing gnome-device-manager again.

If it still does not work, please post the output of
```

cat /etc/apt/sources.list
sudo apt-get update
```

---

### Post by DThoma128 on 2008-12-31
Thanks drs305 and unutbu. The "Community maintained Open Source software" option was however already checked. I am trying to use device manager in order to install ndiswrapper so I can in turn use a Windows Network device driver in order to connect to my home network. Thus I am not connected to the outside workld yet. If I run the sudo apt-get update a bunch of errors are raised that it cannot resolve "http://..." links to the outside. I only just downloaded and installed 8.04.1 today so it seems like it should be current. Is there a way to enable the update to pull from the cd I burned or would the required content not even be in he download?

Outputs of the two commands are as follows:

**cat /etc/apt/sources.list**:
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
# newer versions of the distribution. 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted 

## Major bug fix updates produced after the final release of the 
## distribution. 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security 
## team. 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse 

## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse 
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu 
## users. 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner 
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

**sudo apt-get update**:
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Some index files failed to download, they have been ignored, or old ones used instead. 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable) 
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Some index files failed to download, they have been ignored, or old ones used instead. 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable) 
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by unutbu on 2008-12-31
It is possible to install ndiswrapper from your LiveCD. Here are instructions:
[http://ubuntuforums.org/showpost.php?p=6364751&postcount=2](http://ubuntuforums.org/showpost.php?p=6364751&postcount=2)

---

### Post by drs305 on 2008-12-31
If you remove the comment section from the first line in your sources.list regarding the CDROM, and the CDROM is inserted, it's contents will be available. In this case, however, the CD looks at 'main' and 'restricted' so specifically gnome-device-manager may not be on the CD. It possibly will help for other apps.

If you do uncomment it, however, once you get online you will probably want to disable it again or anytime you do an update it will ask for the CD.

Also, the 'lock' message may mean that you had another installation program operating at the same time. Make sure you have only one instance of synaptic/Add-Remove running.

---

### Post by DThoma128 on 2008-12-31
Even after getting ndiswrapper installed I'll need the Device Manager to check some things...thus I still need it installed. It seems to me that it would be a fundemental include within the distro...is there a way for me to determine if it is on the CD or not?

---

