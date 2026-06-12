---
title: "The package system is broken"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by ritarebollo on 2012-10-10
Hello all,

I installed Ubuntu a month or so ago and it was running quite well until last week. I have a "stop sign" on my task bar and when I click on it the update manager open. I can t do any updates because I get this error :

The following packages have unmet dependencies:

libc6: Depends: libc-bin (= 2.15-0ubuntu10) but 2.15-0ubuntu10.2 is installed
libc6-dev: Depends: libc6 (= 2.15-0ubuntu10.2) but 2.15-0ubuntu10 is installed
           Depends: libc-dev-bin (= 2.15-0ubuntu10.2) but 2.15-0ubuntu10.2 is installed

It is suggest to do apt-get install - f but I get this

media@maisonmedia:~$ sudo apt-get install -f
[sudo] password for media: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
1 not fully installed or removed.
Need to get 0 B/3,935 kB of archives.
After this operation, 20.5 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

Should I type yes or no? Is this going to erase data on my computer? Sorry if this seems all super dumb questions! If you can help me figure it out it would be great. I read some things and most of them suggest a Ubuntu re install?

And... I also went to software manager and tried a repair. I get this :
installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
(Reading database ...  
dpkg: warning: files list file for package `libc6' missing, assuming package has no files currently installed. 
 (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 225575 files and directories currently installed.) 
Preparing to replace libc6 2.15-0ubuntu10 (using .../libc6_2.15-0ubuntu10.2_i386.deb) ... 
 
A copy of the C library was found in an unexpected directory: 
  '/lib/i386-linux-gnu/libc-2.15.so' 
It is not safe to upgrade the C library in this situation; 
please remove that copy of the C library or get it out of 
'/lib/i386-linux-gnu' and try again. 
 
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.2_i386.deb (--unpack): 
 subprocess new pre-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.2_i386.deb 
Error in function:  
dpkg: dependency problems prevent configuration of libc6-dev: 
 libc6-dev depends on libc6 (= 2.15-0ubuntu10.2); however: 
  Version of libc6 on system is 2.15-0ubuntu10. 
dpkg: error processing libc6-dev (--configure): 
 dependency problems - leaving unconfigured 

Help please!!

Also, since I am here, I have a problem when watching videos (any type, streaming, cds...). They seem jumpy. Any ideas?

Thank you

Rita

---

### Post by DuckHook on 2012-10-11
I'm afraid that this one might be a tough one.

Firstly, run:

```
sudo apt-get install -f
```

again but this time, answer yes "Y" when you are asked if you want to proceed. The -f switch just forces apt to fix broken dependencies and won't do any harm.

If you still can't upgrade, please post the output to this forum again, just as you have done here.

If this is coming up in a brand new install, it may make sense to just re-install. However, don't spend the time re-installing until we at least try a few other things first and especially so if you've already done some work and have some data on your machine.

BTW, my compliments on providing so much info. It really helps us to help you.

---

### Post by pissedoffdude on 2012-10-11
Are you running the latest Ubuntu, 12.04?

I can't really tell because of that 10.2!

Again, try sudo apt-get -f.  If you can't get it to work, here's a list of things you can do:

1) sudo dpkg --configure -a
2) sudo dpkg-reconfigure -phigh -a
3) sudo apt-get install libc6-bin && sudo apt-get install lib6
4) google your error, see what other people recommend, and try to learn about the commands so that you can know what you're doing BEFORE you execute it, in case it might makes things worse (I don't mean this in an angry way!)

Also, your error looks like it's anti the 10.2 version of that library.  Did you install software from or add any non-official repositories lately?  If you did, then you can probably search for those packages in synaptic (libc6 ones) then downgarde them to the ones from the official repos.

---

### Post by ritarebollo on 2012-10-11
Hi again!

Thanks for the quick reply. I did the sudo apt-get install -f again and got this :

media@maisonmedia:~$ sudo apt-get install -f
[sudo] password for media: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
1 not fully installed or removed.
Need to get 0 B/3,935 kB of archives.
After this operation, 20.5 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `libc6' missing, assuming package has no files currently installed.
(Reading database ... 225575 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10 (using .../libc6_2.15-0ubuntu10.2_i386.deb) ...

A copy of the C library was found in an unexpected directory:
  '/lib/i386-linux-gnu/libc-2.15.so'
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library or get it out of
'/lib/i386-linux-gnu' and try again.

dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

So it seems the -f really doesn t work right?

As for the Ubuntu specifications : Ubuntu 12.04 LTS

1)

media@maisonmedia:~$ sudo dpkg --configure -a
[sudo] password for media: 
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.15-0ubuntu10.2); however:
  Version of libc6 on system is 2.15-0ubuntu10.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev

2) the reconfigure command
I'm trying this now. I guess if the package needs to be reconfigured it may take a while (I googled it). So I'll see what happens later and will keep you posted.

I don t think I have installed any non official repositories but who knows! I had read that already and tried to install synaptic, which I don t have, but I can't because Software manager doesn t allow me to... gives the same error as I posted before.

Thanks for the help, I ll try the 2) and 3) and keep you posted
Rita

---

### Post by pissedoffdude on 2012-10-11
Let's try to do what the apt-get -f error is telling us to do: remove that file.

First back it up in case of anything:
```

sudo cp /lib/i386-linux-gnu/libc-2.15.so ~/libc-2.15.so
```

Remove it with:
```
sudo rm /lib/i386-linux-gnu/libc-2.15.so
```

Then re-run sudo apt-get -f.  If you get the same error about another file, repeat this process (but change the name of the file of course)

---

### Post by ritarebollo on 2012-10-11
Ok, weird :

media@maisonmedia:~$ sudo cp /lib/i386-linux-gnu/libc-2.15.so ~/libc-2.15.so
[sudo] password for media: 
media@maisonmedia:~$ sudo rm /lib/i386-linux-gnu/libc-2.15.so
media@maisonmedia:~$ sudo apt-get -f
sudo: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
media@maisonmedia:~$ sudo apt-get install -f
sudo: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
media@maisonmedia:~$ 

for info the 2) didn t give me anything

Should I try 3) or get that  libc-2.15.so file back?

---

### Post by pissedoffdude on 2012-10-11
Try 3) and see if you can get it back via apt-get

If it fails, then that's why we backed it up, so you can restore it like this:

```
sudo cp ~/libc-2.15.so /lib/i386-linux-gnu/libc-2.15.so
```

By the way, try the last thing I mentioned afterwards(I should have said 5! lol).  Oh, and can you also post the output of cat /etc/apt/sources.list (run sudo cat /etc/apt/sources.list if it's anti displaying it)

---

### Post by ritarebollo on 2012-10-11
So, the computer crashed! Just after posting the last message. I turned on and I m in a recovery screen where I can chose the OS to boot. If I chose ubuntu, with Linux 3.2.0-31-generic pae I get a screen with an error : error while loading shared libraries: libc.so.6: cannot open shared object file: no such file or directory
Followed by plenty of command lines

I m going to bed so I ll try to take care of this tomorrow night! Thanks for the help and hopefully we ll figure it out!

Rita

---

### Post by pissedoffdude on 2012-10-11
> **ritarebollo said:**
> So, the computer crashed! Just after posting the last message. I turned on and I m in a recovery screen where I can chose the OS to boot. If I chose ubuntu, with Linux 3.2.0-31-generic pae I get a screen with an error : error while loading shared libraries: libc.so.6: cannot open shared object file: no such file or directory
Followed by plenty of command lines

I m going to bed so I ll try to take care of this tomorrow night! Thanks for the help and hopefully we ll figure it out!

Rita

Luckily we backed up the file, so we can restore it easily.  If you get dropped to command line, let me know exactly what it says.  Assuming you mount your root partition, see if you can run the command from my previous post.  Otherwise, you be dropped to a terminal where it tells you to mount the root file system.  For now, keep this goal in mind: you want to restore that libc6 file you backed up.  This can either be done via the command line you're given or pretty easily through a livecd or usb (graphically by running the file manager, mounting your Ubuntu install, then running gksudo nautilus).  I'm probably going to be busy due to school tomorrow, so if I don't get back to you in time, keep that goal in mind

---

### Post by ritarebollo on 2012-10-11
Hello hello,

Ok, it worked! I'll try to fix the initial problem now! 


Also, I couldn t try the "last thing you mentioned" on your first post because I couldn t find synaptic on my ubuntu version (and I can t install it since ubuntu is not working!).

for 3)
media@maisonmedia:~$ sudo apt-get install libc6_bin && sudo apt-get install lib6[sudo] password for media: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libc6_bin

Thanks again!

---

### Post by pissedoffdude on 2012-10-12
Try again with a hy-phen instead of an under_score.  So weird it's anti-that version though.  Can you post your sources list? (Instructions in one of my prev posts)

---

### Post by ritarebollo on 2012-10-12
media@maisonmedia:~$  sudo apt-get install libc6-bin && sudo apt-get install lib6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libc6-bin
media@maisonmedia:~$ 

And

media@maisonmedia:~$ sudo cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

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

---

### Post by pissedoffdude on 2012-10-12
Okay, I am confused! Sorry, but from what I see, it's complaining about wanting to install the 10.2 version, which is not installed, because 10 is installed.  Before we continue, just to confirm, you've ran "sudo apt-get update, and then sudo apt-get upgrade?"  If you have, then see if you can apg-get -d libc.  This will download the libraries you want (that is, it will download the libc package etc, afterwards it will give you a .tar.gz package, which you can extract, then extract all to the appropriate directories)  But before you do this, again, BACK EVERYTHING UP.  If you're confused on how to do this, let us know, otherwise, back everything up, and try extracting the latest versions of the libc packages for your  Ubuntu version.  

And, if anyone is reading this, please suggest something if you can! Regardless of the issue, at least you're gaining valuable linux resources out of it :P, haha!

---

### Post by ritarebollo on 2012-10-21
Hey! Sorry for my late reply, I got a huge week of work.
So :

media@maisonmedia:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.15-0ubuntu10) but 2.15-0ubuntu10.2 is installed
 libc6-dev : Depends: libc6 (= 2.15-0ubuntu10.2) but 2.15-0ubuntu10 is installed
E: Unmet dependencies. Try using -f.

So I guess it doesn t give me the tar file...
I think I m going to dowload ubuntu again and re install. Do you have any suggestions where  can get it? I could use the same cd I used the first time but I think something new may be better.

And last, any idea how I could make videos less jumpy?

Thanks

Rita

---

### Post by NikTh on 2012-10-21
Hi , 

this is my opinion and only my opinion. 
If you brake the libc6 package , then the re-installation is close enough. 
libc6 is a very-very essential package , are the libraries of almost all packages in the system. 
If I was in your situation I would re-install Ubuntu from a LiveCD-USB , without mark the box for formating the drive (so I would not lose my personal data). 
Think about it. 

Thanks

---

