---
title: "Any issues between Linux and some hardware"
date: 2016-06-26
forum: New to Ubuntu
---

### Post by infolix76 on 2016-06-26
Hi,

My name is Olivier, I'm 65, french and more or less a newbie.
English is not my native language, so please forgive my mistakes.

My PC is a own assembled desktop:
Motherboard : ASUS F2A85-V
Processor: AMD A8-5600K APU with Radeon(tm) HD Graphics (64 bits)
Memory : Kingston 8 Go (2 DIMMs 4Go)
Power : Silencer Mark III (80Plus Bronze)
System disk : Western Digital 250 Mo - WDC WD2500HHTZ-0
Data disk : Western Digital 3 To - WDC WD30EZRX-00D

As I'm interested in graphics and music, I installed an Ubuntu Studio 12.04 (about 3 years ago) and everything was allright.
With the time I upgraded to 14.04 although "uname -a" answers : 

Linux EnfinLibre 3.19.0-61-lowlatency #69~14.04.1-Ubuntu SMP PREEMPT Thu Jun 9 10:15:00 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

For a few months now I have more and more crashes using video software:
VLC sometimes shows no pictures and sometimes crashes the whole system : frozen screen, no CRTL-ALT-T 
or CRTL-ALT-Fn will not work.
In this case, the only solution is the SUTMW (Savage Unpluging The Microsoft Way).

Some other times Openshot Video editor crashes while exporting a film with the message:
"Openshot has ended in an unexpected way" (my own translation from the french message)
KDEnlive, avidemux, winff do this as well.
I've had some issues with SoundKonverter too.
On these occasions it's not a complete system crash.

I tried to look at the logs but could not make anything of it.
I tried Linux forums but could not find anyone with the same problems.

So my questions are : 
- Could the hardware be the reason why? 
- Could a fawlty graphic chipset do this?
- Are there any know issues between Linux and my hardware?
- How to trace this problems?
- If not, should I go back to an older version of the system or the software?

If anybody could give me a least a hint, I'd be delighted.
I can provide all wanted info for my system if needed.

Thanks at lot in advance.

---

### Post by Bucky Ball on 2016-06-26
Your system looks like it's way out of date unless you are staying at the .1 point release for a specific reason. Have you been updating/upgrading regularly? Let's try that before going further.

Open a terminal and:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

Please post back any errors, if there are any, between code tags, please. This will not upgrade you to 16.04 but it will upgrade anything in 14.04 that needs to be.

Could you also post the output of:

```
sudo lshw -C video
```

... so we can see the exact Radeon. I read somewhere about a problem with one of them in 16.04 but others are more qualified re. GPUs.

---

### Post by gordintoronto on 2016-06-26
How hot is your CPU? You could install lm-sensors, then run sensors-detect, and say yes to "add the module". Reboot and the command: sensors 
will give you some information. (I use conky to continuously display some of this information.)

It might be time to replace the thermal paste, and clean the heat sink and fan.

---

### Post by infolix76 on 2016-06-26
Thanx for the quick answer. I update the system/software whenever the Ubuntu automatic updates asks me to.
Here's what lshw tells me :
  *-display               
       description: VGA compatible controller
       produit: Trinity [Radeon HD 7560D]
       fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
       identifiant matériel: 1
       information bus: pci@0000:00:01.0
       version: 00
       bits: 32 bits
       horloge: 33MHz
       fonctionnalités: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       ressources: irq:38 mémoire:d0000000-dfffffff portE/S:f000(taille=256) mémoire:feb00000-feb3ffff

I'll do the apt-gets right away.

---

### Post by infolix76 on 2016-06-26
Thanx gordintoronto,

Two days ago I opened the PC. I cleaned a bit though it was not that dusty. On reboot, I went to the graphic EFI bios, waited for the PC to get warm and checked the temperatures. Everything looked OK. I'll check if lm-sensors are installed and install it if not.

---

### Post by infolix76 on 2016-06-26
I did the apt-gets with no mistakes. The apt-get update just showed this warning
Lecture des listes de paquets... Fait (Reading of the packages lists... Done)
W: Aucune clé publique n'est disponible pour la/les clé(s) suivante(s) : (No public key available for the following key(s) 
1397BC53640DB551

---

### Post by Bucky Ball on 2016-06-26
Ok, that's an issue. Which repository is it saying there's no public key for? That's probably the repo that's being dealt with directly above that error perhaps ...

---

### Post by infolix76 on 2016-06-27
To Bucky Ball,
Could you tell me how to find the repo corresponding to this key?
There must be a file that contains this informations somewhere in the system.

To Gordintoronto,
Your idea this could come from some heat problem rings the bell. I had a similar problem long ago on a laptop that was getting overheated. It would put itself in a security state, meaning frozen. I had to wait for it to cool down before rebooting. (I was tied up to Microsoft Wonderful World in those days, so rebooting was a normal daily routine.)
I had lm-sensors already installed. Here's what the command 'sensors' say : 

olivier@EnfinLibre:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +19.0°C  (high = +70.0°C)
                       (crit = +70.0°C, hyst = +69.0°C)

radeon-pci-0008
Adapter: PCI adapter
temp1:         +3.0°C  (crit = +120.0°C, hyst = +90.0°C)

I don't know what to make of this...

To both,
Would you advice me to install 16.04 version? In this case, should I start completely afresh, from a DVD or USB image?
I have heard that any Linux kernel was now realtime. Is this true? or do I have to stick to Ubuntu Studio for the realtime kernel?
I have lots of other stuff installed. I'd like to keep at least the parameters and add-ons for those softs. (I'm thinking about getting Jack to work with my sound card so I could use Guitarix. It took me some time and I'm not too keen on restarting again.)

Anyway, thanks again for the answers

---

### Post by HermanAB on 2016-06-27
Well... VLC is known to be bad quality and tends to crash for no good reason.  I would advise against using VLC.  Mplayer and Xine are more stable and better quality alternatives.

I have never seriously used Openshot, so I cannot say anything specific about it, but video editors in general seem to be unstable things.  I normally use kdenlive as my video editor of choice and it also crashes once in a while.

---

### Post by infolix76 on 2016-06-27
Hi Herman,

VLC bad quality? Is that so? I thought on the opposite that it was a stable and trusty soft. I have had these problems for about three/four months. Before, everything was OK. This morning, I launched Openshot. I wanted to make a DVD image of one of my holiday film (mp4, 20mn). I checked the heat with sensors every ten seconds. I could see the heat growing up to 60°C. After a couple of minutes : suddenly frozen (deep-frozen!). After rebooting, I tried again. Same thing! I don't know if it is the heat that went straight up or if this tool (sensors) messed the system up...

Cheers

---

### Post by infolix76 on 2016-06-27
To Bucky Ball,

I made some investigations and it seems that it comes from the fact Debian banned the SHA1 protocol. See
[https://wiki.debian.org/Teams/Apt/Sha1Removal](https://wiki.debian.org/Teams/Apt/Sha1Removal)
The only repo that would fit on my system is GOOGLE-something. I have GOOGLE EARTH installed.
It is said I could fix the problem with :
sudo wget -q -O - [https://dl.google.com/linux/linux_signing_key.pub](https://dl.google.com/linux/linux_signing_key.pub) | apt-key add -
But all that GOOGLE stuff make me feel ill at ease. I don't trust them. I'd rather get rid of GOOGLE EARTH and see what happens...
-----------
I did that and removed the repo. No warning anymore from apt-get update.
Still, that does'nt solve my problem.

---

### Post by gordintoronto on 2016-06-27
Despite the other comment, I am delighted with VLC.

Nothing in your computer is at 19C, let alone 3C. I don't have a Radeon card, so I can't suggest anything about the video temperature.

Perhaps you could post the entire output of "sensors" in /code tags.

---

### Post by infolix76 on 2016-06-29
It seems that there is a bug with some AMD processor sensors. E.G. core sensors don't appear as if there were none.
There is nothing much to do about that...

---

### Post by phatez on 2016-07-01
First I would recommend updateing your flavor... Installing a newer ubuntu. 14.04 is kinda outdated, and your stuck inbetween a rock and a hardplace because 15.04 and 15.10 are listed as no longer supported on ubuntu's website. So try installing 16.04 instead. 

but if you insist on staying with 14.04  and dont even want to make the jump to 14.10....

Do you see the correct graphics card/ and all your other drivers listed on the software and updated under system settings? if so are the boxes checked? or do you see X.org Xserver checked? 

Here is someones reply for this problem with nvidia   :read Briams reply and possibly change 
sudo apt-get install nvidia-331-updates
to 
sudo apt-get install (Your driver here).

[http://askubuntu.com/questions/449693/how-to-change-graphic-card-driver-using-ubuntu-drivers](http://askubuntu.com/questions/449693/how-to-change-graphic-card-driver-using-ubuntu-drivers)



but I would recommend looking more in the direction of nvidias automatic driver switching. Its what I use, and it works with multiple screens, I was trying to find the correct link that I saw a few weeks ago, but will give you as much help that I find along the way, Sorry if its not exactly direct. 
[http://askubuntu.com/questions/693641/removing-graphics-nvidia-radeon-driver-without-going-headless](http://askubuntu.com/questions/693641/removing-graphics-nvidia-radeon-driver-without-going-headless)
But hey at-least they cover AMD in this one.

Also, try getting fan management software that runs off of Ubuntu. It could also play into it crashing. I use macfanctld, but then again I run my windows, OSX, Ubuntu, and Kali, all from my macbook pro, so naturally you'd need to find something for your particular set up.

Ill edit this if I can find that website with the exact driver switcher program. If you don't thing that's the issue, then keep us updated and I'm sure someone would know something more specific, but I think that's probably it.


_____________________________________________
*****************    edited add link       *************************

also you may want to check out ask Ubuntu, they have a lot of knowledgeable people, and alot of good answers. I was just looking for more repositories when I ended up here, then I saw your question and was hoping to help.
[http://askubuntu.com/questions](http://askubuntu.com/questions)

---

### Post by infolix76 on 2016-07-07
Upgraded to 16.04. Complete reinstall.
Changed the termic paste between the proc and the radiator.
Switch off my machine regularly (once every 2 or 3 days)
So far so good...

---

### Post by DuckHook on 2016-07-08
> **phatez said:**
> ...14.04 is kinda outdated...Please stop passing out advice like this because it is totally inaccurate.

14.04 is absolutely fine and will continue to be supported for another 3 years. At this point, it is more stable, more proven and more reliable than 16.04 although this is likely to change as 16.04 goes through its first point-release and continues to gain stability with time. I daresay that most server admins are still running 14.04 as well as other users who value stability over the latest shiny bells and whistles.> ...but if you insist on staying with 14.04 and dont even want to make the jump to 14.10......again, this is just plain wrong. The upgrade path to 16.04 does not require going through 14.10, which would be a foolish move in any case because it is now out of support, archived, and cannot be upgraded without changing sources.list to the archived site rather than the default mirrors.> Here is someones reply for this problem with nvidia :read Briams reply and possibly change
sudo apt-get install nvidia-331-updates
to
sudo apt-get install (Your driver here)....these instructions are not only wrong, but inapplicable and therefore useless. OP's video card is AMD, not nVidia. Your other link has nothing to do with the OP's problem.

@infolix76

I know that you have since solved your crashes, but it is useful for others who come across this thread to understand some details and not let mistaken advice stand uncorrected. Let's keep our fingers crossed that all your problems are solved. I would only note that you actually had a number of separate issues, and I would encourage you to keep your system as simple as possible. With 16.04, you won't have any option other than the open-source video drivers since AMD is no longer supporting fglrx (their old proprietary closed-source) drivers in this release. This actually simplifies your options. Your old problems may in fact have been due to proprietary drivers, which we don't know if you initially installed. Since you upgraded that install from 12.04, you may have inherited a string of old drivers that led to your initial problems.

If you continue to experience problems, you are more than welcome to post back to this thread, or to start another.

---

### Post by mastablasta on 2016-07-11
> **infolix76 said:**
> 
Changed the termic paste between the proc and the radiator.
Switch off my machine regularly (once every 2 or 3 days)
So far so good...

you need to detect sensors before using them. also i use psensor to monitor the temps:
[http://wpitchoune.net/psensor/](http://wpitchoune.net/psensor/)

every once in a while the dust gatheres a bit too much and heats up the CPU or GPU.

---

