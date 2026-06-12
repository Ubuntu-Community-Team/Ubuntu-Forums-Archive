---
title: "Samsung-535U3C: Ubuntu running slow and other small niggles."
date: 2013-06-28
forum: New to Ubuntu
---

### Post by mrthom on 2013-06-28
Hello people.

So recently ive decided that Windows 8 is annoying due to the fact its optimised for touch and though it was 50/50 between Ubuntu 13.04 and Mint, ive opted for Ubuntu. Anyway, I have a good, modern 'sleekbook' (AMD version of an ultrabook (Samsung Series 5)) which I love due to the fact that in Windows it was running in about 5 seconds, could play Civ5 (I know, i know! ;)) and runs like a dream. 

When I initially installed Ubuntu I was happy that it was fast (Not faster then Win but on par) but over the last couple weeks as ive used it more, ive noticed its got a LOT slower. When I first login I click on Firefox and the icon glows on and off for about 5-10 seconds before it opens, when I try to open up settings (software and updates) it takes about 10-20 seconds and I keep thinking ive not clicked properly so I click again and when Ubuntu catches up with itself it opens about 5 windows.

Ive looked on the forums and have found quite a few people reporting the same thing, one person suggested typing sudo hdparm -Tt /dev/sda to check speed results and this is my results 

 Timing cached reads:   
3944 MB in  2.00 seconds = 1972.88 MB/sec
 Timing buffered disk reads: 286 MB in  3.02 seconds =  94.76 MB/sec

Its my understanding that this is acceptable for an older computer but on a new sleekbook is poor. 
 
Hardware and link to more info (if needed) from Amazon...

[SIZE=2]Samsung 535U3C  13.3-inch Sleekbook - Silver (AMD A6 4455M 2.1GHz, 6Gb RAM, 500Gb HDD,  LAN, WLAN, BT, Webcam, Integrated Graphics, Windows 8)

[/SIZE]http://www.amazon.co.uk/Samsung-535U3C-13-3-inch-Sleekbook-Integrated/dp/B009SJCYBC/ref=sr_1_1?s=computers&ie=UTF8&qid=1372421807&sr=1-1&keywords=NP535
[SIZE=2]
Secondly, another small niggle is that when I start my laptop the screen brightness always resets itself. I always have my laptop on the lower brightness settings as the brightness does my eyes in but everytime I restart it resets to the highest brightness regardless of battery or AC. I was wondering if it was possible that once I set the brightness I could save it and have that brightness everytime I boot? Third small problem is that ive managed to get the power management icon in the taskbar working wonderfully which displays all powermanagement plans and speeds in order to conserve battery, however, again this resets at boot and I was wondering if their is a way to save this as default? 

I want to stick with Ubuntu but the speed thing is a massive issue that if doesnt get corrected I will end up abandoning. This is the millionth time ive tried to integrate to Linux over the last 10+ years but its been a hard and rocky road thats ended up with me ditching it in favour for Win so this time I hope to change that! 

Thank you in advance, folks and I hope that together we can resolve this issue speedily! :)

PS. It might be worth mentioning that I use TLP and the config file is pretty much default other then radio settings. I also need things explained in 'lamer' terms as im still learning my way around. :(
[/SIZE][SIZE=2]
[/SIZE]

---

### Post by snowpine on 2013-06-28
"preload" will preemptively load your favorite apps to speed up load time: [http://www.ubuntugeek.com/speed-up-your-ubuntu-12-04-with-preload.html](http://www.ubuntugeek.com/speed-up-your-ubuntu-12-04-with-preload.html)

For an overall speed boost you can try a "lightweight" desktop environment such as Xfce or LXDE. :)

---

### Post by mrthom on 2013-06-28
Thank you for your quick response, Snowpine! 

I installed "Preload" however this seems to have made minimal difference in speed. It seems that even boot is slow. I also logged into Xfce but again, it seems that there is small difference. :/

---

### Post by mrthom on 2013-06-28
Hmm, I dont know if this is off assistance but I have been carrying on my search and other users have been having the same problems. They suggest the command lines 


sudo lshw -C processor
 sudo lshw -C memory 
sudo lshw -C display

Processor results: 

 *-cpu                   
       description: CPU
       product: AMD A6-4455M APU with Radeon(tm) HD Graphics
       vendor: Advanced Micro Devices [AMD]
       physical id: 22
       bus info: cpu@0
       version: AMD A6-4455M APU with Radeon(tm) HD Graphics
       slot: P0
       size: 2100MHz
       capacity: 2100MHz
       width: 64 bits
       clock: 100MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1 cpufreq
       configuration: cores=2 enabledcores=2 threads=2

Memory:

*-firmware              
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: P07RAS.W73.130411.LEO
       date: 04/11/2013
       size: 64KiB
       capacity: 960KiB
       capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
  *-memory
       description: System Memory
       physical id: 12
       slot: System board or motherboard
       size: 8GiB
     *-bank:0
          description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
          product: Array1_PartNumber0
          vendor: A1_Manufacturer0
          physical id: 0
          serial: A1_SerNum0
          slot: A1_DIMM0
          size: 4GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:1
          description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
          vendor: Undefined
          physical id: 1
          serial: 00000000
          slot: A1_DIMM1
          size: 4GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
  *-cache:0
       description: L1 cache
       physical id: 1c
       slot: L1 CACHE
       size: 96KiB
       capacity: 96KiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
  *-cache:1
       description: L2 cache
       physical id: 1d
       slot: L2 CACHE
       size: 2MiB
       capacity: 2MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified

Display:

oot@Blackbird:/home/mr# sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Trinity [Radeon HD 7500G]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:46 memory:c0000000-cfffffff ioport:f000(size=256) memory:feb00000-feb3ffff





Hope this helps!

---

### Post by linrunner on 2013-06-28
Hi,

is there a difference in performance/hdd speed between ac and battery power?

---

### Post by mrthom on 2013-06-29
Hello,

Doesnt appear to be any difference in speeds whether connected via AC or battery, set in Performance, Conserve, ect. Im really stuck on this problem regardless of my best efforts to search high and low for the solution. :(

---

### Post by linrunner on 2013-06-30
You may want to check your hard drive's health.

Install smartmontools
```
sudo apt-get install smartmontools
```

And show the output from
```
sudo smartctl -A /dev/sda
```

---

### Post by mrthom on 2013-06-30
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.8.0-25-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

```
=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   118   100   006    Pre-fail  Always       -       168435904
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       774
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   068   060   030    Pre-fail  Always       -       8604388656
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       600 (20 24 0)
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       736
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   072   047   045    Old_age   Always       -       28 (Min/Max 23/28)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       6
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       41
193 Load_Cycle_Count        0x0032   085   085   000    Old_age   Always       -       30956
194 Temperature_Celsius     0x0022   028   053   000    Old_age   Always       -       28 (0 12 0 0 0)
196 Reallocated_Event_Count 0x000f   100   100   030    Pre-fail  Always       -       507 (8335 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   100   000    Old_age   Offline      -       35798552412667
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       2899359494
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       1551645579
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       0

```

---

### Post by ext73 on 2013-07-16
Hi - cause: poor kernel, weak settings PM, etc.. ... as using the right components will be like this ... I mean at least 2 x better;) = powerful engine [AMD APU E-350 vs AMD APU A6]:

[https://www.youtube.com/watch?v=MKFYmegb6iI](https://www.youtube.com/watch?v=MKFYmegb6iI)

[https://www.youtube.com/watch?v=f9u-jIx3jDQ](https://www.youtube.com/watch?v=f9u-jIx3jDQ)

[https://www.youtube.com/watch?v=PzmavmFF3UY](https://www.youtube.com/watch?v=PzmavmFF3UY)

[http://ubuntu.pl/forum/viewforum.php?f=216](http://ubuntu.pl/forum/viewforum.php?f=216)

[http://ubuntu.pl/forum/viewtopic.php?f=216&t=168096](http://ubuntu.pl/forum/viewtopic.php?f=216&t=168096)

[https://www.facebook.com/media/set/?set=a.525654367498061.1073741825.100001605079171&type=1&l=7360d1f3f5](https://www.facebook.com/media/set/?set=a.525654367498061.1073741825.100001605079171&type=1&l=7360d1f3f5)

[https://www.facebook.com/media/set/?set=a.525654367498061.1073741825.100001605079171&type=1&l=7360d1f3f5](https://www.facebook.com/media/set/?set=a.525654367498061.1073741825.100001605079171&type=1&l=7360d1f3f5)

Regards

---

