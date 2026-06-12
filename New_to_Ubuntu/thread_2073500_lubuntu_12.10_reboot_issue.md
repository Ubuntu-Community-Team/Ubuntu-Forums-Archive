---
title: "lubuntu 12.10 reboot issue"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by ginmardo84 on 2012-10-19
Hey guys, 

I recently registered with the forum so please feel free to correct me on errors. 

I recently downloaded & installed lubuntu 12.10 i386 via flashdrive. The install itself went flawless but have encountered an issue: Whenever I install an app and reboot the system, my PC hangs on boot. I get nothing displayed, but the monitor is still on; does not go into sleep mode. The numlock indicator on my keyboard is lit, but does not react [on/off] upon pressing the numlock key. I installed numlockx in terminal, I installed firefox browser and in both seperate cases the boot hangs. I can't seem to install any additional apps at the moment for fear that my rig won't reboot. 

Anybody else encountered this problem with their fresh install?

---

### Post by Bashing-om on 2012-10-19
ginmardo84; Hi Welcome to the forum.

That situation is one I can not fathom as it freezes only on installing a new app//

look at any errors that may be generated from dpkg and apt-get.
Terminal (ctl+alt+t)commands 
```
sudo apt-get update
sudo apt-get upgrade
```as a place to start troubleshooting. If any errors post them back here.
[INDENT]try'n to help <==BDQ

[/INDENT]

---

### Post by vasa1 on 2012-10-19
> **ginmardo84 said:**
> ...
I recently downloaded & installed lubuntu 12.10 i386 via flashdrive. The install itself went flawless but have encountered an issue: Whenever I install an app and reboot the system, my PC hangs on boot ...

Please provide your hardware specs (CPU, RAM, graphics card, anything else that may be of interest.)

Also...
Why did you reboot after installing an app? It's usually not necessary.
When do you reboot? Is it immediately after installing the app? Or do you use the app for a while?
Mind sharing the names and sources of these apps?

And, no, I don't have this problem and don't remember seeing anything similar being reported.

---

### Post by ginmardo84 on 2012-10-19
> **vasa1 said:**
> Please provide your hardware specs (CPU, RAM, graphics card, anything else that may be of interest.)

Also...
Why did you reboot after installing an app? It's usually not necessary.
When do you reboot? Is it immediately after installing the app? Or do you use the app for a while?
Mind sharing the names and sources of these apps?

And, no, I don't have this problem and don't remember seeing anything similar being reported.

Sorry about that. i forgot to mention that I am running Lubuntu 12.10 on an old Dell PowerEdge-400SC server. CPU: Pentium 4 with HT, 2048 DDR memory, 30GB SSD, NVIDIA 6200LE GPU. 

I know that its usually not necessary to reboot after installing an app, but I do that from after some time. This happened when after Firefox install. 

In LXTreminal 
[sudo apt-get install firefox] 
[sudo apt-get install numlockx -y]. 

Browsed for a while and rebooted the system. My monitor is active, but there just isn't anything displayed [black screen]. Keyboard & mouse don't seem to respond. 

Any ideas? I hope I have provided sufficient info for the time being.

---

### Post by vasa1 on 2012-10-19
What about free space on your disk? Do you have enough? And is swap being used a lot?
Do you have two separate problems, one relating to numlock and the other to installing apps? I'm asking because you mentioned installing numlockx.
People more familiar with graphic cards may drop by and comment if that could have anything to do with your problem.

Also, have you been running any Linux OS on this rig before without problem? If yes, which one(s)?

---

### Post by ginmardo84 on 2012-10-19
> **vasa1 said:**
> What about free space on your disk? Do you have enough? And is swap being used a lot?
Do you have two separate problems, one relating to numlock and the other to installing apps? I'm asking because you mentioned installing numlockx.
People more familiar with graphic cards may drop by and comment if that could have anything to do with your problem.

Also, have you been running any Linux OS on this rig before without problem? If yes, which one(s)?

I do have enough free disk space available. 

It is just one problem, it simply occurred after installing an apt after the clean install. After installing numlockx, the PC would reboot and than hang at the GRUB boot menu. I tried it a second time but this time with firefox installed and did the same thing. It either doesn't display anything [blacked out display] or it shows the GRUB menu to select the installation to boot, but the keyboard does not respond at all. 

Up until yesterday I was running Lubuntu 12.04 successfully with NVIDIA's 304.51 drivers installed, had plymouth configured so that I don't get those ugly vertical black/white stripes upon boot. Added restricted extras to the software resources.

---

### Post by ginmardo84 on 2012-10-20
> **Bashing-om said:**
> ginmardo84; Hi Welcome to the forum.

That situation is one I can not fathom as it freezes only on installing a new app//

look at any errors that may be generated from dpkg and apt-get.
Terminal (ctl+alt+t)commands 
```
sudo apt-get update
sudo apt-get upgrade
```as a place to start troubleshooting. If any errors post them back here.
[INDENT]try'n to help <==BDQ

[/INDENT]

Hi Bashing-om, 

Thanks for the input. I just ran the update and upgrade in terminal. Some packages were added at upgrading. Nothing outta the ordinary. Perhaps it might be a GPU issue. Encountered that in my previous Lubuntu version. But that was merely cosmetic.

Currently downloading and installing NVIDIA propriety-tested driver to enable. See if and how it will affect the performance.

---

### Post by NikTh on 2012-10-20
> **ginmardo84 said:**
> 

It is just one problem, it simply occurred after installing an apt after the clean install. After installing numlockx, the PC would reboot and than hang at the GRUB boot menu. I tried it a second time but this time with firefox installed and did the same thing. It either doesn't display anything [blacked out display] or it shows the GRUB menu to select the installation to boot, but the keyboard does not respond at all. 

Hi , 

so the "damage" here caused by the installation of numlockx ? 

Firefox I doubt if has any relation with the boot - hang problem. 

Did you try to remove the numlockx ? 

If you cannot boot neither from the grub -> Recovery mode , then boot from a LiveCd-Usb and chroot to the partition with Lubuntu root /  and remove the numlockx.

**From the LiveCD-USB session:**

Open the lxterminal and do 
```
sudo fdisk -l
``` and see in which partition is Lubuntu installed , we assume now its /dev/sda2 partition (if you are not sure , give the results of the command here).

Then do ```
sudo mount /dev/sda2 /mnt
sudo chroot /mnt
sudo apt-get remove numlockx 
exit
sudo umount /mnt 
```Then run one more time the [boot-repair]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu") program and finally reboot your system.

---

### Post by ginmardo84 on 2012-10-21
Guys, 

thanks for the reply but I doubt that the no-display on reboot has anything to do with the Lubuntu 12.10. I think the fact that I installed it on a server, made wuite a difference. 

It runs flawless, with the exception of some bugs which can be solved all in good time, on a more current rig: 
core2duo e7200 cpu
4gb ddr3 memory
30gb ssd 
geforce 8500 gt gpu

Apparently running desktop OS's on servers might prove some significant operational behaviors. 

I have registered with Ubuntu launchpad also for submitting eventual bug reports.

Tho I haven't spent time on looking into the issue I posted -instead running Lubuntu 12.10 on another rig-, I still thank you all for your time and input. 


Regards, 
ginmardo84

---

### Post by amjjawad on 2012-10-29
> **ginmardo84 said:**
> Guys, 

thanks for the reply but I doubt that the no-display on reboot has anything to do with the Lubuntu 12.10. I think the fact that I installed it on a server, made wuite a difference. 

It runs flawless, with the exception of some bugs which can be solved all in good time, on a more current rig: 
core2duo e7200 cpu
4gb ddr3 memory
30gb ssd 
geforce 8500 gt gpu

Apparently running desktop OS's on servers might prove some significant operational behaviors. 


Your machine is not older than mine: [http://ubuntuforums.org/showpost.php?p=11832431&postcount=152](http://ubuntuforums.org/showpost.php?p=11832431&postcount=152)

If you like, I'm here and ready for help :)

---

