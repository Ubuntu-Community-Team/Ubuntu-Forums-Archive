---
title: "Linux kernel drivers problem"
date: 2014-10-19
forum: New to Ubuntu
---

### Post by ahmed20 on 2014-10-19
Hey, Guys. i am new to Ubuntu and i am having a problem with updating the linux kernel drivers. i tried to update the software from 12.04 to 14.04, but then it showed and error so i decided to go and update what's need to be updated (no idea why i did that). So, now i am left with this one update than i can't complete, and for some reason, i have no wireless access, so i'm stuck with an ethenet cable. i would be so grateful for some help to get my **** together. i would also like to know how to install Ubuntu 14.04 without getting much problems. 

Here is what i get:
[HR][/HR]installArchives() failed: (Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 205568 files and directories currently installed.) 
Preparing to replace linux-firmware 1.79.1 (using .../linux-firmware_1.79.18_all.deb) ... 
Unpacking replacement linux-firmware ... 
dpkg: error processing /var/cache/apt/archives/linux-firmware_1.79.18_all.deb (--unpack): 
 trying to overwrite '/lib/firmware/ar3k/AthrBT_0x31010000.dfu', which is also in package bt-dw1705-firmware 0.1 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-firmware_1.79.18_all.deb 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bashing-om on 2014-10-19
ahmed20; Hi Welcome to the forum .

Does not look too bad, Maybe just a bit of corruption in a control file.
As you can see posting unformatted output is difficult to read, so -> code tags !

As a place to start/confirm, please post the outputs - Between Code Tags - of terminal commands :
```

sudo apt-get update
sudo apt-get upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we can see the state of the package manager system and get an idea of how to fix it.

Once the 12.04 system is stable, we then proceed with the release-upgrade to 14.04.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by ahmed20 on 2014-10-19
here is what i got 
```
Ign cdrom://[Ubuntu 12.04 _Precise_ - Build amd64 LIVE Binary 20130203-13:50] precise Release.gpg
Ign cdrom://[Ubuntu 12.04 _Precise_ - Build amd64 LIVE Binary 20130203-13:50] precise Release             
Ign cdrom://[Ubuntu 12.04 _Precise_ - Build amd64 LIVE Binary 20130203-13:50] precise/main amd64 Packages/DiffIndex
Ign cdrom://[Ubuntu 12.04 _Precise_ - Build amd64 LIVE Binary 20130203-13:50] precise/main TranslationIndex
Err cdrom://[Ubuntu 12.04 _Precise_ - Build amd64 LIVE Binary 20130203-13:50] precise/main i386 Packages  
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://[Ubuntu 12.04 _Precise_ - Build amd64 LIVE Binary 20130203-13:50] precise/main Translation-en_US
Ign cdrom://[Ubuntu 12.04 _Precise_ - Build amd64 LIVE Binary 20130203-13:50] precise/main Translation-en 
Hit http://archive.ubuntu.com precise Release.gpg                                                         
Hit http://archive.ubuntu.com precise-updates Release.gpg                                                 
Get:1 http://archive.ubuntu.com precise-backports Release.gpg [198 B]
Hit http://archive.ubuntu.com precise-security Release.gpg                      
Hit http://dell.archive.canonical.com precise-dell Release.gpg       
Hit http://oem.archive.canonical.com precise-oem-sp1 Release.gpg     
Hit http://archive.ubuntu.com precise Release  
Hit http://dell.archive.canonical.com precise-dell Release                                  
Hit http://oem.archive.canonical.com precise-oem-sp1 Release                                
Hit http://archive.ubuntu.com precise-updates Release                 
Get:2 http://archive.ubuntu.com precise-backports Release [50.8 kB]                         
Hit http://dell.archive.canonical.com precise-dell/public Sources            
Hit http://oem.archive.canonical.com precise-oem-sp1/public Sources          
Hit http://dell.archive.canonical.com precise-dell/public amd64 Packages                         
Hit http://dell.archive.canonical.com precise-dell/public i386 Packages                           
Ign http://dell.archive.canonical.com precise-dell/public TranslationIndex                        
Hit http://oem.archive.canonical.com precise-oem-sp1/public amd64 Packages     
Hit http://oem.archive.canonical.com precise-oem-sp1/public i386 Packages                         
Ign http://oem.archive.canonical.com precise-oem-sp1/public TranslationIndex                      
Hit http://archive.ubuntu.com precise-security Release                         
Hit http://archive.ubuntu.com precise/main Sources                    
Hit http://archive.ubuntu.com precise/restricted Sources              
Hit http://archive.ubuntu.com precise/universe Sources                
Hit http://archive.ubuntu.com precise/multiverse Sources              
Hit http://archive.ubuntu.com precise/main amd64 Packages                                                 
Hit http://archive.ubuntu.com precise/restricted amd64 Packages                                           
Hit http://archive.ubuntu.com precise/universe amd64 Packages                               
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages                             
Hit http://archive.ubuntu.com precise/main i386 Packages                                                  
Hit http://archive.ubuntu.com precise/restricted i386 Packages                          
Hit http://archive.ubuntu.com precise/universe i386 Packages      
Hit http://archive.ubuntu.com precise/multiverse i386 Packages    
Hit http://archive.ubuntu.com precise/main TranslationIndex       
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex 
Hit http://archive.ubuntu.com precise/restricted TranslationIndex 
Hit http://archive.ubuntu.com precise/universe TranslationIndex   
Hit http://archive.ubuntu.com precise-updates/main Sources        
Hit http://archive.ubuntu.com precise-updates/restricted Sources  
Hit http://archive.ubuntu.com precise-updates/universe Sources    
Hit http://archive.ubuntu.com precise-updates/multiverse Sources  
Hit http://archive.ubuntu.com precise-updates/main amd64 Packages 
Hit http://archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://archive.ubuntu.com precise-updates/multiverse amd64 Packages                   
Hit http://archive.ubuntu.com precise-updates/main i386 Packages                          
Hit http://archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex 
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex
Get:3 http://archive.ubuntu.com precise-backports/main Sources [5,551 B]
Get:4 http://archive.ubuntu.com precise-backports/restricted Sources [14 B]                               
Get:5 http://archive.ubuntu.com precise-backports/universe Sources [40.2 kB]                              
Get:6 http://archive.ubuntu.com precise-backports/multiverse Sources [5,737 B]                    
Get:7 http://archive.ubuntu.com precise-backports/main amd64 Packages [6,617 B]                           
Get:8 http://archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]                        
Get:9 http://archive.ubuntu.com precise-backports/universe amd64 Packages [43.1 kB]            
Ign http://dell.archive.canonical.com precise-dell/public Translation-en_US                               
Ign http://oem.archive.canonical.com precise-oem-sp1/public Translation-en_US                       
Get:10 http://archive.ubuntu.com precise-backports/multiverse amd64 Packages [5,405 B]
Get:11 http://archive.ubuntu.com precise-backports/main i386 Packages [6,620 B]                           
Get:12 http://archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]                        
Get:13 http://archive.ubuntu.com precise-backports/universe i386 Packages [42.9 kB]                       
Get:14 http://archive.ubuntu.com precise-backports/multiverse i386 Packages [5,399 B]                     
Ign http://dell.archive.canonical.com precise-dell/public Translation-en                                  
Ign http://oem.archive.canonical.com precise-oem-sp1/public Translation-en                           
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex          
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://archive.ubuntu.com precise-security/main Sources          
Hit http://archive.ubuntu.com precise-security/restricted Sources    
Hit http://archive.ubuntu.com precise-security/universe Sources
Hit http://archive.ubuntu.com precise-security/multiverse Sources
Hit http://archive.ubuntu.com precise-security/main amd64 Packages
Hit http://archive.ubuntu.com precise-security/restricted amd64 Packages
Hit http://archive.ubuntu.com precise-security/universe amd64 Packages
Hit http://archive.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com precise-security/main i386 Packages
Hit http://archive.ubuntu.com precise-security/restricted i386 Packages
Hit http://archive.ubuntu.com precise-security/universe i386 Packages
Hit http://archive.ubuntu.com precise-security/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-security/main TranslationIndex
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex
Hit http://archive.ubuntu.com precise/main Translation-en
Hit http://archive.ubuntu.com precise/multiverse Translation-en
Hit http://archive.ubuntu.com precise/restricted Translation-en
Hit http://archive.ubuntu.com precise/universe Translation-en
Hit http://archive.ubuntu.com precise-updates/main Translation-en
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://archive.ubuntu.com precise-updates/universe Translation-en
Hit http://archive.ubuntu.com precise-backports/main Translation-en
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://archive.ubuntu.com precise-backports/universe Translation-en
Hit http://archive.ubuntu.com precise-security/main Translation-en
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en
Hit http://archive.ubuntu.com precise-security/restricted Translation-en
Hit http://archive.ubuntu.com precise-security/universe Translation-en
Fetched 213 kB in 3s (61.4 kB/s)              
W: Failed to fetch cdrom://[Ubuntu 12.04 _Precise_ - Build amd64 LIVE Binary 20130203-13:50]/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
ahmed@ahmed-Inspiron-3537:~$ 

```



```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ahmed@ahmed-Inspiron-3537:~$ 

```

---

### Post by Bashing-om on 2014-10-19
ahmed20; Great !

Looking good,

There is no need to have the CDrom access enabled ( old old old software sources ) ; Disable in Software Sources.
Then let's make sure you are ready to do a release upgrade.
a) screen saver - if any - is disabled
b) disable all 3rd party PPA's ( yeah the installer might take care of it, sometimes though that is not the fact)
c) If you are running a proprietary graphics driver, revert it back to open source.

If you are unsure, and require guided assistance:
post back:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
once all the above is done:
release upgrade !
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
Then, IF, no errors are reported:
```

sudo do-release-upgrade

```
ELSE: post back those outputs and let's fix the system prior to proceeding.

I do expect, however, this to be
[INDENT][INDENT]as smooth as the fur on a Calico cat's back
[/INDENT][/INDENT]

---

### Post by ahmed20 on 2014-10-19
i just want to make sure of it


```
 1    # deb cdrom:[Ubuntu 12.04 _Precise_ - Build amd64 LIVE Binary 20130203-13:50]/ precise main
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://archive.ubuntu.com/ubuntu precise main restricted
     6    deb-src http://archive.ubuntu.com/ubuntu precise main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
    11    deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://archive.ubuntu.com/ubuntu precise universe
    17    deb-src http://archive.ubuntu.com/ubuntu precise universe
    18    deb http://archive.ubuntu.com/ubuntu precise-updates universe
    19    deb-src http://archive.ubuntu.com/ubuntu precise-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://archive.ubuntu.com/ubuntu precise multiverse
    27    deb-src http://archive.ubuntu.com/ubuntu precise multiverse
    28    deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
    29    deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
    37    deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
    38    
    39    deb http://archive.ubuntu.com/ubuntu precise-security main restricted
    40    deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
    41    deb http://archive.ubuntu.com/ubuntu precise-security universe
    42    deb-src http://archive.ubuntu.com/ubuntu precise-security universe
    43    deb http://archive.ubuntu.com/ubuntu precise-security multiverse
    44    deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu precise partner
    51    # deb-src http://archive.canonical.com/ubuntu precise partner
    52    
    53    ## Uncomment the following two lines to add software from Ubuntu's
    54    ## 'extras' repository.
    55    ## This software is not part of Ubuntu, but is offered by third-party
    56    ## developers who want to ship their latest software.
    57    # deb http://extras.ubuntu.com/ubuntu precise main
    58    # deb-src http://extras.ubuntu.com/ubuntu precise main
ahmed@ahmed-Inspiron-3537:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/precise-dell.list <==
deb http://dell.archive.canonical.com/updates/ precise-dell public
deb-src http://dell.archive.canonical.com/updates/ precise-dell public

==> /etc/apt/sources.list.d/precise-dell.list.distUpgrade <==
deb http://dell.archive.canonical.com/updates/ precise-dell public
deb-src http://dell.archive.canonical.com/updates/ precise-dell public

==> /etc/apt/sources.list.d/precise-dell.list.save <==
deb http://dell.archive.canonical.com/updates/ precise-dell public
deb-src http://dell.archive.canonical.com/updates/ precise-dell public

==> /etc/apt/sources.list.d/precise-oem-sp1.list <==
deb http://oem.archive.canonical.com/updates/ precise-oem-sp1 public
deb-src http://oem.archive.canonical.com/updates/ precise-oem-sp1 public

==> /etc/apt/sources.list.d/precise-oem-sp1.list.distUpgrade <==
deb http://oem.archive.canonical.com/updates/ precise-oem-sp1 public
deb-src http://oem.archive.canonical.com/updates/ precise-oem-sp1 public

==> /etc/apt/sources.list.d/precise-oem-sp1.list.save <==
deb http://oem.archive.canonical.com/updates/ precise-oem-sp1 public
deb-src http://oem.archive.canonical.com/updates/ precise-oem-sp1 public
ahmed@ahmed-Inspiron-3537:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
    Subsystem: Dell Device [1028:05ea]
    Kernel driver in use: i915
    Kernel modules: i915, i915_hsw
```

---

### Post by Bashing-om on 2014-10-19
ahmed20; Hey,

Looks good.
The CDrom is now disabled;
And:
> 
[http://dell.archive.canonical.com/updates/](http://dell.archive.canonical.com/updates/)

Does in fact have support in 'trusty'. I think it is safe now to proceed.
DO it.
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
Then, IF, no errors are reported:
```

sudo do-release-upgrade

```

[INDENT][INDENT]small steps, no worries
[INDENT][INDENT][INDENT]get there
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ahmed20 on 2014-10-19
it proceeded with no errors but with the second step this showed up

```
Checking for a new Ubuntu release
No new release found
```

---

### Post by Bashing-om on 2014-10-19
ahmed20; OK,

No reason to panic yet.
What returns:
```

cat /etc/update-manager/release-upgrades

``` and let's see what is set to upgrade to.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by ahmed20 on 2014-10-19
Here 

```
# Default behavior for the release upgrader.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
Prompt=never


```

---

### Post by Bashing-om on 2014-10-19
ahmed20; Ah haww !

We now know the why !
> 
Prompt=never


Are you comfortable using a text editor to edit this system file ?

I am sure there is a way to reset this field to 'lts'. I do not however, run the GUI and I can not give direct specific advise on the where to change this field in the GUI.

We CAN do this in terminal - and with a text editor - so you do know what you are doing.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]more than 1 path to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ahmed20 on 2014-10-19
the reply is vvv

---

### Post by ahmed20 on 2014-10-19
Bashing-om,

 i think you do get the hang on how desperate i am from how i wrote the code when posting the thread lol. I have no previous experience with text editors, but i am willing to do whatever it takes to fix this situation. So, should i download a text editor, and what should i do then?

---

### Post by Bashing-om on 2014-10-19
ahmed20; Hey !

I am all for advancing you in the learning curve and making you the more comfortable with the operating system.

You do have the text editor 'gedit' installed by default. It is a WYSIWYG  (What You See Is What You Get) GUI editor - as opposed to say 'nano' - a terminal editor.

SO we are going to edit a file using 'gedit' as the editor of choice.
Standard operating procedure is to make a backup of any file one edits - never can tell what might perchance and Murphy's Law always applies.
Terminal command:
```

sudo cp /etc/update-manager/release-upgrades /etc/update-manager/release-upgrades-orig

```
which does that for us, making a backup file named "/etc/update-manager/release-upgrades-orig" .

Now to edit our file:
```

gksudo gedit /etc/update-manager/release-upgrades

```
enter password when prompted.

Our target file is now open - with the elevated privileges to change a system file.
Arrow down to the line " Prompt=never " and arrow over to the start of 'never' ;
type lts, and carefully with the delete key remove the letters n e v e r . Stop when the final 'r' is deleted ( we want that invisible end of line format to remain intact). Changing never to Long Term Support , Now the installer has something to work with.
so that the result is:
> 
Prompt=lts

save the file - tool bar "save', and exit out of the editor back to terminal.

Now let's do it:
Make sure the system is up to date, yeah, you just did it, do it again .. as there may have been security updates since the last run, just run the update routine once more.
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
and again ==>Then, IF, no errors are reported:
```

sudo do-release-upgrade

```

[INDENT][INDENT]see ya
[INDENT][INDENT][INDENT]on the other side
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ahmed20 on 2014-10-19
Bashing-om, 

it went smooth this time, but at the end it asked whether to continue or press "d" for details. I pressed it and then dozen lines showed up with ( END) in the last line. So, did i do something wrong or was that supposed to happen? what should i do next?

---

### Post by Bashing-om on 2014-10-19
ahmed20; Humm ...

Do not have a clue ! If you do not provide the referenced outputs, I can not place into context to know anything.

let's get an idea of where we stand:
```

lsb_release -a
cat /etc/issue
uname -a
cat -n /etc/apt/sources.list

```

I do hope all shows 14.04 !

[INDENT][INDENT]so a tale is told
[/INDENT][/INDENT]

---

### Post by ahmed20 on 2014-10-20
I think it is over now. THANK YOU SO MUCH. Is there anything i should do now?

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
ahmed@ahmed-Inspiron-3537:~$ cat /etc/issue
Ubuntu 14.04.1 LTS \n \l

ahmed@ahmed-Inspiron-3537:~$ uname -a
Linux ahmed-Inspiron-3537 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
ahmed@ahmed-Inspiron-3537:~$ cat -n /etc/apt/sources.list


```

---

### Post by Bashing-om on 2014-10-20
ahmed20; Hi !

> 
I think it is over now. THANK YOU SO MUCH. Is there anything i should do now?


I think too you are in good shape, and good to go.

If :
```

sudo apt-get update
sudo apt-get upgrade

```
runs clean, Then yeah, all done and over with.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]I wish
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ahmed20 on 2014-10-20
do you mean update or u[pdate? in case you meant update, this is what i got:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-22 linux-headers-3.5.0-22-generic
  linux-image-3.5.0-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Bashing-om on 2014-10-20
ahmed20l Yeah ; typo ;

Corrected. ( a pet happy kitten in the lap does not help in all respects)

I will be interested to see if/how "autoremove" handles those old kernels.
What results:
```

sudo apt-get autoremove

```

I bet things are 
[INDENT][INDENT]finer than a frog's hair
[/INDENT][/INDENT]

---

### Post by ahmed20 on 2014-10-20
Yeah, i know all about kittens lol. Anyways, here is what happened:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.5.0-22 linux-headers-3.5.0-22-generic
  linux-image-3.5.0-22-generic
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 226 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 256228 files and directories currently installed.)
Removing linux-headers-3.5.0-22-generic (3.5.0-22.34~precise1) ...
Removing linux-headers-3.5.0-22 (3.5.0-22.34~precise1) ...
Removing linux-image-3.5.0-22-generic (3.5.0-22.34~precise1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
dkms: removing: alsa-hda-lts-quantal 0.1 (3.5.0-22-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  alsa-hda-lts-quantal
Version: 0.1
Kernel:  3.5.0-22-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


snd-hda-codec-idt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




snd-hda-codec-realtek.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




snd-hda-codec-conexant.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




snd-hda-codec-ca0132.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




snd-hda-codec-si3054.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




snd-hda-codec-hdmi.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




snd-hda-codec-cirrus.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




snd-hda-codec-via.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




snd-hda-codec-ca0110.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




snd-hda-codec-analog.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




snd-hda-intel.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




snd-hda-codec-cmedia.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




snd-hda-codec.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod.....


DKMS: uninstall completed.
dkms: removing: intel-i915-backport-3.8-dkms 3.8.6.0 (3.5.0-22-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  intel-i915-backport-3.8-dkms
Version: 3.8.6.0
Kernel:  3.5.0-22-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


i915.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
dkms: removing: oem-bt-dw1705 0.1 (3.5.0-22-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  oem-bt-dw1705
Version: 0.1
Kernel:  3.5.0-22-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


btusb.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




ath3k.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
dkms: removing: oem-wireless-ath9k-3.9-rc4-2 0.1 (3.5.0-22-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  oem-wireless-ath9k-3.9-rc4-2
Version: 0.1
Kernel:  3.5.0-22-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


ath9k.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




ath9k_common.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




ath9k_htc.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




ath9k_hw.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




ath.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




compat.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




mac80211.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rfkill-regulator.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




cfg80211.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.


------------------------------
Deleting module version: 0.1
completely from the DKMS tree.
------------------------------
Done.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.5.0-55-generic
Found initrd image: /boot/initrd.img-3.5.0-55-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done



```

---

### Post by Bashing-om on 2014-10-20
ahmed20; Humm ??


Just do not know .. a lot of DKMS .ko files removed ! Quite likely no longer needed.
But I do now know that 'autoremove' will remove the 3.5 kernel images .

What returns:
```

sudo dkms status

```

Now reboot, and tell me all sound (video) and graphics are good.

[INDENT][INDENT]most likely YES
[/INDENT][/INDENT]

---

### Post by ahmed20 on 2014-10-20
```
alsa-hda-lts-quantal, 0.1, 3.5.0-55-generic, x86_64: installedfglrx, 13.350.1, 3.13.0-37-generic, x86_64: installed
fglrx, 13.350.1, 3.5.0-55-generic, x86_64: installed
intel-i915-backport-3.8-dkms, 3.8.6.0, 3.5.0-55-generic, x86_64: installed
oem-bt-dw1705, 0.1, 3.5.0-55-generic, x86_64: built



```

All cool now?

---

### Post by Bashing-om on 2014-10-20
ahmed20;

Well, I am all cool with it IF you are running hybrid graphics ( Intel and ATI ) .. and you have rebooted, and ALL workie great.

looks doable
[INDENT][INDENT]if it ain't broke, do not fix it
[/INDENT][/INDENT]

---

### Post by ahmed20 on 2014-10-20
But i don't think i have hybrid graphics. It is only ATI. So, what should i do?
My laptop is Dell Inspiron 3537

---

### Post by Bashing-om on 2014-10-20
ahmed20; Well;

this:
> 
intel-i915-backport-3.8-dkms

makes me consider that you also have Intel graphics chips. 
I go check the specs on the machine.
But if all is working presently .. I would not worry .

EDIT: Yepper !
Hybrid graphics:
> 
Video 3
Inspiron 3521 Inspiron 3537
Controller:
Integrated Intel HD Graphics 4000 Intel HD Graphics 
5100/4200/4400 series
Discrete &#8226;	 AMD Radeon HD 7670M 
&#8226;	 AMD Radeon HD 8730M
&#8226;	 AMD Radeon HD 8670M
&#8226;	 AMD Radeon HD 8850M



[INDENT][INDENT]don't hurt to look
[/INDENT][/INDENT]

---

