---
title: "Installing QEMU, KQEMU, and DHCP Patch"
date: 2006-06-02
forum: Outdated Tutorials &amp; Tips
---

### Post by andrejkw on 2006-06-02
This is more of a Automatic Installation script, than a HOW-TO.
As of now, it will only work with **Breezy** and **Dapper**.

This script will compile and install:
[IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG] **QEMU 0.8.2 or QEMU from CVS Snapshot** (Choice Given during Install)
[IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG] **KQEMU 1.3.0pre9**

Included QEMU Patches (Optional - asked during installation):
[IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG] **[DHCP Patch]("http://people.brandeis.edu/%7Ejcoiner/qemu_idedma/qemu_dma_patch.html#dhcp")**
[IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG] **Mouse Wall Bug Patch** is no longer needed (=> 0.8.2)

The credits go to:
- Nando Florestan (I used some parts of his Script)
- Saad N. (For inspiration and testing)
- Dmytro (Breezy Testing, Spell Checking, and NT, 95, 95 Russian Testing)

**For those wanting to install _Windows XP_ under QEMU/KQEMU check out this more detailed tutorial: [WindowsXPUnderQemuHowTo]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")**

**INSTALLATION INSTRUCTIONS**:
```
wget http://soultrap.net/andrejkw/install_qemu.sh
chmod +x ./install_qemu.sh
sudo ./install_qemu.sh
``` Afterwards just follow the on-screen instructions.

**USAGE INSTRUCTIONS**:
[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] NOTICE FOR 64bit USERS: You have to use **qemu-system-x86_64** instead of **qemu**. Otherwise the "-kernel-kqemu" option will not work.

1.) The first thing you probably want to do is to create a disk image into which you will install the Guest operating system. You can do this by typing the following into the terminal.
M = MB
G = GB
```
qemu-img create **(FILE NAME).img** **(SIZE OF IMAGE)**

*Example:*
qemu-img create guest.img 1G
``` 
2.) After the image has been created (assuming the step above gave you no errors) we can prepare to launch QEMU. But before we go ahead and do that, we have to make a few decisions. The basic command we will be using now is:
```
qemu -localtime -hda **(FILE NAME).img**

*Example:*
qemu -localtime -hda guest.img
``` 
3.) Now, with the basic command ready, we will now move on to the paramaters. Now, in order to get our Guest OS installed we have to install it from a CD or a CD image. Add the '-cdrom' parameter to tell QEMU that you want to have a CD-ROM present.
```
qemu -localtime -hda **(FILE NAME).img** _-cdrom **(PATH TO DEVICE OR CD IMAGE)**_

*Example:*
qemu -localtime -hda guest.img -cdrom /home/andrejkw/XPCD.iso
**OR**
qemu -localtime -hda guest.img -cdrom /dev/cdrom
``` 
3.) Ok, so now we told QEMU what to use as our CD-ROM drive. The next step is to tell it to boot from our CD-ROM before booting from our Hard-Drive image. To do this we will add a '-boot d' (D: stands for the CD-ROM drive in this case, because it comes right after C: )
```
qemu -localtime -hda **(FILE NAME).img** -cdrom **(PATH TO DEVICE OR CD IMAGE)** _-boot d_

*Example:*
qemu -localtime -hda guest.img -cdrom /dev/cdrom -boot d
``` 
4.) Next thing we have to do, is tell QEMU that we have KEMU installed. It is supposed to detect if KQEMU is installed, but I had a bad experience with this. And it doesn't hurt to be sure that QEMU is using KQEMU. You can do this by adding the '-kernel-kqemu' option.
```
qemu -localtime -hda **(FILE NAME).img** -cdrom **(PATH TO DEVICE OR CD IMAGE)** -boot d _-kernel-kqemu_

*Example:*
qemu -localtime -hda guest.omg -cdrom /dev/cdrom -boot d -kernel-kqemu
``` 
5.) If you were to press enter now, QEMU would start booting. But before you do that, you should consider adding some of these options:

[IMG]http://ubuntuforums.org/images/icons/icon3.gif[/IMG] If you want to give your Guest OS more RAM (QEMU uses 128MB by default) add the '-m SIZE' option.
M = MB
G = GB
```
qemu -localtime -hda **(FILE NAME).img** -cdrom **(PATH TO DEVICE OR CD IMAGE)** -boot d -kernel-kqemu _-m **RAM SIZE**_

*Example:*
qemu -localtime -hda guest.img -cdrom /dev/cdrom -boot d -kernel-kqemu -m 512M
``` 
[IMG]http://ubuntuforums.org/images/icons/icon3.gif[/IMG] If you are going to be installing Windows 2000/XP as your Guest OS, consider adding '-win2k-hack' as your option. It fixes some major issues, like the "Not enough disk space." while installing.
```
qemu -localtime -hda **(FILE NAME).img** -cdrom **(PATH TO DEVICE OR CD IMAGE)** -boot d -kernel-kqemu -m **RAM SIZE** _-win2k-hack_

*Example:*
qemu -localtime -hda guest.img -cdrom /dev/cdrom -boot d -kernel-kqemu -m 512M -win2k-hack
``` 
-----------------------------------------------------------------------

Check out Qemu Launcher (a nice QEMU Gui for GNOME) at [http://download.gna.org/qemulaunch/debian/](http://download.gna.org/qemulaunch/debian/)
Note: In the "Other" tab add "-kernel-kqemu" (no quotes) to the "Additional Arguments" field.

**If you are experiencing the Transparent Window bug (By running XGL...) check out Saad's thread ([http://ubuntuforums.org/showthread.php?t=187941](http://ubuntuforums.org/showthread.php?t=187941)) for instructions on how to fix it.**

Andrew, :D

---

### Post by SaadN on 2006-06-04
This script worked great for me. 100% with no errors are all! Thanks a lot! :)

**Screenshots**
[http://img288.imageshack.us/img288/9775/screenshot8wa.png](http://img288.imageshack.us/img288/9775/screenshot8wa.png)

[http://img147.imageshack.us/img147/9962/screenshotqemu6fc.png](http://img147.imageshack.us/img147/9962/screenshotqemu6fc.png)

---

### Post by Toxicity999 on 2006-06-04
Checking it out now will post results.

---

### Post by Johnsie on 2006-06-05
It didn't work for me. I had the following output:


[B]Your Ubuntu release is: Dapper Drake 6.06
Is this correct? yes
Would you like to download QEMU from the CVS (Unstable)? no
Installing Dependencies...
Reading package lists... Done
Building dependency tree... Done
libsdl1.2debian is already the newest version.
The following extra packages will be installed:
  binutils cpp cpp-3.4 cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-3.4-base gcc-4.0
  installwatch libaa1-dev libartsc0-dev libasound2-dev libaudio-dev
  libaudiofile-dev libc6-dev libesd0-dev libgl1-mesa-dev libglib2.0-dev
  libglu1-mesa-dev libice-dev libncurses5-dev libslang2-dev libsm-dev
  libstdc++6-4.0-dev libstdc++6-dev libx11-dev libxau-dev libxdmcp-dev
  libxext-dev libxi-dev libxt-dev linux-kernel-headers make mesa-common-dev
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev
Suggested packages:
  binutils-doc cpp-doc gcc-4.0-locales debian-keyring gcc-3.4-doc lib64stdc++6
  gcc-4.0-doc manpages-dev autoconf automake1.9 libtool flex bison gcc-doc
  libc6-dev-amd64 lib64gcc1 libasound2-doc glibc-doc libglib2.0-doc
  libstdc++6-4.0-doc stl-manual libstdc++6-doc
Recommended packages:
  libmudflap0-dev
The following packages will be REMOVED
  libsdl1.2debian-alsa
The following NEW packages will be installed
  binutils build-essential checkinstall cpp cpp-3.4 cpp-4.0 dpkg-dev g++
  g++-3.4 g++-4.0 gcc gcc-3.4 gcc-3.4-base gcc-4.0 installwatch libaa1-dev
  libartsc0-dev libasound2-dev libaudio-dev libaudiofile-dev libc6-dev
  libesd0-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev libice-dev
  libncurses5-dev libsdl1.2-dev libsdl1.2debian-all libslang2-dev libsm-dev
  libstdc++6-4.0-dev libstdc++6-dev libx11-dev libxau-dev libxdmcp-dev
  libxext-dev libxi-dev libxt-dev linux-kernel-headers make mesa-common-dev
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev
  zlib1g-dev
0 upgraded, 47 newly installed, 1 to remove and 0 not upgraded.
Need to get 25.0MB of archives.
After unpacking 97.1MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  x11proto-core-dev libice-dev libsm-dev x11proto-kb-dev x11proto-input-dev
  libxau-dev libxdmcp-dev libx11-dev libxi-dev x11proto-xext-dev libxext-dev
  libxt-dev binutils linux-kernel-headers libc6-dev cpp-4.0 cpp gcc-4.0 gcc
  libstdc++6-4.0-dev g++-4.0 g++ make dpkg-dev build-essential installwatch
  checkinstall gcc-3.4-base cpp-3.4 gcc-3.4 libstdc++6-dev g++-3.4
  libslang2-dev libncurses5-dev libaa1-dev libglib2.0-dev libartsc0-dev
  libasound2-dev libaudiofile-dev libesd0-dev mesa-common-dev libgl1-mesa-dev
  libglu1-mesa-dev libaudio-dev libsdl1.2-dev libsdl1.2debian-all zlib1g-dev
E: There are problems and -y was used without --force-yes
ERROR: Unable to Install Dependencies.[/B]

---

### Post by OldGaf on 2006-06-05
[QUOTE=andrejkw]Hey Guys,

This is more of a Automatic Installation script, than a Howto.
It will only work with **Breezy** and **Dapper**.

This script will compile and install:
- **QEMU 0.8.1 or QEMU from CVS** (Choice Given during Install)
- **KQEMU 1.3.0pre7**

Included QEMU Patches (Optional - Choice Given during Install):
- **[DHCP Patch]("http://people.brandeis.edu/~jcoiner/qemu_idedma/qemu_dma_patch.html#dhcp")**
- **[Mouse Wall Bug]("http://lists.gnu.org/archive/html/qemu-devel/2006-05/msg00112.html")**

Installation Instructions:
```
wget http://exvision.net/install_qemu.sh
chmod +x ./install_qemu.sh
sudo ./install_qemu.sh
```

Afterwards just follow the on-screen instructions.

The credits go to:
- Nando Florestan (I used some parts of his Script)
- Saad N. (For inspiration and testing)

If you have any suggestions how I can improve this script, feel free to post them in here :)

Check out Qemu Launcher (a nice QEMU Gui for GNOME) at [http://download.gna.org/qemulaunch/debian/](http://download.gna.org/qemulaunch/debian/)
Note: In the "Other" tab add "-kernel-kqemu" (no quotes) to the "Additional Arguments" field.

**If you are experiencing the Transparent Window bug (By running XGL...) check out Saad's thread ([http://ubuntuforums.org/showthread.php?t=187941](http://ubuntuforums.org/showthread.php?t=187941)) for instructions on how to fix it.**

Andrew, :D[/QUOTE]

I got an error:

Extracting QEMU...
tar: qemu-snapshot-2006-06-04_23.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ERROR: Unable to extract QEMU.

---

### Post by OldGaf on 2006-06-05
[QUOTE=andrejkw]Hey Guys,

This is more of a Automatic Installation script, than a Howto.
It will only work with **Breezy** and **Dapper**.

This script will compile and install:
- **QEMU 0.8.1 or QEMU from CVS** (Choice Given during Install)
- **KQEMU 1.3.0pre7**

Included QEMU Patches (Optional - Choice Given during Install):
- **[DHCP Patch]("http://people.brandeis.edu/~jcoiner/qemu_idedma/qemu_dma_patch.html#dhcp")**
- **[Mouse Wall Bug]("http://lists.gnu.org/archive/html/qemu-devel/2006-05/msg00112.html")**

Installation Instructions:
```
wget http://exvision.net/install_qemu.sh
chmod +x ./install_qemu.sh
sudo ./install_qemu.sh
```

Afterwards just follow the on-screen instructions.

The credits go to:
- Nando Florestan (I used some parts of his Script)
- Saad N. (For inspiration and testing)

If you have any suggestions how I can improve this script, feel free to post them in here :)

Check out Qemu Launcher (a nice QEMU Gui for GNOME) at [http://download.gna.org/qemulaunch/debian/](http://download.gna.org/qemulaunch/debian/)
Note: In the "Other" tab add "-kernel-kqemu" (no quotes) to the "Additional Arguments" field.

**If you are experiencing the Transparent Window bug (By running XGL...) check out Saad's thread ([http://ubuntuforums.org/showthread.php?t=187941](http://ubuntuforums.org/showthread.php?t=187941)) for instructions on how to fix it.**

Andrew, :D[/QUOTE]

Reran the script and got this at the end:

Installing KQEMU...
ERROR: Module kqemu does not exist in /proc/modules
Loading KQEMU Module...
kqemu

---

### Post by andrejkw on 2006-06-05
You can safely ignore that error. It should work.

---

### Post by andrejkw on 2006-06-05
Alrighty, all 3 bugs fixed. :)

---

### Post by OldGaf on 2006-06-05
[QUOTE=andrejkw]Alrighty, all 3 bugs fixed. :)[/QUOTE]

When I run the following:

qemu -localtime -hda winxp.img -cdrom /dev/hda -m 512 -boot d

I get this:

Could not configure '/dev/rtc' to have a 1024 Hz timer. This is not a fatal error, but for better emulation accuracy either use a 2.6 host Linux kernel or type 'echo 1024 > /proc/sys/dev/rtc/max-user-freq' as root.

Is there a config file I need to edit?

---

### Post by OldGaf on 2006-06-05
[QUOTE=andrejkw]Alrighty, all 3 bugs fixed. :)[/QUOTE]


Cool... other then configuring a few thing (screen size etc), this is a VERY cool script...... thanks a bunch =D>

---

### Post by andrejkw on 2006-06-05
[QUOTE=OldGaf]When I run the following:

qemu -localtime -hda winxp.img -cdrom /dev/hda -m 512 -boot d

I get this:

Could not configure '/dev/rtc' to have a 1024 Hz timer. This is not a fatal error, but for better emulation accuracy either use a 2.6 host Linux kernel or type 'echo 1024 > /proc/sys/dev/rtc/max-user-freq' as root.

Is there a config file I need to edit?[/QUOTE]

Type this inside a terminal:
```
sudo su
<enter your password>
echo 1024 > /proc/sys/dev/rtc/max-user-freq
exit
```

and the error should be gone.

---

### Post by chris062689 on 2006-06-05
This sounds like a really cool script!

Too bad it doesn't work for me. ;(

chris@chris-desktop:~$ sudo ./install_qemu.sh
Your Ubuntu release is: Dapper Drake 6.06
Is this correct? yes
Would you like to download QEMU from the CVS (Unstable)? no
Installing Dependencies...
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc-3.4
ERROR: Unable to Install Dependencies.

---

### Post by andrejkw on 2006-06-05
Hmm, did you enable the extra repositories to Ubuntu?
Follow the instrutions on this site for your version of ubuntu and then try the script again: [http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

---

### Post by henriquemaia on 2006-06-05
Hi,

the install script does not work on amd64. It fails to recognize the kernel.

---

### Post by andrejkw on 2006-06-05
ok, I will take a look into it. Could you please type the following two commands, and post the output? thanks :)

```

uname -r

```
```

uname -m

```

---

### Post by henriquemaia on 2006-06-05
[quote=andrejkw]ok, I will take a look into it. Could you please type the following two commands, and post the output? thanks :)

```

uname -r

``` ```

uname -m

```[/quote] 
Here you go:

-r
2.6.15-23-amd64-k8

-m
x86_64

---

### Post by chris062689 on 2006-06-05
Thanks alot.  It's working great!

---

### Post by chris062689 on 2006-06-05
KQEMU Error!
Configuring KQEMU...
No Makefile file present in /lib/modules/2.6.15-23-386/build/ - kqemu cannot be built
grep: /lib/modules/2.6.15-23-386/build//Makefile: No such file or directory
Source path       /tmp/build-qemu/qemu-snapshot-2006-06-05_23/kqemu
C compiler        gcc
Host C compiler   gcc
make              make
host CPU          i386
Compiling KQEMU...
make -C /lib/modules/2.6.15-23-386/build/ M=`pwd` modules
make: *** /lib/modules/2.6.15-23-386/build/: No such file or directory.  Stop.
make: *** [kqemu.ko] Error 2
ERROR: Unable to Compile KQEMU...


How am I able to start QEMU / Set it up after QEMU installs?

---

### Post by andrejkw on 2006-06-05
Hmm.. that doesn't look really great ^^

I just re-uploaded a new version which includes better kernel detection and added support for AMD64. Hopefully that'll do it.

Just delete the current .sh file, and follow the instructions in my post again to download and run the latest version of the script.

```
rm install_qemu.sh
```

---

### Post by Toxicity999 on 2006-06-05
[quote=OldGaf]I got an error:

Extracting QEMU...
tar: qemu-snapshot-2006-06-04_23.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ERROR: Unable to extract QEMU.[/quote]

they don't archive old snapshots apparently so update 2006-06-04_23 to 2006-06-05_23 and tomorrow 2006-06-06_23 I would assume if you don't get around to it tonight. Sorry if someone else answered this I didn't get a chance to read all posts.

---

### Post by andrejkw on 2006-06-05
[QUOTE=Toxicity999]they don't archive old snapshots apparently so update 2006-06-04_23 to 2006-06-05_23 and tomorrow 2006-06-06_23 I would assume if you don't get around to it tonight. Sorry if someone else answered this I didn't get a chance to read all posts.[/QUOTE]

It is fixed in the new version. Remove the current .sh file, and follow the instructions in the post again :)

---

### Post by andrejkw on 2006-06-05
Added a basic tutorial on how to use QEMU to the main post. :cool:

---

### Post by henriquemaia on 2006-06-05
[quote=andrejkw]Hmm.. that doesn't look really great ^^

I just re-uploaded a new version which includes better kernel detection and added support for AMD64. Hopefully that'll do it.

Just delete the current .sh file, and follow the instructions in my post again to download and run the latest version of the script.

```
rm install_qemu.sh
```[/quote] 


Ok, now it runs great. Thanks a lot!

Just a question: when I run qemu with the option -kernel-kqemu, with gives me the following error:

qemu: invalid option -- '-kernel-kqemu'

Any ideas why?

---

### Post by andrejkw on 2006-06-05
[QUOTE=henriquemaia]Ok, now it runs great. Thanks a lot!

Just a question: when I run qemu with the option -kernel-kqemu, with gives me the following error:

qemu: invalid option -- '-kernel-kqemu'

Any ideas why?[/QUOTE]

Hmm, did the script finish running successfully? It looks like the KQEMU support is not compiled. Can you tell me which version of Ubuntu you are using?

---

### Post by henriquemaia on 2006-06-05
[quote=andrejkw]Hmm, did the script finish running successfully? It looks like the KQEMU support is not compiled. Can you tell me which version of Ubuntu you are using?[/quote]

Dapper 64bit:

Distributor ID: Ubuntu
Description:    Ubuntu 6.06 LTS
Release:        6.06
Codename:       dapper

2.6.15-23-amd64-k8 kernel

---

### Post by andrejkw on 2006-06-05
[QUOTE=henriquemaia]Dapper 64bit:

Distributor ID: Ubuntu
Description:    Ubuntu 6.06 LTS
Release:        6.06
Codename:       dapper

2.6.15-23-amd64-k8 kernel[/QUOTE]

Did you let the the compilation script finish before running QEMU?

---

### Post by henriquemaia on 2006-06-05
[quote=andrejkw]Did you let the the compilation script finish before running QEMU?[/quote] 
Everything went ok first time. I have runned the script again, since I change some default configurations for checkinstall and the result was:

Installing KQEMU...
Loading KQEMU Module...

Congratulations! QEMU and KQEMU has been successfully Installed!
Do not forget to run QEMU with the '-kernel-kqemu' parameter!
For more information visit: [http://fabrice.bellard.free.fr/qemu]("http://fabrice.bellard.free.fr/qemu")
Thank you for using this script!


No errors whasoever. But loading qemu with -kernel-kqemu still gives the same error output.

---

### Post by andrejkw on 2006-06-05
[QUOTE=henriquemaia]Everything went ok first time. I have runned the script again, since I change some default configurations for checkinstall and the result was:

Installing KQEMU...
Loading KQEMU Module...

Congratulations! QEMU and KQEMU has been successfully Installed!
Do not forget to run QEMU with the '-kernel-kqemu' parameter!
For more information visit: [http://fabrice.bellard.free.fr/qemu]("http://fabrice.bellard.free.fr/qemu")
Thank you for using this script!


No errors whasoever. But loading qemu with -kernel-kqemu still gives the same error output.[/QUOTE]


Hmm, can you tell em what exactly did you change in checkinstall?

---

### Post by chris062689 on 2006-06-05
chris@chris-desktop:~$ qemu-img create windows.img 10G
bash: qemu-img: command not found

It said it installed everything fine, except KQemu, which never seems to work for me.

---

### Post by henriquemaia on 2006-06-05
[quote=andrejkw]Hmm, can you tell em what exactly did you change in checkinstall?[/quote]

I Just adjusted the architecture, since the packages X86_64 fail to install for some unknown reason to me. I just put there amd64 and checkinstall finishes ok.

This is weird, since the module is present and loaded.

lsmod gives me:

Module                  Size  Used by
kqemu                 166920  0

---

### Post by andrejkw on 2006-06-05
[QUOTE=henriquemaia]I Just adjusted the architecture, since the packages X86_64 fail to install for some unknown reason to me. I just put there amd64 and checkinstall finishes ok.

This is weird, since the module is present and loaded.

lsmod gives me:

Module                  Size  Used by
kqemu                 166920  0[/QUOTE]

Hmm, try searching for all packages name qemu in synaptic, and remove them, then re-run the script, and tell me your results.

---

### Post by andrejkw on 2006-06-06
[QUOTE=henriquemaia]I Just adjusted the architecture, since the packages X86_64 fail to install for some unknown reason to me. I just put there amd64 and checkinstall finishes ok.

This is weird, since the module is present and loaded.

lsmod gives me:

Module                  Size  Used by
kqemu                 166920  0[/QUOTE]

Also, what do you mean by "I Just adjusted the architecture, since the packages X86_64 fail to install for some unknown reason to me. I just put there amd64", can you tell me what you adjusted or show me? So I can include this into the script, so other 64bit users don't ahve this problem? :D

---

### Post by henriquemaia on 2006-06-06
[quote=andrejkw]Hmm, try searching for all packages name qemu in synaptic, and remove them, then re-run the script, and tell me your results.[/quote] 
Thanks for all you replies. I did that, runned the script, no errors, still the same output in qemu. Maybe a fault of 64bit system, or of my system. It would be good to look at the results of another 64bit user.

ps: qemu works great, I just don't have acceleration.

---

### Post by andrejkw on 2006-06-06
[QUOTE=henriquemaia]Thanks for all you replies. I did that, runned the script, no errors, still the same output in qemu. Maybe a fault of 64bit system, or of my system. It would be good to look at the results of another 64bit user.

ps: qemu works great, I just don't have acceleration.[/QUOTE]

Can you tell me what exactly you edited in checkinstall, maybe post in here?

---

### Post by henriquemaia on 2006-06-06
[quote=andrejkw]Can you tell me what exactly you edited in checkinstall, maybe post in here?[/quote]

This:

# Default architecture type (Leave it empty to allow auto-guessing)
ARCHITECTURE="amd64"

the default is:

# Default architecture type (Leave it empty to allow auto-guessing)
ARCHITECTURE=""

---

### Post by FredB on 2006-06-06
Thanks for the script. I will try it as soon as possible ;)

---

### Post by Hellz on 2006-06-06
Hi,

I want to download this script, but web server doesn't work - I see connection timeout message. Can you check this?

---

### Post by izkuru on 2006-06-06
Hey, thanks for the script! It worked great. ;)

Well... I did have one snag, but I was able to fix it. Since I have the *-amd64-generic* kernel installed, I recieved this error upon running the script:
```

Unable to find appropriate Kernel Headers for your Kernel.

```
After looking through the script, I located where it detects your kernel and then downloads the appropriate headers, and noticed that it does not check to see if this kernel is installed. I just added the proper information for my kernel, and the script worked fine afterwords.
```

## DETECT KERNEL -- DOWNLOAD PROPER HEADERS ##
KERNEL386=`uname -r | grep "\-386$"`
KERNEL686=`uname -r | grep "\-686$"`
KERNEL686SMP=`uname -r | grep "\-686-smp$"`
KERNELK7=`uname -r | grep "\-k7$"`
KERNELK7SMP=`uname -r | grep "\-k7-smp$"`
KERNELAMD64K8=`uname -r | grep "\-amd64-k8$"`
KERNELAMD64K8SMP=`uname -r | grep "\-amd64-k8-smp$"`
**KERNELAMD64GENERIC=`uname -r | grep "\-amd64-generic$"`**

if [ "$KERNEL386" != "" ]; then
  	cecho "blue" "Installing Kernel Headers (386)..."
 	apt-get -y --force-yes install linux-headers-386 || error "Unable to Install Kernel Headers."
elif [ "$KERNEL686" != "" ]; then
	cecho "blue" "Installing Kernel Headers (686)..."
	apt-get -y --force-yes install linux-headers-686 || error "Unable to Install Kernel Headers."
elif [ "$KERNEL686SMP" != "" ]; then
	cecho "blue" "Installing Kernel Headers (686-SMP)..."
	apt-get -y --force-yes install linux-headers-686-smp || error "Unable to Install Kernel Headers."
elif [ "$KERNELK7" != "" ]; then
	cecho "blue" "Installing Kernel Headers (K7)..."
	apt-get -y --force-yes install linux-headers-k7 || error "Unable to Install Kernel Headers."
elif [ "$KERNELK7SMP" != "" ]; then
	cecho "blue" "Installing Kernel Headers (K7-SMP)..."
	apt-get -y --force-yes install linux-headers-k7-smp || error "Unable to Install Kernel Headers."
elif [ "$KERNELAMD64K8" != "" ]; then
	cecho "blue" "Installing Kernel Headers (AMD64 K8)..."
	apt-get -y --force-yes install linux-headers-amd64-k8 || error "Unable to Install Kernel Headers."
elif [ "$KERNELAMD64K8SMP" != "" ]; then
	cecho "blue" "Installing Kernel Headers (AMD64 K8-SMP)..."
	apt-get -y --force-yes install linux-headers-amd64-k8-smp || error "Unable to Install Kernel Headers."
[B]elif [ "$KERNELAMD64GENERIC" != "" ]; then
	cecho "blue" "Installing Kernel Headers (AMD64 GENERIC)..."
	apt-get -y --force-yes install linux-headers-amd64-generic || error "Unable to Install Kernel Headers."[/B]
else
	error "Unable to find appropriate Kernel Headers for your Kernel."
fi
```

---

### Post by andrejkw on 2006-06-06
> **izkuru]Hey, thanks for the script! It worked great.  said:**
> ; then
  	cecho "blue" "Installing Kernel Headers (386)..."
 	apt-get -y --force-yes install linux-headers-386 || error "Unable to Install Kernel Headers."
elif [ "$KERNEL686" != "" ]; then
	cecho "blue" "Installing Kernel Headers (686)..."
	apt-get -y --force-yes install linux-headers-686 || error "Unable to Install Kernel Headers."
elif [ "$KERNEL686SMP" != "" ]; then
	cecho "blue" "Installing Kernel Headers (686-SMP)..."
	apt-get -y --force-yes install linux-headers-686-smp || error "Unable to Install Kernel Headers."
elif [ "$KERNELK7" != "" ]; then
	cecho "blue" "Installing Kernel Headers (K7)..."
	apt-get -y --force-yes install linux-headers-k7 || error "Unable to Install Kernel Headers."
elif [ "$KERNELK7SMP" != "" ]; then
	cecho "blue" "Installing Kernel Headers (K7-SMP)..."
	apt-get -y --force-yes install linux-headers-k7-smp || error "Unable to Install Kernel Headers."
elif [ "$KERNELAMD64K8" != "" ]; then
	cecho "blue" "Installing Kernel Headers (AMD64 K8)..."
	apt-get -y --force-yes install linux-headers-amd64-k8 || error "Unable to Install Kernel Headers."
elif [ "$KERNELAMD64K8SMP" != "" ]; then
	cecho "blue" "Installing Kernel Headers (AMD64 K8-SMP)..."
	apt-get -y --force-yes install linux-headers-amd64-k8-smp || error "Unable to Install Kernel Headers."
[B]elif [ "$KERNELAMD64GENERIC" != "" ]; then
	cecho "blue" "Installing Kernel Headers (AMD64 GENERIC)..."
	apt-get -y --force-yes install linux-headers-amd64-generic || error "Unable to Install Kernel Headers."[/B]
else
	error "Unable to find appropriate Kernel Headers for your Kernel."
fi
```

Ok thanks! I will be sure to include that Kernel in the script. :)

---

### Post by izkuru on 2006-06-06
Oh, one more thing. I didn't discover this until I actually tried to use qemu, but if you are using a 64bit system, you need to use qemu-system-x86_64, otherwise the -kernel-kqemu option does not work. (you get the error message "qemu: invalid option -- '-kernel-kqemu'").

so, for a 64bit system, the command to run qemu would be, for example:
```

qemu-system-x86_64 -localtime -hda guest.img -cdrom /home/andrejkw/XPCD.iso -boot d -kernel-kqemu -m 512M
```
instead of
```

qemu -localtime -hda guest.img -cdrom /home/andrejkw/XPCD.iso -boot d -kernel-kqemu -m 512M
```

You can read it for yourself at the kqemu documentation over [here](http://fabrice.bellard.free.fr/qemu/kqemu-doc.html#TOC7).

---

### Post by andrejkw on 2006-06-07
[QUOTE=izkuru]Oh, one more thing. I didn't discover this until I actually tried to use qemu, but if you are using a 64bit system, you need to use qemu-system-x86_64, otherwise the -kernel-kqemu option does not work. (you get the error message "qemu: invalid option -- '-kernel-kqemu'").

so, for a 64bit system, the command to run qemu would be, for example:
```

qemu-system-x86_64 -localtime -hda guest.img -cdrom /home/andrejkw/XPCD.iso -boot d -kernel-kqemu -m 512M
```
instead of
```

qemu -localtime -hda guest.img -cdrom /home/andrejkw/XPCD.iso -boot d -kernel-kqemu -m 512M
```

You can read it for yourself at the kqemu documentation over [here](http://fabrice.bellard.free.fr/qemu/kqemu-doc.html#TOC7).[/QUOTE]

Ok, thanks again :) I put up a note in the first post.

---

### Post by henriquemaia on 2006-06-07
[quote=izkuru]Oh, one more thing. I didn't discover this until I actually tried to use qemu, but if you are using a 64bit system, you need to use qemu-system-x86_64, otherwise the -kernel-kqemu option does not work. (you get the error message "qemu: invalid option -- '-kernel-kqemu'").

so, for a 64bit system, the command to run qemu would be, for example:
```

qemu-system-x86_64 -localtime -hda guest.img -cdrom /home/andrejkw/XPCD.iso -boot d -kernel-kqemu -m 512M
``` instead of
```

qemu -localtime -hda guest.img -cdrom /home/andrejkw/XPCD.iso -boot d -kernel-kqemu -m 512M
``` 
You can read it for yourself at the kqemu documentation over [here]("http://fabrice.bellard.free.fr/qemu/kqemu-doc.html#TOC7").[/quote] 
Thanks, izkuru, for posting this solution. 

Thank you andrejkw for this install script!

Now I have qemu working fast. It's great :)

---

### Post by TradeMark on 2006-06-07
For those having random errors within QEMU, you might like to try disabling the KQEMU acceleration component temporarily with the **-no-kqemu** switch. Solved the problem I was getting with a random STOP screen in Win2K installation.

---

### Post by thatha on 2006-06-07
Hey Andrew!

Well done, awesome script... It would've saved me half an hour if I searched the forums before trying to do it myself. And just a note, out of curiosity: Wouldn't "apt-get -y --force-yes install linux-headers-`uname -r` || ... " instead of all the ifs work as well?

Thanks again,

Theocharis "Ian".

---

### Post by andrejkw on 2006-06-07
[QUOTE=thatha]Hey Andrew!

Well done, awesome script... It would've saved me half an hour if I searched the forums before trying to do it myself. And just a note, out of curiosity: Wouldn't "apt-get -y --force-yes install linux-headers-`uname -r` || ... " instead of all the ifs work as well?

Thanks again,

Theocharis "Ian".[/QUOTE]

Yes, it would :) Thanks for this great suggestion, but I want the user to know what kind of kernel is being installed though.

---

### Post by izkuru on 2006-06-07
[QUOTE=henriquemaia]Thanks, izkuru, for posting this solution.[/QUOTE]
No problem, glad I was able to help someone other than myself =)

---

### Post by hill on 2006-06-07
When i try to run qemu with the "-kernel-kqemu" option i get "Could not open '/dev/kqemu' - QEMU acceleration layer not activated"

---

### Post by henriquemaia on 2006-06-08
[quote=hill]When i try to run qemu with the "-kernel-kqemu" option i get "Could not open '/dev/kqemu' - QEMU acceleration layer not activated"[/quote] 
that happens to me also. To make it work I have to run:

```
sudo mknod /dev/kqemu c 250 0
sudo chmod 666 /dev/kqemu
``` 
Commands which I took from the install script. Don't know why is this.

---

### Post by hill on 2006-06-08
Thanks, works fine now.

---

### Post by henriquemaia on 2006-06-08
[quote=hill]Thanks, works fine now.[/quote]

You have to check after a reboot if it still works. If it doesn't, you'll have to run those commands again.

---

### Post by Ribs on 2006-06-08
Hi,

on 64-bit systems, there is a problem with the script. I believe this has been brought up before.

Basically, the script builds the .deb package as follows:
This package will be built according to these values:

0 -  Maintainer: [ root@localhost ]
1 -  Summary: [ QEMU is a generic and open source processor emulator which achieves a good emulation speed by using dynamic translation. Visit [http://fabrice.bellard.free.fr/qemu](http://fabrice.bellard.free.fr/qemu) ]
2 -  Name:    [ qemu ]
3 -  Version: [ 0.8.1 ]
4 -  Release: [ 1 ]
5 -  License: [ Restricted ]
6 -  Group:   [ Miscellaneous - Text Based ]
7 -  Architecture: [ x86_64 ]
8 -  Source location: [ [http://fabrice.bellard.free.fr/qemu/qemu-0.8.1.tar.gz](http://fabrice.bellard.free.fr/qemu/qemu-0.8.1.tar.gz) ]
9 -  Alternate source location: [  ]

Point 7 should be "amd64", not "x86_64". Building the script as "x86_64" confuses the package system, as it sees the system as "amd64", and therefore fails to install the package.

There are two ways to fix this. Either force dpkg to install the package anyway, or fix the script so it builds for the correct arch.

I've taken the cowards way out, and made the script force dpkg to accept the arch which is given to it. I've attached a patch to this message which should patch against the script to fix this issue. Be warned, this is a dirty hack, and a 'proper' solution is better, but there is no risk of using this patch. Feel free to add it to your script properly so 64-bit users can enjoy it's eternal goodness.

Regards,
Ribs.

---

### Post by henriquemaia on 2006-06-08
[quote=Ribs]Hi,

on 64-bit systems, there is a problem with the script. I believe this has been brought up before.

Basically, the script builds the .deb package as follows:
This package will be built according to these values:

0 -  Maintainer: [ root@localhost ]
1 -  Summary: [ QEMU is a generic and open source processor emulator which achieves a good emulation speed by using dynamic translation. Visit [http://fabrice.bellard.free.fr/qemu]("http://fabrice.bellard.free.fr/qemu") ]
2 -  Name:    [ qemu ]
3 -  Version: [ 0.8.1 ]
4 -  Release: [ 1 ]
5 -  License: [ Restricted ]
6 -  Group:   [ Miscellaneous - Text Based ]
7 -  Architecture: [ x86_64 ]
8 -  Source location: [ [http://fabrice.bellard.free.fr/qemu/qemu-0.8.1.tar.gz]("http://fabrice.bellard.free.fr/qemu/qemu-0.8.1.tar.gz") ]
9 -  Alternate source location: [  ]

Point 7 should be "amd64", not "x86_64". Building the script as "x86_64" confuses the package system, as it sees the system as "amd64", and therefore fails to install the package.

There are two ways to fix this. Either force dpkg to install the package anyway, or fix the script so it builds for the correct arch.

I've taken the cowards way out, and made the script force dpkg to accept the arch which is given to it. I've attached a patch to this message which should patch against the script to fix this issue. Be warned, this is a dirty hack, and a 'proper' solution is better, but there is no risk of using this patch. Feel free to add it to your script properly so 64-bit users can enjoy it's eternal goodness.

Regards,
Ribs.[/quote]

Or you can edit your /etc/checkinstall and put your architecture as amd64, as I did. 

# Default architecture type (Leave it empty to allow auto-guessing)
ARCHITECTURE="amd64"

This way the script works ok without changes.

---

### Post by Ribs on 2006-06-08
[QUOTE=henriquemaia]Or you can edit your /etc/checkinstall and put your architecture as amd64, as I did. 

# Default architecture type (Leave it empty to allow auto-guessing)
ARCHITECTURE="amd64"

This way the script works ok without changes.[/QUOTE]This is true. But if the author edit's his script, then users don't need to edit their system's, and can just run the script 8-)

---

### Post by henriquemaia on 2006-06-08
[quote=Ribs]This is true. But if the author edit's his script, then users don't need to edit their system's, and can just run the script 8-)[/quote] 
I guess you're right, since if an amd64 user is not aware of how checkinstall works, the  script will still work fine for him/her. 


As a side note: for those who use checkisntall a lot on an amd64, it's better to edit your /etc/checkinstall, so that you don't have to edit option 7 (architecture) by hand.

---

### Post by andrejkw on 2006-06-08
Alright, thanks everyone for your suggestions :) I have fixed the checkinstall problem for amd64 now. Hopefully this is the last thing to get fixed :)

---

### Post by 23meg on 2006-06-08
On my custom kernel I get the following error ```
"ERROR: Unable to find appropriate Kernel Headers for your Kernel."
```
It's a kernel I compiled from the stock Dapper kernel source, with a user undervolting patch. ```
$ uname -r
2.6.15.7-ubuntu1-uservcore

```
How should I point the location of my kernel headers to the script?

---

### Post by barmaley on 2006-06-14
Hallo, people
First of all, thank you for the script, nice work. Installation worked like a charm, but :sad: 
I have a win2k image created with previous qemu version (0.8.0) and in Breezy. I was trying to run it with the folllowing command:
qemu -localtime -hda win2k.img -boot c -kernel-kqemu -m 512M

it started the windows, but then it stops and I have the usual windows problem. The screenshot is attached.
If you know how to solve this problem, I will be grateful. It's a pity to loose the data I have in that win image.

---

### Post by midorigin on 2006-06-14
[QUOTE=TradeMark]For those having random errors within QEMU, you might like to try disabling the KQEMU acceleration component temporarily with the **-no-kqemu** switch. Solved the problem I was getting with a random STOP screen in Win2K installation.[/QUOTE]

Works charms. But when can I safely start using KQEMU again?

---

### Post by Scunizi on 2006-06-14
Although I didn't run the script, I did install from the repositories without kqemu.  I just wanted to play around a little.  I've created an wins.img of 5g and now would like to install either win95 or xp.  I have valid cd's of both.  Yet I'm confused if I need to create an ISO of the cd's or can I run the install directly off the cd's ( if so how "command line help please!" ).  If I need to create an ISO on the HD, how do I go about doing that.  Gnomebaker and K3d don't seem to have options to make an ISO without burning it on a cd.

---

### Post by barmaley on 2006-06-15
Since no-one answered my post, I re-phrase the question.
Is it possible to run with QEMU-0.8.1 a windows image which was created by previous version of QEMU-0.8.0?
May be I have to create a new windows image each time I update the QEMU?
Please, help.

---

### Post by midorigin on 2006-06-15
[QUOTE=Scunizi]Although I didn't run the script, I did install from the repositories without kqemu.  I just wanted to play around a little.  I've created an wins.img of 5g and now would like to install either win95 or xp.  I have valid cd's of both.  Yet I'm confused if I need to create an ISO of the cd's or can I run the install directly off the cd's ( if so how "command line help please!" ).  If I need to create an ISO on the HD, how do I go about doing that.  Gnomebaker and K3d don't seem to have options to make an ISO without burning it on a cd.[/QUOTE]

Normally you'll install directly from the CD in your CD drive. (Option A) Some people, however, do not have an actual CD to install from, and only have an ISO file that they've downloaded. They *could* burn it to a CD and continue on like normal, but that would be a waste of a CD. If you have just an ISO file, it's easier to install straight from it (Option B), rather than taking the extra step of burning it first. You should use Option A, because you have a CD and no ISO.

**Option A:** Install from the CD in your CD drive:
```
qemu -localtime -hda wins.img **-cdrom /dev/cdrom -boot d**
```
**Option B:** Install from an ISO on your hard drive:
```
qemu -localtime -hda wins.img **-cdrom */your/cd/image/file.iso* -boot d**
```
If you're curious, which you should be, "[FONT="Courier New"]-cdrom *XXXX*[/FONT]" tells it what to use as the CD, and "[FONT="Courier New"]-boot d[/FONT]" tells it to boot from the CD drive, drive *D:*.

---

### Post by barmaley on 2006-06-15
sorry, guys

---

### Post by barmaley on 2006-06-15
oops

---

### Post by barmaley on 2006-06-15
one more double post, my apologies

---

### Post by dignome on 2006-06-15
@barmaley

I'd expect this to work with the qemu 0.8.1 release.  Are you using CVS?  If so you could try booting with -no-acpi (although the Windows guests don't seem to care about acpi unless installed with it).  Also, booting with -no-kqemu would show whether there is a problem with the emulation or some problem with the proprietary kqemu module.


The mouse wall bug was recently fixed in CVS.  Just a heads up (June 14th commit).

---

### Post by barmaley on 2006-06-15
Thank you for your help.
I don't use CVS.
Booting with -no-kqemu resulted in the same problem, window shows an error  and hangs off. Perhaps, it is a problem of emulation, as you said.
If someone has any idea, please help, I don't know what to do and don't want to loose my data.

---

### Post by Scunizi on 2006-06-15
Thanks midorigin!  Those command lines are similar to what I was running and getting errors with.  I finally flashed on an idea late last night. I typically run two monitors (xinerama) and had to disable that function back to a standard xorg.conf file before anything would load like it was suppose to.  I also discovered that my xp & 95 cd's are "upgrades" and are not directly bootable because of a lack of sys files on them. I ended up loading W2Kpro but now it doesn't recognize the user name and password I set up.  

Eventually I'd like to be able to load the drivers for my scanner (usb) since it IS recognized by Ubuntu but has no drivers for Linux available in Ubuntu or on any of the sites I've been cruzing.  I know I've got to do something special in the command line to get usb functioning.  Suggestions?

---

### Post by Scunizi on 2006-06-15
Sorry for the double post.  Is there a way I can make an bootable ISO from a non bootable install cd?

---

### Post by cleverselfreferentialname on 2006-06-17
Hello. Everything compiles fine on my P4 machine with a i686 kernel. uname -r reports the following: '2.6.15-25-686'. However, a little later, it prints

```
FATAL: Error inserting kqemu (/lib/modules/2.6.15-25-686/misc/kqemu.ko): Invalid module format
ERROR: Unable to Load KQEMU Module...

```

The following thread:[http://qemu.dad-answers.com/viewtopic.php?t=1449&sid=ca81d5cd07ea5955712076dda6eb0803](http://qemu.dad-answers.com/viewtopic.php?t=1449&sid=ca81d5cd07ea5955712076dda6eb0803) says that "If you have changed your kernel recently, you must adjust the config (or maybe just rerun it) so that the correct set of kernel header-files are used." Since I did recently switch to the i686 kernel, how might I do that?

Also, this apparently happens when a module is compiled with a version of gcc different than that of the kernel. The new i686 kernels might be compiled with a different version than you guys have, which would explain it.

dmesg reports the following 
```

[17183014.752000] kqemu: version magic '2.6.15-25-686 SMP preempt 686 gcc-3.4' should be '2.6.15-25-686 SMP preempt 686 gcc-4.0'
```

Does this mean that I need to recompile the kernel with gcc 4.0?

---

### Post by th3t1nm4n on 2006-06-18
How do I force a certain date/time to the BIOS that qemu uses? Such as the year 1997.

---

### Post by HoptownJoel on 2006-06-19
Hey everybody.

I was going to try this script, but it looks like it has been (re)moved from [http://exvision.net/install_qemu.sh](http://exvision.net/install_qemu.sh). New address? Mirrors?

Thanks.

jb

---

### Post by giuliastro on 2006-06-19
Great job!
But since Qemu is already in Dapper repository (0.8.0), but it is not compiled to support KQemu, the best thing to do would be update the repository with 0.8.1 / kqemu support.
This would have great advantages over an install script:

- Installing qemu would still be a matter of apt-getting it
- Installing kqemu would still be a matter of downloading the tar ball from qemu's site BUT no compiling tools needed (to install kqemu you need no dev libraries / tools)

I believe it would be better to distribute a 0.8.1 deb + link to kqemu instead of a script.

---

### Post by jett on 2006-06-19
[QUOTE=HoptownJoel]Hey everybody.

I was going to try this script, but it looks like it has been (re)moved from [http://exvision.net/install_qemu.sh](http://exvision.net/install_qemu.sh). New address? Mirrors?

Thanks.

jb[/QUOTE]

I also can't find the script. Searched for it but couldn't find anything. Been trying several scripts but they don't work on my machine.

---

### Post by dog on 2006-06-20
I have a saved version of the script, but when I run it and answer yes to installing the Mouse Wall patch, it bombs because that has been moved from the exvision site also.

---

### Post by jett on 2006-06-20
I finally got it to work (well to the point where I can load kqemu). Just downloaded the qemu and kqemu sources from the website and built from source. Had to build qemu 0.8.1 using gcc 3.4 and kqemu using gcc 4.0.

My only problem now is that when XP and 2k setup reaches phase 2 of the install process, I get a BSOD with a PAGE_FAULT error.

I'm doing this on an old Dell Inspiron 8100. A friend of was able to build from source and run on his Thinkpad T30.

---

### Post by andb on 2006-06-20
The link to the script, [http://exvision.net/install_qemu.sh](http://exvision.net/install_qemu.sh), is down with a 404 error... Could someone please post the script here or upload it to a stable location? Im paticularly interested in the mouse issue as Im using qemu for old windows games. Would be far better if the ubuntu package was up-to-par. As I remember it had no ALSA or Kqemu support compiled in. ??? Wish I knew why. I think this is a big issue for most users.

---

### Post by dignome on 2006-06-20
@Jett:

Don't use -kernel-kqemu to install win2k/xp.  It has been known not to work for installation.

Attached is the script from 06/08.  Someone probably has something newer they can post.

---

### Post by cronholio on 2006-06-20
```
$ wget http://exvision.net/install_qemu.sh
--16:28:15--  http://exvision.net/install_qemu.sh
           => `install_qemu.sh'
Resolving exvision.net... 12.19.116.172
Connecting to exvision.net|12.19.116.172|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:28:16 ERROR 404: Not Found.

```

:(

**EDIT:** I just saw the gz file. Sorry for bumping.

---

### Post by andrejkw on 2006-06-20
Ok, sorry about that guys!

Links updated!
Also removed Mouse patch for CVS version, since it is now included in the CVS!

:)

---

### Post by giuliastro on 2006-06-21
I noticed the script creates deb packages with checkinstall. Can anybody post them here? Thanks in advance.

---

### Post by exibeo on 2006-06-21
Can someone please post the body of this shell script to this forum?  I've been trying to download the script from the URL in the first message of this thread, but I haven't been able to get it.

I just keep getting connection timeouts.

I've built both qemu and kqemu a number of times before, but this is the first time I've had a problem. 

The farthest of gotten was a build of both packages without errors, but when I try to modprobe kqemu I get the following:

FATAL: Error inserting kqemu (/lib/modules/2.6.15-25-686/misc/kqemu.ko): Invalid module format

I've tried a number of different combos:

Building qemu and kqemu with gcc-3.4
Building qemu with 3.4 and kqemu with 4.0
Building with linux headers only
Building with linux headers and source

It just doesn't seem to work.  If anyone's got an up-to-date copy of the script, I'd love to see it.

Thanks
X

---

### Post by cronholio on 2006-06-22
It's also here: [http://www.ubuntuforums.org/attachment.php?attachmentid=11493&d=1150795992](http://www.ubuntuforums.org/attachment.php?attachmentid=11493&d=1150795992)

---

### Post by exibeo on 2006-06-22
Thanks for the link...but I'm about ready to give up on this.  The script doesn't yield any better results.  I still get the invalid format error when it tries to load the kqemu module.

Ubuntu rocks...but not being able to build kqemu totally sucks.  I've never had a problem getting it to work on other platforms.

Can anyone give me a clue as to what this error message means?

FATAL: Error inserting kqemu (/lib/modules/2.6.15-25-686/misc/kqemu.ko): Invalid module format

X

---

### Post by exibeo on 2006-06-22
I've noticed some odd things about the packages I have installed.

Here are the results of a uname -a:

Linux hostname 2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686 GNU/Linux

It shows kernel version 2.16.15-25, but Synaptic tells me my installed kernel version is 2.16.15.23.

My linux-headers-686 package also indicates version 2.16.15.23 (in Synaptic) but was accompanied by the installation of linux-headers-2.6.15-25-686 and linux-headers-2.6.15-25.

This seems like a funky combination of 2.6.15.23 and 2.6.15.25.

Any advice?
X

---

### Post by exibeo on 2006-06-22
I figured it out...dmesg was showing the following each time kqemu failed to load:

kqemu: version magic '2.6.15-23-686 SMP preempt 686 gcc-3.4' should be '2.6.15-25-686 SMP preempt 686 gcc-4.0'

As it turned out...one qemu install script I tried to run created a link that made my default gcc-3.4.  I removed the link, and relinked my /usr/src/linux directory to point to the linux-source-2.6.15 directory (previous attempts linked to linux-headers-2.6.15-25 or linux-headers-2.6.15-25-686.

So in a nutshell, it looks like the following setup will work:

gcc 4.0 (for kqemu)
gcc 3.4 (for qemu)
latest linux-686 kernel
and Linux source 2.6.15-23.39

Hope that helps others.

---

### Post by tinti on 2006-06-22
Someone can help me???
What can I do?
```
Compiling KQEMU...
make -C /lib/modules/2.6.15-23-386/build/ M=`pwd` modules
make: *** /lib/modules/2.6.15-23-386/build/: Arquivo ou diretório não encontrado.  Pare.
make: ** [kqemu.ko] Erro 2
ERROR: Unable to Compile KQEMU...

```

--------------------


```
tinti@hexorx86:~/Documentos/Downloads$ uname -m
i686
tinti@hexorx86:~/Documentos/Downloads$ uname -r
2.6.15-23-386
tinti@hexorx86:~/Documentos/Downloads$ uname -a
Linux hexorx86 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
tinti@hexorx86:~/Documentos/Downloads$     
```

---

### Post by tinti on 2006-06-22
If in your dapper the kqemu works, can you sent to me your install.sh 
exibeo

my mail is [email]vtintipo@gmail.com[/email]
or [email]vtintipo@coltec.ufmg.br[/email]

Thanks

"The box said: Requires MS Windows or better, so I instaled Linux"

---

### Post by andrejkw on 2006-06-22
Ok, sorry guys :\ Having hosting problems. Should be ok now ;)

---

### Post by tinti on 2006-06-24
I don't know how but I've just make it with kqemu-1.3.0pre8.tar.gz
$./configure
$make 
#make install 
And all works!!!
Before I use de script:
install_qemu.sh
I'have some problems with it.

:)

---

### Post by FredB on 2006-06-24
I installed Qemu 0.8.1 + Kqemu using latest version of the script, and it works flawlessly.

---

### Post by bhamail on 2006-06-25
Using dapper, I ran the script (on an amd64) and had to following error:
```

Packaging and Installing QEMU...

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.

checkinstall: unrecognized option `--pkg-arch=amd64'

Use --help or -h to get more information

Installing KQEMU...
Loading KQEMU Module...

Congratulations! QEMU and KQEMU has been successfully Installed!
Do not forget to run QEMU with the '-kernel-kqemu' parameter!
For more information visit: http://fabrice.bellard.free.fr/qemu
Thank you for using this script!

```

I then changed line 256 in isntall_qemu.sh from:

```
		checkinstall -y --pkg-arch=amd64 --pkgname=qemu --pkgversion=${QEMU} --pkgrelease=1 --pkglicense=Restricted --pkggroup="Miscellaneous - Text Based" --pkgsource=${BASE_URL}/qemu-${QEMU}.tar.gz --exclude=kqemu/install.sh

```

to:

```
		checkinstall -y --arch=amd64 --pkgname=qemu --pkgversion=${QEMU} --pkgrelease=1 --pkglicense=Restricted --pkggroup="Miscellaneous - Text Based" --pkgsource=${BASE_URL}/qemu-${QEMU}.tar.gz --exclude=kqemu/install.sh

```

Just changed --pkg-arch to --arch. Odd, since the man page for checkinstall still says the --pkg-arch param is valid....bug in man page or checkinstall?

NOTE: I couldn't apply the Mouse Wall patch since it appears you're having hosting problems again...(also had to get the script from the attachment referenced in a prior post, so I'm not sure I'm running the latest script.) Could someone post the latest script version as an attachment (if the earlier post is not up to date)? Thanks!

---

### Post by amunimanghi on 2006-06-25
I was wondering before I install this if I needed a Windows CD.

---

### Post by Cubi_X on 2006-06-26
I'm getting a timeout from wget.

---

### Post by giuliastro on 2006-06-26
If anyone is interested I can post a deb file for qemu 0.8.1.
Did anyone succeed in installing Dapper with qemu 0.8.1? I succesfully installed it but doesn't boot. :(

---

### Post by Cubi_X on 2006-06-26
Yes. I had no problems installing and running qemu 0.8.1 on Drapper. I'm having problems with modprobing qemu accelerator though.

---

### Post by andrejkw on 2006-06-26
Oh, jeez not again. Sorry about that guys.
This time I moved it to a complete different hosting, also disabled installation of Mouse Wall patch with CVS (since it is already included), and fixed the mysterious 64bit CPU checkinstall error montioned above.

Andrew,
:)

---

### Post by Cubi_X on 2006-06-27
Sorry but it's still not working:
 
Preparing for Download...
Downloading QEMU...
--15:52:54--  [http://qemu.dad-answers.com/download/qemu/qemu-snapshot-2006-06-27](http://qemu.dad-answers.com/download/qemu/qemu-snapshot-2006-06-27)
_23.tar.bz2
           => `qemu-snapshot-2006-06-27_23.tar.bz2'
Resolving qemu.dad-answers.com... 66.98.184.92
Connecting to qemu.dad-answers.com|66.98.184.92|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:52:55 ERROR 404: Not Found.

Edit: The error only occurs when trying to download from cvs. Otherwise it works!

---

### Post by ephemeron on 2006-06-27
0.8.1 on amd64 works great.  just disable -kernel-kqemu while installing XP/2000.  thanks a lot!

---

### Post by bhamail on 2006-06-28
Andrew,

Just reran the script on Dapper, amd64 and it worked nicely! Thanks for fixing the download.

Dan

---

### Post by kaveraj on 2006-06-29
[QUOTE=Cubi_X]
Connecting to qemu.dad-answers.com|66.98.184.92|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:52:55 ERROR 404: Not Found.[/QUOTE]

Had the same error. Found that the script was looking for a non-existing file:
qemu-snapshot-2006-06-[COLOR="Red"]29[/COLOR]_23.tar.bz2. But what existed under the URL was qemu-snapshot-2006-06-[COLOR="Blue"]28[/COLOR]_23.tar.bz2

I modified the install_qemu.sh as follows and everything worked fine:
#commenting out existing line and adding a new line
#CVS_QEMU=`date +%Y-%m-%d_23`
CVS_QEMU=2006-06-28_23
#based on the snapshot file name from [http://qemu.dad-answers.com/download/qemu/](http://qemu.dad-answers.com/download/qemu/)

I think the problem is in time zones. The script assumes that while it is run, a qemu snapshot will be created with the current date. But when run from certain timezones, this assumption may no longer be valid.

If this is the problem, it should be easier to fix. By the way..Other than that great job... =D>

---

### Post by zebarbu on 2006-06-29
Little question on amd64:
In my Qemu, I can: 
- boot dapper-i386 cdrom with or without kqemu
- boot dapper-amd64 cdrom WITHOUT kqemu
- boot dapper-amd64 cdrom WITH kqemu AND -smp 2

but I can NOT boot dapper-amd64 cdrom with kqemu as a mono-cpu (without the '-smp 2')...
And if I activate the "-smp 2", it is quite slow, so it is not a good choice...

Do you know how I may work around this?

---

### Post by mawahh on 2006-06-30
wget [http://exvision.net/qemu_mouse.patch](http://exvision.net/qemu_mouse.patch)

No connection to exvision.net. Where else can I get the patch?

---

### Post by bobap1950 on 2006-06-30
:cool:   I have tried this 4 or 5 times and I keep getting errors.

Is this correct? y
Would you like to download QEMU from the CVS (Unstable)? y
Installing Dependencies...
Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
g++-3.4 is already the newest version.
libsdl1.2debian is already the newest version.
libsdl1.2debian-all is already the newest version.
build-essential is already the newest version.
libsdl1.2-dev is already the newest version.
zlib1g-dev is already the newest version.
checkinstall is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Installing Kernel Headers (386)...
Reading package lists... Done
Building dependency tree... Done
linux-headers-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Preparing for Download...
Downloading QEMU...
--13:13:54--  [http://qemu.dad-answers.com/download/qemu/qemu-snapshot-2006-06-30_23.tar.bz2](http://qemu.dad-answers.com/download/qemu/qemu-snapshot-2006-06-30_23.tar.bz2)
           => `qemu-snapshot-2006-06-30_23.tar.bz2'
Resolving qemu.dad-answers.com... 66.98.184.92
Connecting to qemu.dad-answers.com|66.98.184.92|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:13:55 ERROR 404: Not Found.

Downloading KQEMU...
--13:13:55--  [http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz)
           => `kqemu-1.3.0pre9.tar.gz'
Resolving fabrice.bellard.free.fr... 212.27.63.117
Connecting to fabrice.bellard.free.fr|212.27.63.117|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 190,070 (186K) [application/x-gzip]

100%[====================================>] 190,070      103.64K/s

13:13:57 (103.35 KB/s) - `kqemu-1.3.0pre9.tar.gz' saved [190070/190070]

Extracting QEMU...
tar: qemu-snapshot-2006-06-30_23.tar.bz2: Cannot open: No such file or directorytar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ERROR: Unable to extract QEMU.

---

### Post by iJeff on 2006-07-02
[QUOTE=bobap1950]:cool:   I have tried this 4 or 5 times and I keep getting errors.

Is this correct? y
Would you like to download QEMU from the CVS (Unstable)? y

--

Extracting QEMU...
tar: qemu-snapshot-2006-06-30_23.tar.bz2: Cannot open: No such file or directorytar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ERROR: Unable to extract QEMU.[/QUOTE]

I kept getting that error until I chose not to install the CVS Unstable version. Just answer 'N' for that and it should work.

---

### Post by johlin on 2006-07-02
The CVS version doesn't work, but the other one does. However, it doesn't want to install kqemu. This is the error I get:
Installing KQEMU...
Loading KQEMU Module...
FATAL: Error inserting kqemu (/lib/modules/2.6.15-25-386/misc/kqemu.ko): Invalid module format
ERROR: Unable to Load KQEMU Module...

---

### Post by tzulberti on 2006-07-02
I am getting the following error while trying to install it:


make[1]: Leaving directory `/tmp/build-qemu/qemu-0.8.1/arm-softmmu'
Configuring KQEMU...
No Makefile file present in /lib/modules/2.6.15-23-386/build/ - kqemu cannot be built
grep: /lib/modules/2.6.15-23-386/build//Makefile: No such file or directory
Source path       /tmp/build-qemu/qemu-0.8.1/kqemu
C compiler        gcc
Host C compiler   gcc
make              make
host CPU          i386
Compiling KQEMU...
make -C /lib/modules/2.6.15-23-386/build/ M=`pwd` modules
make: *** /lib/modules/2.6.15-23-386/build/: No such file or directory.  Stop.
make: *** [kqemu.ko] Error 2
ERROR: Unable to Compile KQEMU...

---

### Post by squilla on 2006-07-03
Hi
Thanks for this great HOWTO.
I had one problem with compilng kqemu - the script seems to look for the "build" dir in the oldest /lib/modules/* directory (for me this is  - "/lib/modules/2.6.15-20-386/") and not in the latest (for me this is -  /lib/modules/2.6.15-25-386/).

The fix is to create a symbolic link to the "build" directory in the latest folder (2.6.15-25-386 in my case).

so just do (easy!)
> cd /lib/modules/2/6/15-20-386
> sudo ln -s /lib/modules/2.6.15-25-386 build

NB: Please substitute your own module directories - these were just the ones I have.
I hope this helps

Regards

---

### Post by moparfan90 on 2006-07-03
everything works fine up until kqwmu i get this:



**********************************************************************

Installing KQEMU...
Loading KQEMU Module...
FATAL: Error inserting kqemu (/lib/modules/2.6.15-25-386/misc/kqemu.ko): Invalid module format
ERROR: Unable to Load KQEMU Module...







what should i do?

---

### Post by tzulberti on 2006-07-03
Thanks squilla, that solved the problem that I was having. The script is great. Also a y/n or yes/no would be appreciated.

Thanks.

---

### Post by giuliastro on 2006-07-08
I uploaded yesterday's CVS [here]("http://www.4shared.com/dir/567222/e3c71a2d/qemu.html"), it is compiled to support KQemu.

---

### Post by qrm on 2006-07-08
hi, i installed qemu with ease following this exellent tutorial. But i cant seem to boot from any cds i have (windows ones, havent tried ubuntu yet). I have both - proffessional and home edition, i insert my cd in to the rom-drive, i mount the cd from disk mounter and still qemu cant seem to recognize that i have a bootable disk :s

EDIT: cant boot from even ubuntu cd-s. It cant be a hardware failuse because i can boot from BIOS perfeclty with livecd

---

### Post by superm1 on 2006-07-09
> **qrm said:**
> hi, i installed qemu with ease following this exellent tutorial. But i cant seem to boot from any cds i have (windows ones, havent tried ubuntu yet). I have both - proffessional and home edition, i insert my cd in to the rom-drive, i mount the cd from disk mounter and still qemu cant seem to recognize that i have a bootable disk :s

EDIT: cant boot from even ubuntu cd-s. It cant be a hardware failuse because i can boot from BIOS perfeclty with livecd

Make sure that when providing the -cdrom /dev/cdrom switch, you also provide -boot d

---

### Post by qrm on 2006-07-09
superm1 thanks a lot for the tip! I am installing Xp at this very same moment :D

---

### Post by qrm on 2006-07-09
I installed windows and everything seems to work but how can i change the size of the screen? If I use the ctrl+alt+f the size of windows window remains the same and everything else turns black

thanks in advance

EDIT: figured it out, had to change resolution in control panel :D

---

### Post by XAsmodeanX on 2006-07-10
I installed everything with the script and all seemed to go well but when I run the command I get the following error:

xasmodeanx@archangel:~/winxp$ qemu -localtime -hda winxp.img -boot d -kernel-kqemu -m 256M
You do not have enough space in '/dev/shm' for the 256 MB of QEMU virtual RAM.
To have more space available provided you have enough RAM and swap, do as root:
umount /dev/shm
mount -t tmpfs -o size=272m none /dev/shm


If I don't tell it to use 256 mb of memory it starts but stops at the bios screen along with giving this error in the terminal:

xasmodeanx@archangel:~/winxp$ qemu -localtime -hda winxp.img -boot d -kernel-kqemu
Could not configure '/dev/rtc' to have a 1024 Hz timer. This is not a fatal
error, but for better emulation accuracy either use a 2.6 host Linux kernel or
type 'echo 1024 > /proc/sys/dev/rtc/max-user-freq' as root.
Could not open '/dev/kqemu' - QEMU acceleration layer not activated

And the error from the bios:

CDROM boot failure code: 0003
Boot from CD-Rom failed
FATAL: Could not read the boot disk

Any help would be greatly appreciated.

---

### Post by qrm on 2006-07-10
type "sudo su", enter your password and then "echo 1024 > /proc/sys/dev/rtc/max-user-freq"

tried to allocate the 256 megs of memory too but i got the same error :/

BTW, does anyone have any tips to improve performance? Tried to tune xp to use less memory but as i understand the emulation depends on your processor - overclocking/better CPU would improve overall performance?

---

### Post by XAsmodeanX on 2006-07-10
if you run the command as sudo it doesn't freak out about the /dev/rtc thing but it still gives the error about memory (which can be fixed if you run what it tells you to but that's ghetto everytime you want to run the command) and it still gives the error:

Could not open '/dev/kqemu' - QEMU acceleration layer not activated

Well, I looked in /dev/ and it turns out there is no kqemu in /dev.  No idea how to make one.

---

### Post by sup on 2006-07-10
> Could not open '/dev/kqemu' - QEMU acceleration layer not activated

Well, I looked in /dev/ and it turns out there is no kqemu in /dev. No idea how to make one.
Read post #48 of this thread

---

### Post by XAsmodeanX on 2006-07-10
I did last night, just too tired to get on and post about it.

---

### Post by sup on 2006-07-10
mouse did not work for me (it stayed in bottom right corner) - and windows are quete useless without mouse. SO i google a bit and found this:
[http://wiki.clug.org.za/wiki/QEMU_mouse_not_working]("http://wiki.clug.org.za/wiki/QEMU_mouse_not_working")
(all you need is to type this ```
export SDL_VIDEO_X11_DGAMOUSE=0
``` in terminal)
hope this helps someone

---

### Post by sup on 2006-07-10
When I installed qemu on my previous install, [this wiki page]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo") helped me a lot, but it become obsolete. I updated it with the script by andrejkw - I hope you will not mind.

---

### Post by qrm on 2006-07-10
thought that id make a new install of windows and made a new .img. Now it gives me a page_fault_in_nonpaged_area. Anyone have any ideas?

---

### Post by hype on 2006-07-11
> **sup said:**
> When I installed qemu on my previous install, [this wiki page]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo") helped me a lot, but it become obsolete. I updated it with the script by andrejkw - I hope you will not mind.

 Exellent Wiki Sup !! 
qrm: you should check that Wiki out; i had the same problem of "no paged blabla"

 andrejkw: Exellent script, installation went perfectly ; there's maybe a little "lack" of explanation on using Qemu, but SUp did it quite well :D

---

### Post by sup on 2006-07-11
Well, most of the credit goes to previous author(s) of the page, I just updated it so that it includes the script and options for using it are not obsolete anymore.

---

### Post by hype on 2006-07-11
Ok, good job anyway ; i have Xp installed and running atm :D

Then i was just wondering, is it necessary to install firewall and antivirus on the "guest" Xp (and sp2) ?

 Actually, i hope that the only thing that could be damaged is my "guest.img" file, right?

---

### Post by sup on 2006-07-11
It should not be more dangerous than having unprotected xp box somewhere on you LAN. 

I personally od not do this "the thing we all love about windows" rubish because I do not use internet within qemu (well, I have Ubuntu, dont I); however, if you are going to extensively browse the web with Internet explorer, you are at risk of getting infected - only your .img file, however.

Do not run qemu under root, though;-).

---

### Post by hype on 2006-07-11
Thanks for infos sup :)

Now i'm struggling with sound :p 
The -sound-hw options is not working here:
```
qemu: invalid option -- '-sound-hw'
```
 -I tried to install my Audigy 4 drivers manually (from cd)
but xp returns a "error code 10" after installing driver and trying to "start" the device, i suppose.

EDit: How do you disable internet on on your guest Xp?

---

### Post by hype on 2006-07-11
GOT IT !!!!
 The option is :
soundhw -all
(not sound-hw)
 Here is the command i used to boot Xp
```
qemu /home/hype/testxp1.img -soundhw all -net user -net nic -m 256 -localtime -kernel-kqemu 
```

Works great ! Xp instantly detected my news hardware - where at first it detected nothing - and after a quick test, sound was here 
Just a quick search on qemu's homepage can save lifes. :p

Sound Softwares are (were?) the only thing that make (made?!) me need to boot on Xp.

Guys...you own.
Sup can i become your fanboy?

---

### Post by sup on 2006-07-11
oops, a typo, it should be -soundhw all (I corrected it already)

as for the internet, you could banish all network with -net none, but that would also shut down your samba connection, so easiest way that comes to my mind is installing any firewall to your guest system and allow only comunication with 10.0.0.0/8 (private network IPs that qemu uses)

---

### Post by hype on 2006-07-11
Great, the wiki should be 100% working :D

 Thanks for advice, ill install a firewall.

Simply one thing i dont get: is samba share or *.img mounting the only ways to share files between host and guest? 
 I mean, isnt there a way to have all the other partions visible in "My Computer" ?

---

### Post by sup on 2006-07-11
I suggest you read man qemu - there is something about tftp. However I thing samba is the only way (but do you need to share anything but home and maybe your windows partition, if you have any (providing you have to windows licenses:-)?)

---

### Post by XAsmodeanX on 2006-07-11
I just got an update notification about a new kernel from synaptic and I went ahead and installed it but now it won't load the kqemu module at startup so I can't use kqemu optimization when I run qemu.  I need to be able to load the module at startup or know how to insert it before running qemu.  Any ideas would be greatly appreciated.

---

### Post by XAsmodeanX on 2006-07-12
It seems that when I boot into the version 26 of the kernel as opposed to 25 it can't find the kqemu module.  In 25 it has no problem but in 26 I get an error from modprobe saying:
FATAL: module kqemu not found.

Or something like that.

---

### Post by tonyp1969 on 2006-07-12
I have installed QEMU, however I have installed Windows XP Pro and I am getting an error stating that it cannot Verify the licence and I cannot login.
How can I remove all this again and reclaim the disk space?

---

### Post by squilla on 2006-07-12
Hi
Boot windows in safe mode by pressing F8 when it starts up  and install SP2 - Service Pack 2. It works great after that.

There is a link to SP2 in one of the earlier posts if you do not have the cd

Regards

Squilla

---

### Post by squilla on 2006-07-12
You have to recompile the kqemu kernel module for every new kernel you install.
Regards
Squilla

---

### Post by superm1 on 2006-07-12
> **squilla said:**
> You have to recompile the kqemu kernel module for every new kernel you install.
Regards
Squilla

This never fails to bother me.  Stuff built with module-assistant at least I think should be adapted to automatically build a new kernel module for you as needed.

---

### Post by tkjacobsen on 2006-07-12
> **superm1 said:**
> This never fails to bother me.  Stuff built with module-assistant at least I think should be adapted to automatically build a new kernel module for you as needed.

Add a spec at launchpad, maybe this can be done in future releases
[https://launchpad.net/distros/ubuntu/+specs](https://launchpad.net/distros/ubuntu/+specs)

---

### Post by IcemanV9 on 2006-07-13
I just updated the kernel to -26. I recompiled kqemu module and it failed with this error message, "FATAL: Error inserting kqemu (/lib/modules/2.6.15-26-686/misc/kqemu.ko): Invalid module format"

Is there a workaround or solution for this problem?

UPDATE: Hey, what do you know? It is fixed. I just found out there is a newer version of kqemu, so I used kqemu-1.3.0pre9.tar.gz instead of -pre7.

---

### Post by tonyp1969 on 2006-07-13
Great, I have a working WinXP under QEMU. Have a problem though, it detects a CD-Rom drive but it will not see any media I insert into the ROM. Help

---

### Post by hype on 2006-07-13
Is anyone having problems with transparency of qemu under **Xgl**?

It works perfectly under Gnome, but Qemu's windows is almost transparent with Xgl.
 Is there a way to make it "non" tranparent?

---

### Post by XAsmodeanX on 2006-07-13
Here's some condensed troubleshooting I wrote in a file in the same directory as the qemu image.  It makes for quick work of some of the common problems I've had.  Archangel is my computer name.


> INSTRUCTIONS FOR RUNNING THE QEMU VIRTUAL MACHINE ON ARCHANGEL

1. First check that the kqemu does not exist.  If it does go on to 3.

        ls /dev/ |grep kqemu

2. Make the kqemu file in /dev/.

        sudo mknod /dev/kqemu c 250 0
        sudo chmod 666 /dev/kqemu

3. Start the qemu virtual machine with kqemu optimization.

        sudo qemu -localtime -hda /home/xasmodeanx/winxp/winxp.img
        -cdrom /dev/cdrom -boot c -kernel-kqemu -m 256M


4. Correct the /dev/shm error (only needed if step 4 gives error).

        sudo umount /dev/shm
        sudo mount -t tmpfs -o size=272m none /dev/shm

5. If you encounter this error:

        Could not configure '/dev/rtc' to have a 1024 Hz timer. This is
        not a fatal error, but for better emulation accuracy either use
        a 2.6 host Linux kernel or type
        'echo 1024 > /proc/sys/dev/rtc/max-user-freq' as root.

   Then type:
        sudo su
        password: (enter password)
        echo 1024 > /proc/sys/dev/rtc/max-user-freq
        exit

   Continue again with step 3.

6. If you experience the transparent window bug because of XGL then:
        export XLIB_SKIP_ARGB_VISUALS=1

   Note that this is only a temporary fix.

IF ANY PROBLEMS ARE ENCOUNTERED CHECK THE BOOKMARK AT
UBUNTUFORUMS.ORG.

---

### Post by hype on 2006-07-14
Thanks for reply but none of this commands removed tranparency of Qemu on Xgl :(

Edit: Btw, my mouse is quite "laggy" when running Qemu + Xp +Xgl.
I noticed my mouse is detected as PS2 mouse ; i guess its the way qemu emulates a mouse. My mouse is a Logitech Mx 518.

---

### Post by Dryer Lint on 2006-07-14
I rand the script several times now and tried through all combinations of using cvs or no, using patches yes or no but the installation always aborts with this error message:

```
========================= Installation results ===========================

Copying documentation directory...
/var/tmp/EdkcQMPjQIOPSXeYFOKA/installscript.sh: line 13: 11417 Segmentation fault      mkdir -p "/usr/share/doc/qemu"
/var/tmp/EdkcQMPjQIOPSXeYFOKA/installscript.sh: line 9: cd: qemu/doc-pak: No such file or directory

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

If anyone could help me figure out why that is, I'd be really glad!

And another thing: The server containing the DHCP patch is pretty much inaccessible all the time, a mirror would be great!

---

### Post by JohnBeaulieu on 2006-07-16
boogedy boogedy boogedy boo

---

### Post by XAsmodeanX on 2006-07-16
The line:

        export XLIB_SKIP_ARGB_VISUALS=1

should work.  I'm using XGL/compiz and I had the transparent window bug and typing that line into the terminal and hitting enter fixed it for me.

---

### Post by XAsmodeanX on 2006-07-16
@Dryer Lint:

Did you run the command as root?

---

### Post by Dryer Lint on 2006-07-16
> **XAsmodeanX said:**
> @Dryer Lint:

Did you run the command as root?

Yes, I ran it with sudo...

But it doesn't matter, I installed QEMU manually from CVS now, using some of the parameters from the script.

---

### Post by HobbitTR on 2006-07-16
I get the following:
Downloading QEMU...
--15:41:21--  [http://qemu.dad-answers.com/download/qemu/qemu-snapshot-2006-07-16_23.tar.bz2](http://qemu.dad-answers.com/download/qemu/qemu-snapshot-2006-07-16_23.tar.bz2)
           => `qemu-snapshot-2006-07-16_23.tar.bz2'
Resolving qemu.dad-answers.com... 66.98.184.92
Connecting to qemu.dad-answers.com|66.98.184.92|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:41:23 ERROR 404: Not Found.

and later:

Extracting QEMU...
tar: qemu-snapshot-2006-07-16_23.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ERROR: Unable to extract QEMU.

I have deleted the install_qemu.sh  file several times and tried the install from both http sites:
 [http://andrew.v5n.net/ubuntu/install_qemu.sh](http://andrew.v5n.net/ubuntu/install_qemu.sh)
AND
 [http://exvision.net/install_qemu.sh](http://exvision.net/install_qemu.sh)

NOW What do I do? I downloaded the qemu-snapshot-2006-07-16_23.tar.bz2  file without a problem but am stumped as to the next step.

I am new to Ubuntu but have a couple of apps I want to run in windoze and would like to see this through without more headaches, any answers please?

---

### Post by luneo on 2006-07-21
To enable the kqemu on system start, get the attachment file and untar the file in the folder /etc/init.d ... the run the command... sudo apt-get install bum ... to install bum (Boot up manager) and enable the kqemu service... it will create the /dev/kqemu and will modprobe the kqemu and tun... and for the xgl thing open the session settings and add the export XLIB_SKIP_ARGB_VISUALS=1 to  start at the begging of the session...

---

### Post by luneo on 2006-07-21
adding the export thing ins't nice... and dosen't work....
so just make a script....
in terminal:
```

sudo nano /usr/local/bin/qemu

```
in nano (copy and paste... to paste in nano just press shift+insert)
```

#!/bin/sh
# This is a hack to avoid problems with alpha channel from xgl and
# sdl from qemu

export XLIB_SKIP_ARGB_VISUALS=1
/usr/bin/qemu $@
unset XLIB_SKIP_ARGB_VISUALS

```
now close and save( crtl+X)
and do the following
```

sudo chmod a+x /usr/local/bin/qemu

```

now it should work....

---

### Post by ethangato on 2006-07-26
> **qrm said:**
> thought that id make a new install of windows and made a new .img. Now it gives me a page_fault_in_nonpaged_area. Anyone have any ideas?

hi, I have the same problem.
did you make it work?

10:30am add:
I remove "-kernel-kemu" then it looks work

---

### Post by skyshock21 on 2006-07-27
> **luneo said:**
> adding the export thing ins't nice... and dosen't work....
so just make a script....
in terminal:
```

sudo nano /usr/local/bin/qemu

```
in nano (copy and paste... to paste in nano just press shift+insert)
```

#!/bin/sh
# This is a hack to avoid problems with alpha channel from xgl and
# sdl from qemu

export XLIB_SKIP_ARGB_VISUALS=1
/usr/bin/qemu $@
unset XLIB_SKIP_ARGB_VISUALS

```
now close and save( crtl+X)
and do the following
```

sudo chmod a+x /usr/local/bin/qemu

```

now it should work....

That worked MARVELOUSLY well!  Many thanks!  I learned something new today.  :cool:

---

### Post by linuksamiko on 2006-07-29
finaly I got a running qemu with kqemu. 

Is it normal that its still MUCH slower then vmware. I have seen vmware once in action and that was very fast (almost as fast as a regular system) but my qemu is still slow even with kqemu.
It is now usable (thanks to kqemu) but still not very usefull for dayly life.

But at least I can setup a test-system now as virtual computer and I don't have to uninstall an old computer of mine :-)

thanks for that script and your howto it helped me alot

---

### Post by eduard on 2006-07-29
Hi, 

Maybe somebody knows the answer to my errors. Is regarding kqemu:

.........

/root/qemu-src/qemu-0.8.2/kqemu-1.3.0pre9/kqemu-linux.c:336: error: ‘ENOMEM’ undeclared (first use in this function)
make[2]: *** [/root/qemu-src/qemu-0.8.2/kqemu-1.3.0pre9/kqemu-linux.o] Error 1
make[1]: *** [_module_/root/qemu-src/qemu-0.8.2/kqemu-1.3.0pre9] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.15'
make: *** [kqemu.ko] Error 2

---

### Post by qrm on 2006-08-05
its seems that the [http://andrew.v5n.net](http://andrew.v5n.net) is down and it has been down for couple of days

---

### Post by chokes on 2006-08-05
someone can upload the file ? tanx in advance! ;)

---

### Post by TuxCrafter on 2006-08-07
can you please upload the script.

I have copiled kqemu and modprobed it. It is loaden but quemu won't use it. I would like to have a look at you script to solve it.

---

### Post by rippon on 2006-08-08
Yes, it would be very much appreciated if someone could upload that script!

This is from the host of that file:

> "Virtual 5 Network is currently under re-development. Our main site, among with many services, has been built from ground up. Once our staff feel like we are stable enough to open we shall. If you wish to become a staff member or a BETA tester you may do so by e-mailing [email]manager@v5n.net[/email]. We also have a Development Blog which will keep you up to date on everything happening at V5N. We look forward to seeing you soon in the near future! Thank you for your valuble support. Virtual 5 Network Management."

They could be down for a while, I think we should upload the script to the first post.

Thanks!

---

### Post by qrm on 2006-08-08
ive uploaded the script to: [HERE]("http://www.zone.ee/qrm/qemu/install_qemu.sh")

The mouse wall patch and kqemu arent downloadble because they were both hosted on the v5n.net site but the DHCP patch is hosted somewhere else.

EDIT: kqemu should compile and install nicely, its hosted @ the same place as qemu

---

### Post by TuxCrafter on 2006-08-08
Thank you for the script it works perfect (the cvs snapshot name was a bit different but no problem i changed the script a bit)

I now have full kqemu support.

I have used VMware but wanted to test qemu because it fits my philosophy more. To bad that kqemu isn't opensource.

However i now could compare qemu an vmware together because i have them both on the same PC.

I have 1 GB DDR2 533 MHz ram. I give the VM 512.

The installation of windows xp was very very slow with qemu i found some reports about that, and it seems to be normal.

However after the install VMWare is still far far faster then qemu. Why is this? 

Also I can change the windows size of the vmplayer and windows will adapt to this size by automatic change the screen resolution. This is a beautiful feature. It allows me to watch sport and news with drm shit on windows media player with vmware in a small box on Linux. I can not do this with qemu because I cant automatic change the windows size or is there a param that i can set?

With vmware i can easily install usb or serial devices with a simple mouse click. On qemu i must search the pid and other stuff to get a usb memory stick connected a lot of work.

Despite this i will always keep faith in qemu but my conclusion is that vmplayer is far better. 

I only wise i new exactly why there is such a big difference. ( I know different coding)

---

### Post by qrm on 2006-08-08
are you quite sure you are running it with -kernel-kqemu ? Last time i had it running it was as fast as my installed windows. I cant use vmware because i get some very rare errors which dont have solutins anywhere so im using qemu

---

### Post by TuxCrafter on 2006-08-08
> **qrm said:**
> are you quite sure you are running it with -kernel-kqemu ? Last time i had it running it was as fast as my installed windows. I cant use vmware because i get some very rare errors which dont have solutins anywhere so im using qemu

yup i am sure in the qemu command info kqemu give me the info that everyting is working.

---

### Post by qrm on 2006-08-08
maybe the problem lied within the dual core (AMD X2 on AM2 or conroe) which i guess your running (the DDR2 was a hint)

---

### Post by TuxCrafter on 2006-08-08
No way I believe in saving energy until we stop using fossil energy sources. So I use a VIA Esther processor 1200MHz.

My total PC excl monitor/tft is only using 20W. But when I installed qemu without kqemu windows reported a PII 1,2 GHz :-D. But with kqemu it reported the correct CPU.

---

### Post by baghery.farhad on 2006-08-09
wget [http://andrew.v5n.net/ubuntu/install_qemu.sh](http://andrew.v5n.net/ubuntu/install_qemu.sh)

not works! :confused:

---

### Post by brownrl on 2006-08-09
Same no worky... server is dead?

---

### Post by brownrl on 2006-08-09
I think this andrew guy got fired from v5n.net. Does some one have a copy of the script? All this work just to get IE going so that I can test pages that I make. 

Dang it! why are 60% of people so stupid and use the browser that comes in their crap but OS?

---

### Post by qrm on 2006-08-10
just look a few posts up, dont add the mouse wall patch because the script cant dl it and it will cancel your installation process

---

### Post by pteglia on 2006-08-10
You could use IEs4Linux to run those IE windows you need:  [http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

---

### Post by brownrl on 2006-08-11
OMG that ies4linux works and does the trick.

Sweet! Super Sweet! Thanks a ton.

The flash 9 player is interesting.

Rob

---

### Post by ciscosurfer on 2006-08-11
Was anyone able to get to the qemu_mouse.patch?  Can someone please post it here in this thread or upload the file here??  Really want the qemu_mouse.patch!

---

### Post by qrm on 2006-08-14
the page is down atm (or it was) so i doubt if anyone could upload it. But thsi might help you, paste it in your console right before you start qmeu:
```
export SDL_VIDEO_X11_DGAMOUSE=0
```

---

### Post by paulb_ on 2006-08-23
...

---

### Post by andrejkw on 2006-08-23
Links updated :) Sorry about the downtime guys.

---

### Post by HobbitTR on 2006-08-24
TC,

I am a newbie to Ubuntu, I need a vm for my wife as she has two specific windoze apps which she uses for work. The vm must support serial and USB connections.  I do not understand vmplayer vs vmserver and which is the appropriate one to install. I just want to install Win2000 on a Ubuntu 6.06 distro and be done with it. Do you know of a simple install procedure that even this newbie can follow? :confused: 

Thanks,
HobbitTR

> **TuxCrafter said:**
> 

I have used VMware but wanted to test qemu because it fits my philosophy more. To bad that kqemu isn't opensource.

However i now could compare qemu an vmware together because i have them both on the same PC.

I have 1 GB DDR2 533 MHz ram. I give the VM 512.

The installation of windows xp was very very slow with qemu i found some reports about that, and it seems to be normal.

However after the install VMWare is still far far faster then qemu. Why is this? 

Also I can change the windows size of the vmplayer and windows will adapt to this size by automatic change the screen resolution. This is a beautiful feature. It allows me to watch sport and news with drm shit on windows media player with vmware in a small box on Linux. I can not do this with qemu because I cant automatic change the windows size or is there a param that i can set?

With vmware i can easily install usb or serial devices with a simple mouse click. On qemu i must search the pid and other stuff to get a usb memory stick connected a lot of work.

Despite this i will always keep faith in qemu but my conclusion is that vmplayer is far better. 

I only wise i new exactly why there is such a big difference. ( I know different coding)

---

### Post by srunni on 2006-08-27
I'm getting a "PAGE_FAULT_IN_NONPAGED_AREA" when installing Windows XP Pro. It says to disable BIOS options like shadowing and caching. Does anyone know what's going on? I know this disc works just fine for a normal install.
EDIT: Got past that, but now it hangs on reboot after the install.

---

### Post by qrm on 2006-09-09
dont use kqemu module while installing XP

---

### Post by John Jones on 2006-09-10
I've just tried following the instructions in the Wiki, which appear to be more or less the same as these, and instead of getting install_qemu.sh, I get a 3.5Kb file called index.html, which, when opened, informs me that this account has been suspended, please contact the billing department. Presumably, this isn't what I'm looking for.

What's happening?

John :confused:

---

### Post by henriquemaia on 2006-09-14
> **John Jones said:**
> I've just tried following the instructions in the Wiki, which appear to be more or less the same as these, and instead of getting install_qemu.sh, I get a 3.5Kb file called index.html, which, when opened, informs me that this account has been suspended, please contact the billing department. Presumably, this isn't what I'm looking for.

What's happening?

John :confused:
His account has been suspended. When trying to download, we're redirected to:

[http://server12.e-webhost.co.uk/suspended.page/](http://server12.e-webhost.co.uk/suspended.page/)

[andrejkw]("http://ubuntuforums.org/member.php?u=45379") please take a look into this. Thanks.

---

### Post by etank on 2006-09-15
Has there been anything new latley about getting the installer script. I just came across this thread today and would love to have a copy of it. I have tried all of the links in the thread but they are all dead. This page [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo) even links to the pages that are dead. Is it possible for someone else to host the files that are needed?

---

### Post by HermesPanduck on 2006-09-19
The script needs a bit of editing: KQEMU is now pre9, not pre7. Not sure about the mouse wall patch because I didn't install it.

Edit: on first attempt, the installation froze on "Installing Devices". I hunted around and someone suggested using the "-win2k-hack" option and it seems to be going fine now.

---

### Post by jrobinson5 on 2006-09-19
Andre, nice work! You might want to edit the post to indicate the new location of the script I found on page 19, because your site 404's.

---

### Post by samslaves on 2006-09-28
Hi all,

I'm lost! The script tells me:

ERROR: Unable to find appropriate Kernel Headers for your Kernel.

>>>>

sudo ./install_qemu.sh
Your Ubuntu release is: Dapper Drake 6.06
Is this correct? y
Would you like to download QEMU from the CVS (Unstable)? n
Installing Dependencies...
Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
g++-3.4 is already the newest version.
libsdl1.2debian is already the newest version.
libsdl1.2debian-all is already the newest version.
build-essential is already the newest version.
libsdl1.2-dev is already the newest version.
zlib1g-dev is already the newest version.
checkinstall is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ERROR: Unable to find appropriate Kernel Headers for your Kernel.

<<<

I'm running Dapper on a dual G5; kernel:

>>>

vmlinux -> vmlinux-2.6.15-27-powerpc64-smp

<<<

with kernel headers for powerpc64-smp 2.6.15-27 .


Please help me.

Thanx
Sam

---

### Post by samslaves on 2006-09-28
Added these lines to install.sh

## DETECT KERNEL -- DOWNLOAD PROPER HEADERS ##
KERNELPPC64SMP=`uname -r | grep "\-powerpc64-smp$"`

...

if [ "$KERNELPPC64SMP" != "" ]; then
  	cecho "blue" "Installing Kernel Headers (PPC64-SMP)..."
 	apt-get -y --force-yes install linux-headers-powerpc64-smp || error "Unable to Install Kernel Headers."


now I was able to compile but at some point...

/usr/bin/ld: qemu-i386: Not enough room for program headers (allocated 8, need 9)
/usr/bin/ld: final link failed: Bad value
collect2: ld returned 1 exit status
make[1]: *** [qemu-i386] Error 1
make[1]: Leaving directory `/tmp/build-qemu/qemu-0.8.1/i386-user'
make: *** [all] Error 1
ERROR: Unable to Compile QEMU...

Could you help.

Sam

---

### Post by TuxCrafter on 2006-09-29
do you have enough space on the disk? ;)

---

### Post by samslaves on 2006-09-29
Hello,

it is not a matter of disk space. It is a ld bug.
Run

perl -pi -e "s/SIZEOF_HEADERS/65536/g" *.ld

to augment the SIZEOF_HEADER constant in the ld script.
Then we face an error about undefined reference to `_SDA_BASE_' 
This can be solved applying a patch to the file ppc.ld in qemu directory:


   /* We want the small data sections together, so single-instruction offsets
      can access them all, and initialized data all before uninitialized, so
      we can shorten the on-disk segment size.  */
-  .sdata     : { *(.sdata) }
+  .sdata     :
+  {
+    PROVIDE (_SDA_BASE_ = 32768);
+    *(.sdata .sdata.* .gnu.linkonce.s.*)
+  }
   _edata  =  .;
   PROVIDE (edata = .);
   __bss_start = .;

---

### Post by samslaves on 2006-09-29
Gasp!

Replace the smile with )

---

### Post by samslaves on 2006-09-29
Ok,

another error, this time while compiling the sparc support. Apply this patch to the file /target-sparc/op_helper.c

#ifdef USE_INT_TO_FLOAT_HELPERS
 void do_fitos(void)
 {
-    FT0 = int32_to_float32(*((int32_t *)&FT1));
+    FT0 = int32_to_float32(*((int32_t *)&FT1), &env->fp_status);
 }
 
 void do_fitod(void)
 {
-    DT0 = int32_to_float64(*((int32_t *)&FT1));
+    DT0 = int32_to_float64(*((int32_t *)&FT1), &env->fp_status);
 }
 #endif

---

### Post by samslaves on 2006-09-29
I'm writing this to help people who want build the latest release of qemu on ubuntu (Dapper) for PPC. All posted informations were gathered from different sites on internet.

...

So far so good. Make completed.
Now installing...

---

### Post by etank on 2006-09-29
Is there any way to get this for Edgy? I get the error about my version of Ubuntu not being supported.

---

### Post by ffadmraven on 2006-09-30
Hi, I just tried to download the script, but I'm getting an error saying the server doesn't exsist.  I even tried it in Firefox, but just get a 404 error.  Could someone please look into this?  Thanks.

---

### Post by tkjacobsen on 2006-09-30
> **ffadmraven]
Hi, I just tried to download the script, but I'm getting an error saying the server doesn't exsist. I even tried it in Firefox, but just get a 404 error. Could someone please look into this? Thanks.[/QUOTE]

See last page, he has a new link:

[QUOTE=HermesPanduck said:**
> The script needs a bit of editing: KQEMU is now pre9, not pre7. Not sure about the mouse wall patch because I didn't install it.
y
Edit: on first attempt, the installation froze on "Installing Devices". I hunted around and someone suggested using the "-win2k-hack" option and it seems to be going fine now.

---

### Post by andrejkw on 2006-09-30
Link once again updated :D
Thanks to **Adrian** for hosting it!

---

### Post by Zed on 2006-10-01
In edgy, something like this will work (barring potential library dependencies the below might be missing...)
```

sudo apt-get install qemu build-essential linux-headers-$(uname -r)
wget http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz
tar xzf kqemu-1.3.0pre9.tar.gz
cd kqemu-1.3.0pre9
./configure --prefix=/usr --disable-gcc-check --kernel-path=/lib/modules/$(uname -r)/build/
sudo ./install.sh

```

---

### Post by yock on 2006-10-14
I haven't read through this entire thread, but I had problems with the install script on Dapper. I took the liberty of fixing it, which involved changing the CVS URL and the append to the version number (changed "23" to "05", which seems to be their new standard). In either case, this script works as of the date of this post. Hope this helps someone.

---

### Post by tonydm on 2006-10-17
Hi,

I ran 
sudo qemu -localtime -hda /home/me/winxp.img -cdrom /dev/cdrom -boot d -kernel-kqemu -m 512M -win2k-hack

Although qemu loads and I am installing WinXP, I get this:
Could not open '/dev/kqemu' - QEMU acceleration layer not activated

Your expert advice is welcome.  Thanks

Tony

---

### Post by ahaslam on 2006-10-21
> **tonydm said:**
> Hi,

I ran 
sudo qemu -localtime -hda /home/me/winxp.img -cdrom /dev/cdrom -boot d -kernel-kqemu -m 512M -win2k-hack

Although qemu loads and I am installing WinXP, I get this:
Could not open '/dev/kqemu' - QEMU acceleration layer not activated

Your expert advice is welcome.  Thanks

Tony
I got the same result.
Kqemu was not located under /dev/ - I had to find it & place a link in that directory. After this the error message changed to something like: *version mismatch* & two long numbers. Qemu is working, just very slowly on my old laptop.

Sorry I couldn't be more specific on the location or error message. I'm running Tovid to make a DVD & I'm struggling to surf, yet alone run Qemu ;)

Tony.

---

### Post by ac4000 on 2006-10-21
Wow!  Thank you so much, andrejkw, that was amazing:  no errors, perfect operation.

---

### Post by murphfin on 2006-10-24
> **Zed said:**
> In edgy, something like this will work (barring potential library dependencies the below might be missing...)
```

sudo apt-get install qemu build-essential linux-headers-$(uname -r)
wget http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz
tar xzf kqemu-1.3.0pre9.tar.gz
cd kqemu-1.3.0pre9
./configure --prefix=/usr --disable-gcc-check --kernel-path=/lib/modules/$(uname -r)/build/
sudo ./install.sh

```
I lost the ability to run Kqemu with Qemu when I updated to Edgy (6.10). I tried your scipt and after entering the last command I received this error message - 
 sudo ./install.sh
 cp: cannot stat `kqemu.o': No such file or directory

Is there something I missed. Thanks

---

### Post by murphfin on 2006-10-24
> **andrejkw said:**
> This is more of a Automatic Installation script, than a HOW-TO.
As of now, it will only work with **Breezy** and **Dapper**.

This script will compile and install:
[IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG] **QEMU 0.8.2 or QEMU from CVS Snapshot** (Choice Given during Install)
[IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG] **KQEMU 1.3.0pre9**

Included QEMU Patches (Optional - asked during installation):
[IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG] **[DHCP Patch]("http://people.brandeis.edu/%7Ejcoiner/qemu_idedma/qemu_dma_patch.html#dhcp")**
[IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG] **Mouse Wall Bug Patch** is no longer needed (=> 0.8.2)

The credits go to:
- Nando Florestan (I used some parts of his Script)
- Saad N. (For inspiration and testing)
- Dmytro (Breezy Testing, Spell Checking, and NT, 95, 95 Russian Testing)

**For those wanting to install _Windows XP_ under QEMU/KQEMU check out this more detailed tutorial: [WindowsXPUnderQemuHowTo]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")**

**INSTALLATION INSTRUCTIONS**:
```
wget http://soultrap.net/andrejkw/install_qemu.sh
chmod +x ./install_qemu.sh
sudo ./install_qemu.sh
``` Afterwards just follow the on-screen instructions.

**USAGE INSTRUCTIONS**:
[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] NOTICE FOR 64bit USERS: You have to use **qemu-system-x86_64** instead of **qemu**. Otherwise the "-kernel-kqemu" option will not work.

1.) The first thing you probably want to do is to create a disk image into which you will install the Guest operating system. You can do this by typing the following into the terminal.
M = MB
G = GB
```
qemu-img create **(FILE NAME).img** **(SIZE OF IMAGE)**

*Example:*
qemu-img create guest.img 1G
``` 
2.) After the image has been created (assuming the step above gave you no errors) we can prepare to launch QEMU. But before we go ahead and do that, we have to make a few decisions. The basic command we will be using now is:
```
qemu -localtime -hda **(FILE NAME).img**

*Example:*
qemu -localtime -hda guest.img
``` 
3.) Now, with the basic command ready, we will now move on to the paramaters. Now, in order to get our Guest OS installed we have to install it from a CD or a CD image. Add the '-cdrom' parameter to tell QEMU that you want to have a CD-ROM present.
```
qemu -localtime -hda **(FILE NAME).img** _-cdrom **(PATH TO DEVICE OR CD IMAGE)**_

*Example:*
qemu -localtime -hda guest.img -cdrom /home/andrejkw/XPCD.iso
**OR**
qemu -localtime -hda guest.img -cdrom /dev/cdrom
``` 
3.) Ok, so now we told QEMU what to use as our CD-ROM drive. The next step is to tell it to boot from our CD-ROM before booting from our Hard-Drive image. To do this we will add a '-boot d' (D: stands for the CD-ROM drive in this case, because it comes right after C: )
```
qemu -localtime -hda **(FILE NAME).img** -cdrom **(PATH TO DEVICE OR CD IMAGE)** _-boot d_

*Example:*
qemu -localtime -hda guest.img -cdrom /dev/cdrom -boot d
``` 
4.) Next thing we have to do, is tell QEMU that we have KEMU installed. It is supposed to detect if KQEMU is installed, but I had a bad experience with this. And it doesn't hurt to be sure that QEMU is using KQEMU. You can do this by adding the '-kernel-kqemu' option.
```
qemu -localtime -hda **(FILE NAME).img** -cdrom **(PATH TO DEVICE OR CD IMAGE)** -boot d _-kernel-kqemu_

*Example:*
qemu -localtime -hda guest.omg -cdrom /dev/cdrom -boot d -kernel-kqemu
``` 
5.) If you were to press enter now, QEMU would start booting. But before you do that, you should consider adding some of these options:

[IMG]http://ubuntuforums.org/images/icons/icon3.gif[/IMG] If you want to give your Guest OS more RAM (QEMU uses 128MB by default) add the '-m SIZE' option.
M = MB
G = GB
```
qemu -localtime -hda **(FILE NAME).img** -cdrom **(PATH TO DEVICE OR CD IMAGE)** -boot d -kernel-kqemu _-m **RAM SIZE**_

*Example:*
qemu -localtime -hda guest.img -cdrom /dev/cdrom -boot d -kernel-kqemu -m 512M
``` 
[IMG]http://ubuntuforums.org/images/icons/icon3.gif[/IMG] If you are going to be installing Windows 2000/XP as your Guest OS, consider adding '-win2k-hack' as your option. It fixes some major issues, like the "Not enough disk space." while installing.
```
qemu -localtime -hda **(FILE NAME).img** -cdrom **(PATH TO DEVICE OR CD IMAGE)** -boot d -kernel-kqemu -m **RAM SIZE** _-win2k-hack_

*Example:*
qemu -localtime -hda guest.img -cdrom /dev/cdrom -boot d -kernel-kqemu -m 512M -win2k-hack
``` 
-----------------------------------------------------------------------

Check out Qemu Launcher (a nice QEMU Gui for GNOME) at [http://download.gna.org/qemulaunch/debian/](http://download.gna.org/qemulaunch/debian/)
Note: In the "Other" tab add "-kernel-kqemu" (no quotes) to the "Additional Arguments" field.

**If you are experiencing the Transparent Window bug (By running XGL...) check out Saad's thread ([http://ubuntuforums.org/showthread.php?t=187941](http://ubuntuforums.org/showthread.php?t=187941)) for instructions on how to fix it.**

Andrew, :D

When attempting to run the script I get a strange error message after the last command - sudo ./install_qemu.sh.
  -ne \E[31m
ERROR: You must run this script as root!
Everything before that worked fine. Any ideas what I'm doing wrong. Thanks

---

### Post by KillerKiwi on 2006-10-24
> **tonydm said:**
> Hi,

I ran 
sudo qemu -localtime -hda /home/me/winxp.img -cdrom /dev/cdrom -boot d -kernel-kqemu -m 512M -win2k-hack

Although qemu loads and I am installing WinXP, I get this:
Could not open '/dev/kqemu' - QEMU acceleration layer not activated

Your expert advice is welcome.  Thanks

Tony

I rerun this fragment from the script 
```
modprobe kqemu || error "Unable to Load KQEMU Module..."
modprobe tun || error "Unable to Load TUN Module..."
mknod /dev/kqemu c 250 0 || error "Unable to Create the KQEMU Device..."
chmod 666 /dev/kqemu || error "Unable to CHMOD the KQEMU Device..."
```

---

### Post by vikasrawal on 2006-10-31
Will this script work with Edgy Eft?

I installed Qemu using apt-get. It does not however show kqemu in the repositories. Is it already included in the qemu binary package? How can I check?

---

### Post by qrm on 2006-10-31
qemu isnt in the repos with support for the kqemu module, you have to compile it yourself. When I last tried it I couldnt get it to work

---

### Post by andreag on 2006-11-01
```

sudo apt-get install qemu build-essential linux-headers-$(uname -r)
wget http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz
tar xzf kqemu-1.3.0pre9.tar.gz
cd kqemu-1.3.0pre9
./configure --prefix=/usr --disable-gcc-check --kernel-path=/lib/modules/$(uname -r)/build/
sudo ./install.sh

```

One should also give the command

make

before install, otherwise there is no kqemu.

I did so in Edgy and apparently there is now a /dev/kqemu.
However when I try to use qemu I get 

Could not open '/dev/kqemu' - QEMU acceleration layer not activated

---

### Post by qrm on 2006-11-01
I got the same error and cpouldnt even fix with the solution given in post nr 48

---

### Post by alphamerik on 2006-11-02
You have to load the newly built kernel module:
  sudo depmod
  sudo modprobe kqemu

And you can rebuild the module image so (hopefully) you don't have to re-type the above commands after re-boot: 
  sudo dpkg-reconfigure linux-image-`uname -r`

---

### Post by Squarky on 2006-11-03
I've compiled and installed on Edgy with no errors:

```

./configure --prefix=/usr --disable-gcc-check --kernel-path=/lib/modules/$(uname -r)/build/
make
sudo ./install.sh

```

and loading the module gives me:

```

sudo depmod -a
sudo modprobe kqemu
FATAL: Error inserting kqemu (/lib/modules/2.6.17-10-generic/misc/kqemu.ko): Invalid module format

```

Anyone experienced this? Maybe has an idea for a solution?

Thanks!

---

### Post by factor on 2006-11-03
Here is how i got it working on Edgy for AMD64
```

sudo apt-get install qemu build-essential linux-headers-$(uname -r)
wget http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz
tar xzf kqemu-1.3.0pre9.tar.gz
cd kqemu-1.3.0pre9
./configure --prefix=/usr --disable-gcc-check --kernel-path=/lib/modules/$(uname -r)/build/
make
sudo ./install.sh
sudo depmod
sudo modprobe kqemu
sudo dpkg-reconfigure linux-image-`uname -r`

```

And then, i made a script i run everytime i want to run qemu +kqemu, you have to make an icon for it in your start menu as it is thought to be run in gnome. If you want to run it in terminal replace "gksu" for "sudo":

```

gksu mknod /dev/kqemu c 250 0 
gksu chmod 666 /dev/kqemu
qemu-system-x86_64 -boot c -hda /path/to/your/image.qcow -m 512 -localtime -kernel-kqemu

```

-m 512 is the amount of ram, here is 512 mb, if you want 256 it would be -m 256, and so on.

Hope it helps.

Regards.

---

### Post by Squarky on 2006-11-03
Thanks factor, it worked when I went back to using GCC 4.1 in stead of GCC 3.4.

---

### Post by J2R on 2006-11-06
I'm running Edgy Eft, and want to be able to run Windows XP Professional as guest OS. I managed to install QEMU with apt-get and get Windows running, but it is rather slow and I'd like to be able to get KQEMU working with it. I tried factor's suggestion, and attempt to start QEMU with the line below: 

qemu /winxp.img -cdrom /dev/cdrom -soundhw all -net user -net nic -m 256 -localtime -kernel-kqemu

but now when starting up Windows it keeps on rebooting (I get to the screen where it says 'Applying computer settings' but no further).

Removing the '-kernel-kqemu' allows me to run Windows OK, albeit at the slow speed.

Has anyone got kqemu working with Edgy Eft and can share the secret?

---

### Post by skenliv on 2006-11-08
I would also like to know how this is possible, it seems fast as hell when the module is loaded, but it keeps restarting... :(

---

### Post by jqp on 2006-11-09
thanks, that helped me, too.  i'm a noob and it explained the problem it was having compiling kqemu

---

### Post by cristobal151 on 2006-11-15
don't work with edgy :

> 
-ne \E[31m
ERROR: You must run this script as root!


---

### Post by gangrel on 2006-11-22
Installing Kernel Headers (386)...
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
linux-headers-386 ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 11 no actualizados.
Preparing for Download...
Downloading QEMU...
--09:57:59--  [http://qemu.dad-answers.com/download/qemu/qemu-snapshot-2006-11-22_23.tar.bz2](http://qemu.dad-answers.com/download/qemu/qemu-snapshot-2006-11-22_23.tar.bz2)
           => `qemu-snapshot-2006-11-22_23.tar.bz2'
Resolviendo qemu.dad-answers.com... falló: Nombre ó servicio desconocido.
Downloading KQEMU...
--09:57:59--  [http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz)
           => `kqemu-1.3.0pre9.tar.gz'
Resolviendo fabrice.bellard.free.fr... 212.27.63.117
Conectando a fabrice.bellard.free.fr|212.27.63.117|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 190,070 (186K) [application/x-gzip]

100%[====================================>] 190,070       53.88K/s    ETA 00:00

09:58:03 (53.77 KB/s) - `kqemu-1.3.0pre9.tar.gz' guardado [190070/190070]

[B]Extracting QEMU...
tar: qemu-snapshot-2006-11-22_23.tar.bz2: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Salida con error demorada desde errores anteriores
ERROR: Unable to extract QEMU.[/B]

please help

---

### Post by outofnicks on 2006-11-23
I did not realize the script would install so many updates! I'm on dialup and if I had known it would take so long I wouldn't have started and tied up the phone line.
This is a major bone to pick for me, it's so often assumed that everyone is on a broadband connection. Just as a forewarning to dialup users intending to use this script, it took a little over an hour before it even got to the qemu download, which itself is 1.7 mb. This is what went on during that period, it's still downloading qemu so I don't know if everything is going to work yet:
```
Your Ubuntu release is: Dapper Drake 6.06
Is this correct? y
Would you like to download QEMU from the CVS (Unstable)? n
Installing Dependencies...
Reading package lists... Done
Building dependency tree... Done
libsdl1.2debian is already the newest version.
build-essential is already the newest version.
zlib1g-dev is already the newest version.
The following extra packages will be installed:
  cpp-3.4 gcc-3.4-base libaa1-dev libartsc0-dev
  libasound2-dev libaudio-dev libgl1-mesa-dev
  libglu1-mesa-dev libncurses5-dev libslang2-dev
  libstdc++6-dev libxt-dev mesa-common-dev
Suggested packages:
  gcc-3.4-doc lib64stdc++6 libc6-dev-amd64 lib64gcc1
  libasound2-doc libstdc++6-doc
The following packages will be REMOVED:
  installwatch libsdl1.2debian-oss
The following NEW packages will be installed:
  cpp-3.4 g++-3.4 gcc-3.4 gcc-3.4-base libaa1-dev
  libartsc0-dev libasound2-dev libaudio-dev libgl1-mesa-dev
  libglu1-mesa-dev libncurses5-dev libsdl1.2-dev
  libsdl1.2debian-all libslang2-dev libstdc++6-dev libxt-dev
  mesa-common-dev
The following packages will be upgraded:
  checkinstall
1 upgraded, 17 newly installed, 2 to remove and 67 not upgraded.
Need to get 10.4MB of archives.
After unpacking 40.0MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com dapper-backports/universe checkinstall 1.6.0-2ubuntu1~dapper1 [90.1kB]
Get:2 http://archive.ubuntu.com dapper/main libxt-dev 1:1.0.0-0ubuntu3 [466kB]
Get:3 http://archive.ubuntu.com dapper/main gcc-3.4-base 3.4.6-1ubuntu2 [164kB]
Get:4 http://archive.ubuntu.com dapper/main cpp-3.4 3.4.6-1ubuntu2 [1687kB]
Get:5 http://archive.ubuntu.com dapper/main gcc-3.4 3.4.6-1ubuntu2 [494kB]

Installing Kernel Headers (386)...
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.15-27 linux-headers-2.6.15-27-386
The following NEW packages will be installed:
  linux-headers-2.6.15-27 linux-headers-2.6.15-27-386
  linux-headers-386
0 upgraded, 3 newly installed, 0 to remove and 67 not upgraded    
         Need to get 7786kB of archives.
After unpacking 79.7MB of additional disk space will be used.
Get:1 http://security.ubuntu.com dapper-security/main linux-he                                           aders-2.6.15-27 2.6.15-27.48 [6906kB]
Get:2 http://security.ubuntu.com dapper-security/main linux-headers-2.6.15-27-386 2.6.15-27.48 [857kB]
Get:3 http://security.ubuntu.com dapper-security/main linux-headers-386 2.6.15.25 [23.4kB]
Fetched 7786kB in 27m15s (4760B/s)
Selecting previously deselected package linux-headers-2.6.15-27.
(Reading database ... 133414 files and directories currently installed.)
Unpacking linux-headers-2.6.15-27 (from .../linux-headers-2.6.15-27_2.6.15-27.48_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-27-386.
Unpacking linux-headers-2.6.15-27-386 (from .../linux-headers-2.6.15-27-386_2.6.15-27.48_i386.deb) ...
Selecting previously deselected package linux-headers-386.
Unpacking linux-headers-386 (from .../linux-headers-386_2.6.15.25_i386.deb) ...
Setting up linux-headers-2.6.15-27 (2.6.15-27.48) ...

Setting up linux-headers-2.6.15-27-386 (2.6.15-27.48) ...
Setting up linux-headers-386 (2.6.15.25) ...
Preparing for Download...
Downloading QEMU...
```

---

### Post by outofnicks on 2006-11-23
A half hour later, I get the good news:
```
Installing KQEMU...
Loading KQEMU Module...

Congratulations! QEMU and KQEMU has been successfully Installed!
Do not forget to run QEMU with the '-kernel-kqemu' parameter!
For more information visit: http://fabrice.bellard.free.fr/qemu
Thank you for using this script!
```

I have yet to try it, think I'll  try an install of Vector Linux.
Thanks!:)

---

### Post by outofnicks on 2006-11-23
Sorry about my rant in the previous post, I was nervous about tying up the phone line and had no idea how much longer the process would take. 
I've tried installing Vector Linux on a 2 gig image, and after getting some of the same errors as other posters I've gotten to where it almost starts then aborts with this error:

```
qemu: could not load PC bios '/usr/local/share/qemu/bios.bin'
```

This is my startup command, used with both sudo and without, also  -kernel-kqemu and -no-kqemu:

```
ken@ubuntu:~/qemu$ sudo qemu -localtime -hda vector.img -cdrom /dev/cdrom -boot d -no-kqemu
```

Before switching to -no-kqemu, I got this error:

```
You do not have enough space in '/dev/shm' for the 128 MB of QEMU virtual RAM.
To have more space available provided you have enough RAM and swap, do as root:
umount /dev/shm
mount -t tmpfs -o size=144m none /dev/shm
Or disable the accelerator module with -no-kqemu
```

I only have 256 mb of RAM, could that be the problem? I've had an earlier version of qemu without kqemu in the past, with Vector Linux and DSL running without problems (not both at the same time, of course).
I did increase the memory for /dev/shm as directed, to no avail. It just spins up the Vector Linux CD, the qemu window pops up and then imediately aborts. What can I try next?

---

### Post by outofnicks on 2006-11-24
Well DUH, it was a simple fix. 
```
qemu: could not load PC bios '/usr/local/share/qemu/bios.bin'
```
Because it wasn't THERE. So I moved the qemu folder, which was in /usr/share/, into /usr/local/share/. And It worked!
Now I'm trying to get through the install process of Vector, but I got a fatal error upon trying to make the partitions.
Probably a thread for the Vector Linux forums!

---

### Post by sdavmor on 2006-11-26
> **murphfin said:**
> I lost the ability to run Kqemu with Qemu when I updated to Edgy (6.10). I tried your scipt and after entering the last command I received this error message - 
 sudo ./install.sh
 cp: cannot stat `kqemu.o': No such file or directory

Is there something I missed. Thanks

I got exactly the same issue and error message when I ran the script on my Edgy 6.10 laptop and a pair of 6.10 Edgy mini-towers (1 an AMD Seprom desktop and 1 an Intel Celeron D server install).

Any suggestions would be appreciated.

Thanks,
Steven Davies-Morris

---

### Post by qrm on 2006-11-27
outofnicks 

try what is said in the error

"To have more space available provided you have enough RAM and swap, do as root:
umount /dev/shm
mount -t tmpfs -o size=144m none /dev/shm"

```
sudo su
```
```
umount /dev/shm
```
```
mount -t tmpfs -o size=144m none /dev/shm
```
```
exit
```

and then try running qemu again

---

### Post by spyke01 on 2006-11-29
awesome script worked flawlessly

---

### Post by Zerlinna on 2006-12-07
> **cristobal151 said:**
> don't work with edgy :

I can confirm this.. even if I AM root, it won't let me run the install script on edgy: 

```
ERROR: You must run this script as root!
```

](*,) 

Z.

---

### Post by outofnicks on 2006-12-09
Well I had it working good on another install on a different partition, now I tried on a fresh install of Dapper and after almost 2 hours of waiting (I'm on dialup if you didn't read my previous posts) I get this:
```
Configuring KQEMU...
No Makefile file present in /lib/modules/2.6.15-26-386/build/ - kqemu cannot be built
grep: /lib/modules/2.6.15-26-386/build//Makefile: No such file or directory
Source path       /tmp/build-qemu/qemu-0.8.2/kqemu
C compiler        gcc
Host C compiler   gcc
make              make
host CPU          i386
Compiling KQEMU...
make -C /lib/modules/2.6.15-26-386/build/ M=`pwd` modules
make: *** /lib/modules/2.6.15-26-386/build/: No such file or directory.  Stop.
make: *** [kqemu.ko] Error 2
ERROR: Unable to Compile KQEMU...
```
So I try running qemu anyway, what the heck--I had an image prepared with Vector Linux installed, ran great before. 
```
qemu -hda vector.img -boot c -localtime -m 80
bash: qemu: command not found
```
Something went wrong in the install, what could it be?

---

### Post by elysium444 on 2006-12-25
I am runing ubuntu 6.10 (amd64) I did everything that was said in the forum but i cant run the make command:
[I]$ make
make -C /lib/modules/2.6.17-10-generic/build/ M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** No rule to make target `INSTALL/kqemu-1.3.0pre9'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [kqemu.ko] Error 2
[/I]
This is what I got, I cant understand what is the problem. 
Please help:confused:

---

### Post by lean on 2007-01-07
A can confirm that it does not work on Edgy 32bit.

Anyone up for the task?

The biggest problem I have with manually installing and running is that I get this error when running with network:


EAX=ffffffff EBX=80f5b000 ECX=02a2ffff EDX=02a30000
ESI=00000009 EDI=80f30880 EBP=80f30880 ESP=f9cda8a4
EIP=804e20d6 EFL=00010286 [--S--P-] CPL=0 II=0 A20=1 HLT=0
ES =0023 00000000 ffffffff 00cff300
CS =0008 00000000 ffffffff 00cffb00
SS =0010 00000000 ffffffff 00cff300
DS =0023 00000000 ffffffff 00cff300
FS =0030 ffdff000 00001fff ff40f3df
GS =0000 00000000 00000000 00000000
LDT=0000 00000000 00000000 00008000
TR =0028 80042000 000020ab 80008904
GDT=     8003f000 000003ff
IDT=     8003f400 000007ff
CR0=e0010031 CR2=ffffffff CR3=00039000 CR4=000006d8
Unsupported return value: 0xffffffff

It works fine without kqemu, but is slow.

---

### Post by FoolishStar on 2007-06-25
Guys the installer works perfect for me until it trys downloading kqemu, I recieve the following error;

Downloading KQEMU...
--08:50:08--  [http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz)
           => `kqemu-1.3.0pre9.tar.gz'
Connecting to 192.168.2.220:3128... connected.
Proxy request sent, awaiting response... 404 Not Found
08:50:08 ERROR 404: Not Found.

ERROR: Unable to download KQEMU.

I know why this error occurs it is because the qemu people have removed that file, is it possible to change something at my end to sort this problem out?

The current active file at qemu is ; [http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre11.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre11.tar.gz)

I managed to workout how the file is being pulled down, but being a total newb, I cannot work out how to make the correct changes to the code..

Many thanks in advance for your help.
Foolish

---

### Post by FoolishStar on 2007-06-25
I just stopped being an idiot and looked at the variables used in the config and made changes to the install.sh file to include;

KQEMU=1.3.0pre11

Adding this line looks for the newer versions of the kqemu build and then installs perfectly.

Thanks for not answering and making me look more of an idiot!!!

Foolish

---

### Post by bhamail on 2008-02-04
In case it helps anyone else:

I made the changes below to the install script to install qemu0.9.1 and kqemu pre 11 on Ubuntu 6.06 Dapper on AMD64.
After making the obvious updates to the version names of qemu and kqemu, I got an "Invalid parameter..." error. I just removed the parm "--kernel-path" and it's building away now.

Dan


$ diff install_qemu.sh install_qemu.sh.orig
11c11
< QEMU=0.9.1
---
> QEMU=0.8.2
13c13
< KQEMU=1.3.0pre11
---
> KQEMU=1.3.0pre9
206,207c206,207
< #sh ./configure --prefix=/usr --cc=gcc-3.4 --host-cc=gcc-3.4 --kernel-path=/lib/modules/$(uname -r)/build/ || error "Unable to configure QEMU."
< sh ./configure --prefix=/usr --cc=gcc-3.4 --host-cc=gcc-3.4 || error "Unable to configure QEMU."
---
> sh ./configure --prefix=/usr --cc=gcc-3.4 --host-cc=gcc-3.4 --kernel-path=/lib/modules/$(uname -r)/build/ || error "Unable to configure QEMU."
>

---

