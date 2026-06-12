---
title: "Ubuntu 18.04: Browsers keep crashing even after OS reinstall"
date: 2020-04-15
forum: New to Ubuntu
---

### Post by nem25 on 2020-04-15
Hey!

I'm new to the Ubuntu forums so hopefully I've got all the posting rules down right.

I've been having a lot of problems with my Ubuntu 18.04. I was using it for the last 5 years (without any reinstalls) and a few weeks ago, my Chrome started crashing with the Aw Snap error. So I got Firefox in the interim and that also started crashing with it's version of the Aw Snap.
Soon after that, a lot of things stopped working properly. It was like multiple organ failure. There was a new crash report every few hours coming from a new file. Sometimes SSO, sometimes VSCode or Chrome or something I have never heard of. It was unusable. I would open a program and it would shut down automatically.

I even tried Deja Dup to back up my files and after 3 days of crashing and corrupted backups, I gave up--copied out a few relevant files manually and wiped the computer clean with a new reinstall of 18.04. 

I did a minimal reinstall. Yesterday, this new install started crashing again. I'm only using Chrome and Firefox on it to test it out and Aw Snap errors every few hours. I have run all hardware diagnostic tools from the BIOS; they all pass. Is it something to do with the recent 18.04 updates? Has my laptop somehow become incompatible?

I have a Lenovo T450s with 12GB RAM and a 256GB SSD.

I had even posted a few weeks back on [AskUbuntu]("https://askubuntu.com/questions/1223691/ubuntu-18-04-chrome-chromium-firefox-keep-crashing-with-aw-snap") but got no replies there.

I would really really appreciate any kind of help. I can't go back to Windows and I don't particularly want to learn a new Linux distro. I'm a software developer so my life revolves around this computer. Hardware wise everything seems to be working fine.

Happy to provide any additional information.
Thanks in advance!

---

### Post by CelticWarrior on 2020-04-15
> I even tried Deja Dup to back up my files and after 3 days of crashing and corrupted backups

This in conjunction with the same symptoms reappearing after a fresh install suggest the drive itself is failing.

---

### Post by Autodave on 2020-04-15
Sounds like an SSD failing to me also.  Could also be overheating.  Could be a RAM chip going bad.

When was the last time you checked and cleaned the internals?  Did you run a mem test and SSD test?

I would boot it from a USB stick and run it from there for a few hours.  If it runs OK, then you know it is the SSD.  If not, then you need to be looking hard at the RAM.

Realize that passing the SSD test and the RAM test does not mean that they are good!  Failing one of those tests (at least in my opinion) guarantees that it is bad.

---

### Post by nem25 on 2020-04-17
> **Autodave said:**
> Sounds like an SSD failing to me also.  Could also be overheating.  Could be a RAM chip going bad.

When was the last time you checked and cleaned the internals?  Did you run a mem test and SSD test?

I would boot it from a USB stick and run it from there for a few hours.  If it runs OK, then you know it is the SSD.  If not, then you need to be looking hard at the RAM.

Realize that passing the SSD test and the RAM test does not mean that they are good!  Failing one of those tests (at least in my opinion) guarantees that it is bad.

I ran all the hardware diagnostics available in the BIOS. I couldn't find memtest86 because I believe my computer might be in UEFI boot mode. Sorry I'm not an expert at this.
Is there any way those diagnostics would pass even if the the SSD and RAM are "broken"?

The USB stick is a good idea. I might try that.

Is there anything else I can do to figure out if it's software or hardware? Given the current scenario with COVID, I don't have access to any new hardware. So it's a bit concerning.

---

### Post by mörgæs on 2020-04-17
Please run ```
sudo lshw -sanitize -C memory
``` and post the results in CODE tags.

---

### Post by nem25 on 2020-04-18
> **mörgæs said:**
> Please run ```
sudo lshw -sanitize -C memory
``` and post the results in CODE tags.

```
 *-cache                          
      description: L1 cache
       physical id: 3
       slot: L1 Cache
       size: 32KiB
       capacity: 32KiB
       capabilities: synchronous internal write-back data
       configuration: level=1
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: L1 Cache
       size: 32KiB
       capacity: 32KiB
       capabilities: synchronous internal write-back instruction
       configuration: level=1
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: L2 Cache
       size: 256KiB
       capacity: 256KiB
       capabilities: synchronous internal write-back unified
       configuration: level=2
  *-cache:2
       description: L3 cache
       physical id: 7
       slot: L3 Cache
       size: 3MiB
       capacity: 3MiB
       capabilities: synchronous internal write-back unified
       configuration: level=3
  *-memory
       description: System Memory
       physical id: 8
       slot: System board or motherboard
       size: 12GiB
     *-bank:0
          description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
          product: K4B8G1646B-MYK0
          vendor: Samsung
          physical id: 0
          serial: [REMOVED]
          slot: ChannelA-DIMM0
          size: 4GiB
          width: 64 bits
          clock: 1600MHz (0.6ns)
     *-bank:1
          description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
          product: HMT41GS6BFR8A-PB
          vendor: Hynix/Hyundai
          physical id: 1
          serial: [REMOVED]
          slot: ChannelB-DIMM0
          size: 8GiB
          width: 64 bits
          clock: 1600MHz (0.6ns)
  *-firmware
       description: BIOS
       vendor: LENOVO
       physical id: 31
       version: JBET51WW (1.16 )
       date: 07/08/2015
       size: 128KiB
       capacity: 15MiB
       capabilities: pci pnp upgrade shadowing cdboot bootselect acpi usb biosbootspecification uefi



```

---

### Post by mörgæs on 2020-04-18
The 12 GB of memory is split into a 4 and an 8 GB module. Try to remove the 8 GB one to see if the system gets stable.

The UEFI firmware is old but don't upgrade it as long as the computer is prone to crashing.

---

### Post by nem25 on 2020-04-27
> **mörgæs said:**
> The 12 GB of memory is split into a 4 and an 8 GB module. Try to remove the 8 GB one to see if the system gets stable.

The UEFI firmware is old but don't upgrade it as long as the computer is prone to crashing.

I managed to run memtest86 from the boot menu. The non + version works in UEFI. The test aborted due to too many errors :(
I even tried to rub the RAM with an eraser (apparently that helps) but one of my RAMs is soldered.

The results of the memtest86 rub is below:

```

**Result summary**

[COLOR=#000000][FONT=Arial][TABLE="width: 600"]
[TR]
[TD="class: value"]Test Start Time[/TD]
[TD="class: altvalue, width: 65%"]2020-04-23 08:16:58[/TD]
[/TR]
[TR]
[TD="class: value, width: 35%"]Elapsed Time[/TD]
[TD="class: altvalue, width: 65%"]0:08:23[/TD]
[/TR]
[TR]
[TD="class: value, width: 35%"]Memory Range Tested[/TD]
[TD="class: altvalue, width: 65%"]0x0 - 33E000000 (13280MB)[/TD]
[/TR]
[TR]
[TD="class: value, width: 35%"]CPU Selection Mode[/TD]
[TD="class: altvalue, width: 65%"]Parallel (All CPUs)[/TD]
[/TR]
[TR]
[TD="class: value, width: 35%"]ECC Polling[/TD]
[TD="class: altvalue, width: 65%"]Enabled[/TD]
[/TR]
[TR]
[TD="class: value, width: 35%"]# Tests Passed[/TD]
[TD="class: FAIL, width: 65%"]1/7 (14%)[/TD]
[/TR]
[/TABLE]
[TABLE="width: 600"]
[TR]
[TD="class: value"]Lowest Error Address[/TD]
[TD="class: altvalue, width: 65%"]0x225A8C008 (8794MB)[/TD]
[/TR]
[TR]
[TD="class: value, width: 35%"]Highest Error Address[/TD]
[TD="class: altvalue, width: 65%"]0x227A8E2E8 (8826MB)[/TD]
[/TR]
[TR]
[TD="class: value, width: 35%"]Bits in Error Mask[/TD]
[TD="class: altvalue, width: 65%"]000000000000FF00[/TD]
[/TR]
[TR]
[TD="class: value, width: 35%"]Bits in Error[/TD]
[TD="class: altvalue, width: 65%"]8[/TD]
[/TR]
[TR]
[TD="class: value, width: 35%"]Max Contiguous Errors[/TD]
[TD="class: altvalue, width: 65%"]1[/TD]
[/TR]
[/TABLE]
[TABLE="width: 600"]
[TR]
[TD="class: header"]Test[/TD]
[TD="class: header, width: 20%, bgcolor: #222222"]# Tests Passed[/TD]
[TD="class: header, width: 20%, bgcolor: #222222"]Errors[/TD]
[/TR]
[TR]
[TD="class: value, width: 60%"]Test 0 [Address test, walking ones, 1 CPU][/TD]
[TD="class: altvalue, width: 20%"]1/1 (100%)[/TD]
[TD="class: altvalue, width: 20%"]0[/TD]
[/TR]
[TR="class: fail"]
[TD="class: value, width: 60%"]Test 1 [Address test, own address, 1 CPU][/TD]
[TD="class: altvalue, width: 20%"]0/1 (0%)[/TD]
[TD="class: altvalue, width: 20%"]44[/TD]
[/TR]
[TR="class: fail"]
[TD="class: value, width: 60%"]Test 2 [Address test, own address][/TD]
[TD="class: altvalue, width: 20%"]0/1 (0%)[/TD]
[TD="class: altvalue, width: 20%"]52[/TD]
[/TR]
[TR="class: fail"]
[TD="class: value, width: 60%"]Test 3 [Moving inversions, ones & zeroes][/TD]
[TD="class: altvalue, width: 20%"]0/1 (0%)[/TD]
[TD="class: altvalue, width: 20%"]433[/TD]
[/TR]
[TR="class: fail"]
[TD="class: value, width: 60%"]Test 4 [Moving inversions, 8-bit pattern][/TD]
[TD="class: altvalue, width: 20%"]0/1 (0%)[/TD]
[TD="class: altvalue, width: 20%"]2127[/TD]
[/TR]
[TR="class: fail"]
[TD="class: value, width: 60%"]Test 5 [Moving inversions, random pattern][/TD]
[TD="class: altvalue, width: 20%"]0/1 (0%)[/TD]
[TD="class: altvalue, width: 20%"]3174[/TD]
[/TR]
[TR="class: fail"]
[TD="class: value, width: 60%"]Test 6 [Block move, 64-byte blocks][/TD]
[TD="class: altvalue, width: 20%"]0/1 (0%)[/TD]
[TD="class: altvalue, width: 20%"]515[/TD]
[/TR]
[TR]
[TD="class: value, width: 60%"]Test 7 [Moving inversions, 32-bit pattern][/TD]
[TD="class: altvalue, width: 20%"]0/0 (0%)[/TD]
[TD="class: altvalue, width: 20%"]3690[/TD]
[/TR]
[TR]
[TD="class: value, width: 60%"]Test 8 [Random number sequence][/TD]
[TD="class: altvalue, width: 20%"]0/0 (0%)[/TD]
[TD="class: altvalue, width: 20%"]0[/TD]
[/TR]
[TR]
[TD="class: value, width: 60%"]Test 9 [Modulo 20, ones & zeros][/TD]
[TD="class: altvalue, width: 20%"]0/0 (0%)[/TD]
[TD="class: altvalue, width: 20%"]0[/TD]
[/TR]
[TR]
[TD="class: value, width: 60%"]Test 10 [Bit fade test, 2 patterns, 1 CPU][/TD]
[TD="class: altvalue, width: 20%"]0/0 (0%)[/TD]
[TD="class: altvalue, width: 20%"]0[/TD]
[/TR]
[TR]
[TD="class: value, width: 60%"]Test 13 [Hammer test][/TD]
[TD="class: altvalue, width: 20%"]0/0 (0%)[/TD]
[TD="class: altvalue, width: 20%"]0[/TD]
[/TR]
[/TABLE]
[TABLE="width: 600"]
[TR]
[TD="class: header, bgcolor: #222222"]Last 10 Errors[/TD]
[/TR]
[TR]
[TD="class: value"]2020-04-23 08:25:21 - [Data Error] Test: 7, CPU: 0, Address: 225A8C108, Expected: 00000008, Actual: 00002008[/TD]
[/TR]
[TR]
[TD="class: value"]2020-04-23 08:25:21 - [Data Error] Test: 7, CPU: 0, Address: 225A8C148, Expected: 00080000, Actual: 00088200[/TD]
[/TR]
[TR]
[TD="class: value"]2020-04-23 08:25:21 - [Data Error] Test: 7, CPU: 0, Address: 225A8C188, Expected: 00000008, Actual: 00002008[/TD]
[/TR]
[TR]
[TD="class: value"]2020-04-23 08:25:21 - [Data Error] Test: 7, CPU: 0, Address: 225A8C208, Expected: 00000008, Actual: 00008008[/TD]
[/TR]
[TR]
[TD="class: value"]2020-04-23 08:25:21 - [Data Error] Test: 7, CPU: 0, Address: 225A8C248, Expected: 00080000, Actual: 00085000[/TD]
[/TR]
[TR]
[TD="class: value"]2020-04-23 08:25:21 - [Data Error] Test: 7, CPU: 0, Address: 225A8C308, Expected: 00000008, Actual: 00000108[/TD]
[/TR]
[TR]
[TD="class: value"]2020-04-23 08:25:21 - [Data Error] Test: 7, CPU: 0, Address: 225A8C348, Expected: 00080000, Actual: 0008D200[/TD]
[/TR]
[TR]
[TD="class: value"]2020-04-23 08:25:21 - [Data Error] Test: 7, CPU: 0, Address: 225A8C488, Expected: 00000008, Actual: 00004108[/TD]
[/TR]
[TR]
[TD="class: value"]2020-04-23 08:25:21 - [Data Error] Test: 7, CPU: 0, Address: 225A8C508, Expected: 00000008, Actual: 00002008[/TD]
[/TR]
[TR]
[TD="class: value"]2020-04-23 08:25:21 - [Data Error] Test: 7, CPU: 0, Address: 225A8C548, Expected: 00080000, Actual: 00088000[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]

```

---

### Post by CelticWarrior on 2020-04-27
Now you should remove the removable one and test again. If there are errors still that is bad news, that one can't be replaced.

---

### Post by nem25 on 2020-05-05
> **CelticWarrior said:**
> Now you should remove the removable one and test again. If there are errors still that is bad news, that one can't be replaced.

Hey,

Ok so I did that and there weren't any errors on the soldered RAM. I had to reinstall Ubuntu. I actually landed up doing it with 20.04 since it was a full wipe anyways.
It seems to be working ok but I have had few SIGSEGV errors on applications. Like Firefox, Gnome calendar. Maybe this is because my system is running on 4GB RAM now.

I guess I will just keep using it until Amazon opens up for delivery and I can buy some new RAM.

Thank you all for helping me so much!

---

### Post by mörgæs on 2020-05-05
You're welcome. If you consider the problem solved please mark the thread so.

With a stable computer you could update UEFI.

---

