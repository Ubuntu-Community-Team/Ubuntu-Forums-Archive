---
title: "ppa or not ppa this is the question"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by Houmie on 2012-06-06
Hi,

I have here two questions, 

first I would like to install Mercurial on Ubuntu 12.04.  How do I see which version of Mercurial is included in my distribution?

Second looking at their website I can't figure out which ppa is the one for the latest release (most stable).

On very top it says: 

This PPA is one of a group of three providing packages of Mercurial:

[provides packages of the latest Mercurial release.]("https://launchpad.net/~mercurial-ppa/+archive/releases?field.series_filter=precise")

Well, and how do I add this ppa then?

And then there is another section in the middle

[Adding this PPA to your system]("https://launchpad.net/~mercurial-ppa/+archive/releases?field.series_filter=precise")

But then it gives a warning:

[COLOR="Red"]You can update your system with unsupported packages from this untrusted PPA by adding ppa:mercurial-ppa/releases to your system's Software Sources. [/COLOR]

It doesn't sound very comforting adding a PPA to my production server after all.  What alternatives do I have?

At the end of the day I am going to install Hg (Mercurial) on my server and need to be sure the security holes are stuffed, or I would expose the source code and the server to the hackers.

So what strategy do you recommend?

Thank you,
Houman

---

### Post by traditionalist on 2012-06-06
I would be very very careful with PPA's.  I just blew one machine away with something downloaded from a PPA, not immediately, but when it updated. Shot the kernel down completely and was not recoverable. A couple of important software packages also failed before that.  No more PPA's for me unless they are backed by a few reputable posters here or something similar.

You could try compiling the source yourself? If you can get a .deb package they seem to be less dangerous as they don't update automatically, but you still have to test them, and best not on a production machine.

They have deb packages here;

[http://mercurial.selenic.com/wiki/Download](http://mercurial.selenic.com/wiki/Download)

but I don't know anything at all about them.

---

### Post by Enigmapond on 2012-06-06
I've been adding and using PPA's for many years with no adverse effcts. You need to do this in the terminal and that message with stop. It needed the public key:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key 323293EE
```

---

### Post by ptn107 on 2012-06-06
v2.2.2 is the latest stable, so the PPA is already outdated.  It's available in the Ubuntu repositories for the 'Q' release in Oct 2012.  You can download it for precise without the use of a PPA (which tend to create problems down the road).  You will need both mercurial and mercurial-common for your architecture.

32-bit files
_[mercurial-common_2.2.2-1]("http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mercurial/mercurial-common_2.2.2-1_all.deb")_
_[mercurial_2.2.2-1]("http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mercurial/mercurial_2.2.2-1_i386.deb")_

or

64-bit files
_[mercurial-common_2.2.2-1]("http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mercurial/mercurial-common_2.2.2-1_all.deb")_
_[mercurial_2.2.2-1]("http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mercurial/mercurial_2.2.2-1_amd64.deb")_

Now pop open a terminal and go to the folder you saved the files in and run:
```
sudo dpkg -i *.deb
```

---

### Post by d4m1r on 2012-06-06
It depends on your need. I for one add PPA's for applications that don't work well out of the gates so I can get the latest and great versions as soon as they are available. For other applications, I specifically disable updates for and DON'T add their PPA's to my system because either I like the older version of the software available in the Ubuntu repo's, or a specific older version is just more stable.

As for a production server environment, I would shy away from PPA's unless they are truly needed, solely based on stability and security concerns.

---

### Post by Houmie on 2012-06-06
> **ptn107 said:**
> v2.2.2 is the latest stable, so the PPA is already outdated.  It's available in the Ubuntu repositories for the 'Q' release in Oct 2012.  

Thanks everyone for the comments. I can see your points.

@ptn107 - you have mentioned that the 'Q' release of Ubuntu in Oct 2012 would automatically offer the latest Mercurial version? I didn't know canonical would actually update the applications. I was under the impression that they only provide you with security patches to existing software only.

If that means that I can get the latest mercurial from Oct 2012 simply by doing a **sudo apt-get update** without the need of adding any additional PPA, I think that's the safest solution, isn't it?

EDIT:

ahhh, with Q you mean Quetzal, which won't be LTS anymore though.
I think the whole idea of LTS is though to keep the apps as they are - hence stable. Maybe I would defeat the idea by adding a PPA after all.  

I just wonder if keeping the current Mercurial version for years to come is a wise decision...

---

### Post by teward on 2012-06-06
Regarding PPAs:
 
 
As someone who works upstream with some packages, I'd like to point out a few things about PPAs, since I also maintain a few:
 
[LIST=1]
[*]PPAs are ***not supported by Canonical***.  Having this been said, certain teams, such as the GNOME team, or the NGINX team, or other teams for upstream projects may maintain PPAs.  While those are marginally more trustworthy, they may break your system.
[*]Only use PPAs if you trust the source of the PPA.  If you do not trust the source of the PPA, ***do not use it***.  Having said this, if you were looking for, say, the latest nginx version (nginx is a web server), I'd point you to the PPAs, because its maintained by the nginx team (i'm on that team).  It's still your call whether to trust it or not.
[/LIST]Personally, unless you really need the PPA, or because multiple people are using it without incident, I'd not touch the PPA, and just stick to the repos or backports.
 
 
As for your 'mercurial' thing, I can't confirm/refute that, I just wanted to give the two-cents on PPAs.

---

### Post by idoitprone on 2012-06-06
> **Houmie said:**
> Thanks everyone for the comments. I can see your points.

@ptn107 - you have mentioned that the 'Q' release of Ubuntu in Oct 2012 would automatically offer the latest Mercurial version? I didn't know canonical would actually update the applications. I was under the impression that they only provide you with security patches to existing software only.

If that means that I can get the latest mercurial from Oct 2012 simply by doing a **sudo apt-get update** without the need of adding any additional PPA, I think that's the safest solution, isn't it?

EDIT:

ahhh, with Q you mean Quetzal, which won't be LTS anymore though.
I think the whole idea of LTS is though to keep the apps as they are - hence stable. Maybe I would defeat the idea by adding a PPA after all.  

I just wonder if keeping the current Mercurial version for years to come a wise decision...

there is a difference between distro version and lastest release
apt-get update only refreshes the package management cache

ppa allows you to get the latest and greatest version

distro updates are only bug fixes and security fixes

mercurial is not a program that needs to be the latest and greatest
dont bother with a ppa because you might get headache with incompatibilities in the future
besides you are running the latest ubuntu
you already have the latest and greatest

---

### Post by Houmie on 2012-06-06
Thanks guys for explaining it. I decided to stick with the mercurial that comes with 12.04 LTS version.

I think what I had misunderstood was that [this PPA provider]("https://launchpad.net/~mercurial-ppa/+archive/releases?field.series_filter=precise") is not the mercurial team itself, rather it is a PPA provided my someone from community. Hence there is no guarantee.

Mercurial [website]("http://mercurial.selenic.com/downloads/") seems not to offer any PPA. Hence I stick with 12.04 LTS for now.

---

