---
title: "Tired of freezing.."
date: 2013-02-06
forum: New to Ubuntu
---

### Post by mark1.0 on 2013-02-06
I've learned a lot the two years I've been using Ubuntu LTS, now at 12.04, which I don't care for as much as 10.04. I can't remember any major issues w/ 10.04.  Only after 12.04 came available did I start having probs. with 10.04.    I upgraded and things started going down hill.   

Now I routinely freeze up 2-3 or more times a day.  I've researched all over and tried everything under the sun that my limited knowledge can feel comfortable trying.  
I would say I'm an advanced beginner.  In any event although the mouse still moves the cursor, all else is frozen solid and my only option is power down and back up.  Nothing else works. 

I tried other browsers besides FF, even Google Chrome but from what I read I wasn't expecting a change and didn't get one.  

This has become a complete pain in the ass and since my time is spent browsing almost entirely, I'm going to look into Chromebooks.

---

### Post by DuckHook on 2013-02-06
Welcome to the forums. Perhaps we can help in some way.

Many of my old machines broke with the upgrade to 12.04 as well. Like you, I upgraded basically from one LTS to another, so it was suddenly Unity and all the trappings (both wanted and unwanted) all in one shot.

Many of the problems in upgrades arise from the graphics subsystem. Unity is far more resource intensive than the older DEs, and many graphics cards worked well for the old 2D DEs but suddenly started to choke on 3D. Also, a number of driver issues seemed to crop up concurrently. Don't know why. The upshot was that we were suddenly getting a lot of graphics issues with the upgrade to 12.04.

To start with, please describe your system. If you know the details, please provide cpu, system RAM, video chipset and video RAM. Also, any unusual peripherals. Are you using proprietary drivers or the open source drivers native to Ubuntu? If easier for you, just post the results of the following, which will tell us what we need to know:

```
lspci -vk | grep -iA10 vga
``````
sudo lshw -C processor
``````
free -m
``````
df -h
```What are you doing when it freezes? Is there one program that invariably causes it to freeze or does it happen randomly? Does it sometimes freeze even if you are doing nothing?

If all you do is browse, you may even want to invest in a tablet which I've found to be a great tool for pure browsing. However, this won't get your current machine working, and I suspect that it won't be that difficult to make some recommendations that could make you a lot happier. Are you prepared to go to a lighter distro?

Last but not least, the next time the system freezes up, try to get to another console with <Ctrl>+<Alt>+<F1>. Then, login and do:

```
sudo shutdown -P now
```

If that doesn't work, try <Ctrl>+<Alt>+<del> and then <Ctrl>+<Alt>+<Backspace>. There are further ways to shut down cleanly, but would be a little overwhelming in one post.

---

### Post by hmag on 2013-02-13
hello

I am also tired of freezing with 12.04 LTS.

Below my info ...
PLEASE HELP !!!

Thanks
HMag

```

root@hubuntu:~# lspci -vk | grep -iA10 vga
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV410 [Radeon X700 (PCIE)] (prog-if 00 [VGA controller])
    Subsystem: PC Partner Limited Device 0670
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe9e0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at c000 [size=256]
    Expansion ROM at fe9c0000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Advanced Error Reporting


root@hubuntu:~# lshw -C processor
  *-cpu:0                 
       description: CPU
       produit: Intel(R) Core(TM)2 Duo CPU     E7500  @ 2.93GHz
       fabriquant: Intel Corp.
       identifiant matériel: 4
       information bus: cpu@0
       version: 6.7.10
       numéro de série: 0001-067A-0000-0000-0000-0000
       emplacement: LGA775
       taille: 1603MHz
       capacité: 3800MHz
       bits: 64 bits
       horloge: 266MHz
       fonctionnalités: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
       configuration: cores=2 enabledcores=2 id=1 threads=2
     *-logicalcpu:0
          description: CPU Logique
          identifiant matériel: 1.1
          bits: 64 bits
          fonctionnalités: logical
     *-logicalcpu:1
          description: CPU Logique
          identifiant matériel: 1.2
          bits: 64 bits
          fonctionnalités: logical
  *-cpu:1
       identifiant matériel: 1
       information bus: cpu@1
       version: 6.7.10
       numéro de série: 0001-067A-0000-0000-0000-0000
       taille: 1603MHz
       capacité: 1603MHz
       fonctionnalités: vmx ht cpufreq
       configuration: id=1
     *-logicalcpu:0
          description: CPU Logique
          identifiant matériel: 1.1
          fonctionnalités: logical
     *-logicalcpu:1
          description: CPU Logique
          identifiant matériel: 1.2
          fonctionnalités: logical


root@hubuntu:~# free -m
             total       used       free     shared    buffers     cached
Mem:          4027        963       3064          0         87        515
-/+ buffers/cache:        359       3667
Swap:         5721          0       5721


root@hubuntu:~# df -h
Sys. fich.          Taille Util. Dispo Uti% Monté sur
/dev/sdb3              34G  3,5G   29G  11% /
udev                  2,0G  4,0K  2,0G   1% /dev
tmpfs                 806M  900K  805M   1% /run
none                  5,0M     0  5,0M   0% /run/lock
none                  2,0G  160K  2,0G   1% /run/shm
/dev/sdb1              74G  339M   70G   1% /home
/home/hmag/.Private    74G  339M   70G   1% /home/hmag


```

---

### Post by aspergerian on 2013-02-13
I too made the mistake of going from 10.04 to 12.04. My computer didn't freeze but it ran much slower. Also, I neither needed nor wanted 12.04's desktop. You might try Xubuntu. I like it; it does what I need; and (with forum help) I even was able to create a 10.04-like desktop.

---

### Post by Gone fishing on 2013-02-13
Odd I’ve got 1 desktop and 4 laptops running Ubuntu on one laptop the browser (I tried Mozilla and Chrome) would freeze X it was a laptop I upgraded from 11.10 and I couldn't be bothered to chase down the problem and installed the latest Mint no problem, however, I prefer Unity to Cinnamon and did a fresh install of 12.04 and it started freezing with the browser. I guess it must be something to do with the video driver (opensource ATI). I upgraded to 12.10   and the problem went away.

---

### Post by hmag on 2013-02-14
Thanks, friends,

I just installed the xubuntu-desktop.
Seems fine... I am not married with Gnome ;-)

Thanks & bye
Cheers

):P   HMag

---

### Post by tgalati4 on 2013-02-14
If you want the look and feel of 10.04, then I would give Linux Mint MATE 14 a spin.

I have it running on 4 machines, 2 laptops and 2 desktops.  No (major) problems, and performance is decent.

---

