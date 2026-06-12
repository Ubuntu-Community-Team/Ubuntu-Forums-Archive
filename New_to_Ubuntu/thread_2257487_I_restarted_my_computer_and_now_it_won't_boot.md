---
title: "I restarted my computer and now it won't boot"
date: 2014-12-20
forum: New to Ubuntu
---

### Post by bigcfk on 2014-12-20
I think I'm boned. Here's the scenario: I'm  on a Acer c720 with Xubuntu 14.04 installed via the Chrubuntu method  (it is/was single boot). I replaced the harddrive with a 128gb SSD (I  think this is what failed).
  I was streaming a video and my computer froze. My system resources  weren't crazy, RAM was low, but it froze for a minute or so. I held the  power button to restart, and it restarted but at SeaBIOS it tells me:

  ```
Booting from Hard Disk... 
Boot failed: not a bootable disk  

Booting from Floppy... 
Boot failed: could not read the boot disk 

No bootable device. 
```  So I checked the boot menu and it only lists:

  ```
1. AHCI/0: PS31109S9 ATA-7 Hard-Disk (20 MiBytes)

```  I made a live disk of Xubuntu14 and tried booting it, but the computer tells me that it does not have the memory. 
  I think I'm going to remove this 128gb drive and replace it with the original 16gb drive.
  Questions:
  
[LIST]
[*]So I am boned, right?
[*]Where did my harddrive go? Could it just be loose inside somehow?
[*]Will it be possible to recover data from a (probably) failed SSD? (I stupidly haven't gotten around to backing it up yet.)
[/LIST]
 
 

I got in, and tried Boot Repair, but I don't get a "recommended repair" option, only "Create a BootInfo summary" which is here: [http://paste.ubuntu.com/9579261/](http://paste.ubuntu.com/9579261/)

I'm at a loss. Any help would be appreciated.

---

### Post by Bucky Ball on 2014-12-20
Before jumping to the SSD, I would check the RAM. If it is telling you you don't have enough memory, perhaps that has given out. 

If you have two sticks in there, test them one at a time, both in the same slot. If they both work, test them in the second slot.

If the SSD is new(ish) it is unlikely to be that (although not entirely impossible).

PS: Here's a clue from your BootInfoScript:

> Error: /dev/sda: unrecognised disk label

I presume sda is the SSD? So maybe not RAM ...

---

### Post by fantab on 2014-12-21
> Error: no partitions

Re-connect the SSD to the machine.
Tell us if your older disk is recognized or works.
Also have a look at that RAM, as suggested earlier.

---

### Post by Bucky Ball on 2014-12-22
... and considering the error you've got going on, perhaps boot from live media, launch Gparted and check the disk label. There's something there it's not liking by the looks, but that might not be the whole problem.

---

