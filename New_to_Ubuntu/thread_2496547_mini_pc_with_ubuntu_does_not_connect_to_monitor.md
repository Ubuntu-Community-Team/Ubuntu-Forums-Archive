---
title: "mini pc with ubuntu does not connect to monitor"
date: 2024-04-02
forum: New to Ubuntu
---

### Post by miriam-101 on 2024-04-02
Hello,


I am new to Linux. I bought a mini PC with Ubuntu on it. So, when the system was updating, the pop-up message was constantly popping up on my monitor whenever I wanted to open an app or simply was trying to reboot the PC. The message was about authentication. The system did not give me any chance to authenticate at this stage. Unexpectedly, the power went off from my monitor and never lighted again. I restarted the pc and now it does not connect to any monitor. The pc is turning on, but it does not connect to any monitor. I suppose the issue occurred with the system during the _updating process and power issues_. Before that issue, the system was working great. Please give me some ideas to how to restore my system.

---

### Post by TheFu on 2024-04-03
Do a fresh install.

You explained the problem, but didn't say which release or which DE or what type of PC or what type of monitor or .... lots of important details are missing.  Also don't say "latest", since the idea of "latest version" can mean many different things to different people.

BTW, when it says not to power off or shutdown during some critical phase, it is being serious.

---

### Post by Impavidus on 2024-04-03
Most issues can be solved, but with a pre-installed Ubuntu, you don't know how it was configured. That makes it harder to see what's going on.

Can you create and boot a live usb with Ubuntu 22.04 or 23.10?

---

### Post by miriam-101 on 2024-04-03
Hello, TheFu

Thanks for your quick answer.  The ubuntu is a new OS for me. I just start to learn about terminal and command line. I see that I need to learn a lot!

---

### Post by miriam-101 on 2024-04-03
Hello, Impavidus
 
I got Wo-We mini pc, and I saw on Youtube that Wo-We mini pc can have either ubuntu or windows preinstalled. My pc has ubuntu OS preinstalled. Yesterday, I was watching a lot of Youtube videos, and realized that for newbies - ubuntu or linux mint is way to go, since they have an intuitive interface for people who wants to change from Windows to Ubuntu. 

I have never ever created any bootable usb. The first time is always scary, but after that everything will be easier, right?  Thanks for your suggestion.

---

### Post by TheFu on 2024-04-03
Download the version of Linux you want to install.  There are 50+ different choices - probably 5 are directly from Canonical, but 15 are based on Ubuntu, so they work very similarly.  There's actually a pre-built ISO that can be placed onto an empty USB-flash drive that will let you try out 25+ different linux versions (called "distros").

I've never heard of a Wo-We mini pc.  [https://www.wo-we.com/collections/mini-pc](https://www.wo-we.com/collections/mini-pc) shows they are all x86-64 based, which means a fairly normal, but inexpensive, compatible computer.  I do worry that some of the components will be poorly supported. If you can be more specific, we may be able to look up the specific chips used for the GPU, NIC, and other important capabilities.  I find the $80 AMD A9 (1300 passmarks) interesting. The Intel N40xx version (1500 passmarks) for the same price is scary to me. The Intel version comes with 50% less RAM for the same price, but requires less power (5W vs 10W for the AMD).  In general, I avoid all "N" series computers for a number of reasons. Perhaps I need to rethink this idea.  I've had Nxxx computers before and found them to be slower than the specifications would imply.  Same for M5 CPUs.  The power savings seems to override performance too much.
Anyway, which model do you have?

There are lots of instructions for creating a bootable USB flash drive.  

Lastly, I'd recommend a light version of Linux Mint OVER any Ubuntu for a beginner.  Mint has only 1 package management solution, so installation of more programs doesn't become complicated like with all recent Ubuntu versions.  Additionally, the new add-on package management included/forced on users in Ubuntu forces constraints on the users, so things don't work like would be expected on any other computer.  This is good for security, but can be terrible for usability, especially when you are new.
[https://linuxmint-installation-guide.readthedocs.io/en/latest/burn.html](https://linuxmint-installation-guide.readthedocs.io/en/latest/burn.html) is the _Linux Mint_ ISO ---> Flash drive instructions for 3 different OSes.
[https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview)  is the _Ubuntu_ ISO ---> Flash drive instructions for 3 different OSes.

Those instructions are meant to be really easy for people new to follow.  The flash drive will be wiped in the process. Any data/programs on it will be gone.  4-8GB size is fine for those.

For the multi-Linux distro flash drive methods, a larger Flash drive will allow more Linux variants to be placed there and tried.  I use **Ventoy** for this myself.

sudodus  in these forums has a little tool called **mkusb** that can do something similar, but probably better, since you can actually setup persistent data storage AND the OS on the same, larger, flash drive.  I have a few friends who run MX Linux 100% off 120G USB3 Flash storage devices and they don't have any HDD/SSD inside the computer at all.  For the most part, their OS and data are completely portable to x86-64 computers, which can be great for traveling.

---

### Post by miriam-101 on 2024-04-04
Hi, TheFu

Thanks a lot for the very thorough explanation!!! I see I need to learn a lot! Also, I appreciate the resources you provided in your answer. It is very helpful to have for starting point.

I have one more question:
How can I install the Ubuntu or **Linux Mint** permanently on my SSD card? Do you have any instructions or resources to learn about clean installation? I want to have that Linux to be my main OS, and then maybe try to install other versions (to try how they operate) through iso files.

---

### Post by TheFu on 2024-04-04
> **miriam-101 said:**
> Hi, TheFu

Thanks a lot for the very thorough explanation!!! I see I need to learn a lot! Also, I appreciate the resources you provided in your answer. It is very helpful to have for starting point.
Yes, google is great.  Or DDG or whatever search engine you prefer, assuming they aren't Linux hostile like 1 we've all heard about. Avoid that one. All the others are fine.  

If you used MacOS or MS-Windows before, you'll need to unlearn lots of stuff too.  Modern Linux doesn't work like those other OSes.  Not just from the slight GUI differences, but under the covers AND how the system is setup, maintained, backed up - all those are different.  I love that Linux allows me to choose how I want it setup, but if you don't know yet, choosing the defaults is a good place to start, usually.  Note, I'm not saying the defaults are safe.  They aren't.  With Linux, you will be allowed to shoot off your toe or leg or head.  Commands assume you know what you are requesting, so they don't ask if you SHOULD do something.  They only ask if the command provided CAN be performed.  There's a huge difference is what we CAN do and what we SHOULD do.  Sometimes the "CAN" is pure genius, but there is a thin line between genius and stupidity. ;)

If you are going to run Linux, you'll need to get better at using web search tools, since the answers are usually already there, waiting for you to find.  Until you have a few more years of full-time-linux experience, search for answers only with "ubuntu" and the exact release you are running as part of the search terms.  From release to release, entire subsystems can change which completely changes how things work and are configured.  Sometimes, after 5 yrs of one subsystem being used, Canonical will decide to stop using it and switch to something else (for reasons that aren't usually clear).  Beware.

Also beware of finding and following answers from random websites.  Often, the person writing the answer doesn't really know all the options and what worked for them was luck or an accident.  Stick with websites that have "ubuntu" in the DNS part of the name and you should be ok ... assuming the release is the same as yours that the instructions were created to handle.

> **miriam-101 said:**
> I have one more question:
How can I install the Ubuntu or **Linux Mint** permanently on my SSD card? Do you have any instructions or resources to learn about clean installation? I want to have that Linux to be my main OS, and then maybe try to install other versions (to try how they operate) through iso files.

Those links should be enough.  Boot from the resulting flash drive and follow the wizard to install.  If you want to see it clearer, there are **lots of video sharing websites** that show installations of different Linux versions, but they are basically the same.
* Boot from the flash drive or ISO
* Choose your Language and Keyboard
* Choose which HDD/SSD you want to install into
* Accept the default storage layout OR do something custom - either can be used to wipe everything on the target disk/storage. If you choose the wrong storage, expect all data on it to be wiped/overwritten.
* Set a username and password - this will be the sudo user, but only 1 password is needed for ubuntu and ubuntu-based distros.  For non-Ubuntu distros, they may ask you to set a password for the 'root' account.  Ubuntu doesn't setup the root account for logins and it isn't designed to be used directly.
* Next / Next / Next / Next / Next / Next / Next / Next / Next.   
* Finished
* Reboot

If the system doesn't boot in to a GUI Login screen, then your hardware probably needs a workaround until the correct GPU driver is installed.  nVidia GPUs commonly have this issue.  Intel and AMD GPU drivers come with the kernel and almost always are automatically loaded.  I got tired of nVidia driver issues, so I build systems without nvidia now.  Saves me lots of hassles.  Saw an article that 72% of the Linux running world do NOT use nvidia now.  Their poor Linux support has real ramifications.  [https://www.phoronix.com/news/Steam-Survey-March-2024](https://www.phoronix.com/news/Steam-Survey-March-2024)

As with any skill, the more times you do it, the better you will become at doing it.  I haven't installed a fresh Linux in a few months and the last few installs were just for play, not production.  The last time I did a production install was about a year ago.  I spent 20 minutes just setting up the disk storage how I wanted it. I have specific needs for my storage layouts.  A quick, normal, install should take about 10-15 minutes, total.  That's fine for toy/play installs. I'm going to wipe them in a week or 2 anyway, so why waste time on the system that will never hold any data?

That's probably enough to get you going - probably more than you need. Good luck. And don't forget to have the appropriate amount of fun.  This stuff isn't supposed to be work.

---

### Post by yancek on 2024-04-04
The link below to the ubuntu.com site is a good starting point as it explains everything you asked about from downloading Ubuntu, creating a bootable usb and finally installing it.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

There is a lot of software available which can be used to create a bootable usb of various Linux systems.  The ubuntu.com (link I posted above) recommends using Balena Etcher to create the bootable usb as does Mint.

Youtube has a lot of good videos but for installing operating systems, definitely not the best source.  Use the official documentation as much as you can since anyone can post anything on youtube and it is not checked or verified in any way by anyone.   c

---

### Post by TheFu on 2024-04-04
BTW, an article about how a cheap mini-PC is a better solution than a Raspberry Pi v5 SBC. 
[https://arstechnica.com/gadgets/2024/04/what-i-learned-when-i-replaced-my-cheap-pi-5-pc-with-a-no-name-amazon-mini-desktop/](https://arstechnica.com/gadgets/2024/04/what-i-learned-when-i-replaced-my-cheap-pi-5-pc-with-a-no-name-amazon-mini-desktop/)

There are a number of caveats related to the mini-pcs that could be very important for some workloads.  Definitely worth reading that article.

---

### Post by him610 on 2024-04-04
I got a mimi-pc for Christmas; it came with Ubuntu 20.04. I immediately installed Xubuntu 22.04.4 on it.
It is actually a pretty good little computer - enough for what I normally do. I have even upgraded it somewhat.
 ```
hugh@MA90:~$ inxi -SMCGDmxz
System:
  Kernel: 6.5.0-25-generic x86_64 bits: 64 compiler: N/A Console: pty pts/2
    Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Mini-pc System: ATOPNUC product: ATOPNUC MA90 v: V1.0 serial: <superuser required>
  Mobo: ATOPNUC model: ATOPNUC MA90 v: Version 1.0 serial: <superuser required>
    UEFI: American Megatrends v: ASB20008 date: 07/19/2022
Memory:
  RAM: total: 15.06 GiB used: 1.28 GiB (8.5%)
  RAM Report: permissions: Unable to run dmidecode. Root privileges required.
CPU:
  Info: dual core model: AMD A9-9400 RADEON R5 5 COMPUTE CORES 2C+3G bits: 64 type: MCP
    arch: Excavator rev: 0 cache: L1: 192 KiB L2: 2 MiB
  Speed (MHz): avg: 1594 high: 1651 min/max: 1400/2400 boost: enabled cores: 1: 1651
    2: 1538 bogomips: 9581
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
Graphics:
  Device-1: AMD Stoney [Radeon R2/R3/R4/R5 Graphics] driver: amdgpu v: kernel bus-ID: 00:01.0
  Display: server: X.org v: 1.21.1.4 driver: X: loaded: amdgpu,ati
    unloaded: fbdev,modesetting,vesa gpu: amdgpu tty: 96x29
  Message: GL data unavailable in console. Try -G --display
Drives:
  Local Storage: total: 471.38 GiB used: 29.57 GiB (6.3%)
  ID-1: /dev/mmcblk0 vendor: Samsung model: GD4QT size: 119.25 GiB
  ID-2: /dev/sda vendor: Samsung model: SSD 840 Series size: 232.89 GiB
  ID-3: /dev/sdb model: SCY SNM4BBG12800D 128GB size: 119.24 GiB
 
```

---

### Post by miriam-101 on 2024-04-04
Hi, him610

Wow! It is very complicated for me now. I hope, one day, I will be able to use command line as well.

---

### Post by TheFu on 2024-04-05
> **miriam-101 said:**
> Hi, him610

Wow! It is very complicated for me now. I hope, one day, I will be able to use command line as well.


him610 included a good link to learn: The Linux Command Line at [http://linuxcommand.org/](http://linuxcommand.org/)

Using the GUI is much harder than using a shell, IMHO.  GUIs don't always tell the truth and there are lots of GUI programmers trying to fit an elegant round peg into a square hole.  Unix was designed to be used from a shell and that's how people used it the first 20+ yrs.  Most GUI programs provide only 20% of the capabilities that the command line version of the program provides.  Many GUIs actually just call the underlying program with the correct options.  That's how **grsync** works.  It is the GUI that creates an rsync command and runs it.  Often, the GUI programmer only needed a few capabilities, so it was never created to provide full access to all that the real program could accomplish.  Most of the time, that's good enough, but there are times when the full capabilities of the real program are extremely useful.

For example, **rsync** can limit the bandwidth used while transferring files.  **grsync** doesn't show that as an option.
The manpage for grsync actually discloses this:
```
GRSYNC is a simple graphical interface using GTK2 for the rsync command line program. It currently supports only a limited set of the most important rsync features, but can be used effectively for local directory synchronization.
```

As a beginner, I cannot stress enough how important learning to use manpages is.  Learn that from a video, if you learn better that way. It will save you many, many, hours.  The documentation for 99% of every command is already on your computer. Why wouldn't you use that first?

---

### Post by miriam-101 on 2024-04-05
Hi, TheFu and him610

Thanks for the link. I just checked it and it looks an awesome resource!!! Thanks!

---

