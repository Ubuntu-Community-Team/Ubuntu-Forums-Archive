---
title: "Computer slow"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by sacha98 on 2013-06-25
Hello everybody,
I just moved from windows to ubuntu 12.04
Unfortunately, the computer is slower with linux than it was with windows vista ... I guess that's not normal.
My CPU is an Intel E5200 and my graphic card an ATI HD4670.
What should I do ?

Thank you for your answers :o

---

### Post by HiImTye on 2013-06-25
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
are you using the proprietary drivers for your video card?

---

### Post by sacha98 on 2013-06-25
I have no idea, I'm using the ones that got installed with ubuntu

---

### Post by newb85 on 2013-06-25
Welcome to the forums and Ubuntu!

The results of the following commands would give us a better idea of what's going on.

```
sudo lshw -C processor
sudo lshw -C memory
sudo lshw -C display
```

You told us what your machine has.  This will tell us what Linux says your machine has, basically to make sure everything is being recognized and handled optimally.  Drag them into the terminal one line at a time.  After the first one, it will prompt you for a password.  Enter your user password for Ubuntu, and know that it won't give any visual feedback as you enter it.

---

### Post by sacha98 on 2013-06-25
sudo lshw -C processor```
  *-cpu                          description: CPU
       produit: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
       fabriquant: Intel Corp.
       identifiant matériel: 4
       information bus: cpu@0
       version: Pentium(R) Dual-Core CPU E5200 @ 2.50GHz
       numéro de série: To Be Filled By O.E.M.
       emplacement: Socket 775
       taille: 1200MHz
       capacité: 3800MHz
       bits: 64 bits
       horloge: 200MHz
       fonctionnalités: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq

```
sudo lshw -C memory```
  *-firmware              
       description: BIOS
       fabriquant: American Megatrends Inc.
       identifiant matériel: 0
       version: 0317
       date: 05/28/2008
       taille: 64KiB
       capacité: 960KiB
       fonctionnalités: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
  *-cache:0
       description: L1 cache
       identifiant matériel: 5
       emplacement: L1-Cache
       taille: 64KiB
       capacité: 64KiB
       fonctionnalités: internal write-back data
  *-cache:1
       description: L2 cache
       identifiant matériel: 6
       emplacement: L2-Cache
       taille: 2MiB
       capacité: 2MiB
       fonctionnalités: internal write-back instruction
  *-memory
       description: Mémoire Système
       identifiant matériel: 30
       emplacement: Carte mère
       taille: 2GiB
     *-bank:0
          description: DIMM DDR2 Synchrone 800 MHz (1,2 ns)
          produit: PartNum0
          fabriquant: Manufacturer0
          identifiant matériel: 0
          numéro de série: SerNum0
          emplacement: DIMM0
          taille: 1GiB
          bits: 64 bits
          horloge: 800MHz (1.2ns)
     *-bank:1
          description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-01-28 19:38+0000X-Generator: Launchpad (build 16451)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-01-28 19:38+0000X-Generator: Launchpad (build 16451) [vide]
          produit: PartNum1
          fabriquant: Manufacturer1
          identifiant matériel: 1
          numéro de série: SerNum1
          emplacement: DIMM1
     *-bank:2
          description: DIMM DDR2 Synchrone 800 MHz (1,2 ns)
          produit: PartNum2
          fabriquant: Manufacturer2
          identifiant matériel: 2
          numéro de série: SerNum2
          emplacement: DIMM2
          taille: 1GiB
          bits: 64 bits
          horloge: 800MHz (1.2ns)
     *-bank:3
          description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-01-28 19:38+0000X-Generator: Launchpad (build 16451)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-01-28 19:38+0000X-Generator: Launchpad (build 16451) [vide]
          produit: PartNum3
          fabriquant: Manufacturer3
          identifiant matériel: 3
          numéro de série: SerNum3
          emplacement: DIMM3

```
sudo lshw -C display
```
  *-display               
       description: VGA compatible controller
       produit: RV730XT [Radeon HD 4670]
       fabriquant: Hynix Semiconductor (Hyundai Electronics)
       identifiant matériel: 0
       information bus: pci@0000:01:00.0
       version: 00
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       ressources: irq:41 mémoire:e0000000-efffffff mémoire:feae0000-feaeffff portE/S:d000(taille=256) mémoire:feac0000-feadffff

```

---

### Post by trevm999 on 2013-06-25
Maybe we should do a quick check of your hard drive. Sometimes an OS installation can bring to light hard drive problems that you weren't aware of before. 
Download Gsmartcontrol from the Ubuntu Software Centre. Open it and double click on your hard drive. Go to the Attributes tab and tell us the Raw value for Reallocated Sector Count, Spin-up Retry Count, Reallocation Event Count, and Current Pending Sector Count. Also, you can go to the Perform Tests tab and select Short Self-Test then click Execute. You may also want to run the Long Self-Test but that will probably take around 2 hours.

---

### Post by HiImTye on 2013-06-26
try enabling the proprietary driver, llvmpipe is incredibly slow
[http://www.psychocats.net/ubuntu/drivers](http://www.psychocats.net/ubuntu/drivers)
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by newb85 on 2013-06-26
trevm999 may be onto something, but I suspect it's something much simpler than that a hard drive issue.

Linux running slower than Windows isn't normal, as long as you compare apples to apples.  In this case, we are comparing apples to oranges.  Windows Vista is a six-year old system.  Ubuntu Precise is a one-year old system.  Mainstream support for Vista ended the same month Precise was released.  The two have basically equivalent system requirements.

An apples-to-apples comparison would be Windows Vista to Ubuntu Gutsy (Gutsy would scream past Vista, though it would be much less glamorous) or Windows 8 to Precise (Precise would be faster).

Your hardware is definitely adequate to run Precise, but 2 GiB memory isn't all that generous, and neither is your Pentium dual-core.

Running an unsupported OS is generally a bad idea.  If the speed of Precise noticeably slower than Vista, but still definitely useable, my recommendation would be to stick with Precise.  It will be supported until April 2017, by which time your machine will basically be obsolete.

---

### Post by mastablasta on 2013-06-26
> **HiImTye said:**
> try enabling the proprietary driver, llvmpipe is incredibly slow
[http://www.psychocats.net/ubuntu/drivers](http://www.psychocats.net/ubuntu/drivers)


these won't work unless you've installed 12.04 or 12.04.1. but they will not work with latest 12.04.2 as AMD didn't do a driver update. they moved the card to legacy support. this means 12.10 and 13.04 will likely also give bad results unless opensource drivers (default) for your GPU chip improved a lot during this time.

so best suggestion is install 12.04 or 12.04.1 and then install additional drivers (proprietary) then it should work well.

option no. 2 - add opensource drivers PPA (xorg edgers) that will install latest opensource drivers.

another option (but this doesn't really solve the drivers issue) is to use a desktop that is not 3D accelerated (e.g. Xubutnu desktop or LUbuntu desktop)

---

### Post by claracc on 2013-06-26
You also could try to run the command top in terminal in order to see is thre is any proccess consumming too much CPU or memory.

---

### Post by sacha98 on 2013-06-26
> **trevm999 said:**
> Maybe we should do a quick check of your hard drive. Sometimes an OS installation can bring to light hard drive problems that you weren't aware of before. 
Download Gsmartcontrol from the Ubuntu Software Centre. Open it and double click on your hard drive. Go to the Attributes tab and tell us the Raw value for Reallocated Sector Count, Spin-up Retry Count, Reallocation Event Count, and Current Pending Sector Count. Also, you can go to the Perform Tests tab and select Short Self-Test then click Execute. You may also want to run the Long Self-Test but that will probably take around 2 hours.
My main hard drive :
reallocated sector count : 1
Spin-up Retry Count : 3
Reallocation Event Count : didn't find that one
Current Pending Sector Count : 0

The secondary one :
reallocated sector count : 0
Spin-up Retry Count : 0
Reallocation Event Count : 0
Current Pending Sector Count : 0

both tests completed without error 
> **HiImTye said:**
> try enabling the proprietary driver, llvmpipe is incredibly slow
[http://www.psychocats.net/ubuntu/drivers](http://www.psychocats.net/ubuntu/drivers)
It only says "no proprietary drivers are in use on this system" and nothing else ...

> **newb85 said:**
> trevm999 may be onto something, but I suspect it's something much simpler than that a hard drive issue.

Linux running slower than Windows isn't normal, as long as you compare apples to apples.  In this case, we are comparing apples to oranges.  Windows Vista is a six-year old system.  Ubuntu Precise is a one-year old system.  Mainstream support for Vista ended the same month Precise was released.  The two have basically equivalent system requirements.

An apples-to-apples comparison would be Windows Vista to Ubuntu Gutsy (Gutsy would scream past Vista, though it would be much less glamorous) or Windows 8 to Precise (Precise would be faster).

Your hardware is definitely adequate to run Precise, but 2 GiB memory isn't all that generous, and neither is your Pentium dual-core.

Running an unsupported OS is generally a bad idea.  If the speed of Precise noticeably slower than Vista, but still definitely useable, my recommendation would be to stick with Precise.  It will be supported until April 2017, by which time your machine will basically be obsolete.My windows seven on a bad laptop is also faster !
Should I move to xubuntu or something like that ?

> **mastablasta said:**
> these won't work unless you've installed 12.04 or 12.04.1. but they will not work with latest 12.04.2 as AMD didn't do a driver update. they moved the card to legacy support. this means 12.10 and 13.04 will likely also give bad results unless opensource drivers (default) for your GPU chip improved a lot during this time.

so best suggestion is install 12.04 or 12.04.1 and then install additional drivers (proprietary) then it should work well.

option no. 2 - add opensource drivers PPA (xorg edgers) that will install latest opensource drivers.

another option (but this doesn't really solve the drivers issue) is to use a desktop that is not 3D accelerated (e.g. Xubutnu desktop or LUbuntu desktop)How do I know if I have 12.04/12.04 1 or 12.04 2?

> **claracc said:**
> You also could try to run the command top in terminal in order to see is thre is any proccess consumming too much CPU or memory.```

top - 12:32:45 up  3:19,  2 users,  load average: 0.24, 0.63, 0.62
Tasks: 178 total,   2 running, 176 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.8%us,  2.2%sy,  0.0%ni, 92.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2050544k total,  1946536k used,   104008k free,    59656k buffers
Swap:  2094076k total,    21580k used,  2072496k free,   839728k cached


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 9767 dieryck   20   0  101m  16m 4984 S    5  0.8   0:00.16 python             
 1564 dieryck   20   0 1437m  99m  36m S    5  5.0   2:45.98 compiz             
 1095 root      20   0  175m  57m  10m S    3  2.9   6:54.08 Xorg               
 9351 dieryck   20   0  378m 103m  35m S    2  5.1   0:21.91 skype              
 9700 dieryck   20   0  523m  18m  12m S    2  0.9   0:00.56 gnome-terminal     
 1394 dieryck   20   0 27856 3696  612 S    1  0.2   0:04.89 dbus-daemon        
 9764 dieryck   20   0 17340 1324  936 R    1  0.1   0:00.06 top                
   10 root      20   0     0    0    0 S    0  0.0   0:02.87 ksoftirqd/1        
 1213 root      20   0     0    0    0 S    0  0.0   0:00.65 wlan1              
 3891 dieryck   20   0  892m  69m  23m S    0  3.5   0:22.25 chromium-browse    
    1 root      20   0 24568 2180 1356 S    0  0.1   0:00.52 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:02.93 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.03 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.03 watchdog/0  

```

---

### Post by newb85 on 2013-06-26
> **sacha98 said:**
> 

My windows seven on a bad laptop is also faster !


What do you mean by "bad laptop"?  

> **sacha98 said:**
> 

How do I know if I have 12.04/12.04 1 or 12.04 2?



```
lsb_release -a
```

---

### Post by sacha98 on 2013-06-26
Well,I don't remember the CPU in the laptop anymore but it is pretty slow
Ok so I have ubuntu 12.04 2
How can I go to 12.04 1 to get the drivers ? What other differences are there with 12.04 2 ?

---

### Post by newb85 on 2013-06-26
> **sacha98 said:**
> Well,I don't remember the CPU in the laptop anymore but it is pretty slow
Ok so I have ubuntu 12.04 2
How can I go to 12.04 1 to get the drivers ? What other differences are there with 12.04 2 ?

You can download the .iso for 12.04.1 at [http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

---

### Post by gnjepar on 2013-06-26
In my experience Ubuntu is always slower than W7. Unless you are an expert in optimizing and removing what is not needed in Ubuntu than W7 is a better choice than Ubuntu. But there is Xubuntu which is the best choice :D I'm speaking in terms of 'old' hardware (dual core with <= 2GB memory).

You can try downloading from [here]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx") and following instructions.

---

### Post by sacha98 on 2013-06-26
So do I need to install it all all over again ? Isn't it possible to keep my applications and everything ?

---

### Post by newb85 on 2013-06-26
If you set up UbuntuOne, you can use it to back up your list of installed applications (through the software center).

---

### Post by trevm999 on 2013-06-26
> **sacha98 said:**
> My main hard drive :
reallocated sector count : 1
Spin-up Retry Count : 3
Reallocation Event Count : didn't find that one
Current Pending Sector Count : 0

The secondary one :
reallocated sector count : 0
Spin-up Retry Count : 0
Reallocation Event Count : 0
Current Pending Sector Count : 0

both tests completed without error 


One reallocated sector can be a sign that your hard drive is failing, but it could also be fine if the problem is just isolated to that one sector. However, Spin-up Retry is bad news, I always replace a hard drive if it has any value other than 0 for that.

---

### Post by gnjepar on 2013-06-27
Since the drive is not spinning up and down all the time I would exclude HDD as a source of your problem.

---

### Post by sacha98 on 2013-06-27
> **trevm999 said:**
> One reallocated sector can be a sign that your hard drive is failing, but it could also be fine if the problem is just isolated to that one sector. However, Spin-up Retry is bad news, I always replace a hard drive if it has any value other than 0 for that.Thanks for the info. As all my important files are saved on other drives as well, I'm gonna keep that one for the moment.

For the slow problems. I understand two things, xubuntu might be a good alternative and I should install the proprietary drivers. So, isn't it possible to install the proprietary drivers in ubuntu 12.04 2 from this website [http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx) ?

I saw that it is quite easy to install xubuntu next to ubuntu. But then I guess I will have xubuntu 12.04 2 and I won't be able to download the proprietary drivers either ?

---

### Post by newb85 on 2013-06-27
From the AMD support website you indicated:
> Description:  Automated installer and Display Drivers for Xorg 6.9 to Xserver **1.12** and Kernel version up to **3.4**

12.04.2 was bumped up to Xserver 1.13 and Linux Kernel 3.5.

---

### Post by trevm999 on 2013-06-27
> **gnjepar said:**
> Since the drive is not spinning up and down all the time I would exclude HDD as a source of your problem.

The point is that the drive is failing, not that the spin retries are directly causing the problem. A failing drive often causes performance issues. It is possible that it might not be the cause here, so I'll watch and see how things turn out.

---

### Post by gnjepar on 2013-06-28
Sure, the drive is failing, like half of them out there, especially in notebooks. This does not mean drive is causing his problems. Best thing to do is to eliminate the HDD as a potential source of problems. Drive performance can be easily checked out using hdparam and Disk Utility, click [here]("http://askubuntu.com/questions/87035/how-to-check-hard-disk-performance") for more info.

---

### Post by sacha98 on 2013-06-28
So this is what I got for the HDD :
```
dieryck@dieryck:~$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   1904 MB in  2.00 seconds = 951.35 MB/sec
 Timing buffered disk reads: 230 MB in  3.07 seconds =  74.92 MB/sec
dieryck@dieryck:~$ 



```
disk utility gives me average read rate : 87.6 mb/s
average access time 14.3ms

So it looks like the hdd isn't the problem.


One more thing, in system parameter -> details (my computer is in french so its just a bad translation from the menu's name) it says graphic card unknown
and in graphic cards it says driver : unknown, experience : standard.

So I suppose the graphic card is the real problem here.

So I'm gonna move to ubuntu 12.04 1
If I want to use xubuntu, will it beas fast if I first install ubuntu and then use sudo apt=get install xubuntu-desktop ?

Edit : One more thing, what is the difference between ubuntu 12.04 2 and 12.04 1 ?
Edit 2 : I have found this, do you think I should try it ? [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/129200#129200](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/129200#129200)
[http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html](http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html)

---

