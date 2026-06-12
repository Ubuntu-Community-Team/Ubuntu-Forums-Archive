---
title: "Weird Warning that my hard drive is full"
date: 2013-12-04
forum: New to Ubuntu
---

### Post by nycap on 2013-12-04
Hi,
All of the sudden I have this warning that my hard drive is full.  how can this be?? i have done nothing to fill up 70 gigs.  how can i clean it? 

Thanks!
using ubuntu 12.10

---

### Post by Bashing-om on 2013-12-04
nycap; Hi !

Chances are it is a partition (device as ubuntu sees it) that is full:
Let's look:
terminal commands:
```

df -h
df -i
sudo du -sx * | sort -n

```
If you need to drill down further, use cd to move to a directory of interest then repeat the du command.
The results are in megabytes.

I expect that you will find it is the /boot directory that is full.
```

la -la /boot

```Depending on those outputs is the action to be taken.

[INDENT][INDENT]maybe yes, maybe not so yes
[/INDENT][/INDENT]

---

### Post by nycap on 2013-12-04
Hi, thanks.  I am unclear what this is telling us:
```

matt@matt-Inspiron-1525:~$ df -h
Filesystem           Size  Used Avail Use% Mounted on
/dev/sda6             65G   61G  879M  99% /
udev                 2.0G  4.0K  2.0G   1% /dev
tmpfs                807M  908K  806M   1% /run
none                 5.0M     0  5.0M   0% /run/lock
none                 2.0G  216K  2.0G   1% /run/shm
none                 100M   88K  100M   1% /run/user
/home/matt/.Private   65G   61G  879M  99% /home/matt
/dev/mmcblk0p1       7.4G  1.9G  5.6G  25% /media/matt/6134-6162
matt@matt-Inspiron-1525:~$ df -i
Filesystem           Inodes   IUsed   IFree IUse% Mounted on
/dev/sda6           4317184 1002696 3314488   24% /
udev                 208517     554  207963    1% /dev
tmpfs                214007     500  213507    1% /run
none                 214007       3  214004    1% /run/lock
none                 214007       7  214000    1% /run/shm
none                 214007      32  213975    1% /run/user
/home/matt/.Private 4317184 1002696 3314488   24% /home/matt
/dev/mmcblk0p1            0       0       0     - /media/matt/6134-6162
matt@matt-Inspiron-1525:~$ sudo du -sx * | sort -n
[sudo] password for matt: 
```

Any help will be much apprecitated.

---

### Post by Bashing-om on 2013-12-04
nycap;

Hey, not a problem to explain,, and help is what we do best !
see this:
> 
/dev/sda6             65G   61G  879M  99% /

says you have no head room (99 % used !) on the partition sda6 that is mounted as "/" (root) .

So, what is taking up all your disk space, we do a du (disk usage) command to see:
To have the authorization to look at certain directories we need elevated privileges, that is where "sudo" come into play .. sudo = Super User DO.

Now we know that "/" is in a separate partiton than is /home .. and we want to look at "/".
So, change the command line's present working directory by the change directory (cd) command:
do terminal command:
```

cd /

```
now let's take a look:
```

sudo du -sx * | sort -n

``` here with "disk usage: we are looking at all the files at and below the PWD , the "s" argument = --summarize,  display only a total for each argument; and x = --one-file-system,  skip directories on different file systems. OK so far ? .. now we are taking the output of du and with the pipe (|) utility and inputting that output into the utility "sort" ->  Write sorted concatenation of all FILE(s) to standard output the "n" argument =  --numeric-sort, compare according to string numerical value.

With that info I still expect to see the /boot directory as full.
verify:
```

ls -la /boot

```

Now when it is confirmed that /boot is full, we will take measures to remove the old unused kernels and headers. Which will return you some operating space. We will want to clean things up a bit first .. to see if we can get enough head room for "apt-get remove" to operate in.

And to return to /home as your Present Working Directory - done looking - do:
terminal code:
```

cd

``` which with no arguments to the "cd" command return one to their /home directory.

[INDENT][INDENT]small steps,
[INDENT][INDENT]but we will get there
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-12-04
nycap; Hey !

I am done for this session, I have an early out in my AM and must retire.
Perhaps others will take up my slack.
I will check back with you in about 14 hours.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by Impavidus on 2013-12-05
See this thread for some general ways of troubleshooting full disks: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
You have to find out which directory is causing the problem.

---

### Post by nycap on 2013-12-05
Hi,
bleacbit and emptying the trash bin freed 20 gigs so i have some time to get this under control.  but I am confused as to what exactly is taking up the other 79% or 50 gigs of space? i dont download music or anything like that.  and the boot directory is loaded with what looks like encrypted files of some sort.
thanks!

---

### Post by philinux on 2013-12-05
> **nycap said:**
> Hi,
bleacbit and emptying the trash bin freed 20 gigs so i have some time to get this under control.  but I am confused as to what exactly is taking up the other 79% or 50 gigs of space? i dont download music or anything like that.  and the boot directory is loaded with what looks like encrypted files of some sort.
thanks!

Possibly old kernels. They can take up a lot of space. Unless bleachbit has already done this.

I use this, step 5 includes a dry run so you can see exactly what the remove will do. I run this now and again.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by nycap on 2013-12-05
> **philinux said:**
> Possibly old kernels. They can take up a lot of space. Unless bleachbit has already done this.

I use this, step 5 includes a dry run so you can see exactly what the remove will do. I run this now and again.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

for some reason it wont let me do step 5:

```

matt@matt-Inspiron-1525:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libc6-dev : Depends: linux-libc-dev but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```
Any ideas will be greatly appreciated.  Thanks!

---

### Post by philinux on 2013-12-05
Run these. Post back any errors.

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by nycap on 2013-12-05
> **philinux said:**
> Run these. Post back any errors.

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

```
sudo apt-get update && sudo apt-get upgrade
```

Hi!
I did those three and then went back to the step 5 to clear some kernels and here is the error:

```

matt@matt-Inspiron-1525:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libc6-dev : Depends: linux-libc-dev but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


```

Thanks!!

---

### Post by Bashing-om on 2013-12-05
nycap; Hey, I am back !

You have been in good hands. Let's see about:
> 
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 Try:
```

sudo apt-get dist-upgrade

```
See if apt-get's smart mode will deal with  ->
"inux-libc-dev" !!

BUT ----

What in the world are you - as a "beginner" - doing with development packages installed onto your system ?
> 
Package: libc6-dev
<snip>
Description-en: Embedded GNU C Library: Development Libraries and Header Files
 Contains the symlinks, headers, and object files needed to compile
 and link programs which use the standard C library.
<snip>

Can you make do with out the development tools, not sure, but may be a lot easier to remove than to build and resolve that dependency (??)

bk

And still to be dealt with, is whatever directory (/boot ??) is maxed out. 1st order of priority, however, is to get the package manager in a happy state.

[INDENT][INDENT]all in a day's work
[/INDENT][/INDENT]

---

### Post by nycap on 2013-12-05
Hey!
I did the command you have shown above but I am having the same error still when trying to get some old kernels out.   yeah i need the c and c++ stuff for programming.  Thanks!

---

### Post by Bashing-om on 2013-12-05
nycap; OK !

Let's go to work and fix the package manager.
Show me the entire output of terminal command;
```

sudo apt-get install linux-libc-dev

```

We will then get an idea of what to do .

[INDENT][INDENT]regards
[/INDENT][/INDENT]

---

### Post by nycap on 2013-12-05
Here is the ouput:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-libc-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Bashing-om on 2013-12-05
nycap; Hummm,
Not making much sense to me at this moment.

This says there is a problem;
> 
libc6-dev : Depends: linux-libc-dev but it is not going to be installed

BUT, this says all is hunky dory:
> 
linux-libc-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So, what results now from:
```

sudo apt-get update
sudo apt-get upgrade

```

[INDENT][INDENT]sometimes I wonder, othertimes I do not know
[/INDENT][/INDENT]

---

### Post by r-senior on 2013-12-05
> **nycap said:**
> Hi!
I did those three and then went back to the step 5 to clear some kernels and here is the error:

```

[color="red"][s]**$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y[/s]**[/color] 
```

You should stop running this command. It was posted over three years ago and the person who posted it only checked it on a 32-bit system.

It is only supposed to match kernel related packages but it matches **linux-libc-dev:amd64**. Essentially what that string of commands does is find all installed packages that begin with 'linux-', excludes those that contain the same version number as your current kernel, then assumes that anything with a number should be deleted. This is an incorrect assumption on recent 64-bit versions of Ubuntu.

You may or may not want linux-libc-dev:amd64 installed but you certainly don't want to uninstall it as a side-effect of trying to remove old kernels.

---

### Post by nycap on 2013-12-05
shortened output:
```

Reading package lists... Done
matt@matt-Inspiron-1525:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

---

### Post by Bashing-om on 2013-12-05
nycap; Hey,

see r-senior's most excellent observation !

Ok, seemingly at this point the package manager is in a happy state.
Back to "disk full"

let's just cut to the chase and have a direct looksee:
```

ls -la /boot

```
Just to easy my mind.
[INDENT][INDENT]ubuntu, all things are possible
[/INDENT][/INDENT]

---

### Post by nycap on 2013-12-05
Here is the output from that command:
```

total 618920
drwxr-xr-x  4 root root     4096 Dec  3 08:19 .
drwxr-xr-x 25 root root     4096 Dec  3 08:18 ..
-rw-r--r--  1 root root   853738 Oct  9  2012 abi-3.5.0-17-generic
-rw-r--r--  1 root root   853793 Oct 19  2012 abi-3.5.0-18-generic
-rw-r--r--  1 root root   856743 Jan  8  2013 abi-3.5.0-22-generic
-rw-r--r--  1 root root   856743 Jan 24  2013 abi-3.5.0-23-generic
-rw-r--r--  1 root root   858289 Feb  7  2013 abi-3.5.0-24-generic
-rw-r--r--  1 root root   858289 Feb 25  2013 abi-3.5.0-25-generic
-rw-r--r--  1 root root   858541 Mar  8  2013 abi-3.5.0-26-generic
-rw-r--r--  1 root root   860818 Mar 25  2013 abi-3.5.0-27-generic
-rw-r--r--  1 root root   860943 Apr 23  2013 abi-3.5.0-28-generic
-rw-r--r--  1 root root   860943 May 14  2013 abi-3.5.0-30-generic
-rw-r--r--  1 root root   860983 May 16  2013 abi-3.5.0-31-generic
-rw-r--r--  1 root root   860983 May 29  2013 abi-3.5.0-32-generic
-rw-r--r--  1 root root   861067 Jun  6 16:49 abi-3.5.0-34-generic
-rw-r--r--  1 root root   860873 Jun 19 11:41 abi-3.5.0-36-generic
-rw-r--r--  1 root root   861363 Jul  8 18:40 abi-3.5.0-37-generic
-rw-r--r--  1 root root   861474 Aug 13 15:04 abi-3.5.0-39-generic
-rw-r--r--  1 root root   861648 Aug 21 21:27 abi-3.5.0-40-generic
-rw-r--r--  1 root root   861789 Sep 11 12:10 abi-3.5.0-41-generic
-rw-r--r--  1 root root   861789 Oct  1 18:08 abi-3.5.0-42-generic
-rw-r--r--  1 root root   861854 Oct 23 14:02 abi-3.5.0-43-generic
-rw-r--r--  1 root root   861854 Nov 12 15:07 abi-3.5.0-44-generic
-rw-r--r--  1 root root   154429 Oct  9  2012 config-3.5.0-17-generic
-rw-r--r--  1 root root   154429 Oct 19  2012 config-3.5.0-18-generic
-rw-r--r--  1 root root   154427 Jan  8  2013 config-3.5.0-22-generic
-rw-r--r--  1 root root   154427 Jan 24  2013 config-3.5.0-23-generic
-rw-r--r--  1 root root   154500 Feb  7  2013 config-3.5.0-24-generic
-rw-r--r--  1 root root   154500 Feb 25  2013 config-3.5.0-25-generic
-rw-r--r--  1 root root   154500 Mar  8  2013 config-3.5.0-26-generic
-rw-r--r--  1 root root   154652 Mar 25  2013 config-3.5.0-27-generic
-rw-r--r--  1 root root   154652 Apr 23  2013 config-3.5.0-28-generic
-rw-r--r--  1 root root   154652 May 14  2013 config-3.5.0-30-generic
-rw-r--r--  1 root root   154689 May 16  2013 config-3.5.0-31-generic
-rw-r--r--  1 root root   154689 May 29  2013 config-3.5.0-32-generic
-rw-r--r--  1 root root   154689 Jun  6 16:49 config-3.5.0-34-generic
-rw-r--r--  1 root root   154689 Jun 19 11:41 config-3.5.0-36-generic
-rw-r--r--  1 root root   154704 Jul  8 18:40 config-3.5.0-37-generic
-rw-r--r--  1 root root   154704 Aug 13 15:04 config-3.5.0-39-generic
-rw-r--r--  1 root root   154704 Aug 21 21:27 config-3.5.0-40-generic
-rw-r--r--  1 root root   154704 Sep 11 12:10 config-3.5.0-41-generic
-rw-r--r--  1 root root   154704 Oct  1 18:08 config-3.5.0-42-generic
-rw-r--r--  1 root root   154704 Oct 23 14:02 config-3.5.0-43-generic
-rw-r--r--  1 root root   154704 Nov 12 15:07 config-3.5.0-44-generic
drwxr-xr-x  3 root root     4096 Dec  3 08:19 extlinux
drwxr-xr-x  5 root root     4096 Dec  3 08:19 grub
-rw-r--r--  1 root root 21554583 Nov 13  2012 initrd.img-3.5.0-17-generic
-rw-r--r--  1 root root 21555381 Nov 13  2012 initrd.img-3.5.0-18-generic
-rw-r--r--  1 root root 21561731 Jan 24  2013 initrd.img-3.5.0-22-generic
-rw-r--r--  1 root root 21562530 Feb 13  2013 initrd.img-3.5.0-23-generic
-rw-r--r--  1 root root 21574613 Feb 21  2013 initrd.img-3.5.0-24-generic
-rw-r--r--  1 root root 21574348 Mar  3  2013 initrd.img-3.5.0-25-generic
-rw-r--r--  1 root root 21605159 Mar 29  2013 initrd.img-3.5.0-26-generic
-rw-r--r--  1 root root 21638092 Apr  9  2013 initrd.img-3.5.0-27-generic
-rw-r--r--  1 root root 21642570 May  2  2013 initrd.img-3.5.0-28-generic
-rw-r--r--  1 root root 21646905 May 16  2013 initrd.img-3.5.0-30-generic
-rw-r--r--  1 root root 21646412 May 24  2013 initrd.img-3.5.0-31-generic
-rw-r--r--  1 root root 21647367 Jun  2  2013 initrd.img-3.5.0-32-generic
-rw-r--r--  1 root root 21642588 Jun 16 12:40 initrd.img-3.5.0-34-generic
-rw-r--r--  1 root root 21649408 Jul  6 08:00 initrd.img-3.5.0-36-generic
-rw-r--r--  1 root root 21705288 Aug  1 11:32 initrd.img-3.5.0-37-generic
-rw-r--r--  1 root root 21707085 Aug 22 22:28 initrd.img-3.5.0-39-generic
-rw-r--r--  1 root root 21709369 Sep  6 08:41 initrd.img-3.5.0-40-generic
-rw-r--r--  1 root root 21713521 Sep 29 07:45 initrd.img-3.5.0-41-generic
-rw-r--r--  1 root root 21712660 Oct 25 13:06 initrd.img-3.5.0-42-generic
-rw-r--r--  1 root root 21711980 Nov  8 09:37 initrd.img-3.5.0-43-generic
-rw-r--r--  1 root root 21712104 Dec  3 08:19 initrd.img-3.5.0-44-generic
-rw-r--r--  1 root root   176764 Jan  3  2013 memtest86+.bin
-rw-r--r--  1 root root   178944 Jan  3  2013 memtest86+_multiboot.bin
-rw-------  1 root root  2320733 Oct  9  2012 System.map-3.5.0-17-generic
-rw-------  1 root root  2321612 Oct 19  2012 System.map-3.5.0-18-generic
-rw-------  1 root root  2323082 Jan  8  2013 System.map-3.5.0-22-generic
-rw-------  1 root root  2322953 Jan 24  2013 System.map-3.5.0-23-generic
-rw-------  1 root root  2323673 Feb  7  2013 System.map-3.5.0-24-generic
-rw-------  1 root root  2323653 Feb 25  2013 System.map-3.5.0-25-generic
-rw-------  1 root root  2318941 Mar  8  2013 System.map-3.5.0-26-generic
-rw-------  1 root root  2320304 Mar 25  2013 System.map-3.5.0-27-generic
-rw-------  1 root root  2320804 Apr 23  2013 System.map-3.5.0-28-generic
-rw-------  1 root root  2320804 May 14  2013 System.map-3.5.0-30-generic
-rw-------  1 root root  2320825 May 16  2013 System.map-3.5.0-31-generic
-rw-------  1 root root  2320825 May 29  2013 System.map-3.5.0-32-generic
-rw-------  1 root root  2321450 Jun  6 16:49 System.map-3.5.0-34-generic
-rw-------  1 root root  2321569 Jun 19 11:41 System.map-3.5.0-36-generic
-rw-------  1 root root  2321800 Jul  8 18:40 System.map-3.5.0-37-generic
-rw-------  1 root root  2322548 Aug 13 15:04 System.map-3.5.0-39-generic
-rw-------  1 root root  2323087 Aug 21 21:27 System.map-3.5.0-40-generic
-rw-------  1 root root  2323311 Sep 11 12:10 System.map-3.5.0-41-generic
-rw-------  1 root root  2323311 Oct  1 18:08 System.map-3.5.0-42-generic
-rw-------  1 root root  2323317 Oct 23 14:02 System.map-3.5.0-43-generic
-rw-------  1 root root  2323346 Nov 12 15:07 System.map-3.5.0-44-generic
-rw-r--r--  1 root root  5171760 Oct 17  2012 vmlinuz-3.5.0-17-generic
-rw-------  1 root root  5176048 Oct 19  2012 vmlinuz-3.5.0-18-generic
-rw-------  1 root root  5176592 Jan  8  2013 vmlinuz-3.5.0-22-generic
-rw-------  1 root root  5176144 Jan 24  2013 vmlinuz-3.5.0-23-generic
-rw-------  1 root root  5180752 Feb  7  2013 vmlinuz-3.5.0-24-generic
-rw-------  1 root root  5180432 Feb 25  2013 vmlinuz-3.5.0-25-generic
-rw-------  1 root root  5167568 Mar  8  2013 vmlinuz-3.5.0-26-generic
-rw-------  1 root root  5169520 Mar 25  2013 vmlinuz-3.5.0-27-generic
-rw-------  1 root root  5169232 Apr 23  2013 vmlinuz-3.5.0-28-generic
-rw-------  1 root root  5169232 May 14  2013 vmlinuz-3.5.0-30-generic
-rw-------  1 root root  5170160 May 16  2013 vmlinuz-3.5.0-31-generic
-rw-------  1 root root  5170160 May 29  2013 vmlinuz-3.5.0-32-generic
-rw-------  1 root root  5171952 Jun  6 16:49 vmlinuz-3.5.0-34-generic
-rw-------  1 root root  5172784 Jun 19 11:41 vmlinuz-3.5.0-36-generic
-rw-------  1 root root  5173136 Jul  8 18:40 vmlinuz-3.5.0-37-generic
-rw-------  1 root root  5174352 Aug 13 15:04 vmlinuz-3.5.0-39-generic
-rw-------  1 root root  5174640 Aug 21 21:27 vmlinuz-3.5.0-40-generic
-rw-------  1 root root  5175280 Sep 11 12:10 vmlinuz-3.5.0-41-generic
-rw-------  1 root root  5175280 Oct  1 18:08 vmlinuz-3.5.0-42-generic
-rw-------  1 root root  5175504 Oct 23 14:02 vmlinuz-3.5.0-43-generic
-rw-------  1 root root  5175632 Nov 12 15:07 vmlinuz-3.5.0-44-generic


```

---

### Post by Bashing-om on 2013-12-05
nycap; Well !

"apt-get" has been renovated - in later kernels - such that "autoremove" will remove the old kernels and config files, But I do not know the cutoff for the older kernel versions !
Let's try it first - for my info as much as anything else - and see if it is effective with the 3.5 series kernels.
Else I will provide the correct command to remove the kernels and then do the cleanup.

Try:
```

sudo apt-get autoremove
ls -la /boot

```

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by philinux on 2013-12-06
The link I gave to tuxtweaks has an update at the bottom which says it works on 64 bit.  In fact my rigs are all 64 bit and I've never had an issue with that one liner.

I always recommend the dry run first in any case.

I'll contact the author re dev libraries though. This could well be an issue for some.

---

### Post by nycap on 2013-12-06
Hi!
I ran the command you posted and the contents of the boot directory are the same.  Thanks!

---

### Post by nycap on 2013-12-06
Thanks!  I did the dry run, i did all th steps, which are sort of just piecemeal of the last one liner.  I am on 32 bit machine I believe.  dont know if that makes a difference.  Thanks.

---

### Post by nycap on 2013-12-06
The following packages have unmet dependencies:
 libc6-dev : Depends: linux-libc-dev but it is not going to be installed

I am a little confused by this being that i have both of these packages installed??

---

### Post by r-senior on 2013-12-06
What do you get if you run that command up to the point where it does the apt-get, i.e. this:

```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9]
```

Could you post your output?

---

### Post by nycap on 2013-12-06
HI!  here is the output from that:
```

matt@matt-Inspiron-1525:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9]
linux-headers-3.5.0-17
linux-headers-3.5.0-17-generic
linux-headers-3.5.0-18
linux-headers-3.5.0-18-generic
linux-headers-3.5.0-22
linux-headers-3.5.0-22-generic
linux-headers-3.5.0-23
linux-headers-3.5.0-23-generic
linux-headers-3.5.0-24
linux-headers-3.5.0-24-generic
linux-headers-3.5.0-25
linux-headers-3.5.0-25-generic
linux-headers-3.5.0-26
linux-headers-3.5.0-26-generic
linux-headers-3.5.0-27
linux-headers-3.5.0-27-generic
linux-headers-3.5.0-28
linux-headers-3.5.0-28-generic
linux-headers-3.5.0-30
linux-headers-3.5.0-30-generic
linux-headers-3.5.0-31
linux-headers-3.5.0-31-generic
linux-headers-3.5.0-32
linux-headers-3.5.0-32-generic
linux-headers-3.5.0-34
linux-headers-3.5.0-34-generic
linux-headers-3.5.0-36
linux-headers-3.5.0-36-generic
linux-headers-3.5.0-37
linux-headers-3.5.0-37-generic
linux-headers-3.5.0-39
linux-headers-3.5.0-39-generic
linux-headers-3.5.0-40
linux-headers-3.5.0-40-generic
linux-headers-3.5.0-41
linux-headers-3.5.0-41-generic
linux-headers-3.5.0-42
linux-headers-3.5.0-42-generic
linux-headers-3.5.0-43
linux-headers-3.5.0-43-generic
linux-image-3.5.0-17-generic
linux-image-3.5.0-18-generic
linux-image-3.5.0-22-generic
linux-image-3.5.0-23-generic
linux-image-3.5.0-24-generic
linux-image-3.5.0-25-generic
linux-image-3.5.0-26-generic
linux-image-3.5.0-27-generic
linux-image-3.5.0-28-generic
linux-image-3.5.0-30-generic
linux-image-3.5.0-31-generic
linux-image-3.5.0-32-generic
linux-image-3.5.0-34-generic
linux-image-3.5.0-36-generic
linux-image-3.5.0-37-generic
linux-image-3.5.0-39-generic
linux-image-3.5.0-40-generic
linux-image-3.5.0-41-generic
linux-image-3.5.0-42-generic
linux-image-3.5.0-43-generic
linux-image-extra-3.5.0-17-generic
linux-image-extra-3.5.0-18-generic
linux-image-extra-3.5.0-22-generic
linux-image-extra-3.5.0-23-generic
linux-image-extra-3.5.0-24-generic
linux-image-extra-3.5.0-25-generic
linux-image-extra-3.5.0-26-generic
linux-image-extra-3.5.0-27-generic
linux-image-extra-3.5.0-28-generic
linux-image-extra-3.5.0-30-generic
linux-image-extra-3.5.0-31-generic
linux-image-extra-3.5.0-32-generic
linux-image-extra-3.5.0-34-generic
linux-image-extra-3.5.0-36-generic
linux-image-extra-3.5.0-37-generic
linux-image-extra-3.5.0-39-generic
linux-image-extra-3.5.0-40-generic
linux-image-extra-3.5.0-41-generic
linux-image-extra-3.5.0-42-generic
linux-image-extra-3.5.0-43-generic
linux-libc-dev:i386

```

---

### Post by r-senior on 2013-12-06
OK ... this is the problem with this command: it selects this, which is not an old kernel:

```
linux-libc-dev:i386
```

Try adding another condition to exclude libc:

```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -v libc
```

If that only selects linux-headers*, linux-image* and linux-image-extra*, you should be OK to add the xargs part on the end of that modified command. Use the --dry-run option before you run it for real.

Before you run the remove for real, double check that your current kernel version is being excluded. Make sure the version number listed by uname -r is _not_ appearing in the list.

Check and double check everything and if in doubt, post the output of the command before you commit to adding the xargs part.

---

### Post by nycap on 2013-12-06
ok here is the output from that command.  the c lib is not listed.  are we good to proceed?

```

matt@matt-Inspiron-1525:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -v libc
linux-headers-3.5.0-17
linux-headers-3.5.0-17-generic
linux-headers-3.5.0-18
linux-headers-3.5.0-18-generic
linux-headers-3.5.0-22
linux-headers-3.5.0-22-generic
linux-headers-3.5.0-23
linux-headers-3.5.0-23-generic
linux-headers-3.5.0-24
linux-headers-3.5.0-24-generic
linux-headers-3.5.0-25
linux-headers-3.5.0-25-generic
linux-headers-3.5.0-26
linux-headers-3.5.0-26-generic
linux-headers-3.5.0-27
linux-headers-3.5.0-27-generic
linux-headers-3.5.0-28
linux-headers-3.5.0-28-generic
linux-headers-3.5.0-30
linux-headers-3.5.0-30-generic
linux-headers-3.5.0-31
linux-headers-3.5.0-31-generic
linux-headers-3.5.0-32
linux-headers-3.5.0-32-generic
linux-headers-3.5.0-34
linux-headers-3.5.0-34-generic
linux-headers-3.5.0-36
linux-headers-3.5.0-36-generic
linux-headers-3.5.0-37
linux-headers-3.5.0-37-generic
linux-headers-3.5.0-39
linux-headers-3.5.0-39-generic
linux-headers-3.5.0-40
linux-headers-3.5.0-40-generic
linux-headers-3.5.0-41
linux-headers-3.5.0-41-generic
linux-headers-3.5.0-42
linux-headers-3.5.0-42-generic
linux-headers-3.5.0-43
linux-headers-3.5.0-43-generic
linux-image-3.5.0-17-generic
linux-image-3.5.0-18-generic
linux-image-3.5.0-22-generic
linux-image-3.5.0-23-generic
linux-image-3.5.0-24-generic
linux-image-3.5.0-25-generic
linux-image-3.5.0-26-generic
linux-image-3.5.0-27-generic
linux-image-3.5.0-28-generic
linux-image-3.5.0-30-generic
linux-image-3.5.0-31-generic
linux-image-3.5.0-32-generic
linux-image-3.5.0-34-generic
linux-image-3.5.0-36-generic
linux-image-3.5.0-37-generic
linux-image-3.5.0-39-generic
linux-image-3.5.0-40-generic
linux-image-3.5.0-41-generic
linux-image-3.5.0-42-generic
linux-image-3.5.0-43-generic
linux-image-extra-3.5.0-17-generic
linux-image-extra-3.5.0-18-generic
linux-image-extra-3.5.0-22-generic
linux-image-extra-3.5.0-23-generic
linux-image-extra-3.5.0-24-generic
linux-image-extra-3.5.0-25-generic
linux-image-extra-3.5.0-26-generic
linux-image-extra-3.5.0-27-generic
linux-image-extra-3.5.0-28-generic
linux-image-extra-3.5.0-30-generic
linux-image-extra-3.5.0-31-generic
linux-image-extra-3.5.0-32-generic
linux-image-extra-3.5.0-34-generic
linux-image-extra-3.5.0-36-generic
linux-image-extra-3.5.0-37-generic
linux-image-extra-3.5.0-39-generic
linux-image-extra-3.5.0-40-generic
linux-image-extra-3.5.0-41-generic
linux-image-extra-3.5.0-42-generic
linux-image-extra-3.5.0-43-generic

```
the kernel from the other command:
```

matt@matt-Inspiron-1525:~$ uname -r
3.5.0-44-generic

```

---

### Post by nycap on 2013-12-06
Looks like the current kernel is excluded right?  should i just go ahead and do it

---

### Post by r-senior on 2013-12-06
Looks good to me.

So, your new command will be:

```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -v libc | xargs sudo apt-get remove --dry-run
```

If that looks OK, i.e. linux-libc-dev is not listed and neither is your current kernel, you can go for it:

```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -v libc | xargs sudo apt-get remove -y
```

It's going to take a while. It should update grub, but you can always run that at the end. If should list only your current kernel.

```
sudo update-grub
```

Then lets see where you are on disk space:

```
df -h -t ext4
```

---

### Post by Gadgetech on 2013-12-06
I've fixed this in my tutorial by adding
```
grep -E "(image|headers)"
```
This limits it to packages starting with "linux" and containing either "image" or "headers" in their name. This makes the dry run command
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get --dry-run remove
```
or the final command
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get -y purge
```

---

### Post by nycap on 2013-12-06
so here is where we are at with disk space:

```

matt@matt-Inspiron-1525:~$ df -h -t ext4
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        65G   36G   26G  59% /

```

---

### Post by r-senior on 2013-12-06
[quote=nycap]so here is where we are at with disk space:[/quote]

[quote=Gadgetech]I've fixed this in my tutorial by adding[/quote]

Looks like a good result! :)

---

### Post by nycap on 2013-12-06
Have plenty free space here now.  :D  Thanks a bunch!

---

### Post by philinux on 2013-12-08
Good result. Thanks Linerd at tuxtweaks

---

### Post by hokie79 on 2013-12-26
x

---

