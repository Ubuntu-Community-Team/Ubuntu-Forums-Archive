---
title: "HOWTO: Setup VMware Server 1.0.4 on Gutsy (3 Steps, no fuss)"
date: 2007-10-25
forum: Outdated Tutorials &amp; Tips
---

### Post by SilverWave on 2007-10-25
_________________________________________

**HOWTO:**

Install VMware Server 1.0.4 on Ubuntu 7.10.

*Hardy Heron 8.04 users with VMware server 1.0.5 (see note at bottom of page).
_________________________________________

**1 -** Download VMware-server-1.0.4-56528.tar.gz from [www.vmware.com/download/server/](www.vmware.com/download/server/)

**2 -** Issue these commands:
sudo apt-get install build-essential linux-headers-`uname -r`
sudo apt-get install xinetd
cd /home/YOU/MyDownloads
tar -vxzf VMware-server-1.0.4-56528.tar.gz
cd /home/YOU/MyDownloads/vmware-server-distrib
sudo ./vmware-install.pl

**3 - **Answer the questions - defaults are ok.

Applications> System Tools > VMware Server Console

Done :)

Cheers

Note: If you need a serial number for VMware-server get it here:
[http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)




_________________________________________

**Confirmed fixes:**
_________________________________________

**1 - **USB not working: VM > Removable Devices > USB > BLANK
From: [http://ubuntuforums.org/showthread.php?t=588225](http://ubuntuforums.org/showthread.php?t=588225)

Issue the following command:
gksudo gedit /etc/init.d/mountdevsubfs.sh

Before:
```

	#
	# Magic to make /proc/bus/usb work
	#
	#mkdir -p /dev/bus/usb/.usbfs
	#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	#ln -s .usbfs/devices /dev/bus/usb/devices
	#mount --rbind /dev/bus/usb /proc/bus/usb
```

Uncomment the lines as below:

After:
```

	#
	# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Restart and your usb devices will be recognised


**2 - **VMware Wide Screen Issue: missing resolution 1680x1050 (for a new SAMSUNG SyncMaster 226BW).

From: [http://ubuntuforums.org/showthread.php?t=316381&page=2](http://ubuntuforums.org/showthread.php?t=316381&page=2)
Based off: [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003)

Using regedt32 I searched for "Resolution.0" and found two of them in CurrentControlSet.
In each location I created a Binary Key "Resolution.11" .
Added this data to key:
31 36 38 30 78 31 30 35
Rebooted the VM of XP and new resolution showed up, worked like a charm :)

Details:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Contro l\Video\{C90973F8-2114-4C78-BB94-FD8721591CCF}\0000
Resolution.11
31 36 38 30 78 31 30 35
1680x1050.




_________________________________________

**Possible fixes:**
_________________________________________

From: [http://ubuntuforums.org/showthread.php?t=337040](http://ubuntuforums.org/showthread.php?t=337040)

**1 -** Unable to get the last modification timestamp of the destination file /etc/vmware/ssl/rui.key. Execution aborted.
```
sudo touch /etc/vmware/ssl/rui.key
sudo touch /etc/vmware/ssl/rui.crt
```


**2 -** The serial number XXXXX-XXXXX-XXXXX-XXXXX is invalid.
```
sudo apt-get install ia32-libs
sudo /usr/bin/vmware-config.pl
```
Note: See **8 -** as well.


**3 -** /usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
```
sudo apt-get install ia32-libs
```


**4 -** Unable to get the last modification timestamp of the destination file /etc/vmware/ssl/rui.key.
```
sudo apt-get install libc6-i386
```


**5 - **A previous installation of VMware software has been detected - Failure - Execution aborted.

Go into vmware-server-distrib/bin and find the file called "vmware-uninstall.pl"  
[http://ubuntuforums.org/showpost.php?p=3713941&postcount=6](http://ubuntuforums.org/showpost.php?p=3713941&postcount=6)


**6 - ** Issue with  xinetd with Edubuntu or an LTSP setup, clients unable to log in to the server. 

Don't use the command "sudo apt-get install xinetd" in these cases.
[http://ubuntuforums.org/showpost.php?p=3750174&postcount=17](http://ubuntuforums.org/showpost.php?p=3750174&postcount=17)


**7 -** Unable to get the access rights of source file "./vmware-vix/bin". Execution aborted.

In directory ./vmware-vix create symbolic link to ../bin
[http://ubuntuforums.org/archive/index.php/t-260159.html](http://ubuntuforums.org/archive/index.php/t-260159.html)


**8 -** Following packages have unsatisfied dependencies (after sudo apt-get install ia32-libs).
```
Following packages have unsatisfied dependencies:
ia32-libs: Depends on: lib32gcc1 but it is not installable
Depends on: lib32stdc++6 but it is not installable
Depends on: lib32asound2 but it is not installable
Depends on: lib32ncurses5 but it is not installable
```

Could be a problem with the repository.
System > Administration > Software Source
Try switching to the UK or US one. 
[https://answers.launchpad.net/ubuntu/+source/ia32-libs/+question/15484](https://answers.launchpad.net/ubuntu/+source/ia32-libs/+question/15484)




_________________________________________

**Notes:**

Not Tested -  May not apply to server... etc., etc.
_________________________________________

From: [http://communities.vmware.com/message/439407;jsessionid=B96F8395A4BF488CC8D60748B1CDA433](http://communities.vmware.com/message/439407;jsessionid=B96F8395A4BF488CC8D60748B1CDA433)

**1 -** If you issue the command: vmware

The following EM is displayed: /usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)

ericberm may have an answer but I am not sure it applies to Server as well as Workstation. Also server works regardless :)

_________________________________________

***Hardy Heron 8.04 users with VMware server 1.0.5***
This post worked for me:
[http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/)
_________________________________________

Also 64 bit required the following:
sudo sed -i -e ’s/usr\/l3232/usr\/l32/g’ /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
fixes em: Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so:

and to fix em: “.vmware/preferences permission denied”
/home/USER/.vmware/preferences
Permissions were root but needed to be reset to whoever the user is.



Best of luck :)

---

### Post by bryhhh on 2007-10-26
Many thanks. That got me much further than I had managed before, however it doesn't manage to complete for me.

```

The installation of the VMware VmPerl Scripting API succeeded.

Generating SSL Server Certificate

Unable to get the last modification timestamp of the destination file
/etc/vmware/ssl/rui.key.

Execution aborted.

```

The file /etc/vmware/ssl/rui.key doesn't exist

Does anyone have a fix for this, or know where I should start trying to work out what has gone wrong?

---

### Post by SilverWave on 2007-10-26
This could resolve the issue:
```
sudo touch /etc/vmware/ssl/rui.key
sudo touch /etc/vmware/ssl/rui.crt
```

From this post:
[http://ubuntuforums.org/showthread.php?t=337040](http://ubuntuforums.org/showthread.php?t=337040)

Best of luck :)

---

### Post by bryhhh on 2007-10-26
I'm running on 64 bit Ubuntu 7.10, and I've seen other people suggest that, however somebody that posted in this thread [http://communities.vmware.com/thread/32130](http://communities.vmware.com/thread/32130) had the following errors after touching the file

```
sh: /usr/lib/vmware/bin/vmware-vmx: Accessing a corrupted shared library
The serial number xxxxx-xxxxx-xxxxx-xxxxx is invalid.
```

I've followed the advice in that thread (purely because I saw that before I saw your reply), and that allowed me to complete the install.

All I had to do was execute 

```
sudo apt-get install ia32-libs
```

There are reports that the 32 bit packages of libxrender and pam need installing, it doesn't seem to be an issue for me, but I'm not running an X server.

Thanks for your help, I couldn't even get past the kernel module stage until I saw your post. :KS

EDIT: Just followed the link in your last post, which makes most of this post redundant. - Sorry, I should learn to read before typing.

---

### Post by linux4all on 2007-11-05
Hello!

after this:

sudo ./vmware-install.pl

I got This:

A previous installation of VMware software has been detected.

Failure

Execution aborted.

This is a new instalation of gutsy. no home folder .vmware. no etc.
I dont understend this!
any help? thanks

---

### Post by Athanasius on 2007-11-05
If it says that then it means that vmware was installed on your system at one time, maybe vmware player?

If you download vmware server go into vmware-server-distrib/bin and find the file called "vmware-uninstall.pl"

---

### Post by brawa on 2007-11-05
Thank you very much for the guide, but I get the following error message:

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

Any ideas? Sorry I am very new to this all, and thanks in advance.

---

### Post by linux4all on 2007-11-06
> **Athanasius said:**
> If it says that then it means that vmware was installed on your system at one time, maybe vmware player?

If you download vmware server go into vmware-server-distrib/bin and find the file called "vmware-uninstall.pl"

Solved! I just did sudo vmware-uninstall.pl
I tried again and was OK!

Tanks for the help!!

---

### Post by Athanasius on 2007-11-06
What does xinetd do?  I have installed vmware server before but never with that program, what is the purpose of it?

---

### Post by infinite84 on 2007-11-06
I´ve got stuck here, wich i have been almost every time i tried to install vmware.
I´m running a clean install of 7.10 server. Anyone who have a solution?

The correct version of one or more libraries needed to run VMware Server may be
missing.  This is the output of ldd /usr/bin/vmware:
        linux-gate.so.1 =>  (0xffffe000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7f67000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f63000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f4a000)
        libX11.so.6 => not found
        libXtst.so.6 => not found
        libXext.so.6 => not found
        libXt.so.6 => not found
        libICE.so.6 => not found
        libSM.so.6 => not found
        libXrender.so.1 => not found
        libz.so.1 => /usr/lib/libz.so.1 (0xb7f34000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7dea000)
        /lib/ld-linux.so.2 (0xb7f92000)

This program cannot tell for sure, but you may need to upgrade libc5 to glibc
before you can run VMware Server.

---

### Post by endurion on 2007-11-07
Try this:

```
apt-get install linux-headers-`uname -r` libx11-6 libx11-dev x-window-system-core x-window-system xspecs libxtst6 psmisc build-essential
```

Worked for me on vanilla install of Ubuntu 7.10, 32-bit. Vmware server is running beautifully as I type.

---

### Post by fernando_lopes_jr on 2007-11-08
When I try to use the comand:

sudo apt-get install ia32-libs

I get:

E: Couldn't find package ia32-libs

---

### Post by SilverWave on 2007-11-08
Hmm not sure but I would check your software sources 

/etc/apt/sources.list
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

Alternatively use the package manager and search for "ia32-libs" I have tried it and it shows up there on my machine.

---

### Post by SilverWave on 2007-11-08
> **endurion said:**
> Try this:

```
apt-get install linux-headers-`uname -r` libx11-6 libx11-dev x-window-system-core x-window-system xspecs libxtst6 psmisc build-essential
```

Worked for me on vanilla install of Ubuntu 7.10, 32-bit. Vmware server is running beautifully as I type.

hmm that seems like a lot of extras to install if you don't need them.
I would also want to check what they do before installing that lot...
Can you provide a url to your source?

Thanks

---

### Post by SilverWave on 2007-11-08
> **brawa said:**
> Thank you very much for the guide, but I get the following error message:

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

Any ideas? Sorry I am very new to this all, and thanks in advance.

Assuming you are using sudo before your commands... then you could try this:
In directory ./vmware-vix create symbolic link to ../bin
[http://ubuntuforums.org/archive/index.php/t-260159.html](http://ubuntuforums.org/archive/index.php/t-260159.html)

---

### Post by SilverWave on 2007-11-08
> **Athanasius said:**
> What does xinetd do?  I have installed vmware server before but never with that program, what is the purpose of it?

[http://www.xinetd.org/](http://www.xinetd.org/)
> xinetd is a secure replacement for inetd. It was originally written by [email]panos@cs.colorado.edu[/email]. 

[http://www.linuxfocus.org/English/November2000/article175.shtml](http://www.linuxfocus.org/English/November2000/article175.shtml)
> xinetd - eXtended InterNET services daemon - provides a good security against intrusion and reduces the risks of Denial of Services (DoS) attacks. Like the well known couple (inetd+tcpd), it enables the configuration of the access rights for a given machine, but it can do much more. In this article we will discover its many features.

---

### Post by Athanasius on 2007-11-11
A thing that I noticed with the inclusion of xinetd is that in Edubuntu or an LTSP setup, it makes the clients unable to log in to the server.  I have had to reinstall four ties to figure this out.

---

### Post by SilverWave on 2007-11-11
Thanks I have added point 6 to the "possible fixes" section to warn of this issue :)

---

### Post by elec999 on 2007-11-17
I followed every possible guide and keep on getting
giant@GiantQ:~/vmware-server-distrib$ sudo ./vmware-install.pl
Setup is unable to find the "more" program on your machine. Please make sure it
is installed. Do you want to specify the location of this program by hand? 
[yes] 
Thanks

---

### Post by SilverWave on 2007-11-19
> **elec999 said:**
> 
Setup is unable to find the "more" program on your machine. Please make 

Hmm 

At a terminal if I type more and enter I receive this:
```
me@mypc:~$ more
usage: more [-dflpcsu] [+linenum | +/pattern] name1 name2 ...
me@mypc:~$ 

```

What output do you see if you do the same?

---

### Post by SilverWave on 2007-11-26
_________________________________________________

_**VMware Wide Screen Issue.**_

I have a new SAMSUNG SyncMaster 226BW
I cannot see  the resolution that I need.
________________________________________________

FIX:
[http://ubuntuforums.org/showthread.php?t=316381&page=2](http://ubuntuforums.org/showthread.php?t=316381&page=2)
Based off [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003)
Thanks "tocleora"

useing regedt32 I searched for "Resolution.0" and found two of them in CurrentControlSet created "Resolution.11" as a Binary Key in both locations. 
Add 31 36 38 30 78 31 30 35 as the Value Data and rebooted XP - new resolution showed up, worked like a charm :)


HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Video\{C90973F8-3114-4C68-BB94-FD8721591CCF}\0000
Resolution.11
31 36 38 30 78 31 30 35
1680x1050. 

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Video\{F75F1C35-91E7-4BE9-B602-4D9DE64E5C0D}\0000
Resolution.11
31 36 38 30 78 31 30 35
1680x1050.

---

### Post by peofsz1600 on 2007-12-02
Hello, 

I have Ubuntu 7.10 (in Italian) for AMD64 but I cannot Install VMware server.
During execution of vmware-config.pl I got 

/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
The serial number xxxxx-xxxxx-xxxxx-xxxxx is invalid.

I tried to install ia32-libs but I got:

Following packages have unsatisfied dependencies:
  ia32-libs: Depends on: lib32gcc1 but it is not installable
             Depends on: lib32stdc++6 but it is not installable
             Depends on: lib32asound2 but it is not installable
             Depends on: lib32ncurses5 but it is not installable

NB messages are in Italian, and I translated in English thus there may be some differences to native Ubuntu messages.

Thanks
Piero

---

### Post by SilverWave on 2007-12-02
Looks like it could be a problem with the repository?
System > Administration > Software Source
Try switching to the UK or US one?

See here: 
[https://answers.launchpad.net/ubuntu/+source/ia32-libs/+question/15484](https://answers.launchpad.net/ubuntu/+source/ia32-libs/+question/15484)

"switched back to us.archive.ubuntu.com and everything works"

---

### Post by peofsz1600 on 2007-12-04
> **SilverWave said:**
> Looks like it could be a problem with the repository?


You got it.
BTW Italian server is now up to date :)
Thank you very much
Piero

---

### Post by nieekou on 2007-12-04
i just set it up, works like promised, thx for the guide :D
now i want to be able to copy files from ubuntu to vm winxp and backwards..

---

### Post by Scoobie_snack on 2007-12-05
Hey,
Excellent post mate, thanks a lot for the info.
 I have a small problem though. I have installed VM and its running xp, the problem is that it can't see my sound card.. I have media playing through Gutsy so I know its not a problem with hardware but things like Windows Live Messenger (MSN Messenger) can't see my head set or sound card. The options for choosing my sound setting just say "none"... Any ideas?

Thanks again.
Scoobie

:popcorn:

---

### Post by pout on 2007-12-07
I like to install mailcleaner.org on a vmware server 1.04 on a 7.10 server, but installation from iso always stops at hardware detection with:
"mount: mount point /proc/bus/usb does not exist".

I did "confirmed fixes #1"
and also a  
```
sudo mount -t usbfs /dev/bus/usb /proc/bus/usb
```
on host, but this didn't sove the problem.

---

### Post by SilverWave on 2007-12-08
> **pout said:**
> ...

Can you see any USB devices?
Notes:
[http://www.mailcleaner.org/doku.php](http://www.mailcleaner.org/doku.php)

> MailCleaner is a full email filtering gateway. It includes a complete GNU/Linux OS and a graphical web interface for user and administrative access. It comes in the form of an ISO image that contains a fully automated installer..
Download iso here: [http://sourceforge.net/project/showfiles.php?group_id=176202](http://sourceforge.net/project/showfiles.php?group_id=176202)

I'll see if I can install it and post back.
--
[EDIT] Installed the mailcleaner_2006090101.iso all works no problem with VMware, no errors.
Used the Ubuntu VMware option for creating the VM with 512 RAM.
The only issue with MailCleaner is the default keyboard :D 
Hint shift7 is '/'
I installed by setting the CD to where I had saved the iso.

---

### Post by SilverWave on 2007-12-08
> **Scoobie_snack said:**
> ... Live Messenger (MSN Messenger) can't see my head set or sound card. The options for choosing my sound setting just say "none"... Any ideas?


Hi Scoobie,
Just to confirm do you get *any* sound from your XP VM?
Check on the VMware server status bar, bottom right you should see an icon for the sound, if you click this what settings do you see?

Have you installed VMware Tools?

If you are missing the sound on your VMware Virtual Machine, shutdown the VMware Virtual Machine, goto settings and add a sound device.

Notes:
To see the Status bar: View > status bar [ticked].

---

### Post by Scoobie_snack on 2007-12-08
Hey Silver,
Thanks for your reply.
I've been playing with it since posting and I can get sound if I restart the computer and make sure that I run media in the VM first otherwise I get all sorts of errors. What makes this a little more strange is that I have just installed Vista as a VM too, XP has issues seeing my sound card but the Ethernet is fine, Vista is the other way around. All sound card drivers but no internet.

I'm so glad I switched to Linux, windows drives me insane but I just wish I could get the programs I need, working properly.

---

### Post by SilverWave on 2007-12-08
Hi Scobbie,

Glad that you are making some progress :)
If I come across anything I will repost.
If you find a solution please post an update :)

Cheers!

---

### Post by Scoobie_snack on 2007-12-08
Hi again Silver,

I seem to be clicking the right things, I'm only a week or so old in linux so this must be beginer's luck :)

Thus far my problem seems to be with the sound card that Windows has detected.I have updated my drivers and after trying more than enough of them, one finally stuck although its unstable.

I'm not going to lay the blame on VMware though as my computer (3 months old) seems to be full of Via Chrome9 cards... Not the best system to be running Gutsy on as I can never get anything to run right. Although that could just be me :lolflag:

If I get something stable happening, I'll be sure to post it here too. 
:)

---

### Post by SilverWave on 2007-12-08
Hi Scoobie,

I ran across this in researching your issue, not sure if it will be of any use but here you go:
[http://www.networkcomputing.com/article/printFullArticle.jhtml;jsessionid=Q5WSI3HNGJXACQSNDLPSKHSCJUNN2JVN?articleID=197008134](http://www.networkcomputing.com/article/printFullArticle.jhtml;jsessionid=Q5WSI3HNGJXACQSNDLPSKHSCJUNN2JVN?articleID=197008134)

He mentions sound about 1/4 of the way down.

Cheers!

---

### Post by SilverWave on 2007-12-08
> **nieekou said:**
> i just set it up, works like promised, thx for the guide :D
now i want to be able to copy files from ubuntu to vm winxp and backwards..

Hi nieekou,

You can configure samba to do this but tbh I am just using a 320GB USB drive... when I get time I will set samba up honest ;)

Oh and this howto below looks interesting but thats another one I have yet to try ;)

Mount NTFS VMware Virtual Disk Image (vmdk) read/write
here: [http://ubuntuforums.org/showthread.php?p=3797812#post3797812](http://ubuntuforums.org/showthread.php?p=3797812#post3797812)

Cheers!

---

### Post by pout on 2007-12-08
> **SilverWave said:**
> 
--
[EDIT] Installed the mailcleaner_2006090101.iso all works no problem with VMware, no errors.
Used the Ubuntu VMware option for creating the VM with 512 RAM.
The only issue with MailCleaner is the default keyboard :D 
Hint shift7 is '/'
I installed by setting the CD to where I had saved the iso.

Thanks SilverWave!!!
These settings also worked on my installation.
I used "Other Linux" and less than 20GB HD space before. Thanks again.

---

### Post by Scoobie_snack on 2007-12-08
Hey again silver,

Thanks for the link, it looks very interesting and I'm going to give it a go later today (its 2:30 am) and let you know how it goes.
I see that VM has a new beta 2.0, has anyone tried it out yet?

Oh and after sorting my sound in XP, its now lost the video drivers... I'm amazed at the stupidity of the windows programming. Vista can see it and use it but XP can't... Good ol' Bill's at it again!

:popcorn:

---

### Post by JasonStackhouse on 2007-12-08
Incredibly useful thread, thanks to all.  I was all set for a fight and was instead up and running in <20min.

---

### Post by SilverWave on 2007-12-30
Sharing files between a Windows guest and Ubuntu host using VMware and Samba
> VMware Workstation (and presumably the other enterprise-grade products in the VMware family) come with the handy “shared folders” feature which makes sharing files between a host and a virtual appliance nice and simple. The free products (VMware Player and Server) do not, unfortunately, have this ability and so we must find another way.

[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

---

### Post by Clancy_s on 2008-01-22
Thanks for the guide VMware server install worked beautifully for me following your 3 steps ( on a newish install of 64 bit Gutsy).

I'm leaving the XP install for another day...

---

### Post by SilverWave on 2008-05-11
_________________________________________

***Hardy Heron 8.04 users with VMware server 1.0.5***
This post worked for me:
[http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/)
_________________________________________

Also 64 bit required the following:
sudo sed -i -e ’s/usr\/l3232/usr\/l32/g’ /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
fixes em: Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so:

and to fix em: “.vmware/preferences permission denied”
/home/USER/.vmware/preferences
Permissions were root but needed to be reset to whoever the user is.



Best of luck :)

---

