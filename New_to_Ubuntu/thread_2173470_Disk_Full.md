---
title: "Disk Full"
date: 2013-09-09
forum: New to Ubuntu
---

### Post by nuwanga on 2013-09-09
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       228G  216G   15M 100% /
udev           1001M  4.0K 1001M   1% /dev
tmpfs           404M  872K  403M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1009M  120K 1008M   1% /run/shm


It says that my disk is full but all I have done was install Ubuntu and update then I never really touched it.

I found out which folder its in under home/username but when I checked each folder there they were all around 4kb. When I tried du -h home/username it said that the folder was 200+ gb but I couldnt find any file in there that was higher then 1mb. Could be be a cache folder? When it was searching though there was alot of cache folders but I dont know how to check them. but I am not home to reformat and can only use Putty to get in the VNC cant be started up either.

Any ideas on what I should do?

---

### Post by Bashing-om on 2013-09-09
nuwanga; Hi ! Welcome to the forum.

As you seem to have narrowed down to the /home directory. The more likely file to look at is the hidden file ".xsession-errors".
```

ls -la ~/.xsession-errors

```
if indeed this is the culprit .. keep in mind to note the errors prior to removing that file. And then repair the cause of the generation of the error messages.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by oldos2er on 2013-09-10
Moved to Absolute Beginners.

---

### Post by nuwanga on 2013-09-10
So I did do that and got "-rw------- 1 klmnooooo klmnooooo [COLOR=#ff0000]215557312512[/COLOR] Sep  9 17:11 /home/klmnooooo/.xsession-errors"  Then I looked around on how to delete it and used

 [FONT=Ubuntu Mono]rm /wherever/you/have/.xsession-errors[/FONT]ln -s /dev/null /wherever/you/have/.xsession-errors
changed the pathing and it seemed to work

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       228G   15G  201G   7% /
udev           1001M  4.0K 1001M   1% /dev
tmpfs           404M  868K  403M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1009M  120K 1008M   1% /run/shm


It freed up about 200gb. Thing is I dont use that pc but that code I put in should now stop that from happening in the future right?

I knew it would be somthing hidden but didnt know the code to look for it. Thanks Bashing-om!!

---

### Post by Bashing-om on 2013-09-10
nuwanga' Hey;

You are quite welcome. And NO that does not "fix" the problem.
As that file was huge you need to find out why .. what errors are being reported ? .. and correct the issue,
Else in due time that file will once more consume all the disk space.


[INDENT][INDENT]your system needs a helping hand
[/INDENT][/INDENT]

---

### Post by nuwanga on 2013-09-11
Actually yes you're right.I checked again and it is back up to 100% usage. What do you suggest I do?

---

### Post by Bashing-om on 2013-09-11
nuwanga; Hey !

Read that file and determine what error is being reported. When you know the repeated error(s) you may post the error segment back to this forum and we will see about an interpretation and possible action to take.. if the solution is not obvious to you.

[INDENT][INDENT]your system needs your assistance
[/INDENT][/INDENT]

---

### Post by nuwanga on 2013-09-11
So this time it is in a different place. The file is called fileHwealE and I cant go in it in terminal. This file is over 200gb too and the file is located under tmp. Should I delete or investigate it a bit more first. Also its weird since the files last time was hidden xsession and now its in a different place.

---

### Post by Bashing-om on 2013-09-12
nuwanga; Wow..
Ok, unless one is real versatile with managing files, there is not much you can do with a file that large.
What I suggest is to go ahead and delete that file ... and pay close attention to it (and the .xsession-errors file) and when that file is regenerated then load it up and look at it. One may then use utilities such as "cat", "less" or your favorite text editor to look at it.
see; In terminal:
```

man cat
man less

```for usage instruction.

200GB in a few hours is a lot of spam and certainly you need to find the cause.

[INDENT][INDENT]inquiring minds want to know[/INDENT][/INDENT]

---

### Post by nuwanga on 2013-09-12
Well this is interesting. Frist off someone tried to connect to the server I think. It said this for about 5min strait in terminal "11/09/2013 05:16:55 PM Authentication deferred - ignoring client message" after about 100 lines that time would move up a minute. I think someone tried to flush it or something? Also I got two IP's [122.155.13.68]("http://122.155.13.68/") when I put that in google it took me to a program called WorldClient for MDaemon. Here's its wiki [http://en.wikipedia.org/wiki/MDaemon](http://en.wikipedia.org/wiki/MDaemon). The second IP that I saw in the terminal as a crap ton of lines went past with the same 2 IP. That last one and this one 89.111.239.114 that IP is located near Italy. [http://whatismyipaddress.com/ip/89.111.239.114](http://whatismyipaddress.com/ip/89.111.239.114). Also I tried the rm command and deleted that file. Then after I did df -h and it showed that the disk was still full. The file I deleted was around 200gb so I dont know why its still full.

---

### Post by Bashing-om on 2013-09-12
nuwanga; That might be real serious.

Might I suggest open a new thread in the Security subforum on the topic of intrusion. To gain greater visibility. This is out of my experience range and I will not be much help in that respect.

[INDENT]it is a serious matter requiring serious steps
[/INDENT]

---

### Post by nuwanga on 2013-09-12
Alright I will make a post there soon. Thank you for the help so far. Its been very helpful.

---

### Post by Bashing-om on 2013-09-12
nuwanga; Roger that !

Please return to this thread and update/close it when completed.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by nuwanga on 2013-09-15
Well its been a couple of days and it has not happened again. Its been working fine and disk space is staying normal. Should I still take it to security part of forums or forget about it?

---

### Post by Jacob_Sherven on 2013-09-15
I would still take it there so you can see what problems you have with your security to prevent it from happening again.

---

### Post by evertonmint on 2013-09-19
Hi Peeps, I'm getting disk full message and can't figure out how to move memory. As yopou can see there is plenty of space, but everything seems to be goint to the 'boot'?
Any solutions would be greatly welcomed.

Regards

[HTML]Filesystem                 1K-blocks     Used Available Use% Mounted on
/dev/mapper/crownunit-root  74609840 10338412  60481400  15% /
udev                         1016216        4   1016212   1% /dev
tmpfs                         410152      912    409240   1% /run
none                            5120        0      5120   0% /run/lock
none                         1025380      152   1025228   1% /run/shm
/dev/sda1                     233191   231032         0 100% /boot
bill@crownunit:~$ [/HTML]

Evertonmint

---

### Post by ibjsb4 on 2013-09-19
> **evertonmint said:**
> Hi Peeps, I'm getting disk full message and can't figure out how to move memory. As yopou can see there is plenty of space, but everything seems to be goint to the 'boot'?
Any solutions would be greatly welcomed.

Regards

[HTML]Filesystem                 1K-blocks     Used Available Use% Mounted on
/dev/mapper/crownunit-root  74609840 10338412  60481400  15% /
udev                         1016216        4   1016212   1% /dev
tmpfs                         410152      912    409240   1% /run
none                            5120        0      5120   0% /run/lock
none                         1025380      152   1025228   1% /run/shm
/dev/sda1                     233191   231032         0 100% /boot
bill@crownunit:~$ [/HTML]

Evertonmint

This means that your /boot is probably full of old kernels and you need to clean them out.  I use [Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager+remove+old+kernels&sa=Search&cof=FORID:9") for kernel cleaning, but there are [many ways]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9") to do this.

To install SPM [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get install synaptic
```

---

### Post by evertonmint on 2013-09-19
Thanks ibjsb4,
Tried apt-get install synaptic and it came back with;
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.53.63 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ 

How do I proceed?

Regards

> bill@crownunit:~$ apt-get -f install
E: Could not obpen lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
bill@crownunit:~$ 
And this is what I got when trying the advised.

> bill@crownunit:~$ sudo apt-get clean
[sudo] password for bill: 
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
bill@crownunit:~$ 
It gets worse?

---

### Post by evertonmint on 2013-09-19
> bill@crownunit:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-31-generic linux-image-3.2.0-37-generic
  linux-headers-3.2.0-31 linux-headers-3.2.0-32 linux-headers-3.2.0-33
  linux-headers-3.2.0-36 linux-headers-3.2.0-37 linux-headers-3.2.0-38
  linux-headers-3.2.0-37-generic linux-headers-3.2.0-32-generic
  linux-image-3.2.0-38-generic language-pack-kde-en
  linux-headers-3.2.0-38-generic vlc-data linux-headers-3.2.0-33-generic
  language-pack-kde-en-base linux-headers-3.2.0-36-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.2.0-53-generic linux-image-server linux-server
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed
  linux-image-3.2.0-53-generic
The following packages will be upgraded:
  linux-image-server linux-server
2 upgraded, 1 newly installed, 0 to remove and 601 not upgraded.
4 not fully installed or removed.
Need to get 0 B/38.6 MB of archives.
After this operation, 150 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 484887 files and directories currently installed.)
Unpacking linux-image-3.2.0-53-generic (from .../linux-image-3.2.0-53-generic_3.2.0-53.81_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-53-generic_3.2.0-53.81_amd64.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/System.map-3.2.0-53-generic': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-53-generic_3.2.0-53.81_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
bill@crownunit:~$ 


Back to square 1.

---

### Post by Bashing-om on 2013-09-19
evertonmint; Hey,

You have backed yourself into a corner:
> 
failed in write on buffer copy for backend dpkg-deb during `./boot/System.map-3.2.0-53-generic': No space left on device

with no headroom to do anything. However, we can try and manually remove some kernels' images and headers with "apt-get" commands.
Before addressing the method.. lets us see what kernel you are booting:
```

uname -r

```
and what kernels you presently have installed:
```

ls -la /boot
dpkg -l | grep linux-image-

```
and then we can see what might be done to get ya out of that mess.

[INDENT][INDENT]we can try
[/INDENT][/INDENT]

---

### Post by slickymaster on 2013-09-19
> **Bashing-om said:**
> evertonmint; Hey,

You have backed yourself into a corner:

with no headroom to do anything. However, we can try and manually remove some kernels' images and headers with "apt-get" commands.
Before addressing the method.. lets us see what kernel you are booting:
```

uname -r

```
and what kernels you presently have installed:
```

ls -la /boot
pkg -l | grep linux-image-

```
and then we can see what might be done to get ya out of that mess.
[INDENT][INDENT]we can try
[/INDENT]
[/INDENT]


@Bashing-om
Sorry for stepping in so abruptly, I don't mean to be disrespectful, but it's just to point out that there's a typo in your last command, you've missed a 'd' in dpkg.

@OP
The command is:```
dpkg -l | grep linux-image-
```

---

### Post by Bashing-om on 2013-09-19
@ slickymaster, Thanks ! .. I really appreciate that our post are "peer" reviewed. That 2nd typo corrected.

---

### Post by evertonmint on 2013-09-20
Thanks for the help guy's,
> bill@crownunit:~$ uname -r
3.2.0-40-generic
bill@crownunit:~$ ls -la /boot
total 226978
drwxr-xr-x  4 root root     3072 Sep 19 15:22 .
drwxr-xr-x 24 root root     4096 Sep 19 15:22 ..
-rw-r--r--  1 root root   791023 Apr 11  2012 abi-3.2.0-23-generic
-rw-r--r--  1 root root   791281 Jul 27  2012 abi-3.2.0-29-generic
-rw-r--r--  1 root root   791446 Sep  7  2012 abi-3.2.0-31-generic
-rw-r--r--  1 root root   792532 Sep 26  2012 abi-3.2.0-32-generic
-rw-r--r--  1 root root   792532 Oct 18  2012 abi-3.2.0-33-generic
-rw-r--r--  1 root root   792767 Jan  8  2013 abi-3.2.0-36-generic
-rw-r--r--  1 root root   792767 Jan 24  2013 abi-3.2.0-37-generic
-rw-r--r--  1 root root   792830 Feb 19  2013 abi-3.2.0-38-generic
-rw-r--r--  1 root root   794933 Mar 25 22:02 abi-3.2.0-40-generic
-rw-r--r--  1 root root   794996 Apr 25 05:08 abi-3.2.0-41-generic
-rw-r--r--  1 root root   794996 May 15 05:14 abi-3.2.0-43-generic
-rw-r--r--  1 root root   140279 Apr 11  2012 config-3.2.0-23-generic
-rw-r--r--  1 root root   140432 Jul 27  2012 config-3.2.0-29-generic
-rw-r--r--  1 root root   140459 Sep  7  2012 config-3.2.0-31-generic
-rw-r--r--  1 root root   140488 Sep 26  2012 config-3.2.0-32-generic
-rw-r--r--  1 root root   140488 Oct 18  2012 config-3.2.0-33-generic
-rw-r--r--  1 root root   140505 Jan  8  2013 config-3.2.0-36-generic
-rw-r--r--  1 root root   140505 Jan 24  2013 config-3.2.0-37-generic
-rw-r--r--  1 root root   140488 Feb 19  2013 config-3.2.0-38-generic
-rw-r--r--  1 root root   140586 Mar 25 22:02 config-3.2.0-40-generic
-rw-r--r--  1 root root   140622 Apr 25 05:08 config-3.2.0-41-generic
-rw-r--r--  1 root root   140622 May 15 05:14 config-3.2.0-43-generic
drwxr-xr-x  3 root root     5120 Apr 23 07:57 grub
-rw-r--r--  1 root root 14894301 Aug 17  2012 initrd.img-3.2.0-23-generic
-rw-r--r--  1 root root 14927381 Aug 17  2012 initrd.img-3.2.0-29-generic
-rw-r--r--  1 root root 14933321 Oct  5  2012 initrd.img-3.2.0-31-generic
-rw-r--r--  1 root root 14936189 Nov 14  2012 initrd.img-3.2.0-32-generic
-rw-r--r--  1 root root 14935800 Nov 19  2012 initrd.img-3.2.0-33-generic
-rw-r--r--  1 root root 14936076 Jan 28  2013 initrd.img-3.2.0-36-generic
-rw-r--r--  1 root root 14935540 Feb  1  2013 initrd.img-3.2.0-37-generic
-rw-r--r--  1 root root 14923546 Feb 22  2013 initrd.img-3.2.0-38-generic
-rw-r--r--  1 root root 14964501 Apr 23 07:56 initrd.img-3.2.0-40-generic
drwxr-xr-x  2 root root    12288 Aug 16  2012 lost+found
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2884358 Apr 11  2012 System.map-3.2.0-23-generic
-rw-------  1 root root  2882108 Jul 27  2012 System.map-3.2.0-29-generic
-rw-------  1 root root  2883401 Sep  7  2012 System.map-3.2.0-31-generic
-rw-------  1 root root  2884076 Sep 26  2012 System.map-3.2.0-32-generic
-rw-------  1 root root  2884306 Oct 18  2012 System.map-3.2.0-33-generic
-rw-------  1 root root  2886319 Jan  8  2013 System.map-3.2.0-36-generic
-rw-------  1 root root  2886103 Jan 24  2013 System.map-3.2.0-37-generic
-rw-------  1 root root  2887333 Feb 19  2013 System.map-3.2.0-38-generic
-rw-------  1 root root  2890703 Mar 25 22:02 System.map-3.2.0-40-generic
-rw-------  1 root root  2891358 Apr 25 05:08 System.map-3.2.0-41-generic
-rw-------  1 root root  2891358 May 15 05:14 System.map-3.2.0-43-generic
-rw-------  1 root root  4965840 Apr 11  2012 vmlinuz-3.2.0-23-generic
-rw-------  1 root root  4960752 Jul 27  2012 vmlinuz-3.2.0-29-generic
-rw-------  1 root root  4963792 Sep  7  2012 vmlinuz-3.2.0-31-generic
-rw-------  1 root root  4966768 Sep 26  2012 vmlinuz-3.2.0-32-generic
-rw-------  1 root root  4966896 Oct 18  2012 vmlinuz-3.2.0-33-generic
-rw-------  1 root root  4969392 Jan  8  2013 vmlinuz-3.2.0-36-generic
-rw-------  1 root root  4969072 Jan 24  2013 vmlinuz-3.2.0-37-generic
-rw-------  1 root root  4968592 Feb 19  2013 vmlinuz-3.2.0-38-generic
-rw-------  1 root root  4974672 Mar 25 22:02 vmlinuz-3.2.0-40-generic
-rw-------  1 root root  4975248 Apr 25 05:08 vmlinuz-3.2.0-41-generic
-rw-------  1 root root  4974640 May 15 05:14 vmlinuz-3.2.0-43-generic
bill@crownunit:~$ dpkg -l grep linux-image-
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  grep           2.10-1         GNU grep, egrep and fgrep
No packages found matching linux-image-.
bill@crownunit:~$ 

Not sure if the second command was right, don't understand the line between -l and grep

---

### Post by evertonmint on 2013-09-20
'copy paste' drrr
> bill@crownunit:~$ dpkg -l | grep linux-image-
ii  linux-image-3.2.0-23-generic           3.2.0-23.36                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-29-generic           3.2.0-29.46                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-31-generic           3.2.0-31.50                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-32-generic           3.2.0-32.51                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-33-generic           3.2.0-33.52                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-36-generic           3.2.0-36.57                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-37-generic           3.2.0-37.58                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-38-generic           3.2.0-38.61                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-40-generic           3.2.0-40.64                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-41-generic           3.2.0-41.66                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-43-generic           3.2.0-43.68                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iU  linux-image-server                     3.2.0.41.49                                  Linux kernel image on Server Equipment.
bill@crownunit:~$ 


regards
evertonmint

---

### Post by slickymaster on 2013-09-20
As Bashing-om is already helping you, I'll leave to his more than competent hands how you should proceed in order to remove some of those old kernels you have on your system which are at the moment eating a big chunk of space.

I'm just posting just to explain you the part you mention you don't understand.
> ... [COLOR=#000000]the line between -l and grep[/COLOR]is a pipe (it's the vertical bar character, which is located on the same key as the backslash), and is a form of redirection that is used in Linux and other Unix-like operating systems to send the output of one program to another program for further processing.
In this specific command it's transferring the output of ```
dpkg -l
```which lists all packages in **/var/lib/dpkg/status**) to serve as an input to the command```
grep linux-image-
```which searches the named input files for lines containing a match to the given pattern and prints the matching lines.

---

### Post by evertonmint on 2013-09-20
Thank you for that informative explanation Slickymaster, much apprieceiated.

---

### Post by Bashing-om on 2013-09-20
evertonmint; Well .. lets roll the sleeves up and see what we can do:
We are going to try and remove some images and header files ... we do not want the current running kernel removed .. and want to keep 1 kernel as a backup ...let's identify the kernel you are booting:
show us:
```

uname -a
uname -r

```
Tattoo that version on the back of your eyeball ... DO NOT remove it !

Let's see now if we can do this in a "easier" manner; Do in terminal:
```

sudo apt-get --purge remove linux-image-3.2.0-23-generic

```
As a test to see if there is even enough "head room" for the package manager to even work.

[INDENT]slowly - surely, exercise great care
[/INDENT]

---

### Post by evertonmint on 2013-09-20
Bashing-om, I have just picked up your post at home, I will be back at the terminal on Monday, thanks for your help, must appreciated.

Regards

evertonmint.

---

### Post by Bashing-om on 2013-09-20
evertonmint; Roger.

We will pick this back up at that time.

[INDENT][INDENT]a time and a place for all things
[/INDENT][/INDENT]

---

### Post by evertonmint on 2013-09-25
Sorry so late, probs at home, wife in hospital, any way here we are.
> bill@crownunit:~$ uname -a
Linux crownunit 3.2.0-40-generic #64-Ubuntu SMP Mon Mar 25 21:22:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
bill@crownunit:~$ uname -r
3.2.0-40-generic
bill@crownunit:~$ uname -a
Linux crownunit 3.2.0-40-generic #64-Ubuntu SMP Mon Mar 25 21:22:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
bill@crownunit:~$ sudo apt-get --purge remove linux-image3.2.0-23-generic
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image3.2.0-23-generic
E: Couldn't find any package by regex 'linux-image3.2.0-23-generic'
bill@crownunit:~$ 

I eagerly anticipate your answer.

Regards
evertonmint

---

### Post by JKyleOKC on 2013-09-25
> **evertonmint said:**
> Sorry so late, probs at home, wife in hospital, any way here we are.Sorry to see that news; however here's a quick assist with ```
bill@crownunit:~$ sudo apt-get --purge remove linux-imag[COLOR="#FF0000"]e3[/COLOR].2.0-23-generic

```It needs a blank space between the "e" and the "3" that I've highlighted in red. Try it again with that and it should give you more information.

---

### Post by Bashing-om on 2013-09-25
@ JKyleOKC; Thanks for having my back !
My error corrected in the prior post (should have had a '-" in between ...)
Just goes to show ... proper syntax at all times !

@evertonmint; Not done yet !
Do the same procedure for "linux-headers"; See if any persist. Then advise when that is done; to look for any residual config files.

[INDENT][INDENT]it ain't over 'till that fat lady sings
[/INDENT][/INDENT]

---

### Post by evertonmint on 2013-09-30
Thanks for all your assistance, we seem to be moving in the right direction
> bill@crownunit:~$ sudo apt-get --purge remove linux-image-3.2.0-23-generic
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.53.63 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
bill@crownunit:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-31-generic linux-image-3.2.0-37-generic
  linux-headers-3.2.0-31 linux-headers-3.2.0-32 linux-headers-3.2.0-33
  linux-headers-3.2.0-36 linux-headers-3.2.0-37 linux-headers-3.2.0-38
  linux-headers-3.2.0-37-generic linux-headers-3.2.0-32-generic
  linux-image-3.2.0-38-generic language-pack-kde-en
  linux-headers-3.2.0-38-generic vlc-data linux-headers-3.2.0-33-generic
  language-pack-kde-en-base linux-headers-3.2.0-36-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-54 linux-headers-3.2.0-54-generic linux-headers-server
  linux-image-3.2.0-54-generic linux-image-server linux-server
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed
  linux-headers-3.2.0-54 linux-headers-3.2.0-54-generic
  linux-image-3.2.0-54-generic
The following packages will be upgraded:
  linux-headers-server linux-image-server linux-server
3 upgraded, 3 newly installed, 0 to remove and 613 not upgraded.
4 not fully installed or removed.
Need to get 51.3 MB of archives.
After this operation, 217 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-54 all 3.2.0-54.82 [11.7 MB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-54-generic amd64 3.2.0-54.82 [981 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-server amd64 3.2.0.54.64 [1,736 B]
Get:4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-server amd64 3.2.0.54.64 [2,272 B]
Get:5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-3.2.0-54-generic amd64 3.2.0-54.82 [38.6 MB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-server amd64 3.2.0.54.64 [2,276 B]
Fetched 51.3 MB in 49s (1,035 kB/s)                                            
Selecting previously unselected package linux-headers-3.2.0-54.
(Reading database ... 484887 files and directories currently installed.)
Unpacking linux-headers-3.2.0-54 (from .../linux-headers-3.2.0-54_3.2.0-54.82_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-54-generic.
Unpacking linux-headers-3.2.0-54-generic (from .../linux-headers-3.2.0-54-generic_3.2.0-54.82_amd64.deb) ...
Preparing to replace linux-headers-server 3.2.0.53.63 (using .../linux-headers-server_3.2.0.54.64_amd64.deb) ...
Unpacking replacement linux-headers-server ...
Selecting previously unselected package linux-image-3.2.0-54-generic.
Unpacking linux-image-3.2.0-54-generic (from .../linux-image-3.2.0-54-generic_3.2.0-54.82_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-54-generic_3.2.0-54.82_amd64.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-54-generic': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-54-generic /boot/vmlinuz-3.2.0-54-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-54-generic /boot/vmlinuz-3.2.0-54-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-54-generic_3.2.0-54.82_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
bill@crownunit:~$ 


Regards
evertonmint

---

### Post by evertonmint on 2013-09-30
I have tried removing headers to no avail. Seems to be going round and round.
> bill@crownunit:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is installed
E: Unmet dependencies. Try using -f.
bill@crownunit:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-31-generic linux-image-3.2.0-37-generic
  linux-headers-3.2.0-31 linux-headers-3.2.0-32 linux-headers-3.2.0-33
  linux-headers-3.2.0-36 linux-headers-3.2.0-37 linux-headers-3.2.0-38
  linux-headers-3.2.0-37-generic linux-headers-3.2.0-32-generic
  linux-image-3.2.0-38-generic language-pack-kde-en
  linux-headers-3.2.0-38-generic vlc-data linux-headers-3.2.0-33-generic
  language-pack-kde-en-base linux-headers-3.2.0-36-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.2.0-54-generic linux-image-server linux-server
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed
  linux-image-3.2.0-54-generic
The following packages will be upgraded:
  linux-image-server linux-server
2 upgraded, 1 newly installed, 0 to remove and 613 not upgraded.
7 not fully installed or removed.
Need to get 0 B/38.6 MB of archives.
After this operation, 150 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
bill@crownunit:~$ 


Regards
evertonmint

---

### Post by Bashing-om on 2013-09-30
evertonmint; Hey !

Let's do this:
```

dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```
Now, you know what kernel versions you are booting with .. should be the latest (??), keep it as well as one other for a backup.
Remove all other images and headers.
```

sudo apt-get --purge remove linux-image-<version>
sudo apt-get --purge remove linux-headers-<version>

```
The version numbers of image and headers MUST match one to the other on the kernels that you retain !

and clean up:
```

sudo apt-get clean
sudo apt-get --purge autoremove

```
now do once more
```

dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```
See all those files marked as "rc" .. once more:
Now let’s remove all the packages marked as rc.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

and finally what results:
```

sudo apt-get update
sudo apt-get upgrade

```

[INDENT][INDENT]hunky dory now ??
[/INDENT][/INDENT]

---

### Post by evertonmint on 2013-10-02
I have attempted to remove images and headers, but it doesn't seem to be accepting or doing any thing, as for 'files marked, rc?
> bill@crownunit:~$ dpkg -l | grep linux-image-
ii  linux-image-3.2.0-23-generic           3.2.0-23.36                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-29-generic           3.2.0-29.46                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-31-generic           3.2.0-31.50                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-32-generic           3.2.0-32.51                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-33-generic           3.2.0-33.52                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-36-generic           3.2.0-36.57                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-37-generic           3.2.0-37.58                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-38-generic           3.2.0-38.61                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-40-generic           3.2.0-40.64                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-41-generic           3.2.0-41.66                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-43-generic           3.2.0-43.68                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iU  linux-image-server                     3.2.0.41.49                                  Linux kernel image on Server Equipment.
bill@crownunit:~$ dpkg -l | grep linux-headers-
ii  linux-headers-3.2.0-31                 3.2.0-31.50                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-31-generic         3.2.0-31.50                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-32                 3.2.0-32.51                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-32-generic         3.2.0-32.51                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-33                 3.2.0-33.52                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-33-generic         3.2.0-33.52                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-36                 3.2.0-36.57                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-36-generic         3.2.0-36.57                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-37                 3.2.0-37.58                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-37-generic         3.2.0-37.58                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-38                 3.2.0-38.61                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-38-generic         3.2.0-38.61                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-40                 3.2.0-40.64                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-generic         3.2.0-40.64                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-41                 3.2.0-41.66                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-41-generic         3.2.0-41.66                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-43                 3.2.0-43.68                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-43-generic         3.2.0-43.68                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-48                 3.2.0-48.74                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic         3.2.0-48.74                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-52                 3.2.0-52.78                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic         3.2.0-52.78                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-53                 3.2.0-53.81                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic         3.2.0-53.81                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
iU  linux-headers-3.2.0-54                 3.2.0-54.82                                  Header files related to Linux kernel version 3.2.0
iU  linux-headers-3.2.0-54-generic         3.2.0-54.82                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                  3.2.0.43.51                                  Generic Linux kernel headers
iU  linux-headers-server                   3.2.0.54.64                                  Linux kernel headers on Server Equipment.
bill@crownunit:~$ uname -r
3.2.0-40-generic
bill@crownunit:~$ uname -a
Linux crownunit 3.2.0-40-generic #64-Ubuntu SMP Mon Mar 25 21:22:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
bill@crownunit:~$ sudo apt-get --purge remove linux-image-3.2.0-23-generic
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ sudo apt-get --purge remove linux-image-3.2.0-29-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ sudo apt-get --purge remove linux-image-3.2.0-31-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ sudo apt-get --purge remove linux-image-3.2.0-32-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ sudo apt-get --purge remove linux-image-3.2.0-33-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ sudo apt-get --purge remove linux-image-3.2.0-36-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ sudo apt-get --purge remove linux-image-3.2.0-37-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ sudo apt-get --purge remove linux-headers-3.2.0-31-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ sudo apt-get --purge remove linux-headers-3.2.0-32-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ sudo apt-get --purge remove linux-headers-3.2.0-33-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ sudo apt-get --purge remove linux-headers-3.2.0-36-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ sudo apt-get --purge remove linux-headers-3.2.0-37-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ sudo apt-get --purge remove linux-3.2.0-31.50
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-3.2.0-31.50
E: Couldn't find any package by regex 'linux-3.2.0-31.50'
bill@crownunit:~$ sudo apt-get --purge remove linux-3.2.0-32.51
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-3.2.0-32.51
E: Couldn't find any package by regex 'linux-3.2.0-32.51'
bill@crownunit:~$ sudo apt-get clean
bill@crownunit:~$ sudo apt-get --purge autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is installed
E: Unmet dependencies. Try using -f.
bill@crownunit:~$ dpkg -l | grep linux-image-
ii  linux-image-3.2.0-23-generic           3.2.0-23.36                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-29-generic           3.2.0-29.46                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-31-generic           3.2.0-31.50                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-32-generic           3.2.0-32.51                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-33-generic           3.2.0-33.52                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-36-generic           3.2.0-36.57                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-37-generic           3.2.0-37.58                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-38-generic           3.2.0-38.61                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-40-generic           3.2.0-40.64                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-41-generic           3.2.0-41.66                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-43-generic           3.2.0-43.68                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iU  linux-image-server                     3.2.0.41.49                                  Linux kernel image on Server Equipment.
bill@crownunit:~$ dpkg -l | grep linux-headers-
ii  linux-headers-3.2.0-31                 3.2.0-31.50                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-31-generic         3.2.0-31.50                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-32                 3.2.0-32.51                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-32-generic         3.2.0-32.51                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-33                 3.2.0-33.52                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-33-generic         3.2.0-33.52                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-36                 3.2.0-36.57                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-36-generic         3.2.0-36.57                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-37                 3.2.0-37.58                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-37-generic         3.2.0-37.58                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-38                 3.2.0-38.61                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-38-generic         3.2.0-38.61                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-40                 3.2.0-40.64                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-generic         3.2.0-40.64                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-41                 3.2.0-41.66                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-41-generic         3.2.0-41.66                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-43                 3.2.0-43.68                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-43-generic         3.2.0-43.68                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-48                 3.2.0-48.74                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic         3.2.0-48.74                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-52                 3.2.0-52.78                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic         3.2.0-52.78                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-53                 3.2.0-53.81                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic         3.2.0-53.81                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
iU  linux-headers-3.2.0-54                 3.2.0-54.82                                  Header files related to Linux kernel version 3.2.0
iU  linux-headers-3.2.0-54-generic         3.2.0-54.82                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                  3.2.0.43.51                                  Generic Linux kernel headers
iU  linux-headers-server                   3.2.0.54.64                                  Linux kernel headers on Server Equipment.
bill@crownunit:

Regards
evertonmint

---

### Post by Bashing-om on 2013-10-02
evertonmint; Houston, We have a problem.

No head room to operate from makes it tough to do anything. But, let's see if we can resolve the dependency issue.
We can at least try !
See what results from:
```

sudo apt-get --purge remove linux-image-server 3.2.0.41.49
##IF that one is moderately successful; - looks like there may be nothing to (UN)install - run:
sudo apt-get --purge remove linux-headers-server 3.2.0.41.49 ##which is only half configured.

```
Let's take every effort to work from with in the package management system.
We do  not want to go to any manual individual method to remove kernels unless there is no other option. That option is real tedious and can be a real night mare and as well lead to dependency hell to resolve all the lingering config files. 

If fails, might try "dpkg" assets and see if "dpkg" can work in such tight quarters.

[INDENT]when it rains here, it pours
[/INDENT]

---

### Post by evertonmint on 2013-10-03
Looks like this ain't working either?

> bill@crownunit:~$ sudo apt-get --purge remove linux-image-server 3.2.0.41.49
[sudo] password for bill: 
Sorry, try again.
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 3.2.0.41.49
E: Couldn't find any package by regex '3.2.0.41.49'
bill@crownunit:~$ 

regards

---

### Post by evertonmint on 2013-10-03
> bill@crownunit:~$ sudo apt-get --purge remove linux-headers-server 3.2.0.54.64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 3.2.0.54.64
E: Couldn't find any package by regex '3.2.0.54.64'
bill@crownunit:~$ 

Regards

evertonmint

---

### Post by Bashing-om on 2013-10-03
evertonmint;
Let's drop down in package management to the lower level of "dpkg" see if "dpkg" can operate in this situation:
See what kernel you are booting with, and DO NOT remove it !
```

uname -r
sudo dpkg -P linux-image-3.2.0-{23,29,31,32,33,36,37,38,40}-generic

```

If that runs successfully and does get us some head room, will tackle the headers files next !

[INDENT][INDENT]we be try'n
[/INDENT][/INDENT]

---

### Post by JKyleOKC on 2013-10-03
> **evertonmint said:**
> ```
bill@crownunit:~$ sudo apt-get --purge remove linux-headers-[COLOR="#FF0000"]server 3[/COLOR].2.0.54.64
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package 3.2.0.54.64
E: Couldn't find any package by regex '3.2.0.54.64'
bill@crownunit:~$ 
```RegardsThe reason for these two errors is that the blank space in that area I made red should be a hyphen, not a space. Try it again and it ought to work.

However your earlier attempt got this error message and suggestion: > E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
Did you try the suggestion? It might be necessary to clear out some space before it can work, though, so I think the next step should be to try the {purge remove" commands with the space replaced by a dash (in all of them). If you can get rid of at least one old kernel, that ought to leave you some headroom for the "force install" to work.

And another way to get headroom is to check out the content of /var/log which contains dozens of log files. All of them that end in single digits are historical in nature, and in an emergency such as this can be totally deleted with no damage to the system (if you're deleting from a GUI, press the shift key when deleting to force deletion rather than transfer to a trash folder). I've seen this recover more than a gigabyte of space in extreme cases!

@bashing-om: Not meaning to hijack your help, just passing along a couple of points that struck me. I'll go back to lurking now...

---

### Post by Bashing-om on 2013-10-03
@ JKyleOKC. Jim, I am always pleased when you pop in, particularly when you are pulling my chestnuts out of the fire !

[INDENT][INDENT]peer review is so re-assuring 
[/INDENT][/INDENT]

---

### Post by JKyleOKC on 2013-10-03
It's Jim; John is my eldest son! Glad you understand. I don't want to confuse the issue at all...

---

### Post by evertonmint on 2013-10-04
Well no luck there chaps, will try dpkg

> bill@crownunit:~$ sudo apt-get --purge remove linux-headers-server-3.2.0.54.64
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-server-3.2.0.54.64
E: Couldn't find any package by regex 'linux-headers-server-3.2.0.54.64'
bill@crownunit:~$ 

Regards

---

### Post by evertonmint on 2013-10-04
May have dropped a boo boo?

> bill@crownunit:~$ uname -r
_**3.2.0-40-generic**_
bill@crownunit:~$ sudo dpkg -P linux-image-3.2.0-{23,29,31,32,33,36,37,38_**,40**_}-generic
[sudo] password for bill: 
(Reading database ... 506916 files and directories currently installed.)
Removing linux-image-3.2.0-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /memtest86+.bin
ERROR: ddf1: wrong # of devices in RAID set "ddf1_Mirror" [1/2] on /dev/sdb
done
Purging configuration files for linux-image-3.2.0-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
Removing linux-image-3.2.0-29-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found memtest86+ image: /memtest86+.bin
ERROR: ddf1: wrong # of devices in RAID set "ddf1_Mirror" [1/2] on /dev/sdb
done
Purging configuration files for linux-image-3.2.0-29-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
Removing linux-image-3.2.0-31-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found memtest86+ image: /memtest86+.bin
ERROR: ddf1: wrong # of devices in RAID set "ddf1_Mirror" [1/2] on /dev/sdb
done
Purging configuration files for linux-image-3.2.0-31-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
Removing linux-image-3.2.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found memtest86+ image: /memtest86+.bin
ERROR: ddf1: wrong # of devices in RAID set "ddf1_Mirror" [1/2] on /dev/sdb
done
Purging configuration files for linux-image-3.2.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
Removing linux-image-3.2.0-33-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found memtest86+ image: /memtest86+.bin
ERROR: ddf1: wrong # of devices in RAID set "ddf1_Mirror" [1/2] on /dev/sdb
done
Purging configuration files for linux-image-3.2.0-33-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
Removing linux-image-3.2.0-36-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found memtest86+ image: /memtest86+.bin
ERROR: ddf1: wrong # of devices in RAID set "ddf1_Mirror" [1/2] on /dev/sdb
done
Purging configuration files for linux-image-3.2.0-36-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
Removing linux-image-3.2.0-37-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found memtest86+ image: /memtest86+.bin
ERROR: ddf1: wrong # of devices in RAID set "ddf1_Mirror" [1/2] on /dev/sdb
done
Purging configuration files for linux-image-3.2.0-37-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
Removing linux-image-3.2.0-38-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found memtest86+ image: /memtest86+.bin
ERROR: ddf1: wrong # of devices in RAID set "ddf1_Mirror" [1/2] on /dev/sdb
done
Purging configuration files for linux-image-3.2.0-38-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
_**Removing linux-image-3.2.0-40-generic .**_..
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-40-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found memtest86+ image: /memtest86+.bin
ERROR: ddf1: wrong # of devices in RAID set "ddf1_Mirror" [1/2] on /dev/sdb
done
Purging configuration files for linux-image-3.2.0-40-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
bill@crownunit:~$ 


regards
evertonmint

---

### Post by evertonmint on 2013-10-04
> bill@crownunit:~$ dpkg -l | grep linux-image-
iF  linux-image-3.2.0-41-generic           3.2.0-41.66                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-43-generic           3.2.0-43.68                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iU  linux-image-server                     3.2.0.41.49                                  Linux kernel image on Server Equipment.
bill@crownunit:~$ dpkg -l | grep linux-headers-dpkg -l | grep linux-headers-
bill@crownunit:~$ 

Looks like we have no headers?

Regards

---

### Post by evertonmint on 2013-10-04
> bill@crownunit:~$ uname -r
3.2.0-40-generic
bill@crownunit:~$ 


thanks for all your help,  				 					[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar374258_2.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=374258") 				 				 					 						 	[**[COLOR=#000000]JKyleOKC[/COLOR]**]("http://ubuntuforums.org/member.php?u=374258")  &  				 					[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1111508_1.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1111508") 				 				 					 						 	[**[COLOR=#000000]Bashing-om[/COLOR]**]("http://ubuntuforums.org/member.php?u=1111508") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]

It is much appreciated.
evertonmint.

---

### Post by Bashing-om on 2013-10-04
evertonmint; Whoohww ! May have dodged that bullet.
Let's look.
```

uname -r
dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```
Make sure version numbers are same same between image and headers.

[INDENT]pretty descent operating system[/INDENT]

---

### Post by evertonmint on 2013-10-05
Bashing-om

unmae -r
dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-



This is answered in my last two post's, as I said, it looks like we have no headers?

Regards
evertonmint.

---

### Post by Bashing-om on 2013-10-05
evertonmint; Hey.

What I want to see is current updated  info .. I find it hard to understand that one can even boot up if those hearer files are missing.
Strickly out of concern for your well being.
```

uname -r
ls -la /boot
dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```
[INDENT][INDENT]anything worth doing is worth doing right 
[/INDENT][/INDENT]

---

### Post by JKyleOKC on 2013-10-05
Bill has two kernel image files, according to the report from his last run of grub updating, and that's all he needs to boot. The header files are necessary only when rebuilding the kernel or kernel modules during an update. I *think* he can get the headers back by installing the generic header package, which will have the current version's header files as dependencies, but I'm not absolutuely sure of this. Using Synaptic package manager, though, he should be able to find and install the specific header packages for the two kernel image versions he has...

I'm a bit concerned that his previous run of uname showed 3.2.0-40, which he then removed (with a warning message) and the two he still has are newer versions. Also, did the cleanup take care of the original Disk Full problem, so that he has room to complete the update that was failing?

---

### Post by Bashing-om on 2013-10-05
@ JKyleOKC; Thanks for that confirmation to my thinking process .. thought that might be the case for the headers files ..
As you say, if we can boot we can fix easy-est . And hey, it's ubuntu - with a liveDVD and good backups, we can fix anything !
(broken hearts take longer)

A current status for confirmation and direction.

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by evertonmint on 2013-10-05
Hi boy's, those last two post's were after I did Bashing-om's dpkg purge suggestion. 
I haven't done clean up or autoremove. In fact I haven't shut it down since I started trying to remove the junk.
I was surprised to see the  3.2.0-40 after it 'erased' so to speak.
I tried Jim's suggestion first yesterday, putting the '-' instead of space, to no avail, then copied and pasted Basing-om's suggestion.
When it finished I hit uname -r to see what we had and then had a look at images and headers, which is were it is now.
What do you suggest for Monday?

Regards 
evertonmint.

---

### Post by evertonmint on 2013-10-05
Sorry,
"[COLOR=#000000]When it finished I hit uname -r to see what we had and then had a look at images and headers, which is were it is now."

This should read the other way around. Images then headers and finally because I was interested in what I was running on, uname -r.




Cheers[/COLOR]

---

### Post by Bashing-om on 2013-10-05
evertonmint; Hey !

Remove all confusion - on my part - and show NOW what is.
```

uname -r
ls -la /boot
dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```
will put my spirit to rest.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by evertonmint on 2013-10-07
Bashing-om; Here we go boy, this is as is now.

> bill@crownunit:~$ uname -r
3.2.0-40-generic
bill@crownunit:~$ ls -la /boot
total 17644
drwxr-xr-x  4 root root    3072 Oct  4 12:38 .
drwxr-xr-x 24 root root    4096 Sep 19 15:22 ..
-rw-r--r--  1 root root  794996 Apr 25 05:08 abi-3.2.0-41-generic
-rw-r--r--  1 root root  794996 May 15 05:14 abi-3.2.0-43-generic
-rw-r--r--  1 root root  140622 Apr 25 05:08 config-3.2.0-41-generic
-rw-r--r--  1 root root  140622 May 15 05:14 config-3.2.0-43-generic
drwxr-xr-x  3 root root    5120 Oct  4 12:38 grub
drwxr-xr-x  2 root root   12288 Aug 16  2012 lost+found
-rw-r--r--  1 root root  176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root  178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root 2891358 Apr 25 05:08 System.map-3.2.0-41-generic
-rw-------  1 root root 2891358 May 15 05:14 System.map-3.2.0-43-generic
-rw-------  1 root root 4975248 Apr 25 05:08 vmlinuz-3.2.0-41-generic
-rw-------  1 root root 4974640 May 15 05:14 vmlinuz-3.2.0-43-generic
bill@crownunit:~$ dpkg -l | grep linux-image-
iF  linux-image-3.2.0-41-generic           3.2.0-41.66                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-43-generic           3.2.0-43.68                                  Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iU  linux-image-server                     3.2.0.41.49                                  Linux kernel image on Server Equipment.
bill@crownunit:~$ dpkg -l | grep linux-headers-
ii  linux-headers-3.2.0-31                 3.2.0-31.50                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-31-generic         3.2.0-31.50                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-32                 3.2.0-32.51                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-32-generic         3.2.0-32.51                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-33                 3.2.0-33.52                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-33-generic         3.2.0-33.52                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-36                 3.2.0-36.57                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-36-generic         3.2.0-36.57                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-37                 3.2.0-37.58                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-37-generic         3.2.0-37.58                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-38                 3.2.0-38.61                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-38-generic         3.2.0-38.61                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-40                 3.2.0-40.64                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-generic         3.2.0-40.64                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-41                 3.2.0-41.66                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-41-generic         3.2.0-41.66                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-43                 3.2.0-43.68                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-43-generic         3.2.0-43.68                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-48                 3.2.0-48.74                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic         3.2.0-48.74                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-52                 3.2.0-52.78                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic         3.2.0-52.78                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-53                 3.2.0-53.81                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic         3.2.0-53.81                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
iU  linux-headers-3.2.0-54                 3.2.0-54.82                                  Header files related to Linux kernel version 3.2.0
iU  linux-headers-3.2.0-54-generic         3.2.0-54.82                                  Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                  3.2.0.43.51                                  Generic Linux kernel headers
iU  linux-headers-server                   3.2.0.54.64                                  Linux kernel headers on Server Equipment.
bill@crownunit:~$ 


Regards

evertonmint

---

### Post by Bashing-om on 2013-10-07
evertonmint; Yuk !

I am uncertain how to get out of this mess.
You are booting with kernel 3.2.0-40-generic, but according to the dpkg out put, it is not even installed:
> 
bill@crownunit:~$ dpkg -l | grep linux-image-
iF linux-image-3.2.0-41-generic 3.2.0-41.66 Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF linux-image-3.2.0-43-generic 3.2.0-43.68 Linux kernel image for version 3.2.0 on 64 bit x86 SMP

from that output you have no "image" fully installed.. and tons of headers files that do need to be removed.

Lets see what we can do when those headers files are removed, and try and (re-)install the latest kernel.
```

sudo apt-get --purge remove linux-headers-3.2.0-{31,32,33,36,38,40,48,52,54}
sudo apt-get --purge remove linux-headers-3.2.0-{31,32,33,36,38,40,48,52,54}-generic
sudo apt-get install linux-generic linux-headers-generic linux-image-generic

```
 Can't really say in a situation as this,

[INDENT][INDENT]but we can at least try
[/INDENT][/INDENT]

---

### Post by evertonmint on 2013-10-08
Bashing-om; Hi as you can see I haven't tried any of the suggestions. Just wondering,
Which of these would be the 'desktop' version?

> bill@crownunit:~$ sudo apt-get --purge remove linux-headers-3.2.0-{31,32,33,36,38,40,48,52,54}
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-headers-3.2.0-31-generic : Depends: linux-headers-3.2.0-31 but it is not going to be installed
 linux-headers-3.2.0-32-generic : Depends: linux-headers-3.2.0-32 but it is not going to be installed
 linux-headers-3.2.0-33-generic : Depends: linux-headers-3.2.0-33 but it is not going to be installed
 linux-headers-3.2.0-36-generic : Depends: linux-headers-3.2.0-36 but it is not going to be installed
 linux-headers-3.2.0-38-generic : Depends: linux-headers-3.2.0-38 but it is not going to be installed
 linux-headers-3.2.0-40-generic : Depends: linux-headers-3.2.0-40 but it is not going to be installed
 linux-headers-3.2.0-48-generic : Depends: linux-headers-3.2.0-48 but it is not going to be installed
 linux-headers-3.2.0-52-generic : Depends: linux-headers-3.2.0-52 but it is not going to be installed
 linux-headers-3.2.0-54-generic : Depends: linux-headers-3.2.0-54 but it is not going to be installed
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ sudo apt-get --purge remove linux-headers-3.2.0-{31,32,33,36,38,40,48,52,54}-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-headers-server : Depends: linux-headers-3.2.0-54-generic but it is not going to be installed
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ sudo apt-get install linux-generic linux-headers-generic linux-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-generic : Depends: linux-image-3.2.0-54-generic but it is not going to be installed
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.54.64 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bill@crownunit:~$ 


Regards

evertonmint.

---

### Post by Bashing-om on 2013-10-08
evertonmint; That's tough !
All of those headers listed are for the desktop (31 through and inclusive of 54).
Quite frankly, I do not even have a comprehension of how you are able to boot with no kernel image fully installed, nor the image you are booting even shown as installed. The kernel must have something up it's sleeve I am unaware of ! 

Let's try and see if we can give the package manager what It thinks it wants.
```

sudo apt-get install linux-headers-server-3.2.0.41.49

```

Then maybe we can do the cleanup ??? -> ultimate goal is two images with matching headers files installed and operational.

[INDENT][INDENT]this has become interesting
[/INDENT][/INDENT]

---

### Post by evertonmint on 2013-10-09
Bashing-om Sorry lad, no luck there?

> bill@crownunit:~$ sudo apt-get install linux-headers-server-3.2.0.41.49
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-server-3.2.0.41.49
E: Couldn't find any package by regex 'linux-headers-server-3.2.0.41.49'
bill@crownunit:~$ 

Regards

---

### Post by Bashing-om on 2013-10-09
evertonmint; Not what I wanted to see !

OK, let's try it as more generic:
```

sudo apt-get install linux-headers-server-3.2.0-41

```

I am in ->
[INDENT][INDENT]a learning mode too
[/INDENT][/INDENT]

---

### Post by evertonmint on 2013-10-10
Bashing-om; Me thinks the server is also?

> bill@crownunit:~$ sudo apt-get install linux-headers-server-3.2.0-41
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-server-3.2.0-41
E: Couldn't find any package by regex 'linux-headers-server-3.2.0-41'
bill@crownunit:~$ 

regards

---

### Post by evertonmint on 2013-10-10
Bashing-om;
Should I close down and try restarting?
As I said earlier, since we started this, I haven't closed down at all.

---

### Post by Bashing-om on 2013-10-10
evertonmint; I do not think rebooting and/or shutting down the system right now is a good idea at all. As the kernel that you are booting is not even installed.

As to the "sever" kernels, As I have no indication that you are running a server, and the majority of kernels that were and are installed are the desk top versions, we are going to try and eliminate the server kernels, and of utmost priority is to get you a image and corresponding headers for the latest kernel installed.
Trying to wrap my head around this as to why the package manager will not deal with this:
show:
```

ls -la /var/cache/apt/archives/linux-image*
ls -la /var/cache/apt/archives/linux-headers*
apt-cache policy linux-image* | grep Installed
ls -la /usr/src/
ls -la /var/lib/dpkg/info/linux*.list

```
I honestly do not know, if worst comes to worst, will try and remove them manually. Got to get the latest kernel to install !

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by evertonmint on 2013-10-11
Bashing-om; A long list of nothing?
> bill@crownunit:~$ ls -la /var/cache/apt/archives/linux-image*
ls: cannot access /var/cache/apt/archives/linux-image*: No such file or directory
bill@crownunit:~$ ls -la /var/cache/apt/archives/linux-image
ls: cannot access /var/cache/apt/archives/linux-image: No such file or directory
bill@crownunit:~$ ls -la /var/cache/apt/archives/linux-headers*
ls: cannot access /var/cache/apt/archives/linux-headers*: No such file or directory
bill@crownunit:~$ apt-cache policy linux-image* | grep Installed
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: 3.2.0-43.68
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: 3.2.0-41.66
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: 3.2.0.41.49
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
bill@crownunit:~$ ls -la /usr/src/
total 112
drwxr-xr-x 28 root root 4096 Sep 30 11:23 .
drwxr-xr-x 11 root root 4096 Aug 17  2012 ..
drwxr-xr-x 24 root root 4096 Sep 27  2012 linux-headers-3.2.0-31
drwxr-xr-x  7 root root 4096 Sep 27  2012 linux-headers-3.2.0-31-generic
drwxr-xr-x 24 root root 4096 Nov 14  2012 linux-headers-3.2.0-32
drwxr-xr-x  7 root root 4096 Nov 14  2012 linux-headers-3.2.0-32-generic
drwxr-xr-x 24 root root 4096 Nov 19  2012 linux-headers-3.2.0-33
drwxr-xr-x  7 root root 4096 Nov 19  2012 linux-headers-3.2.0-33-generic
drwxr-xr-x 24 root root 4096 Jan 28  2013 linux-headers-3.2.0-36
drwxr-xr-x  7 root root 4096 Jan 28  2013 linux-headers-3.2.0-36-generic
drwxr-xr-x 24 root root 4096 Feb  1  2013 linux-headers-3.2.0-37
drwxr-xr-x  7 root root 4096 Feb  1  2013 linux-headers-3.2.0-37-generic
drwxr-xr-x 24 root root 4096 Feb 22  2013 linux-headers-3.2.0-38
drwxr-xr-x  7 root root 4096 Feb 22  2013 linux-headers-3.2.0-38-generic
drwxr-xr-x 24 root root 4096 Apr 23 07:55 linux-headers-3.2.0-40
drwxr-xr-x  7 root root 4096 Apr 23 07:55 linux-headers-3.2.0-40-generic
drwxr-xr-x 24 root root 4096 May  2 07:50 linux-headers-3.2.0-41
drwxr-xr-x  7 root root 4096 May  2 07:50 linux-headers-3.2.0-41-generic
drwxr-xr-x 24 root root 4096 May 16 07:38 linux-headers-3.2.0-43
drwxr-xr-x  7 root root 4096 May 16 07:38 linux-headers-3.2.0-43-generic
drwxr-xr-x 24 root root 4096 Jun 27 11:53 linux-headers-3.2.0-48
drwxr-xr-x  7 root root 4096 Jun 27 11:53 linux-headers-3.2.0-48-generic
drwxr-xr-x 24 root root 4096 Aug 20 14:23 linux-headers-3.2.0-52
drwxr-xr-x  7 root root 4096 Aug 20 14:23 linux-headers-3.2.0-52-generic
drwxr-xr-x 24 root root 4096 Sep 19 13:09 linux-headers-3.2.0-53
drwxr-xr-x  7 root root 4096 Sep 19 13:09 linux-headers-3.2.0-53-generic
drwxr-xr-x 24 root root 4096 Sep 30 11:23 linux-headers-3.2.0-54
drwxr-xr-x  7 root root 4096 Sep 30 11:23 linux-headers-3.2.0-54-generic
bill@crownunit:~$ ls -la /var/lib/dpkg/info/linux*.list
-rw-r--r-- 1 root root  23634 Apr 27 07:57 /var/lib/dpkg/info/linux-firmware.list
-rw-r--r-- 1 root root 558723 Sep 27  2012 /var/lib/dpkg/info/linux-headers-3.2.0-31-generic.list
-rw-r--r-- 1 root root 881992 Sep 27  2012 /var/lib/dpkg/info/linux-headers-3.2.0-31.list
-rw-r--r-- 1 root root 558800 Nov 14  2012 /var/lib/dpkg/info/linux-headers-3.2.0-32-generic.list
-rw-r--r-- 1 root root 881992 Nov 14  2012 /var/lib/dpkg/info/linux-headers-3.2.0-32.list
-rw-r--r-- 1 root root 558800 Nov 19  2012 /var/lib/dpkg/info/linux-headers-3.2.0-33-generic.list
-rw-r--r-- 1 root root 881992 Nov 19  2012 /var/lib/dpkg/info/linux-headers-3.2.0-33.list
-rw-r--r-- 1 root root 559071 Jan 28  2013 /var/lib/dpkg/info/linux-headers-3.2.0-36-generic.list
-rw-r--r-- 1 root root 881992 Jan 28  2013 /var/lib/dpkg/info/linux-headers-3.2.0-36.list
-rw-r--r-- 1 root root 559071 Feb  1  2013 /var/lib/dpkg/info/linux-headers-3.2.0-37-generic.list
-rw-r--r-- 1 root root 881992 Feb  1  2013 /var/lib/dpkg/info/linux-headers-3.2.0-37.list
-rw-r--r-- 1 root root 559006 Feb 22  2013 /var/lib/dpkg/info/linux-headers-3.2.0-38-generic.list
-rw-r--r-- 1 root root 881992 Feb 22  2013 /var/lib/dpkg/info/linux-headers-3.2.0-38.list
-rw-r--r-- 1 root root 559351 Apr 23 07:55 /var/lib/dpkg/info/linux-headers-3.2.0-40-generic.list
-rw-r--r-- 1 root root 881152 Apr 23 07:55 /var/lib/dpkg/info/linux-headers-3.2.0-40.list
-rw-r--r-- 1 root root 559351 May  2 07:50 /var/lib/dpkg/info/linux-headers-3.2.0-41-generic.list
-rw-r--r-- 1 root root 881992 May  2 07:50 /var/lib/dpkg/info/linux-headers-3.2.0-41.list
-rw-r--r-- 1 root root 559351 May 16 07:38 /var/lib/dpkg/info/linux-headers-3.2.0-43-generic.list
-rw-r--r-- 1 root root 881992 May 16 07:38 /var/lib/dpkg/info/linux-headers-3.2.0-43.list
-rw-r--r-- 1 root root 559351 Jun 27 11:53 /var/lib/dpkg/info/linux-headers-3.2.0-48-generic.list
-rw-r--r-- 1 root root 881992 Jun 27 11:53 /var/lib/dpkg/info/linux-headers-3.2.0-48.list
-rw-r--r-- 1 root root 559433 Aug 20 14:23 /var/lib/dpkg/info/linux-headers-3.2.0-52-generic.list
-rw-r--r-- 1 root root 881992 Aug 20 14:23 /var/lib/dpkg/info/linux-headers-3.2.0-52.list
-rw-r--r-- 1 root root 559433 Sep 19 13:09 /var/lib/dpkg/info/linux-headers-3.2.0-53-generic.list
-rw-r--r-- 1 root root 881992 Sep 19 13:09 /var/lib/dpkg/info/linux-headers-3.2.0-53.list
-rw-r--r-- 1 root root 559433 Sep 30 11:23 /var/lib/dpkg/info/linux-headers-3.2.0-54-generic.list
-rw-r--r-- 1 root root 881992 Sep 30 11:23 /var/lib/dpkg/info/linux-headers-3.2.0-54.list
-rw-r--r-- 1 root root    168 May 16 07:38 /var/lib/dpkg/info/linux-headers-generic.list
-rw-r--r-- 1 root root    165 Sep 30 11:23 /var/lib/dpkg/info/linux-headers-server.list
-rw-r--r-- 1 root root 274118 May  2 07:50 /var/lib/dpkg/info/linux-image-3.2.0-41-generic.list
-rw-r--r-- 1 root root 274118 May 16 07:38 /var/lib/dpkg/info/linux-image-3.2.0-43-generic.list
-rw-r--r-- 1 root root    159 May  2 07:50 /var/lib/dpkg/info/linux-image-server.list
-rw-r--r-- 1 root root  23286 May 16 07:38 /var/lib/dpkg/info/linux-libc-dev:amd64.list
-rw-r--r-- 1 root root    141 May  2 07:50 /var/lib/dpkg/info/linux-server.list
-rw-r--r-- 1 root root    456 Aug 17  2012 /var/lib/dpkg/info/linux-sound-base.list
bill@crownunit:~$ 

See you Monday :icon_frown:

Regards

---

### Post by Bashing-om on 2013-10-11
evertonmint; Yep, a long list of nothing, Are you seeing now what the nature of the problem is, and why you should not shut the machine down ?

Let's try this and see:
```

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get --purge remove linux-headers-3.2.0-{31,32,33,36,38,40,48,52,54}

```

Later we will re-build that index file. After we get these headers and old-image files removed.

[INDENT][INDENT]try try again
[/INDENT][/INDENT]

---

### Post by evertonmint on 2013-10-14
Morning Bashing-om;
We are up a creek without a paddle. I came in and the screen would not come on, server was running. I had to close down, I placed a ubuntu 12.4 disc in it comes up with an 'option' screen;
Ubuntu, with Linux 3.2.0-43 generic
Ubuntu, with Linux 3.2.0-43 generic (recovery mode)
Previous Linux versions
Mem test 86+
Mem test 86+, serial console 115200

On the first three it won't boot, I get message
> Autorun   Done
cannot open root device "root=" boot options;
[0.826950] please append correct "root=" boot option;here are available partitions
[0.827034] 0800     78150744 sda driver : sd
[0.827130]    0801        248832 sda1
[0.827228]    0802                1 sda2
[0.827326]    0805        77899776 sda5
[0.827518] kernel panic -not syning : VFS : unable to mount root fs on unknown-block(0,0)
[11.100134] pid : 1, comm : swapper/0 Not tainted 3.2.0-43 generic #68-ubuntu
[11.100196] call trace:
[11.100259] [<ffffffff81645fb1>] panic+0x91/0x1a4
[11.100322] [<ffffffff81cfd02d>] mount_block_root+0xdc/0x18e
[11.100386] [<ffffffff81002930>] ? populate_rootfs_wait+0x300/0x9d0
[11.100448] [<ffffffff81cfd266>] mount_root+0x54/0x59
[11.100508] [<ffffffff81cfd3d8>] prepare_namespace+0x16d/0x1a6
[11.100570] [<ffffffff81cfcd72>] kernel_init+0x15f/0x164
[11.100632] [<ffffffff81669234>] kernel_thread_helper+0x4/0x10
[11.100694] [<ffffffff81cfcc13>] ? start_kernel+0x3c2/0x3c2
[11.100755] [<ffffffff81669230>] ? gs_change+0x13/0x13


Sorry about this looks like it wont even accept a disc now?
regards

evertonmint :(

---

### Post by Bashing-om on 2013-10-14
evertonmint; With a liveCD/DVD/USB we ->

Are never without that paddle. However, if we are going to salvage this installation will have to jump through some hoops.

This could be a learning experience for the both of us ! Change rooting into the install system from the liveCD; fumbling around in the install trying to get the package manager back into a consistent state, remove those old kernel files and then install the current kernel. Can be done. But, upfront, it is going to be a trial and I expect no little amount of tribulation.

Keep in mind that if the frustration level becomes oppressive, there is always the option from the liveCD to copy your data off that hard disk and (RE-)install ubuntu from scratch. 

Set in bios to boot from the CD drive as the 1st boot priority;
Boot the liveCD to the desktop in "try ubuntu" mode.

When you can do this .. will discuss change rooting. Hopefully you are in a position where you can focus full attention to this.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by evertonmint on 2013-10-15
It is set to 'boot from disc' as 1st priority and this is the box I get;
> [COLOR=#000000]Ubuntu, with Linux 3.2.0-43 generic[/COLOR]
[COLOR=#000000]Ubuntu, with Linux 3.2.0-43 generic (recovery mode)[/COLOR]
[COLOR=#000000]Previous Linux versions[/COLOR]
[COLOR=#000000]Mem test 86+[/COLOR]
[COLOR=#000000]Mem test 86+, serial console 115200[/COLOR][COLOR=#000000]
[/COLOR]
At the bottom it say's scroll up or down and select what option to boot 'or' press 'c' for command line!

[COLOR=#000000]When I try 'Previous Linux versions it gives me 3.2.0-41 with a similar option as the others.[/COLOR]
[COLOR=#000000]The desktop didn't come up, which is why I had to shut down in the first place.[/COLOR]
[COLOR=#000000]I submitted the last reply from another machine and had to type that code in myself.

This option does not present it'self; [/COLOR][COLOR=#000000]"try ubuntu" mode.[/COLOR][COLOR=#000000]
regards

evertonmint[/COLOR]

---

### Post by Bashing-om on 2013-10-15
evertonmint; Welp;

That menu is from the install, not from the liveCD. That do imply;
a) priority not set in bios,
b) the CD is not bootable, (corrupted)
c) the disk drive has died, (bios no longer brings it up)
d) perhaps there is some key combo at boot time to boot from the CD.

Until we can boot that liveCD, we are indeed "dead in the water".

Fast check: take that liveCD to another box - resetting the boot priority - and see if it boots there.

Booting the CD is not an operating system thing, that is all done within bios.

[INDENT][INDENT]we don't miss the water 'till the well runs dry
[/INDENT][/INDENT]

---

### Post by evertonmint on 2013-10-16
Bashing-om;

In Bios 
ROM-Based Setup Utility, V 2.10
Boot Controller Order
Ctlr :1  PCI Embedded Intel (R) 82801 GR SATA Controller  (This is highlited)
Ctlr :2  PCI Embedded HP Intergrated PCI  IDE Controller

Standard Boot Order
IPL :1 CD-ROM                   This is selected.
IPL :2 Floppy disc    (A:)
IPL :3 USB DriveKey (C:)
IPL :4 Hard Drive C: (see Boot Controller Order)
IPL :5 PCI Embedded HP NC320i PCIe Gigabit Server Adapter Port 1

Regards

evertonmint

---

### Post by Bashing-om on 2013-10-16
evertonmint; welp ......
Certainly looks like the cd drive is set as 1st boot priority.

Aside: do you really have a floppy drive installed on that box ? If not, disable that option, no sense in wasting bios' time and resources hunting for a device that does not exist.

Still need to boot up a livemedium ! Either the CD or USB .. MOST preferable to be the same version as what is actually installed. Now, not to teach grampa how to suck eggs, but; in trying to isolate the booting fault;
Will your system boot a different bootable CD ?
Will the present liveCD boot in a different box ? 
Fault isolation can be an art in in own right !

[INDENT][INDENT]the right tool for the right job
[/INDENT][/INDENT]

---

### Post by evertonmint on 2013-10-17
Bashing-om;
I have downloaded to USB 12.4.03 Lts server AMD 64 ISO will take it with me later on.
I know the disc works as it's the same one I used to install Ubuntu on the server, what I did notice when in Bios yesterday, it wouldn't let me change from SATA to HP Integrated?
Perhaps if I change to IPL : 4 and then to HP?
Then back to IPL : 3? And try booting from USB? Wouldn't this then let Ubuntu format SATA, when installing?

Speak later
Regards.
evertonmint

---

### Post by evertonmint on 2013-10-17
Bashing-om;
It won't let me change anything?
Every time I change it reverts back?
On start up it tells me the SATA write cache is disabled?
Success!
I put the USB in and it fired up, even though the IPL is set to CD?

Now, how do I stop all this happening again?

Cheers Bashing-om
Regards

Evertonmint

---

### Post by Bashing-om on 2013-10-17
evertonmint;
BIOS: I am not at all familiar with your version of bios, however all the bios I have encountered, one must choose explicitly to save any changes made to the bios for the change to take effect.

Status update: You are now able to boot to "try ubuntu" mode from the leveUSB ? Such that we can now try and salvage the install with the change root routine ?

I have in mind to change root into the install from that liveMedium, and see if the package manager will install a kernel for us - as the headers are still present -  from "sudo apt-get install -f" command.

[INDENT][INDENT]hey, it might happen !
[/INDENT][/INDENT]

---

### Post by Azzurra on 2013-10-18
Hi everyone!!
I have a problem and by the title of the thread I think I can have some help...
I am used to work on an external hard drive (eHD). I needed to copy into the eHD a big folder (70GB). Since the available space inside the disk was approximately 100GB i thougth it was not a problem. On the contrary, when I tried to copy the folder, the message "there is not enough space in the drive" appeard. Looking around I saw that deleting a file just using "canc" or "rm" from the shell, does not completely erase files so that they remain in the drive occupying free space. Now, I do not really now how to re-call those files and how to completely erase them.
Where they should be???
I hope someone can hel me!!
Thanks
Azzurra

---

### Post by evertonmint on 2013-10-18
Bashing-om;
I have an HP Proliant ML 310

because there was nothing of importance in the mem I have re-installed, this is where we are now;
> bill@bill:~$ uname -r
3.8.0-29-generic
bill@bill:~$ ls -la /boot
total 25848
drwxr-xr-x  3 root root     4096 Oct 18 14:24 .
drwxr-xr-x 23 root root     4096 Oct 18 13:32 ..
-rw-r--r--  1 root root   919604 Aug 14 17:42 abi-3.8.0-29-generic
-rw-r--r--  1 root root   154969 Aug 14 17:42 config-3.8.0-29-generic
drwxr-xr-x  3 root root    12288 Oct 18 13:42 grub
-rw-r--r--  1 root root 16389790 Oct 18 14:24 initrd.img-3.8.0-29-generic
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  3187899 Aug 14 17:42 System.map-3.8.0-29-generic
-rw-------  1 root root  5426416 Aug 14 17:42 vmlinuz-3.8.0-29-generic
bill@bill:~$ dpkg -l | grep linux-image-
ii  linux-image-3.8.0-29-generic           3.8.0-29.42~precise1                    Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-raring         3.8.0.29.29                             Generic Linux kernel image
bill@bill:~$ dpkg -l | grep linux-headers-
ii  linux-headers-3.8.0-29                 3.8.0-29.42~precise1                    Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-29-generic         3.8.0-29.42~precise1                    Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-raring       3.8.0.29.29                             Generic Linux kernel headers
bill@bill:~$ 


Regards
evertonmint.

---

### Post by Bashing-om on 2013-10-18
evertonmint; Hey !

(RE-)installing is always a sure-fire fix !.. The nuclear approach works. Though we learn little or nothing from doing so.

I am concluding that this matter is resolved and no further action is required. If you are happy, I am tickled to no end.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-10-18
@ Azzurra; Hi !
The "disk full" maybe a bit misleading if one does not know the linux file system hierarchy. That often means that a "partition" is full.
Let's see if your problem does relate to this thread:
Post the output of terminal commands:
```

df -h
df -i
du -h --max-depth=1 | sort -hr

```

Aside:
Linux (ubuntu) assumes that you know exactly what you are doing - and does not forgive mistakes. If you "rm" a file from the terminal (shell); That file is gone gone and that space is available. The average user will not be able to recover any file removed with a terminal command ! Though it can be done, it takes a deep, intimate knowledge of the inner workings of the file system (inodes and related pointers to where on disk the info is located).

If one wants to "find" a file on the file system, use the "find" command, "locate" will also do the job if the relational database is kept up to date.
To search your entire file system for a particular file - here my example is the file "xcopy". do:
```

sudo find / -name xcopy

```
Will take a bit of time to get the result as it takes time to search the entire file system of thousands and thousands of files, looking for a match.
see:
```

man find

```

let us see ->
[INDENT][INDENT]what is to be done
[/INDENT][/INDENT]

---

### Post by evertonmint on 2013-10-19
[COLOR=#000000][[COLOR=#000000]Bashing-om[/COLOR]]("http://ubuntuforums.org/member.php?u=1111508") [/COLOR]
[COLOR=#000000][/COLOR][IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]
 Thanks for your help, though I wonder why a new install didn't 'install' the latest images and headers? 
Also, as I meander through, what is not to stop this happening again, later down the line?

Again, thanks for your help.

Regards

evertonmint ; )  PS; Do I close this now, or are you continuing with Azzurra?

---

### Post by Bashing-om on 2013-10-19
evertonmint; Hey !

As to the kernel installed, what is installed is what was available on the install disk - which can never be what is current . When you do the update routine:
```

sudo apt-get update
sudo apt-get upgrade

```
then the latest kernel will be installed.

And as to filling up /boot, yes it will happen again unless you practice house keeping. "apt-get" has recently been "upgraded" to where the command:
```

sudo apt-get autoremove

``` will remove all but the latest two kernels, providing that NO old kernels from prior releases are installed on your system. This sure makes a simple procedure that much simpler !
Now housecleaning .. on occasion, as you feel the need: and look;
```

df -h
df -i
du -h --max-depth=1 | sort -hr
##or maybe something like:
du -h /<dir> | sort -nr | less ##for large directories
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```is all there is to house cleaning. If the "df" and "du" commands indicate a problem, it is no longer housecleaning, but a maintenance detail.

My PS for edit: Closing thread; nope, only the original poster may close a thread..
We will see what other posters pop up with. However, posting in another's thread limits the visibility of that thread to that person taking the responsibility of maintaining that thread. Other responders may not see additional posters.

Nothing to it ... just sometimes ->
[INDENT][INDENT][INDENT]the garbage has to be taken out
[/INDENT][/INDENT][/INDENT]

---

