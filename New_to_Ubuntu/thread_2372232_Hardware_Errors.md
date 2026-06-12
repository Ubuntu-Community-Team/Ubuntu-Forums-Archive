---
title: "Hardware Errors"
date: 2017-09-22
forum: New to Ubuntu
---

### Post by truefalse on 2017-09-22
Hello Guys,

During the installation and after the installation, kernel is throwing hardware errors logs. My spec is:

i7 6700k stock clock currently
16gb 2x8GB DDR4 3000Mhz
MSI RX480 8GB Gaming X
Corsair HX750 - over 8 years old
Noctua NH-US14

Hardware Error Logs
```
[    0.083645] WARNING: CPU: 0 PID: 23 at /build/linux-hwe-3u3SZg/linux-hwe-4.10.0/kernel/workqueue.c:2042 process_one_work+0x44a/0x4a0
[    0.083645] Modules linked in:
[    0.083647] CPU: 0 PID: 23 Comm: kworker/2:0 Not tainted 4.10.0-35-generic #39~16.04.1-Ubuntu
[    0.083647] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./Z170 Extreme4, BIOS P7.20 11/22/2016
[    0.083650] Call Trace:
[    0.083653]  dump_stack+0x63/0x90
[    0.083654]  __warn+0xcb/0xf0
[    0.083655]  warn_slowpath_null+0x1d/0x20
[    0.083656]  process_one_work+0x44a/0x4a0
[    0.083656]  worker_thread+0x4b/0x500
[    0.083658]  kthread+0x109/0x140
[    0.083658]  ? process_one_work+0x4a0/0x4a0
[    0.083659]  ? kthread_create_on_node+0x60/0x60
[    0.083661]  ret_from_fork+0x2c/0x40
[    0.083662] ---[ end trace 3790ed6593d21f30 ]---
[    0.083663] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 3: cc40010000100151
[    0.083663] mce: [Hardware Error]: TSC a97bd8ae31a ADDR 35eab5440 MISC 346485 
[    0.083665] mce: [Hardware Error]: PROCESSOR 0:506e3 TIME 1506103801 SOCKET 0 APIC 4 microcode ba
[    0.083665] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 3: cc40034000100151
[    0.083666] mce: [Hardware Error]: TSC a97bd8afb59 ADDR 35eab4ae0 MISC 106485 
[    0.083667] mce: [Hardware Error]: PROCESSOR 0:506e3 TIME 1506103801 SOCKET 0 APIC 4 microcode ba
[    0.083667] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 3: cc4000c000100151
[    0.083668] mce: [Hardware Error]: TSC a97bd8b0fd5 ADDR 35eabb540 MISC 536485 
[    0.083669] mce: [Hardware Error]: PROCESSOR 0:506e3 TIME 1506103801 SOCKET 0 APIC 4 microcode ba
[    0.083669] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 3: 8c40004000100151
[    0.083670] mce: [Hardware Error]: TSC a97bd8b23fd ADDR 35ef94440 MISC 516485 
[    0.083671] mce: [Hardware Error]: PROCESSOR 0:506e3 TIME 1506103801 SOCKET 0 APIC 4 microcode ba
[    0.083708]  #3 #4 #5 #6


```

I have my SSD, HDD - they are fine.
My GPU is fine
RAM has been checked using MemTest in UEFI
I am not sure about the PSU but PC is stable all the time. I wonder if my Motherboard is acting or CPU :-(

---

### Post by mörgæs on 2017-09-23
How does it work if you install 17.04?

---

### Post by truefalse on 2017-09-23
Hello There,

I have test another PSU today with no luck.
Here are the logs from 17.04:
```
[    0.081466] smpboot: CPU0: Intel(R) Core(TM) i7-6700K CPU @ 4.00GHz (family: 0x6, model: 0x5e, stepping: 0x3)
[    0.081491] Performance Events: PEBS fmt3+, Skylake events, 32-deep LBR, full-width counters, Intel PMU driver.
[    0.081508] ... version:                4
[    0.081509] ... bit width:              48
[    0.081509] ... generic registers:      4
[    0.081509] ... value mask:             0000ffffffffffff
[    0.081509] ... max period:             00007fffffffffff
[    0.081510] ... fixed-purpose events:   3
[    0.081510] ... event mask:             000000070000000f
[    0.082006] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.082013] smp: Bringing up secondary CPUs ...
[    0.082048] x86: Booting SMP configuration:
[    0.082048] .... node  #0, CPUs:      #1 #2
[    0.082818] mce: [Hardware Error]: Machine check events logged
[    0.082822] mce: [Hardware Error]: Machine check events logged
[    0.082837] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 3: cc5eb2c000100135
[    0.082839] mce: [Hardware Error]: TSC 0 ADDR 4658130c0 MISC 102285 
[    0.082841] mce: [Hardware Error]: PROCESSOR 0:506e3 TIME 1506182841 SOCKET 0 APIC 4 microcode 74
[    0.082843] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 3: cc4007c000100151
[    0.082844] CMCI storm detected: switching to poll mode
[    0.082844] mce: [Hardware Error]: TSC 38b79d15f68 ADDR 2176488c0 MISC 316485 
[    0.082846] mce: [Hardware Error]: PROCESSOR 0:506e3 TIME 1506182841 SOCKET 0 APIC 4 microcode 74
[    0.082847] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 3: cc400b8000100151
[    0.082848] mce: [Hardware Error]: TSC 38b79d1bfee ADDR 2176488c0 MISC 306485 
[    0.082850] mce: [Hardware Error]: PROCESSOR 0:506e3 TIME 1506182841 SOCKET 0 APIC 4 microcode 74
[    0.082852] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 3: cc4002c000100151
[    0.082854] mce: [Hardware Error]: TSC 38b79d1d7ba ADDR 2176b4740 MISC 306485 
[    0.082857] mce: [Hardware Error]: PROCESSOR 0:506e3 TIME 1506182841 SOCKET 0 APIC 4 microcode 74
[    0.082859] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 3: cc40008000100151
[    0.082861] mce: [Hardware Error]: TSC 38b79d1f657 ADDR 217646440 MISC 306485 
[    0.082864] mce: [Hardware Error]: PROCESSOR 0:506e3 TIME 1506182841 SOCKET 0 APIC 4 microcode 74
[    0.082866] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 3: 8c40004000100151
[    0.082868] mce: [Hardware Error]: TSC 38b79d21110 ADDR 217655d40 MISC 786485 
[    0.082871] mce: [Hardware Error]: PROCESSOR 0:506e3 TIME 1506182841 SOCKET 0 APIC 4 microcode 74
[    0.082873] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 3: 8c40004000100135
[    0.082875] mce: [Hardware Error]: TSC 38b79d22600 ADDR 218434968 MISC 312285 
[    0.082877] mce: [Hardware Error]: PROCESSOR 0:506e3 TIME 1506182841 SOCKET 0 APIC 4 microcode 74
[    0.082880] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 3: cc40034000100151
[    0.082882] mce: [Hardware Error]: TSC 38b79d25232 ADDR 217646ec0 MISC 506485 
[    0.082884] mce: [Hardware Error]: PROCESSOR 0:506e3 TIME 1506182841 SOCKET 0 APIC 4 microcode 74
[    0.082887] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 3: cc40008000100151
[    0.082888] mce: [Hardware Error]: TSC 38b79d260f7 ADDR 217ed4f40 MISC 716485 
[    0.082891] mce: [Hardware Error]: PROCESSOR 0:506e3 TIME 1506182841 SOCKET 0 APIC 4 microcode 74
[    0.082893] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 3: cc40014000100151
[    0.082895] mce: [Hardware Error]: TSC 38b79d27410 ADDR 217632a40 MISC 706485 
[    0.082898] mce: [Hardware Error]: PROCESSOR 0:506e3 TIME 1506182841 SOCKET 0 APIC 4 microcode 74
[    0.082900] mce: [Hardware Error]: CPU 2: Machine Check: 0 Bank 3: cc40008000100135
[    0.082902] mce: [Hardware Error]: TSC 38b79d2880b ADDR 21858ecc0 MISC 102285 
[    0.082905] mce: [Hardware Error]: PROCESSOR 0:506e3 TIME 1506182841 SOCKET 0 APIC 4 microcode 74
[    0.082911] ------------[ cut here ]------------
[    0.082914] WARNING: CPU: 0 PID: 23 at /build/linux-Fk60NP/linux-4.10.0/kernel/workqueue.c:2042 process_one_work+0x436/0x4b0
[    0.082914] Modules linked in:
[    0.082916] CPU: 0 PID: 23 Comm: kworker/2:0 Not tainted 4.10.0-19-generic #21-Ubuntu
[    0.082916] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./Z170 Extreme4, BIOS P7.20 11/22/2016
[    0.082920] Call Trace:
[    0.082922]  dump_stack+0x63/0x81
[    0.082923]  __warn+0xcb/0xf0
[    0.082924]  warn_slowpath_null+0x1d/0x20
[    0.082925]  process_one_work+0x436/0x4b0
[    0.082925]  worker_thread+0x4b/0x500
[    0.082927]  kthread+0x101/0x140
[    0.082927]  ? process_one_work+0x4b0/0x4b0
[    0.082928]  ? kthread_create_on_node+0x60/0x60
[    0.082930]  ret_from_fork+0x2c/0x40
[    0.082931] ---[ end trace 9f9d4542577960ee ]---

```

Edit@
I have run Intel Processor Diagnostic tool via UEFI all went fine apart of one thing regarding Ethernet Controller. When I was trying to install Fedora - I wanted to run a live CD and it was getting stuck when trying to get DNS loaded etc. At the end of the Intel test I have seen this:
[IMG]https://s26.postimg.org/y9z1ndb09/IMG_20170923_173809.jpg[/IMG]

Edit@
I have found out the problem. Just now I have downloaded Ubuntu 16.04.1 which has a kernel version 4.4.0-31 and guess what. System has booted without any problems. "dmesg" does not show any hardware errors. My question now is: is it a bug in the kernel or what is it?

---

### Post by mörgæs on 2017-09-24
We need someone other than me to tell if it's a bug or somehow an intended function.

*If* it's a bug it would be interesting to see how 17.10 (beta) behaves.

---

