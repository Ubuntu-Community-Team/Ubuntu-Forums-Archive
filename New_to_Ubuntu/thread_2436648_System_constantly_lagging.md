---
title: "System constantly lagging"
date: 2020-02-10
forum: New to Ubuntu
---

### Post by ntertainer on 2020-02-10
Hello,

I've been using Ubuntu for a couple of weeks and everytime i move the mouse, change window (or basically anything) for the first few seconds of doing it, the system stutters/lags.
Before Ubuntu, I used Linux Mint for a few months. I changed to Ubuntu because the same issue started there. With Ubuntu it has been from the start, so I'm guessing it's not just with the OS.

On Windows 10, which is installed on a different (but same exact model), I don't have this issue.

As for the hardware I have a 
GPU: 5700xt
CPU: 3700x
RAM: Corsair 32gb DDR4 3200MHz
SSD: Corsair Force MP510 480gb m.2

Do you have any ideas on what might be the problem?

Thank you!

---

### Post by TheFu on 2020-02-10
Sorry, I don't know what a 3700x CPU is.  Please run  **inxi -Fz** and post that command + output inside code tags, so everything lines up here. CPUs usually have a brand with them.  Is it ARM, AMD, Intel, Citix, Via?  Same for the GPU. Is there a brand?

We cannot read your mind.

---

### Post by CatKiller on 2020-02-10
> **ntertainer said:**
> GPU: 5700xt

This needs new stuff. The kernel that's in 19.10 has been released for 18.04's hardware enablement stack, but you'd still need a newer Mesa. There are PPAs that will add newer Mesa to 18.04: which one you go for depends on how much newness you're comfortable with.

---

### Post by ntertainer on 2020-02-10
> **TheFu said:**
> Sorry, I don't know what a 3700x CPU is.  Please run  **inxi -Fz** and post that command + output inside code tags, so everything lines up here. CPUs usually have a brand with them.  Is it ARM, AMD, Intel, Citix, Via?  Same for the GPU. Is there a brand?

We cannot read your mind.

Sorry, I didn't think that far. CPU is as it states in below output AMD Ryzen 3700X and GPU is PowerColor AMD Radeon RX 5700 XT Red Dragon 8gb.

```
$ inxi -Fz
System:    Host: Gustaf Kernel: 5.3.0-28-generic x86_64 bits: 64
                Desktop: Gnome 3.28.4 Distro: Ubuntu 18.04.4 LTS
Machine:   Device: desktop System: Gigabyte product: X570 I AORUS PRO WIFI v: -CF serial: N/A
                Mobo: Gigabyte model: X570 I AORUS PRO WIFI v: x.x serial: N/A
                UEFI: American Megatrends v: F10 date: 11/15/2019
CPU:         8 core AMD Ryzen 7 3700X (-MT-MCP-) cache: 4096 KB
                clock speeds: max: 3600 MHz 1: 2195 MHz 2: 2201 MHz 3: 2196 MHz
                4: 2195 MHz 5: 2801 MHz 6: 1863 MHz 7: 1863 MHz 8: 2590 MHz
                9: 2193 MHz 10: 2193 MHz 11: 2194 MHz 12: 2195 MHz 13: 2794 MHz
                14: 1861 MHz 15: 1862 MHz 16: 2065 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Device 731f
                Display Server: x11 (X.Org 1.20.5 )
                drivers: ati,vesa (unloaded: modesetting,fbdev,radeon)
                Resolution: 3440x1440@99.98hz
                OpenGL: renderer: AMD Radeon RX 5700 XT version: 4.6.13581
Audio:      Card-1 Advanced Micro Devices [AMD] Device 1487
                driver: snd_hda_intel
                Card-2 Advanced Micro Devices [AMD/ATI] Device ab38
                driver: snd_hda_intel
                Card-3 Bose driver: USB Audio
                Card-4 Turtle Beach driver: USB Audio
                Sound: Advanced Linux Sound Architecture v: k5.3.0-28-generic
Network:   Card-1: Intel I211 Gigabit Network Connection driver: igb
                IF: enp5s0 state: up speed: 100 Mbps duplex: full mac: <filter>
                Card-2: Intel Device 2723 driver: iwlwifi
                IF: wlp6s0 state: down mac: <filter>
Drives:      HDD Total Size: 2960.6GB (35.4% used)
                ID-1: /dev/nvme0n1 model: Force_MP510 size: 960.2GB
                ID-2: /dev/nvme1n1 model: Force_MP510 size: 480.1GB
                ID-3: /dev/sda model: ST2000DM008 size: 2000.4GB
Partition:  ID-1: / size: 439G used: 11G (3%) fs: ext4 dev: /dev/nvme1n1p2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: No active sensors found. Have you configured your sensors yet? mobo: N/A
Info:        Processes: 389 Uptime: 4 min Memory: 1774.8/32126.4MB
               Client: Shell (bash) inxi: 2.3.56
```

> **CatKiller said:**
> This needs new stuff. The kernel that's in 19.10 has been released for 18.04's hardware enablement stack, but you'd still need a newer Mesa. There are PPAs that will add newer Mesa to 18.04: which one you go for depends on how much newness you're comfortable with.

How do I go about to do this? As I'm quite new to Linux overall, I guess I'm as comfortable to any newness as I can get. Thanks!

---

### Post by CatKiller on 2020-02-10
> **ntertainer said:**
> How do I go about to do this? As I'm quite new to Linux overall, I guess I'm as comfortable to any newness as I can get. Thanks!

So you've probably noticed that all your software packages when you install or update them get downloaded from *somewhere on the Internet* that the package manager knows about. PPAs are just another *somewhere on the Internet* that you can tell your package manager about, so it can get new packages or updates from there as well.

I don't use AMD graphics myself, but I understand that [this PPA](https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa) is popular with those that do. It tracks the most recent point release, rather than the absolute newest dev version that people could test with (there are other PPAs that would give you those dev versions).

You just run the command listed on that page to add the repository, and then update or install your software in the normal way. 

There's another package called *ppa-purge* (I don't think it's installed by default) that will automatically remove a PPA repository and downgrade any packages you've installed from it to the versions from the normal repositories. That's useful to have should you run into any problems, or if the software from a PPA doesn't actually do what you were hoping it would.

---

### Post by TheFu on 2020-02-10
With Linux, because the manufacturers tend not to work with anyone not running Windows, it is best to stay 6-12 months behind on any hardware.  You are likely in the "bleeding edge."  New isn't always better. Sometimes it just means "barely works" until the hardware support gets into a new release.  There are ways to use the newest code, but that is seldom point-n-click, so some technical expertise with Unix/Linux drivers is needed.

Anyway, I have a Ryzen 2600 (not bleeding edge) and an nVidia 1030 GPU (not bleeding edge).  There were newer CPUs and GPUs when I built the system, but staying behind 1 generation was a hard learned lesson.

BTW, the Intel NIC is a good one, but it is only connecting at 100 base-tx?  Any idea why not GigE?  It should be providing 920Mbps throughput, easily.

Unless there is a kernel issue with that CPU, I'd look at the GPU drivers and swap setup for any stuttering issues.  For a Linux desktop, 4.1G is the correct size for swap regardless of RAM, IMHO.  There have been issues with systems not having enough swap showing really poor performance - something in the kernel wants _some_ swap.  On a system like yours, swap is there to provide feedback when you've over extended the available RAM, so the user will "feel" the system get slower and take action to close some bloated applications.  Running out of RAM (including swap) will crash a computer.

---

### Post by ntertainer on 2020-02-10
Thank you CatKiller. I added the PPA and made sure everything is updated/upgraded, but the issue still remains.

---

### Post by ntertainer on 2020-02-10
Might have to wait a while before everything starts running smoothly on my machine then, I guess.

When it comes to the NIC, unless the 920Mbps is shown otherwise, I'm guessing it's my network speed that limits it? Or am I completely lost in the woods? 
As I'm guessing you've noticed, I'm not used to the more technical stuff.

I'll look into the swap setup to see if it would help. 

Thanks!

---

### Post by CatKiller on 2020-02-10
> **ntertainer said:**
> Thank you CatKiller. I added the PPA and made sure everything is updated/upgraded, but the issue still remains.

That's a shame. You can try standard troubleshooting stuff, then; running something like top to see if some process is doing something weird at the point where you experience symptoms, checking logs, that sort of thing.

---

### Post by CatKiller on 2020-02-11
I also notice that there's a UEFI update for your motherboard that claims to > Improve PCIe device compatibility
Improve memory compatibility

Might help; shouldn't hurt.

---

### Post by CatKiller on 2020-02-11
> **ntertainer said:**
> 
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Device 731f
                Display Server: x11 (X.Org 1.20.5 )
                drivers: **ati,vesa** (unloaded: modesetting,fbdev,radeon)


This is odd, too. As far as I know this should say **amdgpu** for a new card like yours. That might explain your symptoms: vesa is doing things in software, and ati is really old.

```
dmesg | grep 'amdgpu'
``` might show something; maybe it's looking for firmware that you don't have?

Also make sure that you've got the amdgpu packages installed.

---

### Post by ntertainer on 2020-02-11
Upgraded BIOS and set swap to 4GB, but still no change in performance. Still lags alot everytime I open a process (including tabs in Firefox, new email in thunderbird or even open the terminal).
I'll google around some more, but I really can't figure out what might be off. If you have other ideas I'd be glad to try them out!

Thank you guys!

---

### Post by ntertainer on 2020-02-11
I think I've found something. So I opened the system monitor, checked the different processes and tried to tie the lag to something. What I found was that everytime the disk reads or writes something the system starts lagging. Can't find any solution online for this other than a quick read about Gnome being the issue, but that seems a bit farfetched..

---

### Post by TheFu on 2020-02-11
**top**, **free**, and checking the system logs are the first steps to tracking down issues.

With disk issues, determining performance would be my first step, then figuring out if that is the normal, expected, speed the 2nd.  If the storage subsystem isn't close to the performance specs, start tracing where the slowdown is.  Most of the time, either the selected file system or how the storage is mounted are the problems.  In general, if a GUI was used to mount the storage, then performance will suffer.

---

### Post by ntertainer on 2020-02-15
I changed from kernel 5.3 to 4.15 and it fixed the issue! I have no idea what the difference is but the problem is finally gone!

---

