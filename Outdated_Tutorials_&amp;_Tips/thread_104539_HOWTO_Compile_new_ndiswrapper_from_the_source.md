---
title: "HOWTO: Compile new ndiswrapper from the source"
date: 2005-12-16
forum: Outdated Tutorials &amp; Tips
---

### Post by foxy123 on 2005-12-16
**[COLOR="Red"]THIS TOPIC IS OUTDATED[/COLOR]**
The version in the repositories is 1.1 which is a bit outdated. So I decided to update it to a current version. I hope it may help someone. This HOWTO is based on ndiswrapper [Wiki Page]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/InstallDebian")

1. Install kernel headers:
```
sudo apt-get install linux-headers-$(uname -r)
```
and dependencies:
```
sudo apt-get install dh-make fakeroot gcc-3.4 build-essential
```

2. Download the current version of ndiswrapper from [here]("http://sourceforge.net/project/showfiles.php?group_id=93482")

3. Untar 
```
tar xvfz ndiswrapper-[current version].tar.gz
cd ndiswrapper-[current version]
```

4. Build deb packages:
```
fakeroot debian/rules binary-modules
fakeroot debian/rules binary-utils
cd ..
```

5. Install
```
sudo dpkg -i ndiswrapper-modules-[your kernel]_[current version]-1_i386.deb ndiswrapper-utils_[current version]-1_i386.deb
```

That's it. I installed it over an old version available from repositories but if you want to do a clean install then uninstall the previous version and remove old dirs:
```
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
```
Taken from ihavenoname's post [here]("http://www.ubuntuforums.org/showpost.php?p=571571&postcount=34") 

I may have left some dependencies, since I did not have a fresh Breezy installation.

**[COLOR="Red"]THIS TOPIC IS OUTDATED[/COLOR]**

---

### Post by nelposto on 2005-12-17
Hi, thanks for this HOWTO.

I have a question before I try .. will this work with custom compiled kernels?

In this case would I change the line:

 linux-headers-$(uname -r) 

to linux -headers-$ and then the kernel on which my custom one is based?

Thanks for this.

---

### Post by curtis on 2005-12-18
If you compiled the kernel your self, the headers are already there.
You can build seperate kernel headers if you want though...

---

### Post by Lambert on 2005-12-24
You may want to add to your instructions all the packages needed to complete this howto.

dh_make
fakeroot
gcc-3.4
build-essential

---

### Post by greenway on 2005-12-24
[QUOTE=Lambert]You may want to add to your instructions all the packages needed to complete this howto.

dh_make
fakeroot
gcc-3.4
build-essential[/QUOTE]

Hey Lambert,

Just wondering; aren't the kernel-tree package needed here?? I always thought they did but I am not sure...

---

### Post by foxy123 on 2005-12-24
[QUOTE=Lambert]You may want to add to your instructions all the packages needed to complete this howto.

dh_make
fakeroot
gcc-3.4
build-essential[/QUOTE]

thanks a lot, done...

---

### Post by foxy123 on 2005-12-24
[QUOTE=greenway]Hey Lambert,

Just wondering; aren't the kernel-tree package needed here?? I always thought they did but I am not sure...[/QUOTE]

I do not think it is required... I have not got it installed on my box and still I did not have any problems with compiling ndiswrapper...

---

### Post by greenway on 2005-12-24
[QUOTE=foxy123]I do not think it is required... I have not got it installed on my box and still I did not have any problems with compiling ndiswrapper...[/QUOTE]

Yeah, you might well be right there. I always made sure I the packages were installed because I was taught so, never checked without them though... Anyway, nice howto!

grtz 

-mattijs

---

### Post by Lambert on 2005-12-24
I'm not that knowledge here but this is how I understand the linux-tree. Anybody who knows better can correct me.

> This meta package is used as a build-time dependency of prepackaged
Ubuntu linux-image packages. Its dependencies are structured so that a
complete kernel tree with Ubuntu patches applied will be available after
this package is installed

Kernel tree is just source of the kernel it's self. With the linux-tree package installed, it's only used when building a new kernel so there is a kernel tree of the new image with any patches.

---

### Post by greenway on 2005-12-24
[QUOTE=Lambert]I'm not that knowledge here but this is how I understand the linux-tree. Anybody who knows better can correct me.



Kernel tree is just source of the kernel it's self. With the linux-tree package installed, it's only used when building a new kernel so there is a kernel tree of the new image with any patches.[/QUOTE]

Tnx  for clearing that up and a merry christmas to you all!

---

### Post by gauss on 2005-12-27
Thanks for this excellent HOWTO. I'm a Ubuntu/Debian newbie and couldn't have done this without your HOWTO. Here are a few spots that might catch newbies like me:
> 1. Install kernel headers:
```
sudo apt-get install linux-headers-$(uname -r)
```
and dependencies:
```
sudo apt-get install dh_make fakeroot gcc-3.4 build-essential
```
In the repository it's dh-make.

> ```
fakeroot debian/rules binary-modules
fakeroot debian/rules binary-utils
```
You might need ```
sudo fakeroot ...
```
> 5. Install
```
sudo dpkg -i ndiswrapper-modules-2.6.12-10-686_1.7-1_i386.deb ndiswrapper-utils_1.7-1_i386.deb
```

The .deb packages are in the parent directory, so you'll need to precede the installation with ```
cd ..
```
Thanks again for your help. I'm hoping ndiswrapper 1.7 will work with Netgear WG311v3!

---

### Post by foxy123 on 2005-12-27
[QUOTE=gauss]Thanks for this excellent HOWTO. I'm a Ubuntu/Debian newbie and couldn't have done this without your HOWTO. Here are a few spots that might catch newbies like me:

In the repository it's dh-make.


You might need ```
sudo fakeroot ...
```

The .deb packages are in the parent directory, so you'll need to precede the installation with ```
cd ..
```
Thanks again for your help. I'm hoping ndiswrapper 1.7 will work with Netgear WG311v3![/QUOTE]

thanks for the comments, I will make the changes

you do not need to do 'sudo fakeroot' though... 

> Gives a fake root environment
This package is intended to enable something like:
  dpkg-buildpackage -rfakeroot
i.e. to remove the need to become root for a package build.

---

### Post by foxy123 on 2006-01-18
Ndiswrapper 1.8 is released. I have updated the howto, removing any version specific stuff.

---

### Post by Daramarak on 2006-03-21
*Complete newbie warning*

When trying to sudo apt-get install dh-make fakerppt gcc-3.4 build-essential

I get the message:
The package dh-make is unavailable, but another package refers to it.
...
Package dh-make have not got a installation candidate.

(roughly translated from norwegian)

---

### Post by foxy123 on 2006-03-21
[QUOTE=Daramarak]*Complete newbie warning*

When trying to sudo apt-get install dh-make fakerppt gcc-3.4 build-essential

I get the message:
The package dh-make is unavailable, but another package refers to it.
...
Package dh-make have not got a installation candidate.

(roughly translated from norwegian)[/QUOTE]
it's strange because the package is in the repository....

---

### Post by Daramarak on 2006-03-21
Yeah. I downloaded Breezy 5.10 from net, and burned the CD. I should have the same distribution as everybody else.

This is the absolutly first thing i tried after installing Breezy. Help are really needed. It is my first go at any Linux, and it is kind of discouraging not to get online.

---

### Post by foxy123 on 2006-03-21
[QUOTE=Daramarak]Yeah. I downloaded Breezy 5.10 from net, and burned the CD. I should have the same distribution as everybody else.

This is the absolutly first thing i tried after installing Breezy. Help are really needed. It is my first go at any Linux, and it is kind of discouraging not to get online.[/QUOTE]
did you add all repositories?
see here:
[http://doc.gwos.org/index.php/Sources.list](http://doc.gwos.org/index.php/Sources.list)

---

### Post by Daramarak on 2006-03-22
[QUOTE=foxy123]did you add all repositories?
see here:
[http://doc.gwos.org/index.php/Sources.list](http://doc.gwos.org/index.php/Sources.list)[/QUOTE]

As I said, I haven't touched the new installation, so no I haven't added anything. I didn't know I had to either. Good to know.

My problem is, due to no Ndiswrapper, no internett, and theese sources seem to be urls. Is it enough to edit the sourcelist, or do I have to access them through the net? Is it possible to copy them from another computer in any way?

---

### Post by foxy123 on 2006-03-22
[QUOTE=Daramarak]As I said, I haven't touched the new installation, so no I haven't added anything. I didn't know I had to either. Good to know.

My problem is, due to no Ndiswrapper, no internett, and theese sources seem to be urls. Is it enough to edit the sourcelist, or do I have to access them through the net? Is it possible to copy them from another computer in any way?[/QUOTE]
why don't you install ndiswrapper from the CD then?

btw, do other packages install fine?

---

### Post by Daramarak on 2006-03-22
[QUOTE=foxy123]why don't you install ndiswrapper from the CD then?

btw, do other packages install fine?[/QUOTE]

I do this, because a simple installation of Ndiswrapper did not work ok when I have tried to install it previously. It seems to work, but the modprobe (what ever that is) doesnt find it, I seem to remember. That thwarted my first go at my quest for the net.

I haven't tried to install other packages. My first step in setting up this computere is to get the net up and running.

So is there anything I can do?
Is there anyway I can make sure everything is installed alright?

---

### Post by foxy123 on 2006-03-22
[QUOTE=Daramarak]I do this, because a simple installation of Ndiswrapper did not work ok when I have tried to install it previously. It seems to work, but the modprobe (what ever that is) doesnt find it, I seem to remember. That thwarted my first go at my quest for the net.

I haven't tried to install other packages. My first step in setting up this computere is to get the net up and running.

So is there anything I can do?
Is there anyway I can make sure everything is installed alright?[/QUOTE]
I've taken a look at Breezy CD and have not found dh-make there. Try to download it from Internet and install and then try HOWTO again. Go [here]("http://packages.ubuntulinux.org/breezy/devel/dh-make"). Make sure that all dependencies listed there are installed.

---

### Post by Daramarak on 2006-03-22
[QUOTE=foxy123]I've taken a look at Breezy CD and have not found dh-make there. Try to download it from Internet and install and then try HOWTO again. Go [here]("http://packages.ubuntulinux.org/breezy/devel/dh-make"). Make sure that all dependencies listed there are installed.[/QUOTE]

installed dh-make, found five more dependencies, installed them, got a whole bunch of new dependencies, and after some more fiddeling got the thing installed.

Rest of the How to did work fine (I got some warnings, but there was nothing I could do, and it seemed to compile fine) After installing the Ndiswrapper modprobe didn't complain, and my drivers loaded fine.

My only concern now is that my little wlan card is still in the dark ](*,)  I hope ill find a way. Anyhow. Thanks for the support. It was good to get something to work.

Thanks!

---

### Post by Daramarak on 2006-03-22
After some fiddling my card lit up, and everything is just swell. Once again. Thanks for this great "HowTo"

---

### Post by TheEclypse on 2006-04-04
I am trying to compile ndiswrapper 1.12, and I get the following error on the *fakeroot debian/rules build-modules* step.

```
CC [M]  /home/nnamdi/ndiswrapper-1.12/driver/ndis.o
/home/nnamdi/ndiswrapper-1.12/driver/ndis.c:38:51: macro "create_singlethread_workqueue" requires 2 arguments, but only 1 given
/home/nnamdi/ndiswrapper-1.12/driver/ndis.c: In function `ndis_init':
/home/nnamdi/ndiswrapper-1.12/driver/ndis.c:38: error: `create_singlethread_workqueue' undeclared (first use in this function)
/home/nnamdi/ndiswrapper-1.12/driver/ndis.c:38: error: (Each undeclared identifier is reported only once
/home/nnamdi/ndiswrapper-1.12/driver/ndis.c:38: error: for each function it appears in.)
make[3]: *** [/home/nnamdi/ndiswrapper-1.12/driver/ndis.o] Error 1
make[2]: *** [_module_/home/nnamdi/ndiswrapper-1.12/driver] Error 2

```

Any ideas what could be causing it ?

---

### Post by greenbmw530i on 2006-04-16
[QUOTE=foxy123]
5. Install
```
sudo dpkg -i ndiswrapper-modules-[your kernel]_[current version]-1_i386.deb ndiswrapper-utils_[current version]-1_i386.deb
```
[/QUOTE]

I was good with everything until up to #5. I'm not sure as to what I put in each bracket. An example would be incredibly helpful.

          2.6.16 is my kernel version
          1.13 is my ndiswrapper version

Please help me.
Thanks a lot.

---

### Post by foxy123 on 2006-04-16
[QUOTE=greenbmw530i]I was good with everything until up to #5. I'm not sure as to what I put in each bracket. An example would be incredibly helpful.

          2.6.16 is my kernel version
          1.13 is my ndiswrapper version

Please help me.
Thanks a lot.[/QUOTE]
do 'ls *.deb' in the directory you are currently in...

---

### Post by greenbmw530i on 2006-04-16
[QUOTE=foxy123]do 'ls *.deb' in the directory you are currently in...[/QUOTE]
Ok, great. I got:
```

mike@Jamestown:~$ ls *.deb
ndiswrapper-modules-2.6.12-10-386_1.13-1_i386.deb
ndiswrapper-utils_1.8-1_i386.deb

```
The thing is, is that I'm on kernel 2.6.12 right now...and the whole reason i wanted to install the new ndiswrapper was because I wanted my wifi to work on my freshly installed 2.6.16 kernel...
What should I do in this case?
For instance:
```

mike@Jamestown:~$ sudo dpkg -i ndiswrapper-modules-2.6.12-10-386_1.13-1_i386.deb ndiswrapper-utils_1.8-1_i386.deb
```
OR
```

mike@Jamestown:~$ sudo dpkg -i ndiswrapper-modules-2.6.16ck3_1.13-1_i386.deb ndiswrapper-utils_1.8-1_i386.deb
```

---

### Post by foxy123 on 2006-04-16
[QUOTE=greenbmw530i]Ok, great. I got:

```

mike@Jamestown:~$ sudo dpkg -i ndiswrapper-modules-2.6.12-10-386_1.13-1_i386.deb ndiswrapper-utils_1.8-1_i386.deb
```

---

### Post by extremecarver on 2006-05-28
Hi - I got here because I followed the link from the thread on how to compile kernel 2.6.6 --> before using dapper RC1 with intel-wireless 2915 
however I want to undervolt my laptop and therefore I need a custom compiled kernel.
I did already 2 kernel compiles and after I had the kernel installed I reebooted and installed my newly compiled ndiswrapper package (25.8KB) - using 1.16. However my wifi still doesn't show up.

Do I have to install and compile IPW2200 as written on sourceforge?

---

### Post by extremecarver on 2006-05-29
Well Actually you have to install IPW2200 too. (only IPW 2200 didn't bring me any further either) and reboot. Afterwards it works - but only for the kernel you installed them for. If you recompile you have to do it again.

---

### Post by linuxunil on 2006-06-05
> root@linuxunil-laptop:~/ndiswrapper-1.17# fakeroot debian/rules binary-modules
/usr/bin/fakeroot: line 150: debian/rules: No such file or directory

I get this error and have followed all the steps up to here

---

### Post by eus107709 on 2006-06-05
I'm also having the same problem as linuxunil, any help would be appreciated.

Ubuntu 6.06
Ndiswrapper 1.17

---

### Post by sunspots on 2006-06-06
[QUOTE=Daramarak]*Complete newbie warning*

When trying to sudo apt-get install dh-make fakerppt gcc-3.4 build-essential

I get the message:
The package dh-make is unavailable, but another package refers to it.
...
Package dh-make have not got a installation candidate.

(roughly translated from norwegian)[/QUOTE]
I got the same error on Dapper 6.06. I upgraded from Breezy Badger 5.10 to Dapper using the Alternate CD.

How did you resolve your error?

I saw another message about making sure that debhelper, dpkg-dev, make, perl, build-essential are installed.

Do I use :
sudo apt-get install <each of the above packages>

Thanks for any help.

---

### Post by OPaul on 2006-06-07
I'm also getting the ```
/usr/bin/fakeroot: line 150: debian/rules: No such file or directory 
``` error. Any suggestions?

---

### Post by foxy123 on 2006-06-08
[QUOTE=OPaul]I'm also getting the ```
/usr/bin/fakeroot: line 150: debian/rules: No such file or directory 
``` error. Any suggestions?[/QUOTE]
it looks like they removed Debian rules from the latest version. You may try 1.16 or follwo the guide [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") (basically make and make install).

---

### Post by sunspots on 2006-06-08
Well I worked out how to install the packages and installed those without problem. Trying to install just dh-make still gives me the error:

Package dh-make is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dh-make has no installation candidate

Is there any manual process I can do to get around this problem?

Thanks

---

### Post by extremecarver on 2006-07-17
Could you please include in the first post that Dapper is using IPW firmware 3. So if one updates to 2.6.16 one will need to go back to old firmware.

If one updates to 2.6.17 internet works directly on first start - no configuration needed at all (well link to the old kernel modules as usual).
In Kernel configuration select all available options for 2915 except debugging.

Works like a charm.

---

### Post by OPaul on 2006-07-21
> **extremecarver said:**
> Could you please include in the first post that Dapper is using IPW firmware 3. So if one updates to 2.6.16 one will need to go back to old firmware.

If one updates to 2.6.17 internet works directly on first start - no configuration needed at all (well link to the old kernel modules as usual).
In Kernel configuration select all available options for 2915 except debugging.

Works like a charm.

Is there a list somewhere of wireless devices supported?

---

### Post by Trab on 2006-08-15
i need a deb of the latest version if anyone could please provide one?
my computer is having terrible problems with compiling one of its own, or even just make and make installing....

please help by providing a deb?
cheers much,
Trab

---

### Post by Chinthor on 2007-03-12
After much searching, found the easiest solution to many problems with wireless cards and NDIS-wrapped drivers.

The most common family of Broadcom chipsets are those in the 43xx series. So much so, that there is an automated script for getting it, and your wireless lan button working. The explanation and download are here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

The syntax is of course for Ubuntu, but with minor adjustments can work with almost anything.

Thank you to everyone who have kept these threads alive. Without them, I would never have found this.

---

### Post by evilnecrosis on 2007-04-23
im new to linux and dont really know much about it. is this the same stuff what it says in the ndiswrapper install text file coz i did what it said but it came up with errors

---

### Post by spots11 on 2009-12-10
followed the instructions perfectly, but i get the following error: 
marshall@marshall-laptop:~/ndiswrapper-1.55$ fakeroot debian/rules binary-modules
/usr/bin/fakeroot: 166: debian/rules: not found

---

### Post by foxy123 on 2009-12-12
> **spots11 said:**
> followed the instructions perfectly, but i get the following error: 
marshall@marshall-laptop:~/ndiswrapper-1.55$ fakeroot debian/rules binary-modules
/usr/bin/fakeroot: 166: debian/rules: not found

Unfortunately this topic is outdated. Ndiswrapper team does not provide Debian rules anymore. You can find a few more recent howtos on the forum.

---

