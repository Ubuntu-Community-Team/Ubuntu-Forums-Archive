---
title: "HOWTO: Install gcc-3.4 via apt-get without an Internet connection"
date: 2005-10-21
forum: Outdated Tutorials &amp; Tips
---

### Post by blastus on 2005-10-21
Compiling kernel modules on Breezy is difficult because the kernel was compiled with gcc-3.4.5 but the distribution CD does not contain gcc-3.4. Instead, when you install the build-essential package, gcc-4.0.2 is installed. The issue is that to compile kernel modules, you need the same version of gcc that was used to compile the kernel, otherwise you cannot compile kernel modules. This presents a dilemma to those ([like myself](http://www.ubuntuforums.org/showthread.php?t=77537)) that have to compile kernel modules for modems and things like that in order to connect to the Internet. NOTE: this guide is for i386 architectures only.

**1. Find a machine that has an Internet connection and download the following 3 packages**
[cpp-3.4_3.4.4-6ubuntu8_i386.deb (1707096 bytes)](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb)
[gcc-3.4_3.4.4-6ubuntu8_i386.deb (484408 bytes)](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb)
[gcc-3.4-base_3.4.4-6ubuntu8_i386.deb (163028 bytes)](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb)

**2. On your Breezy machine, create a directory called "gcc-3.4" and copy the above files to it**
```
mkdir ~/gcc-3.4
```

**3. Create a local repository**
```
cd ~/gcc-3.4
sudo apt-get install build-essential
dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
```
You should see something like this:
```
 ** Packages in archive but missing from override file: **
  cpp-3.4 gcc-3.4 gcc-3.4-base

 Wrote 3 entries to output Packages file.
```

**4. Edit /etc/apt/sources.list**
```
sudo gedit /etc/apt/sources.list
```
Comment out all the lines in the file that start with "deb-src http" or "deb http". To comment out a line, add a pound character # to the start of the line. We want to do this because we do not have an Internet connection, so we cannot access any repositories that exist on the Internet.

Then add the following line to the file:
```
deb file:///home/username/gcc-3.4 ./
```
Replace "username" with your username. For example, if your usename is "susie" then you would add this line instead: ```
deb file:///home/susie/gcc-3.4 ./
```

**5. Install gcc-3.4**
```
sudo apt-get update
sudo apt-get install gcc-3.4
```
You should see something like this:
```
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp-3.4 gcc-3.4-base
Suggested packages:
  binutils-doc gcc-3.4-doc libc6-dev-amd64
Recommended packages:
  libc6-dev
The following NEW packages will be installed:
  binutils cpp-3.4 gcc-3.4 gcc-3.4-base
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3824kB of archives.
After unpacking 15.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  gcc-3.4-base cpp-3.4 gcc-3.4
Install these packages without verification [y/N]? y

Preconfiguring packages ...
Selecting previously deselected package binutils.
(Reading database ... 56661 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1-2ubuntu6_i386.deb) ...
Selecting previously deselected package gcc-3.4-base.
Unpacking gcc-3.4-base (from .../gcc-3.4-base_3.4.4-6ubuntu8_i386.deb) ...
Selecting previously deselected package cpp-3.4.
Unpacking cpp-3.4 (from .../cpp-3.4_3.4.4-6ubuntu8_i386.deb) ...
Selecting previously deselected package gcc-3.4.
Unpacking gcc-3.4 (from .../gcc-3.4_3.4.4-6ubuntu8_i386.deb) ...
Setting up binutils (2.16.1-2ubuntu6) ...

Setting up gcc-3.4-base (3.4.4-6ubuntu8) ...
Setting up cpp-3.4 (3.4.4-6ubuntu8) ...
Setting up gcc-3.4 (3.4.4-6ubuntu8) ...
```

If step 5 doesn't work for you, you may want to try Arktis' tip "sudo dpkg -i filename" after you download the .deb files, where the filename is the .deb file. Try that for all three .deb files in addition to "sudo apt-get install binutils". I think "sudo dpkg -i *.deb" may do the trick.

You should now be able to compile your kernel modules. Following these steps, I was able to compile the kernel modules for my Lucent modem. Once you get an Internet connection, go back and uncomment all the lines you commented out in /etc/apt/sources.list in step 4. You can also remove the line you added to /etc/apt/sources.list and the ~/gcc-3.4 directory if you like.

---

### Post by chanders on 2005-10-21
Excellent howto. I saw a lot of people having trouble setting up their wireless cards and I guess like you their modem, because they didnt have gcc-3.4 that the kernel uses....

Again, great work!

---

### Post by Arrrhalomynn on 2005-10-21
I've done exactly what's in this howto, but when I type sudo apt-get update, I get an error that it ignores the file ./packages and that it can't be found.

I'd post the exact error message here, but it's in dutch, and I doubt you'd be able read it. If I'm not clear enough, I'll see if I can change it to english.

---

### Post by Arktis on 2005-10-21
I should like to point out that there is no need to create a local repository; you can just install the three debian packages with dpgk from the command line.

sudo dpkg -i filename

---

### Post by Arrrhalomynn on 2005-10-21
[QUOTE=Arktis]I should like to point out that there is no need to create a local repository; you can just install the three debian packages with dpgk from the command line.

sudo dpkg -i filename[/QUOTE]

That does work, thanks!

---

### Post by blastus on 2005-10-21
[QUOTE=Arrrhalomynn]I've done exactly what's in this howto, but when I type sudo apt-get update, I get an error that it ignores the file ./packages and that it can't be found.

I'd post the exact error message here, but it's in dutch, and I doubt you'd be able read it. If I'm not clear enough, I'll see if I can change it to english.[/QUOTE]

If forgot to mention that to use dpkg-scanpackages you need to install the build-essential package. I just finished installing Breezy from scratch and can confirm that it works on my machine. Make sure that the line you added to /etc/apt/sources.list is exactly correct.

As mentioned, you don't need to setup a local repository. You can use dpkg -i instead, but I trashed my system doing it that way. As far as I know, dpkg -i does not automatically handle dependencies so it will not install the binutils package (which is on the Breezy CD) and seems to be required for gcc-3.4. I used the apt-get method because it seems more reliable.

---

### Post by Arktis on 2005-10-22
Well, you could always use 'apt-get check' to look for broken dependancies, and then you can satisfy them from the cd.

---

### Post by elfgoh on 2005-10-22
Hi blastus,

I've followed all the steps u listed conscientiously... And it works great!!! Tks a million. Let's keep the community effort ongoing!

---

### Post by blastus on 2005-10-22
[QUOTE=elfgoh]Hi blastus,

I've followed all the steps u listed conscientiously... And it works great!!! Tks a million. Let's keep the community effort ongoing![/QUOTE]

Thanks elfgoh! I hope you are able to get your modules compiled now. :)

---

### Post by smoshe on 2005-11-15
I'm having trouble with this very issue.
Seems to me that it would make more sense to recompile the kernel in the latest gcc. Does anyone know if there is an ubuntu specific tutorial out there on how to do that?

---

### Post by blastus on 2005-11-16
As far as I know, the default Ubuntu Breezy kernel will not compile with gcc-4.0. I don't know why though but I suspect it is some kind of compatibility issue. You might want to check out [HOWTO: Kernel Compilation for Newbies](http://www.ubuntuforums.org/showthread.php?t=85064).

---

### Post by smoshe on 2005-11-17
I noticed. There's an error on line 787 according to my log. Problem is removing the latest gcc takes EVERYTHING with it. I lose apt, synamptic, g++, debian-builder, build essential, and libstdc++.

Do you know if there is going to be a kernel fix?

---

### Post by blastus on 2005-11-21
I can't help you on that one smoshe. I've never tried to compile the kernel being a newbie myself. :) Maybe the posters in the Kernel Compilation for Newbies thread can be of assistance?

Edit: I also did try to remove gcc one time and it destroyed my installation removing basically everything. [Magic command destroys entire Kubuntu installation!](http://ubuntuforums.org/showthread.php?t=77629)

---

### Post by ami on 2005-12-22
I used this howto to get my RT2570 USB Wireless network going.
Worked great but when I let the automatic update do its work everything stoped working. 
Guess the modifications on gcc-3.4 where destroyed.
Also the kernel was updated and I don't have the headers for the new kernel. 

To get everything working again do I have to reinstall or what.

---

### Post by darrowconley on 2005-12-30
on step 5 it seems like it wants to get the updates from the internet. I have done everything else and the results have been what is showen. 

any ideas on what I can do.

Thank you

---

### Post by Rasymas on 2006-01-17
Pretty Cool Step by Step tutorial, but here's what do I recieve after entering these commands:

arnoldas@ubuntu:~/gcc-3.4$ sudo apt-get update

.......

Fetched 4371kB in 30s (144kB/s)
Reading package lists... Done

arnoldas@ubuntu:~/gcc-3.4$ sudo apt-get install gcc-3.4

Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Does this mean that I already have a gcc-3.4? So I've been installing some other stuff, but I got some sort of error, saying that I don't have gcc-3.4 and so on. Btw.. does anyone knows why I have to configure my DSL internet each time I load my pc. And why sources.list open only when internet is not configured ? 

Thanks in advance :roll:

---

### Post by adamthompson on 2006-01-17
I tried this, and it worked fine until I got to step 5. After I typed "sudo apt-get install gcc-3.4", it said "Couldn't find package gcc-3.4".

I'm using 64-bit Ubuntu. Does that matter? Is this only for 32-bit?

---

### Post by blastus on 2006-01-19
OK everyone. I'll take a look into this soon. I'm not much on the forums anymore and I've been really busy lately, but I'll try my best to help everyone here. Just give me a couple of days and I'll look into it. ;)

---

### Post by blastus on 2006-01-29
I'm sorry for this very late response. I did try to get on the forums last weekend but everytime I tried the forums were down. :( Anyway, I think I know what the problem is. I've updated steps 4 and 5 with the changes. Lemme know if this works for y'all now. ;)

---

### Post by blastus on 2006-01-29
[QUOTE=adamthompson]I tried this, and it worked fine until I got to step 5. After I typed "sudo apt-get install gcc-3.4", it said "Couldn't find package gcc-3.4".

I'm using 64-bit Ubuntu. Does that matter? Is this only for 32-bit?[/QUOTE]

I'm not totally sure, but I would assume that it is only for the generic 32-bit Ubuntu installation. I believe the [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/) directory would have the .deb files you need for gcc-3.4 on 64-bit Ubuntu, but I'm not sure which ones you would need. Instead of downloading the *_i386.deb files, I would try downloading the corresponding *_amd64.deb files.

---

### Post by roy913 on 2006-02-02
Excellent howto. It solves my problem.

---

### Post by Subbu.exe on 2006-02-02
Thanks for the debs, Had to Compile my Own Drivers for my Lan Card!

---

### Post by Radon on 2006-05-03
Does the latest 6.06 beta 2 also use gcc 3.4?

---

### Post by pellgarlic on 2006-05-05
i'm so glad i found this post, thanks a lot blastus - this really helped me sort out problems i was having trying to install my intel 536ep modem. there were a couple of other problems too, but this was the biggest one, and it would have taken me ages to figure it out myself. you saved me a lot of time and pain! 

cheers :)

---

### Post by blastus on 2006-05-10
[quote=Radon]Does the latest 6.06 beta 2 also use gcc 3.4?[/quote]

I'm not sure. I would hope that the final release of Dapper includes the same version of gcc that the kernel was compiled with. If not, then we'll need another one of these HOWTOs for Dapper. Not including the version of gcc that was used to compile the kernel on the Breezy distribution CD was a HUGE oversight.

[quote=pellgarlic]i'm so glad i found this post, thanks a lot blastus - this really helped me sort out problems i was having trying to install my intel 536ep modem. there were a couple of other problems too, but this was the biggest one, and it would have taken me ages to figure it out myself. you saved me a lot of time and pain!

cheers :)[/quote]

Hey that's great :) I'm glad to know I've contributed something others find really helpful!

---

### Post by towsonu2003 on 2006-05-10
[https://launchpad.net/distros/ubuntu/+source/gcc-3.4/+bug/44139](https://launchpad.net/distros/ubuntu/+source/gcc-3.4/+bug/44139) --just filed it for this (have been seeing this problem sooo much during winmodem support)... any support **very much** appreciated :)

---

### Post by towsonu2003 on 2006-05-10
[QUOTE=towsonu2003][https://launchpad.net/distros/ubuntu/+source/gcc-3.4/+bug/44139](https://launchpad.net/distros/ubuntu/+source/gcc-3.4/+bug/44139) [/QUOTE]
wow... amazed how fast they **rejected** the bug... ~25 minutes. The **first** bug I've seen getting attention in such a little time... 


anyone willing to comment to open the bug back up?.. Thanks :)

---

### Post by bluegene on 2006-06-01
blastus:

after a sleepless nights i've spent getting ipw2200 to work and thousands of googlish info..at last i found ur procedure really works;) . im using toshiba satellite m40-237+ubuntu breezy+ipw200 and successfuly run kismet..however, it took me awhile since i had to obtain the required libraries..

anyway..many thanks to you and the developers out there...kudus!!!

---

### Post by sivasankarigovind on 2010-07-31
hi all,
while installing my gcc, whenever i give apt-get install build-essential or apt-get install bison i am getting errors like
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

or

Package bison is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bison has no installation candidate

can anyone pls help me out

---

### Post by sivasankarigovind on 2010-07-31
hi all,
I have completed my gcc installation upto step 5. but it shows only 3 files installed. binutils is missing... what should i do now. can anyone help...

---

### Post by QT embedded on 2010-11-21
Hi Man, i Download 3 package follow this instruction:
> 
Download the following 3 deb packages from [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/)
a)         cpp-3.4_3.4.4-6ubuntu8_i386.deb (1707096 bytes
b)        gcc-3.4_3.4.4-6ubuntu8_i386.deb (484408 bytes)
c)        gcc-3.4-base_3.4.4-6ubuntu8_i386.deb (163028 bytes)

but when i type [SIZE=4][COLOR=Red]**sudo apt-get install gcc-3.4 [SIZE=2][COLOR=Black]it Error message[/COLOR][/SIZE]**[/COLOR][/SIZE]

> [SIZE=4][COLOR=Red]**sudo apt-get install gcc-3.4**[/COLOR][/SIZE]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc-3.4 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  g++-3.4: Depends: gcc-3.4 (= 3.4.6-6ubuntu3) but 3.4.6-8ubuntu2 is to be installed
           Depends: gcc-3.4-base (= 3.4.6-6ubuntu3) but 3.4.6-8ubuntu2 is to be installed
  libstdc++6-dev: Depends: gcc-3.4-base (= 3.4.6-6ubuntu3) but 3.4.6-8ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
hieunt@hieunt-laptop:~$ sudo apt-get update
Ign file: ./ Release.gpg
Ign file:/home/hieunt/Desktop/gcc3.4/ ./ Translation-en_US
Ign file: ./ Release
Ign file: ./ Packages
Ign file: ./ Packages
Err file: ./ Packages
  File not found
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,088B]
Fetched 2,632B in 0s (8,658B/s)
W: Failed to fetch file:/home/hieunt/Desktop/gcc3.4/./Packages.gz  File not found

E: Some index files failed to download, they have been ignored, or old ones used instead.
hieunt@hieunt-laptop:~$ sudo gedit /etc/apt/sources.list
hieunt@hieunt-laptop:~$ sudo apt-get update
Ign file: ./ Release.gpg
Ign file:/home/hieunt/gcc3.4/ ./ Translation-en_US
Ign file: ./ Release             
Ign file: ./ Packages            
Ign file: ./ Packages            
Err file: ./ Packages            
  File not found
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,088B]
Fetched 2,632B in 1s (1,445B/s)
W: Failed to fetch file:/home/hieunt/gcc3.4/./Packages.gz  File not found

E: Some index files failed to download, they have been ignored, or old ones used instead.
hieunt@hieunt-laptop:~$ 



---

