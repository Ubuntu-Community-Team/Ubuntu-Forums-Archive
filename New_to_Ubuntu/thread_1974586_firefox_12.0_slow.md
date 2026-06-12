---
title: "firefox 12.0 slow?"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by al.adab on 2012-05-06
hello,

recently updated to Xubutu 12.04. All is well except for Firefox 12.0: painfully slow - particularly the Google search option, where even typing itself is slow. 

Any idea? This wasn't the case on Xubuntu 11.10 - same addons, extension. Same computer. 

Chrome works fine, by comparison.

---

### Post by al.adab on 2012-05-06
it seems to be getting worse - I tried to remove "flash-aid" (the only extension I didn't have on Xubuntu 11.10) to no avail. 

At the moment, even writing an email or this very message on Ubuntu Forums is a nightmare...

I confirm that Chrome works perfectly fine. I could easily switch to Chrome if I didn't somehow like Firefox better...

Internet connection is fast. No problem on that side...

---

### Post by al.adab on 2012-05-06
found someone with the same issue - no solution, though
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/990997](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/990997)

---

### Post by Peripheral Visionary on 2012-05-06
The latest build of Seamonkey is wicked fast compared to Firefox. It's also a Mozilla project and most of the cool add-ons and stuff are compatible!

I love Midori too, super fast! Except that it crashes every 4th or 5th page load, don't know why.

Perhaps the next version of Firefox will be better.

---

### Post by idoitprone on 2012-05-06
> **Peripheral Visionary said:**
> The latest build of Seamonkey is wicked fast compared to Firefox. It's also a Mozilla project and most of the cool add-ons and stuff are compatible!

I love Midori too, super fast! Except that it crashes every 4th or 5th page load, don't know why.

Perhaps the next version of Firefox will be better.

your probably using a outdated version of midori
**[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)**

HEre the link to the ppa dont forget to install webkit ppa


OP If your firefox is slow, then you need better ram or use midori.
Chrome and firefox will only be more memory intensive in the future, so save yourself the trouble and use a different browser


```
sudo add-apt-repository ppa:midori/ppa
sudo add-apt-repository ppa:webkit-team

```

---

### Post by al.adab on 2012-05-06
thanx both. 

is it a good idea to purge-remove firefox? or does it contain packages, etc, that are necessary to run seamonkey and/or midori?

---

### Post by al.adab on 2012-05-06
Btw, not so sure I like Midori but Seamonkey rocks! :) great suggestion. Thanx!

---

### Post by al.adab on 2012-05-08
if silence means that removing-purging Firefox is foolish, I'll edit this thread as "solved" :)

---

### Post by brainwash on 2012-05-08
Can you reproduce the issue, if you run Firefox in safe mode?
```
firefox -safe-mode
```
Maybe a new Firefox profile might solve the problem. Renaming your current profile forces Firefox to create a fresh one:
```
mv ~/.mozilla ~/.mozilla.bak
```

---

### Post by al.adab on 2012-05-08
thanks brainwash

couldn't reproduce it in safe mode. I've made a new profile as you suggested. Will test it + get back on it in a couple of days.

---

### Post by al.adab on 2012-05-09
new profile tested - same as before. Painfully slow. back to Seamonkey. 

how do I get rid of the old Firefox profile - and all the clutter associated with it?

---

### Post by idoitprone on 2012-05-09
> **al.adab said:**
> new profile tested - same as before. Painfully slow. back to Seamonkey. 

how do I get rid of the old Firefox profile - and all the clutter associated with it?

post output of 

```
cat /proc/meminfo
```
i have reason to believe that your ram is painfully slow

---

### Post by iMurshaq on 2012-05-09
I wouldn't recommend it but if necessary, you can purge firefox. Also give Chromium a try, I love it.

---

### Post by al.adab on 2012-05-09
~$ cat /proc/meminfo
MemTotal:        1025024 kB
MemFree:          163080 kB
Buffers:           46760 kB
Cached:           431648 kB
SwapCached:          200 kB
Active:           371276 kB
Inactive:         397320 kB
Active(anon):     261848 kB
Inactive(anon):    32140 kB
Active(file):     109428 kB
Inactive(file):   365180 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:        138632 kB
HighFree:           1824 kB
LowTotal:         886392 kB
LowFree:          161256 kB
SwapTotal:        522236 kB
SwapFree:         521840 kB
Dirty:               136 kB
Writeback:             0 kB
AnonPages:        290044 kB
Mapped:            92476 kB
Shmem:              3800 kB
Slab:              27892 kB
SReclaimable:      16296 kB
SUnreclaim:        11596 kB
KernelStack:        2336 kB
PageTables:         5220 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1034748 kB
Committed_AS:    1460900 kB
VmallocTotal:     122880 kB
VmallocUsed:       16744 kB
VmallocChunk:      97644 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       98296 kB
DirectMap4M:      811008 kB

---

### Post by idoitprone on 2012-05-09
> **al.adab said:**
> ~$ cat /proc/meminfo
MemTotal:        1025024 kB
MemFree:          163080 kB
Buffers:           46760 kB
Cached:           431648 kB
SwapCached:          200 kB
Active:           371276 kB
Inactive:         397320 kB
Active(anon):     261848 kB
Inactive(anon):    32140 kB
Active(file):     109428 kB
Inactive(file):   365180 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:        138632 kB
HighFree:           1824 kB
LowTotal:         886392 kB
LowFree:          161256 kB
SwapTotal:        522236 kB
SwapFree:         521840 kB
Dirty:               136 kB
Writeback:             0 kB
AnonPages:        290044 kB
Mapped:            92476 kB
Shmem:              3800 kB
Slab:              27892 kB
SReclaimable:      16296 kB
SUnreclaim:        11596 kB
KernelStack:        2336 kB
PageTables:         5220 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1034748 kB
Committed_AS:    1460900 kB
VmallocTotal:     122880 kB
VmallocUsed:       16744 kB
VmallocChunk:      97644 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       98296 kB
DirectMap4M:      811008 kB

opps wrong command

well you have only 1 gb of ram, so any modern broswer will give you pain
```
sudo dmidecode --type 17
```

---

### Post by al.adab on 2012-05-10
that's funny 'cause no browser ever gave me any pain up to xubuntu 11.10...the 1gb Ram seemed to be all i needed. Plus both Seamonkey and Chrome run perfectly...it's only Firefox that's acting up. 

anyway, will test it on the new command asap

---

### Post by brainwash on 2012-05-10
So Firefox in safe mode (no extensions and so on) works ok, but a fresh profile does not solve the problem. Weird.

If hardware acceleration is enabled in Firefox (Options > Advanced > General > Use hardware acceleration when available) and supported by your GPU (about:support > Graphics), it could somehow cause the slow performance. But it is more likely disabled anyway.

---

### Post by al.adab on 2012-05-11
i'll try that. here's the result in the meantime: 

~$ sudo dmidecode --type 17
[sudo] password for imageraw: 
# dmidecode 2.11
SMBIOS version fixup (2.33 -> 2.3).
SMBIOS 2.3 present.

Handle 0x002D, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002C
	Error Information Handle: No Error
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM 1
	Bank Locator: Bank 0/1
	Type: DDR
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

Handle 0x002E, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002C
	Error Information Handle: No Error
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM 2
	Bank Locator: Bank 2/3
	Type: DDR
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

---

### Post by ssherwood on 2012-05-11
install google chrome its fast and is up-to-date with latest web technology with its web kits and it easier for any flash videos and content.

I only use fireox for web design previewing

Stephen

---

### Post by al.adab on 2012-05-12
hardware acceleration was enabled - it wasn't me :) 

unticked it + will try again for a couple of days + report back. Chrome is definitely faster.

---

### Post by Peripheral Visionary on 2012-05-12
Since upgrading to Precise, I don't have the crashes in Midori that I had with Lucid. And the font rendering problem is cured as well. Ad-blocking, private browsing option, lots to love now. I still love my Seamonkey, but it's nice to know I have this superb ultralight option as well!

---

### Post by ssherwood on 2012-05-13
the ubuntu branding package has a little to do with it as they have stripped out the AIO menu tab which actually consisted of sum generic global functions so that could be why its slow and maybe not the 3d accelerator.

Stephen

---

### Post by brainwash on 2012-05-14
> **ssherwood said:**
> the ubuntu branding package has a little to do with it as they have stripped out the AIO menu tab which actually consisted of sum generic global functions so that could be why its slow and maybe not the 3d accelerator.
Simply hide the menu bar and the menu tab gets activated ([Alt]+V -> T -> M). However, this should not affect the overall performance in any way.

---

