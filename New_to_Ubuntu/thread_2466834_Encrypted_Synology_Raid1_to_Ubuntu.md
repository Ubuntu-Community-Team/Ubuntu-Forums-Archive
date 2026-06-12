---
title: "Encrypted Synology Raid1 to Ubuntu"
date: 2021-09-07
forum: New to Ubuntu
---

### Post by ajbower86 on 2021-09-07
Hello ubuntu community,

_Cause:_
I had a hardware failure on Synology DS920+ Friday morning which has all my work data.  In my discovery and trouble shooting my best suspect was motherboard or power supply unit.  I quickly found that both were proprietary and that i had no local option to replace or troubleshoot this device at which point i scrambled for an ultimate change of operation.

_Issue needing resolved:_
I decided to follow the recovery instructions from Synology which worked, however i have no way to read the individual folders (3) within the mounted drive as they are encrypted.  I cannot find a guide that helps me apply the encryption code/key, to allow me to read the files.The entire disk is not encrypted, only the 3 folders, all part of Volume_1, which coincidentally is the entire data set i need to access and all share the same encryption key.

_End goal:_
Ultimately i want to migrate this data to operate with Ubuntu Desktop in a server setup which i would access within my network as i did the Synology and also with a ISP IPv4 VPN access.  I am far from advanced enough to run Ubuntu server which i understand lacks a UI i would remotely be familiar with.

Your help in access to this data is most appreciated.  If i need to add another disk to decrypt the data to that would not be any issue.


Thank you!

References:
**Synology to ubuntu recovery instructions -** [https://kb.synology.com/en-my/DSM/tutorial/How_can_I_recover_data_from_my_DiskStation_using_a_PC](https://kb.synology.com/en-my/DSM/tutorial/How_can_I_recover_data_from_my_DiskStation_using_a_PC)
**Ubuntu USB Boot creation -** [https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#10-installation-complete](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#10-installation-complete)
**Old command 'ecryptfs' -** *(cannot find suitable replacement to try)* [https://web.archive.org/web/20190723214141/https://robertcastle.com/2012/10/howto-recover-synology-encrypted-folders-in-linux/](https://web.archive.org/web/20190723214141/https://robertcastle.com/2012/10/howto-recover-synology-encrypted-folders-in-linux/)
**Reading on LUKS*** (I cannot understand this or get any luks commands to function)* [https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)

---

### Post by scorp123 on 2021-09-08
> however i have no way to read the individual folders (3) within the mounted drive as they are encrypted. 

And what mechanism are they encrypted with?

---

