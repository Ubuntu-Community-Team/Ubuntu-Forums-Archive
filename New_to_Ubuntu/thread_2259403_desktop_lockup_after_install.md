---
title: "desktop lockup after install"
date: 2015-01-04
forum: New to Ubuntu
---

### Post by poorguy on 2015-01-04
hey all need some help. have an hp/compaq CQ5600 bm411aa-aba / amd x2 b24processor / motherboardm2n68-la rev 5.00 have installed w7 on it so i know that all works. tried the dvd that i made and also the dvd from os disc and both install. when i restart i can enter my password and then hit enter and then it locks up. on the boot menu that does not operate at all. please help.

thanks poorguy

---

### Post by codingman on 2015-01-04
> **poorguy said:**
> when i restart i can enter my password and then hit enter and then it locks up. on the boot menu that does not operate at all.

Are you referring to the manditory restart after installation? Can you please describe, "locks up"? Also, what "boot menu that does not operate at all." are you talking about? Is it booting into a TTY? Finally, what flavor of Ubuntu are you using (e.g. Lubuntu)?

---

### Post by poorguy on 2015-01-04
hey codingman, the manditory restart i can do and then when i enter my password and hit enter it goes all orange and then locks up, from there i can only do a hard restart and when i try to chose the ubnuntu recovery option after restarting cannot access any choices. what i have is ubunty 14.04 lts 32 & 64 bit both do the same. i am thinking maybe the unity desktop is not installing or a driver issue from what i have reaserched. i was able to install and run from windows on the same desktop a debian standalone network install that runs perfectly. 

poorguy

---

### Post by codingman on 2015-01-04
Interesting. Probably a graphics driver issue, but I'm not using Ubuntu/Debian at the moment, so I can't point to a specific issue. If you can spare the bandwidth and time, I'd recommend you try another flavor of Ubuntu, (probably Lubuntu or Xubuntu). I personally find Unity quite bloated, even on a modern system.

If Debian worked, why not stick with that? Most tutorials and guides for Ubuntu will work well with Debian (except Mir-related issues).

---

### Post by grahammechanical on 2015-01-04
To recap in words that are clear to us. The OS loads to the login screen. The keyboard works because you can enter the password and press Enter but the desktop environment does not load to a user interface (Unity).

Also, at the boot menu you can select either Windows 7 or Ubuntu. So, the keyboard is working at that point. You can also open the Advanced Options for Ubuntu Sub-menu and select recovery mode but at the recovery menu you cannot "access any choices." Strange.

At the recovery menu Resume should be highlighted. Does pressing Enter work?  Resume will load to a desktop using an open source video driver called llvmpipe. So, if there is some kind of conflict with proprietary video drivers using Resume should get us to a point where we can change video drivers.

Also, after login can you right click the wallpaper? That should bring up a menu. Select Change Desktop Background. That will open System Settings at the Appearance utility. From there you can get to the main System Settings window and at Software and Updates>Additional Drivers tab you can change video drivers.

Another thing to try at that desktop without a user interface is Ctrl+Alt+T to open a terminal. Or Ctrl+Alt+F2 to open a console or tty. If you can do that you can then run commands that might fix things. Here are two commands. The  first to restart the second to shutdown or halt.

```
sudo shutdown -r now
```

```
sudo shutdown -h now
```

As I understand things, Debian does not provide proprietary video drivers. Ubuntu does provide proprietary video drivers but we have to give our consent and we do that when we tick "Install third party software" during the installation process. So, if you ticked that box you are using a proprietary video driver with Ubuntu. But maybe not using one with Debian. And that could account for the fact that Debian works but Ubuntu does not.

This is where I ask for details about the graphic adapter. Can we have some details please?

Regards.

---

### Post by codingman on 2015-01-04
> **grahammechanical said:**
> As I understand things, Debian does not provide proprietary video drivers. Ubuntu does provide proprietary video drivers but we have to give our consent and we do that when we tick "Install third party software" during the installation process. So, if you ticked that box you are using a proprietary video driver with Ubuntu. But maybe not using one with Debian. And that could account for the fact that Debian works but Ubuntu does not.


Good point, they should be using the same drivers if proprietary drivers aren't selected. I haven't installed Ubuntu in ages ;)

---

### Post by poorguy on 2015-01-04
hey all, ok boot menu for windows or ubuntu does not wok. keyboard does not work after entering password. advane recovery menu does not work because key board is not working. after entering password nothing works but the power butten on the front of the desktop. i do allow the third party software to be used on install. integrated graphic nvidia geforce 6150se nforce 430 / motherboard is hp m2n68-la(narra5). i would really like to solve this just to understand and to learn but am very pleased with the debian 7.7 wheezy. this problem also occurs with linux mint 17.1 (rebbeca) and also linux zorin all installed from dvd discs i made and also some that i bought from OS Disc online store.have tries different dvd roms and hdd no luck. windows 7 install fine and debian network install runs excellent. has sure got me puzzled. 

poorguy

---

### Post by codingman on 2015-01-04
Try installing Ubuntu without the use of the third party proprietary software. Nouveau works much better than the proprietary drivers, especially with the older models.

---

### Post by poorguy on 2015-01-04
hey all, i do believe you are on the right track as my issue does seem to be graphic relate and i base that only on problems simular that i have had in windows. i build most of my personal desktops and this one i salvaged from a death on big trash day as my neighbor was bringing it out to the curb. new power supply and here we are.

i would like to figure out why this problem occuered for future use and knowledge. being new to linux i have had to try different distros to find which i like, linux mint 17.1 seems to be a good one and i do like the debian 7.7 , i am sure that i will try the 2 that were mentioned above also. any help is very appretiated as this is new to me. interested and willing to learn linux thanks for the help and the space.

poorguy

---

### Post by poorguy on 2015-01-04
hey codingman, did try that after the 2nd install and still no difference. had found the commands and how to access the terminal that grahammechanical mentioned above and no change. i just don't know what to try. i have read that some prebuild motherboards just don't like linux as far as the drivers aren't released or availbe to linux. i really don't understand why the debian network install loaded and runs excellent but i am very glad it does so i am going to use it becuase i like it. i do agree that the unity desktop seems to be more resource demanding then linux mint or the debian desktop which is real cool. thanks for the help and the space. i may install a second hdd and keep trying as i would like to figure this out.

poorguy

---

### Post by poorguy on 2015-01-04
hey all, some hours later and into the terminal before entering password did my sudo apt-get update and the install ubuntu desktop and then install unity desktop and reboot bam i am up and working and i am more confused now then ever, as my iptables command notes are written all over everywhere i could. now with fingers crossed i will try to figure out exactly what i did. i was not going to give up. we will see how it runs and for now all is good and no more lock ups. thanks for the help you guys got me to the teminal to where i could work with the commands without lockups. 

happy poorguy

---

### Post by poorguy on 2015-01-04
it is all so true all good things come to an end. i thought i had solved my problem and for a couple of hours it seemed that i had and then for whatever reason or why desktop was locked up again same old same old except now after i enter my password it at least shows a locked up desktop with icons. too much headache and to many hours. i will just connect the debian hardrive back up and be happy. again thanks for all the help from all. 

poorguy

---

### Post by JeQhdMD on 2015-01-04
On many systems with nvidia or ati graphics, those closed-source drivers cannot be loaded at install and will often result in very slow screen rendering and system freezes.   Often, the "nomodeset" option has to be added to the startup sequence in grub2.  That will allow your system to be functional (but slow) so you can go to the system setting, software sources and install the restricted or proprietary drivers.   Once the nvidia drivers are installed this way, your whole system will run like new . . a major improvement.   

Another way around this, is to install Linux Mint . . . BUT, not the standard gnome3 based Cinnamon desktop.   Instead - install Linux Mint "Mate" desktop and all is good, as it doesn't require the accelerated graphics codecs to run.

---

### Post by poorguy on 2015-01-05
hey JeQhdMD, yep this has been a challenge may try what you are talking about later. the debian runs really well on this desktop so i may just stick with that for now. will look  into the linux mate and try it also. thanks. 

poorguy

---

### Post by poorguy on 2015-01-28
hey all back to this problem desktop that seems to only like debian wheezy 7.8 distro and hates other linux distros. anyway as i have a dual hdd setup i went and downloaded linux mint 17.1 mate and installed it and i was shocked it runs great and all that i had to do was install the nvidia proprietary tested driver that it recommends and that was it. don't understand exactly what the differences are from linux mint 17.1 mate disto and the debian wheezy 7.8 distro the only 2 that run and the differences in ubuntu 14.04 lts / linux mint 17.1 cinammon / zorin os 9 which will not run without freeze up or lock up. specs are already listed in earlier post. compaq cq5600f / amd x2 b24 processor / geforce se6150 nforce 430 integrated graphics / 3gb ddr2 ram / motherboard is a hp m2n68-la narra5 some oddball made for hp/compaq. just don't understand but there has to be something different since 2 out of the 5 i have tried do run. comfused.

poorguy

---

### Post by sgian on 2015-04-20
I have the same motherboard that worked for years fine with various ubuntu versions including 14.04 and 14.10 64 bit.  Then after an update (possibly a kernel update?)  it stopped working right, which is why I found this thread searching for support for this motherboard.  Ubuntu would freeze up on me, mouse wouldn't work, time would stay the same, and I would have to do a hard reboot after waiting 5-10 minutes.  Windows 7 works fine on this computer, and I took the computer in to a computer shop to get the hardware tested.  They couldn't find anything wrong.  I tried multiple times to reinstall Ubuntu 14.10 with download updates enabled, but I had multiple problems including the mouse not working during installation or the computer freezing up.  I even removed the Radeon R5400 graphics card and tried the motherboard's integrated graphics, but the same problems persisted.  So I installeed Ubuntu 13.10 64 bit from a dvd I burned in 2013, and it had no problems installing.  My suspicion is that this motherboard is no longer supported by Ubuntu, but I don't know for sure.  Can anyone confirm this?  

My specs are...
hp slimpc s5503w that I bought at walmart in 2010.
motherboard is m2n68-la
3 GB RAM
AMD Sempron 140 processor (single core 2.7 GHz)
graphics I tried were Radeon R5450 PCI card and then the integrated GeForce 6150SE nForce 430

---

