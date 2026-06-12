---
title: "Intel drivers (firmware) up to date"
date: 2021-08-14
forum: New to Ubuntu
---

### Post by coutte-chris on 2021-08-14
Dear all,

I am on Ubuntu 20.04 LTS up to date, freshly re-installed.

I just updated my system and I saw the system complaining about a missing missing firmware (tgl_huc_7.5.0.bin).[INDENT]/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.10.0-1038-oem
W: Possible missing firmware /lib/firmware/i915/tgl_huc_7.5.0.bin for module i915
W: Possible missing firmware /lib/firmware/i915/tgl_huc_7.5.0.bin for module i915
[/INDENT]
 

I am OK to update that firmware , with the command "update-initramfs".

But I checked the following link: [INTEL Repository of firmware]("https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/i915") and I found newer INTEL firmwares to prevent bugs ! Such as:

[LIST]
[*]             tgl_huc_7.5.0.bin - 2020-08-13 
[*]tgl_huc_7.9.3.bin - 2021-06-29 
[/LIST]
 


** So: How to tell our Ubuntu that all INTEL firmware files needs to be updated ?**

[LIST]
[*]             tgl_dmc_ver2_12.bin 
[*]tgl_guc_62.0.0.bin 
[*]tgl_huc_7.9.3.bin 
[/LIST]
 

Note: even the file "tgl_guc_49.0.1.bin" from 24-Nov-2020 (8 months ago)  is missing and the system is NOT complaining about it. It would be good  to be able to install them.

Cheers

-------------------------------------------------------------------------------------
Edit for partial answer provided : 
The issue was broken down into 2 parts :

[LIST]
[*][Missing firmware files, in Ubuntu 20.04 LTS, for initramfs, when it loads i915]("https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1939986")
[*][Module i915 is not updated, in Ubuntu 20.04 LTS]("https://bugs.launchpad.net/ubuntu/+source/linux-oem-5.10/+bug/1939989")
[/LIST]

The missing firmware is in the linux-firmware package [here (from System76)]("https://launchpad.net/~system76-dev/+archive/ubuntu/stable") [https://launchpad.net/~system76-dev/+archive/ubuntu/stable](https://launchpad.net/~system76-dev/+archive/ubuntu/stable)
See [monkeybrain20122 post here]("https://ubuntuforums.org/showthread.php?t=2465900&p=14053940#post14053940").

I still don't know how to tell the i915 nodule that new firmware files are available.

---

### Post by mikewhatever on 2021-08-14
Can you add the output of "lscpu | grep Model".
Apparenly, Intel's firmware is from the linux-firmware package. In 20.04 there is only tgl_huc_7.3.0.bin, and I am not sure when it gets updated, because, obviously, it needs to be tested first.
One way "to tell our Ubuntu that all INTEL firmware files needs to be updated" is to file a bug report on launchpad.net

---

### Post by coutte-chris on 2021-08-15
Hi Mike, thanks for the reply , 

> **mikewhatever said:**
> Can you add the output of "lscpu | grep Model".

as expected I have an Intel Tiger Lake (tgl) processor. 
the command "lscpu | grep Model"
gives:
> Model:                           140
Model name:                      11th Gen Intel(R) Core(TM) i7-1165G7 @ 2.80GHz

Cheers

---

### Post by coutte-chris on 2021-08-15
> **mikewhatever said:**
> One way "to tell our Ubuntu that all INTEL firmware files needs to be updated" is to file a bug report on launchpad.net
Hi,
This is a good suggestion , I'll keep you all posted about this.
Also , do you think , there is a possibility to update , via a PPA or something the linux-firmware package ?
I tried to look for it , but I do not know where to start TBH. 

Cheers

---

### Post by coutte-chris on 2021-08-15
Hi, 
I have seen a Debian package : [URL="https://packages.debian.org/buster/firmware-misc-nonfree"]
[https://packages.debian.org/buster-backports/firmware-misc-nonfree](https://packages.debian.org/buster-backports/firmware-misc-nonfree)
[/URL]
Is this something that can be used ?
Cheers

---

### Post by coutte-chris on 2021-08-15
> **mikewhatever said:**
>  One way "to tell our Ubuntu that all INTEL firmware files needs to be updated" is to file a bug report on launchpad.net
Thanks for that. 
I have broken down the problem into 2 parts : 

[LIST=1]
[*]Missing firmware files, in Ubuntu 20.04 LTS, for initramfs, when it loads i915 : [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1939986](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1939986) 
[*]Module i915 is not updated, in Ubuntu 20.04 LTS: [https://bugs.launchpad.net/ubuntu/+source/linux-oem-5.10/+bug/1939989](https://bugs.launchpad.net/ubuntu/+source/linux-oem-5.10/+bug/1939989) 
[/LIST]
Hope this may help someone else. 
Cheers

---

### Post by coutte-chris on 2021-08-16
> **coutte-chris said:**
> This is a good suggestion , I'll keep you all posted about this.

FYI: no update yet on the bugs . But I can see that many bugs on launchpad, around modules have been left open. :(

---

### Post by mikewhatever on 2021-08-16
There are many more bugs then people able to fix them. That said, have some patience, the time gap between post #6 and post #7 is only 18 hours.

---

### Post by monkeybrain20122 on 2021-08-16
The missing firmware is in the linux-firmware package here [https://launchpad.net/~system76-dev/+archive/ubuntu/stable](https://launchpad.net/~system76-dev/+archive/ubuntu/stable)

---

### Post by fyfe54 on 2021-08-17
Just today updated my Ubuntu 21.04 and this update was in there:
Unpacking linux-firmware (1.197.3) over (1.197.2)

---

### Post by coutte-chris on 2021-08-17
> **fyfe54 said:**
> Just today updated my Ubuntu 21.04 and this update was in there:
Unpacking linux-firmware (1.197.3) over (1.197.2)

Hi @fyfe54, you are right , in Ubuntu 21.04 (hirsute) , there is an updated version of the INTEL firmware. 
Package: [linux-firmware (1.197.3)]("https://packages.ubuntu.com/hirsute-updates/linux-firmware") contains [these files]("https://packages.ubuntu.com/hirsute-updates/all/linux-firmware/filelist") : 
[LIST]
[*]i915/tgl_dmc_ver2_04.bin       - 2019-09-13 
[*]i915/tgl_dmc_ver2_06.bin       - 2020-03-04 
[*]i915/tgl_dmc_ver2_08.bin       - 2020-08-13 
[/LIST]


[LIST]
[*]i915/tgl_guc_35.2.0.bin       - 2019-11-06 
[*]i915/tgl_guc_49.0.1.bin       - 2020-11-24    i915: Add GuC firmware v49.0.1 for all platforms 
[/LIST]


[LIST]
[*]i915/tgl_huc_7.0.12.bin       - 2020-03-04 
[*]i915/tgl_huc_7.0.3.bin       - 2019-11-06 
[*]i915/tgl_huc_7.5.0.bin       - 2020-08-13    i915: Add HuC firwmare v7.5.0 for TGL 
[/LIST]

But , you are still missing the following: 

[LIST]
[*]i915/tgl_dmc_ver2_12.bin         2021-07-28    i915: Add v2.12 DMC for TGL 
[*]i915/tgl_guc_62.0.0.bin         2021-06-29    firmware/i915/guc: Add GuC v62.0.0 for all platforms 
[*]i915/tgl_huc_7.9.3.bin         2021-06-29    firmware/i915/guc: Add HuC v7.9.3 for TGL & DG1 
[/LIST]
(Files released 6 weeks ago)

So it's slightly better on Ubuntu 21.04 (hirsute) , but there is room for improvement.

From my POV , this is especially important when we are dealing with new hardware , with quick turnarounds from the vendors. 
Hope you see what I mean.

---

### Post by coutte-chris on 2021-08-17
> **fyfe54 said:**
> Just today updated my Ubuntu 21.04 and this update was in there:
Unpacking linux-firmware (1.197.3) over (1.197.2)
That being said :
Have you tried to pay attention to your kernel updates ? (or Do you use the update interface HMI ?)
Because , I was wondering if your ```
update-initramfs -u
``` would complain about one of these 3 newer files, being missing : 

[LIST]
[*]i915/tgl_dmc_ver2_12.bin 
[*]i915/tgl_guc_62.0.0.bin 
[*]i915/tgl_huc_7.9.3.bin 
[/LIST]
(if , you also have a Tiger Lake processor)

Cheers

---

### Post by coutte-chris on 2021-08-17
> **monkeybrain20122 said:**
> The missing firmware is in the linux-firmware package here [https://launchpad.net/~system76-dev/+archive/ubuntu/stable](https://launchpad.net/~system76-dev/+archive/ubuntu/stable)

Hi @monkeybrain20122, 
Thank you for that:
[LIST]
[*]Seeing this PPA is maintained by System76 is kinda reassuring. 
[*]Using this PPA would bring a similar set of files as @fyfe54's linux-firmware (1.197.3)
[LIST]
[*]i.e still missing the latest stuff , but already a good update of the firmware files. 
[/LIST]
  
[/LIST]
So thanks for that.

2 questions, if you can indulge me: 
[LIST=1|INDENT=1]
[*]To help me in the future, Could you tell me how you found that PPA ?
[LIST=1]
[*]I have not found a way to search for a PPA based on a file , as an input 
[*]or is it just because , you are already using it... 
[/LIST]
  
[*]Your suggestion solves the first point "Missing firmware files, in Ubuntu 20.04 LTS"
[LIST=1]
[*]But, I am still wondering how the modules work. or how to tell the i915 module that there are new firmware files to load? 
[*]if you see what I mean. 
[/LIST]
  
[/LIST]

Anyway , thank you both for your insight , this is already a great progress.

---

### Post by monkeybrain20122 on 2021-08-17
> **coutte-chris said:**
> Hi @monkeybrain20122, 
Thank you for that:
[LIST]
[*]Seeing this PPA is maintained by System76 is kinda reassuring. 
[*]Using this PPA would bring a similar set of files as @fyfe54's linux-firmware (1.197.3)
[LIST]
[*]i.e still missing the latest stuff , but already a good update of the firmware files. 
[/LIST]
      
[/LIST]
So thanks for that.

2 questions, if you can indulge me: 
[LIST=1|INDENT=1]
[*]To help me in the future, Could you tell me how you found that PPA ?
[LIST=1]
[*]I have not found a way to search for a PPA based on a file , as an input 
[*]or is it just because , you are already using it... 
[/LIST]
  
[*]Your suggestion solves the first point "Missing firmware files, in Ubuntu 20.04 LTS"
[LIST=1]
[*]But, I am still wondering how the modules work. or how to tell the i915 module that there are new firmware files to load? 
[*]if you see what I mean. 
[/LIST]
      
[/LIST]

Anyway , thank you both for your insight , this is already a great progress.

Well actually I know because I have a system 76 laptop. :) But you don't need to have a system 76 machine to use the ppa. Intel firmware should work across the board.

---

### Post by coutte-chris on 2021-08-17
> **monkeybrain20122 said:**
> Well actually I know because I have a system 76 laptop. :) But you don't need to have a system 76 machine to use the ppa. Intel firmware should work across the board.

I thought so. 
I was thinking about buying their laptop. But I preferred to turn back to the evil Dell corporation. 
Now , I am paying the price. their helpdesk support is ...... to be improved , let's say...

---

