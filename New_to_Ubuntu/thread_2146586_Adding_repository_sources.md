---
title: "Adding repository sources"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by faust99 on 2013-05-19
When I run apt-get update I have a few 404 errors in reference to some repositories. For example:

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages    
  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/raring/main/binary-amd64/Packages](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found


I would like to remove these repositories from my sources list but I cannot find them in /etc/apt/sources.list. So my question is why is apt-get update using sources which are not in my list of sources and how can I get rid of them? Is there another file somewhere which specifies software sources?

---

### Post by faust99 on 2013-05-19
This helped
[http://askubuntu.com/questions/65911/how-can-i-fix-a-404-error-using-a-ppa](http://askubuntu.com/questions/65911/how-can-i-fix-a-404-error-using-a-ppa)

---

### Post by faust99 on 2013-05-19
The problem is that [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages and [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages are not listed in either the Software & Updates GUI list nor in /etc/apt/sources.list.d. So where are they and how can they be removed to prevent daily 404 errors?

---

### Post by claracc on 2013-05-19
> **faust99 said:**
> The problem is that [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages and [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages are not listed in either the Software & Updates GUI list nor in /etc/apt/sources.list.d. So where are they and how can they be removed to prevent daily 404 errors?

All the ppas used have to be in sources.list file, could you run the command ```
cat /etc/apt/sources.list
``` and post the ouput in order to see what lines have to be removed?

---

### Post by faust99 on 2013-05-19
Thank you for the reply. I have noticed that if I deselect [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) from the Other Software tab in the Software & Updates dialogue, the 404 errors related to [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages and [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 do not occur.

Here's the output from cat /etc/apt/sources.list 

# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) raring universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) raring universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) raring-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) raring free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) raring free non-free
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) raring-security multiverse restricted main universe

---

### Post by claracc on 2013-05-19
The problem is that there is not a raring folder in [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu), so you cannot add this ppa to your sources-list as you are running the 13.04 raring ubuntu release.

So, you remove the indicated ppa [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) from your sources.list . Ithink the easier way is through the gui of software & updates in the other software tab.

---

### Post by faust99 on 2013-05-19
Right I see-thank you.

---

### Post by mc33 on 2013-06-24
[COLOR=#000000]To remove a PPA from the command line, simply add the [/COLOR]**-r **switch to the original add PPA command.

So, to remove the PPA of OpenShot stable, the command is:[B]

sudo add-apt-repository -r ppa:openshot.developers/ppa
[/B]
To re-add the PPA of OpenShot stable, exclude the **-r** switch from the above command:
[B][B]
[B]sudo add-apt-repository ppa:openshot.developers/ppa

[/B][/B][/B]When the OpenShot developer team adds a sources.list entry for Ubuntu 13.04 (Raring Ringtail), you will then be able to keep the above PPA without encountering a 404 error during 'apt-get update'.

---

