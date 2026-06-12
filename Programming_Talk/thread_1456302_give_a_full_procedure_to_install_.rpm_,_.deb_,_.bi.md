---
title: "give a full procedure to install .rpm , .deb , .bin and .tar.gz files in ubuntu 9.10"
date: 2010-04-17
forum: Programming Talk
---

### Post by smitpatel24 on 2010-04-17
give a full procedure to install .rpm , .deb , .bin and .tar.gz files in ubuntu 9.10

i have downloaded packages of some softwares in .rpm  , .deb , .bin and .tar.gz file-format

help me to install
:(

---

### Post by slavik on 2010-04-17
1. No
2. No
3. See #1 and #2
4. There are search engines which you can use to find howtos
5. Use Synaptic/apt/aptitude/software center to install things.

---

### Post by lisati on 2010-04-17
> **slavik said:**
> 1. No
2. No
3. See #1 and #2
4. There are search engines which you can use to find howtos
5. Use Synaptic/apt/aptitude/software center to install things.

:lolflag:

/me resists urge to suggest one of the "forbidden" commands.

---

### Post by steinzeitmensch on 2010-04-17
My apologies lisati on behalf of smitpatel24 and slavik.
These 2 guys do not represent the overall helpful people who keep this forum going.
I like you are somewhat new to the world of Linux and often have stupid simpleton questions.
The know-it-all geeks who smirk and sneer at us as we try to grapple with this fantasitc but often confussing SW world called 'open source' do a huge disservice to all their fellow geeks who want to liberate the world from tyrannical, profit driven SW vendors.

I too like you have a problem with installing a .tar.gz file. In my case it is Open office which I cannot install using the usually reliable and simple to use 'Ubuntu Software Center'.
I am no computer idiot and have had Linux on my computer for a year or so now with generally good experiences, but I am starting to loose patience with trying to get this thing installed and working.
I run a business and need OO to work!. I, seemingly unlike the arrogant geeks who responded to your post have a goal which lies beyond the installation. This step is not my destination so I do not want to spend my Sat morning f---king around with it.

So slavik or smitpatel24, if it is so stupidly easy to perform this task that you deem it so distantly below your esteemed pedastals to assist with, and if there is such a multitude of resources just a mouseclick through google's portal away, then I ask you to take 27 milliseconds out of your day to post a link here to such an 'idiots' guide to installing a .tar.gz in Ubuntu

Remember idiots guides do not contain such text as:

> please 'unset' the SESSION_MANAGER environment variable inside the shell you use to start OpenOffice.org. This can be done by adding the line "unset SESSION_MANAGER" to the beginning of the soffice shell script found in the "[office folder]/program" directory.

To about 80% of us who use computer, this is almost gobblygook that aims to make the search for the answer the goal of our Sat morning instead of the annoying  hiderance which is preventing us from doing something truly fun on Sat afternoon!

---

### Post by geirha on 2010-04-17
deb-files are easy to install. You just double-click them to open gdebi, and then click on the install button, however stand-alone deb files are not signed by Ubuntu developers. When you install a package from the repositories, those also come as deb-packages, but they are signed by the Ubuntu developers, giving you assurance that they do not contain malware.

rpm-files. These are packages meant for other linux distributions, and other linux distributions typically do things differently than Ubuntu. That means that along with the issue of malware mentioned earlier, an installed rpm package may not work, or even hose your system because it expects certain files to be at location A, while ubuntu keeps them at location B, or it overwrites some files it did not know was there. With that in mind, some rpm-packages can be converted to deb-packages using the alien tool, and then installed as a deb-package.

bin-files. This can be anything. Usually they are self-extracting archives; you run a bin-file, it extracts an embedded .tar.gz-file, and asks you where to install the program it contains. Installing under /opt should be the safest choice, but the issue of malware is of course still an issue.

tar.gz-files. These are plain compressed archives, like a .zip file for windows. They can contain anything, a program, source code, someone's photo album, whatever. The only way to know is to see what files it contains. If it's a program, either source or pre-built, it usually contains one or more files named something like README, README.txt, readme.txt, INSTALL, INSTALL.txt, etc..., which contains information on what it is, and instructions on how to install it.

So to save yourself the trouble when wanting to install some software, always search the package repositories first. Applications -> Ubuntu Software Center. If you don't find it there, look for a PPA that has it. [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

@steinzeitmensch, I think you've mixed up the nicks.

---

