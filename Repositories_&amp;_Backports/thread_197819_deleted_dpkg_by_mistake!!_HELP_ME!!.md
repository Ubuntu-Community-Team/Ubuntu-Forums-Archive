---
title: "deleted dpkg by mistake!! HELP ME!!"
date: 2006-06-16
forum: Repositories &amp; Backports
---

### Post by arpitp on 2006-06-16
hi guys..
i have deleted my dpkg file by mistake. what should i do now?

please help as soon as possible. this is urgent becoz i m not being able to run apt-get at all.

I tried copying the dpkg file of some other computer. But the error that i am getting is as given below:

[COLOR="Red"]arpit@flicker:~$ sudo apt-get install ubuntu-sounds
Reading package lists... Done
Building dependency tree... Done
ubuntu-sounds is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)[/COLOR]

what should i do now??
i have tried reinstalling dpkg as well..But then it says 407 authentication failed as given below:

[COLOR="Red"]arpit@flicker:~$ sudo apt-get install dpkg --reinstall
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1866kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  dpkg
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main dpkg 1.13.11ubuntu6
  407 Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu6_i386.deb)  407 Proxy Authentication Required
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/COLOR]

even though the settings in my apt.conf are perfect and i have the proxy at all places set up correctly but i m not being able to do anything.
Please please please help me!!

---

### Post by avender on 2006-06-16
Your solution is simple. U just deleted dpkg right ?

Download dpkg debian package from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Extract.

Copy dpkg to  /usr/bin/

That's it.. :)

---

### Post by iason86 on 2008-11-05
i have about the same problem. it started when i left synaptic to install some libraries when the power went down after that when i open synaptic and after entering my passwd i have this screen appeared 

[[IMG]http://img442.imageshack.us/img442/3104/screenshotsynapticez6.th.png[/IMG]](http://img442.imageshack.us/my.php?image=screenshotsynapticez6.png)

does anyone know what i have to do?

---

### Post by chenel on 2008-11-05
The first thing to try is opening a terminal and typing
```
sudo dpkg --configure -a
```
like the message suggests.  Hopefully that'll fix things -- probably a package just didn't get completely extracted or configured when the power went out.  If not, post what the output of the command is and we'll see where to go from there.

---

### Post by iason86 on 2008-11-06
you where right thanks a lot _o_
i have tried the command before but with not sudo in front :\
i learn while i live!

---

### Post by Kevbert on 2008-11-06
If you installed from CD, the .deb file will be there, in the /pool/main/d/dpkg directory. Just copy to your PC and then double click on it to install.

---

### Post by chenel on 2008-11-06
> **iason86 said:**
> you where right thanks a lot _o_
i have tried the command before but with not sudo in front :\
i learn while i live!

Ah, yes.  dpkg is only allowed to be run by the superuser: that's why it only works with sudo.  Glad it's working now :)

---

### Post by rajhanschinmay on 2010-04-18
Dear all,

I am facing the same problem.
I am shown exactly error code 100.
I tried all the steps mentioned above.

- Reinstalling the software from CD.
- Configuring the dpkg package.

None seem to work.

Any more solutions?
Please reply me if you need output of any command. I am ready to give you any info required. But please solve the problem.


Thanking you,
Yours
Chinmay

---

### Post by Bachstelze on 2010-04-18
Boot a live CD, download the dpkg DEB package for your architecture, mount your Ubuntu root partition and do something like

```
sudo dpkg -x dpkg*.deb /mnt/
```

It should install all the necessary files so you can chroot into your Ubuntu installation and do a *bona fide* reinstallation of the dpkg package.

---

