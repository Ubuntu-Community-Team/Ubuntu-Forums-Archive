---
title: "How I can Run Ubuntu and Wondows Simultaneously?"
date: 2020-10-20
forum: New to Ubuntu
---

### Post by dezintop on 2020-10-20
Hi there.

I'm new here. Hope to learn linux this time. Please guide me to my question:

How I can Run Ubuntu and Wondows Simultaneously?

I'm using currently windows 10

---

### Post by mastablasta on 2020-10-20
install a subsystem in windows.
install virtualbox and with enough ram you can run many OS "simultaneously".

but all in all on PC (bare metal) only one OS can run at one time.

---

### Post by dezintop on 2020-10-20
> **mastablasta said:**
> install a subsystem in windows.
install virtualbox and with enough ram you can run many OS "simultaneously".

but all in all on PC (bare metal) only one OS can run at one time.

what is the ram requirement.

> **mastablasta said:**
> install a subsystem in windows.
install virtualbox and with enough ram you can run many OS "simultaneously".

but all in all on PC (bare metal) only one OS can run at one time.

how to install the subsystem? any tutorial?

hello @mastablasta

---

### Post by Impavidus on 2020-10-20
To run two operating systems simultaneously, you need two machines. Ideally two real machines, but you can get away with one real and one virtual machine. Install the OS you'll use most of the time on the real machine, install the other on the virtual machine. Performance of the virtual machine will be a bit less than a real machine, depending on what applications you run. Graphics in particular will be worse. Memory requirement is close to the sum of memory requirements of the individual systems.

There's also the possibility of dual booting. That allows you to have both OSs installed at the same time on a single real machine, but you can only run one at a time, choosing at boot. To switch operating system, reboot. Unfortunately, dual booting is not as easy and reliable as it used to be, due to changes in Windows.

When using virtual machines, the client can't damage the host (and the host is unlikely to damage the client). When dual booting, both systems can damage the other. Windows has a history of damaging Linux automatically when installing upgrades and Linux makes it really easy for the user to damage Windows.

Windows Subsystem for Linux is a partial Linux environment that can be installed on Windows. I don't know the details; Wikipedia tells me it's somewhere between a compatibility layer and a virtual machine. It's not a proper Linux system, but may be useful if you want to run a few Linux applications on Windows, similar to how Linux users can use Wine to run some Windows applications on Linux.

---

### Post by metacell on 2020-10-20
You mean you want to run Linux and Windows apps at the same time, not just switch between Linux and Windows when you reboot?

Then you can use a virtual machine like VirtualBox or VMWare Workstation Player. VirtualBox is open source and completely gratis. VMWare Workstation Player is gratis for personal use, and has better graphics performance.

You need as much RAM as you normally need to run Windows, plus as much RAM you normally need to run Linux, plus as much RAM as your apps normally require.

You can also use Virtual PC from Microsoft, but I've never tried it myself.

---

### Post by dezintop on 2020-10-20
> **metacell said:**
> You mean you want to run Linux and Windows apps at the same time, not just switch between Linux and Windows when you reboot?

Then you can use a virtual machine like VirtualBox or VMWare Workstation Player. VirtualBox is open source and completely gratis. VMWare Workstation Player is gratis for personal use, and has better graphics performance.

You need as much RAM as you normally need to run Windows, plus as much RAM you normally need to run Linux, plus as much RAM as your apps normally require.

You can also use Virtual PC from Microsoft, but I've never tried it myself.

switching between them at reboot. you are right. 

VMware may be not a perfect solution.

---

### Post by metacell on 2020-10-20
> **dezintop said:**
> switching between them at reboot. you are right. 

If you want to switch between them at boot, it's much simpler.

Go into Windows disk manager, and shrink your Windows partition to make space for Ubuntu.

Then run the Ubuntu installation disk/USB stick, and install it in the empty space.

Or, you could install a new HDD/SSD in your computer, and install Ubuntu on that.

---

### Post by dezintop on 2020-10-20
> **metacell said:**
> If you want to switch between them at boot, it's much simpler.

Go into Windows disk manager, and shrink your Windows partition to make space for Ubuntu.

Then run the Ubuntu installation disk/USB stick, and install it in the empty space.

Or, you could install a new HDD/SSD in your computer, and install Ubuntu on that.


Thanks for your guidelines. more detail will be more appreciated.

---

### Post by ActionParsnip on 2020-10-20
You can run virtualbox and run a virtual machine of Ubuntu inside of Windows. You'll need enough CPU and RAM to run both.

---

### Post by C.S.Cameron on 2020-10-20
You can run Ubuntu in Microsoft's very own virtualization product, Hyper-V:
[https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/about/](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/about/)

VirtualBox will not run on a computer that has Hyper-V enabled.
Hyper-V is available on 64-bit versions of Windows 10 Pro, Enterprise, and Education. It is not available on the Home edition.

---

### Post by dezintop on 2020-10-20
> **C.S.Cameron said:**
> You can run Ubuntu in Microsoft's very own virtualization product, Hyper-V:
[https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/about/](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/about/)

VirtualBox will not run on a computer that has Hyper-V enabled.
Hyper-V is available on 64-bit versions of Windows 10 Pro, Enterprise, and Education. It is not available on the Home edition.

Thanks for this suggestion.

---

### Post by sdsurfer on 2020-10-20
You can also buy a KVM, if you have two computers. Seems like a bit of a waste of a KVM port to use one for Windows, but if that's your thing, it works. KVM's are getting cheaper and more reliable. I use one to switch between two Linux machines.

---

### Post by TheFu on 2020-10-20
Only 1 other OS?  That seems like a little under-use for most current hardware.
```
$ virsh list
 Id    Name                           State
----------------------------------------------------
 1     regulus                        running
 2     blog44-1604                    running
 3     zcs45-16.04                    running
 4     vpn09-1604                     running
 5     xen41-1604                     running
 6     spam3                          running
 9     WinUlt                         running
```
Each of those is a separate virtual machine running on the same hardware.
```
thefu@regulus:~$ uptime
 10:13:48 up 19 days, 13:29,
```
One of those VMs has been running for 19 days. It is my "desktop" system and available to me from anywhere in the world with internet access. From it, I can access that Windows VM, securely.
```
virt-top 10:15:32 - x86_64 12/12CPU 1546MHz 32160MB
11 domains, 7 active, 7 running, 0 sleeping, 0 paused, 4 inactive D:0 O:0 X:0
CPU: 1.1%  Mem: 11952 MB (11952 MB by guests)

   ID S RDRQ WRRQ RXBY TXBY %CPU %MEM    TIME   NAME                                    
    1 R             92    0  0.5  6.0  35:41:12 regulus
    9 R    0    0  522  104  0.3  4.0  90:56.46 WinUlt
    3 R             92    0  0.1 12.0  84:39:17 zcs45-16.04
    6 R             92    0  0.1  3.0 217:54.10 spam3
    4 R             92    0  0.1  3.0 134:58.28 vpn09-1604
    5 R             92    0  0.1  3.0 576:01.95 xen41-1604
    2 R             92    0  0.0  3.0 202:38.66 blog44-1604
```
As you can see from the virt-top output, all these VMs have been running for some time. My systems are very stable. Well, except Windows.  I run that usually once a week to do some financial stuff. Forgot to shut it down when I was done yesterday. Windows has been running a little over 1 day, but has used more CPU than an Ubuntu-Mate desktop that has been up 19 days.  The "Time" column above, is "CPU Time", not wall clock time.

So, basically, don't use Windows as the hostOS. It wastes too much CPU, too much RAM, and doesn't provide nearly the performance or stablity  as almost any Linux hostOS.  IMHO.

I use a KVM switch too. It is a 4-port thing to connect to 4 different physical computers, but share the same keyboard, mouse and video/monitor. 4 in and 1 out.  It keeps me from moving my hands and swapping keyboards around.  The version I have supports keyboard shortcuts to change the input computer that takes over the hardware I'm using.

To add some confusion, my hypervisor of choices is called "KVM" - Kernel Virtual Machine.  This is a hypervisor built and maintained by the Linux kernel guys.  It is rock solid, stable, and faster than all other hypervisors.  

A KVM switch has ZERO, nothing, nada, to to with KVM the hypervisor.

Amazon, IBM, Oracle, and pretty much every VPS hosting company in the world uses KVM, with 2 exceptions.  Microsoft Azure doesn't - they have a NIH problem and VMware, also with the NIH problem.  Clearly, those companies have their own commercial, expensive, hypervisors they want everyone to pay to use instead.  I've only played with MSFT's hypervisor about 10 yrs ago. At the time, it was a toy and not too stable.  

I've used 6 of VMware's virtualization products and deployed them at a few client sites.  At the time, also about 10 yrs ago, they were the safe, solid, fast enough, answer. I ran VMware ESXi at home, but it only worked on 1 computer due to hardware incompatibility issues.  I first used VMware Workstation in 1998. By far, it was the best choice back then for x86 VMs.

In 2008, I used Xen for production needs at work.  It was a little funky and not as stable as ESXi. 

In 2011, I replaced Xen and ESXi with KVM as the hypervisor after about 6 months of testing.  I've never regretted that move.  KVM isn't just for servers anymore.  Thanks to the SPICE remote desktop protocol, accessing any desktop running inside a VM is crazy fast both if on the same system and over the network.  My desktop, regulus, is accessed for almost everything using spice. The windows and programs run so fast that I forget I'm not using the actual physical machine where typing or using the mouse.  Plus, the convenience of having a virtual machine rather than a physical install is something people new to virtualization need a few years to understand.  I can move regulus to a different VM host here easily with just a few seconds of downtime.  Look up "live migration" if that interests you.

Sorry to go on and on.  Virtualization is something I'm fairly excited about because it solves so many problems that enterprise clients have and about 20 problems that home users have.  VMs are pretty amazing.

---

### Post by tea for one on 2020-10-20
Methinks, a bit of acronym aggravation has materialised:-

KVM = KVM Switch (Keyboard, Video Monitor, Mouse)

KVM = Kernel-based Virtual Machine

I bet the OP is confused ;)

---

### Post by dezintop on 2020-10-20
ok thanks for your comments.

---

### Post by lammert-nijhof on 2020-10-22
If you are new to virtualization, use Virtualbox. It is by far the most user friendly and reliable solution. If you run Windows as Host OS, you need approx 2 GB of RAM for each Linux system you want to run as Virtual Machine. If needed you can easily increase the size later. I use Virtualbox since more than 10 years.  To play my music with WMP, I still run occasionally a Windows XP VM. I've created the VM during my Christmas holidays in 2010. That VM has been created on a 32-bits Pentium 4 HT without HW virtualization support and its still runs flawlessly and much faster on my 64-bit Ryzen with virtualization support.

---

### Post by SeijiSensei on 2020-10-22
If you have only 4 GB and are running [VirtualBox]("http://www.virtualbox.org/") on Windows, I've gotten away with 1.5 GB for the Ubuntu guest leaving 2.5 GB for Windows on the host.  I recently increased my memory to 16 GB on my desktop machine to improve overall performance on both the host system and any virtual machines.

Microsoft has released something called Windows Subsystem for Linux (WSL) that lets you run Linux on top of Windows. However you're limited to the distributions available for WSL in the Microsoft Store. With VirtualBox you have no such limitations. You can spin up multiple virtual machines and install various flavors of Linux on them. Good for side-by-side testing.

---

### Post by C.S.Cameron on 2020-10-23
+1 for VBox

---

