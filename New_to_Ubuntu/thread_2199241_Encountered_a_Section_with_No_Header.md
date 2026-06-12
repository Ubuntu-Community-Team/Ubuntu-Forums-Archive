---
title: "Encountered a Section with No Header"
date: 2014-01-12
forum: New to Ubuntu
---

### Post by connor.ruebusch on 2014-01-12
I've seen several problems similar to this on the forums, but I don't have a good enough grasp of the terminal yet to infer and apply those fixes to this one. When I attempt to run update-manager from the terminal (as well as when I attempt to do other tasks) I get the following error:  'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_gwendal-lebihan-dev?cinnamon-stable_ppa_ubuntu_dists_precise_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'  I'm sure this isn't as complicated as it seems to me... so thanks for your help!

---

### Post by Bashing-om on 2014-01-12
connor.ruebusch; Hi !

That error condition is generally due to a corrupted control file, to remove the file(s) and rebuild them:
Terminal codes:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```

Run these and advise us of your status.

[INDENT][INDENT]ain't nothin' but a thing
[/INDENT][/INDENT]

---

### Post by connor.ruebusch on 2014-01-12
After sudo apt-get update I received the following messages. 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease: File /var/lib/apt/lists/partial/ppa.launchpad.net_gwendal-lebihan-dev?cinnamon-stable_ppa_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_gwendal-lebihan-dev?cinnamon-stable_ppa_ubuntu_dists_precise_main_source_Sources  Encountered a section with no Package: header

W: Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu/dists/precise/main/i18n/Index](http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/ppa.launchpad.net_gwendal-lebihan-dev?cinnamon-stable_ppa_ubuntu_dists_precise_main_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.


Then I ran apt-get upgrade and got this: 

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_gwendal-lebihan-dev?cinnamon-stable_ppa_ubuntu_dists_precise_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

Update manager still won't work.

---

### Post by Bashing-om on 2014-01-12
connor.ruebusch; Well, now;

That might be a horse of another color.
1. Makes me wonder if cinnamon is a version mismatch of the version of ubuntu you are running.
2. Maybe you have not got the keys on your system to authenticate cinnamon ?
Let's look:
```

lsb_release -a
ls -la ~/.gnupg
cat /etc/apt/sources.list.d/*.list

```

That should provide enough info to look deeper.

[INDENT][INDENT]if at first you do not succeed 
[INDENT][INDENT][INDENT]try again (sky diving excepted !)[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by connor.ruebusch on 2014-01-21
Hey, thanks for your help by the way. I didn't say thank you before, I just realized. 

Anyway, here are the lines of code followed by the message I receive after entering them. 

For:
lsb_release -a 

I received:

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise

For:

ls -la ~/.gnupg

I received:


total 24
drwx------  2 connor connor 4096 Dec 25 23:11 .
drwxr-xr-x 27 connor connor 4096 Jan 12 21:20 ..
-rw-------  1 connor connor 9398 Dec 25 23:11 gpg.conf
-rw-------  1 connor connor    0 Dec 25 23:11 pubring.gpg
-rw-------  1 connor connor    0 Dec 25 23:11 secring.gpg
-rw-------  1 connor connor   40 Dec 25 23:11 trustdb.gpg

For:

cat /etc/apt/sources.list.d/*.list

I received:


deb [http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu) precise main
deb [http://asus.archive.canonical.com/updates](http://asus.archive.canonical.com/updates) precise-annan public
deb-src [http://asus.archive.canonical.com/updates](http://asus.archive.canonical.com/updates) precise-annan public

---

### Post by Bashing-om on 2014-01-21
connor.ruebusch; Well,

What I do not know is not making a lot of sense right now ! Cinnamon is supported for your installed version, and the PPA is valid.

what returns from terminal code:
```

ls -la /var/lib/apt/lists/partial/ppa.*

```
Meanwhile I am looking to find the location of the 3rd party gpg keys ! sheeshh, forgot where they are !

[INDENT][INDENT]I be work'n
[/INDENT][/INDENT]

---

### Post by connor.ruebusch on 2014-02-14
Thing is, I don't think I'm running Cinnamon. I believe I downloaded the file because I was planning to switch to Linux Mint, but I didn't have a working DVD burner at the time, so I couldn't actually install. Could that be donking things up at all?

That code gave the folowing response:

-rw-r--r-- 1 root root 2320 Jan 12 22:32 /var/lib/apt/lists/partial/ppa.launchpad.net_gwendal-lebihan-dev?cinnamon-stable_ppa_ubuntu_dists_precise_main_i18n_Index
-rw-r--r-- 1 root root 2320 Jan 12 22:32 /var/lib/apt/lists/partial/ppa.launchpad.net_gwendal-lebihan-dev?cinnamon-stable_ppa_ubuntu_dists_precise_main_source_Sources
-rw-r--r-- 1 root root 2320 Jan 12 22:32 /var/lib/apt/lists/partial/ppa.launchpad.net_gwendal-lebihan-dev?cinnamon-stable_ppa_ubuntu_dists_precise_main_source_Sources.decomp.FAILED

Thanks again.

---

### Post by Bashing-om on 2014-02-15
connor.ruebusch; Hello,

Yeah, looks as if that partial install of cinnamon is the root of the problem.

Let's see what we can do to clean things up; starting with the sources list file(s).
Post back the outputs of terminal codes:
```

cat /etc/apt/sources.list 
cat /etc/apt/sources.list.d/*.list

```
And then we can look about removing cinnamon from the system.

Identify a process
[INDENT][INDENT]follow through
[/INDENT][/INDENT]

---

### Post by connor.ruebusch on 2014-02-15
Alright, first code gave me this: 

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main


deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner



Second code returned this: 

> deb [http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu) precise main
deb [http://asus.archive.canonical.com/updates](http://asus.archive.canonical.com/updates) precise-annan public
deb-src [http://asus.archive.canonical.com/updates](http://asus.archive.canonical.com/updates) precise-annan public



Thanks again for your help!

---

### Post by Bashing-om on 2014-02-15
connor.ruebusch; Well,
This:
> 
deb [http://ppa.launchpad.net/gwendal-leb...ble/ppa/ubuntu](http://ppa.launchpad.net/gwendal-leb...ble/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/gwendal-leb...ble/ppa/ubuntu](http://ppa.launchpad.net/gwendal-leb...ble/ppa/ubuntu) precise main

Is the source of the problem, we have to deal with,

I have outdoor chores I must attend to, so be a while before I can get back to this.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by connor.ruebusch on 2014-02-15
I believe in you! 

I still might switch to Mint in the future, simply because I'm more comfortable with a Windows-esque layout. Would this same forum be a good place to go for advice on how to do that? And do I need a DVD of the install, or is there another way to go about it?

---

### Post by Bashing-om on 2014-02-15
connor.ruebusch; Hey,

Faith is a good thing !

Let's try this approach and see how far we get.
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get purge cinnamon
sudo apt-get autoremove

```
If all that goes well, look and see what cleanup remains:
```

ls -la /etc/apt/sources.list.d/

```
As I am not completely sure that the "fetches" will be removed by the above. Bet that must be done manually, AFTER all else is removed.

For a  "Windows-esque layout" try Lubuntu. a much simpler and lighter desk top environment.
As to Mint. sure, we not only do ubuntu, but any linux distribution ! However the knowledge base may be somewhat limited.
As to weather Mint will fit on a CD, can not advise; The lighter releases of 'buntu will fit on a CD. The CD/DVD is my preferred method to install, but, there are several others.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by connor.ruebusch on 2014-02-27
Got an error message on the very first line of code. 

> Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_gwendal-lebihan-dev?cinnamon-stable_ppa_ubuntu_dists_precise_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.



---

### Post by ibjsb4 on 2014-02-27
Hi :)

[http://ubuntuforums.org/showthread.php?t=2190797&p=12860782&viewfull=1#post12860782](http://ubuntuforums.org/showthread.php?t=2190797&p=12860782&viewfull=1#post12860782)

---

