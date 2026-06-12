---
title: "Package build-essential is not available"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by paulm2008 on 2008-07-23
Good Afternoon.

I'm very new at Linux.  But I'm now getting good at re-installing both Vista and ubuntu [vista once/ubuntu 3 times]

Following an attemp to install ndiswrapper, where I was kindly infomed by the make process that a number .h include files were not found stdlib.h etc... I was informed that I needed to install a package names build-essential.  I assume this produces a file identifying the locations of various libraries reuired to be included during compilation.  

Having re-built the ubuntu installation.  I opened a terminal window and typed the following command

sudo apt-get install build-essential

A message

package build-essential is not available, but is referred to by another package...
...package build-essential has no installation candidate

Does this mean that I'm required to install something else before I can install build-essential ?

Any ideas as to what's going wrong here ?

I think I need a more simplitic guide i.e. the one before Linux for dummies !!

Regards

Paul

PS I dwonloaded ubuntu from the web - copies ISO to CD - and booted via CD to install.
PPS Is the problem related to the 64bit installation - should I give up with this and stick with 32 ?

---

### Post by OldTimeTech on 2008-07-23
try sudo apt-get build essential without the hyphen or go to synapic package manager and type in search build essential, should be the first package shown and install from there.

---

### Post by LaRoza on 2008-07-23
No, build-essential is the name of the package. It is even on the CD...

```

sudo apt-get update && sudo aptitude install build-essential

```

Copy and paste that.

---

### Post by Heinzelotto on 2008-07-23
> **paulm2008 said:**
> 
PPS Is the problem related to the 64bit installation - should I give up with this and stick with 32 ?

build-essential contains the basic development tools. If those weren't available for 64-bit linux... :D

This is a strange error, normally build-essential should install without problems on a standard ubuntu installation.

first, do a "apt-cache search build-essential", which looks in the package database for the string "build-essential".
If you don't find the package there, please post your "/etc/apt/sources.list" file here. In this file there is information about where your package manager gets his software from. Sometimes you have to enable some additional software-repositories first.

---

### Post by OldTimeTech on 2008-07-23
Forgive me LaRoza...your right...it does have the hyphen

---

### Post by Potatoj316 on 2008-07-23
Ive had problems installing build-essential before, I fixed it by using this command
```
sudo aptitude install build-essential
```
aptitude is similar to apt-get but is a little smarter.

---

### Post by paulm2008 on 2008-07-23
Thank you all for your reply's.

I do not know of any other forum where member's respond instantly to problems/issues - Amazing.

I will review the above posts and see if I can make progress - I will keep you informed either way, but if I have further problems I will provide the source.list information.

Kind Regards

Paul

---

### Post by estyles on 2008-07-23
A note: even if you get build-essential installed okay, I recommend trying to get ndiswrapper from the repositories.  It's on the CD, I believe, so you should be able to get it even if you have no internet connection.  I know that most guides suggest compiling ndiswrapper from source, but IMHO that's a bad idea - it doesn't check dependencies, and IIRC, there were other dependencies than just build-essential when I mistakenly tried to compile it before realizing it was in the repos.  Only try installing from source *after* you try getting it from the repositories.

---

### Post by paulm2008 on 2008-07-23
Good Evening,

Again I appologies for any stupidity on my part.

But I assumee by repositories - I may be wrong - is this the area accessed by the add/remove program facility.  If so when I find the correct package in the list it simply ststes that the package cannot be installed.  When I highlight/enable it there is  little timer type icon which keeps running round and round until I close the application.

I also tried to generate the build-essential package using the command

sudo aptitude install build-essential

The screen dump for this is given below

paul@paul-desktop:~/ndiswrapper-1.53$ sudo aptitude install build-essential

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      

No candidate version found for build-essential
No candidate version found for build-essential

The following packages have been kept back:
  ssl-cert 

0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Need to get 0B of archives. After unpacking 0B will be used.

Writing extended state information... Done

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      



Therefter I tried to install ndiswrapper, I have added

.
.
.

statements to represent line and line of error messages which to keep the post small !! I have removed

paul@paul-desktop:~/ndiswrapper-1.53$ sudo make

make -C driver
make[1]: Entering directory `/home/paul/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.24-19-generic M=/home/paul/ndiswrapper-1.53/driver

make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'

  Building modules, stage 2.

  MODPOST 1 modules

make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

make[1]: Leaving directory `/home/paul/ndiswrapper-1.53/driver'

make -C utils

make[1]: Entering directory `/home/paul/ndiswrapper-1.53/utils'

gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c

loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
.
.
.
.
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory

In file included from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,

                 from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,

                 from loadndisdriver.c:28:

/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory

loadndisdriver.c:29:19: error: ctype.h: No such file or directory
.
.
.
.
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory

In file included from loadndisdriver.c:37:

../driver/loader.h:28: error: expected specifier-qualifier-list before &#8216;size_t&#8217;

loadndisdriver.c: In function &#8216;load_file&#8217;:

loadndisdriver.c:67: error: &#8216;size_t&#8217; undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
.
.
.
.
.
.
.
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:590: warning: implicit declaration of function &#8216;closelog&#8217;

make[1]: *** [loadndisdriver] Error 1

make[1]: Leaving directory `/home/paul/ndiswrapper-1.53/utils'

make: *** [all] Error 2

paul@paul-desktop:~/ndiswrapper-1.53$

Any help in sorting this out would be most appreciated.  Currently everytime I try and do anything it goes wrong - ubuntu does not even recognise my usb flash pen now - it used too

Kind Regards

Paul

---

### Post by estyles on 2008-07-23
Those errors you are getting when trying to build ndiswrapper are missing libraries and headers.  Those are source code files that are installed by build-essential, and would be needed to build *anything* from source.  As I said in my last post, you're better off installing ndiswrapper from the repositories.  To do this in terminal, type ```
sudo apt-get install ndiswrapper-utils-1.9
```  (edited the above, based on Requin's post, to avoid confusing you more than is necessary)

However, if you're having trouble using apt-get for build-essential, then we have a different problem.  Please post the contents of your "/etc/apt/sources.list" file here.  You can get this by browsing to the directory and opening it, or by typing ```
gedit /etc/apt/sources.list
```

You might want to try typing "sudo apt-get install" and hit tab twice, it will tell you how many packages are available and ask if you want to list them all (you don't, trust me).  If it comes up with around 32000, then you are able to see the repositories, if not, then again, it should have something to do with your sources.list.

---

### Post by RequinB4 on 2008-07-23
> **estyles said:**
>  To do this in terminal, type ```
sudo apt-get ndiswrapper
```  Before hitting enter, you might want to hit tab and see - I don't remember for sure, but ndiswrapper might be in the repos as something like ndiswrapper-1.53 or something like that.  Hitting tab will look for acceptable matches.

The package name is ndiswrapper-utils-1.9
```

sudo apt-get install ndiswrapper-utils-1.9

```

The package is also available on the LiveCD, so technically you don't need access to the repos (just have the CD in the drive)

---

### Post by paulm2008 on 2008-07-23
Hello,

I attempted the command you suggested, see below - Sorry this is another long thread !!

paul@paul-desktop:~$ sudo apt-get ndiswrapper-utils-1.9
E: Invalid operation ndiswrapper-1.53

The contents of source.list are also provided below

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to

# newer versions of the distribution.

deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy main restricted

deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy universe

deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates universe

deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

# deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

I appreciate the help - Thank you very much

Kind Regards

Paul

---

### Post by estyles on 2008-07-23
> sudo apt-get ndiswrapper-utils-1.9

should be

```
sudo apt-get install ndiswrapper-utils-1.9
```

edit: Note: this assumes you either have internet access or have the Ubuntu CD in the drive.

---

### Post by paulm2008 on 2008-07-23
Thanks, As you may have realised your communicating with a complete novice here - Thank you for your time - I will re-boot and try again.  But why cannot I actually compile and link the package, I thought build-essential would have sorted out the required paths for the headers and include statements

Kind Regards

Paul

---

### Post by estyles on 2008-07-23
> **paulm2008 said:**
> Thanks, As you may have realised your communicating with a complete novice here - Thank you for your time - I will re-boot and try again.  But why cannot I actually compile and link the package, I thought build-essential would have sorted out the required paths for the headers and include statements

Kind Regards

Paul

One possible reason: do you have internet access on the machine you're trying to install?  I tend to assume that anyone trying to install a package has an internet connection.  In the case of ndiswrapper, this is sometimes a bad assumption - it's quite possible for you to be connected via an ethernet cable while trying to get your wireless working, but some people are not.  If you aren't connected, then you could only get build-essential if it's on the CD (and I personally have no idea if it is or not).

Trust me, I'm definitely a newb - but I try to help out in the cases where I kind of know what I'm talking about - give back to the community which has definitely helped me out a lot.  You'll notice that I gave you a bad commandline for apt-get...  :confused:  Sorry about that.  Usually I try to check for sure before posting to make sure I didn't forget something or make a typo, but I'm at work and in Windows...  Anyway, good luck with the wireless - it's one of the more annoying things to get working in Ubuntu.

---

### Post by paulm2008 on 2008-07-24
Hello,

The on-going saga of the wireless adaptor.

I have now managed to install the ndiswrapper package, by double clicking on the file on the download CD I produced - this seems to have worked.  I also have "Installed" the wg111v3.inf driver using ndiswrapper.  But there appear to be a problem.  Basically when I go into

Windows Wireless Drivers

It lists the driver wg111v3

and states that the hardware is present - all good [I think !!]

However when I then goto Network, the wireless option is not listed, onlt 2 wired options + Point-to-Point connection.  I guess something's not quite right.  

any further assistance would be appreciated - I feel it's probably almost there.

Also the usb wireless adaptor does not actually show any sign of life - it usually flashes when it alive

Regards

Paul

---

### Post by paulm2008 on 2008-07-24
Good Afternoon and Hello,

The on-going saga of the wireless adaptor.

I have now managed to install the ndiswrapper package, by double clicking on the file on the download CD I produced - this seems to have worked. I also have "Installed" the wg111v3.inf driver using ndiswrapper. But there appear to be a problem. Basically when I go into

Windows Wireless Drivers

It lists the driver wg111v3

and states that the hardware is present - all good [I think !!]

However when I then goto Network, the wireless option is not listed, onlt 2 wired options + Point-to-Point connection. I guess something's not quite right. 

any further assistance would be appreciated - I feel it's probably almost there.

Also the usb wireless adaptor does not actually show any sign of life - it usually flashes when it alive

Regards

Paul

---

### Post by Oldsoldier2003 on 2008-07-24
I've merged your second thread into the main thread, please dont repost the same message with a similar title as a new thread. If you would like to gain visibility on your issue by starting another thread, it is best to use a title that explains the current issue instead of the original issue.

---

### Post by estyles on 2008-07-24
Copied this from another thread.  In particular, I think it might be the modprobe line.  If that doesn't help, try searching the forums for "ndiswrapper essid".  I remember having to set an essid when I set up my wife's wireless card.  It was a while ago, so I don't remember it exactly.  If you're still having trouble, I'll check her computer when I get home and see if I can find anything to help.

> 
```
ndiswrapper -l
```

(to list all your drivers that have been installed.
(There shouldn't be anything there)
then, copy all the .sys and .inf files from the windows driver cd, into another folder in your home folder.
then type:

```

cd ~/folder that has your driver
sudo ndiswrapper -i [your inf file]
sudo ndiswrapper -l

```

now it should say:
driver installed, device present

```
sudo ndiswrapper -m
sudo modprobe ndiswrapper

```

that should start the driver, and in a few minutes, you'll have a working internet connection.


---

### Post by paulm2008 on 2008-07-24
Hello, I think you are correct, something's not quite right here.  When I typed the command

sudo modprobe ndiswrapper

it came up with an error

FATAL: module ndiswrapper not found

Oh dear look's like I'm back to square 1 !!

Thanks for the info, any further advice would be appreciated

Thank You

Paul

---

