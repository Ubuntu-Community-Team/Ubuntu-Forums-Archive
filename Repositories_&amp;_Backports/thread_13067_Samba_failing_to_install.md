---
title: "Samba failing to install"
date: 2005-01-28
forum: Repositories &amp; Backports
---

### Post by UrbanSlayer on 2005-01-28
Repost from the Software forum, since i realised this is more appropriate - 

Ive just installed Ubuntu on my laptop, ive had it on my desktop for a while and didnt have a problem with installing samba, however I just tried to install it using just the main and universe repo's in my sources list, and got this - 

mizuho@shinobu: $ sudo apt-get install samba 
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
samba: Depends: samba-common (= 3.0.7-1ubuntu6) but 3.0.7-1ubuntu6.3 is to be installed
E: Broken packages

Ive run apt-get update several times, and ive waited a couple of days inbetween trying.

Ive tried using multiverse as well, and have browsed round these forums looking for a reason as to why it says the packages are broken, but I am unsure. Can anyone help?

These are my sources - 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe multiverse

Thanks

---

