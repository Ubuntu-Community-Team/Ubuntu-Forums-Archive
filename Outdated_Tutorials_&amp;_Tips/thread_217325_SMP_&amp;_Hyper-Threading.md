---
title: "SMP &amp; Hyper-Threading"
date: 2006-07-17
forum: Outdated Tutorials &amp; Tips
---

### Post by autocrosser on 2006-07-17
A question I see asked a fair amount is "I have the 686-SMP kernel installed--yet I look at dmesg & it says that "CPU Hyper-threading is disabled"---WHAT'S UP??

Intel states that Hyper-Threading will improve performance in "aware applications"--I used SETI@Home-Enhanced as my bench-mark--it runs all the time-24hrs per & is both cpu-intensive & a "new" enough app to be H/T-aware.

In my last 30 work-units I've seem a average 2/4 hrs DROP in unit complete times--quite a major improvement for such a simple change.

HOW?

#1--Check your processor specs to see if you can enable H/T.
#2--Check you Bios to see if you can enable with your motherboard.
#3--Make sure you enable it in your /boot/grub/menu.lst
First in a terminal  "dmesg"  (without the quotes)
You will most likely see--"CPU--Hyper-Threading disabled"

Then:

Code:sudo gedit /boot/grub/menu.lst
find the "kernel  /boot/vmlinuz-"your #" root-/dev/drive# ro quiet splash"  & add: ht=on  at the end.

Save the file---Reboot

That's all---recheck your dmesg after the reboot & if you have done your homework right you will see something like:

[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 2795.714 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.524000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.524000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.952000] Memory: 3104964k/3145408k available (2110k kernel code, 39124k reserved, 595k data, 332k init, 2227904k highmem)
[17179570.952000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.032000] Calibrating delay using timer specific routine.. 5599.74 BogoMIPS (lpj=11199490)
[17179571.032000] Security Framework v1.0.0 initialized
[17179571.032000] SELinux:  Disabled at boot.
[17179571.032000] Mount-cache hash table entries: 512
[17179571.032000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000651d 00000000 00000001
[17179571.032000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000651d 00000000 00000001
[17179571.032000] monitor/mwait feature present.
[17179571.032000] using mwait in idle threads.
[17179571.032000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179571.032000] CPU: L2 cache: 1024K
[17179571.032000] CPU: Physical Processor ID: 0
[17179571.032000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000080 0000651d 00000000 00000001
[17179571.032000] mtrr: v2.0 (20020519)
[17179571.032000] Enabling fast FPU save and restore... done.
[17179571.032000] Enabling unmasked SIMD FPU exception support... done.
[17179571.032000] Checking 'hlt' instruction... OK.
[17179571.048000] SMP alternatives: switching to UP code
[17179571.048000] checking if image is initramfs... it is
[17179572.164000] Freeing initrd memory: 6820k freed
[17179572.176000] ACPI: Looking for DSDT ... not found!
[17179572.192000] CPU0: Intel(R) Pentium(R) D  CPU 2.66GHz stepping 07
[17179572.192000] SMP alternatives: switching to SMP code <<<-----!!!!!!!!----->>>8)
[17179572.192000] Booting processor 1/1 eip 3000
[17179572.204000] Initializing CPU#1
[17179572.284000] Calibrating delay using timer specific routine.. 5590.41 BogoMIPS (lpj=11180824)<<<-----!!!!!----->>>8)8)
[17179572.284000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000651d 00000000 00000001
[17179572.284000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000651d 00000000 00000001
[17179572.284000] monitor/mwait feature present.
[17179572.284000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179572.284000] CPU: L2 cache: 1024K
[17179572.284000] CPU: Physical Processor ID: 0
[17179572.284000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000080 0000651d 00000000 00000001
[17179572.284000] CPU1: Intel(R) Pentium(R) D  CPU 2.66GHz stepping 07
[17179572.284000] Total of 2 processors activated (11190.15 BogoMIPS).<<<-----!!!8)8)8)!!!----->>>
[17179572.284000] ENABLING IO-APIC IRQs
[17179572.284000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.956000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[17179572.956000] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[17179572.956000] ...trying to set up timer as Virtual Wire IRQ... works.
[17179573.104000] checking TSC synchronization across 2 CPUs: passed.
[17179573.108000] Brought up 2 CPUs

Easy enough------

---

### Post by Janux on 2006-07-17
I believe that option is disabled because it might have a security risk. This could be troublesome on a server, but with a desktop you shouldn't have major problems (see [http://kerneltrap.org/node/5103](http://kerneltrap.org/node/5103))

---

### Post by autocrosser on 2006-07-17
That sounds about right & a further note from Intel: Hyper-Threading "might" cause instability with your system--Although I have not see this & if I do, it's a simple matter to disable it in the Bios & remove the line in the boot kernel;)
 
As per the website:
 
Colin Percival, a FreeBSD committer and security team member, has found a local exploit against the current implementation of Intel's [_[COLOR=#003366]Hyper-Threading Technology[/COLOR]_]("http://www.intel.com/technology/hyperthread/"). "*Hyper-Threading, as currently implemented on Intel Pentium Extreme Edition, Pentium 4, Mobile Pentium 4, and Xeon processors, suffers from a serious security flaw,*" Colin explains. "*This flaw permits local information disclosure, including allowing an unprivileged user to steal an RSA private key being used on the same machine. Administrators of multi-user systems are strongly advised to take action to disable Hyper-Threading immediately.*"--snip--
 
Hyper-Threading allows multi-threaded applications to execute threads in parallel on a single CPU. Intel's website [_[COLOR=#003366]explains[/COLOR]_]("http://www.intel.com/business/bss/products/hyperthreading/server/index.htm"), "*Hyper-Threading Technology enables this thread-level parallelism (TLP) by duplicating the architectural state on each processor, while sharing one set of processor execution resources. When scheduling threads, the operating system treats the two distinct architectural states as separate 'logical' processors. This allows multiprocessor capable software to run unmodified on twice as many logical processors.*"
 
So, it's up to you---

---

