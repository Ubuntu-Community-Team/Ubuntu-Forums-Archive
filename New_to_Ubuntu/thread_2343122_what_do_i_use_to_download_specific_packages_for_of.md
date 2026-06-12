---
title: "what do i use to download specific packages for offline use"
date: 2016-11-13
forum: New to Ubuntu
---

### Post by a.dusty.trail on 2016-11-13
what do i use to download specific packages for offline use

i have a list of specific  packages  that i want to download
(in a text file)
what would be the simplest way to have that text file read and the packages downloaded to the current (or another directory)

ie:
 libsystemd0_229-4ubuntu7_i386.deb  

  chromium-codecs-ffmpeg-extra_51.0.2704.79-0ubuntu0.16.04.1.1242_amd64.deb  

   snap-confine_1.0.38-0ubuntu0.16.04.4_amd64.deb  

   ubuntu-core-launcher_1.0.38-0ubuntu0.16.04.4_amd64.deb  

  libudev1_229-4ubuntu7_i386.deb  

  m4_1.4.17-5_amd64.deb  

   autoconf_2.69-9_all.deb  

   autotools-dev/autotools-dev_20150820.1_all.deb  

   automake-1.15/automake_1.15-4ubuntu1_all.deb  

  autopoint_0.19.7-2ubuntu3_all.deb  

   libbamf3-2_0.5.3~bzr0+16.04.20160701-0ubuntu1_amd64.deb  

   bamfdaemon_0.5.3~bzr0+16.04.20160701-0ubuntu1_amd64.deb  

   compiz-core_0.9.12.2+16.04.20160714-0ubuntu1_amd64.deb  
libdecoration0_0.9.12.2+16.04.20160714-0ubuntu1_amd64.deb

---

### Post by howefield on 2016-11-13
I think that apts download option will do what you want, eg

```
sudo apt download cowsay
```

will download the cowsay package into the current working directory.

---

### Post by a.dusty.trail on 2016-11-13
nope it cant find the package

(treid with the first two packages listed)

apt download libsystemd0_229-4ubuntu7_i386.deb  
E: Unable to locate package libsystemd0_229-4ubuntu7_i386.deb
E: Couldn't find any package by glob 'libsystemd0_229-4ubuntu7_i386.deb'
E: Couldn't find any package by regex 'libsystemd0_229-4ubuntu7_i386.deb'


i can find them manually
[http://packages.ubuntu.com/uk/xenial-updates/i386/libsystemd0/download]("http://packages.ubuntu.com/uk/xenial-updates/i386/libsystemd0/download")

it need to be a specific package not just the newest

---

### Post by deadflowr on 2016-11-13
Unfortunately for you those package version most likely are gone from any Ubuntu repos.
As new versions of packages overwrite old versions

(Not that you get a new version of a particular package, per se, but rather you get the updated/patched version of the package.
Example, the original package was called silly-package-1-1, but the updated version is now silly-package-1-1b. The new b package will be the version now in the repos.
If that makes sense.

However, one way to possibly get those older packages is if you never cleaned your system with apt get autoclean or apt-get clean, then there is a chance you yourself actually have those packages in your own archive cache folder
(/var/cache/apt/archives)
If somehow you have those packages in the cached archive, you can copy the deb files somewhere like your Downloads folder, for safe keeping and install or reinstall those packages till the sun goes down.

Outside of that longshot, there is always the chance of grabbing the upstream source for the package and compiling the package on your system yourself.
But that's a ton of extra footwork.

---

### Post by jeremy31 on 2016-11-13
Why do you need these specific versions?  The only trace of libsystemd0_229-4ubuntu7_i386.deb I can find is that it once was in xenial-proposed.  There is a version 229-4ubuntu4 in the repos

---

### Post by CantankRus on 2016-11-13
> **jeremy31 said:**
> Why do you need these specific versions?  The only trace of libsystemd0_229-4ubuntu7_i386.deb I can find is that it once was in xenial-proposed.  There is a version 229-4ubuntu4 in the repos

I only found using google.
[https://launchpad.net/ubuntu/xenial/i386/libsystemd0/229-4ubuntu7](https://launchpad.net/ubuntu/xenial/i386/libsystemd0/229-4ubuntu7)

---

### Post by a.dusty.trail on 2016-11-13
dependences are hell for offline use.
i can see why windows is just easier....

theses are the dependencies that my off line computer requests for the applications that i am installing..


applications that i have downloaded and installed on this online system that im useing right now.
(which is fully updated once a month, just done 3 days ago)

no the files are not on this system. they never have been, i backup my /var/cache/apt/archives to try to avoid dependency messes like this.

but i still get dumped in dependency hell.

with no way out..

i hear that trueos  has a worked to fix dependency hell, maybe i should look at switching

---

### Post by jeremy31 on 2016-11-13
> **CantankRus said:**
> I only found using google.
[https://launchpad.net/ubuntu/xenial/i386/libsystemd0/229-4ubuntu7](https://launchpad.net/ubuntu/xenial/i386/libsystemd0/229-4ubuntu7)

I didn't see that page when I searched, just a launchpad page that had the source code files

a.dusty.trail

The easy route would be to get a USB wifi card that works with Ubuntu like the TP Link TL-WN722N 150 Mbps model

It still is unlikely to find that libsystemd0 package in that version

---

### Post by ian-weisser on 2016-11-14
Since you have both offline and online Ubuntu systems,
do you use apt-zip to manage the offline system?

Your version-hell seems self-inflicted. Online or offline doesn't matter - you are seeking obsolete versions of software. 

Example: snap-confine 1.0.38 was *never* in Ubuntu. It was in one PPA.  Versions 1.0.43 and 44 are the only versions ever appearing in Ubuntu.
(If you really want it, it's at downloadable [https://launchpad.net/~canonical-foundations/+archive/ubuntu/ubuntu-image/+packages](https://launchpad.net/~canonical-foundations/+archive/ubuntu/ubuntu-image/+packages) )

---

### Post by a.dusty.trail on 2016-11-14
no im not seeking anything
this is what ubuntu has said it needs to install software on the offline system,software that i have running on an identical online system.
(once again running fine and updated fully three days ago.)

do you think i choose each and every package based on the nightmare of dependences involved?
 sure its self inflicted if you consider i want to run an offline system as self inflicted
(i can see why windows and others just keep all the libraries for compatibility rather than brakeing everything each week)
other wise its all decided by ubuntu and apt.

you say some of these packages were never in ubuntu..

but UBUNTU is asking for them and refusing to use newer versions that i can get easily.

and no i dont have any other ppa's added.. as that just leads to more dependency hell

which i have been dealing with on and off for years with ubuntu.. i know better..


and thanks for suggesting..
[U]"The easy route would be to get a USB wifi card that works with Ubuntu like the TP Link TL-WN722N 150 Mbps model"

[/U]if there was any wifi where the system ran...that might work.. if i wanted an online system
(even though it lead title says quite clearly offline)

its nice to know that if you have problems with ubuntu the best that can be suggested is...  go online and let it work it self out..
which is just about and useful and someone telling you to hardreset your device and wipe it back to factory. 


maybe i should just install from scratch..
that is also a useless answer i could use..  
but if i do.. i will not be reinstalling ubuntu.


ubuntu is getting more and more buggy every year..
and its things like this that makes it impossible to use daily..

unless you only update twice a year.

and just to make things easy to understand..
i copy each and every package that is installed on the online system to the offline systems /var/apt/chace  or whatever.. and let synapic do the installs

---

### Post by jeremy31 on 2016-11-14
You could see the download URL of the packages with ```
apt-get install --print-uris package libsystemd0
```
It may point you to the version you want

---

### Post by ian-weisser on 2016-11-14
One easy answer, I'll say it again, is to use the apt-zip package.
I used it for years to maintain an offline system. Works great.
Before apt-zip, I maintained the offline system the hard way...the way you seem to be doing. Yes, it's very frustrating to manage packages manually. Been there.

If you don't want to use apt-zip, Synaptic can do something fairly similar for offline systems. That's another easy answer.

---

### Post by a.dusty.trail on 2016-11-17
apt-zip is not found by synaptic...

is it part of the official repos? 

the only thing i found was a old link to a download for 15.04
lastupdated in 2015

[https://launchpad.net/ubuntu/+source/apt-zip](https://launchpad.net/ubuntu/+source/apt-zip)

is it abandoned?
( or outdated like aptoncd,Keryx and other offline solutions that no longer work with out a massive headache, all last updated 4 years ago if your lucky)

---

### Post by ian-weisser on 2016-11-17
Ach, apt-zip was indeed abandoned after 15.10. What a shame.

My sincere apologies for directing you down the wrong path.

Nevertheless, Synaptic's download-script function does much the same thing.

---

