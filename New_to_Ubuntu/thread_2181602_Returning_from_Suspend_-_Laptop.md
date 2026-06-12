---
title: "Returning from Suspend - Laptop"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by EmpireITtech on 2013-10-18
Okay, so I've had this issue now on many versions of Ubuntu (12.04, 12.10, 13.04, and now 13.10) and Linux Mint. I've also had this issue on multiple laptops, so it's not just relegated to this current laptop. But every time I close the lid of my laptop (which is set to *Suspend* when doing so) or Menu > Suspend when I try to restart it the screen never returns. The laptop starts up (lights on and the screen is a muted black) but it's like the GPU never kicks in. 
Anyone know what this is about or how to fix it?

---

### Post by Toz on 2013-10-18
Hello and welcome to the forums.

It would be helpful if you could provide some more details. Specifically:

1. The make and model of your laptop.

2. The video card and driver. To get this information, open a terminal window, type in the following command, and post back the results.
```
lspci -k | grep -A3 VGA
```

3. The contents of your suspend log file:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

4. Anything PM-related in your syslog:
```
cat /var/log/syslog | grep PM:
```

Sorry for all the terminal commands, its simply the easiest way to get this information.

---

### Post by EmpireITtech on 2013-10-18
1. HP ProBook 4545s, originally came with Windows 8

2. ```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7520G]
    Subsystem: Hewlett-Packard Company Device 17ed
    Kernel driver in use: radeon
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
```

3. ```
The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>
```
I'm guessing I need to install this program....?

4. ```
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.225539] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 17 11:44:06 EmpireITubuntu kernel: [    2.087925] PM: Hibernation image not present or could not be loaded.
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.225535] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 17 11:52:02 EmpireITubuntu kernel: [    2.092483] PM: Hibernation image not present or could not be loaded.
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.225485] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 17 12:00:32 EmpireITubuntu kernel: [    2.066672] PM: Hibernation image not present or could not be loaded.
Oct 17 14:00:17 EmpireITubuntu kernel: [ 7196.486982] PM: Syncing filesystems ... done.
Oct 17 14:00:17 EmpireITubuntu kernel: [ 7196.647016] PM: Preparing system for mem sleep
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7196.797009] PM: Entering mem sleep
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7197.378396] PM: suspend of devices complete after 580.674 msecs
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7197.378645] PM: late suspend of devices complete after 0.246 msecs
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7197.458475] PM: noirq suspend of devices complete after 79.814 msecs
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7197.469470] PM: Saving platform NVS memory
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7197.578959] PM: Restoring platform NVS memory
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7198.433644] PM: noirq resume of devices complete after 177.279 msecs
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7198.433877] PM: early resume of devices complete after 0.145 msecs
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7201.174031] PM: resume of devices complete after 2739.780 msecs
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7201.174612] PM: Finishing wakeup.
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.225494] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 17 14:06:20 EmpireITubuntu kernel: [    2.243210] PM: Hibernation image not present or could not be loaded.
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.225487] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 17 16:13:50 EmpireITubuntu kernel: [    2.086743] PM: Hibernation image not present or could not be loaded.
Oct 17 16:51:02 EmpireITubuntu kernel: [ 2242.513055] PM: Syncing filesystems ... done.
Oct 17 16:51:02 EmpireITubuntu kernel: [ 2242.623424] PM: Preparing system for mem sleep
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2242.814734] PM: Entering mem sleep
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2243.320364] PM: suspend of devices complete after 504.945 msecs
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2243.320601] PM: late suspend of devices complete after 0.234 msecs
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2243.398868] PM: noirq suspend of devices complete after 78.252 msecs
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2243.410482] PM: Saving platform NVS memory
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2243.419845] PM: Restoring platform NVS memory
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2244.278016] PM: noirq resume of devices complete after 180.196 msecs
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2244.278252] PM: early resume of devices complete after 0.147 msecs
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2247.078372] PM: resume of devices complete after 2799.739 msecs
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2247.078957] PM: Finishing wakeup.
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.225536] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 17 16:53:47 EmpireITubuntu kernel: [    2.105301] PM: Hibernation image not present or could not be loaded.
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.225535] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 17 21:58:56 EmpireITubuntu kernel: [    2.281589] PM: Hibernation image not present or could not be loaded.
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.225493] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 18 08:57:26 EmpireITubuntu kernel: [    2.247252] PM: Hibernation image not present or could not be loaded.
```

---

### Post by Toz on 2013-10-18
> **empireittech said:**
> 
2. ```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7520G]
    Subsystem: Hewlett-Packard Company Device 17ed
    Kernel driver in use: radeon
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
```
Have you tried enabling the proprietary drivers for this card?

> 3. ```
The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>
```
I'm guessing I need to install this program....?
Yes please, if you don't mind. Its not large and its really helpful with posting log files up to paste.ubuntu.com so they can easily be viewed.

> 4. ```
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 17 11:44:06 EmpireITubuntu kernel: [    0.225539] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 17 11:44:06 EmpireITubuntu kernel: [    2.087925] PM: Hibernation image not present or could not be loaded.
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 17 11:52:02 EmpireITubuntu kernel: [    0.225535] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 17 11:52:02 EmpireITubuntu kernel: [    2.092483] PM: Hibernation image not present or could not be loaded.
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 17 12:00:32 EmpireITubuntu kernel: [    0.225485] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 17 12:00:32 EmpireITubuntu kernel: [    2.066672] PM: Hibernation image not present or could not be loaded.
Oct 17 14:00:17 EmpireITubuntu kernel: [ 7196.486982] PM: Syncing filesystems ... done.
Oct 17 14:00:17 EmpireITubuntu kernel: [ 7196.647016] PM: Preparing system for mem sleep
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7196.797009] PM: Entering mem sleep
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7197.378396] PM: suspend of devices complete after 580.674 msecs
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7197.378645] PM: late suspend of devices complete after 0.246 msecs
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7197.458475] PM: noirq suspend of devices complete after 79.814 msecs
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7197.469470] PM: Saving platform NVS memory
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7197.578959] PM: Restoring platform NVS memory
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7198.433644] PM: noirq resume of devices complete after 177.279 msecs
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7198.433877] PM: early resume of devices complete after 0.145 msecs
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7201.174031] PM: resume of devices complete after 2739.780 msecs
Oct 17 14:03:58 EmpireITubuntu kernel: [ 7201.174612] PM: Finishing wakeup.
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 17 14:06:20 EmpireITubuntu kernel: [    0.225494] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 17 14:06:20 EmpireITubuntu kernel: [    2.243210] PM: Hibernation image not present or could not be loaded.
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 17 16:13:50 EmpireITubuntu kernel: [    0.225487] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 17 16:13:50 EmpireITubuntu kernel: [    2.086743] PM: Hibernation image not present or could not be loaded.
Oct 17 16:51:02 EmpireITubuntu kernel: [ 2242.513055] PM: Syncing filesystems ... done.
Oct 17 16:51:02 EmpireITubuntu kernel: [ 2242.623424] PM: Preparing system for mem sleep
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2242.814734] PM: Entering mem sleep
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2243.320364] PM: suspend of devices complete after 504.945 msecs
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2243.320601] PM: late suspend of devices complete after 0.234 msecs
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2243.398868] PM: noirq suspend of devices complete after 78.252 msecs
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2243.410482] PM: Saving platform NVS memory
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2243.419845] PM: Restoring platform NVS memory
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2244.278016] PM: noirq resume of devices complete after 180.196 msecs
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2244.278252] PM: early resume of devices complete after 0.147 msecs
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2247.078372] PM: resume of devices complete after 2799.739 msecs
Oct 17 16:51:22 EmpireITubuntu kernel: [ 2247.078957] PM: Finishing wakeup.
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 17 16:53:47 EmpireITubuntu kernel: [    0.225536] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 17 16:53:47 EmpireITubuntu kernel: [    2.105301] PM: Hibernation image not present or could not be loaded.
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 17 21:58:56 EmpireITubuntu kernel: [    0.225535] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 17 21:58:56 EmpireITubuntu kernel: [    2.281589] PM: Hibernation image not present or could not be loaded.
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e1d3000-0x9f0cefff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f0cf000-0x9f7cefff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f7cf000-0x9f7fefff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xdfffffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Oct 18 08:57:26 EmpireITubuntu kernel: [    0.225493] PM: Registering ACPI NVS region [mem 0x9f0cf000-0x9f7cefff] (7340032 bytes)
Oct 18 08:57:26 EmpireITubuntu kernel: [    2.247252] PM: Hibernation image not present or could not be loaded.
```
Nothing out of the ordinary here. Can you try manually suspend with the following commands, one at a time, to see if the screen comes back on resume?
```
sudo pm-suspend --quirk-dpms-on
```
```
sudo pm-suspend --quirk-radeon-off
```
```
sudo pm-suspend --quirk-s3-mode
```
```
sudo pm-suspend --quirk-vbestate-restore
```

---

### Post by EmpireITtech on 2013-10-21
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo pm-suspend --quirk-dpms-on[/FONT][/COLOR]
```
Went to sleep, never came back up

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo pm-suspend --quirk-radeon-off[/FONT][/COLOR]
```
Went to sleep, never came back up and also the screen was just pitch black (not even a muted black like normal)

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo pm-suspend --quirk-s3-mode[/FONT][/COLOR]
```
Went to sleep, same as before

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo pm-suspend --quirk-vbestate-restore[/FONT][/COLOR]
```
Went to sleep, same as always

I'm going to try the graphic card driver thing and get back again, thanks!

---

### Post by EmpireITtech on 2013-10-21
Using a proprietary driver for this card has made my screen not even start up on reboot. I had to use an external monitor to reset it...and the external monitors (I tried 3 separate ones) didn't work, I must reinstall Ubuntu first. 
Maybe it's just a lost cause...

---

### Post by Toz on 2013-10-21
Lets dig a little deeper.

Can I see your dmesg and Xorg log files? If you've installed pastebinit, then:
```
pastebinit /var/log/dmesg
pastebinit /var/log/Xorg.0.log
```
...and post back the links that are generated.

If you haven't/don't want to install pastebinit, then copy/paste the contents of those two files and post back in between **[noparse]```
 
```[/noparse]** tags.

Can you also create the following file (as root):
```
sudo -i gedit /etc/pm/sleep.d/0000backlight
```
...with the following content:
```

#!/bin/bash
case $1 in
   sleep)
      for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
      ;;
   resume)
      for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
      ;;
esac
```
...save the file and then attempt a sleep/resume. Once you've recovered can you post back /var/log/pm-suspend.log (using pastebinit or copy/paste)?

---

