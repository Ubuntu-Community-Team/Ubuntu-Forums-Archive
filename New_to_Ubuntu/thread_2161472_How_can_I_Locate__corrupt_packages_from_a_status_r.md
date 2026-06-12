---
title: "How can I Locate  corrupt packages from a status report"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by ro12 on 2013-07-10
[COLOR=#333333][FONT=UbuntuRegular]How can I locate the corrupt package, and [/FONT][/COLOR]**remove the whole block of information about it**[COLOR=#333333][FONT=UbuntuRegular] and save the file from a status file and how can I copy and paste the file as it's quite long.
Thank you[/FONT][/COLOR]

---

### Post by Cheesehead on 2013-07-11
The description of your problem is confusing.
Normally, you redownload and reinstall a corrupt package.
There is no 'status report' by that name or intent.

Are you having problems locating a corrupt package?
Or are you having problems fixing a corrupt package you have located?

---

### Post by ro12 on 2013-07-12
Hi ,I am having problems finding and fixing broken packages. I am unable to fix them in synaptic.

---

### Post by Cheesehead on 2013-07-13
1) Quit all package managers, including Synaptic and Software Center
2) Open a Terminal.
3) Enter this command: sudo apt-get update
4) Enter this command, *and paste the entire reply here*: sudo apt-get upgrade

The system will tell you what is broken in the error messages...Of course, Synaptic tells you what the packages are if you use the filter setting.

Broken packages are usually caused by a PPA or other unsupported third party repository, or a partial-upgrade (which is usually also caused by a PPA). If you have installed any PPAs, disable them and try the commands again.

---

### Post by deadflowr on 2013-07-13
> **ro12 said:**
> Hi ,I am having problems finding and fixing broken packages. I am unable to fix them in synaptic.

If you open synaptic and go to custom filters, broken is a selection you can choose(right after ALL).
If you have any broken packages they will be listed here.

---

### Post by ro12 on 2013-07-13
When I try to fix broken packages in synaptic I get this```
 Extracting templates from packages: 100%Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 27728 package 'rar':
 mixed non-coinstallable and coinstallable package instances present
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: parsing file '/var/lib/dpkg/status' near line 27728 package 'rar':
 mixed non-coinstallable and coinstallable package instances present



```

---

### Post by Cheesehead on 2013-07-13
According to [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015567](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015567) , this can happen if a wrong-arch package gets installed. A solution is in there, too.

First, try reinstalling the 'rar' package.
Disable any PPAs you have installed. Then:
```
sudo apt-get clean rar    # delete the existing copy(ies) of the rar package in your local archive
sudo apt-get --reinstall install rar    # download a new copy of rar and reinstall.
```

---

### Post by ro12 on 2013-07-19
What is the rar package  and how can I find and disable ppa's?
Thank you for your help

---

### Post by deadflowr on 2013-07-19
The rar package is an archiver for .rar files.

To disable PPAs, In synaptic
Settings > Repositories > Other Software.
Look for any lines that say PPA.
Uncheck them.
Then close and reload the package list.

Run Cheesehead's commands.

---

### Post by awmoles1 on 2013-10-18
I think what they are asking is this.....
sudo gedit /var/lib/dpkg/status
How would you locate the corrupt package in the text file. At least that is what I have been trying to figure out

---

