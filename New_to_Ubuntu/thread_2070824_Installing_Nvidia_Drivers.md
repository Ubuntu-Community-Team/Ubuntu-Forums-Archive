---
title: "Installing Nvidia Drivers"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by Vesnog on 2012-10-13
Greetings,

I need to install the drivers for my Nvidia Geforce 540M video card in order to install Bumblebee. How can I do so? 

Thanks

P.S: I tried some methods I found on the net up to no avail.

---

### Post by DogMatix on 2012-10-13
Have you tried the [Additional Drivers]("https://apps.ubuntu.com/cat/applications/precise/jockey-gtk/").



[Bumblebee]("https://wiki.ubuntu.com/Bumblebee") on Ubuntu wiki may help too

---

### Post by Vesnog on 2012-10-13
I followed the instructions given in the following URL: 
[https://wiki.ubuntu.com/Bumblebee#Installation ]("https://wiki.ubuntu.com/Bumblebee#Installation")

1) However, when I try to launch Nvidia X Server settings I get the screen that I have attached to this post. I think this means I have the drivers installed but they are not working.

2) I get the following result in the terminal when I try to install Bumblebee:

```

user@Vesnog:~$ sudo apt-get install bumblebee bumblebee-nvidia 
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bumblebee
E: Unable to locate package bumblebee-nvidia
```

3) I am unable to run glxgears. When I try it, I get the following:
```

user@Vesnog:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

4) Also I am experiencing a weird issue related with Google Chrome. The problem is as follows: When I try to move a tab from one position to another(say moving tab 2 from left of tab 3 to right of it), instantly the browser opens a new window and I am unable to put the tab back to its place which is very frustrating.

Thanks in advance for any suggestions or remedies.


P.S:I have used sudo apt-get update command many times up to no avail. Some applications refuse to get installed by giving similar error messages.

---

### Post by Vesnog on 2012-10-13
I tried changing the Unity Desktop by logging out, however it failed and I am stuck with a resolution of 640x480 and cannot change it. How can I change it ?

---

### Post by Vesnog on 2012-10-13
I have resolved the lowered resolution issue by consulting the 7th post following URL:

[http://ubuntuforums.org/showthread.php?t=1966987](http://ubuntuforums.org/showthread.php?t=1966987)

But the above mentioned problems persist.

---

### Post by NikTh on 2012-10-13
Can you post the results of these commands ? 

```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
``````
apt-cache policy nvidia-current
``` 
```
lspci -nnk | grep -iA2 vga
```

---

### Post by Vesnog on 2012-10-14
[SIZE=3]I am posting some information relating the problem:[/SIZE]

@Vesnog:~$ dpkg-query -l nvidia*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  nvidia-180-mod <none>         (no description available)
un  nvidia-185-mod <none>         (no description available)
ii  nvidia-common  1:0.2.44.2     Find obsolete NVIDIA drivers
ii  nvidia-current 304.51-0ubuntu NVIDIA binary Xorg driver, kernel module and
un  nvidia-current <none>         (no description available)
ii  nvidia-current 295.49-0ubuntu NVIDIA binary Xorg driver, kernel module and
ii  nvidia-setting 304.51-0ubuntu Tool of configuring the NVIDIA graphics driv
ii  nvidia-setting 295.33-0ubuntu Tool of configuring the NVIDIA graphics driv

[SIZE=3]The part of the output of the command "sudo lspci -v" is as follows:[/SIZE]

01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 050e
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 3000 [size=128]
    Expansion ROM at f1000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current_updates, nvidia, nouveau, nvidiafb

---

### Post by Vesnog on 2012-10-14
> **NikTh said:**
> Can you post the results of these commands ? 

```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
``````
apt-cache policy nvidia-current
``````
lspci -nnk | grep -iA2 vga
```

Excuse me for missing you post earlier. Here are the outputs of the commands:
[SIZE=3]
1.Command[/SIZE]
/etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise main restricted
     6    deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    11    deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise universe
    17    deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise universe
    18    deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-updates universe
    19    deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise multiverse
    27    deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise multiverse
    28    deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    29    deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    37    deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    38    
    39    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    40    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    41    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    42    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    43    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    44    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    51    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    56    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

/etc/apt/sources.list.d/google-talkplugin.list

     1    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2    # You may comment out this entry, but any other modifications may be lost.
     3    deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

/etc/apt/sources.list.d/webupd8team-java-precise.list

     1    deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
     2    deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main

/etc/apt/sources.list.d/google-chrome.list

     1    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2    # You may comment out this entry, but any other modifications may be lost.
     3    deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list

     1    deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main
     2    deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main




[SIZE=3]2.Co[SIZE=3]mmand[/SIZE][/SIZE]
nvidia-current:
  Installed: 304.51-0ubuntu1~precise~xup1
  Candidate: 304.51-0ubuntu1~precise~xup1
  Version table:
 *** 304.51-0ubuntu1~precise~xup1 0
        500 [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) precise/main i386 Packages
        100 /var/lib/dpkg/status
     295.40-0ubuntu1.1 0
        500 [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-updates/restricted i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted i386 Packages
     295.40-0ubuntu1 0
        500 [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise/restricted i386 Packages

[SIZE=3]3.Command[/SIZE]
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Dell Device [1028:050e]
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 540M] [10de:0df4] (rev a1)
    Subsystem: Dell Device [1028:050e]
    Kernel driver in use: nvidia

---

### Post by sandyd on 2012-10-14
You are missing the bumblebee ppa
```

sudo add-apt-repository ppa:bumblebee/stable

```

---

### Post by Vesnog on 2012-10-14
> **sandyd said:**
> You are missing the bumblebee ppa
```

sudo add-apt-repository ppa:bumblebee/stable

```

I added it for more than once.

---

### Post by sandyd on 2012-10-14
> **Vesnog said:**
> I added it for more than once.

thats weird - its not in the above list

---

### Post by NikTh on 2012-10-14
> **Vesnog said:**
> I added it for more than once.

Add it again with the way @sandyd suggested. It is not in sources.list 

Thanks

---

### Post by Meschi on 2012-10-14
Did you run apt-get update after adding the ppa? I forgot that and was wondering for a while :)

---

### Post by Vesnog on 2012-10-15
I managed to get it done, by first installing Ironhide then installing Bumblebee afterwards with the command:

sudo apt-get install bumblebee

Notice that I excluding bumblebee-nvidia seemed to have resolved the situation and I think I already got the Nvidia drivers then. I am marking the thread as solved, thanks everyone for help.

---

