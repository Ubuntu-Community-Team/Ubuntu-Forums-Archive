---
title: "Folding@Home, problem with origami"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by Zephilinox on 2011-09-17
I want to start running F@H, I've installed origami and fahmon, and at first I got it to work fine, but then I wanted to change my origami install options so I deleted the /var/lib/origami folder and uninstalled the origami package, installed it again and added the options I wanted, except now I get this:

```
[10:25:52] Trying to unzip core FahCore_a3.exe
[10:25:53] Decompressed FahCore_a3.exe (5277040 bytes) successfully
[10:25:53] + Core successfully engaged
[10:26:09] Deleting current work unit & continuing...
[10:26:14] - Preparing to get new work unit...
[10:26:14] + Attempting to get work packet
[10:26:14] - Connecting to assignment server
[10:26:14] - Successful: assigned to (171.64.65.75).
[10:26:14] + News From Folding@Home: Welcome to Folding@Home
[10:26:14] Loaded queue successfully.
[10:26:18] + Closed connections
[10:26:23] 
[10:26:23] + Processing work unit
[10:26:23] Core required: FahCore_a3.exe
[10:26:23] Core found.
[10:26:23] Working on Unit 07 [September 17 10:26:23]
[10:26:23] + Working ...
[10:26:23] 
[10:26:23] *------------------------------*
[10:26:23] Folding@Home Gromacs SMP Core
[10:26:23] Version 2.22 (June 10, 2010)
[10:26:23] 
[10:26:23] Preparing to commence simulation
[10:26:23] - Ensuring status. Please wait.
[10:26:23] Created dyn
[10:26:23] - Files status OK
[10:26:23] Need version 227
[10:26:23] Error: Work unit read from disk is invalid
[10:26:23] 
[10:26:23] Folding@home Core Shutdown: CORE_OUTDATED
[10:26:28] CoreStatus = 6E (110)
[10:26:28] + Core out of date. Auto updating...
[10:26:28] - Attempting to download new core...
[10:26:28] + Downloading new core: FahCore_a3.exe
[10:26:28] + 10240 bytes downloaded
[10:26:28] + 20480 bytes downloaded
[10:26:28] + 30720 bytes downloaded
[10:26:28] + 40960 bytes downloaded
[10:26:28] + 51200 bytes downloaded
[10:26:28] + 61440 bytes downloaded
[10:26:28] + 71680 bytes downloaded
[10:26:29] + 81920 bytes downloaded
[10:26:29] + 92160 bytes downloaded
[10:26:29] + 102400 bytes downloaded
[10:26:29] + 112640 bytes downloaded
[10:26:29] + 122880 bytes downloaded
[10:26:29] + 133120 bytes downloaded
[10:26:29] + 143360 bytes downloaded
[10:26:29] + 153600 bytes downloaded
[10:26:29] + 163840 bytes downloaded
[10:26:29] + 174080 bytes downloaded
[10:26:29] + 184320 bytes downloaded
[10:26:29] + 194560 bytes downloaded
[10:26:29] + 204800 bytes downloaded
[10:26:29] + 215040 bytes downloaded
[10:26:29] + 225280 bytes downloaded
[10:26:29] + 235520 bytes downloaded
[10:26:30] + 245760 bytes downloaded
[10:26:30] + 256000 bytes downloaded
[10:26:30] + 266240 bytes downloaded
[10:26:30] + 276480 bytes downloaded
[10:26:30] + 286720 bytes downloaded
[10:26:30] + 296960 bytes downloaded
[10:26:30] + 307200 bytes downloaded
[10:26:30] + 317440 bytes downloaded
[10:26:30] + 327680 bytes downloaded
[10:26:30] + 337920 bytes downloaded
[10:26:30] + 348160 bytes downloaded
[10:26:30] + 358400 bytes downloaded
[10:26:30] + 368640 bytes downloaded
[10:26:30] + 378880 bytes downloaded
[10:26:30] + 389120 bytes downloaded
[10:26:30] + 399360 bytes downloaded
[10:26:30] + 409600 bytes downloaded
[10:26:30] + 419840 bytes downloaded
[10:26:31] + 430080 bytes downloaded
[10:26:31] + 440320 bytes downloaded
[10:26:31] + 450560 bytes downloaded
[10:26:31] + 460800 bytes downloaded
[10:26:31] + 471040 bytes downloaded
[10:26:31] + 481280 bytes downloaded
[10:26:31] + 491520 bytes downloaded
[10:26:31] + 501760 bytes downloaded
[10:26:31] + 512000 bytes downloaded
[10:26:31] + 522240 bytes downloaded
[10:26:31] + 532480 bytes downloaded
[10:26:31] + 542720 bytes downloaded
[10:26:31] + 552960 bytes downloaded
[10:26:31] + 563200 bytes downloaded
[10:26:31] + 573440 bytes downloaded
[10:26:31] + 583680 bytes downloaded
[10:26:32] + 593920 bytes downloaded
[10:26:32] + 604160 bytes downloaded
[10:26:32] + 614400 bytes downloaded
[10:26:32] + 624640 bytes downloaded
[10:26:32] + 634880 bytes downloaded
[10:26:32] + 645120 bytes downloaded
[10:26:32] + 655360 bytes downloaded
[10:26:32] + 665600 bytes downloaded
[10:26:32] + 675840 bytes downloaded
[10:26:32] + 686080 bytes downloaded
[10:26:32] + 696320 bytes downloaded
[10:26:32] + 706560 bytes downloaded
[10:26:32] + 716800 bytes downloaded
[10:26:32] + 727040 bytes downloaded
[10:26:32] + 737280 bytes downloaded
[10:26:32] + 747520 bytes downloaded
[10:26:33] + 757760 bytes downloaded
[10:26:33] + 768000 bytes downloaded
[10:26:33] + 778240 bytes downloaded
[10:26:33] + 788480 bytes downloaded
[10:26:33] + 798720 bytes downloaded
[10:26:33] + 808960 bytes downloaded
[10:26:33] + 819200 bytes downloaded
[10:26:33] + 829440 bytes downloaded
[10:26:33] + 839680 bytes downloaded
[10:26:33] + 849920 bytes downloaded
[10:26:33] + 860160 bytes downloaded
[10:26:33] + 870400 bytes downloaded
[10:26:33] + 880640 bytes downloaded
[10:26:33] + 890880 bytes downloaded
[10:26:33] + 901120 bytes downloaded
[10:26:33] + 911360 bytes downloaded
[10:26:33] + 921600 bytes downloaded
[10:26:33] + 931840 bytes downloaded
[10:26:34] + 942080 bytes downloaded
[10:26:34] + 952320 bytes downloaded
[10:26:34] + 962560 bytes downloaded
[10:26:34] + 972800 bytes downloaded
[10:26:34] + 983040 bytes downloaded
[10:26:34] + 993280 bytes downloaded
[10:26:34] + 1003520 bytes downloaded
[10:26:34] + 1013760 bytes downloaded
[10:26:34] + 1024000 bytes downloaded
[10:26:34] + 1034240 bytes downloaded
[10:26:34] + 1044480 bytes downloaded
[10:26:34] + 1054720 bytes downloaded
[10:26:34] + 1064960 bytes downloaded
[10:26:34] + 1075200 bytes downloaded
[10:26:34] + 1085440 bytes downloaded
[10:26:34] + 1095680 bytes downloaded
[10:26:35] + 1105920 bytes downloaded
[10:26:35] + 1116160 bytes downloaded
[10:26:35] + 1126400 bytes downloaded
[10:26:35] + 1136640 bytes downloaded
[10:26:35] + 1146880 bytes downloaded
[10:26:35] + 1157120 bytes downloaded
[10:26:35] + 1167360 bytes downloaded
[10:26:35] + 1177600 bytes downloaded
[10:26:35] + 1187840 bytes downloaded
[10:26:35] + 1198080 bytes downloaded
[10:26:35] + 1208320 bytes downloaded
[10:26:35] + 1218560 bytes downloaded
[10:26:35] + 1228800 bytes downloaded
[10:26:35] + 1239040 bytes downloaded
[10:26:35] + 1249280 bytes downloaded
[10:26:35] + 1259520 bytes downloaded
[10:26:36] + 1269760 bytes downloaded
[10:26:36] + 1280000 bytes downloaded
[10:26:36] + 1290240 bytes downloaded
[10:26:36] + 1300480 bytes downloaded
[10:26:36] + 1310720 bytes downloaded
[10:26:36] + 1320960 bytes downloaded
[10:26:36] + 1331200 bytes downloaded
[10:26:36] + 1341440 bytes downloaded
[10:26:36] + 1351680 bytes downloaded
[10:26:36] + 1361920 bytes downloaded
[10:26:36] + 1372160 bytes downloaded
[10:26:36] + 1382400 bytes downloaded
[10:26:36] + 1392640 bytes downloaded
[10:26:36] + 1402880 bytes downloaded
[10:26:36] + 1413120 bytes downloaded
[10:26:36] + 1423360 bytes downloaded
[10:26:36] + 1433600 bytes downloaded
[10:26:36] + 1443840 bytes downloaded
[10:26:37] + 1454080 bytes downloaded
[10:26:37] + 1464320 bytes downloaded
[10:26:37] + 1474560 bytes downloaded
[10:26:37] + 1484800 bytes downloaded
[10:26:37] + 1495040 bytes downloaded
[10:26:37] + 1505280 bytes downloaded
[10:26:37] + 1515520 bytes downloaded
[10:26:37] + 1525760 bytes downloaded
[10:26:37] + 1536000 bytes downloaded
[10:26:37] + 1546240 bytes downloaded
[10:26:37] + 1556480 bytes downloaded
[10:26:37] + 1566720 bytes downloaded
[10:26:37] + 1576960 bytes downloaded
[10:26:37] + 1587200 bytes downloaded
[10:26:37] + 1597440 bytes downloaded
[10:26:38] + 1607680 bytes downloaded
[10:26:38] + 1617920 bytes downloaded
[10:26:38] + 1628160 bytes downloaded
[10:26:38] + 1638400 bytes downloaded
[10:26:38] + 1648640 bytes downloaded
[10:26:38] + 1658880 bytes downloaded
[10:26:38] + 1669120 bytes downloaded
[10:26:38] + 1679360 bytes downloaded
[10:26:38] + 1689600 bytes downloaded
[10:26:38] + 1699840 bytes downloaded
[10:26:38] + 1710080 bytes downloaded
[10:26:38] + 1720320 bytes downloaded
[10:26:38] + 1730560 bytes downloaded
[10:26:38] + 1740800 bytes downloaded
[10:26:38] + 1751040 bytes downloaded
[10:26:38] + 1761280 bytes downloaded
[10:26:38] + 1771520 bytes downloaded
[10:26:39] + 1781760 bytes downloaded
[10:26:39] + 1792000 bytes downloaded
[10:26:39] + 1802240 bytes downloaded
[10:26:39] + 1812480 bytes downloaded
[10:26:39] + 1822720 bytes downloaded
[10:26:39] + 1832960 bytes downloaded
[10:26:39] + 1843200 bytes downloaded
[10:26:39] + 1853440 bytes downloaded
[10:26:39] + 1863680 bytes downloaded
[10:26:39] + 1873920 bytes downloaded
[10:26:39] + 1884160 bytes downloaded
[10:26:39] + 1894400 bytes downloaded
[10:26:39] + 1904640 bytes downloaded
[10:26:39] + 1914880 bytes downloaded
[10:26:39] + 1925120 bytes downloaded
[10:26:39] + 1935360 bytes downloaded
[10:26:39] + 1945600 bytes downloaded
[10:26:39] + 1955840 bytes downloaded
[10:26:40] + 1966080 bytes downloaded
[10:26:40] + 1976320 bytes downloaded
[10:26:40] + 1986560 bytes downloaded
[10:26:40] + 1996800 bytes downloaded
[10:26:40] + 2007040 bytes downloaded
[10:26:40] + 2017280 bytes downloaded
[10:26:40] + 2027520 bytes downloaded
[10:26:40] + 2037760 bytes downloaded
[10:26:40] + 2048000 bytes downloaded
[10:26:40] + 2058240 bytes downloaded
[10:26:40] + 2068480 bytes downloaded
[10:26:40] + 2078720 bytes downloaded
[10:26:40] + 2088960 bytes downloaded
[10:26:40] + 2099200 bytes downloaded
[10:26:40] + 2109440 bytes downloaded
[10:26:41] + 2119680 bytes downloaded
[10:26:41] + 2129920 bytes downloaded
[10:26:41] + 2140160 bytes downloaded
[10:26:41] + 2150400 bytes downloaded
[10:26:41] + 2160640 bytes downloaded
[10:26:41] + 2170880 bytes downloaded
[10:26:41] + 2181120 bytes downloaded
[10:26:41] + 2191360 bytes downloaded
[10:26:41] + 2201600 bytes downloaded
[10:26:41] + 2211840 bytes downloaded
[10:26:41] + 2222080 bytes downloaded
[10:26:41] + 2232320 bytes downloaded
[10:26:41] + 2242560 bytes downloaded
[10:26:41] + 2252800 bytes downloaded
[10:26:41] + 2263040 bytes downloaded
[10:26:42] + 2268923 bytes downloaded
[10:26:42] Verifying core Core_a3.fah...
[10:26:42] Signature is VALID
[10:26:42] 
[10:26:42] Trying to unzip core FahCore_a3.exe
[10:26:42] Decompressed FahCore_a3.exe (5277040 bytes) successfully
[10:26:42] + Core successfully engaged
[10:27:07] 
[10:27:07] + Processing work unit
[10:27:07] Core required: FahCore_a3.exe
[10:27:07] Core found.
[10:27:07] Working on Unit 07 [September 17 10:27:07]
[10:27:07] + Working ...
[10:27:08] 
[10:27:08] *------------------------------*
[10:27:08] Folding@Home Gromacs SMP Core
[10:27:08] Version 2.22 (June 10, 2010)
[10:27:08] 
[10:27:08] Preparing to commence simulation
[10:27:08] - Ensuring status. Please wait.
[10:27:08] 
[10:27:08] Folding@home Core Shutdown: INTERRUPTED
[10:27:12] CoreStatus = 6E (110)
[10:27:12] + Core out of date. Auto updating...
[10:27:12] New core downloaded for this work unit, but still out of date.
[10:27:12] 
Folding@Home will go to sleep for 1 day as there have been 5 consecutive Cores executed which failed to complete a work unit.
[10:27:12] (To wake it up early, quit the application and restart it.)
[10:27:12] If problems persist, please visit our website at http://folding.stanford.edu for help.
[10:27:12] + Sleeping...
```I'm using Xubuntu, did I screw up origami by deleting the /var/lib/origami folder? (origami re-created it) or is it something else?

The first time I installed it I did

```
sudo origami install -u Zephilinox -t 45104
```the second time I did

```
sudo origami install -u Zephilinox -t 45104 -p amd64 -s big -k {mypasskey}
```

I've tried re-starting, re-installing origami, re-installing fahmon, re-loading my fahmon client, updating fahmon, updating workload, but nothing has worked.

---

### Post by P05TMAN on 2011-09-17
Look into this command before trying (and perhaps someone with more experience may add to this)

```

sudo apt-cache purge *program name*

```Hope this kind of paves the way to a more concrete answer

*That command I found is to completely remove a program; perhaps when you tried to uninstall there were other files that were left*

DON'T try this yet until you learn more about it, I am trying to facilitate a better, more explanatory answer for you.

---

### Post by Zephilinox on 2011-09-18
> **P05TMAN said:**
> Look into this command before trying (and perhaps someone with more experience may add to this)

```

sudo apt-cache purge *program name*

```Hope this kind of paves the way to a more concrete answer

*That command I found is to completely remove a program; perhaps when you tried to uninstall there were other files that were left*

DON'T try this yet until you learn more about it, I am trying to facilitate a better, more explanatory answer for you.  Thanks, but I already tried purging the program (why did you use apt-cache?) anyway I managed to resolve it after following section 2 of [http://ubuntuforums.org/showthread.php?t=1540733](http://ubuntuforums.org/showthread.php?t=1540733) seems there is a problem with origami and smpt.

---

