---
title: "Error code 5 when installing"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by Hardhat_Harry on 2013-01-09
Hi all

Im using a single core 2.8Ghz pc with 1Gb ram and 400Gb harddrive.

On installing either 12.10 or 12.04 I get an Error Code 5 input / output error halfway through the install.

I have tried 5 CD's of different speeds 3 hard drives (although I want to use the 400Gb one) 2 different CD rom drives and 2 different IDE cables.

After reading through the forum I have booted Ubuntu into "try it" mode and accessed the disk utility which confirms the harddrive is healthy. I have unmounted the drive, formatted and remounted, I have also repartitioned the drive.

Im not doing anything fancy, its a vanilla install and Im selecting default options. 

Still getting the same error, its driving me mad.

Please help

---

### Post by Bashing-om on 2013-01-09
Hardhat_Harry; Hi !

Just a thought, were the drives used in a "raid array" ? If so, the embedded "meta data" will have to be removed. The tools to do so exist on the server install.

[INDENT][INDENT]my 2 pennies worth < == BDQ
 
[/INDENT][/INDENT]

---

### Post by Hardhat_Harry on 2013-01-09
Maybe, I havent used this pc in a couple of years it did have a RAID card in it but I dont believe the 400Gb was part of the RAID.

How can I check or can I remove the Meta data anyway to be on the safe side?

How do I do this?

Doesn't repartition or formatting do this?

---

### Post by Bashing-om on 2013-01-09
Hardhat_Harry;

Formatting the drive will not touch the "embeded" meta data.
Try this for removal of the "software raid metadata":
Boot up the install media (cd or usb):
download the raid tool dmraid:
```
 sudo apt-get install dmraid
```then in terminal run this terminal command:
```
 sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
``` sdb for the second drive, if connected.

If Hardware raid not sure !
[INDENT][INDENT][INDENT]just try'n to help < == BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by Hardhat_Harry on 2013-01-09
Ok will try that tomorrow

I have also just swapped the memory but no joy, installation failed and always on the Any Questions install screen

---

### Post by Bashing-om on 2013-01-09
Hardhat_Harry;

We still be here on the morrow, at your convenience.

Have you booted up in the "try ubuntu" mode ? Verified all devices operate as expected ?

[INDENT][INDENT]just try'n to help <== BDQ
 
[/INDENT][/INDENT]

---

### Post by Hardhat_Harry on 2013-01-10
Try Ubuntu looks fine its only the installation that fails

---

### Post by Hardhat_Harry on 2013-01-10
Ubuntu 10.04 installs without a problem......bizarre

---

### Post by Hardhat_Harry on 2013-01-10
Attempting to upgrade to Ubuntu 12.04 via manager now

---

### Post by Bashing-om on 2013-01-10
Hardhat_Harry;

How old is your processor ? I do not know the cut off version for pae support. 
Run this code to see if pae is supported:
```
cat /proc/cpuinfo
``` look for "pae" in the flags descriptor. 
[INDENT][INDENT]maybe just a poke-in-the-dark <== BDQ

[/INDENT][/INDENT]

---

