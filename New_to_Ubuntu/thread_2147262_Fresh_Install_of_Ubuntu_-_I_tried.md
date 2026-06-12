---
title: "Fresh Install of Ubuntu - I tried"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by Killah on 2013-05-21
I am running 10.10 and have decided to do a fresh install to 13.04. Problems I have encountered:

**I am looking before to backup my files using apt-get install deja-dup and this was unsuccessful because:**
vanessa@kw:~$ apt-get install deja-dup
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

**So I went to root.**
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  duplicity deja-dup
Install these packages without verification [y/N]? y
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/universe duplicity i386 0.6.10-0ubuntu1
  404  Not Found [IP: 91.189.91.14 80]
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/universe deja-dup i386 16.1.1-0ubuntu1
  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/d/duplicity/duplicity_0.6.10-0ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/d/duplicity/duplicity_0.6.10-0ubuntu1_i386.deb) 404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/d/deja-dup/deja-dup_16.1.1-0ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/d/deja-dup/deja-dup_16.1.1-0ubuntu1_i386.deb) 404  Not Found [IP: 91.189.91.14 80]
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

**I followed the instructions of running apt-get update**:
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release        
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources        
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages  
  404  Not Found
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
E: Some index files failed to download, they have been ignored, or old ones used instead.

**So I tried to fix the sources:**


Nano and then possibly changing the ca. to us. Then save then exit.

Sill I am not able to

I tried running apt-get --fix-missing source...but it is now asking me to specify the source to fetch..which I do not know. 

Bottom line: Before I can do the fresh install I need to back up my settings and clearly I have encountered issues.

Help :)

---

### Post by verymadpip on 2013-05-21
Hi there.
I think this may be related to 10.10 being EOL (End Of Life).
Perhaps back up your data to external media (CDs, DVDs, external hard drive or the like), then try again.
I'm unsure if you'll actually be able to install any software given the age of the release you have.

I'm really unsure about this, so perhaps you should wait for some more definite advice.

Good luck.

---

### Post by ibjsb4 on 2013-05-21
For starters you need to use old-release sources.

[https://help.ubuntu.com/community/EOLUpgrades#Upgrade](https://help.ubuntu.com/community/EOLUpgrades#Upgrade)

Could you not just create another partition for 13o4 and transfer your files to it?

---

### Post by Killah on 2013-05-28
So..after a few days of going back and forth and trying to figure it out...I have finally been able to install deja-dup in order to back up my files. Half through the interface and half through commands....I added the EOL sources list but since I had trouble doing it through terminal I did it through the Synaptic Package Manager. Then once those were added to the repositories I was able to reload and the continue to update the update manager and then the kernels and then finally installed deja-dup. So Im back to square one!!! But at least I figured out how to go round and round! Oh you have to love learning linux :)

Thanks for the help my friend.

---

### Post by mastablasta on 2013-05-29
round and round? if you upgraded your system when promted or on time you might have less issues. also since you don't mind staying with old release why not just use LTS (Last one was 12.04) and then upgrade every 2 or 5 years? especially since new cycle for releases between LTS is shorter now that it was.

---

### Post by mastablasta on 2013-05-29
round and round? if you upgraded your system when promted or on time you might have less issues. also since you don't mind staying with old release why not just use LTS (Last one was 12.04) and then upgrade every 2 or 5 years? especially since new cycle for releases between LTS is shorter now that it was.

---

### Post by Killah on 2013-06-01
Thank you for your input. i will take it into consideration.

Reading up on backing up my files I cam across some other info:

When I first installed Ubuntu 10.10 I created the following partitions

/home
/root
/swap
/tmp
/usr
/var
/opt
/var/log
/pics
/music
/multimedia
with an additional 37.5 unallocated. 

Can I install the distro without necessarily doing a back-up? Is it even necessary for me to save current settings when everything is already partitioned?

---

### Post by Killah on 2013-06-01
Nothing is working on this install. I have tried every which way to upgrade / install fresh and I cant even do that. I ddl 12.04ltd. bured the image on a dvd. all the files are on the dvd. I tested it on my other laptop running windows and it asks me install. When I put the dvd in my other desktop and i reboot (the boot sequence has already been changed and adjusted to dvd) nothing happens. it goes straight to 10.10.

I tried accessing the files. I see the file, I try to click on the executable file wubi.exe and I get the following:

Archive:  /media/Ubuntu 12.04.2 LTS i386/wubi.exe
[/media/Ubuntu 12.04.2 LTS i386/wubi.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/Ubuntu 12.04.2 LTS i386/wubi.exe or
          /media/Ubuntu 12.04.2 LTS i386/wubi.exe.zip, and cannot find /media/Ubuntu 12.04.2 LTS i386/wubi.exe.ZIP, period.

I tried other ways:

sudo apt-get install update-manager-core

vanessa@kw:~$ sudo apt-get install update-manager-core
[sudo] password for vanessa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
vanessa@kw:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

[FONT=consolas, 'Courier New', courier, monospace]-------> ok this is new...

Can someone please advise me....[/FONT]

---

### Post by presence1960 on 2013-06-01
Did you try another bootable DVD/CD in the offending machine? You need to find out if the optical drive is the problem.

---

### Post by Paqman on 2013-06-02
> **Killah said:**
> 
When I first installed Ubuntu 10.10 I created the following partitions

/home
/root
/swap
/tmp
/usr
/var
/opt
/var/log
/pics
/music
/multimedia
with an additional 37.5 unallocated. 


That's a pretty complicated partitioning scheme. I get the idea of having some of your data seperated, but is there any particular reason you've got partitions for things like /root, /tmp, /usr, /var, /opt and another one for /var/log? You might find it much easier and more space-efficient to just keep all those on your / partition.

As for your trouble with the DVD, have you checked that it burned ok? [Run an MD5 hash]("https://help.ubuntu.com/community/HowToMD5SUM") on the disk, and see that it [matches what it should]("http://releases.ubuntu.com/precise/MD5SUMS").

---

### Post by speartip on 2013-06-02
Killah...
You will always encounter problems when using an out of date unsupported operating system.
My advise.
Copy all your important files/folders to an external source/partition.
Download a 12.04lts iso from here.
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)
Burn to disc or better still, use unetbootin & burn to usb.
boot from that media & install.
As paqman says, your setup looks too complicated to me.
3 partitions are best to use:
/
/home
/swap
Then copy all your files/folders back to your new o/s.

---

### Post by presence1960 on 2013-06-02
> **speartip said:**
> Killah...
You will always encounter problems when using an out of date unsupported operating system.
My advise.
Copy all your important files/folders to an external source/partition.
Download a 12.04lts iso from here.
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)
Burn to disc or better still, use unetbootin & burn to usb.
boot from that media & install.
As paqman says, your setup looks too complicated to me.
3 partitions are best to use:
/
/home
/swap
Then copy all your files/folders back to your new o/s.

read post #7 and you will see she is trying a clean install of a current version of Ubuntu. The DVD works in another computer. So I believe the problem is her optical drive, not the DVD.

---

### Post by speartip on 2013-06-02
> **presence1960 said:**
> read post #7 and you will see she is trying a clean install of a current version of Ubuntu. The DVD works in another computer. So I believe the problem is her optical drive, not the DVD.

Which is why I also advised to use unetbootin & boot from usb.

---

### Post by MidnightGrey on 2013-06-03
> **Killah said:**
> 

When I first installed Ubuntu 10.10 I created the following partitions

/home
/root
/swap
/tmp
/usr
/var
/opt
/var/log
/pics
/music
/multimedia
with an additional 37.5 unallocated. 


Wait.. Killah did you really create 11 partitions? Or did you mean you created folders in "/"??

---

