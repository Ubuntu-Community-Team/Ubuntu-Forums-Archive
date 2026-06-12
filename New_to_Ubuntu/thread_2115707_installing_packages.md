---
title: "installing packages"
date: 2013-02-13
forum: New to Ubuntu
---

### Post by Nobi on 2013-02-13
hey guys, am trying to install "villagetelco-dashboard" and it says installation has no candidate, what does that mean??

---

### Post by schragge on 2013-02-13
It means that there's no such package in Ubuntu repositories.

---

### Post by Nobi on 2013-02-13
okay, am trying to install villagetelco-dashboard and this is what i get,

root@elizabeth-3000-N200:~# sudo apt-get install villagetelco-dashboardReading package lists... Done
Building dependency tree       
Reading state information... Done
Package villagetelco-dashboard is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'villagetelco-dashboard' has no installation candidate


please help

---

### Post by snowpine on 2013-02-13
I am not familiar with this software; is it the same thing as "SPUD"? If so, it looks like they have detailed install instructions here: [http://villagetelco.org/2011/06/spud-simple-unified-dashboard-for-mesh-networks/](http://villagetelco.org/2011/06/spud-simple-unified-dashboard-for-mesh-networks/)

---

### Post by Nobi on 2013-02-13
I did try SPUD but i could not connect to its server. 

Afrimesh is similar to SPUD, so i need tose villagetelco-dashboard packages for it to work.

I dont know what i did but another problem is my synaptic manager cant load, it shuts down after it gives a massage that "lucid" is not in the source list. before that, i could find the villagetelco-dashboard.

---

### Post by snowpine on 2013-02-13
As I mentioned, I am unfamiliar with this software. Can you provide a link to the tutorial or how-to you are trying to follow? Then if you tell us which step you're stuck on and copy & paste the exact error messages, perhaps someone can help. Alternately you can research if there is comparable-function software available through the Ubuntu repositories, in which case you can easily install with a couple of mouse clicks in the Software Center.

You do understand that your software sources (governed by the file /etc/apt/sources.list and files in /etc/apt/sources.list.d) are important system files, and modifying them can break your system, right? Which Ubuntu release are you using? If you are not using Ubuntu 10.04 Lucid Lynx, then there should be no "lucid" in your software sources. :)

---

### Post by Nobi on 2013-02-13
am trying to follow the HowTo on this link

[http://wiki.villagetelco.org/index.php?title=Mesh_Potato_HOWTOs#Testing_Afrimesh_Version_.954](http://wiki.villagetelco.org/index.php?title=Mesh_Potato_HOWTOs#Testing_Afrimesh_Version_.954)

step 2 of testing the afrimesh, the ohter packages installed but villagetelco-dashboard couldnt be authenticated.

I think this problem is caused by problems in source list. anyway, i tried editing the source list but it was read-only.

---

### Post by snowpine on 2013-02-13
OK, let's take a look at those instructions, step by step, I will try to help you through.

Step 0 is, which Ubuntu release are you using? 

[https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

If the answer is anything other than 10.04 Lucid Lynx, you are following the wrong instructions. You need to find correct instructions for whichever release you are using.

If the answer is 10.04 then you are ready to proceed to step 1, and so on. Copy & paste the full terminal output of each step here on the forums so people can assist you.

However, I think you are going to hit a brick wall on Step 3, because the link is broken. 

If I were in your shoes, I would contact the makers of this software directly and ask for help, since it is third-party software not provided or supported by Ubuntu in any way.

---

### Post by Dodeca on 2013-02-13
I found this code on the web with a google search ...  be cautious !

```
  sudo apt-add-repository ppa:afrimesh/ppa
  sudo apt-get update
  sudo apt-get install villagetelco-dashboard



```

---

### Post by Nobi on 2013-02-13
am using ubuntu 12.04 and i added the repositories manually. on the second step batman and polipo are installed.

i used this command:
**sudo gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 50CFBA3E**

instead of:
sudo apt-add-repository ppa:afrimesh/ppa
everything worked fine. it was available in the repository until...(I dnt know what i did).
now when i open the synaptic manager, i get this error message and it shuts down.

[B]E: The value 'lucid' is invalid for APT::Default-Release as such a release is not available in the sources
E: _cache->open() failed, please report.
[/B]

---

### Post by snowpine on 2013-02-13
12.04 is "Precise Pangolin" not "Lucid Lynx." The instructions you have found for 10.04 Lucid **will not work on your Ubuntu release**, sorry. It is possible the steps you have taken so far have damaged your system in some way (thus the error in Synaptic), but I really can't say for sure. :(

---

### Post by Nobi on 2013-02-13
hey Dodeca!

 thanx but I think I may be having a problem with my source list.

everytime i open synaptic manager i get this:[B]

E: The value 'lucid' is invalid for APT::Default-Release as such a release is not available in the sources
E: _cache->open() failed, please report.

[/B]then it shuts down**. **I did use lucid main not precise when adding my repositories. 

I figure if i edit my source list manually this might stop.
my source list is read-only. how can i change it?

---

### Post by Nobi on 2013-02-13
is there a way for me to fix this or not???

and how can i edit my source list coz i think i still have lucid in it???

---

### Post by snowpine on 2013-02-13
Here is a guide to editing software sources in Ubuntu:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

The quickest/easiest way to do it, in my opinion is to directly edit the sources.list file with your favorite text editor (such as gedit in my example):

```
gksu gedit /etc/apt/sources.list
```

It should go without saying that you must tread very carefully when editing this important system file. If you are in doubt how to proceed, then you should copy & paste the contents of this file here, and we will give advice how to proceed.

---

### Post by Nobi on 2013-02-13
i just edited my source.list and my synaptic manager works after i replaced all the precise with the lucid.

will this be a problem?

---

### Post by snowpine on 2013-02-13
> **Nobi said:**
> 
will this be a problem?

Yes. You must only use "precise" sources for 12.04.

---

### Post by Nobi on 2013-02-13
**APT::Default-Release error** 			
 			 			 		   		 		 		E: The value 'lucid' is invalid for APT::grin:efault-Release as such a release is not available in the sources
E: _cache->open() failed, please report.

could you please show me where the problem is....here is my source.list output.:

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted multiverse universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted multiverse universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb [http://ppa.launchpad.net/afrimesh/ppa/ubuntu](http://ppa.launchpad.net/afrimesh/ppa/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/afrimesh/ppa/ubuntu](http://ppa.launchpad.net/afrimesh/ppa/ubuntu) hardy main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

---

### Post by snowpine on 2013-02-13
Looks good to me, I hope it is enough to undo the previous damage. :)

---

### Post by Nobi on 2013-02-13
thank you so much you guys! 

lastly, what do you advice me to do with this situation???

---

### Post by snowpine on 2013-02-13
I recommend you contact the makers of this software/hardware and ask for updated instructions for Ubuntu 12.04 Precise Pangolin. Village Telco has a support page on their site: [http://villagetelco.org/support/](http://villagetelco.org/support/)

It's likely you will get better support for your Village Telco product from the manufacturer than here on Ubuntu Forums, since the software is not distributed or supported by Ubuntu. In fact I did a forum search (top right of the screen) for the terms "afrimesh" and "villagetelco" and this thread right here is the only discussion of these topics in the history of Ubuntu Forums, implying that you will not find the answers you seek here (sorry).

---

### Post by schragge on 2013-02-14
Please post the output of
```

grep -wH lucid /etc/apt/sources.list.d/*

```

---

