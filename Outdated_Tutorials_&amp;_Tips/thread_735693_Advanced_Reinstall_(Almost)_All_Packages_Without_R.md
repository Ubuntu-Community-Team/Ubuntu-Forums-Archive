---
title: "Advanced: Reinstall (Almost) All Packages Without Reinstalling All Of Ubuntu"
date: 2008-03-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Lumenary on 2008-03-25
[COLOR="Black"]**[SIZE="4"]Advanced: Reinstall (Almost) All Packages Without Reinstalling All Of Ubuntu[/SIZE]**[/COLOR]



[COLOR="Green"]**[SIZE="3"]What Does This Procedure Do?[/SIZE]**[/COLOR]


This procedure allows an advanced user or system administrator to perform a mostly unattended, automatic, batch-mode reinstallation of almost all packages that are already installed on a system.



[COLOR="Green"]**[SIZE="3"]When Should This Procedure Be Used?[/SIZE]**[/COLOR]


This procedure was designed to assist in the recovery of a damaged or compromised system.


For example, suppose a system has incurred damage to its system libraries because of a slowly failing hard drive.  Presuming the filesystems (partitions, volumes, etc.) have been imaged and transferred to a good, identical replacement drive, one may be able to use this procedure (described below) to replace corrupt packages with good ones.


Or, suppose an important system has suffered a security breach, and so the integrity of the installed packages can no longer be guaranteed.  One may be able to use this procedure to make sure that most of the installed packages came from a trusted source, such as an official Ubuntu repository.



[COLOR="Green"]**[SIZE="3"]When Should This Procedure NOT Be Used?[/SIZE]**[/COLOR]


Because the procedure described below is designed to replace almost every installed package on the system with a fresh copy, there is a chance that customized scripts and configuration files will be overwritten.  *Thus, users and system administrators should consider the effectiveness of other, more traditional system recovery options before using this procedure.*


:!: [COLOR="Sienna"]This procedure is dependent upon, at the absolute minimum, a bootable system with the following:[/COLOR]


[INDENT]1. A working network connection.[/INDENT]

[INDENT]2. Functional package management software (APT and Dpkg).[/INDENT]

[INDENT]3. An intact installed packages database.

[/INDENT]

[INDENT]If any of the above conditions cannot be met, then do not use this procedure.[/INDENT]


:!: [COLOR="Sienna"]This procedure presumes a good level of familiarity with all of the following:[/COLOR]


[INDENT]1. Basic system backup/restore procedures (in case things do not work as expected).[/INDENT]

[INDENT]2. Package management with APT and Dpkg.[/INDENT]

[INDENT]3. Command execution using the Bash shell.[/INDENT]

[INDENT]4. The location of important system libraries and log files.

[/INDENT]

[INDENT]If you are not confident in your ability to perform mid-level to advanced debugging of your Linux system, then do not use this procedure.[/INDENT]




[COLOR="Green"]**[SIZE="3"]On What Distributions Has This Procedure Been Tested?[/SIZE]**[/COLOR]


This procedure has been tested on:


[INDENT]1. Ubuntu, Gutsy Gibbon, 7.10.[/INDENT]

[INDENT]2. Xubuntu, Gutsy Gibbon, 7.10.[/INDENT]

[INDENT]3. Xubuntu with KDE added, Gutsy Gibbon, 7.10.[/INDENT]



[COLOR="Green"]**[SIZE="3"]Background:[/SIZE]**[/COLOR]


I came upon a request for assistance in reinstalling all of the packages on a system that had suffered some filesystem damage that was not corrected by Ext3 and/or ReiserFS journalling.


After searching far-and-wide for info on this topic, I managed to stumble upon a very simple Bash shell script, posted by Tod Detre to the debianHELP.org forums, that tackles a similar issue.


[INDENT]:!: [COLOR="Sienna"]Important: Do not equate simplicity with safety.  This procedure could (theoretically) reset important parts of your system configuration, requiring you to redo earlier work.[/COLOR][/INDENT]


I took the script I found and modified it slightly so that it is a bit less "draconian" with regard to package reinstallation. The original script completely purged and reinstalled each package; this could result in a loss of carefully-tweaked configuration files. (Which is not necessarily a Bad Thing, if that is what you want.) The modified script, presented below, uses the APT


[INDENT][COLOR="Blue"]--reinstall[/COLOR][/INDENT]


method instead, which should in most cases maintain each package's current configuration files.


Like the original, the modified script uses Dpkg and APT to iterate through and reinstall all packages that are listed as already installed by the package management database.


Because the script reinstalls packages one at a time, it isn't fast, but it does get the job done. On an Intel 2.4GHz Q6600 with 2GB of RAM, a fast SATA-II drive, and using Xubuntu Gutsy (32-bit) with KDE added, the script will reinstall anywhere from 350 to 800 packages per hour, depending on the size of the package cache and other factors.


Each package is installed individually; this gets around "package X pre-depends on package Y" errors.


Also, the script skips certain packages, namely:


[INDENT]APT- and Dpkg- related packages:
(You don't want the package manager and related software to change mid-stream.)[/INDENT]

[INDENT]MySQL- and MythTV- related packages:
(These packages don't seem to take too well to non-interactive configuration.)[/INDENT]


Feel free to add your own additional exception patterns to the


[INDENT][COLOR="Blue"]egrep[/COLOR][/INDENT]


command embedded within the script.



[COLOR="Green"]**[SIZE="3"]Usage:[/SIZE]**[/COLOR]


To use the script, follow the steps below:


**Step 0:** Backup all of your data.  (This is a prerequisite for *any* procedure that performs global changes to a system.)


**Step 1:** Open a Bash command shell, and clear out the downloaded packages cache with a


[INDENT][COLOR="Red"]sudo apt-get clean[/COLOR][/INDENT]


command.


**Step 2:** Using Synaptic (or your preferred package management tool), download, _but do not install_, fresh copies of all packages currently installed on the system.


[INDENT][COLOR="Sienna"]:!: Note: Have your original installation CD-ROM handy; the package management utilities may ask for it.[/COLOR]

[/INDENT]

[INDENT][COLOR="Sienna"]:!: Important: Make sure you update the package repository list(s) before beginning the download.[/COLOR][/INDENT]


**Step 3:** Open a plain text editor, and copy/paste the following code:


```
[COLOR="Blue"]#!/bin/bash

for pkg in `dpkg --get-selections | awk '{print $1}' | egrep -v '(dpkg|apt|mysql|mythtv)'` ; do apt-get -y --force-yes install --reinstall $pkg ; done
[/COLOR]

```


[INDENT]
:!: [COLOR="Sienna"]Important: The commands "[COLOR="Blue"]for pkg ... done[/COLOR]" should all be on the same line.[/COLOR][/INDENT]


**Step 4:** Save the file with an appropriate name, such as:


[INDENT][COLOR="Blue"]reinstall_all.sh[/COLOR][/INDENT]


**Step 5:** Open a Bash shell, change the script's owner to "root", and make it executable:


[INDENT][COLOR="Red"]sudo chown root:root reinstall_all.sh
sudo chmod 755 reinstall_all.sh[/COLOR][/INDENT]


**Step 6:** Execute the script:


[INDENT][COLOR="Red"]sudo ./reinstall_all.sh[/COLOR]

[/INDENT]


[INDENT]:!: [COLOR="Sienna"]Important: Once the script completes:[/COLOR]

[/INDENT]


[INDENT]If you are using proprietary drivers for an nVIDIA or ATi video card, or are running a vendor-provided (as opposed to Ubuntu-provided) copy of VMware, you will probably need to re-run the appropriate driver configuration utility in order to ensure the driver integrates properly with the installed kernel.[/INDENT]



[COLOR="Green"]**[SIZE="3"]Attributions:[/SIZE]**[/COLOR]


The above package reinstallation script is based upon the solution presented by Tod Detre on debianHELP.org at 2007-09-20 17:00:

[INDENT][[COLOR="Blue"]http://www.debianhelp.org/node/10487[/COLOR]]("http://www.debianhelp.org/node/10487")[/INDENT]

---

### Post by SqRt7744 on 2009-06-26
Thanks, this really helped me. I'm in Germany, and due to a power out in Toronto a small business server I manage went down and when it came back up it wasn't working properly - there were some damaged system files. I was able to reinstall all packages this way, and restored the owner's home directory from the command line sbackup tool. Luckily I set up daily backups with sbackup. Everything could be done with simple ssh access and gnu screen. This was done on Ubuntu 9.04. The only hick-up was that I had to manually reinstall the nvidia-glx-180 package.

Another small note: in preparation I also did a bit more clean-up
sudo apt-get autoremove
sudo apt-get autoclean
computer-janitor find
computer-janitor cleanup
orphaner

I removed the few 3rd Party packages that were installed and not available from repositories and reinstalled them manually after the end (there were only 3 or 4 of oddballs)

---

### Post by farbird on 2009-06-30
this is a good guide..

---

### Post by Daniel G. Taylor on 2009-08-24
Many thanks - this script is just what I was looking for to help me in debugging an issue I'm having on a single laptop.

---

### Post by Lumenary on 2009-12-12
Hello Everyone,



Sorry I haven't been around to say "You're Welcome"...  Work has been taking a lot of what should be free-time lately.


Anyways, I'm glad that the little snippet of code I cribbed from Tod - and then tweaked - helped out; it took me quite a lot of digging to find such a simple and elegant solution...  :-)

---

### Post by ALIENDUDE5300 on 2010-05-15
Hey... a while back I wrote a guide to reinstall all packages based on your method, just wanted to say thanks for the starting point, and post a link to my thread: [http://ubuntuforums.org/showthread.php?t=1407060](http://ubuntuforums.org/showthread.php?t=1407060)

---

