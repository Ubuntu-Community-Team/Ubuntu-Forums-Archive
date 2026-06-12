---
title: "Installing Truecrypt 4.2 on Ubuntu 6.06"
date: 2006-06-18
forum: Outdated Tutorials &amp; Tips
---

### Post by kabronkline on 2006-06-18
[SIZE=4]*** UPDATE: Truecrypt + GUI Frontend is installable via Automatix for 32-Bit Ubuntu ***
*** I will no longer be updating this post, feel free to make use of any of this text in any way ***
*** If you would like to repost this as a 64-Bit install guide, PM Me... I'll give you the entire thread text (formatting and all) ***

THANKS FOR ALL THE SUPPORT! 
[/SIZE]

TrueCrypt is Free open-source disk encryption software for Windows XP/2000/2003 and Linux.

Main Features:
* Creates a virtual encrypted disk within a file and mounts it as a real disk.
* Encrypts an entire hard disk partition or a device, such as USB flash drive.
* Encryption is automatic, real-time (on-the-fly) and transparent.
* Provides two levels of plausible deniability, in case an adversary forces you    to reveal the password:
* Hidden volume (steganography).
* No TrueCrypt volume can be identified (volumes cannot be distinguished from random data).
* Encryption algorithms: AES-256, Blowfish (448-bit key), CAST5, Serpent, Triple DES, and Twofish.
* Mode of operation: LRW (CBC supported as legacy).

[SIZE=4]This post contains TWO METHODS for how to install TrueCrypt on NEW version of Ubuntu 6.06, including new version of Ubuntu Dapper kernel (this is important, since Dapper updated kernel through security updates).[/SIZE]
[SIZE=4][B]
ONLY USE METHOD #2 IF METHOD #1 DOESN'T WORK![/B][/SIZE]

**[SIZE=4]METHOD #1[/SIZE]**

**1. Download TrueCrypt 4.2a debian (.deb) installer at: [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php) to your _home directory._ The debian installer is wrapped inside a tar file. If you have a standard 32-bit kernel select "Ubuntu 6.06 x86" from the drop-down menu. If you have a 64-bit kernel select "Ubuntu 6.06 x86-64 from the drop-down menu.**

**2. Download the debian installer into your _Home_ folder and then un-tar it in your home folder and run the following command seperately:**

**32-Bit Kernel:**
> cd
tar -xvf truecrypt-4.2a-ubuntu-6.06-x86.tar.gz**64-Bit Kernel:**
> cd
tar -xvf truecrypt-4.2a-ubuntu-6.06-x86-64.tar.gz**3. After the file is untarred execute the following commands seperately:**

**Install the debian file with the following commands:**
> cd truecrypt-4.2a
sudo dpkg -i truecrypt_4.2a-0_i386.deb**4. Execute the following command to allow non-sudo users access to mount Truecrypt volumes:**
> sudo chmod u+s /usr/bin/truecryptKudos to everybody posting in this thread for contributing this method to the HowTo... cheers!

**[SIZE=4]METHOD #2[/SIZE]**

**1. Download TrueCrypt 4.2a source code at: [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php) (tar.gz version) to your _home directory_ by selecting "Other (source code)" from the drop-down menu.**

**2. Run the following commands:**
> cd
tar xvfz truecrypt-4.2a-source-code.tar.gzFor security purposes, download the gpg signature file and then import the key with command:
> gpg --keyserver subkeys.pgp.net --recv F0D6B1E0Verify the signature by running the following command:
> gpg --verify truecrypt-4.2a-source-code.tar.gz.sig truecrypt-4.2-source-code.tar.gz**3. Check the version of your Linux kernel by running the following command:**
> uname -r**4. For instance, if it is 2.6.15-25-386 - so we have to install the source and create a symbolic link for version 2.6.15 by running the following commands:**
> sudo apt-get install linux-source-2.6.15
cd /usr/src/
sudo tar xvjf linux-source-2.6.15.tar.bz2
sudo ln -s linux-source-2.6.15 linux
**5. Install required tools needed for compiling the source by running the following commands:**
> sudo apt-get install build-essential**6. Check which version your kernel was compiled with by running the following commands:**
> cat /proc/versionThe output should look something like the following:
[I]> Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
[/I]
**7. Verify that gcc 4.0 is Installed by running the following command:**
> 
sudo apt-get install gcc-4.0
**8. Install TrueCrypt by running the following commands:**
> cd
cd truecrypt-4.2a/Linux/
sudo ./build.shIf you run into problems during this step please consult this reply: [http://www.ubuntuforums.org/showpost.php?p=1171019&postcount=18](http://www.ubuntuforums.org/showpost.php?p=1171019&postcount=18)

**9. Once the build is complete run the following command:**
> sudo ./install.shDuring this process you will be prompted three different times immediately after the script executes. For the first prompt press the "Enter" key, for the second prompt specify the location of the man pages as "/usr/share/man", for the third prompt provide either "y" for yes or "N" for no. (Aside from the first prompt which I pressed the "Enter" on, I have provided below the answers I chose during install marked in **bold**. If you want to allow all users on your machine to use Truecrypt make sure to input "Y" for question #3 below. Note allowing non-admins users to run Truecrypt will allow ALL users access to the program.
> 1. Install binaries to [/usr/local/bin]:
2. Install man page to [/usr/local/man]: **/usr/share/man**
3. Allow non-admin users to run TrueCrypt [y/N]:**Y**If you chose "Y" (i.e., yes) to question #3 above, please execute the following command:
> 
sudo chmod u+s /usr/bin/truecrypt
[SIZE=4]That's it, install is finished. The following are all commands for the operation of Truecrypt.[/SIZE]

**Mounting a TC volume named "secure.tc" from a USB device to the directory "/mnt" :**
> 1. sudo truecrypt /media/usbdisk/secure.tc /mnt/If you are prompted with just "password:" after running the command you will need to insert your Ubuntu login password to supply SUDO with appropriate permissions. However, if you see the below in your command line simply provide the TC volume password and everything should mount without any problems:

> Enter password for '/media/usbdisk/secure.tc':**Unmount the drive:**
> cd
sudo truecrypt -d**Check if it is really unmounted (If total = 0, there isn't a truecrypt volume mounted):**
> ls -l /mnt/**List all mounted TrueCrypt partitions:**
> sudo truecrypt -vl**Create a Truecrypt volume using the wizard:**
> truecrypt -cHave fun and also check the documentation: [http://www.truecrypt.org/documentation.php](http://www.truecrypt.org/documentation.php)

Credit and thanks go out to Ubuntuforums member *virtadept* for his previous post that can be found at [http://ubuntuforums.org/showthread.php?t=114225&highlight=truecrypt](http://ubuntuforums.org/showthread.php?t=114225&highlight=truecrypt).
Without his help this post would not be here and all our data would still be insecure! 

**This guide has been reported working for Ubuntu 6.06, both 32 and 64 bit editions.**
**IF YOU USE THIS HOW-TO, PLEASE CONTRIBUTE BY POSTING A REPLY WITH YOUR RESULTS**

---

### Post by rso on 2006-06-19
hi,

what happens after a kernel update?
do I have to do this again after each kernel update?

thanx for the well written how to!

richard

---

### Post by kabronkline on 2006-06-19
I'm not entirely sure of the answer to your question; however, to my understanding as long as the release is 2.6.15 there will be no need to reinstall Truecrypt.

---

### Post by dilidon on 2006-06-19
Hi,
Thanks for the guide. Just what I needed, as I have all my documents and pictures backed up in some TrueCrypt volumes from WinXP days, and now I need to restore them. And as any kind of configure/make/make install or kernel compilation is still a mystery that fails 95% of the times tried, a step-by-step guide including the requirements like gcc and similar (even though I had them) as well is most welcome for many beginners, I would think. It is not as self-evident as gurus would think.:roll: 

Now, as for the installation, during step 9 I got the following error:
> Checking build requirements...
Error: Kernel source code is incomplete - header file dm.h not found.
Any suggestions for continuing? Followed every step and got no erros before.

---

### Post by w00d77 on 2006-06-19
[QUOTE=dilidon]
...Now, as for the installation, during step 9 I got the following error:

Any suggestions for continuing? Followed every step and got no erros before.[/QUOTE]

You most likely don't have the headers installed for your kernel.  Use this command:
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by dilidon on 2006-06-19
[QUOTE=w00d77]You most likely don't have the headers installed for your kernel.  Use this command:
```
sudo apt-get install linux-headers-`uname -r`
```[/QUOTE]
Thanks for the recommendation. That's however the puzzling part. I thought I had them and the command confirms this by saying "linux-headers-2.6.15-23-386 is already the newest version."](*,)
Removed them and reinstalled them, but that was of little help.

---

### Post by kabronkline on 2006-06-19
This seems to be very puzzling.... I would imagine somebody around here can provide the answer! If so, I'll add it in to the how-to.

---

### Post by alaaji on 2006-06-20
I'm having trouble with truecrypt too.  I had it working under Breezy but now I can't get it to work under Dapper.  I get this message once I enter the password for my encrypted volume:

FATAL: Error inserting truecrypt (/lib/modules/2.6.15-25-686/extra/truecrypt.ko): Invalid module format
truecrypt: Failed to load TrueCrypt kernel module

Does it have anything to do with me using the 686 kernel now?

---

### Post by kabronkline on 2006-06-20
Changing kernal version can definitely break Truecrypt. Try following my howto for Dapper if you haven't already.

Hopefully, we can get some GURUs in here to clarify some things. Hopefully this guide can grow and become more useful..... hopefully.

---

### Post by alaaji on 2006-06-21
I tried recompiling & reinstalling the program to no avail.  I'll check back periodically to see if anyone has a solution.  Thanks!

Anybody have any ideas?

---

### Post by cbudden on 2006-06-21
How can I create a truecrypt volume?

---

### Post by cornelis1 on 2006-06-21
One of the new features of version 4.2 is the following: [URL="http://www.truecrypt.org/user-guide/?s=version-history"]

*The build.sh script can now perform automatic configuration of the Linux kernel source code, which is necessary in order to compile TrueCrypt on Linux. Note that this works only if the installed version of the kernel enables/supports it.*

This means that you don't have to follow step 8 of the how to, which (as is my experience with version 4.1) a bit of a hassle. I succesfully compiled Truecrypt 4.2 under Dapper this way. I,m not sure if it is necessary to follow steps 6 and 7 of the how to: I didn't but, I had gcc-4.0 installed already.

During the running of the install-script you're asked where to install the binaries and the man pages. I set this to /usr/bin and /usr/share/man.

---

### Post by kabronkline on 2006-06-21
If somebody could please explain to me what is holding back Truecrypt, or the Ubuntu community, from building a deb install package to greatly simplify all of this I would greatly appreciate it. With the increasing use of portable media, primarily USB media, the need for encryption is ever increasing just the same.

Or perhaps, is there an alternative software application out there that works on multiple platforms, such as Truecrypt, that would work better?

I appreciate your time guys....

---

### Post by aerials on 2006-06-22
[QUOTE=kabronkline]
**7. So we need gcc 4.0 (subversion 4.0.x is not important). Install it by running the following command:**
[/B]
[/QUOTE]

Isn't gcc 4.0 already installed as a dependency of the meta-package build-essential?

Great how-to by the way, no I know what to do with my weekend :mrgreen:

---

### Post by kabronkline on 2006-06-22
Yes, GCC 4.0 is included with Ubuntu 6.06; however, the original HowTo I used for Ubuntu 5.10 had this step included, so I just updated the steps as-per that guide. However, it doesn't break anything even if you have GCC 4 installed and thus I decided to include it just incase there were any potential situations where GCC isn't installed (if that's even possible?).

...Just taking a stab at it.

---

### Post by jvl on 2006-06-22
[QUOTE=alaaji]I'm having trouble with truecrypt too.  I had it working under Breezy but now I can't get it to work under Dapper.  I get this message once I enter the password for my encrypted volume:

FATAL: Error inserting truecrypt (/lib/modules/2.6.15-25-686/extra/truecrypt.ko): Invalid module format
truecrypt: Failed to load TrueCrypt kernel module

Does it have anything to do with me using the 686 kernel now?[/QUOTE]

Recompile & reinstall truecrypt, if you change your kernel version. It's pretty straightforward.

---

### Post by jvl on 2006-06-22
[QUOTE=cbudden]How can I create a truecrypt volume?[/QUOTE]

```
truecrypt -c
```would start new volume creation "wizzard"*.

more info in the manual page or at [http://www.truecrypt.org/user-guide/linux-manpage.php]("http://www.truecrypt.org/user-guide/linux-manpage.php")

* it's cli and there are no "NEXT" buttons, could it be called wizzard? :-D

---

### Post by dilidon on 2006-06-22
[QUOTE=dilidon]Thanks for the recommendation. That's however the puzzling part. I thought I had them and the command confirms this by saying "linux-headers-2.6.15-23-386 is already the newest version."](*,)
Removed them and reinstalled them, but that was of little help.[/QUOTE]
Thanks kabronkline and w00d77, for the guide and for thinking along. I wanted to give it one last try before reinstalling Windows XP only to get my documents out of my containers. And I found a solution to my problem. I will post it here a) for the Howto and b) for someone else, who might be experienceing this. Its one of those moments when you are happy that you've studied languages and your Internet is not only confined to your own and then English language.:rolleyes:
As usual, I *did* do everything by the book, but stumbled across one of those numerous building and installing problems that will keep driving beginning people away from Ubuntu (or any other distro). The solution is easy but no newbie will ever come up with this kind of a solution.
I found the solution from [http://wiki.ubuntuusers.de/TrueCrypt](http://wiki.ubuntuusers.de/TrueCrypt). Search for "Fehlerbehandlung" on the page and its quite self evident. What was needed was to edit the build.sh file and replace
```
KERNEL_SRC=/usr/src/linux-$(uname -r)
```
with
```
KERNEL_SRC=/usr/src/linux-source-2.6.15 
```.
After that it took only a few moments to get things up and running.:twisted: Got some other erros from install.sh, which were probably permissions related, but these were in human language so it was easy to find their causes and correct them.

Just a general remark or question. Why do these things happen? I mean, yes, the solution, once found, is easy. But no newbie will ever look for this.  I really want to stay with Ubuntu, but things like this little problem shouldn't even happen, if it's gonna be "Linux for Human Beings". These kinds of bulding problems are quite frustrating for those starting up - you follow every comma in every howto, and still, you are out of luck. You learn bit by bit, but still. If you work in a non-computer-related field then the amount of time you can devote to understanding kernel compilation and similar will forever be limited. So, you go: Requirements? Check. Sources and headers? Check. And then... somewhere in fine print it's written that "oh, and then, in case its raining, edit the files in this and this manner". I'm not whining, really. I'm really greatful to all of those devoting their time to guides and howto-s and tips, I'm just curious whats the underlying cause if these little problems that will keep scaring off a significant bunch of beginners.:-k Is this simply the moment when you say that "there is no such thing as a free lunch" after all? :D

---

### Post by cbudden on 2006-06-22
[QUOTE=jvl]```
truecrypt -c
```would start new volume creation "wizzard"*.

more info in the manual page or at [http://www.truecrypt.org/user-guide/linux-manpage.php]("http://www.truecrypt.org/user-guide/linux-manpage.php")

* it's cli and there are no "NEXT" buttons, could it be called wizzard? :-D[/QUOTE]

Why thank you!

---

### Post by rso on 2006-06-23
Hi,

I found encfs, it does not work for windows, but in dapper it is really easy to install and use:
[https://wiki.ubuntu.com/encryption_with_encfs_and_pam-encfs](https://wiki.ubuntu.com/encryption_with_encfs_and_pam-encfs)

apt-get and no need for recompiling the kernel after each upgrade. 

richard

---

### Post by jvl on 2006-06-23
[QUOTE=rso]Hi,
no need for recompiling the kernel after each upgrade. 
[/QUOTE]

The only thing you have to recompile is the truecrypt kernel module, not the whole kernel!

---

### Post by rso on 2006-06-23
[QUOTE=jvl]The only thing you have to recompile is the truecrypt kernel module, not the whole kernel![/QUOTE]
Cool,
could you please post the steps one has to do after a kernel update?
with the "use old config" option.

Thanks

---

### Post by jvl on 2006-06-23
```

tar xvzf truecrypt-4.2.tar.gz
sudo bash
cd truecrypt-4.2/Linux
./build.sh
./install.sh

```

The kernel source of the current running kernel is under /usr/src/linux-$(uname -r)

It's basically like new installation.

Hope this helps.

---

### Post by kabronkline on 2006-06-23
[QUOTE=rso]Hi,

I found encfs, it does not work for windows, but in dapper it is really easy to install and use:
[https://wiki.ubuntu.com/encryption_with_encfs_and_pam-encfs](https://wiki.ubuntu.com/encryption_with_encfs_and_pam-encfs)

apt-get and no need for recompiling the kernel after each upgrade. 

richard[/QUOTE]

Will Truecrypt decrypt the volumes created with ENCFS and vice versa?

---

### Post by kabronkline on 2006-06-23
[QUOTE=dilidon]
Just a general remark or question. Why do these things happen? I mean, yes, the solution, once found, is easy. But no newbie will ever look for this.  I really want to stay with Ubuntu, but things like this little problem shouldn't even happen, if it's gonna be "Linux for Human Beings". These kinds of bulding problems are quite frustrating for those starting up - you follow every comma in every howto, and still, you are out of luck. You learn bit by bit, but still. If you work in a non-computer-related field then the amount of time you can devote to understanding kernel compilation and similar will forever be limited. So, you go: Requirements? Check. Sources and headers? Check. And then... somewhere in fine print it's written that "oh, and then, in case its raining, edit the files in this and this manner". I'm not whining, really. I'm really greatful to all of those devoting their time to guides and howto-s and tips, I'm just curious whats the underlying cause if these little problems that will keep scaring off a significant bunch of beginners.:-k Is this simply the moment when you say that "there is no such thing as a free lunch" after all? :D[/QUOTE]

I totally agree with you on this point; however, I think that Ubuntu has a real chance to give Windows a run for it's money. With that said, it is we in the community that must refine this product by identifying problems and providing clear action steps for the developers to address. At this stage in the Ubuntu project it appears that providing HowTo's is merely a tool for other power-users to take advantage of -- to expect a novice Windows users to use anything other than a Wizard for configuration is just plain asking to much.

How does this tie in with this HowTo topic? I ask that those among us, such as yourself, clearly explain problems and steps nesseccary for resolution. Could you please eleborate on your instructions to fix the build errors so that I can update the HowTo? Future, if anybody out there finds errors or something missing from the HowTo, you know what to do.... post away.

---

### Post by dilidon on 2006-06-23
[QUOTE=kabronkline] Could you please eleborate on your instructions to fix the build errors so that I can update the HowTo? Future, if anybody out there finds errors or something missing from the HowTo, you know what to do.... post away.[/QUOTE]
Cheers. Thanks for commenting. However, this time I can't really elaborate any further than that crucial change in the *build.sh* file which I already indicated in my previous post. There seems to a problem that without this the headers are not found or smth. The German Ubuntu site did not elaborate on the reasons in detail. However, the fix that I decribed works. So you could append it to the howto with a "and-in-case-this-happens" or troubleshooting clause just like the German one had.

The other very minor error that I got during installation was that the installer could not copy the man pages to the default location it itself offered. This resulted in and error and termination of the install. The error was quite clear, however, saying that a directory */usr/local/share/man/man1* does not exist (the default offered by the program was */usr/local/share/man*, after which I simply pressed enter at first). So, after the failed attempt I manually created that folder, which it couldn't find or create, and ran the install again. After that, ok.

---

### Post by rso on 2006-06-23
During the kernel compile I got the following problem:
```

drivers/usb/net/zd1211/zdhw.c:1748: warning: unused variable ‘reg’
CC [M] drivers/usb/net/zd1211/zddebug.o
drivers/usb/net/zd1211/zddebug.c: In function ‘zd1205_dump_regs’:
drivers/usb/net/zd1211/zddebug.c:57: warning: unused variable ‘flags’
CC [M] drivers/usb/net/zd1211/zdtkipseed.o
CC [M] drivers/usb/net/zd1211/zdmic.o
DEVLIST drivers/usb/net/zd1211/zddevlist.h
make[5]: *** [drivers/usb/net/zd1211/zddevlist.h] Error 1
make[4]: *** [drivers/usb/net/zd1211] Error 2
make[3]: *** [drivers/usb/net] Error 2
make[2]: *** [drivers/usb] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.15'
make: *** [stamp-build] Error 2

```

I solved it by editing the file:
```

sudo gedit /usr/src/linux/drivers/usb/net/zd1211/zddevlist.h

```

replace line
```
#error
```
with
```
//#error
```

This is not great but now the kernel compiles and there are no errors so far.

---

### Post by kabronkline on 2006-06-23
Thanks guys for your feedback! I have updated the HowTo with links to these replies if anybody should run into any problems.

---

### Post by kabronkline on 2006-06-23
I found an interesting post on the Truecrypt forums, check it out:

[http://forums.truecrypt.org/viewtopic.php?t=3156]("http://forums.truecrypt.org/viewtopic.php?t=3156")

I believe this is a pre-compiled binary? I will be testing this binary out later for verification. If it successfully installs I will be revising the HowTo so that I can include both methods for install, pre-compiled binary and self-compiled binaries. Let me know about any feedback you might have!

---

### Post by marcip on 2006-06-23
Hi there;
As a stop-gap solution, I've posted the binary package on:
[http://www.savefile.com/files/1316093](http://www.savefile.com/files/1316093)

the md5 sum of the file is:
6117f6d6e13ec70fc094d07aa44572bc tc_dapper.tar

Download the tar archive, un-tar it in any temporary directory and run:
sudo ./install.sh

This should work as long as the main kernel version number remains 2.6.15... . However, "sudo ./install.sh" part has to be re-done whenever the 'sub-number' (for instance, from 2.6.15-25-386 to 2.6.15-28-386) changes. I'll try to re-compile and post the update (and report here) if there is a main kernel number change and TrueCrypt is not included in Ubuntu (see below).  

A few comments, if I may:

Write to Ubuntu distribution owners with demands/suggestions to include TrueCrypt in their "official" application repository. They refuse to do that due to the doctrinal reasons: TrueCrypt is open source, but the license is not GPL, and that seems to make it unpalatable to to them. However, no alternative comes even remotely close to TC in terms of both security and utility; this (AND the fact it's open source, so it can be inspected) is all that users care about.

Linux will not replace Windows until there is a stable binary kernel interface, and that will not happen as long as the inept linux kernel hackers do not understand that USERS DO NOT COMPILE APPLICATIONS!  Or, failing that, Ubuntu will not replace Windows until Ubuntu distribution authors do not understand that any ONE UBUNTU RELEASE DOES NOT CHANGE KERNEL VERSIONS. If, in addition, linux application writers would be willing to learn from MacOSX application packaging - what a world it would be... :)
cheers, marcip

---

### Post by kabronkline on 2006-06-24
> **marcip]Hi there said:**
> http://www.savefile.com/files/1316093[/url]

the md5 sum of the file is:
6117f6d6e13ec70fc094d07aa44572bc tc_dapper.tar

Download the tar archive, un-tar it in any temporary directory and run:
sudo ./install.sh

This should work as long as the main kernel version number remains 2.6.15... . However, "sudo ./install.sh" part has to be re-done whenever the 'sub-number' (for instance, from 2.6.15-25-386 to 2.6.15-28-386) changes. I'll try to re-compile and post the update (and report here) if there is a main kernel number change and TrueCrypt is not included in Ubuntu (see below).  

A few comments, if I may:

Write to Ubuntu distribution owners with demands/suggestions to include TrueCrypt in their "official" application repository. They refuse to do that due to the doctrinal reasons: TrueCrypt is open source, but the license is not GPL, and that seems to make it unpalatable to to them. However, no alternative comes even remotely close to TC in terms of both security and utility; this (AND the fact it's open source, so it can be inspected) is all that users care about.

Linux will not replace Windows until there is a stable binary kernel interface, and that will not happen as long as the inept linux kernel hackers do not understand that USERS DO NOT COMPILE APPLICATIONS!  Or, failing that, Ubuntu will not replace Windows until Ubuntu distribution authors do not understand that any ONE UBUNTU RELEASE DOES NOT CHANGE KERNEL VERSIONS. If, in addition, linux application writers would be willing to learn from MacOSX application packaging - what a world it would be... :)
cheers, marcip

Awesome... I will be posting your instruciton in the HowTo as the primary method for install. The manual method will only be secondary. Thanks big time for your support!

---

### Post by rso on 2006-06-25
If you have ddclient installed, check if it still works after the upgrade!

I had to reinstall the old kernel with synaptec and completely deinstall ddclient and the install it to make it work again. After a reboot ddclient did not start with the old kernel even though it was in /etc/init.d

Unfortunately now I cannot use truecrypt since I keep getting 

```
FATAL: Error inserting truecrypt (/lib/modules/2.6.15-25-server/extra/truecrypt.ko): Invalid module format
truecrypt: Failed to load TrueCrypt kernel module

```

I reocompiled the kernel 2 times, rebooted, recompiled truecrypt, used the binary. Nothing seems to work :(

---

### Post by kabronkline on 2006-06-26
HowTo has been updated with a new method.... if anybody could provide more mirrors for download of the file it would be greatly appreciated by many! Let me know if there are any problems.

---

### Post by RolatoR on 2006-06-26
*doh*

finished my installation minutes befor the first post was updated^^ but ...well my first compiled modules :] and it seems that truecrypt works fine. thx for the howto.

*notice for me: read the entire thread*

---

### Post by kabronkline on 2006-06-26
Sorry to hear I didn't get the update in time.... my bad. Thanks for the feedback - glad to hear it's working for you.

---

### Post by Teunis on 2006-06-26
Thanks all for the fine (and growing) tutorial!

I've got both the 386 and 686 kernel available and installing the deb in the 386 worked fine.
For the 686 kernel it was necessary to go by option #2 that worked as well.

I did get the compile errors rso reported but so far they don't seem to affect anything.

One question; the opened directory plus content are owned by root, even when the commands are done without sudo, this way you can't add or modify anything.
How to get them owned by the user opening the container?

---

### Post by kabronkline on 2006-06-27
Good question. I believe the answer lies within **Step 10** of **Method #2** - When you are prompted for the following if you answer with an "N" and this *should* provide the solution you are looking for.

> 3. Allow non-admin users to run TrueCrypt [y/N]:**N**

---

### Post by jvl on 2006-06-28
[QUOTE=Teunis]
One question; the opened directory plus content are owned by root, even when the commands are done without sudo, this way you can't add or modify anything.
How to get them owned by the user opening the container?[/QUOTE]

truecrypt /encrypted/device /mount/point -u

---

### Post by nanotube on 2006-06-28
Big amendment to your howto:
in method #2, step 8 (the compiling of all the kernel modules) is completely unnecessary. the truecrypt build.sh takes care of compiling only its own truecrypt module, using the kernel sources. there is no need to compile any other modules, you can just skip step 8 completely (as it happens, the most time consuming and error-prone step).

so, you might wish to modify your original howto (which is good in all other respects) with this in mind. :)

oh and another thing. very important to verify the gpg key after downloading the truecrypt source archive. to do that, download the gpg signature file as well, and then import the key with command:

```
gpg --keyserver subkeys.pgp.net --recv F0D6B1E0
```

and then verify the signature

```
gpg --verify truecrypt-4.2-source-code.tar.gz.sig truecrypt-4.2-source-code.tar.gz
```

that would also be a good thing to add to your howto. :)

---

### Post by kabronkline on 2006-06-29
Thank you very much for the feedback! I will definitely be making changes to the HowTo..... I appreciate your attention. O:)

---

### Post by nanotube on 2006-07-02
so, i have made a bash script to automate the installation of truecrypt from source. i am including the source in this message. please feel free to test it and report any errors or problems. also, feel free to give it a look and make coding suggestions. just copy the source to a plain text file, save as  installtruecrypt.sh, chmod to make it executable, and run it simply with command "./installtruecrypt.sh" . 

```

#!/bin/bash
#
# installtruecrypt.sh
#               Script to automatically download and install the newest truecrypt version for linux, on an Ubuntu system.
#               Requires an internet connection to work (obviously).
# 
# Author:       nanotube <nanotube@users.sf.net>.
#               
# Version:      installtruecrypt.sh  1.0  01-Jul-2006  nanotube@users.sf.net
# 
#
#######

check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully. Exiting."
    exit 1
  fi
}

## Get the newest truecrypt release version from truecrypt website
VERSION=`wget -q -O - http://www.truecrypt.org/downloads.php |grep "Latest Stable" -m 1 |sed -e 's/.*Version - //' -e 's@</h1.*@@'`

echo -e -n "The most recent release of truecrypt is detected to be $VERSION. Please make sure this is correct before proceeding. (You can confirm by going to http://www.truecrypt.org/) Is it correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "If this does not agree with the latest version as listed on truecrypt.org, please contact nanotube@users.sf.net and let me know."; exit ;;
  [Nn][Oo]) echo "If this does not agree with the latest version as listed on truecrypt.org, please contact nanotube@users.sf.net and let me know."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Proceed to download and install truecrypt and dependencies.

echo -e "\nUpdating repositories list\n"
sudo aptitude update
check_exit_status

echo -e "\nMaking sure that build tools are installed\n"
sudo aptitude -y install build-essential
check_exit_status

echo -e "\nGetting kernel sources (necessary to build truecrypt). Note that this will be a large download (~70M)\n"
sudo aptitude -y install linux-source-`uname -r |awk -F - '{print $1}'`
check_exit_status

echo -e "\nUnzipping and setting up linux source (this may take a minute).\n"
cd /usr/src/
if [ ! -d linux-source-`uname -r |awk -F - '{print $1}'` ]; then
  sudo tar -xjf linux-source-`uname -r |awk -F - '{print $1}'`.tar.bz2
  check_exit_status
else
  echo -e "\nLooks like the source has been unzipped already. Proceeding with installation.\n"
fi
if [ ! -e linux ]; then
  sudo ln -s linux-source-`uname -r |awk -F - '{print $1}'` linux
  check_exit_status
else
  echo -e "\nLooks like /usr/src/linux already exists. Will assume that kernel is already present there. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading truecrypt source archive.\n"
wget -c http://www.truecrypt.org/downloads/truecrypt-$VERSION-source-code.tar.gz
check_exit_status

echo -e "\nDownloading truecrypt gpg signature.\n"
wget -c http://www.truecrypt.org/downloads/truecrypt-$VERSION-source-code.tar.gz.sig

echo -e "\nImporting Truecrypt public key\n"
echo -e "Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.\n"
gpg --keyserver subkeys.pgp.net --recv F0D6B1E0
check_exit_status

echo -e "\nVerifying signature...\nNote: do not worry about \"untrusted key\" warnings. That is normal behavior for newly imported keys. Just make sure that key is verified.\n"
gpg --verify truecrypt-$VERSION-source-code.tar.gz.sig truecrypt-$VERSION-source-code.tar.gz
check_exit_status

echo -e "\nUnzipping the truecrypt archive .tar.gz file\n"
tar -xzvf truecrypt-$VERSION-source-code.tar.gz
check_exit_status

echo -e "\nRemoving the .tar.gz archive.\n"
rm -f firefox-$VERSION.tar.gz firefox-$VERSION.tar.gz.asc
check_exit_status

echo -e "\nSetting Ubuntu defaults for Truecrypt.\n"
cd truecrypt-$VERSION/Linux
cp install.sh install.sh.orig
cat ./install.sh.orig |sed -e 's@local/man@share/man@' > ./install.sh
check_exit_status

echo -e "\nCompiling Truecrypt module. Please follow along with the prompts (defaults are ok, unless you know what you are doing).\n"
sudo ./build.sh
check_exit_status

echo -e "\nInstalling Truecrypt. Please follow along with the prompts (defaults are ok, unless you know what you are doing).\n" 
sudo ./install.sh
check_exit_status

echo -e "\nTruecrypt $VERSION has been installed successfully. Run it with command \"truecrypt\". For help, run \"man truecrypt\", or see truecrypt.org for documentation."

exit

```

edit: generalized kernel install section...

---

### Post by nanotube on 2006-07-03
well, for what it's worth, (though nobody seems to have checked out my truecrypt install script), here is a new version of it, with neater error checking. please feel free to test it out and report your feedback.

```

#!/bin/bash
#
# installtruecrypt.sh
#               Script to automatically download and install the newest truecrypt version for linux, on an Ubuntu system.
#               Requires an internet connection to work (obviously).
# 
# Author:       nanotube <nanotube@users.sf.net>.
#               
# Version:      installtruecrypt.sh  1.1  03-Jul-2006  nanotube@users.sf.net
# 
#
#######

## Make sure that we exit if any commands do not complete successfully.
set -o errexit
trap 'echo "Previous command did not complete successfully. Exiting."' ERR

## Get the newest truecrypt release version from truecrypt website
VERSION=`wget -q -O - http://www.truecrypt.org/downloads.php |grep "Latest Stable" -m 1 |sed -e 's/.*Version - //' -e 's@</h1.*@@'`

echo -e -n "The most recent release of truecrypt is detected to be $VERSION. Please make sure this is correct before proceeding. (You can confirm by going to http://www.truecrypt.org/) Is it correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "If this does not agree with the latest version as listed on truecrypt.org, please contact nanotube@users.sf.net and let me know."; exit ;;
  [Nn][Oo]) echo "If this does not agree with the latest version as listed on truecrypt.org, please contact nanotube@users.sf.net and let me know."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Proceed to download and install truecrypt and dependencies.

echo -e "\nUpdating repositories list\n"
sudo aptitude update

echo -e "\nMaking sure that build tools are installed\n"
sudo aptitude -y install build-essential

echo -e "\nGetting kernel sources (necessary to build truecrypt). Note that this will be a large download (~70M)\n"
sudo aptitude -y install linux-source-`uname -r |awk -F - '{print $1}'`

echo -e "\nUnzipping and setting up linux source (this may take a minute).\n"
cd /usr/src/
if [ ! -d linux-source-`uname -r |awk -F - '{print $1}'` ]; then
  sudo tar -xjf linux-source-`uname -r |awk -F - '{print $1}'`.tar.bz2
else
  echo -e "\nLooks like the source has been unzipped already. Proceeding with installation.\n"
fi
if [ ! -e linux ]; then
  sudo ln -s linux-source-`uname -r |awk -F - '{print $1}'` linux
else
  echo -e "\nLooks like /usr/src/linux already exists. Will assume that kernel is already present there. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd

echo -e "\nDownloading truecrypt source archive.\n"
wget -c http://www.truecrypt.org/downloads/truecrypt-$VERSION-source-code.tar.gz

echo -e "\nDownloading truecrypt gpg signature.\n"
wget -c http://www.truecrypt.org/downloads/truecrypt-$VERSION-source-code.tar.gz.sig

echo -e "\nImporting Truecrypt public key\n"
echo -e "Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.\n"
gpg --keyserver subkeys.pgp.net --recv F0D6B1E0

echo -e "\nVerifying signature...\nNote: do not worry about \"untrusted key\" warnings. That is normal behavior for newly imported keys. Just make sure that key is verified.\n"
gpg --verify truecrypt-$VERSION-source-code.tar.gz.sig truecrypt-$VERSION-source-code.tar.gz

echo -e "\nUnzipping the truecrypt archive .tar.gz file\n"
tar -xzf truecrypt-$VERSION-source-code.tar.gz

echo -e "\nRemoving the .tar.gz archive.\n"
rm -f truecrypt-$VERSION-source-code.tar.gz.sig truecrypt-$VERSION-source-code.tar.gz

echo -e "\nSetting Ubuntu defaults for Truecrypt.\n"
cd truecrypt-$VERSION/Linux
cp install.sh install.sh.orig
cat ./install.sh.orig |sed -e 's@local/man@share/man@' > ./install.sh

echo -e "\nCompiling Truecrypt module. Please follow along with the prompts (defaults are ok, unless you know what you are doing).\n"
sudo ./build.sh

echo -e "\nInstalling Truecrypt. Please follow along with the prompts (defaults are ok, unless you know what you are doing).\n" 
sudo ./install.sh

echo -e "\nTruecrypt $VERSION has been installed successfully. Run it with command \"truecrypt\". For help, run \"man truecrypt\", or see truecrypt.org for documentation."

exit

```

---

### Post by marcip on 2006-07-03
From the TrueCrypt forum: 
-----
TrueCrypt 4.2a has been released.
[http://www.truecrypt.org/user-guide/?s=version-history](http://www.truecrypt.org/user-guide/?s=version-history)
[http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)
------
Ubuntu 6.06 is now among the binaries, 
marcip

---

### Post by nanotube on 2006-07-03
[QUOTE=marcip]From the TrueCrypt forum: 
-----
TrueCrypt 4.2a has been released.
[http://www.truecrypt.org/user-guide/?s=version-history](http://www.truecrypt.org/user-guide/?s=version-history)
[http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)
------
Ubuntu 6.06 is now among the binaries, 
marcip[/QUOTE]

ah excellent. :) i have added the ability to install from packaged ubuntu binaries to the script. here is the new script:

```

#!/bin/bash
#
# installtruecrypt.sh
#               Script to automatically download and install the newest truecrypt version for linux, on an Ubuntu system.
#               Requires an internet connection to work (obviously).
# 
# Author:       nanotube <nanotube@users.sf.net>.
#               
# Version:      installtruecrypt.sh  1.2  03-Jul-2006  nanotube@users.sf.net
# 
#
#######

## Make sure that we exit if any commands do not complete successfully.
set -o errexit
trap 'echo "Previous command did not complete successfully. Exiting."' ERR

## Get the newest truecrypt release version from truecrypt website
VERSION=`wget -q -O - http://www.truecrypt.org/downloads.php |grep "Latest Stable" -m 1 |sed -e 's/.*Version - //' -e 's@</h1.*@@'`

echo -e -n "The most recent release of truecrypt is detected to be $VERSION. Please make sure this is correct before proceeding. (You can confirm by going to http://www.truecrypt.org/) Is it correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "If this does not agree with the latest version as listed on truecrypt.org, please contact nanotube@users.sf.net and let me know."; exit ;;
  [Nn][Oo]) echo "If this does not agree with the latest version as listed on truecrypt.org, please contact nanotube@users.sf.net and let me know."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Get list of available packages

PACKAGES=( `wget -q -O - http://www.truecrypt.org/downloads.php |grep "option value" |grep -vi "select .* distribution" |sed -e 's/.*option value=\"//' -e 's/\">.*//' |grep -i "ubuntu\|source"` )

LIMIT=${#PACKAGES[*]}

## Get user choice of package

echo "Please choose the Truecrypt package you want to get. Enter the number of your choice from the list below."
for ((i=0; i < LIMIT ; i++))
do
  echo "$i: ${PACKAGES[$i]}"
done

CHOICE=$(($LIMIT + 1))

echo -n "Enter your choice of localization: "
while [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]
do
  read CHOICE
  if echo -n "$CHOICE" | grep -q "[^0-9]"; then
    echo -n "Your input contains non-numeric characters. Please try again: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ -z "$CHOICE" ]; then
    echo -n "Please enter the number of your choice from the list: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]; then
    echo -n "Your input is not in the range of available localizations. Please try again: "
  fi
done

echo -n "You have chosen localization \"${PACKAGES[$CHOICE]}\". Is that correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "In that case, start over by running this script again."; exit ;;
  [Nn][Oo]) echo "In that case, start over by running this script again."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Proceed to download and install truecrypt and dependencies.

if [ "${PACKAGES[$CHOICE]}" == "source-code.tar.gz" ]; then
  echo -e "\nUsing the source package will require some extra dependencies.\n"
  echo -e "\nUpdating repositories list\n"
  sudo aptitude update

  echo -e "\nMaking sure that build tools are installed\n"
  sudo aptitude -y install build-essential

  echo -e "\nGetting kernel sources (necessary to build truecrypt). Note that this will be a large download (~70M)\n"
  sudo aptitude -y install linux-source-`uname -r |awk -F - '{print $1}'`

  echo -e "\nUnzipping and setting up linux source (this may take a minute).\n"
  cd /usr/src/
  if [ ! -d linux-source-`uname -r |awk -F - '{print $1}'` ]; then
    sudo tar -xjf linux-source-`uname -r |awk -F - '{print $1}'`.tar.bz2
  else
    echo -e "\nLooks like the source has been unzipped already. Proceeding with installation.\n"
  fi
  if [ ! -e linux ]; then
    sudo ln -s linux-source-`uname -r |awk -F - '{print $1}'` linux
  else
    echo -e "\nLooks like /usr/src/linux already exists. Will assume that kernel is already present there. Proceeding with installation.\n"
  fi
fi

echo -e "\nChanging to home directory\n"
cd

echo -e "\nDownloading truecrypt source archive.\n"
wget -c http://www.truecrypt.org/downloads/truecrypt-$VERSION-${PACKAGES[$CHOICE]}

echo -e "\nDownloading truecrypt gpg signature.\n"
wget -c http://www.truecrypt.org/downloads/truecrypt-$VERSION-${PACKAGES[$CHOICE]}.sig

echo -e "\nImporting Truecrypt public key\n"
echo -e "Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.\n"
gpg --keyserver subkeys.pgp.net --recv F0D6B1E0

echo -e "\nVerifying signature...\nNote: do not worry about \"untrusted key\" warnings. That is normal behavior for newly imported keys. Just make sure that key is verified.\n"
gpg --verify truecrypt-$VERSION-${PACKAGES[$CHOICE]}.sig truecrypt-$VERSION-${PACKAGES[$CHOICE]}

echo -e "\nUnzipping the truecrypt archive .tar.gz file\n"
tar -xzf truecrypt-$VERSION-${PACKAGES[$CHOICE]}

echo -e "\nRemoving the .tar.gz archive.\n"
rm -f truecrypt-$VERSION-${PACKAGES[$CHOICE]}.sig truecrypt-$VERSION-${PACKAGES[$CHOICE]}

cd truecrypt-$VERSION

if [ "${PACKAGES[$CHOICE]}" == "source-code.tar.gz" ]; then
  cd Linux
  
  echo -e "\nCompiling Truecrypt module. Please follow along with the prompts (defaults are ok, unless you know what you are doing).\n"
  sudo ./build.sh

  echo -e "\nInstalling Truecrypt. Please follow along with the prompts (defaults are ok, unless you know what you are doing).\n" 
  sudo ./install.sh
else
  sudo dpkg -i truecrypt*.deb
fi

echo -e "\nRemoving install files.\n"
cd
sudo rm -rf ./truecrypt-$VERSION

echo -e "\nTruecrypt $VERSION has been installed successfully. Run it with command \"truecrypt\". For help, run \"man truecrypt\", or see truecrypt.org for documentation."

exit

```

---

### Post by mackinax on 2006-07-03
Thanks to kabronkline for the original post

And thanks to nanotube; your script helped me to install TrueCrypt 4.2a successfully

---

### Post by pjman on 2006-07-08
nonotube - Is your script suppose to work with the AMD kernel (2.6.15-25-k7)? Everything installed fine but when I try to mount a TC file I get the following error

```
truecrypt: Incorrect version of kernel module loaded - version 4.2 required
```

Thanks!

---

### Post by nanotube on 2006-07-09
> **pjman said:**
> nonotube - Is your script suppose to work with the AMD kernel (2.6.15-25-k7)? Everything installed fine but when I try to mount a TC file I get the following error

```
truecrypt: Incorrect version of kernel module loaded - version 4.2 required
```

Thanks!

well, it is supposed to work with anything. did you install using the ubuntu deb packages, or did you select to install from source?

if you are running an 64bit kernel, you have to select the 64bit ubuntu deb (if you want to use the binary).

---

### Post by gonegolf on 2006-07-09
Hi, I am a switcher from Windows XP and so totally new on Ubuntu.  Please bear with my ignorance.

I enjoy using Truecrypt and hence would like to be able to use this on Ubuntu.  But, I have no idea how to do the chmod command even after trying to use the help menu.  I have copied the script to a file.

It would be great if you can specify the whole series of command to make this works.  Am I right to assume that there will be a graphical interface after successful installation?  I am really struggling with the command line.

Thanks

---

### Post by krazykirk on 2006-07-09
Hmm... I installed TrueCrypt myself from the website, and followed the instructions and it worked fine for me!
Also it took me a while to figure out that there was no GUI for the program! (I've used the windows version)

---

### Post by nanotube on 2006-07-09
> **gonegolf said:**
> Hi, I am a switcher from Windows XP and so totally new on Ubuntu.  Please bear with my ignorance.

I enjoy using Truecrypt and hence would like to be able to use this on Ubuntu.  But, I have no idea how to do the chmod command even after trying to use the help menu.  I have copied the script to a file.

It would be great if you can specify the whole series of command to make this works.  Am I right to assume that there will be a graphical interface after successful installation?  I am really struggling with the command line.

Thanks
hi
well, first i will have to disappoint you - truecrypt for linux is a commandline program, no gui.
so you would definitely want to go through a tutorial on commandline. there are some good ones listed in the third link in my sig (the faq), under "learn about commandline".

but as to the chmod specifically, you can bypass the commandline, and just right click the file, select properties, then select permissions tab, and check some checkboxes to enable execute permissions. :)

---

### Post by kromcuich on 2006-07-10
> **nanotube said:**
> ah excellent. :) i have added the ability to install from packaged ubuntu binaries to the script. here is the new script:

```

#!/bin/bash
#
# installtruecrypt.sh
#               Script to automatically download and install the newest truecrypt version for linux, on an Ubuntu system.
#               Requires an internet connection to work (obviously).
# 
# Author:       nanotube <nanotube@users.sf.net>.
#               
# Version:      installtruecrypt.sh  1.2  03-Jul-2006  nanotube@users.sf.net
# 
#
#######

## Make sure that we exit if any commands do not complete successfully.
set -o errexit
trap 'echo "Previous command did not complete successfully. Exiting."' ERR

## Get the newest truecrypt release version from truecrypt website
VERSION=`wget -q -O - http://www.truecrypt.org/downloads.php |grep "Latest Stable" -m 1 |sed -e 's/.*Version - //' -e 's@</h1.*@@'`

echo -e -n "The most recent release of truecrypt is detected to be $VERSION. Please make sure this is correct before proceeding. (You can confirm by going to http://www.truecrypt.org/) Is it correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "If this does not agree with the latest version as listed on truecrypt.org, please contact nanotube@users.sf.net and let me know."; exit ;;
  [Nn][Oo]) echo "If this does not agree with the latest version as listed on truecrypt.org, please contact nanotube@users.sf.net and let me know."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Get list of available packages

PACKAGES=( `wget -q -O - http://www.truecrypt.org/downloads.php |grep "option value" |grep -vi "select .* distribution" |sed -e 's/.*option value=\"//' -e 's/\">.*//' |grep -i "ubuntu\|source"` )

LIMIT=${#PACKAGES[*]}

## Get user choice of package

echo "Please choose the Truecrypt package you want to get. Enter the number of your choice from the list below."
for ((i=0; i < LIMIT ; i++))
do
  echo "$i: ${PACKAGES[$i]}"
done

CHOICE=$(($LIMIT + 1))

echo -n "Enter your choice of localization: "
while [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]
do
  read CHOICE
  if echo -n "$CHOICE" | grep -q "[^0-9]"; then
    echo -n "Your input contains non-numeric characters. Please try again: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ -z "$CHOICE" ]; then
    echo -n "Please enter the number of your choice from the list: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]; then
    echo -n "Your input is not in the range of available localizations. Please try again: "
  fi
done

echo -n "You have chosen localization \"${PACKAGES[$CHOICE]}\". Is that correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "In that case, start over by running this script again."; exit ;;
  [Nn][Oo]) echo "In that case, start over by running this script again."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Proceed to download and install truecrypt and dependencies.

if [ "${PACKAGES[$CHOICE]}" == "source-code.tar.gz" ]; then
  echo -e "\nUsing the source package will require some extra dependencies.\n"
  echo -e "\nUpdating repositories list\n"
  sudo aptitude update

  echo -e "\nMaking sure that build tools are installed\n"
  sudo aptitude -y install build-essential

  echo -e "\nGetting kernel sources (necessary to build truecrypt). Note that this will be a large download (~70M)\n"
  sudo aptitude -y install linux-source-`uname -r |awk -F - '{print $1}'`

  echo -e "\nUnzipping and setting up linux source (this may take a minute).\n"
  cd /usr/src/
  if [ ! -d linux-source-`uname -r |awk -F - '{print $1}'` ]; then
    sudo tar -xjf linux-source-`uname -r |awk -F - '{print $1}'`.tar.bz2
  else
    echo -e "\nLooks like the source has been unzipped already. Proceeding with installation.\n"
  fi
  if [ ! -e linux ]; then
    sudo ln -s linux-source-`uname -r |awk -F - '{print $1}'` linux
  else
    echo -e "\nLooks like /usr/src/linux already exists. Will assume that kernel is already present there. Proceeding with installation.\n"
  fi
fi

echo -e "\nChanging to home directory\n"
cd

echo -e "\nDownloading truecrypt source archive.\n"
wget -c http://www.truecrypt.org/downloads/truecrypt-$VERSION-${PACKAGES[$CHOICE]}

echo -e "\nDownloading truecrypt gpg signature.\n"
wget -c http://www.truecrypt.org/downloads/truecrypt-$VERSION-${PACKAGES[$CHOICE]}.sig

echo -e "\nImporting Truecrypt public key\n"
echo -e "Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.\n"
gpg --keyserver subkeys.pgp.net --recv F0D6B1E0

echo -e "\nVerifying signature...\nNote: do not worry about \"untrusted key\" warnings. That is normal behavior for newly imported keys. Just make sure that key is verified.\n"
gpg --verify truecrypt-$VERSION-${PACKAGES[$CHOICE]}.sig truecrypt-$VERSION-${PACKAGES[$CHOICE]}

echo -e "\nUnzipping the truecrypt archive .tar.gz file\n"
tar -xzf truecrypt-$VERSION-${PACKAGES[$CHOICE]}

echo -e "\nRemoving the .tar.gz archive.\n"
rm -f truecrypt-$VERSION-${PACKAGES[$CHOICE]}.sig truecrypt-$VERSION-${PACKAGES[$CHOICE]}

cd truecrypt-$VERSION

if [ "${PACKAGES[$CHOICE]}" == "source-code.tar.gz" ]; then
  cd Linux
  
  echo -e "\nCompiling Truecrypt module. Please follow along with the prompts (defaults are ok, unless you know what you are doing).\n"
  sudo ./build.sh

  echo -e "\nInstalling Truecrypt. Please follow along with the prompts (defaults are ok, unless you know what you are doing).\n" 
  sudo ./install.sh
else
  sudo dpkg -i truecrypt*.deb
fi

echo -e "\nRemoving install files.\n"
cd
sudo rm -rf ./truecrypt-$VERSION

echo -e "\nTruecrypt $VERSION has been installed successfully. Run it with command \"truecrypt\". For help, run \"man truecrypt\", or see truecrypt.org for documentation."

exit

```
hey nanotube, thanks for the install script, however it failed on my 2.6.15-25-686 thinkpad. Error message:

make[4]: *** [drivers/usb/net/zd1211/zddevlist.h] Error 1
make[3]: *** [drivers/usb/net/zd1211] Error 2
make[2]: *** [drivers/usb/net] Error 2
make[1]: *** [drivers/usb] Error 2
make: *** [drivers] Error 2
Previous command did not complete successfully. Exiting.

I had tis before with other attempted installs of truecrypt, however it happened after I updated to 686. Any ideas?

---

### Post by nanotube on 2006-07-10
> **kromcuich said:**
> hey nanotube, thanks for the install script, however it failed on my 2.6.15-25-686 thinkpad. Error message:

make[4]: *** [drivers/usb/net/zd1211/zddevlist.h] Error 1
make[3]: *** [drivers/usb/net/zd1211] Error 2
make[2]: *** [drivers/usb/net] Error 2
make[1]: *** [drivers/usb] Error 2
make: *** [drivers] Error 2
Previous command did not complete successfully. Exiting.

I had tis before with other attempted installs of truecrypt, however it happened after I updated to 686. Any ideas?

so, i take it you decided to install from source. :) i have no idea why the build could be failing, you might have better luck to ask somewhere in the programming forum, they could help you track this down. or you could install using the binary...

---

### Post by cornelis1 on 2006-07-10
I had the same problem. After some searching around I found out it has something to do with the fact that on Ubuntu &#8220;mawk&#8221; is installed rather than &#8220;gawk&#8221;. So I installed &#8220;gawk&#8221; (through Synaptic) and everything went fine (although the whole process of compiling took almost an hour).
BTW: I had remove the &#8220;linux-source-2.6.15&#8221;-folder from /usr/src first and put in a &#8220;fresh&#8221;one.

---

### Post by krazykirk on 2006-07-10
Wouldn't it be easier to download the .deb file from the website and install if off that?

---

### Post by cornelis1 on 2006-07-11
> **krazykirk said:**
> Wouldn't it be easier to download the .deb file from the website and install if off that?

I tried that, but it doesn't work with a 686-kernel. (At least it doesn't for me)

---

### Post by kromcuich on 2006-07-11
> **nanotube said:**
> so, i take it you decided to install from source. :) i have no idea why the build could be failing, you might have better luck to ask somewhere in the programming forum, they could help you track this down. or you could install using the binary...
Heya,

thanks for advice in the pages, i managed to compily truecrypt succesfully - using your script. However, and I hate to say it! now i have the following error, upon attempting to mount a truecrypt volume

dmitri@ezhik:~$ truecrypt -u ~/borch ~/Desktop/Data/
Enter password for '/home/dmitri/borch':
FATAL: Error inserting truecrypt (/lib/modules/2.6.15-25-686/extra/truecrypt.ko): Invalid module format
truecrypt: Failed to load TrueCrypt kernel module


Now I must stress, that I have updated my linux source and headers and recompiled everything. Just incase here's an ls of /usr/src

kernel-headers-2.6.15.7-ubuntu1-dmitri_10.00.Custom_i386.deb
kernel-image-2.6.15.7-ubuntu1-dmitri_10.00.Custom_i386.deb
linux
linux-headers-2.6.15-25
linux-headers-2.6.15-25-686
linux-source-2.6.15
linux-source-2.6.15.tar.bz2
sl-modem.tar.bz2

I get this in dmseg, but i dont know what to do about it

[17183918.844000] truecrypt: version magic '2.6.15.7-ubuntu1-dmitri SMP preempt 586 gcc-4.0' should be '2.6.15-25-686 SMP preempt 686 gcc-4.0'


Please advise fellow truecrypteres

thanks

---

### Post by alaaji on 2006-07-11
Hello there again.  I am still a newbie at all this and I've tried everything that I know possible.  I've reinstalled & recompiled the kernel.  I've removed it and reinstalled it.  I've looked all through these forums, the truecrypt forums and google but I can't get an answer.  Could someone please help me?  

I am getting this error when I try to open my truecrypt volume:

FATAL: Error inserting truecrypt (/lib/modules/2.6.15-25-686/extra/truecrypt.ko): Invalid module format
truecrypt: Failed to load TrueCrypt kernel module

Does anyone know what else I could try?

---

### Post by alaaji on 2006-07-11
> **kromcuich said:**
> hey nanotube, thanks for the install script, however it failed on my 2.6.15-25-686 thinkpad. Error message:

make[4]: *** [drivers/usb/net/zd1211/zddevlist.h] Error 1
make[3]: *** [drivers/usb/net/zd1211] Error 2
make[2]: *** [drivers/usb/net] Error 2
make[1]: *** [drivers/usb] Error 2
make: *** [drivers] Error 2
Previous command did not complete successfully. Exiting.

I had this before with other attempted installs of truecrypt, however it happened after I updated to 686. Any ideas?

I got that message too when I compiled from source.  I guess that I can't win. ](*,)

---

### Post by cornelis1 on 2006-07-11
Have you tried installing "gawk"? See my earlier post #53.

---

### Post by orb9220 on 2006-07-12
There now is a file to down at truecrypt called:

truecrypt-4.2a-ubuntu-6.06-x86.tar.gz which has the .deb inside

[http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

---

### Post by jbus on 2006-07-12
It would be great to get a GUI for TC that would cover the most basic options. Does anyone know if anyone is working on this?

---

### Post by traveller on 2006-07-12
> **krazykirk said:**
> Wouldn't it be easier to download the .deb file from the website and install if off that?
I downloaded and installed (succesfully? I hope) TrueCrypt for Ubuntu  before finding this thread. There's is not a gui as in its Windows version and I cannot find TC among my applications but when I type truecrypt in terminal here's what I read:
--filesystem TYPE               Filesystem type
     --hash HASH                     Hash algorithm
 -k, --keyfile FILE|DIR              Keyfile for volume
     --keyfile-add FILE|DIR          New keyfile for volume
 -K, --keyfile-protected FILE|DIR    Keyfile for protected volume
 -M, --mount-options OPTIONS         Mount options
 -N, --device-number NUMBER          Map volume as device number
     --overwrite                     Overwrite files without confirmation
 -p, --password PASSWORD             Password for volume
     --password-tries NUMBER         Password entry tries
 -P, --protect-hidden                Protect hidden volume
     --random-source FILE            Random number generator input file
     --quick                         Use quick format
     --update-time                   Do not preserve timestamps
 -r, --read-only                     Map/Mount volume as read-only
     --size SIZE                     Volume size
     --type TYPE                     Volume type
 -u, --user-mount                    Set default user and group ID on mount
 -v, --verbose                       Verbose output

 MAPPED_VOLUME = DEVICE_NUMBER | DEVICE_NAME | MOUNT_POINT | VOLUME_PATH
For a detailed help, use --help or see truecrypt(1) man page.
For more information, visit <http://www.truecrypt.org/docs/>.

By typing truecrypt --help here's what I have:

truecrypt -k keyfile -C volume.tc
 Change password and remove a keyfile from volume.

truecrypt -k keyfile --keyfile-add keyfile -C volume.tc
 Change password and keep previous keyfile.

Creating a hidden volume without risking data corruption:
 1) Create an outer volume:
    truecrypt --type normal --size 100M -c volume.tc
 2) Create a hidden volume:
    truecrypt --type hidden --size 50M -c volume.tc
 3) Mount the outer volume with the hidden volume protected:
    truecrypt -P volume.tc /mnt/tc
 4) Copy files to the outer volume:
    cp outer_volume_file.txt /mnt/tc
 5) Dismount the outer volume:
    truecrypt -d volume.tc
 6) If a warning message has been displayed in 5), start again from 1). Either
 a larger outer volume should be created in 1), or smaller files should be
 copied to the outer volume in 4).



What do you think? Is it Ok so far?

---

### Post by djembe330 on 2006-07-13
Hello all, my first post on Ubuntu forums!

I had some problems with 4.2a trying to rebuild the entire kernel from scratch...not cool.  So I downloaded the kernel source, copied the correct config file to it (not sure if this is necessary or not?) and then went to the truecrypt directory.  From there I issued a make command from ~/truecrypt-4.2a/Linux/Kernel/ and ~/truecrypt-4.2a/Linux/Cli/  

After this I ran the install script.  It works!

Reasoning for this:

-I use core duo so the available 386 binaries did not work.
-build.sh either wanted to compile the entire kernel or if I checked No, then it wouldn't work with some errors (I forget what errors exactly)
-I tried compiling the entire kernel and got some errors.  (after this I nuked the kernel source since it was half-compiled and re-installed it)

Let me know if this works for anyone else!

---

### Post by flyingbrass on 2006-07-14
As of this morning I'm running 2.6.15-26-686.

Why does the installer need to compile the kernel (or even all the modules) just to build a single module?  I don't understand this stuff.  After waiting forever for build.sh to finish, numerous warnings and a few errors scared me away from actually installing it.

I tried djembe330's method. Installation seemed to go ok, but when I try to map/mount a volume it says:

truecrypt: Incorrect version of kernel module loaded - version 4.2 required

The truecrypt deb for Dapper doesn't work. The module won't load.

---

### Post by TestUser on 2006-07-15
Hi flyingbrass

Just so you know I have the same problem and I use an old container and just recopiled after kernel upgrade and I get same problem as you. So ther is something in installation and I do not know what...

I first did as I did before with success but now it fails, tried different solutions and solved the errors one by one but the module error is not solved.

TU

---

### Post by pjman on 2006-07-15
> **nanotube said:**
> well, it is supposed to work with anything. did you install using the ubuntu deb packages, or did you select to install from source?

if you are running an 64bit kernel, you have to select the 64bit ubuntu deb (if you want to use the binary).

I installed from source. Any ideas?

Thanks,
Travis

**EDIT**
This is being logged in my /var/log/messages.

```
Jul 15 03:40:54 ubuntu1 kernel: [17454381.516000] truecrypt: no version for "struct_module" found: kernel tainted.
Jul 15 03:40:54 ubuntu1 kernel: [17454381.516000] truecrypt: disagrees about version of symbol dm_put_device
Jul 15 03:40:54 ubuntu1 kernel: [17454381.520000] truecrypt: Unknown symbol dm_put_device
Jul 15 03:40:54 ubuntu1 kernel: [17454381.520000] truecrypt: disagrees about version of symbol dm_unregister_target
Jul 15 03:40:54 ubuntu1 kernel: [17454381.520000] truecrypt: Unknown symbol dm_unregister_target
Jul 15 03:40:54 ubuntu1 kernel: [17454381.520000] truecrypt: disagrees about version of symbol dm_register_target
Jul 15 03:40:54 ubuntu1 kernel: [17454381.520000] truecrypt: Unknown symbol dm_register_target
Jul 15 03:40:54 ubuntu1 kernel: [17454381.520000] truecrypt: disagrees about version of symbol dm_table_get_mode
Jul 15 03:40:54 ubuntu1 kernel: [17454381.520000] truecrypt: Unknown symbol dm_table_get_mode
Jul 15 03:40:54 ubuntu1 kernel: [17454381.520000] truecrypt: disagrees about version of symbol dm_get_device
Jul 15 03:40:54 ubuntu1 kernel: [17454381.520000] truecrypt: Unknown symbol dm_get_device
```

---

### Post by Mulli on 2006-07-15
I've got the same problems and this was the solution for me:

1.) "locate truecrypt" I deleted everything that was listed
2.) Download the Ubuntu 6.06 file from here: [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php) ,unpack the file and install it (double click on the .deb package) 
3.) change the rights so that "normal" users can mount devices "sudo chmod u+s /usr/bin/truecrypt" (

Thats it. Hope it works for you too.

---

### Post by TestUser on 2006-07-15
Hi

Thank you for your input, now I managed to install and mount a container.
I edited bash.sh, removed linux-source from /usr/src and extracted a new one. Then removed all truecrypt on HDD. I also rebuild all modules but I am not sure it is nedded.

If you have problem I can write exactly how I did, but it is more or less a compilation of all tips in topics in this forum.

TU

---

### Post by flyingbrass on 2006-07-15
Thanks Mulli.  That did the trick.

---

### Post by alejandrops on 2006-07-15
hi, I installed truecrypt with the deb prob truecrypt page anda with the scrip published in this thread.
I can create a container but cant mount
the error is:

```

insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.15.ko': -1 Invalid module format
FATAL: Module truecrypt not found.
truecrypt: Failed to load TrueCrypt kernel module

```

I have a core duo and my kernel is 2.6.15-26-686

thanks!

---

### Post by TestUser on 2006-07-15
Hi

Have you removed everything related to truecrypt before installing?
Thanks to mulli I managed to install, I more and less followed this and similar How To [http://forums.truecrypt.org/viewtopic.php?t=2368](http://forums.truecrypt.org/viewtopic.php?t=2368)
and then edited bash and removing all old TC.

This will rebuild your modules so do not forget it:
sudo make -C /usr/src/linux-source-2.6.15 config modules 

Good luck and post again if it is not working.

TU

---

### Post by cprise on 2006-07-15
I am ambivalent about using TrueCrypt. It does not encrypt the home folder, which IMO is where privacy is most needed by a long margin. This is by default where you will find browsing-related data, emails and most anything else the user does. I do not want my privacy protected only for those bits of data that I consciously, determinedly move into a special partition.

The encryption Howtos seem like a better place to start toward securing data. Whereas Truecrypt plays more of a role of supplementing basic system privacy for those times when sharing encrypted partitions between operating systems becomes necessary (i.e. not often for most people).

I heard there is a GUI wizard under development for managing encrypted home folders on Ubuntu. Anyone seen it?

---

### Post by alejandrops on 2006-07-15
I already removed everything, downloaded the deb from truecrypt page and installed again and same problem
shoul I run 

sudo make -C /usr/src/linux-source-2.6.15 config modules 

I am afraid I can make a mistake.


> **TestUser said:**
> Hi

Have you removed everything related to truecrypt before installing?
Thanks to mulli I managed to install, I more and less followed this and similar How To [http://forums.truecrypt.org/viewtopic.php?t=2368](http://forums.truecrypt.org/viewtopic.php?t=2368)
and then edited bash and removing all old TC.

This will rebuild your modules so do not forget it:
sudo make -C /usr/src/linux-source-2.6.15 config modules 

Good luck and post again if it is not working.

TU

---

### Post by TestUser on 2006-07-16
Hi

I had no problems doing that, try with source first.

Cl

---

### Post by konradbeckmann on 2006-07-19
> **alejandrops said:**
> hi, I installed truecrypt with the deb prob truecrypt page anda with the scrip published in this thread.
I can create a container but cant mount
the error is:

```

insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.15.ko': -1 Invalid module format
FATAL: Module truecrypt not found.
truecrypt: Failed to load TrueCrypt kernel module

```

I have a core duo and my kernel is 2.6.15-26-686

thanks!
Hi,
A minute ago, I got the same problem as you.
My computer runs on an AMD64-processor, but that doesn't seem to be the issue here.
I use the kernel **2.6.15-26**-amd64-generic. Running that kernel makes the module unuseable. So I booted with my *original* 2.6.15-**23**-amd64-generic. With that, the problem was solved. I can mount the TC-volumes.

So the solution is either to *run an older kernel*, or to compile the module with the *latest kernel*. Simple, huh? ;)

---

### Post by kabronkline on 2006-07-20
> **cprise said:**
> I am ambivalent about using TrueCrypt. It does not encrypt the home folder, which IMO is where privacy is most needed by a long margin. This is by default where you will find browsing-related data, emails and most anything else the user does. I do not want my privacy protected only for those bits of data that I consciously, determinedly move into a special partition.

The encryption Howtos seem like a better place to start toward securing data. Whereas Truecrypt plays more of a role of supplementing basic system privacy for those times when sharing encrypted partitions between operating systems becomes necessary (i.e. not often for most people).

I heard there is a GUI wizard under development for managing encrypted home folders on Ubuntu. Anyone seen it?

Although what you are speaking of is possible, I don't plan on using Truecrypt for that purpose. My biggest use for Truecrypt is encrypting files on my USB drive.

---

### Post by WishMaster on 2006-07-22
I have an Icy-Box (external HD), with 3 partitions on it:
- ntfs
- fat
- hidden truecrypt volume

How the h*ll can I mount the hidden encrypted volume ??
/media only shows the ntfs and fat partition

If I try " /media/<name of hidden volume> " it doesn't work

[COLOR=Gray]edit: truecrypt 4.2a installed from source code on Ubuntu 6.06 with 2.6.17 kernel. Installed fine.[/COLOR]

---

### Post by TestUser on 2006-07-22
Hi

This is how I mount an external USB HDD with truecrypt:
truecrypt /dev/sdbX /media/XYZ --mount-options 'iocharset=utf8,umask=000,uid=1000,gid=100'

since you have one volume in a fat32 partition (?)you have to edit sdbX and XYZ to suite your needs.
sdb should be ok just check what the partition is called then you need the mounting point XYZ.

If you already have the disk mounted just point to the TC volume, all depends how you did.
You also need to verify you have TC working with your kernel.

TU

---

### Post by WishMaster on 2006-07-22
okay, that worked :D
thanks !!

> sudo truecrypt /dev/sdb6 /mnt/encr/this mounts my encrypted partition correctly.

Now another question: is it possible to create a starter for mounting the encr. partition?
My Icy Box isn't plugged in all the time (only when I do backup).
I would like to have an icon on my desktop, when I doubleclick it, it must ask for my encr. password. If pass checks out OK, I want the partition to be opened in Nautilus.

---

### Post by TestUser on 2006-07-22
Hi

Right click on the list and choose "add to panel" then custom apllication Launcher" There you choose terminal and application and at command you paste the link you have.
I do not know about nautilus, perhaps it is mentioned in readme file, as I have it there are a new folder on desktop.

TU

---

### Post by pumpkin_escobar on 2006-07-24
i've got a dell d620 running dapper and was having the same problem kromcuich was

was getting this error when compiling: 

In file included from drivers/usb/net/zd1211/zdusb.c:41:
drivers/usb/net/zd1211/zddevlist.h:7:2: error: #error "Error in source file, line 35"
make[4]: *** [drivers/usb/net/zd1211/zdusb.o] Error 1
make[3]: *** [drivers/usb/net/zd1211] Error 2
make[2]: *** [drivers/usb/net] Error 2
make[1]: *** [drivers/usb] Error 2
make: *** [drivers] Error 2


i got rid of the error by commenting out line 7 of the zddevlist.h file

it then let me compile without further errors and truecrypt seems to work fine

can create, mount, unmount volumes with no troubles

it may have problems with usb mounted drives but am not going to be using them so that wasn't an issue for me

hope it helps someone else

---

### Post by Bonez56 on 2006-07-26
Has anyone managed to get TC working with the k7 AMD kernel?

I am running [B]Linux bonezpc 2.6.15-26-k7 #1 SMP PREEMPT Mon Jul 17 20:36:04 UTC 2006 i686 GNU/Linux
[/B] and I have compiled TC and built the module, but this is the error I get when trying to mount a volume:

```

blake@bonezpc:~/Desktop$ sudo truecrypt /d/volume /mnt
Enter password for '/d/volume':
truecrypt: Incorrect version of kernel module loaded - version 4.2 required

```

I saw some earlier posts in this thread about the issue but nobody seems to have posted if they had been able to correct the issue or not.

Thanks

---

### Post by popie on 2006-07-28
I'm using the 686 kernal and Method 1 didn't work for me. Still got kernal module errors when running TrueCrypt. So I removed Truecrypt and proceeded with Method 2.

Upon performing step 8 of Method 2, I got pages and pages of warnings and errors. My terminal buffer is 1000 lines and it was exceeded... Is that normal?

PS> The how-to needs to be updated for TC version 4.2a. It would make cutting and pasting the commands easier. :) Thanks.

---

### Post by argusBR on 2006-07-28
Bonez56, try the following:

When install.sh prompts for 

```

Install binaries to [/usr/bin]:

```

don't accept the default value and install to /usr/local/bin

It worked for me.

---

### Post by simone.brunozzi on 2006-08-11
It seems that I successfully installed Truecrypt 4.2a on my laptop.
However, after creating a normal (not hidden) truecrypt volume, I have the following error:

```

simone@ubuntu:~$ ls -l
total 20508
drwxr-xr-x 2 simone simone     4096 2006-08-11 16:50 Desktop
lrwxrwxrwx 1 simone simone       26 2006-06-30 15:04 Examples -> /usr/share/example-content
-rw-r--r-- 1 simone simone 20971520 2006-08-11 17:03 zimone.tc
simone@ubuntu:~$ truecrypt zimone.tc
Enter password for '/home/simone/zimone.tc':
insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.15.ko': -1 Invalid module formatFATAL: Module truecrypt not found.
truecrypt: Failed to load TrueCrypt kernel module
simone@ubuntu:~$


```

How can I solve it?

Thanks

---

### Post by kotti on 2006-08-17
Could someone please upload the "Truecrypt binary compiled for Ubuntu Dapper with kernal version 2.6.15" somewhere as savefile.com seems to be down?

Thanks.

---

### Post by 454redhawk on 2006-08-19
Truecrypt.org now has the .deb available for ubuntu 6.06

---

### Post by trmentry on 2006-08-21
I installed Truecrypt with the DEB file that is on the TC site now.  It installed without issue.

When I do a:

truecrypt file.tc /mnt  

It told me I needed to be root.   So I tried it with sudo and get this.

```

truecrypt: No free loopback device available for file-hosted volume

```

I did a 'sudo modprobe loop' and tried again with the same results.  A 
'sudo losetup -f' shows that I have /dev/loop0 available.  But still no dice.

However I can mount an ISO without issue by doing the following:

sudo mount -o loop -t iso9660 blah.iso /mnt


Can someone please point me in the right direction?  Thanks

---

### Post by trmentry on 2006-08-21
can anyone point me in the right direction with this?

TIA

---

### Post by 454redhawk on 2006-08-22
> **trmentry said:**
> can anyone point me in the right direction with this?

TIA

TrueCrypt requires administrator (root) privileges. If you intend to
use TrueCrypt from a user account, you should execute the following command
as root in a terminal. This will only have to be done once.

```
chmod u+s /usr/bin/truecrypt
```

you also might want to create a mount point other than /mnt.

Maybe something like /mnt/whatever or media/whatever or /home/whatever not just dumping it in the /mnt dir.  Just a suggestion.

---

### Post by 454redhawk on 2006-08-22
I am using Mepis 6.0 and have installed Truecrypt 4.2 using the .deb in the download section.

This is how I installed and use Truecrypt.

1. I am using truecrypt from a user account and applied this command from a root terminal. I think its sudo for you ubuntu guys.
```
chmod u+s /usr/bin/truecrypt
```

2. Created a volume using this command and answered the required questions.
```
truecrypt -c /home/454redhawk/filename
```

3.Created a mount point for the encrypted volume at /home/454redhawk/mount-point

4. Created a simple script to assist in the mounting of the volume to my mount point.
```
#!/bin/sh
truecrypt -u /home/454redhawk/my-truecrypt-file /home/454redhawk/mount-point
```
**[SIZE="4"]Dont forget the -u option if you created a FAT volume.[/SIZE]**

5. Created another simple script to unmount all volumes
```
#!/bin/sh
truecrypt -d
```

6. Created a link to URL on the desktop that points to the mount script and runs in a terminal. It runs, asks for the password and exits the terminal.

7.Created another link to URL on the desktop that runs the unmount script.

8. Created a link on the desktop that opens a file manager window to the mounted location.

---

### Post by trmentry on 2006-08-22
> **454redhawk said:**
> TrueCrypt requires administrator (root) privileges. If you intend to
use TrueCrypt from a user account, you should execute the following command
as root in a terminal. This will only have to be done once.

```
chmod u+s /usr/bin/truecrypt
```

you also might want to create a mount point other than /mnt.

Maybe something like /mnt/whatever or media/whatever or /home/whatever not just dumping it in the /mnt dir.  Just a suggestion.


No go.  I added the sticky bit to truecrypt and still get the no loopback device availble error.

 truecrypt: No free loopback device available for file-hosted volume

This is trying to mount as a user, sudo or as sudo su.   


I am mounting to a dir under /mnt.  I guess I got ahead of myself when typing the post and forgot to put it there.   Its actually /mnt/truecrypt.

I'm thinking this isn't a truecrypt issue but a Ubuntu issue, at least with my install.  

Any other suggestions?   

thanks

---

### Post by 454redhawk on 2006-08-23
> **trmentry said:**
> No go.  I added the sticky bit to truecrypt and still get the no loopback device availble error.

 truecrypt: No free loopback device available for file-hosted volume

This is trying to mount as a user, sudo or as sudo su.   


I am mounting to a dir under /mnt.  I guess I got ahead of myself when typing the post and forgot to put it there.   Its actually /mnt/truecrypt.

I'm thinking this isn't a truecrypt issue but a Ubuntu issue, at least with my install.  



Any other suggestions?   

thanks


Try placing the actual truecrypt container file in your home directory and also try mounting it to a dir in your home directory.

Example
 truecrypt container file goes here /home/trmentry/truecpypt-container
and mount point would be /home/trmentry/truecrypt

It may or may not make a difference but give it a try anyway. I suspect its simply a permissions problem.

What file system is the container? Try using FAT and include the -u option or exclude it if not FAT

---

### Post by loafman on 2006-08-23
> **simone.brunozzi said:**
> It seems that I successfully installed Truecrypt 4.2a on my laptop.
However, after creating a normal (not hidden) truecrypt volume, I have the following error:

insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.15.ko': -1 Invalid module formatFATAL: Module truecrypt not found.
Thanks

OK, here goes... if you have any system other than the default supplied by the .deb (savefile.org or truecrypt.org or ...) you will need to follow option 2 with the following additions.

1) Get the source for your running kernel.  Supposedly, the headers work as well, but I have not tested that.

2) Use 'ln -s /usr/src/linux-source-<version> /usr/src/linux' to make sure /usr/src/linux is pointing to the correct source.

3) cp the /boot/config-<version> file to /usr/src/linux/.config.  This will make sure the config of the sources matches your running config (I have a K7-SMP box, nothing matched).

4) Now, go to the truecrypt-<version>/Linux dir and do:
   # ./build.sh
   # ./install.sh
I just take the defaults on the install.sh.  Seems to work.

This is the process I had to go through to get the module to load.  Other things to note are:

- If you have played with building a kernel and have gone back to a distributed kernel, do a 'sudo make distclean' from the /usr/src/linux directory prior to step 3 above.

- If you default to a different version of gcc than the currently released version (or one that matches the running kernel), you will need to build truecrypt with that version of gcc that matches your kernel's before step 4 above.

- If you have installed truecrypt with a .deb, remove it before doing any of this.

The idea of making a single .deb would be nice, but I think what will have to happen is that there will need to be a .deb for each version of the distributed kernel.  Plus, someone at Truecrypt needs to tackle doing decent documentation for the Linux world.

...Ken

---

### Post by trmentry on 2006-08-23
> **454redhawk said:**
> Try placing the actual truecrypt container file in your home directory and also try mounting it to a dir in your home directory.

Example
 truecrypt container file goes here /home/trmentry/truecpypt-container
and mount point would be /home/trmentry/truecrypt

It may or may not make a difference but give it a try anyway. I suspect its simply a permissions problem.

What file system is the container? Try using FAT and include the -u option or exclude it if not FAT


That worked!   I have a couple TC files on my file server.  In Windows (just got rid of that a few weeks ago) I would just mount the share they were in and mount the TC files over the network.   So I figured the same thing here.  Guess not.

I copied the TC file to my home dir and mounted it into a folder in my home dir which was where it was trying to mount before, but I guess it just needed to be local.

Why would it work this way?  And why didn't it work as root?   I'm just curious but happy this now working.   Thank you for the help.

---

### Post by koick on 2006-08-24
I was having same problems with Fedora Core 5 ( FC 5 ) and found this link helpful:
[http://rpmfarm.free.fr/5/i386/RPMS.farm/repodata/repoview/kmod-truecrypt-2.6.17-1.2174_FC5smp-0-4.2a-1.EL.FC5.html](http://rpmfarm.free.fr/5/i386/RPMS.farm/repodata/repoview/kmod-truecrypt-2.6.17-1.2174_FC5smp-0-4.2a-1.EL.FC5.html)

It seems that the kernel needs a patch for the truecrypt module.

---

### Post by koick on 2006-08-24
sorry, dup

---

### Post by koick on 2006-08-24
:-\"

---

### Post by 454redhawk on 2006-08-24
> **trmentry said:**
> That worked!   I have a couple TC files on my file server.  In Windows (just got rid of that a few weeks ago) I would just mount the share they were in and mount the TC files over the network.   So I figured the same thing here.  Guess not.

I copied the TC file to my home dir and mounted it into a folder in my home dir which was where it was trying to mount before, but I guess it just needed to be local.

Why would it work this way?  And why didn't it work as root?   I'm just curious but happy this now working.   Thank you for the help.


What file system is you file server? NTFS maybe? The truecrypt volume needs write access. If the file (volume) is stored on a NTFS partition it cant write to it and will fail. Or maybe some other file system that you did not have permission to write to.

Just guessing. Glad it worked

---

### Post by robert_pectol on 2006-08-25
In case anyone is interested in a very simplistic gui for mounting and unmounting Truecrypt containers, I've written one.  I call it, 'tcmounter.'  It really only gives you a desktop launcher that when clicked, opens a dialog password prompt for your container's password.  Upon successful authentication, it then mounts the container and opens it up in Nautilus file manager.  When the tcmounter window is closed, the container is then automatically unmounted and it is again secured.  tcmounter requires only a config file in your home directory.  The included installer script pretty much takes care of everything for you.

For those that want to try it out, simply download tcmounter here:
[http://rob.pectol.com/tcmounter.tgz](http://rob.pectol.com/tcmounter.tgz)
Then, untar/unzip the file with, "tar -zxvf tcmounter.tgz" and run the install script.  It will prompt you for anything it needs during execution and will then open the config file for you to edit.

A couple of things to note...
First, this version supports only 1 Truecrypt container and associated mount point.  Future versions will support more.  As I said, it's very simplistic!  Second, tcmounter requires that you already have a functioning Truecrypt installation.  Make sure you can mount/unmount your container manually before trying to use tcmounter.

Enjoy!

---

### Post by kabronkline on 2006-08-25
WOOT! This thread has taken off since my last visit. Thanks to everbody. I just updated the original HowTo post with debian install instructions instead of the script method contributed by Nano.

---

### Post by kotti on 2006-08-25
Excellent. Just one question.. shouldn't there be the -i switch in "dpkg truecrypt_4.2a-0_i386.deb" ?

---

### Post by wallacetheweasel on 2006-08-27
I realize the main focus of this thread is to install Truecrypt, but I'm a firm believer that you shouldn't get yourself into places you can't get out of.  I can't find any documentation or sites on the internet explaining how to uninstall Truecrypt if you compile it from source.

See, normally it's as easy as a make uninstall, but Truecrypt doesn't follow conventions.  I'd be happy if anyone could shed some light on how to go about it, other than tracking down every file by hand.

---

### Post by zooz on 2006-08-27
> **wallacetheweasel said:**
> I realize the main focus of this thread is to install Truecrypt, but I'm a firm believer that you shouldn't get yourself into places you can't get out of.  I can't find any documentation or sites on the internet explaining how to uninstall Truecrypt if you compile it from source.

See, normally it's as easy as a make uninstall, but Truecrypt doesn't follow conventions.  I'd be happy if anyone could shed some light on how to go about it, other than tracking down every file by hand.

I totally agree.
I refuse to try the methods discssed although I'm sure I can get this done. My reason is not only the lack of uninstall but also the need to recompile when my kernel will get updated.

I just want to use the program, not compiling, configuring, tweaking and etc. (you get the point).

I know it's only me who sufferes from my refusal to install. It's my choice and I don't think that the sw-developers/ubuntu-developers/anyone-else-to-be-blamed-for-truecrypt-is-not-in-official-repositories will be shocked by my choice and do something about it. I just think the time the good people spent here to try and get this work the wrong way (manual/semi-automated install) should be put to good use (getting this into repositories).

Thanks.

---

### Post by bandoba on 2006-08-27
I created truecrypt volume using /dev/hdb1. This is the only partition on 250GB hard drive. Volume creation was successful but I can't mount this volume. I get errors like this...

Enter password for '/dev/hdb1':
mount: you must specify the filesystem type
truecrypt: Mount failed

Can somebody help me understanding what is wrong here? BTW, while creating volume, it asked me what file system to use 1) FAT or 2) None. I selected option 2 which was None since I don't want to use 250GB FAT32 volume. Just want to make sure if that works or not.

TIA.

---

### Post by 454redhawk on 2006-08-28
> **bandoba said:**
> I created truecrypt volume using /dev/hdb1. This is the only partition on 250GB hard drive. Volume creation was successful but I can't mount this volume. I get errors like this...

Enter password for '/dev/hdb1':
mount: you must specify the filesystem type
truecrypt: Mount failed

Can somebody help me understanding what is wrong here? BTW, while creating volume, it asked me what file system to use 1) FAT or 2) None. I selected option 2 which was None since I don't want to use 250GB FAT32 volume. Just want to make sure if that works or not.

TIA.


If you wanted to encrypt the whole drive I think you should have done /dev/hdb not /dev/hdb1 . Anyway redo it and use FAT this time and mount with the -u option.

Just to see if you have trucrypt installed correctly.

---

### Post by bandoba on 2006-08-28
Thanks for quick reply 454redhawk. 

I can redo it for /dev/hdb but still trying to understand why I need to use FAT. Can I not use something like ext3? The reason I don't want to use FAT is eventually I am going to put this drive in a remote machine and plan to use rsync to backup data from my local server to this drive in remote machine. I believe rsynch doesn't work well w/ FAT system and hence I want something other than FAT.

---

### Post by 454redhawk on 2006-08-28
> **bandoba said:**
> Thanks for quick reply 454redhawk. 

I can redo it for /dev/hdb but still trying to understand why I need to use FAT. Can I not use something like ext3? The reason I don't want to use FAT is eventually I am going to put this drive in a remote machine and plan to use rsync to backup data from my local server to this drive in remote machine. I believe rsynch doesn't work well w/ FAT system and hence I want something other than FAT.


Lemmie research it and try it on my stuff. I will try with ext3.

---

### Post by 454redhawk on 2006-08-28
Ok, here is what needs to be done to use ext3.

You had most of it right but I will start from the top anyway.

```
truecrypt -c /dev/sda
```
That creates a truecrypt volume using the ENTIRE disk of sda. If you had a disk with other partitions on it you would choose the exact partition you want encrypted like /dev/sda1.
Replace /sda or /sda1 with whatever it is for you.

Continue on and answer each question with the default except the filesystem FAT or none, Choose NONE.

When you are finished type this

```
truecrypt /dev/sda
```
Replace /sda for whatever it is for you.
type in your password when asked.

That command will place an entry in the /dev/mapper directory.
Go see what the name of it is. Most likely truecrypt0

Now we want to create the ext3 filesystem on the drive
```
mkfs.ext3 /dev/mapper/truecrypt0
```
replace truecrypt0 with whatever it is for you.

It will create the ext3 file system (if its a large drive it will take awhile so be patient).

when its finished you can mount the volume as you normally would.
```
truecrypt /dev/sda /home/454redhawk/somemountpoint
```

Type your password

goto the mountpoint
create a sample file
unmount the volume
```
truecrypt -d
```
goto the mount point make sure nothing is there.
Remount the volume with the command above
goto the mount point and see if your sample file is there.

Hope it works for you.

---

### Post by bandoba on 2006-08-28
Thanks very much 454redhawk! The steps are very clear and worked without any problem. I appreciate your help.

Now just to understand, why does the truecrypt volume gets mapped as /dev/mapper/truecrypt0 instead of normal /dev/sda1?

---

### Post by 454redhawk on 2006-08-28
> **bandoba said:**
> Thanks very much 454redhawk! The steps are very clear and worked without any problem. I appreciate your help.

Now just to understand, why does the truecrypt volume gets mapped as /dev/mapper/truecrypt0 instead of normal /dev/sda1?

Good question. I have yet to find out. I would like the mounted volume appear as a drive/device as it does in windows. I have not yet taken the time to find out if it will work thst way.

---

### Post by TrinitronX on 2006-08-29
I just tried to install the .deb file, and it installed, however trying to open an encrypted volume returned an error inserting the kernel module.  I looked for the error I was recieving, and found that someone using the 686 kernel was getting the same error.  So, I grabbed the source and compiled (I already had my kernel, kernel headers, and gcc 4.0.3).  It seemed like it took forever to compile (almost as if it was re-compiling the kernel itself :p).  Anyway, after it finally compiled, I ran the install script, and it worked as well.  Then after all this, I tried to mount the same volume as before.  Again, a similar yet slightly different error when inserting the kernel module:

```

insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.15.ko': -1 Unknown symbol in module
FATAL: Error inserting truecrypt (/lib/modules/2.6.15-26-686/extra/truecrypt.ko): Unknown symbol in module, or unknown parameter (see dmesg)
truecrypt: Failed to load TrueCrypt kernel module
```

looking at dmesg as it suggests reveals:
```

...*snip*...
[17204598.752000] VFS: busy inodes on changed media.
[17204600.288000] VFS: busy inodes on changed media.
[17204600.304000] VFS: busy inodes on changed media.
[17204600.812000] VFS: busy inodes on changed media.
[17204600.828000] VFS: busy inodes on changed media.
[17204602.364000] VFS: busy inodes on changed media.
[17204602.380000] VFS: busy inodes on changed media.
[17204602.724000] truecrypt: disagrees about version of symbol dm_put_device
[17204602.724000] truecrypt: Unknown symbol dm_put_device
[17204602.724000] truecrypt: disagrees about version of symbol dm_unregister_target
[17204602.724000] truecrypt: Unknown symbol dm_unregister_target
[17204602.724000] truecrypt: disagrees about version of symbol dm_register_target
[17204602.724000] truecrypt: Unknown symbol dm_register_target
[17204602.724000] truecrypt: disagrees about version of symbol dm_table_get_mode[17204602.724000] truecrypt: Unknown symbol dm_table_get_mode
[17204602.724000] truecrypt: disagrees about version of symbol dm_get_device
[17204602.724000] truecrypt: Unknown symbol dm_get_device
[17204602.736000] truecrypt: disagrees about version of symbol dm_put_device
[17204602.736000] truecrypt: Unknown symbol dm_put_device
[17204602.736000] truecrypt: disagrees about version of symbol dm_unregister_target
[17204602.736000] truecrypt: Unknown symbol dm_unregister_target
[17204602.736000] truecrypt: disagrees about version of symbol dm_register_target
[17204602.736000] truecrypt: Unknown symbol dm_register_target
[17204602.736000] truecrypt: disagrees about version of symbol dm_table_get_mode[17204602.736000] truecrypt: Unknown symbol dm_table_get_mode
[17204602.736000] truecrypt: disagrees about version of symbol dm_get_device
[17204602.736000] truecrypt: Unknown symbol dm_get_device
[17204602.740000] truecrypt: disagrees about version of symbol dm_put_device
[17204602.740000] truecrypt: Unknown symbol dm_put_device
[17204602.740000] truecrypt: disagrees about version of symbol dm_unregister_target
[17204602.740000] truecrypt: Unknown symbol dm_unregister_target
[17204602.740000] truecrypt: disagrees about version of symbol dm_register_target
[17204602.740000] truecrypt: Unknown symbol dm_register_target
[17204602.740000] truecrypt: disagrees about version of symbol dm_table_get_mode[17204602.740000] truecrypt: Unknown symbol dm_table_get_mode
[17204602.740000] truecrypt: disagrees about version of symbol dm_get_device
[17204602.740000] truecrypt: Unknown symbol dm_get_device
[17204602.892000] VFS: busy inodes on changed media.
[17204602.904000] VFS: busy inodes on changed media.
[17204604.440000] VFS: busy inodes on changed media.
[17204604.452000] VFS: busy inodes on changed media.
[17204604.968000] VFS: busy inodes on changed media.
[17204604.980000] VFS: busy inodes on changed media.
..*snip*...

```

Ok, so apparently there are 'busy inodes' on my media, and something about the version of a symbol?
Why does the kernel module contain unknown symbols, and what does that exactly mean?  I compiled using my kernel version's source code (as far as I know).  My kernel headers are: linux-headers-2.6.15-26-686, which my 'linux' symlink points to (the new build.sh script autodetects the kernel source installed in '/usr/src/linux-source-2.6.15', and returns a message when compiling which references this directory.  I thought the linux kernel source is the same for the 386 and 686 kernels, with only the configs differing... is this right?

Anyone know how to fix this, or can anyone post a working binary compiled for the 686 kernel?

---

### Post by 454redhawk on 2006-08-29
How did you create the volume?
What commands did you use to create the volume?
What file system is the volume?
Where is the volume located?
What commands did you use to try and mount the volume?

If it was a previously created volume did you try to create a new one? If so what errors were shown.

Are you running a standard ver of ubuntu? (modified kernel?)

---

### Post by Jabbadahut on 2006-08-31
Hi, I am having trouble installing Truecrypt.  I typed the commands as shown at the beginning of this thread, but when I type the dpkg command, I get the following message

```

jabba@linux:~/truecrypt-4.2a$ dpkg truecrypt_4.2a-0_amd64.deb
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

Can anyone here help a Linux newbie?

---

### Post by 454redhawk on 2006-08-31
> **Jabbadahut said:**
> Hi, I am having trouble installing Truecrypt.  I typed the commands as shown at the beginning of this thread, but when I type the dpkg command, I get the following message

```

jabba@linux:~/truecrypt-4.2a$ dpkg truecrypt_4.2a-0_amd64.deb
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

Can anyone here help a Linux newbie?



You are runnig the amd64 .deb. Is that the correct one for you?

---

### Post by Jabbadahut on 2006-08-31
"You are runnig the amd64 .deb. Is that the correct one for you?"

I'm sure it is since I'm using the AMD64 version of Ubuntu 6.06 as I have a machine running w/Athlon 64 3800+ processor.

---

### Post by kverde on 2006-09-01
EDIT: please ignore.. i should have read the post closer!

---

### Post by phansiizwe on 2006-09-01
Jabbadahut:

Try,

```
sudo dpkg **-i** truecrypt_4.2a-0_amd64.deb
```

*sudo* makes you run the command as root (it will ask for your password), this is needed to install programs.

The -i switch tells dpkg to install something.

Next time this happens run:

```
man dpkg
```

and you will see the manual for dpkg.

---

### Post by AriseNow on 2006-09-02
Thanks for the HowTo :) The binary they provide only had worked for an earlier kernel so I had to compile form source. Everything works perfectly, I tested with a volume I created in the Windows version of Truecrypt.

---

### Post by pchearne on 2006-09-04
> **AriseNow said:**
> Thanks for the HowTo :) The binary they provide only had worked for an earlier kernel so I had to compile form source. Everything works perfectly, I tested with a volume I created in the Windows version of Truecrypt.

AriseNow,
I have **exactly** the same issue as you. Have tried the .deb etc with the sam results. When I've tried compiling myself using install.sh I get :

/truecrypt-4.2a/Linux$ sudo ./install.sh
Checking installation requirements...
Checking build requirements...
Building internal kernel modules (may take a long time)... In file included from drivers/usb/net/zd1211/zdusb.c:41:
drivers/usb/net/zd1211/zddevlist.h:7:2: error: #error "Error in source file, line 35"
make[4]: *** [drivers/usb/net/zd1211/zdusb.o] Error 1
make[3]: *** [drivers/usb/net/zd1211] Error 2
make[2]: *** [drivers/usb/net] Error 2
make[1]: *** [drivers/usb] Error 2
make: *** [drivers] Error 2
Error: Build failed - installation aborted

All the errors seem to be related to USB drivers? I'm not aware of any errors on my system re USB nor why it should matter anyway.


I'm using kernel 2.6.15-26-amd64-generic (and have tried booting to 2.6.15-26-amd64-server aswell).

The source I have in /usr/src is linux-source-2.6.15 (is this the one you have)

Any help gratefully received (since have have an inaccessible partition :-/ )

---

### Post by Jabbadahut on 2006-09-05
> **phansiizwe said:**
> Jabbadahut:

Try,

```
sudo dpkg **-i** truecrypt_4.2a-0_amd64.deb
```



Okay, thanks for the info.  I got it installed, but now I'm having trouble mounting an encrypted volume created on a FAT32 partition in Windows.

The FAQ on Truecrypt's website states that mounted volumes can be used in both Windows AND Linux.  Here's what I did (note that <nameofvolume> stands for the Truecrypt volume file created with the Windows version of Truecrypt):

```


jabba@linux:~$ sudo truecrypt /media/windows/<mameofvolume> /mnt/
Enter password for '/media/windows/<nameofvolume>:


```

Here's where I copy & paste the password that I had put in a text document. It doesn't show on the Terminal, but I assume this is for security reasons.  My password is 63 characters long - I know that sounds extreme, but I don't think this is an issue, as Truecrypt can accept passwords up to 64 characters.  Anyway, after inputing my password I get the following message:

```


insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.15.ko': -1 Unknown symbol in module (this is all on one line)
FATAL: Module truecrypt not found.
truecrypt: Failed to load TrueCrypt kernel module
jabba@linux:~$


```

Is this a problem with the program or with Ubuntu not loading the program correctly, or...?  Again, I'm using the AMD64 version of Truecrypt.

---

### Post by AriseNow on 2006-09-06
> **pchearne said:**
> AriseNow,
I have **exactly** the same issue as you. Have tried the .deb etc with the sam results. When I've tried compiling myself using install.sh I get :

/truecrypt-4.2a/Linux$ sudo ./install.sh
Checking installation requirements...
Checking build requirements...
Building internal kernel modules (may take a long time)... In file included from drivers/usb/net/zd1211/zdusb.c:41:
drivers/usb/net/zd1211/zddevlist.h:7:2: error: #error "Error in source file, line 35"
make[4]: *** [drivers/usb/net/zd1211/zdusb.o] Error 1
make[3]: *** [drivers/usb/net/zd1211] Error 2
make[2]: *** [drivers/usb/net] Error 2
make[1]: *** [drivers/usb] Error 2
make: *** [drivers] Error 2
Error: Build failed - installation aborted

All the errors seem to be related to USB drivers? I'm not aware of any errors on my system re USB nor why it should matter anyway.


I'm using kernel 2.6.15-26-amd64-generic (and have tried booting to 2.6.15-26-amd64-server aswell).

The source I have in /usr/src is linux-source-2.6.15 (is this the one you have)

Any help gratefully received (since have have an inaccessible partition :-/ )

Hmm, as I was installing a second time I got that error. I think the errors are not in your system but in the source. Try this method mentioned in a link from the first page: [http://www.ubuntuforums.org/showpost.php?p=1171019&postcount=18](http://www.ubuntuforums.org/showpost.php?p=1171019&postcount=18)

It leads into a German wiki, the whole process is editing:
/usr/src/linux-source-2.6.15/drivers/usb/net/zd1211/zddevlist.h
and commenting out the #error "Error in source file, line 35" part, it should work afterwards.

---

### Post by 454redhawk on 2006-09-07
> **Jabbadahut said:**
> Okay, thanks for the info.  I got it installed, but now I'm having trouble mounting an encrypted volume created on a FAT32 partition in Windows.

The FAQ on Truecrypt's website states that mounted volumes can be used in both Windows AND Linux.  Here's what I did (note that <nameofvolume> stands for the Truecrypt volume file created with the Windows version of Truecrypt):

```


jabba@linux:~$ sudo truecrypt /media/windows/<mameofvolume> /mnt/
Enter password for '/media/windows/<nameofvolume>:


```

Here's where I copy & paste the password that I had put in a text document. It doesn't show on the Terminal, but I assume this is for security reasons.  My password is 63 characters long - I know that sounds extreme, but I don't think this is an issue, as Truecrypt can accept passwords up to 64 characters.  Anyway, after inputing my password I get the following message:

```


insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.15.ko': -1 Unknown symbol in module (this is all on one line)
FATAL: Module truecrypt not found.
truecrypt: Failed to load TrueCrypt kernel module
jabba@linux:~$


```

Is this a problem with the program or with Ubuntu not loading the program correctly, or...?  Again, I'm using the AMD64 version of Truecrypt.




Easy fix:) If I understand you correctly you made a FAT volume right?. Because thats the only way to share the volume between windows and linux.

 You forgot the -u switch that FAT needs.

Also if you mount that volume as root or SU you may not be able to access it as a user (not sure).
Why not just change the rights to truecrypt so a user can run it instead of using sudo?
One more thing. Copy and paste the password may not work and is insecure since you are saving it in a file somewhere. Just pick a 4 or 5 word phrase with a few extra extended char that you can remember. "the chair is against the wall!@#" or something of the like.

---

### Post by Jabbadahut on 2006-09-08
> **454redhawk said:**
> Easy fix:) If I understand you correctly you made a FAT volume right?. Because thats the only way to share the volume between windows and linux.

 You forgot the -u switch that FAT needs.

Also if you mount that volume as root or SU you may not be able to access it as a user (not sure).
Why not just change the rights to truecrypt so a user can run it instead of using sudo?
One more thing. Copy and paste the password may not work and is insecure since you are saving it in a file somewhere. Just pick a 4 or 5 word phrase with a few extra extended char that you can remember. "the chair is against the wall!@#" or something of the like.

Thanks for the assistance, but I get the same error even when using the -u switch.  I also tried using a shorter password too.  On a hunch, I went directly to Truecrypt's website and posted this problem I'm having on their forum.  Here's what one user suggested:

> 
Somehow loading of the truecrypt kernel module failed. I'm sure you can produce the same error message by just doing 'modprobe truecrypt'. Please tell us if you get a different error message then. Anyway, I would suggest a brute-force attempt:

Download the truecrypt sources and compile&install truecrypt by yourself.

You may need to install a headers-only package for the kernel sources or even the full kernel sources or you might even need to build a new kernel from those sources. That's not as difficult as you might think :-)

Compiling the sources by yourself is IMHO the safest method to get a kernel module that is loadable by your kernel.


Looks like I'm back to the drawing board. ](*,) Now, if I can just only figure out how to un-install Truecrypt.  I would manually delete the files, but I have no idea where the heck they are stored, and I don't want to mess up the file system.

---

### Post by MontanaMax on 2006-09-08
> **kabronkline said:**
> 
**3. After the file is untarred execute the following commands seperately:**

cd truecrypt_4.2a
dpkg truecrypt_4.2a-0_i386.deb


I had to replace the second command line entry in install method #1, step 3 to this:

```
cd truecrypt_4.2a
sudo dpkg -i truecrypt_4.2a-0_i386.deb
```

Once I added the sudo and "-i" option this worked like a charm.

Thanks for the help - this was one of the "last critical desktop programs" I needed to get running on Linux to feel confident in throwing my windoze cd's in the trash. :-D

---

### Post by kotti on 2006-09-09
> **Jabbadahut said:**
> Looks like I'm back to the drawing board. ](*,) Now, if I can just only figure out how to un-install Truecrypt.  I would manually delete the files, but I have no idea where the heck they are stored, and I don't want to mess up the file system.

I dug around a bit at Truecrypt's forum and you could try the following:

1. First uninstall Truecrypt. If you used the precompiled .deb package type the following:
```
sudo dpkg -r truecrypt
```

If you've tried to install from the source code using the guide on the first page of this thread try this:

```
cd /usr/src/
rm linux
rm -R linux-source-2.6.15/
```

You might need to add sudo in the beginning of the commands.

2. Install a package called gawk, it's apparently needed for some reason at least on the 64bit Ubuntu.
```
sudo apt-get install gawk
```

3. Get truecrypt-4.2a-source-code.tar.gz from the Truecrypt page and install using the guide on the first page of this thread. It should work now. If you don't have the package gawk installed it might give you some errors related to usb.

---

### Post by Starlyth on 2006-09-12
I compiled a copy of truecrypt for K7 processor.  Seems to work fine. Except the way I want it to.  I did the chmod recommended earlier in this thread.  When compiling truecrypt, I set it to allow the user to run in.  However, to get it to run, it will only allow me to run with sudo, or as root, not as the user.  I can't get it to mount to anything but /mnt, and unless I'm running a the file manager (Thunar in this case) as sudo or root, I can only read the files, and not write to the volume.

I'm a (not totally) complete newbie at the whole Linux thing, so please excuse my failures.  I've checked a couple of online resources, but nothing seems to explain my situation.  Any ideas?](*,)

---

### Post by 454redhawk on 2006-09-13
> **Starlyth said:**
> I compiled a copy of truecrypt for K7 processor.  Seems to work fine. Except the way I want it to.  I did the chmod recommended earlier in this thread.  When compiling truecrypt, I set it to allow the user to run in.  However, to get it to run, it will only allow me to run with sudo, or as root, not as the user.  I can't get it to mount to anything but /mnt, and unless I'm running a the file manager (Thunar in this case) as sudo or root, I can only read the files, and not write to the volume.

I'm a (not totally) complete newbie at the whole Linux thing, so please excuse my failures.  I've checked a couple of online resources, but nothing seems to explain my situation.  Any ideas?](*,)



Did you create a FAT volume? If so did you use the -u option? (I am starting to sound like a broken record :))
I see it quite often people forget the -u switch on a FAT volume.

You will have the **EXACT** symptoms you described if you dont use the -u option on a FAT volume.


Just to be clear. When I ask if you created a FAT volume I am refering to the filesystem of the truecrypt container/volume NOT the filesystem of your disk or partition. (sorry, I just want to be clear)

---

### Post by Starlyth on 2006-09-13
The truecrypt volume is FAT. I am using the -u switch.  Do you think it matters where the switch is called?  I've put it both after the initial truecrypt command, plus I've put it before the -k  switch, which I have after the mountpoint call.

And no worries about asking the clarifying questions, I'm all for that.

---

### Post by 454redhawk on 2006-09-13
> **Starlyth said:**
> The truecrypt volume is FAT. I am using the -u switch.  Do you think it matters where the switch is called?  I've put it both after the initial truecrypt command, plus I've put it before the -k  switch, which I have after the mountpoint call.

And no worries about asking the clarifying questions, I'm all for that.

hmmmm....I can think of one more thing. Did you CREATE the volume as ROOT? In the past I have created a volume as root and ONLY been able to access it as root.

If the option came directly after truecrypt then you should have it right ```
truecrypt -u /dev/sda1 /home/Starlyth/mountpoint
```

Just to try and narrow this down. Is this a filetype volume or a disk or partition? If its a filetype volume where is it located? If it is a filetype volume try putting it in the /home/Starlyth. Also try mounting it (no matter if its a filetype or not) to a dir in /home/Starlyth

---

### Post by Starlyth on 2006-09-13
(If this ends up being a dupe, sorry.  I posted a reply a few hours ago, but I guess something didn't take.  Of course it could be the id10t at the keyboard.)

I created the Truecrypt volume in the Window version of TrueCrypt. Just to clarify, with my being unable to run truecrypt without sudo (or as root), I wouldn't be able to create a new Truecrypt volume without root or sudo privileges.

On a slightly different note, I was able to mount it into my home folder (I was using /home/tc, not /home/starlyth/tc), but of course I still only have read priviliges without sudo.

(sigh)

Added: just to let you know.  To experiment, I did create a new truecrypt volume WITHOUT sudo. So that means I can run truecrypt as a user.  However, I can't mount it without sudo (despite folder and file permissions showing me as the owner).  I'm guessing that my issue is not with Truecrypt, but with the mounting of the truecrypt volume.  I can mount the microdrive, by right-clicking on its desktop icon, and selecting mount from the menu, so I know I can mount other things.  It just seems to be the mounting of the Truecrypt volume that required higher privileges.

---

### Post by Starlyth on 2006-09-14
I found the answer (or AN answer that works) at the[TrueCrypt Forums]("http://forums.truecrypt.org/viewtopic.php?t=3821").

Here's the example command:

truecrypt --filesystem vfat --mount-options "rw,sync,gid=mygroup,umask=0007" /home/fcgreg/volume.tc /mnt/secure-tmp

Obviously (or not so obvious if you're me and fail to recognize the obvious), the "gid=mygroup" needs to be change to (as in my case) "gid=starlyth", and the file to be mounted and where need to be changed as well.

454redhawk - thanks for your help.  I'll be honest.  I still have no idea why this works, and the way that this thread (and as I understood it from the man pages at Truecrypt) doesn't.

---

### Post by 454redhawk on 2006-09-14
> **Starlyth said:**
> I found the answer (or AN answer that works) at the[TrueCrypt Forums]("http://forums.truecrypt.org/viewtopic.php?t=3821").

Here's the example command:

truecrypt --filesystem vfat --mount-options "rw,sync,gid=mygroup,umask=0007" /home/fcgreg/volume.tc /mnt/secure-tmp

Obviously (or not so obvious if you're me and fail to recognize the obvious), the "gid=mygroup" needs to be change to (as in my case) "gid=starlyth", and the file to be mounted and where need to be changed as well.

454redhawk - thanks for your help.  I'll be honest.  I still have no idea why this works, and the way that this thread (and as I understood it from the man pages at Truecrypt) doesn't.



Glad you got it going.

However that seems to be an excessive amount of options. Maybe you setup your user with some different options. Oh well, whatever works.:p

---

### Post by Jabbadahut on 2006-09-14
> **kotti said:**
> I dug around a bit at Truecrypt's forum and you could try the following:

1. First uninstall Truecrypt. If you used the precompiled .deb package type the following:
```
sudo dpkg -r truecrypt
```

If you've tried to install from the source code using the guide on the first page of this thread try this:

```
cd /usr/src/
rm linux
rm -R linux-source-2.6.15/
```

You might need to add sudo in the beginning of the commands.

2. Install a package called gawk, it's apparently needed for some reason at least on the 64bit Ubuntu.
```
sudo apt-get install gawk
```

3. Get truecrypt-4.2a-source-code.tar.gz from the Truecrypt page and install using the guide on the first page of this thread. It should work now. If you don't have the package gawk installed it might give you some errors related to usb.

Oh my gosh, thank you so much Kotti! :D I got the program up and running and everything is running smoothly.  Thank you, thank you, thank you! :cool:

---

### Post by Starlyth on 2006-09-14
I think that this a bit much on the options as well.  Plus I still haven't resolved the need to run as sudo to mount (whoops! I just realized I didn't note that part in my command).  Does anyone else have to use sudo to mount? Since I compiled the Truecrypt module, I guess this question would be aimed more towards those that compiled theirs as well.

---

### Post by norrman on 2006-09-14
> **kotti said:**
> Excellent. Just one question.. shouldn't there be the -i switch in "dpkg truecrypt_4.2a-0_i386.deb" ?

Noticed the same obvious typo ;)

---

### Post by Starlyth on 2006-09-14
(Proverbial whack upside Starlyth's head)  I figured out MY problem.  When installing (post kernel build), it helps to make sure that the defaults you receive are the same ones as in the instructions.  During the install, I was provided /usr/bin as the install location, not (as listed by the instructions) /usr/local/bin. (Note to self: read and UNDERSTAND the instructions).  I reinstalled TrueCrypt, did NOT stay with the default install location, and now I can run without sudo.

Thanks, again, redhawk454, for your help.  Your comment about there being too many switches caused me to step back and reexamine my situation.

-----

One thing I needed to add is that when using the .deb installation (before updating my Linux kernel, and thus having to compile my own TrueCrypt) I had to use sudo, so another advantage of compiling one's own TrueCrypt module, is that (after all my issues) I can run without sudo.

---

### Post by 454redhawk on 2006-09-15
> **Starlyth said:**
> (Proverbial whack upside Starlyth's head)  I figured out MY problem.  When installing (post kernel build), it helps to make sure that the defaults you receive are the same ones as in the instructions.  During the install, I was provided /usr/bin as the install location, not (as listed by the instructions) /usr/local/bin. (Note to self: read and UNDERSTAND the instructions).  I reinstalled TrueCrypt, did NOT stay with the default install location, and now I can run without sudo.

Thanks, again, redhawk454, for your help.  Your comment about there being too many switches caused me to step back and reexamine my situation.

-----

One thing I needed to add is that when using the .deb installation (before updating my Linux kernel, and thus having to compile my own TrueCrypt) I had to use sudo, so another advantage of compiling one's own TrueCrypt module, is that (after all my issues) I can run without sudo.



Great job!
This is one slick program when you get it going.

---

### Post by balan on 2006-09-16
Got it installed fine & mounted my truecrypt volume to /mnt/test but the "test" is folder is locked. Could anyone show me how to unlock/access it?

balan

---

### Post by 454redhawk on 2006-09-16
> **balan said:**
> Got it installed fine & mounted my truecrypt volume to /mnt/test but the "test" is folder is locked. Could anyone show me how to unlock/access it?

balan

Need more info

What filesystem is the truecrypt volume?
What kind of volume is it? (entire partition, entire drive or file type volume?)
Where is the volume located if its a file type?
What commands are you using to mount it? (post EXACTLY the command you used)
Is it a previously created volume from windows?

---

### Post by flyingbrass on 2006-09-21
Now that we have yet another new kernel I had to fight with Truecrypt again.

Last time the deb install worked after manually removing everything with Truecrypt in its name.  Not this time.

I don't understand why the build.sh script rebuilds all modules (I presume that's what it is doing).  Building them all isn't necessary and takes forever.  I gave up after about 30 minutes.

Somewhere in one of these Truecrypt threads a guy said he just ran make in truecrypt-4.2a/Linux/Kernel and truecrypt-4.2a/Linux/Cli, then ran the install script.  That's what I did, and it worked for me too.

---

### Post by TiredBird on 2006-09-29
I just wrote four paragraphs and lost it because the system said I wasn't signed in and wouldn't let me sign in. It was probably just blowing in the wind anyway so no big loss. 

My TrueCrypt is not working for the first time in several months. I'm going to try something and if it works I'll post again to tell you what I did.

---

### Post by TiredBird on 2006-09-29
Maybe I have learned something. At least its working for me.

I have just tried the binary available from Truecrypt, (as referred to in the howto at the beginning of this thread), and it works just fine with the 2.6.15 kernels for '386' but not with the 'k7' kernels. As an experiment I ran it with 2.6.15-23-386 and 2.6.15-27-386 and had no problem but it would not work with 2.6.15-27-k7, (it gives the oft-mentioned 'Failed to load...' message.) 

So even though my machine has an AMD Duron processor and should be running a 'k7' kernel, I'm going to use '386' kernels because my TrueCrypt works with those, at least for now. It'll be interesting to see what happens when we upgrade from 2.6.15. Also I'm keeping the 'k7' kernel handy in case I encounter some other problems.

I've been using TrueCrypt quite successfully now for a couple of months. I have five encrypted containers, including a file type on a thumbdrive, an internal harddrive file type, two internal harddrive partition types and one that encrypts an entire USB external harddrive (160 GB). Three of the containers are accessed from both Dapper and XP and all mount wherever I want with whatever permissions I desire. I would be happy to share my methods for the above if you don't mind hearing it from a 'newb'. Just ask.

---

### Post by paca on 2006-09-29
I have created a normal volume and a hidden, now how do I mount the hidden volume?

---

### Post by Starlyth on 2006-09-29
TiredBird:

TrueCrypt is VERY kernel sensitive.  The .deb installer downloaded from TrueCrypt.org is for the 386 kernel.  You will have to compile your own to get it to work on the K7 kernel.  Plus, there is a strong likelihood that you will have to recompile after every kernel update.  Just use the Synaptic Installer, download the K7 kernel source and the kernel headers, then follow the TrueCrypt OPTION 2 instructions that kabronkline wrote at the beginning of the forum.  Make sure NOT to repeat my mistakes, and verify that the output that TrueCrypt gives you during the install matches kabronkline's.  Mine didn't, and I didn't catch it for awhile.

---

### Post by TiredBird on 2006-09-29
Starlyth,

I appreciate your reply but one of the things that got lost when I wasn't allowed to enter my reply was a statement by me that I wasn't going to get involved with compiling anything that I'm using regularly. Either it works out of the box in binary form or I don't use it.

I have several machines, each of which should be running one of the alternative kernels but all of which will run on the '386' version. Since the '386' versions run all of my software without any recompiles I'd like to continue running the '386' versions. Is there any reason that I shouldn't be doing that? What do I gain by running the 'ky' and '686' versions? What do I lose or risk by running the '386' versions?

---

### Post by Starlyth on 2006-09-29
TiredBird:

From what I understand, you will lose very little, if anything, by running the "generic" 386 kernel.  In my case, I am using a laptop, and because of a few issues, I started compiling.  I'm still a newbie at it.  One thing to keep in mind though, as I said earlier, is that TrueCrypt is very kernel sensitive.  Anytime your kernel is updated, like the update just recently, there is a strong chance that TrueCrypt will error out, and either you will have to reinstall TrueCrypt (depeding on if it will recompile itself in the install package, about which I have no idea), or you will have to complile a compatible version for yourself.  In other words, you may have to start compiling regardless, but someone else may be able to speak on that more authoritatively than I.  In all things, Linux, I am still a newbie.

---

### Post by TiredBird on 2006-09-29
Starlyth,

Thanks again. Actually, if I'm not mistaken, the '386' kernels were installed by Ubuntu's installer when I started using 5.10 which was sometime early this year. So as long as it isn't doing any harm and things are working, I'm going to stick with it.

As far as compiling goes, I've done a little in the past but I have an aversion to software that needs to be recompiled just to make it run. I program and compile as a hobby, not because I have to.

Yes, I'm a 'newb' when it comes to Linux but not to computing in general.

I have read this entire thread and I have watched people give up on TrueCrypt because it caused errors on their machines. No where did I see anyone explain that it works fine with the 386 kernel. I thought I would introduce that in hopes that more people would find it workable.

I personally think that TrueCrypt is one of the best pieces of encryption software ever produced. I want to keep using it myself and I want to see others use it. (I have written a rather lengthy howto on using it with XP which was my first exposure to it.) It's extremely good encryption software but for most people, myself included, it has to be nearly invisable. I've done a lot to make that so. Having to compile everytime the kernel changes is counter to that objective.

---

### Post by TiredBird on 2006-09-29
Paca,

I am sorry I didn't answer your question earlier. Guess I got caught up in the elation of getting my own system to work.

Unfortunately, hidden volumes are an area I have never dabbled in, even under XP. I can only suggest that you read the full documentation, (available on the [TrueCrypt website]("http://www.truecrypt.org/docs/")), very carefully so you understand how they are doing it. 

(The full documentation unfortunately was written for XP so the interface instructions are quite different - gui in XP and cli in Linux - but the way it works is still the same.) Then read the ['man' page for Linux]("http://www.truecrypt.org/docs/?s=linux-manpage") to figure out how to interface to it.

Good luck!

---

### Post by thehigherentity on 2006-10-04
not sure this is the right place to post this but, I hope somone can help me....

I have installed Truecrypt 4.2 on Ubuntu 6.06 and have created a 3 gig file with ext3 format on my slave drive which mounts and unmounts fine.

however this file is now too small and I decided I would make one masive 50 gig file lol "that should last me a lifetime".

I created the file with no filesystem as i did with the first and waited the hour for it to be made, but once i ran the following command to make the new filesystem it crashed my computer?

mkfs -t ext3 /dev/mapper/truecrypt0

i have tried making smaller files and these all work just fine and there is no differance to how i am making these apart from the size differance but as soon as i try to make anything of any great size it crashes/locks/freezes?

is this a known problem ? I have looked all over for anyone with the same problem but cant seem to find anyone or anything to help me get this working. 

I can make a 50 gig fat32 just fine (but the file size limmit is a big problem for me so i need to have ext2/3) and the 50 gig file with no filesystem seems to be made ok too its just when i try to make the file system i have no luck.

could anyone help me out here or at least point me in the right direction?

Thank for any help u can give
Stephen

---

### Post by TiredBird on 2006-10-04
Not sure this helps but...

I have a 160 GB USB external drive that is set up as one TrueCrypt partition but it's formatted in FAT32. As I recall, I created the partition without any formatting and then used TrueCrypt to format the drive. Although I run it from Ubuntu 6.06 I probably formatted it with TrueCrypt on XP. Not sure that TrueCrypt for Linux has the ability to format on Linux.

Looking back at your post I see you are using TrueCrypt 4.2. I don't think they added the Linux formatting capability until 4.2a. You might check on that. You might need to update your TrueCrypt.

---

### Post by thehigherentity on 2006-10-04
I have tried updating to the new 4.2a but still no joy, I have even looked at making it in winxp but i cant make it into a ext2/3 format from windows and I dont have the trust to use ntfs in linux.

When I make the file in linux I only have the option to make fat32 or no filesystem, I cant understand why there would not be an option for an ext2/3 format there already?

is there a way to format with truecrypt? or can this only be done with the mkfs -t ext3 /dev/mapper/truecrypt0 command?

I'm thinking it might be better to make a 50 gig partition and try to use that but to be honist i would rather have a file just incase i need to more it at anytime.

if anyone has any ideas please let me know how i might beable to create this

thanks again in advance
Stephen

---

### Post by TiredBird on 2006-10-04
I might have misunderstood what you are trying to do. I thought you were trying to format a partition, but now I'm thinking you're trying to format a file as your container. Which is it?

If you're trying to create a file there is at least one limitation you should be aware of. A fat file cannot be larger than 4GB. Fat partitions however, if I remember correctly, go to 4 TB. However, Windows, while it can read and write large partitions, is not capable of formatting a fat partition larger than 32 GB, if I remember correctly. There is probably a limitation on Ext2/3 file and partition sizes too but I've never heard anyone mention them.

If you are trying to create a file as the container, you have probably exceeded the maximum size, even for ext2/3. Frankly, I can't imagine a 50 GB file.

I would strongly recommend that if that is your size objective, you should make it a partition, not a file. You talked about moving it. With today's partition managers, (QTParted and GParted in particular), it is probably easier to copy or move a large partition than a large file. The largest file type container I personally use for TrueCrypt is 512 MB and I'm even considering turning that into a partition. Partitions seem a lot easier to manage, at least for me.

---

### Post by thehigherentity on 2006-10-06
Well you was right, I have made a partition and converted it to ext3 no problems. just a couple of questions I have though...

If i wanted to change the size of the partition could i just resize it or would i have to reformat and re-encrypt it again?

also if i copyed th partision to another partision would I have to make sure they were both the same size?

hope you dont mind me asking all these questions lol

thanks
Stephen

---

### Post by TiredBird on 2006-10-07
Stephen,

I think what I'm saying here is correct. You might want to check into the [TrueCrypt forum]("http://www.truecrypt.org/forum.php") for more definitive answers though.

If you create a partition and let TrueCrypt format it as an encrypted partition, then change the size of the partition, you have just lost it. It is not going to open as an encrypted partition. You have to start over. The good news is that when you create a partition, you don't have to format it. Give it an unformatted file type and let TrueCrypt do the formatting. (I just tried to format an encrypted partition as ext3 and couldn't do it. How did you do it and are you sure it's still ext3?)

I have not done a lot of partition copying and when I have, I have always copied to the same size. Gparted uses 'dd' to do the copying, which is explained in [Wikipedi]("http://en.wikipedia.org/wiki/Dd_(Unix)")a and in the 'man' pages. If it's an encrypted partition, my guess is that you better make it the same size if you don't want to lose your encrypted data.

---

### Post by thehigherentity on 2006-10-08
> (I just tried to format an encrypted partition as ext3 and couldn't do it. How did you do it and are you sure it's still ext3?)

My problem was, using fat32 I could not manage to save a largefile into the partition so what i did was run truecrypt -c and when i got the the file-format i selected non, once the drive was created I mounted it to /media/locked and ran 

mkfs.ext3 /dev/mapper/truecrypt0

after this i unmounted and remounted the drive and now it will take large files.

I have ran a df -T on the mounted drive and get the following

Filesystem Type   1K-blocks Used Available Use% Mounted on
/dev/mapper/truecrypt0
              ext3    40313996  16786888  21479224  44% /media/locked

SO I'm fairly sure its worked but then again I am new to all this and could be-doing it all wrong lol

---

### Post by TiredBird on 2006-10-09
It sounds like it worked and your method of doing it makes sense. Are you still having to use TrueCrypt to create and destroy '/dev/mapper/truecrypt0'? If so, you've found out something that I definitely wasn't aware of.

If so, the procedure seems to be as follows:

(1) Create an empty partition - no need to format it - just assign the space. (The partioning program - whichever one is used - will make the appropriate entries in the partition table.) 

(2) Encrypt the partition using TrueCrypt but with no file system format.

(3) Map the encrypted partition as /dev/mapper/truecrypt0 with TrueCrypt.

(4) Format the encrypted partion /dev/mapper/truecrypt0 with some filesystem creation program.

(5) Mount the encrypted file system on some previously defined mount point with appropriate options as determined by the file system type.

Is that the way you got it working?

My problem is that I had always formatted the partitions as fat32, (using TrueCrypt to do the formatting), because I wanted to be able to read and write from both Linux and Windows. My understanding was that fat32 was the only one that worked reliably under both systems. Recently, I had need of an encrypted file system under Linux only but I couldn't figure out how to create an encrypted ext3 system, like you have, so I just used fat32 again.

In spite of having learned something new, I believe that what I told you about changing partition size and copying encrypted partitions is still true. If you find out otherwise, please let me know.

---

### Post by thehigherentity on 2006-10-10
I have tried it a couple of different ways now and both seem to work

1. create partition, no need to format, but i have also managed to do this with a preformated partition that was in ext3 format.

2. Encrypt the partition using TrueCrypt but with no file system format.

3. Map the encrypted partition as /dev/mapper/truecrypt0 with TrueCrypt.
simply run "truecrypt /dev/hdb2" or what ever your partition is and this maps the drive to /dev/mapper/truecrypt0

4. Format the encrypted partion /dev/mapper/truecrypt0 with some filesystem creation program. in my case "mkfs.ext3 /dev/mapper/truecrypt0"

I did have to run "truecrypt -d" to unmount the drive before i could remount it

5. Mount the encrypted file system on some previously defined mount point with appropriate options as determined by the file system type.
in my case no options were needed and all i use is "truecrypt /dev/hdb2 /media/locked" after this it will ask for the password and thats it

I use ext3 on both windows xp and linux, all i have done is added ext3 support to windows, a quick google will find plenty of patches and as of yet i have had no problems.

I have also tried this with encrypted files but have had problems with the larger size 25 gig pluss however you can make files well into the 50 gig maybe more if u use the fat32 filesystem.

I havent tried changing partition size but if i do get round to it i will let you know the outcome :-k

---

### Post by bandoba on 2006-10-13
I used exact same steps as listed by TiredBird in the post above and everything worked fine. I then moved my encrypted disk (with only one partition) to other machine. Installed truecrypt (no errors using method 1), mounted the partition (again no errors). But when I issued command dmesg | tail it shows following line...

truecrypt: no version for "struct_module" found: kernel tainted.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on dm-5, internal journal
EXT3-fs: mounted filesystem with ordered data mode.

What exactly does this mean and what can I do to fix this?

TIA

---

### Post by alexus_fs on 2006-10-13
[truecrypt-4.2a - ubuntu kernel 2.6.15-27-686]

Hi!

This is my kernel version:
# cat /proc/version
Linux version 2.6.15-27-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006

The installation using the truecrypt-4.2a.deb package (Method #1) did not worked to me: I had the "FATAL: Module truecrypt not found." error.

So I tried Method #2... and now truecrypt works fine!
I suggest you to update this howto to the new truecrypt 4.2a version (there are just some small discrepancies to fix).

Thank you a lot!

---

### Post by bodhi.zazen on 2006-10-14
First nice how-to.

This how-to has been added to the ubuntu wiki at: [Truecrypt](http://doc.gwos.org/index.php/TrueCrypt)

Note: IN INSTALLATION METHOD 2 YOU NEED TO CHANGE THE COMMANDS TO **truecrypt-4.2a**.

---

### Post by rakotolavasanga on 2006-10-17
I am also having a problem with the truecrypt kernel module.  Although truecrypt appears to compile normally and works to create a volume, when I try to mount a volume I get the following (probably familiar) error message:

```
insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.15.ko': -1 Invalid module format
FATAL: Error inserting truecrypt (/lib/modules/2.6.15-27-server/extra/truecrypt.ko): Invalid module format
truecrypt: Failed to load TrueCrypt kernel module
```

The kernel, source, and gcc version match, which seems to be the error in most cases.  I did notice that the first time I ran the build.sh script, it got hung up building the kernel module.

Any help would really be appreciated.  Details:

Ubuntu 6.06
Kernel upgraded using apt-get to 2.6.15-27-server
Kernel sources (linux-source) installed manually 2.6.15
gcc 4.0.3

Thanks again for any insights.  I've been trying to figure this out for a couple of days.  Incidentally, the ubuntu .deb package from the truecrypt website installs fine on my kubuntu installation, but no success on the server.

---

### Post by kotti on 2006-10-17
rakotolavasanga: Try installing the package gawk (sudo apt-get install gawk) and then using the #2 method of the guide. This seems to work for many people who get the same error message.

---

### Post by TrinitronX on 2006-10-18
> **rakotolavasanga said:**
> I am also having a problem with the truecrypt kernel module.  Although truecrypt appears to compile normally and works to create a volume, when I try to mount a volume I get the following (probably familiar) error message:

```
insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.15.ko': -1 Invalid module format
FATAL: Error inserting truecrypt (/lib/modules/2.6.15-27-server/extra/truecrypt.ko): Invalid module format
truecrypt: Failed to load TrueCrypt kernel module
```

The kernel, source, and gcc version match, which seems to be the error in most cases.  I did notice that the first time I ran the build.sh script, it got hung up building the kernel module.

Any help would really be appreciated.  Details:

Ubuntu 6.06
Kernel upgraded using apt-get to 2.6.15-27-server
Kernel sources (linux-source) installed manually 2.6.15
gcc 4.0.3

Thanks again for any insights.  I've been trying to figure this out for a couple of days.  Incidentally, the ubuntu .deb package from the truecrypt website installs fine on my kubuntu installation, but no success on the server.

I have gotten this error too when attempting to compile truecrypt for my 686 kernel.  It seems that the current truecrypt build.sh script does not ensure that your kernel config is for the current kernel!  Here's my post on how to fix it, and ensure that it asks every time whether or not to use the current running kernel's config: [http://www.ubuntuforums.org/showpost.php?p=1577276&postcount=29](http://www.ubuntuforums.org/showpost.php?p=1577276&postcount=29)

It's as simple as removing an if statement in the script :D.
Hope this works for you.

EDIT: I've just filed a bug report regarding this scripting 'oops', and hopefully the fix will be accepted into the build script.  Until then, I hope this works for everyone who encounters the bad kernel module errors.

---

### Post by Ravenik on 2006-10-23
Following your instructions I managed to create EXT3 enrypted partition on Suse Linux.

But I need help with mounting it on WindowsXP. I just can't unmount it without "force" ](*,) . TC says that files or folders are in use. I don't run any application which may access files while unmounting.
Do you experience such problem?
I suppose problem is because of Ext2IFS_1_10b driver I use.
Could you give a link to EXT2/3 driver for Windows you use? I am looking for driver which will not cause me to "forced" unmount in TrueCrypt. 

Mark

---

### Post by WhiteHorse on 2006-10-24
> **kabronkline said:**
> I'm not entirely sure of the answer to your question; however, to my understanding as long as the release is 2.6.15 there will be no need to reinstall Truecrypt.

Yes, but only if the source headers change(such as in a major version upgrade). You might get lucky and it will still work with a new kernel, but that just depends on the changes.

---

### Post by Acollective on 2006-10-24
Just as a small aside to this forum .. Fantastic thread BTW and the howto is well done (needs to be updated to include the check for gawk tho with the 64bit kernel). Has anyone tried using ntfs3g with truecrypt. I thought I would ask before I jumped in to trying to compile it (the fuse dependency is currently breaking the ntfs3g configure script). 

   BTW I posted the, now standard, error message after installing over in the truecrypt forums and got really no love. Thanks to all who have/are maintaining this thread. It has been immensely helpful in getting truecrypt to work on my system.

---

### Post by Acollective on 2006-10-24
woohoo... after posting my last message I went ahead and got into it with ntfs-3g and fuse.

After finally getting the above two items to compile and install, I unmounted my truecrypt volume and re-mounted it with the flag --filesystem  set to ntfs-3g. Guess what ... it worked. I am now reading and writing to my ntfs truecrypt volume. 

so the answer to my previous question was YES. you can use ntfs-3g with an ntfs truecrypt volume.

---

### Post by Aybara on 2006-11-02
I tried #1, but when I tried to mount my volume it said that it could not load the truecrypt kernel module.

#2 went smooth until I reached 

sudo sh ~/src/truecrypt-4.2a/Linux/build.sh

The output I got was:

anders@anders-laptop:/usr/src$ sudo sh ~/src/truecrypt-4.2a/Linux/build.sh
Checking build requirements...
Configure kernel source according to the currently running kernel? [Y/n]: 
Configuring kernel source in /usr/src/linux-source-2.6.17... Done.
Preparing kernel build system in /usr/src/linux-source-2.6.17... Done.
Building internal kernel modules (may take a long time)... Done.
Building kernel module... cd: 132: can't cd to Kernel
Error: Failed to build kernel module

Anyone know what my problem is?

I'm running Edgy.

---

### Post by Aybara on 2006-11-02
played around a bit, and did the step "sudo ln -s linux-source-2.6.15 linux" again, only I created a symlink called kernel. after that it started building. no idea why I had to do this, but I like I said I have edgy and linux-source-2.7.10-generic. maybe something that needs to be updated in the tutorial??

EDIT: later in the build process I get another error:

WARNING: sound/oss/cs4232.o - Section mismatch: reference to .init.text: from .text between 'cs4232_pnp_probe' (at offset 0x7c) and 'unload_cs4232'
Done.
Building truecrypt... cd: 137: can't cd to ../Cli
Error: Failed to build truecrypt


Am I doing something wrong here, or doesn't this guide work for edgy?

---

### Post by Aybara on 2006-11-02
I found the solution in this thread

[http://ubuntuforums.org/showthread.php?t=269305](http://ubuntuforums.org/showthread.php?t=269305)

All I had to do was:

tar xfz truecrypt-4.2a-build.tar.gz
cd truecrypt-4.2a-build/Linux/
sudo ./install.sh

Now things work like a charm :-D

---

### Post by Skoezie on 2006-11-10
Did not have any idea that there was a linux version of this program untill today. Just installed the deb from the Truecrypt site & works :-D 

Made a simple mount & unmount script and voila. Finally able to use it in Windows & Linux

Also tried the tcmounter gui thingy, but that wasn't that big of a succes. Any plans for a 'real'  Truecrypt gui?

---

### Post by ranpha on 2006-11-12
He i just finished some testing with encrypting. I have three questions. 

Can you mount a true crypt volume with another decrypt program? 

And I made a volume with ext3 now i want to make a hidden volume within the normal encrypt volume. Is this possible with ext3?

And is their a program which can see and (attempt) a cracking of encrypt volumes? I want to make sure my files a secure where nobody can find them

---

### Post by zetetic on 2006-11-17
I'm on the middle of a truecrypt nightmare, so It would be nice if someone could please help me.

a) If I try method 1, I can install Truecrypt and even create a truecrypt volume. But when I try to open the encrypted volume I get this error:
«insmod: error inserting 'usr/share/truecrypt/kernel/truecrypt-2.6.15.ko': -1 Invalid module format
Fatal: Could not open '/lib/modules/2.6.15-27-686/extra/truecrypt.ko': No such file or directory
truecrypt: Failed to load truecrypt kernel module»

b) If I try method 2, I cant't install truecrypt, getting this error after "sudo sh ./install.sh":
«trying to overwrite '/lib/modules/2.6.15-27-686/modules.isapnpmap', which is also in package linux-image-2.6.15-27-686
dpkg-deb: subprocess paste killed by signal (Broken pipe)»

I'm on Dapper LTS, with kernet image 2.6.15-27-686.

Can anyone please help me? Thanks in advance,
zetetic

---

### Post by ranpha on 2006-11-19
zetetic, does this also happen when you use a 386 kernel?

---

### Post by zetetic on 2006-11-19
ranpha:
«zetetic, does this also happen when you use a 386 kernel?»

Well, I really don't know, I've never used a 386 kernel. But the HowTo posted on this thread doesn't say I cannot use a 686 kernel...

Does someone has a solution for my problem?

---

### Post by mrsteveman1 on 2006-11-23
For you who are having problems with loading the module saying it isnt there (truecrypt.ko), try loading tcrypt instead of truecrypt, as i have found this to be what the module is apparently called now, though i used the binary 6.10 deb and not source. 

If as some noted you are seeing that the module isnt there, try loading tcrypt instead.



If you see "module is wrong format" etc etc, then its probably got more to do with the kernel and gcc version.

i believe most of these problems stem from ubuntu using gcc 4.1.2 for the kernel now (and everything else in the system) as of 6.10, not sure what the exact problem is but that would seem to be why the kernel tools (modprobe) are telling people the module isnt in the right format etc etc.

i am using ubuntu 6.10 installed from the new iso so that might be newer than some of you are using (hence the name of the thread), but i suspect this thread just happens to be where the discussion is at the moment.

i should note that i had none of these problems in 6.06 so perhaps people using 6.06 had upgraded certain parts of the system without knowing it? this could be why people in 6.06 have the same problem, with the kernel and gcc being updated etc.

---

### Post by zetetic on 2006-11-24
mrsteveman1: Thanks for your post.

I didn't upgraded any party of the system, except de kernel image, which, If I remember well, was automatic updated from ubuntu repositories.

My kernel image is "2.6.15-27-686".

And my linux source is "linux-source-2.6.15", wich is the lastest available on ubuntu repositories and the same used by kripkenstein in the HowTo he posted on the this same thread!

Perhaps kripkenstein, himself, could through some light on this subject...

I really need truecrypt, cause I want to put some stuff on an encrypted volume and burn the file on a CD or DVD.

So any help would be appreciated.

regards,
zetetic

---

### Post by SundaY82 on 2006-12-02
Hi!

First of great guide...

Some questions. 

1) How strong is the encryption if you compare to loop-aes 256 AES or dm-crypt?

2) Running Ubunutu 6.10 server and the #1 didnt work for me, same error as you have seen here before about not being able to load the .ko module while trying to mount the enc volume you just created. So i uninstalled it and ran #2, and at ./build.sh i changed from /usr/bin to /usr/local/bin as suggested in guide. There where also a new question between 2 and 3 but i used default /usr/share/man , something about were to store docs and modules i think. All went good and i managed to create encrypt the partition and format it as ext3 and mount it. One big annoying thing though, when changing to /usr/local/bin , now when i type truecrypt it still searches in /usr/bin for it at cant find it, so i have to type /usr/local/bin/truecrypt everytime, how can i change this?

3) Last question, how can i format the partition as raiserfs instead of ext3? i tried mkfs -t raiserfs /dev/mapper/truecrypt0 but it just said the mkfs.raiserfs didnt exist or something like that. What is the proper whay to create a raiserfs partition?

---

### Post by stefanl on 2006-12-05
> **thehigherentity said:**
> ...
I use ext3 on both windows xp and linux, all i have done is added ext3 support to windows, a quick google will find plenty of patches and as of yet i have had no problems.
...

thehigherentity,
I have tried to use both ext2ifs v1.10c and explorer2fs v1.07 but they can't find my TC mounted partition. Which software are you using to access ext3 on XP? 

Regards,
Stefan

---

### Post by DarthSwampy on 2006-12-11
I use Ubuntu 6.06 on my Server and everything is working fine, except that I want to change the MySQL datadir to a directory in my truecrypt-partition. MySQL wont run unless the owner of the directory is the user "mysql", and every file and folder on the truecrypt-partition is automaticly "swampy", and it cant be changed by chown. Anyone got an answer? ](*,)

---

### Post by TheWizzard on 2006-12-23
> **kabronkline said:**
> 
**IF YOU USE THIS HOW-TO, PLEASE CONTRIBUTE BY POSTING A REPLY WITH YOUR RESULTS**

thanks for the howto! after struggeling for hours i found your #2 method and it worked like a charm :KS 

just one remark: in order to mout as a normal user, one needs to use the u option (it's in the man) like this: 

```
$ truecrypt -u /home/wizzard/test.tc /home/wizzard/encrypted/
```

---

### Post by 454redhawk on 2006-12-29
> **TheWizzard said:**
> thanks for the howto! after struggeling for hours i found your #2 method and it worked like a charm :KS 

just one remark: in order to mout as a normal user, one needs to use the u option (it's in the man) like this: 

```
$ truecrypt -u /home/wizzard/test.tc /home/wizzard/encrypted/
```

-u is for fat volumes only

TrueCrypt requires administrator (root) privileges. If you intend to
use TrueCrypt from a user account, you should execute the following command
as root in a terminal. This will only have to be done once.

```
sudo chmod u+s /usr/bin/truecrypt
```

---

### Post by TheWizzard on 2006-12-29
> **454redhawk said:**
> -u is for fat volumes only

TrueCrypt requires administrator (root) privileges. If you intend to
use TrueCrypt from a user account, you should execute the following command
as root in a terminal. This will only have to be done once.

```
sudo chmod u+s /usr/bin/truecrypt
```

my volume is fat. i couldn't find hints on fat vs none, so i chose the default.

---

### Post by 454redhawk on 2006-12-30
> **TheWizzard said:**
> my volume is fat. i couldn't find hints on fat vs none, so i chose the default.

Here is an explanation using an entire drive or entire partiton formatted to ext3. Substitute with a file type volume as nessesary. Example    truecryptFile.tc ------ vs--------     /dev/sda


[http://www.ubuntuforums.org/showpost.php?p=1432222&postcount=109]("http://www.ubuntuforums.org/showpost.php?p=1432222&postcount=109")

---

### Post by 454redhawk on 2006-12-30
If anyone would like to give it a try I wrote a crude GUI for truecrypt. Give it a few tries and it makes mounting, unmounting, creating, viewing and formatting a snap.
Save the below to a file and call it whatever you want. Right click and make it executable. Create an app launcher on your panel to start it.

```
#!/bin/bash

# TrueCrypt GUI. Written by 454redhawk on Sep 19 2006 in Afghanistan. 
######The first option must be selected in addition to your mount options if mounting a FAT volume.#####
# If mounting a USB Device type volume (partition or drive) and you do not know the dev name you can find out by selecting the fdisk option.
#If its an # ext3 truecrypt volume it will say its invalid but this is of no concern as the volume cannot be recognized because its encrypted.


function MNT_UMNT ()
{

ACTION=`zenity --height=340 --width=410 \
			--title="TRUECRYPT GUI" \
			--text="Pick your Function" \
			--list \
			--checklist \
			--column="Pick This" \
			--column="Action" \
			False "Also check this option if MOUNTING a FAT Volume" \
			False "Mount File Type Volume" \
			False "Mount Partition or Disk" \
			False "UnMOUNT ALL" \
			False "View already mounted volumes" \
			False "Create a Truecrypt Volume" \
			False "Format a volume to ext3" \
			False "Run Fdisk -l to see devices"`
			if [ $? = 1 ]; then
				exit
			fi
			if [ "$ACTION" = "UnMOUNT ALL" ]; then
			truecrypt -d
			zenity --info --text="All Volumes Unmounted"
			elif [ "$ACTION" = "Also check this option if MOUNTING a FAT Volume|Mount File Type Volume" ]; then
			SELECT_VOLUME
			elif [ "$ACTION" = "Mount File Type Volume" ]; then
			SELECT_VOLUME
			elif [ "$ACTION" = "Also check this option if MOUNTING a FAT Volume|Mount Partition or Disk" ]; then
			SELECT_DEVICE
			elif [ "$ACTION" = "Mount Partition or Disk" ]; then
			SELECT_DEVICE
			elif [ "$ACTION" = "View already mounted volumes" ]; then
			truecrypt -l | zenity --width=500 --height=100 --text-info --title "Here are the mounted volumes"
			MNT_UMNT
			elif [ "$ACTION" = "Run Fdisk -l to see devices" ]; then
			fdisk -l | zenity --width=600 --height=600 --text-info --title "Here are your devices"
			MNT_UMNT
			elif [ "$ACTION" = "Create a Truecrypt Volume" ]; then
			zenity --info --text="A Terminal is about to open,  when you finish close the window.
			
			Click ok to open the terminal
			"
			xterm -hold -e truecrypt -c
			zenity --info --text="Volume Created Unless you aborted early.

You may now mount and use your volume if you made it FAT. Otherwise you need to format it for ext3"
			MNT_UMNT
			elif [ "$ACTION" = "Format a volume to ext3" ]; then
			FMT
			fi
}


function SELECT_DEVICE ()
{
DEVICE=`zenity --entry --title="Device Select" --text="Select Your disk or partition, Example sda or sda1"`
if [ $? = 1 ]; then
exit
fi
SELECT_MNTPT
}

function SELECT_VOLUME ()
{
TC_VOLUME=`zenity --title="Select a TrueCrypt Volume" --file-selection --filename=/home/`
			if [ $? = 1 ]; then
			exit
			fi
		
			SELECT_MNTPT
}


function SELECT_MNTPT ()
{
MNTPNT=`zenity --title="Select a Mount Point for the TrueCrypt Volume" --file-selection --directory --filename=/media/`

			if [ $? = 1 ]; then
			exit
			fi

MNT
}

function MNT ()
{
if [ "$ACTION" = "Also check this option if MOUNTING a FAT Volume|Mount Partition or Disk" ]; then
		zenity --entry --title="Truecrypt Password" --text="Enter Your Password:" --hide-text | truecrypt -u /dev/$DEVICE $MNTPNT
elif [ "$ACTION" = "Also check this option if MOUNTING a FAT Volume|Mount File Type Volume" ]; then
		zenity --entry --title="Truecrypt Password" --text="Enter Your Password:" --hide-text | truecrypt -u $TC_VOLUME $MNTPNT
elif [ "$ACTION" = "Mount Partition or Disk" ]; then
		zenity --entry --title="Truecrypt Password" --text="Enter Your Password:" --hide-text | truecrypt /dev/$DEVICE $MNTPNT
elif [ "$ACTION" = "Mount File Type Volume" ]; then
		zenity --entry --title="Truecrypt Password" --text="Enter Your Password:" --hide-text | truecrypt $TC_VOLUME $MNTPNT
fi
if [ $? = 1 ]; then
		zenity --error --text="ERROR  Maybe an incorrect password or you tried to mount an unformated ext3 volume"
else
 		truecrypt -l | zenity --width=500 --height=100 --text-info --title "Here are the mounted volumes"
fi
exit
}

function FMT ()
{
zenity --question --text="MAKE SURE all volumes are UNmounted.

If a volume IS MOUNTED it will be destroyed.

Any data on the volume to be formatted volume WILL be destroyed.

 If you are unsure cancel NOW and check, or else you WILL lose data"
if [ $? = 1 ]; then
zenity --error --text="You were unsure and hit cancel. Use the GUI to view mounted volumes"
MNT_UMNT
fi
if [ $? = 0 ]; then

TYPE=`zenity --height=300 --width=370 \
			--title="What are we formatting?" \
			--text="What are we formatting?" \
			--list \
			--radiolist \
			--column="Pick This" \
			--column="Action" \
			False "DEVICE type volume" \
			False "File type Volume"`
fi
			if [ "$TYPE" = "DEVICE type volume" ]; then
FMT_DEVICE_SYSTEM=`zenity --entry --title="Device Select" --text="Select Your disk or partition to be formatted. Example sda or sda1"`
if [ $? = 1 ]; then
exit
fi
zenity --entry --title="Truecrypt Password" --text="Enter The Password for the selected volume:" --hide-text | truecrypt /dev/$FMT_DEVICE_SYSTEM
if [ $? = 1 ]; then
exit
fi
zenity --info --text="You may be prompted for your SUDO password to format the volume (Close the window when its finished)"
xterm -hold -e sudo mkfs.ext3 /dev/mapper/truecrypt0
zenity --info --text="$FMT_DEVICE_SYSTEM format complete

You may have to log into a SU file manager (Press F2 and type gksudo nautilus) after you mount it and change permissions on the mounted location to your user or group before you can write to it"
truecrypt -d
MNT_UMNT

elif [ "$TYPE" = "File type Volume" ]; then
FMT_FILE_SYSTEM=`zenity --title="Select a TrueCrypt Volume to be formatted" --file-selection`
if [ $? = 1 ]; then
exit
fi
zenity --entry --title="Truecrypt Password" --text="Enter The Password for the selected volume:" --hide-text | truecrypt $FMT_FILE_SYSTEM
if [ $? = 1 ]; then
exit
fi
zenity --info --text="You may be prompted for your SUDO password to format the volume (Close the window when its finished)"
xterm -hold -e sudo mkfs.ext3 /dev/mapper/truecrypt0
zenity --info --text="$FMT_FILE_SYSTEM format complete 


You may have to log into a SU file manager (Press F2 and type gksudo nautilus) after you mount it and change permissions on the mounted location to your user or group before you can write to it"
truecrypt -d
MNT_UMNT
fi

}
MNT_UMNT

```

---

### Post by TheWizzard on 2006-12-30
> **454redhawk said:**
> Here is an explanation using an entire drive or entire partiton formatted to ext3. Substitute with a file type volume as nessesary. Example    truecryptFile.tc ------ vs--------     /dev/sda


[http://www.ubuntuforums.org/showpost.php?p=1432222&postcount=109]("http://www.ubuntuforums.org/showpost.php?p=1432222&postcount=109")

aha, now i understand. thanks!

---

### Post by AbeJarano on 2007-01-08
Thank you for the walkthrough.  I chose the second method and contentedly waited 20 minutes or so while the modules compiled.  Everything was neat and clear, and ordered so that the next step seemed to follow the previous.  The only glitch I had was at step 6.  Couldn't figure why I needed to know the kernel version number there but not a real problem.  And at the end there was no example of mounting a device but it turned out to be easy to do.
Thanks again, I'm beginning to see I'm going to enjoy linux Ubuntu a lot more than I expected.

---

### Post by bandoba on 2007-01-14
Hello friends,

I am using truecrypt with Edgy. I used method 2 and truecrypt seems to mount volumes fine. But everytime I mount volume using truecrypt, following message shows in dmesg log.

*[17191269.156000] truecrypt: no version for "struct_module" found: kernel tainted.*

Can somebody tell me what this means and how can I get it working without any messages like this?

I would also like to know how to mount truecrypt volume (in my case the whole partition /dev/sda1) automatically from /etc/fstab. Can somebody tell me how can I provide username and password when I make entry for this volume in /etc/fstab?

TIA.

---

### Post by MontanaMax on 2007-01-14
I don't believe a truecrypt file can be mounted using fstab, but you can write a quick bash script and call it on boot or user startup to mount the drive automatically and achieve the same end effect.

---

### Post by bandoba on 2007-01-15
> **MontanaMax said:**
> I don't believe a truecrypt file can be mounted using fstab, but you can write a quick bash script and call it on boot or user startup to mount the drive automatically and achieve the same end effect.

I was planning put /home folder on truecrypt volume. So as per your comment, the only way I can do it is mount it from script at boot time. Is that correct?

---

### Post by igb on 2007-01-16
Thanks for the guide, I managed to get it all up and running on Edgy AMD64 by compiling from source. 

Here's a few additions to your guide:

[LIST]
[*]When compiling from source don't forget to change the permissions on truecrypt to allow normal users to mount drives:
[/LIST]

```
chmod u+s /usr/bin/truecrypt
```

[LIST]
[*]To make an ext3 container, rather than FAT:
[/LIST]

[LIST]
[*]Set the format type to None when creating the container.
[*]Mount the container:
[/LIST]
```
truecrypt /home/ian/encrypted_files.tc
```

[LIST]
[*]Check which device your container is mounted as:
[/LIST]

```
ian@hannah:/var/home/ian$ truecrypt -vl
/dev/mapper/truecrypt0:
 Volume: /home/ian/encrypted_files.tc
 Type: Normal
 Size: 1073741312 bytes
 Encryption algorithm: AES
 Mode of operation: LRW
 Read-only: No
 Hidden volume protected: No

```

[LIST]
[*]Now format the device:
[/LIST]

```
sudo mkfs.ext3 /dev/mapper/truecrypt0
```

[LIST]
[*]You can now mount the formatted container as per usual:
[/LIST]

```
sudo truecrypt /home/ian/encrypted_files.tc /home/ian/encrypted
```

Note do **NOT** use the -u option for ext3 drives.

[LIST]
[*]You will now have to change the permissions of the mount point. You only need to do this once (it survives a reboot):
[/LIST]
```
sudo chmod ian.users -R /home/ian/encrypt
```

Ian.

---

### Post by flyingbrass on 2007-01-17
Good info, Ian.  There is a problem creating large ext2/3 containers.  Anything over a few GB will hard lock the system.  According to posts at the Truecrypt forum this is a kernel issue.  The workaround is to:

export MKE2FS_SYNC=10 

Then create filesystem normally.

See [http://forums.truecrypt.org/viewtopic.php?t=4205](http://forums.truecrypt.org/viewtopic.php?t=4205)

---

### Post by lex1 on 2007-01-18
is it possible to open a container created under linux on a windows machine?

lex1

---

### Post by TheWizzard on 2007-01-19
> **lex1 said:**
> is it possible to open a container created under linux on a windows machine?

lex1

yes

---

### Post by edgimar on 2007-01-20
In case it is of interest to any of you, I have written a small shell script which can be used to automatically mount/unmount a truecrypt volume with a GUI-like interface...  I have attached it to this  message.

I realized that if you're not logged in, you can't access the attachment, so for those of you who don't want to log in...

```

#!/bin/bash
# script to mount/unmount a truecrypt volume under GNOME

# this script assumes that it will be run by a user, and that the truecrypt binary has had its
# permissions set to SUID root.  (i.e. from a root shell, type "chmod u+s /usr/bin/truecrypt")

# A launcher should be created which runs this script from an icon on the desktop or panel.
# Make sure to specify the script's absolute path in the launcher

# Using this script could be a security hazard -- someone could maliciously modify the script
#  to get your encrypted-volume password.  Use it at your own risk...

# ------------- CHANGE THE FOLLOWING VARIABLES AS NEEDED -----------------
# location of truecrypt binary
TC=/usr/bin/truecrypt

# file containing an encrypted volume
ENCRYPTEDFILE=/home/johndoe/secretvolume.tc

# where to mount the volume
MOUNTPOINT=/media/truecrypt
# ------------------------------------------------------------------------

function update_volismounted {
VOLISMOUNTED=`$TC -l|grep $ENCRYPTEDFILE`
}

update_volismounted
if [ "$VOLISMOUNTED" ]; then
  # unmount the volume
  $TC -d $ENCRYPTEDFILE
  update_volismounted
  if [ "$VOLISMOUNTED" ]; then
    # open file-browser
    zenity --error --text="truecrypt volume mounted at $MOUNTPOINT could not be unmounted."
  else
    zenity --info --text="Successfully unmounted truecrypt volume $ENCRYPTEDFILE"
  fi
else
  # mount the volume
  gksu -p --message "Please enter your truecrypt password for $ENCRYPTEDFILE" | $TC -u $ENCRYPTEDFILE $MOUNTPOINT
  update_volismounted
  if [ "$VOLISMOUNTED" ]; then
    # open file-browser
    nautilus $MOUNTPOINT
  else
    zenity --error --text="Mounting of truecrypt volume failed."
  fi
fi

```

---

### Post by bandoba on 2007-01-20
> **flyingbrass said:**
> Good info, Ian.  There is a problem creating large ext2/3 containers.  Anything over a few GB will hard lock the system.  According to posts at the Truecrypt forum this is a kernel issue.  The workaround is to:

export MKE2FS_SYNC=10 

Then create filesystem normally.

See [http://forums.truecrypt.org/viewtopic.php?t=4205](http://forums.truecrypt.org/viewtopic.php?t=4205)

I have used truecrypt to create ext3 contains as big as 250GB and never saw this issue. Maybe I am just lucky! Thanks for the info though.

---

### Post by TDK800 on 2007-03-10
If the only reason TrueCrypt won't be included in Ubuntu is that it's not GPL, lets start mailing the makers of TrueCrypt to publish it under GPL. With enough requests from people and also  donations I'm confident they'd change to GPL.

---

### Post by daz23 on 2007-03-17
Thanks for the guide. I was able to finally figure out how to mount my NTFS partition created in WinXP. 

> truecrypt --filesystem ntfs-3g /dev/sda1 /home/daz/tcmnt

---

### Post by kabronkline on 2007-03-20
> **TDK800 said:**
> If the only reason TrueCrypt won't be included in Ubuntu is that it's not GPL, lets start mailing the makers of TrueCrypt to publish it under GPL. With enough requests from people and also  donations I'm confident they'd change to GPL.

This sounds like a great idea. Maybe somebody could create a template for an email everybody interested could send over to the good people at Truecrypt?

---

### Post by popie on 2007-03-20
I was just looking at Automatix and noticed that it now has an installer and even an interface for Truecrypt. Anyone try this yet?

I haven't tried it yet, but wanted to let everyone know that this might be a good option for an easy install. If you try it please let us know how it works.

[www.getautomatix.com]("http://www.getautomatix.com")

---

### Post by N7DR on 2007-03-20
> **popie said:**
> I was just looking at Automatix and noticed that it now has an installer and even an interface for Truecrypt. Anyone try this yet?

[www.getautomatix.com]("http://www.getautomatix.com")

I guess that this must be 32-bit only. My 64-bit install of dapper doesn't mention TrueCrypt when I run automatix :-(

---

### Post by outofnicks on 2007-04-12
454redhawk posted on December 30th, 2006:
> If anyone would like to give it a try I wrote a crude GUI for truecrypt. Give it a few tries and it makes mounting, unmounting, creating, viewing and formatting a snap.

Thanks for that script, I haven't tried it much but it seems to work very well for me using truecrypt 4.3. Dude, that's not crude it looks quite thorough to me!

[http://ubuntuforums.org/showpost.php?p=1946485&postcount=186](http://ubuntuforums.org/showpost.php?p=1946485&postcount=186)

---

### Post by nanotube on 2007-05-07
ok, it looks like truecrypt is not releasing binary debs for dapper, and today i got a message from user *jetpack* requesting some updates to the install script that i have posted here earlier... so, here's the new version of it, attached to this message. if you are using a later version of ubuntu, one which is supported by truecrypt, you probably don't really need this script. :)

---

### Post by wazzup on 2007-06-18
> **kabronkline said:**
> [SIZE=4]*** UPDATE: Truecrypt + GUI Frontend is installable via Automatix for 32-Bit Ubuntu ***
*** I will no longer be updating this post, feel free to make use of any of this text in any way ***
*** If you would like to repost this as a 64-Bit install guide, PM Me... I'll give you the entire thread text (formatting and all) ***

THANKS FOR ALL THE SUPPORT! 
[/SIZE]


Too bad automatix is still giving 4.1 where 4.3 is already out. (also it won't let me make a  volume, so something else is buggy as well).


/edit: oh wait, I had an old binary of truecrypt that was in the front of the path... 

still can't make a volume though. (at least not using forcefield... commandline is fine though)

---

### Post by arnieboy on 2007-06-19
> **kabronkline said:**
> [SIZE=4]*** UPDATE: Truecrypt + GUI Frontend is installable via Automatix for 32-Bit Ubuntu ***

Its now available on 64 bit Automatix-Feisty as well

---

### Post by i M@N on 2007-06-19
Hello.

i've always compiled truecrypt like in the #2 method until the v4.3 where i had to use a patch to be able to mount my fat volume without entering the sudo password then my vfat volume password.
Today i'm forced to keep my 4.3 version because even with the command
```
sudo chmod u+s /usr/bin/truecrypt
```
i can't mount my vfat volume with options like i used to to in 4.3 (patched, yes this is when they begun to make truecrypt act this stupid way, i don't want to type 2 passwords, only one) :
```
truecrypt --filesystem vfat -u --mount-options "rw,gid=0,umask=0000" /media/mountpoint/tcvolume /media/tcvolume
```
it's the same : i've got to enter 2 passwords and that's so boring ...

So i did a 
```
sudo visudo
```
then added **iman    ALL=NOPASSWD: /usr/bin/truecrypt** and **ctrl+o** to save **sudo -v** to reload sudo finally **sudo -l** to ensure ... but i still can't mount my vfat volume specifing mount options without the sudo password ...

Please help me !

@+...

---

### Post by i M@N on 2007-08-15
Hello.

Finally i've got it !

i've compiled truecrypt 4.3a and :

edited /etc/sudoers :
```
sudo visudo
```
and i added this at the end of /etc/sudoers :
> #iman truecrypt
iman ALL=NOPASSWD:/usr/bin/truecrypt

And that roxX ... no more sudo pass asked when mounting a truecrypt volume, just the truecrypt volume pass. :mrgreen:

(it didn't work last time because i putted a space beetween NOPASSWD: and /usr/bin/truecrypt)

@+...

---

### Post by wieman01 on 2007-08-15
> **i M@N said:**
> Hello.

Finally i've got it !

i've compiled truecrypt 4.3a and :

edited /etc/sudoers :
```
sudo visudo
```
and i added this at the end of /etc/sudoers :


And that roxX ... no more sudo pass asked when mounting a truecrypt volume, just the truecrypt volume pass. :mrgreen:

(it didn't work last time because i putted a space beetween NOPASSWD: and /usr/bin/truecrypt)

@+...
Thanks, buddy. Worked like a charm for me.

---

### Post by kaginken on 2007-09-15
Thanks for the posting of these instructions!  I initially installed the .deb I downloaded from Truecrypts website.  I downloaded the edgy version because there wasn't a dapper version, actually upgraded from dapper just to insure I could get truecrypt installed using the .deb file.  

Installed the .deb and I got the same problem noted above with the fatal errors.

Uninstalled truecrypt:  sudo dpkg -r truecrypt

Downloaded the source as per your instruction, compiled, built, etc

Now it works!!  Thanks!:guitar:

---

### Post by Tehut on 2007-10-18
I use kernel 2.6.23.1.
When I tried to compile truecrypt 4.3a I got the following error:

Checking build requirements...
 Building kernel module... .../truecrypt-4.3a-source-code/Linux/Kernel/Dm-target.c: In function &#8216;dm_truecrypt_init&#8217;:
 .../truecrypt-4.3a-source-code/Linux/Kernel/Dm-target.c:659: error: too many arguments to function &#8216;kmem_cache_create&#8217;
[...]
 Error: Failed to build kernel module

Fixed it following the instructions I found somewhere else ([http://forums.fedoraforum.org/showthread.php?p=873476):](http://forums.fedoraforum.org/showthread.php?p=873476):)
Remove the last 'NULL' in line 659 of Dm-target.c in truecrypt.../Linux/Kernel.

---

