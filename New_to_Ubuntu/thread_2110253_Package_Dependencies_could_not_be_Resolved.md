---
title: "Package Dependencies could not be Resolved"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by PeterVenn on 2013-01-29
Hi,

I'm a total newbie to Ubuntu which I installed a few days ago, I like it a lot but when I try to install WINE and a couple of other things I get this:

"This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is a virtual package"

I'm afraid I have absolutely no idea what this means.  I researched online and have tried entering the following commands using the Terminal box:

"First clean & update

 	Code:
 	sudo apt-get clean && sudo apt-get update 
Then post the full output of 

 	Code:
 	sudo apt-get upgrade"


I also got as far as doing this:  

"Go to synaptic package manager.
Edit > Fix broken Packages."

... Neither worked, can anyone help me?

---

### Post by omeomi on 2013-01-29
Have you enabled all the repositories in Software Sources?

---

### Post by PeterVenn on 2013-01-29
Hi, I think so  (all the boxes are ticked under 'Other Sources')?

I found on another thread that someone else was having the same sort of problem with an AMD 64 bit machine, which is what I'm using.  Something to do with:

"Multiarch i386"

[http://ubuntuforums.org/showthread.php?t=2100827](http://ubuntuforums.org/showthread.php?t=2100827)

It's all Greek to me though I'm afraid. 

Any assistance appreciated

---

### Post by Cheesehead on 2013-01-29
> **PeterVenn said:**
> 
wine1.4: PreDepends: dpkg (>= **1.15.7.2**~) but **1.16.7ubuntu6** is to be installed

Here is what it means: You are trying to install a version of Wine for the wrong release of Ubuntu.

Take a look at this (edited) list of versions of Wine:
```
me@me:~$ rmadison dpkg
Looking for package "dpkg". Checking in Ubuntu...
dpkg is currently in the Ubuntu repositories
      dpkg | 1.15.5.6ubuntu4 |         lucid | source, amd64, armel, i386, ia64, powerpc, sparc
      dpkg | 1.15.5.6ubuntu4.5 | lucid-security | source, amd64, armel, i386, ia64, powerpc, sparc
      dpkg | 1.15.5.6ubuntu4.6 | lucid-updates | source, amd64, armel, i386, ia64, powerpc, sparc
      dpkg | 1.16.0.3ubuntu5 |       oneiric | source, amd64, armel, i386, powerpc
      dpkg | 1.16.0.3ubuntu5.1 | oneiric-updates | source, amd64, armel, i386, powerpc


      dpkg | 1.16.1.2ubuntu7.1 | precise-updates | source, amd64, armel, armhf, i386, powerpc
```

There are two really good clues here.

1) The version your system is looking for, 1.15.7.2, most closely matches Lucid (Ubuntu 10.04) or Oneric (Ubuntu 11.10). But it doesn't quite match either. So you may be using a quite old -but still supported- version of Ubuntu. Or you may be using a version of Ubuntu that has reached end-of-life and is no longer supported. Or possibly you are using a version of Ubuntu that is simply not updated. Or possibly a PPA version of wine.

2) The version your system is choking on, 1.16.7ubuntu6, matches Precise (Ubuntu 12.10). So whatever older version of Ubuntu you are running, you are trying to install 12.04 packages onto it...and that won't work.

There are two possibilities. Either you are using an older version of Ubuntu, and are mistakenly trying to install 12.04 packages onto it...or you are running 12.04, and are mistakenly trying to install some obsolete or PPA version of Wine onto it.

Go into System Settings --> Software Sources, and uncheck (disable) all PPAs and non-Ubuntu repositories. PPAs are a common source of package manager breakage. That is why they are not supported software.

Next, uncheck (disable) all Ubuntu repositories that don't match the current version of Ubuntu that you are running. 11.10 cannot use 12.04 repos, nor can 12.04 use 11.10 repos. Mismatched repositories are a less-common source of package manager breakage, but easy to do if you unknowingly follow obsolete instructions discovered online.

Finally, open a terminal and try
```
sudo apt-get update
sudo apt-get upgrade
```

Post all error messages here.

After your package manager is working again -not before!-, tell us what you want to install, and we can tell you how to install it properly.
For example, wine is simple:
```
sudo apt-get install wine
```

---

### Post by squakie on 2013-01-29
12.10 = Quantal, Precise is 12.04 lts. ;)

---

### Post by PeterVenn on 2013-01-30
Hi guys,

Thanks for the input.  Sorry if I didn't make it clear, I've just installed Ubuntu 12.10.  It's my first contact with Ubuntu so I went straight for the newest version.  I would have expected the version of WINE on Software Centre to work?

From my research, the problem (knowing nothing about computers, I might add) seems to be something to do with the fact that AMD A8 I am using is a 64 bit machine, and WINE runs 32 bit programs... and there is an issue surrounding a compatibility feature called Multiarch.   

I've looked at loads of threads but it's not apparent what the actual solution is.  

(I don't have Windows by the way!)

Hmmmm...

---

### Post by gordintoronto on 2013-01-30
Run Software Centre and install multiarch-support.

---

### Post by squakie on 2013-02-01
I have a 64-bit AMD processor (FX 8120) and installed Wine via synaptic package manager.  It runs fine.  It may be something specific to your particular processor - I don't know.

Perhaps you tried to initially install Wine from somewhere other than the Ubuntu repositories?

At any rate, if it's still not working, this is what I would do:

[LIST]
[*]completely reverse what you tried to do to install.  It may be as simple as sudo apt-get remove wine
[*]try reinstalling Wine from the synaptic package manager
[*]if any error messages show, copy and paste them back in a reply here.
[*]post back the contents of /etc/apt/sources.list - we can check to be sure it is pointing to the correct version as someone mentioned earlier.
[/LIST]
Did you do anything to the software source prior to trying to install Wine?

---

### Post by NikTh on 2013-02-01
Hi , 
can you open a terminal (CTRL+ALT+T) and post back here some results ? 

```
dpkg --print-foreign-architectures
dpkg --print-arcitecture
find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
lsb_releace -rcd ; uname -r
```_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by grahammechanical on 2013-02-01
I have been using wine for four or five years. I have never had a problem installing wine using either the instructions from the wine.hq web site or using the Software Centre. I have wine installed on 12.04 and as a test I just installed wine using the Software Centre on my 13.04 development release. It installed without any problems.

Did you install the Microsoft Windows Compatibility Layer (meta package) or the Wine Windows Program Loader? It should not make much difference. Both have the same size download file and both install wine 1.4

By the way, once you get wine installed you will find at least 3 wine utilities in the Dash, Browse C: Drive; Configure Wine & Uninstall Wine Software. To install a Windows program in wine you open Uninstall Wine Software. When it opens it becomes Add/Remove Programs with an Install button. Click on that and you can browse to the programs setup.exe file and install just like under Windows.

Regards.

---

### Post by grahammechanical on 2013-02-01
I have been using wine for four or five years. I have never had a problem installing wine using either the instructions from the wine.hq web site or using the Software Centre. I have wine installed on 12.04 and as a test I just installed wine using the Software Centre on my 13.04 development release. It installed without any problems.

Did you install the Microsoft Windows Compatibility Layer (meta package) or the Wine Windows Program Loader? It should not make much difference. Both have the same size download file and both install wine 1.4

By the way, once you get wine installed you will find at least 3 wine utilities in the Dash, Browse C:Drive; Configure Wine & Uninstall Wine Software. To install a Windows program in wine you open Uninstall Wine Software. When it opens it becomes Add/Remove Programs with an Install button. Click on that and you can browse to the programs setup.exe file and install just like under Windows.

Regards.

---

### Post by squakie on 2013-02-01
Or right click on the install program and select run with wine.

---

