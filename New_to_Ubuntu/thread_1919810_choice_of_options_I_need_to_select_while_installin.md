---
title: "choice of options I need to select while installing"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by archangel2003 on 2012-02-03
1: I used the forum search first and was unable to find the info I need.
 
2: I assume I posted in the correct forum.
 
3: Indicate your level of experience with Ubuntu and the topic of your problem.

My daughter installed Ubuntu 10.04 on my previous laptop a couple years ago when we went to, and met in Florida, and it was wonderful. 
I now have a new laptop and have to install it myself as she is ½ way across the country. I used Windows 7 to make 2 partitions on the drive and allocated 100 gig for the Ubuntu.

4: Explain how you installed or are installing Ubuntu. 

I have a 750 GB Hard drive.

I used Windows 7 to make 2 partitions on the drive.
 Labeled as Logical Drives are... 
 Partition X @ 100 GB for the Ubuntu. 
 Partition Z @ 200 GB for future CADD programs. 
 Labeled as Primary Partition are... 
 Partition C @ 386 GB Healthy (Boot, Page File, Crash Dump, Primary Partition. 
 There is also 1.46 GB Healthy (Active Recovery Partition) 
 There is also 15.07 GB Healthy (Primary Partition) 
 
 
 I have to wonder what takes 15 GB and is labeled Primary if the &#8220;C&#8221; drive is the primary as there already a Recovery Partition. 
 
 
 After repeated attempts to get a start up disc or flash drive, I finally succeeded using the &#8220;install with Windows&#8221; option, but it only offered the newest version 11, but I really wanted the LTS version 10.04. 
 I assume version 11 was installed in the X partition as that is where I told it to install. 
 
 
 A week or so later I was successful in getting the 11 version to make a working boot disc of the 10.04 and have run it a few times. 
 So in windows I formatted the X partition to prepare for installing the 10.04 
 Funny that in Ubuntu, when I look at the volumes of the partitions, they seem (5 to 7 GB) larger than what they are in Windows, have no designations like in Windows (&#8220;TI10620W0DC&#8221; &#8220;Ubuntu X&#8221; and &#8220;CADD management Z&#8221;) also there seem to be more partitions than in windows. 
 The first time I tried to install letting the program choose a location, it was going to install on Partitions 7 and 8 and there were only 6 partitions as per windows. 
 
The final issues remaining are the choice of options I need to select while installing the Ubuntu 10.04 pictured below.
 
I assume I need to partition manually to tell it to go to the Ubuntu partition, and the one I want is 100 GB but the closest I see is 107 GB so should I assume that is the correct one?
Running the 10.04 from a disc does not show the partition labels.

I had to go back to Windows 7 and recombine the unallocated partitions into the "C" partition so I am back to the original 5 partitions.
 
Do I select DOS or windows?

Do I choose FAT 32, or something else?

---

### Post by Mark Phelps on 2012-02-03
OK, first of all, you can't install Ubuntu natively to an NTFS partition.  That is a Windows filesystem and Ubuntu needs a Linux filesystem.  So, what I would do is go back into Win7 and remove the NTFS "Ubuntu" partition. I don't know if Win7 will let you create an Ext4 Linux filesystem partition, but even if it does, it would be better to let the Ubuntu installer format the target partition, not Win7.

As to the other partitions, sda1 is the Wi7 boot partition, the other two NTFSs are most likely, the first one is Win7 OS, the second one (inside the extended) is a data partition.

BEFORE you attempt another install, you should use the Win7 Backup feature to create and burn a Win7 repair CD.  That will prove invaluable later, should you need to restore the Win7 loader, or Win7 boot capability.

Also, if you want to recovery the space used by the Recovery partition, you can do so by making your own image backup of Win7.  The advantage of doing this, is that you can later restore Win7 exactly as it was when you made the backup.  You don't have to reinstall your apps -- as you would if you did a restore using the Recovery partition.

If you want to do that, download the FREE version of Macrium Reflect (MR) and install it in Win7.  Then, make a backup of your boot partition and OS partition to an external drive.  Then, use the option to create and burn a Linux Boot CD.

NOW, you have the ability to restore Win7 to its current state anytime you want in the future.

---

### Post by d4m1r on 2012-02-03
No, Windows 7 does NOT have the option to create a EXT4 partition, which is required for Ubuntu.

Go back to Windows 7 and delete the partition (so its unallocated space), run the Ubuntu installer, specify that unallocated space is where you want to install Ubuntu (clean option, not upgrade/along side Windows) and make sure file server = EXT4 and not NTFS or fatxx.

---

### Post by archangel2003 on 2012-02-04
I did get it on, (Friday night Professional GEEK help at JJC) but when looking at the partitions decided to redo them and reinstall 10.04.
There were extra partitions and free spaces out there and we would clean them up
Somehow it screwed up the GRUB and nothing opened up, and my computer only came with recovery discs that destroy everything I added, not a Windows 7 repair disc!

14 hours later (Saturday morning GEEK help) it was all straightened out/up and running, (Thank You Jos***) but the Ubuntu took almost 1/2 the available drive space rather than the smaller 100 GB I wanted.

Windows will not let me do anything to any other partition but delete it, but Ubuntu looks like it will let me. 
I'll deal with that later, as I want to enjoy it before I screw things up messing with it!

But now the only serious issue is (and I think it also happened on my other laptop after installation) the WIFI acts like there is nothing available. I turn the WIFI button on and off, and even though I can see by the light it is turning on and off, nothing works.
I had to go back to 7 to use this wireless connection.

I have the 
Toshiba Satellite P775, 
i7-2670QM, 
6 GB RAM, 
64 bit

Windows 7, running fine including the wireless.
Ubuntu 10.04 running fine except for the wireless connection seems dead.

I do think it was a simple issue to correct, but can't remember.

If Ubuntu has not spread through JJC yet, it will now as it seemed to have piqued "J's" interest and he is not stingy with sharing tech!

---

### Post by Mark Phelps on 2012-02-05
The WiFi button on laptops generally does not work in Linux distros because it needs a special driver that is not available.

So, if you turn wireless off using the button when in Win7, you will most likely NOT be able to turn it back on in Linux.

---

### Post by archangel2003 on 2012-02-05
> **Mark Phelps said:**
> The WiFi button on laptops generally does not work in Linux distros because it needs a special driver that is not available.

So, if you turn wireless off using the button when in Win7, you will most likely NOT be able to turn it back on in Linux.

The first time I touched the button was in Ubuntu to see it it was on or not, and it was.

It lights up when turned on and goes dark when turned off in both Windows and Ubuntu. 

Otherwise I leave it on all the time.

---

### Post by wildmanne39 on 2012-02-05
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by archangel2003 on 2012-02-05
#(cat /etc/lsb-release; uname -a lspci -nnk | grep -iA2 net iwconfig rfkill list all lsmod)

---

### Post by archangel2003 on 2012-02-05
I guess # and 
cat /etc/lsb-release; uname -a lspci -nnk | grep -iA2 net iwconfig rfkill list all lsmod

Between ( and ) in a new reply did not work.

What was it supposed to do?
Link me to someone who has some insight or solved the issue?

I am a new guy ya know, as in clueless about technical computer things and stuff.

---

### Post by wildmanne39 on 2012-02-05
Hi, just copy and paste the commands one line at a time into the terminal and then paste the results here.
Thanks

---

### Post by archangel2003 on 2012-02-06
> **wildmanne39 said:**
> Hi, just copy and paste the commands one line at a time into the terminal and then paste the results here.
Thanks
Here it is.


 michael@michael-laptop:~$ cat /etc/lsb-release; uname -a  
 DISTRIB_ID=Ubuntu  
 DISTRIB_RELEASE=10.04  
 DISTRIB_CODENAME=lucid  
 DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"  
 Linux michael-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:13:52 UTC 2011 x86_64 GNU/Linux  
 michael@michael-laptop:~$ lspci -nnk | grep -iA2 net  
 02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)  
     Kernel driver in use: r8169  
     Kernel modules: r8169  
 03:00.0 Network controller [0280]: Intel Corporation Device [8086:0885] (rev 67)  
 05:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2392] (rev 30)  
 05:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2391] (rev 30)  
 michael@michael-laptop:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 michael@michael-laptop:~$ rfkill list all  
 michael@michael-laptop:~$ lsmod  
 Module                  Size  Used by  
 nls_iso8859_1           4633  1  
 nls_cp437               6351  1  
 vfat                   10866  1  
 fat                    55350  1 vfat  
 joydev                 11104  0  
 binfmt_misc             7960  1  
 ppdev                   6375  0  
 snd_hda_codec_realtek   279008  1  
 snd_hda_intel          25805  2  
 snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep               6924  1 snd_hda_codec  
 snd_pcm_oss            41394  0  
 snd_mixer_oss          16299  1 snd_pcm_oss  
 snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss  
 snd_seq_dummy           1782  0  
 snd_seq_oss            31191  0  
 snd_seq_midi            5829  0  
 snd_rawmidi            23420  1 snd_seq_midi  
 snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi  
 snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 uvcvideo               62851  0  
 snd_timer              23649  2 snd_pcm,snd_seq  
 snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 videodev               40518  1 uvcvideo  
 v4l1_compat            15495  2 uvcvideo,videodev  
 v4l2_compat_ioctl32    11892  1 videodev  
 fbcon                  39270  71  
 tileblit                2487  1 fbcon  
 font                    8053  1 fbcon  
 bitblit                 5811  1 fbcon  
 softcursor              1565  1 bitblit 
 video                  20623  0  
 output                  2503  1 video  
 snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 psmouse                65040  0  
 serio_raw               4918  0  
 vga16fb                12757  1  
 vgastate                9857  1 vga16fb 
 xhci                   42519  0  
 sdhci_pci               6700  0  
 sdhci                  17960  1 sdhci_pci  
 led_class               3764  1 sdhci  
 soundcore               8052  1 snd  
 snd_page_alloc          8500  2 snd_hda_intel,snd_pcm  
 lp                      9336  0  
 parport                37160  2 ppdev,lp  
 usb_storage            50377  1  
 r8169                  39714  0  
 mii                     5237  1 r8169  
 ahci                   38030  2  
 michael@michael-laptop:~$

---

### Post by archangel2003 on 2012-02-06
There was one place that was supposed to show me how to turn it on but I only got as far as System> administrator>Network.
But in network (assuming Network tools is what they imply by Network) there was no "Unlock" to press and no place to input a password, also there was no connections tab or anything else listed either.

---

### Post by wildmanne39 on 2012-02-06
Hi, please try:
```
sudo modprobe iwlagn
```
make sure your wired connection is disconnected. 

If it does not come on install rfkill in synaptic then run this command and post the results.
```
rfkill list all
```

Also go to the internet icon in the top right corner of the screen and make sure enable wireless is checked.
Thanks

---

### Post by archangel2003 on 2012-02-06
> **wildmanne39 said:**
> Hi, please try:
```
sudo modprobe iwlagn
```make sure your wired connection is disconnected. 

My laptop is not using a wire.


> **wildmanne39 said:**
> 
If it does not come on install rfkill in synaptic then run this command and post the results.
```
rfkill list all
```Also go to the internet icon in the top right corner of the screen and make sure enable wireless is checked.
Thanks

Install rfkill in synaptic?
Sorry to ask, but...
How do I install rfkill, and what is synaptic?

The wireless was working without any issues when the Ubuntu 11 was installed last week.
I deleted Ubuntu 11 and installed Ubuntu 10.04.

---

### Post by wildmanne39 on 2012-02-06
Hi, do you have any way to connect to the internet and install updates and drivers?
Thanks

---

### Post by archangel2003 on 2012-02-07
> **wildmanne39 said:**
> Hi, do you have any way to connect to the internet and install updates and drivers?
Thanks

I was so hung up on there being a programing solution (select this button, not that button) like last time I never thought that updating might be an option.

If hooking up the hard wire from the cable box at home will work with 10.04 set up as it is, then yes.

I'll give it a try tonight and report back.

Thanks.

---

### Post by wildmanne39 on 2012-02-07
Hi, yes please update your system completely then disconnect your wired connection and reboot.

The driver you need should be included with ubuntu but it does not show up, let me know what happens after you update and we can go from there.

Synaptic is the package manager in ubuntu 10.04 is for installing software and after you update rfkill can be installed by opening synaptic and typing rfkill into the search box then click to install it if you still need too.
Thanks

---

### Post by Miljet on 2012-02-07
In 10.04 the Synaptic Package Manager can be accessed by going to the top of your screen, select "System", then "Administration", and "Synaptic Package Manager".

---

### Post by archangel2003 on 2012-02-07
HMM, I hooked up the phone like cord and turned on the computer then selected Ubuntu and this (pictured) is what I got.

Now Ubuntu does not work at all.

I attempted recovery but in the end after a minute or two it says it Quits.

Now I am at a total loss as to why hooking up the internet cable would kill Ubuntu.

---

### Post by archangel2003 on 2012-02-08
Well, I did get it to boot up twice out of about 8 or more attempts, and it does seem to take forever to either start up, or complain about not being able to.

If I fire up my old laptop in Ubuntu, I would already be surfing the net by the time this computer's Ubuntu either begins to start up or tells me it failed to.

Once it did boot up, after endless fudging finally got it to accept (a second wire connection?) as it kept disconnecting me as soon as it connected on the first default one.

I activated the update manager and there were something like 150+ updates.
They were uploaded and installed, but when I attempted to restart, I am still having the issue of getting it to fire up in the first place to even see if it can pick up a wireless signal.

When I try to click Ubuntu repair rather than Ubuntu for start up, is pictured below.

The whole reason I was willing to go with Ubuntu is to surf the net safely and because it booted up so fast!

Now I have neither.

I wish I knew of an Ubuntu expert near me!

---

### Post by archangel2003 on 2012-02-08
I did get the synaptic manager to install that rfkill as suggested and even though I did get it to boot all three times I tried today, it will only go on line through a wire (inconvienient as it's not long enough to reach out from under the desk in the office).

---

### Post by wildmanne39 on 2012-02-08
Hi, I am just trying to get your wireless to work please post the results of:
```
rfkill list all
```
```
lsmod
```
you may want to get these issues fixed first before trying to get the wireless to work that is what I would do.
Thanks

---

### Post by archangel2003 on 2012-02-08
"rfkill list all" did nothing but with rfkill there was something pictured below.
I assume you meant to download in the synaptic manager?

The pictures below show what is up.

Booting to Ubuntu is still a hit and miss gamble.

---

### Post by archangel2003 on 2012-02-08
And a few more.

I installed what came up for those things listed in synaptic except for the sudo selections, there were a lot of games and I was unsure what to mark for upload.

After all this was done, I can't tell if anything has changed.

Booting up is still a god awful long wait for that hit or miss, and there is no wireless at all.

I would just delete the whole thing and try again, but last time I did that I could not even get into windows!

---

### Post by wildmanne39 on 2012-02-08
Hi, all commands given are to be ran in the terminal.

When you ran ```
sudo modprobe iwlagn
```
did you enter your password after you entered the command? The sudo command requires you to enter your user password and it will not show in the terminal as you type it so after you have entered it just hit the enter key and the command will not show output unless there is an error.

Also unplug your wired connection first.
Thanks

---

### Post by archangel2003 on 2012-02-08
Post 23, picture 4 was of when I ran them together as one, and each, one at a time in terminal, and I do think I remember inputting the password.

The picture below shows the result.

---

### Post by wildmanne39 on 2012-02-08
Hi, yes I saw that, the first command looks right if you entered your password.

Here are directions for all commands.

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by archangel2003 on 2012-02-09
Here is is.
rfkill list all did nothing, but lsmod had a lot listed below.
I still don't get the 
"by clicking on new reply and click # and paste the information between the brackets.
Thank you     "

All I get is a new window with a # in it with no brackets.
It's probably something simple that I am unaware of.


 michael@michael-laptop:~$ rfkill list all 
  michael@michael-laptop:~$ lsmod 
  Module                  Size  Used by 
  joydev                 11104  0 
  binfmt_misc             7960  1 
  ppdev                   6375  0 
  snd_hda_codec_realtek   279072  1 
  snd_hda_intel          25805  2 
  snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel 
  snd_hwdep               6924  1 snd_hda_codec 
  snd_pcm_oss            41394  0 
  snd_mixer_oss          16299  1 snd_pcm_oss 
  snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
  snd_seq_dummy           1782  0 
  snd_seq_oss            31191  0 
  snd_seq_midi            5829  0 
  snd_rawmidi            23420  1 snd_seq_midi 
  snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi 
  snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
  snd_timer              23681  2 snd_pcm,snd_seq 
  snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
  fbcon                  39270  71 
  tileblit                2487  1 fbcon 
  uvcvideo               62915  0 
  font                    8053  1 fbcon 
  videodev               40550  1 uvcvideo 
  v4l1_compat            15495  2 uvcvideo,videodev 
  v4l2_compat_ioctl32    11892  1 videodev 
  psmouse                65040  0 
  bitblit                 5811  1 fbcon 
  softcursor              1565  1 bitblit 
  serio_raw               4918  0 
  xhci                   42775  0 
  video                  20623  0 
  snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
  sdhci_pci               6700  0 
  sdhci                  17960  1 sdhci_pci 
  led_class               3764  1 sdhci 
  output                  2503  1 video 
  soundcore               8052  1 snd 
  snd_page_alloc          8500  2 snd_hda_intel,snd_pcm 
  vga16fb                12757  1 
  vgastate                9857  1 vga16fb 
  lp                      9336  0 
  parport                37160  2 ppdev,lp 
  ahci                   38350  2 
  r8169                  39714  0 
  mii                     5237  1 r8169 
  michael@michael-laptop:~$

---

### Post by archangel2003 on 2012-02-09
Also, I have to toggle between W7 to go on line and Ubuntu 10 with the issue.

There is no guarantee that Ubuntu will even load up as some times the success rate of Unbuntu actually loading up is 50% or less.:(

---

### Post by archangel2003 on 2012-02-09
[wildmanne39]("http://ubuntuforums.org/member.php?u=508533"), 

Are you seriously in Roswell? :shock:

If so tell the alien overlords I have be good and could they please let my Ubuntu work. ;)

---

### Post by wildmanne39 on 2012-02-09
Hi, yes I live in Roswell.

Please post the results of:
```
dmesg | egrep 'iwl|firm|radio|switch|wlan0'
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e radio -e switch -e etork | tail -n55
```
Thanks

---

### Post by archangel2003 on 2012-02-09
michael@michael-laptop:~$ dmesg | egrep 'iwl|firm|radio|switch|wlan0'
    [   27.258640] Console: switching to colour frame buffer device 80x30
    michael@michael-laptop:~$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e radio -e switch -e etork | tail -n55
    [sudo] password for michael: 
    Feb  8 08:46:57 michael-laptop kernel: [   35.871629] Console: switching to colour frame buffer device 80x30
    Feb  8 08:46:59 michael-laptop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
    Feb  8 08:46:59 michael-laptop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
    Feb  8 08:56:15 michael-laptop kernel: [   27.076784] Console: switching to colour frame buffer device 80x30
    Feb  8 08:56:15 michael-laptop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
    Feb  8 08:56:15 michael-laptop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
    Feb  8 08:59:33 michael-laptop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
    Feb  8 08:59:33 michael-laptop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
    Feb  8 08:59:33 michael-laptop kernel: [   37.081311] Console: switching to colour frame buffer device 80x30
    Feb  8 13:47:15 michael-laptop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
    Feb  8 13:47:15 michael-laptop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
    Feb  8 13:47:15 michael-laptop kernel: [   26.981070] Console: switching to colour frame buffer device 80x30
    Feb  8 14:50:51 michael-laptop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
    Feb  8 14:50:51 michael-laptop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
    Feb  8 14:50:51 michael-laptop kernel: [   36.986959] Console: switching to colour frame buffer device 80x30
    Feb  8 15:31:33 michael-laptop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
    Feb  8 15:31:33 michael-laptop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
    Feb  8 15:31:33 michael-laptop kernel: [   37.095031] Console: switching to colour frame buffer device 80x30
    Feb  8 15:39:56 michael-laptop kernel: [  541.422372] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
    Feb  8 15:39:56 michael-laptop kernel: [  541.422376] iwlagn: Copyright(c) 2003-2009 Intel Corporation
    Feb  8 23:46:06 michael-laptop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
    Feb  8 23:46:06 michael-laptop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
    Feb  8 23:46:06 michael-laptop kernel: [   36.254976] Console: switching to colour frame buffer device 80x30
    Feb  8 23:53:04 michael-laptop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
    Feb  8 23:53:04 michael-laptop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
    Feb  8 23:53:04 michael-laptop kernel: [   26.808716] Console: switching to colour frame buffer device 80x30
    Feb  9 16:45:13 michael-laptop kernel: [   27.258640] Console: switching to colour frame buffer device 80x30
    Feb  9 16:45:13 michael-laptop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
    Feb  9 16:45:13 michael-laptop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
    michael@michael-laptop:~$

---

### Post by wildmanne39 on 2012-02-09
Hi, I believe you have a bad install of ubuntu because some of these commands should have given output and did not or not what is expected and you are having so much trouble booting.

If you do not like unity I recommend installing 11.10 xubuntu it is a lot like 10.04 and make sure you are connected to the internet when you install it and choose to install all updates and third party packages and this will save you a lot of work when xubuntu is installed and your wireless should work with no problems.
Thanks

---

### Post by archangel2003 on 2012-02-10
I did have 11.10 installed and did not like it at all.
The tool bar on the left kept jumping out when I was in firefox and I could not move it.

As far as being on the net when installing Ubuntu, the only option for that type of install was 11.10.
10.04 options were flash or disc install only.

If you know of another option to get 10.04 directly on my computer, or another way to customize 11.10 and I can have it the way I want it, I would love to hear about it.

---

### Post by wildmanne39 on 2012-02-10
Hi, I have the left bar hidden all the time in 11.10 it only comes out when I hit the windows key, but I installed awn launcher at the bottom of my screen and it even has a gnome 2 type menu.
Thanks

---

### Post by archangel2003 on 2012-02-10
> **wildmanne39 said:**
> Hi, I have the left bar hidden all the time in 11.10 it only comes out when I hit the windows key, but I installed awn launcher at the bottom of my screen and it even has a gnome 2 type menu.
Thanks


Now that looks a lot better than what I had.

This Friday night, or Saturday afternoon I'll delete the old one and try 11 again with awn like you have.

---

### Post by wildmanne39 on 2012-02-10
Hi, okay sounds good and you can install awn and all applets using software center.

Then you will need to install ccsm to change the launcher on the left to make it stay hidden all the time, if you need more help post back.

 I may respond a little slow I am very busy at the moment.
Thanks

---

### Post by archangel2003 on 2012-02-11
I just never stops.

I got the old Ubuntu off and got the system back to it's pre-Ubuntu condition with a lot of help.

It seems that Ubuntu 11 can't be uninstalled without screwing up the BIOS on my computer.

I just did the "in windows" download, set it up, but did not press finish as I wanted to view the instructions once again so hit the red X in the upper right corner of the installation box.

Now when I try to do it again it tell me what is pictured below.

First uninstall the previous version, then ERROR, CAN'T UNINSTALL BECAUSE IT IS NOT THERE.

As far as I can tell, other than a couple of installation files on the desk top, it's not there.

---

### Post by wildmanne39 on 2012-02-11
Hi, I have never installed inside windows, that is not meant to be used permanently just to try ubuntu out then do a normal install, if you really want to do it inside windows you can have a look at this link.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
Thanks

---

### Post by Learning Linux 2011 on 2012-02-11
I have to say, archangel, that you have a pretty convoluted hard drive.

Can you explain what all those partitions are?  If you just want Windows 7 and Ubuntu, why do you have so many partitions?

---

### Post by archangel2003 on 2012-02-11
> **Learning Linux 2011 said:**
> I have to say, archangel, that you have a pretty convoluted hard drive.

Can you explain what all those partitions are?  If you just want Windows 7 and Ubuntu, why do you have so many partitions?


Well, at first I only had the three stock partitions, but I made 2 partitions, one intended for the CADD programs using XP and the other for Ubuntu, but after I installed Ubuntu there were extra partitions as well as extra free space.

Everything is back to normal now thanks to a very intelligent 17 yr old college student willing to help out put things back to normal.

I'll try that link listed by wildmanne39.

---

### Post by archangel2003 on 2012-02-12
[SIZE=3]Here are the partitions with the Ubuntu 11 installed shown below.

Are there any good videos on how to get AWN working?

I seem to be having issue getting the stock tool bar items off the left and into the bottom.

I was able to add some to the AWN like firefox and other applets that are not on the stock one, but the rest that are already on the left I cant get into AWN, and how do we get rid of the old stock tool panel when I'm done?

Also, how do I disable quitting the AWN tool bar, because I have quit it a couple times and the only way I can get it back is to restart Ubuntu.[/SIZE]

---

### Post by archangel2003 on 2012-02-12
[SIZE=3][B]I guess the main idea of this topic is no longer primarily relevant.

Now I need to get this system up and running properly like this one shown below.

BTW if anyone working on Ubuntu cares, 11 is too confusing and clunky.

I see advice telling me to

Open the main Ubuntu menu, move your cursor over "System," then "Administration," and click on "Synaptic Package Manager."

And have no clue where the main menu is.

I can find system tools, but nowhere in there is the "Administration" or the "Synaptic manager" in system tools.

People tell you to click this and click that, but do not tell you how to find it.

I'm told to drag and drop things from the main tool bar into the AWN tool bar, but when I drag them, they pop right back to where they came from.

It would be nice to have an illustrated guide or video of someone actually doing these things.[/B][/SIZE]

---

### Post by wildmanne39 on 2012-02-12
Hi, > Are there any good videos on how to get AWN working?I did not find one that is working at the moment.

> I seem to be having issue getting the stock tool bar items off the left and into the bottom.
I did not remove any icons off of my launcher on the left I just opened the application I wanted that is on the launcher on the left or in dash and after it is opened go to your awn launcher right click on the icon and click on keep in launcher.
> how do we get rid of the old stock tool panel when I'm done?

In the Unity plugin, set Reveal to Auto hide and the Reveal edge to None or Disabled. 

Screenshot shows that the edges are disabled so that it will not open ,you can tell because all around the little window it is in red, if it was set to open when the mouse was moved to the edge it would be in green. 

You do have to have ccsm installed to change unity plugin settings, use software center for that then click on dash type ccsm annd then click on compiz settings manager that is where the unity plug in is located.

I am including a screenshot. I also discovered I can put my awn dock on the left of the screen right on top of the unity dock if I want to, but you can not remove it.

Now the unity launcher will only open when you hit the windows key.
[COLOR="Red"]**Do not disable the unity plug in or change any other settings in compiz**[/COLOR]
> how do I disable quitting the AWN tool barI do not know, I have never tried but you can go into dash and type awn then click on avaint window manager to restart it.
Thanks

---

### Post by archangel2003 on 2012-02-12
[SIZE=3]> **wildmanne39 said:**
> 
I did not remove any icons off of my launcher on the left I just opened the application I wanted that is on the launcher on the left or in dash and after it is opened go to your awn launcher right click on the icon and click on keep in launcher.[/SIZE] [SIZE=3]

I did that but the issue is that it is still on the left and not in the AWN tool box. I need to know how to get a copy of it into AWN.

> **wildmanne39 said:**
> [/SIZE] [SIZE=3]
In the Unity plugin, set Reveal to Auto hide and the Reveal edge to None or Disabled.
Screenshot shows that the edges are disabled so that it will not open ,you can tell because all around the little window it is in red, if it was set to open when the mouse was moved to the edge it would be in green. [/SIZE] [SIZE=3]

I can not find unity[/SIZE] [SIZE=3]anywhere, and how do I get to where you got to in the screen shot?
Pretend I know nothing (not far from the truth) , "step by step, first click this, then click that" type of directions.

> **wildmanne39 said:**
> 
You do have to have ccsm installed to change unity plugin settings, use software center for that then click on dash type ccsm annd then click on compiz settings manager that is where the unity plug in is located. 

I went into the software center and typed in ccsm. There was something that came up with a different name "ConQAT library of unity functions" but sounded good so I installed it.
I still don't know how to find it though as I looked.

[/SIZE][SIZE=3]> **wildmanne39 said:**
> [/SIZE]
[SIZE=3] I am including a screenshot. I also discovered I can put my awn dock on the left of the screen right on top of the unity dock if I want to, but you can not remove it. [/SIZE][SIZE=3]

Now the unity launcher will only open when you hit the windows key.[/SIZE] [SIZE=3]
[/SIZE] [SIZE=3][COLOR=Red]**Do not disable the unity plug in or change any other settings in compiz**[/COLOR][/SIZE][SIZE=3]

Where is compiz?
[/SIZE]

---

### Post by wildmanne39 on 2012-02-12
Hi, > I need to know how to get a copy of it into AWN.

Open the application you want that is on the launcher on the left, or in dash by hitting the windows key then type the name of the application you want to open then click on it and after it is opened go to your awn launcher right click on the icon and click on keep in launcher.

Dash is where all your applications are now.

Install compiz type compiz into software center, then install compizconfig settings manager (ccsm) is short for compizconfig settings manager ccsm .

The top of the unity launcher has the dash icon click on it, then type ccsm and then click on compiz settings manager that is where the unity plug in is located.

Once compiz is opened type unity click on unity plugin, set Reveal Mode to Auto hide and the Reveal edge to None or Disabled.
[COLOR="Red"][B]Do not disable the unity plug in or change any other settings in compiz.
[/B][/COLOR]
Thanks

---

### Post by archangel2003 on 2012-02-12
[SIZE=2][B]WOOOO HOOOO, I GOT IT NOW!

I found and got the compizconfig settings manager installed and found the unity with that computer screen looking thing where you tell it to only come out when I go directly to the lower left!

I guess I do best with pictures.

I get it now after looking closer at your desk top that the tool bar can not be deleted, just hidden.

I still can't get the Firefox or the screen shot camera down on the AWN tool bar.

But what is that translucent menu you have on the far right with the temp and time on it?

That looks nice.[/B][/SIZE] ;-)
[SIZE=4]**SHINNY!**[/SIZE]

---

### Post by wildmanne39 on 2012-02-12
Hi, okay I will try to explain better how to add firefox in my two previous posts I used generalised terms like applications for firefox so you would know that you could use this method for other applications as well.

Open fire firefox then go to your awn launcher and you will see the firefox icon there right click on it and choose to keep in launcher, it is that easy.

> But what is that translucent menu you have on the far right with the temp and time on it?It is called conky but the one I am using is very hard to set up and it took me several days the first time.

You need to become a student of ubuntu to get familiar with how it works, google is your best friend, if you type what you are looking for in google and add the work ubuntu you will usually get a lot of results to look at, this is the same method we all use to learn to use ubuntu.
Thanks

---

### Post by archangel2003 on 2012-02-13
> **wildmanne39 said:**
> Hi, okay I will try to explain better how to add firefox in my two previous posts I used generalised terms like applications for firefox so you would know that you could use this method for other applications as well.

Open fire firefox then go to your awn launcher and you will see the firefox icon there right click on it and choose to keep in launcher, it is that easy.

I did open Firefox and tried it as instructed.

The thing is Firefox only shows an icon in the standard tool bar, but I do not get one in the AWN tool bar, and I even have the AWN icon that is supposed to be blank until something is activated.

I also added a few of the green + signs that are supposed to allow adding applications, but nothing sticks.

I'm in Windows 7 installing Solidworks so I cant see the Ubuntu screen right now.

> **wildmanne39 said:**
> 
It is called conky but the one I am using is very hard to set up and it took me several days the first time.

You need to become a student of ubuntu to get familiar with how it works, google is your best friend, if you type what you are looking for in google and add the work ubuntu you will usually get a lot of results to look at, this is the same method we all use to learn to use ubuntu.
Thanks

With as much trouble I had with install of Ubuntu 11, conky might be beyond my abilities, but I think I will look into it. 
Who knows, I might figure it out with the help of the fellow student that helped me fix this laptop when the install removals went wrong.

---

### Post by archangel2003 on 2012-02-13
Firefox is available, I think, here listed below, but it says the task manager applet needs to be active, and as usual I can't find it.

---

### Post by wildmanne39 on 2012-02-13
Hi, that picture means it is added so I do not know why it is not showing up, I would google firefox not showing on awn launcher in ubuntu and you will probably find the answer.
Here is a link for the conky I use.
[http://ubuntuforums.org/showthread.php?t=1771033&highlight=conky](http://ubuntuforums.org/showthread.php?t=1771033&highlight=conky)

Please note other then the guide written you will not receive much help at this link it is not for support questions.
Thanks

---

### Post by archangel2003 on 2012-02-17
[SIZE=3]Well, I don't know about that last picture I saved where it shows up but does not move, but I did find a way to get them there. 

I have steps one, two, and three (pictured) as to how I got them to move there.

Now, in hind sight, it seems all too simple.

I had no clue but I guess you can have more than one app button at a time, like 5 Firefox buttons at once all over the place.

Go to Dash home in the upper left corner.
Click either on the more apps, the applied apps or the installed apps to find the one you want to move.
Then just click and drag.[/SIZE]

---

### Post by wildmanne39 on 2012-02-18
Hi, that is great to hear you got it the way you want it please use thread tools and mark the thread solved.
Thanks

---

