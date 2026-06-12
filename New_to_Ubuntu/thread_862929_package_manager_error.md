---
title: "package manager error"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by Unotforme on 2008-07-18
The package manager is teeling me I have an error. I'm not sure how to fix it. I tried running sudo get-apt update, this is what I get:
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing scim-gtk2-immodule (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I've tried a few of the other apt-get commands, but I keep getting the same error.

I recently downloaded a driver for my ati radeon card, so I'm not sure if this had any effect on the resulting error.

---

### Post by SunnyRabbiera on 2008-07-18
maybe, sometimes errors like this crop up if you have two package managers running at the same time...
try a restart to start out with.

---

### Post by Unotforme on 2008-07-18
I've restarted my system, started up Synaptic package manager, and this is what I get:

E: Problem parsing dependency Depends
E: Error occurred while processing scim-gtk2-immodule (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I'd remove the video driver, but how can I do that when I can't get into Package manager?

---

### Post by SunnyRabbiera on 2008-07-18
hmm, any errors if you run apt-get update in a terminal?

---

### Post by Unotforme on 2008-07-18
It runs through a few of the Hit http:// ( I just listed a few here), then wham! Errors...

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing scim-gtk2-immodule (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

### Post by SunnyRabbiera on 2008-07-18
It might be an apt issue then, I have seen errors like this before but they are usually easy to fix.
It might be a dpkg issue by the looks of it, very common.
Try posting the output of sudo dpkg --configure -a

---

### Post by Unotforme on 2008-07-18
What would you suggest? I'm very new to Linux, so I'm unsure where to go from here?

---

### Post by SunnyRabbiera on 2008-07-18
try the command I suggested first
sudo dpkg --configure -a
the kind of error you are having is something I see often, but its normally nothing to worry about.

---

### Post by Unotforme on 2008-07-18
This is what I get:

larry@home-desktop:~$ sudo dpkg --configure -a
[sudo] password for larry: 
dpkg: parse error, in file `/var/lib/dpkg/status' near line 12972 package `scim-gtk2-immodule':
 `Depends' field, reference to `libcairo2': error in version: version string is empty

---

### Post by SunnyRabbiera on 2008-07-18
Now for the driver for your ati radeon card, how did you get it?

---

### Post by Unotforme on 2008-07-18
I went under system>admin>hardware drivers. I was actually looking for my printer, and the hardware drivers showed me an updated driver for my video card, so naturally :oops: I selected it.

---

### Post by SunnyRabbiera on 2008-07-18
it could very well be the source of your issues, I have heard stuff like this happen...
Ati has crap linux support so I am not surprised.
I am not entirely sure on how to fix your issue but at least i gave you some starting points... hopefully someone with a similar issue will come along and help.

---

