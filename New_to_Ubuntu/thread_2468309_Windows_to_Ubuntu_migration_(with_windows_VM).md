---
title: "Windows to Ubuntu migration (with windows VM)"
date: 2021-10-25
forum: New to Ubuntu
---

### Post by penn919 on 2021-10-25
I've always planned on eventually making the move to Linux from windows, eventually, mainly to break free from dependence on paid software. With the news of strict hardware requirements and optimization issues on AMD hardware, it seems now is a good time to plot out my move. Windows 10 support will end in less than 4yrs 10/14/2025, so I figure I'd best start the planning phase now.

My idea is to make an image of my current windows installation and then recover it onto a VM within Ubuntu. My system specs are as follows:

CPU: Ryzen 1700x
Ram: 16GB DDR4 3000MHZ
GPU: AMD RX Vega56, Nvidia GT 710
Motherboard: Asrock Fatal1ty AB350 Gaming K4
Storage: 250GB Samsung SSD, 1TB Samsung SSD, 6TB Seagate HDD

I'm wondering if my system is adequate for VM and whether or not I can anticipate any challenges with my current hardware config. I've used Linux in the past and one of the pitfalls then was hardware compatibility (especially with GPUs). This post is mainly for feedback and intelligence gathering. I figure earlier planning will translate to a smoother transition.

---

### Post by Tadaen_Sylvermane on 2021-10-25
I think you've got more than enough there to run a vm well . I run games (world of warcraft, skyrim and such) with pci pass through on an intel i5 3470, 16gb of ram, 120gb ssd + 250gb ssd in a lvm volume group on a basic mATX board and an RX570. I ususally stream them to the Linux side over the steam in home streaming. Not perfect but it's livable. Does run better with a dedicated screen and kb / mouse though. I have found some issues that I think are related to threading (one should probably do cpu pinning) and I haven't enough cores over all to do that at the moment. May change to a 3770 4c/8t. would help.

---

### Post by oldfred on 2021-10-25
I do not use Windows, but just saw this post:

Windows 11 as KVM virtual install 
[https://ubuntuforums.org/showthread.php?t=2468297](https://ubuntuforums.org/showthread.php?t=2468297)

---

### Post by ActionParsnip on 2021-10-25
What applications do you use in Windows that makes you want to keep the install? In short, why bother with the Windows OS?

---

### Post by TheFu on 2021-10-25
I ran 15 VMs on a Core2 Duo system in 2010.  One of those was Win7 Ultimate with all the bloat that includes.

Today a Ryzen 2600 (13K passmarks) is my VM host, which is about the same speed as the 1700x (15.5k passmarks) and easily runs 20 VMs and 4 linux containers. It uses a little over 16G of RAM, but that can easily be controlled by limiting the concurrent VMs running and not over allocating limited resources to VMs.  In general, I give a Linux VM, 1vCPU and 1GB of RAM, unless I 100% KNOW is needs more.  My normal desktop runs inside a VM an get 3G of RAM with 1 vCPU.  A Windows VM gets 3GB of RAM and 2 vCPUs, but it is powered off almost all the time.

I think the harder problem is the expectation that you can move a physical install of Windows into a VM.  I don't think that is possible due to license restructions. The license keys typically are tied to hardware. MSFT license registration keeps up with the underlying hardware.  Retail copies of Windows get a little more leeway, but pre-installed ones do not. The license key is stored in hardware.   It is also possible that MSFT has become less picky with licenses being tied to hardware.  I have doubts about that, but I've been burned by MSFT too many times. [https://www.zdnet.com/article/microsoft-quietly-rewrites-its-activation-rules-for-windows-10/](https://www.zdnet.com/article/microsoft-quietly-rewrites-its-activation-rules-for-windows-10/) has some info about the Win10 rules. Seems too complicated to me.

Even I, die-hard Linux lover, still have to use Windows for a few programs that I've not found acceptable alternatives in other OSes. I've come close a few times.  Even wrote my own TV schedule parsing and recording scripts when 7MC support ended, which I've been using about 2 yrs now.  Many people would use online services for this, but I'm a bit of a privacy freak. The last thing I need is yet another online account, somewhere, to track our stuff. 

I have moved a Windows VM from 1 VM host to another running a different version of KVM.  There was a Windows tool - sysprep - which removed all the drivers and told the Windows system to expect fresh hardware on the next boot. This is more about Windows and I don't know if Win10/11 have it. Sorry.  

I've also migrated entire Linux install with VMs on them to newer hardware at least 3 times.  The only problem I've had there was self-inflicted - going from Intel CPUs to Ryzen by forgetting to tell the VM config about that change in 1 VM (I remembered in all the others) caused a problem. I just moved a full install from a Pentium dual-core to a Ryzen 5600G a few days ago.  There wasn't any MS-Windows involved and the VMs were setup to use the host CPU, so they all worked, but I did have a boot issue because the system directly specified the ethernet adapter from the old system (a Marvell Gbps NIC) and the new system is full of Intel i211 and 82575GB NICs.  None of them were configured, so no networking would start ... so no network services on the system would start.  It was bad and took me far to long to realize (embarrassing).  Once I figured that out, then the igpx Radeo wasn't supported by the Ubuntu 18.04 5.4.x kernel, so it was running in VESA mode.  The fix I chose for that was to load a non-mainstream kernel to get newer hardware support:
```
$ uname -r
5.11.20-051120-generic
```
It has been stable, so far.

If it were me, I'd get a new SSD/HDD ($50) and leave the old install alone, migrating things to the new install with little risk. That way, if it goes well, you have a good backup storage device left over and if it goes badly, you can swap the new storage for the old storage with little/zero risk.  Just don't leave them both connected at the same time.

---

### Post by penn919 on 2021-10-26
> **Tadaen_Sylvermane said:**
> I think you've got more than enough there to run a vm well . I run games (world of warcraft, skyrim and such) with pci pass through on an intel i5 3470, 16gb of ram, 120gb ssd + 250gb ssd in a lvm volume group on a basic mATX board and an RX570. I ususally stream them to the Linux side over the steam in home streaming. Not perfect but it's livable. Does run better with a dedicated screen and kb / mouse though. I have found some issues that I think are related to threading (one should probably do cpu pinning) and I haven't enough cores over all to do that at the moment. May change to a 3770 4c/8t. would help.

I've got a fair amount of steam games I haven't finished playing through, so I do intend to make use of my Vega. I remember seeing a Level1Linux video about PCI passthrough but honestly I still don't know too much about it. I was under the impression that linux gaming support was gaining traction via native support and platforms like SteamOS+Proton and Stadia (stadia requires Linux ports for all games). I do anticipate there'll be a 1:1 ratio in terms of game playability eventually.  Is there a significant advantage with PCI passthrough over the current software solutions? I might try it if it's worth while.

---

### Post by penn919 on 2021-10-26
> **oldfred said:**
> I do not use Windows, but just saw this post:

Windows 11 as KVM virtual install 
[https://ubuntuforums.org/showthread.php?t=2468297](https://ubuntuforums.org/showthread.php?t=2468297)

I'll be avoiding Windows 11, but I'll use it as one of my references for my Windows 10 VM. Btw, it's nice to see a fellow SW Floridian on here :cool:

---

### Post by Tadaen_Sylvermane on 2021-10-27
It's really quite easy to do. I followed this guide. Simple enough. [https://mathiashueber.com/pci-passthrough-ubuntu-2004-virtual-machine/](https://mathiashueber.com/pci-passthrough-ubuntu-2004-virtual-machine/) Performance isn't different enough to be worth mentioning. I did use the Xanmod kernel and kisak mesa drivers though. I have strong suspicions that if I had the core count I could pin 4 cpus to the vm and it would be indistinguishable from bare metal.

*EDIT* Just noticed the guide uses teh Ryzen x1800. You have a x1700. should be nearly straight across.

---

### Post by penn919 on 2021-10-27
> **ActionParsnip said:**
> What applications do you use in Windows that makes you want to keep the install? In short, why bother with the Windows OS?

Right now, it's just a contingency measure. I haven't actually gone through my complete list of programs to find out which has native support and which will need to be replaced with an alternative. Right now, I'm expecting that there'll be at least a few programs I'll need Windows for. After about a year or so into the migration, The list of "Windows-bound" programs that I can't do without should be clear. If it turns out I really don't need the VM, then it should be easy enough to dismantle....I hope. 

> **TheFu said:**
> 

I think the harder problem is the expectation that you can move a physical install of Windows into a VM.  I don't think that is possible due to license restructions. The license keys typically are tied to hardware. MSFT license registration keeps up with the underlying hardware.  Retail copies of Windows get a little more leeway, but pre-installed ones do not. The license key is stored in hardware.   It is also possible that MSFT has become less picky with licenses being tied to hardware.  I have doubts about that, but I've been burned by MSFT too many times. [https://www.zdnet.com/article/microsoft-quietly-rewrites-its-activation-rules-for-windows-10/](https://www.zdnet.com/article/microsoft-quietly-rewrites-its-activation-rules-for-windows-10/) has some info about the Win10 rules. Seems too complicated to me.

Even I, die-hard Linux lover, still have to use Windows for a few programs that I've not found acceptable alternatives in other OSes. I've come close a few times.  Even wrote my own TV schedule parsing and recording scripts when 7MC support ended, which I've been using about 2 yrs now.  Many people would use online services for this, but I'm a bit of a privacy freak. The last thing I need is yet another online account, somewhere, to track our stuff. 

I have moved a Windows VM from 1 VM host to another running a different version of KVM.  There was a Windows tool - sysprep - which removed all the drivers and told the Windows system to expect fresh hardware on the next boot. This is more about Windows and I don't know if Win10/11 have it. Sorry.  



If it turns out that the only issue would be licensing, then that would be Okay. I've discovered that activation in Windows 10 is surprisingly lenient. If you're activating windows on a "fresh" motherboard (not used with windows 10 previously) then normally you can get away with using your Microsoft account to activate it because windows licenses are now tied to whatever account you sign in with. Since I refurbish laptops as a side-hustle, I've accumulated quite a few licenses on one of my accounts. I just revert to a generic local account before resale. (side note) I sell them with User accounts pre-configured and service packs installed due to complaints of performance issues...it's usually just a ton of updates that slam the machine in the background after initial setup.

btw, Since the motherboard I'll be using with the VM is the same as now, wouldn't it automatically activate? I don't know if Windows' motherboard detection behaves differently under VM. Btw, I'm running Windows 10 already.

---

### Post by penn919 on 2021-10-27
> **Tadaen_Sylvermane said:**
> It's really quite easy to do. I followed this guide. Simple enough. [https://mathiashueber.com/pci-passthrough-ubuntu-2004-virtual-machine/](https://mathiashueber.com/pci-passthrough-ubuntu-2004-virtual-machine/) Performance isn't different enough to be worth mentioning. I did use the Xanmod kernel and kisak mesa drivers though. I have strong suspicions that if I had the core count I could pin 4 cpus to the vm and it would be indistinguishable from bare metal.

*EDIT* Just noticed the guide uses teh Ryzen x1800. You have a x1700. should be nearly straight across.

I suppose it wouldn't hurt to have the Passthrough configured on top of Native/Steam+Proton support. The more options the better. Thanks for the Guide!

---

### Post by TheFu on 2021-10-28
That "simple" guide is about 10 pages of technical stuff - any wrong step and it won't work.  Swapping out the supported kernel? Really? Also, who has multiple $250/ea GPUs in their system? I doubt that 710 GT will work, but I don't know.

OTOH, perhaps it is simple for some people.

> btw, Since the motherboard I'll be using with the VM is the same as now, wouldn't it automatically activate? I don't know if Windows' motherboard detection behaves differently under VM. Btw, I'm running Windows 10 already. 
The real hardware isn't seen under a VM, unless that specific component is passed through using IOMMU.  You cannot pass the entire motherboard thru - sorry.

---

### Post by penn919 on 2021-10-29
> **TheFu said:**
> 

The real hardware isn't seen under a VM, unless that specific component is passed through using IOMMU.  You cannot pass the entire motherboard thru - sorry.
...and this is why I started this thread. I was unaware of that. I'll attempt the microsoft sign-in method first before exploring other options. Assuming Windows hasn't the ability to detect the VM, it should just treat the "new" mobo as a hardware change.

---

### Post by TheFu on 2021-10-29
Create a new VM.  If you make it Linux, then we can guide with commands to see the hardware presented.  **inxi -Fxxx** is a start.  Look that over.  The motherboard, BIOS, CPU, GPU, networking, and disks are all virtual devices.  The best performance comes when we choose "virtio" as the devices when that is possible.  That goes for disks, NICs, and if your hypervisor is new enough, the GPU.  Changing the CPU model is possible, but the only reason to do that would be in support of automatic failover to another hypervisor.  For years, I emulated Core2Duo CPUs even when the main system had a Core i5 - that was purely for failover needs.  It wouldn't do to have new instructions used on a CPU without those instructions.  I'm setting up a Ryzen failover system in the next few weeks.  But the CPUs are 2xxx and 5xxx series, so I need to ensure only 2xxx instructions are used.

VMs have a whole new world of skills.  Running Windows inside VMs brings even more.  I've never seen Win10/11.  Don't like the license agreement, so it isn't allowed on the LAN. Not everyone can do that.  But with older Windows licenses, swapping the motherboard was sufficient reason to require a new license and pre-installed licenses couldn't be moved, just retail.  With retail licenses being moved, I've always had to speak with someone at MSFT to get the license approved on a new system. It was never automatic unless swapping a GPU or something trivial like that.  vmvga, cirrus, qxl, and now we have virtvid as an option.  My hypervisors are too old to have virt-io for the GPU, so I don't have any experience with it.  Plus, I tend to access any graphic desktops over the network, not from the physical system running the hypervisor.  For me, the network is the computer has been how I've done things 25 yrs and I'm not going to sit in the same room with a computer just for graphics.

An example of virtio for NICs .... iperf3 can show the maximum transfers possible:
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  5] local 172.22.22.3 port 32786 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec  3.01 GBytes  25.9 Gbits/sec    0   2.25 MBytes       
[  5]   1.00-2.00   sec  2.91 GBytes  25.0 Gbits/sec    0   2.25 MBytes       
[  5]   2.00-3.00   sec  3.29 GBytes  28.2 Gbits/sec    0   2.25 MBytes       
[  5]   3.00-4.00   sec  3.17 GBytes  27.2 Gbits/sec    0   2.25 MBytes       
[  5]   4.00-5.00   sec  3.31 GBytes  28.4 Gbits/sec    0   2.25 MBytes       
[  5]   5.00-6.00   sec  3.20 GBytes  27.4 Gbits/sec    0   2.25 MBytes       
[  5]   6.00-7.00   sec  3.15 GBytes  27.1 Gbits/sec    0   2.25 MBytes       
[  5]   7.00-8.00   sec  3.10 GBytes  26.6 Gbits/sec    0   2.62 MBytes       
[  5]   8.00-9.00   sec  2.80 GBytes  24.0 Gbits/sec    0   2.62 MBytes       
[  5]   9.00-10.00  sec  2.90 GBytes  24.9 Gbits/sec    0   2.75 MBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  30.8 GBytes  26.5 Gbits/sec    0             sender
[  5]   0.00-10.00  sec  30.8 GBytes  26.5 Gbits/sec                  receiver
```
That test was between a VM and the hostOS, but it is the same for connections between 2 VMs on the same host too.  **25 Gbps. Not bad, right?**  The physical system has some Intel GigE NICs, but not 25 Gbps worth.  Of course, the same test between a VM and a different physical system drops back to whatever the physical NIC can handle ....
```
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  1.10 GBytes   943 Mbits/sec  270             sender
[  5]   0.00-10.00  sec  1.10 GBytes   941 Mbits/sec                  receiver
```
That's typical GigE connectivity.

---

### Post by Tadaen_Sylvermane on 2021-10-30
> **TheFu said:**
> That "simple" guide is about 10 pages of technical stuff - any wrong step and it won't work.  Swapping out the supported kernel? Really? Also, who has multiple $250/ea GPUs in their system? I doubt that 710 GT will work, but I don't know.

OTOH, perhaps it is simple for some people.


The real hardware isn't seen under a VM, unless that specific component is passed through using IOMMU.  You cannot pass the entire motherboard thru - sorry.

It all works for a default Ubuntu install. I did the kernel of my own volition. However if the hardware can't do it then you are screwed. I also did it with an RX570 to the vm and the built in motherboard graphics to the host. Of that whole guide all I had to do was make sure the cpu supported iommu, and enable it + the vfio-pci.ids in the /etc/default/grub. Didn't even bother to look at the other pages. Quite simple.

---

### Post by penn919 on 2021-10-30
> **Tadaen_Sylvermane said:**
> ... I also did it with an RX570 to the vm and the built in motherboard graphics to the host. Of that whole guide all I had to do was make sure the cpu supported iommu, and enable it + the vfio-pci.ids in the /etc/default/grub. Didn't even bother to look at the other pages. Quite simple.

That's interesting. I have an AM4 board that has no IGP; however, I have a GT 710 and an AMD RX Vega 56. I'm guessing I'd reserve the Vega for the VM and the 710 for the Host...but would that be permanent? Would I have the ability to use the Vega with Ubuntu when I'm not running the VM?

---

### Post by bunny9000 on 2021-10-30
GPU passthrough is a bit of a meh. Win 10 removed remotefx due to security issues except for maybe win 10 pro. dgpu is something that may work. Virtualbox sort of supports GPU passthrough, but the support is better for Linux and no surprise hyper v gpu passthrough is better for Windows. You might be just have to be a bit creative or and keep a physical box around for when you need whatever the windows GPU power is needed for.

Personally stay away from that side of things. There are plenty of companies running virtualized GPUS in servers for end users so it must be possible.

For the migrate Macrium reflect free is a good option as it will take an image of your drive only the making it to the size of the installed data. You can then create a backup disk to boot into via your vm and then pull the image in over a mounted drive or network share.

---

### Post by Tadaen_Sylvermane on 2021-11-02
I apologize if my last reply was a bit rude or condescending. Bad day. At any rate it is simple for a person who's been rolling linux / open source for awhile. If not then it can be a risk, yes. Make sure to dot your i's and cross your t's so to speak. The guide must be used in generalizations, not specific hardware as they suggest. If your hardware is capable, then it will work most likely.

I should say though that recently I did try again with the vm using a passed through ssd and the hugepages thing (needs to be enabled outside of the guide) and the performance was better however it did not match a bare metal run. In my case with World of Warcraft I noticed a good 20-30 fps lower performance in the latest expac main hub vs bare metal Windows performance. Still 40+ but when you are used to 70-90 on Windows it's a big loss.

My apologies again.

---

