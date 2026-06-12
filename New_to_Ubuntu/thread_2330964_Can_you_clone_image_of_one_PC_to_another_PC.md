---
title: "Can you clone image of one PC to another PC?"
date: 2016-07-16
forum: New to Ubuntu
---

### Post by zbernie on 2016-07-16
If I have an image of my Dell laptop running Ubuntu 16.04, can I then by a Dell PC, then DD the image to the new PC?  I'm thinking not, because the existing image will have drivers and so forth, for the laptop.

-Thanks

---

### Post by Frogs Hair on 2016-07-16
Yes , clonezilla and similar programs can clone an image , but I can't address hardware/driver considerations.

---

### Post by &amp;KyT$0P# on 2016-07-16
Don't do it unless the two disks are exactly the same size.  Either it'll get cut off or there will be much unusable space on the target disk.

Anyway, if the resulting system boots then can't you just use the normal apt-get / Synaptic / "Additional Drivers" settings / etc. to install the proper drivers (and uninstall the wrong ones) for the new setup?

---

### Post by Frogs Hair on 2016-07-16
For one computer a clean installation  would be quicker and safer than a clone for the reason stated above. By the time you create the clone and format you could have installed the same programs , themes and so on . File transfer via cloud or external device wouldn't take long.

---

### Post by cariboo on 2016-07-16
Clonezilla allows you to clone either to a larger or smaller disk. I've done it many times with Windows installs, never tried with an Ubuntu install, as it takes so little time to do a fresh install.

---

### Post by sudodus on 2016-07-17
In general, linux systems are portable, but there are exceptions. The built in drivers are selected automatically for the hardware detected in each computer, but if you have installed some proprietary driver for example for the graphics or wifi, there can be problems. So I suggest that you remove any proprietary drivers, if you have installed such drivers, unless you know that the new computer also has hardware that needs/wants such {a driver/drivers}.

1 - If you have a fairly basic system, it is much easier to make a ***fresh installation*** and transfer your personal files afterwards.

2 - If there are many tweaks, you might copy your home directory to a ***separate home partition*** in the new computer, install a fresh system, but select something else at the partitioning page and select that partition as /home of the new system. Do ***not*** format the /home partition! You want the tweaks stored in the home folder(s) to be preserved.

3 - If you have installed many program packages and tweaked a lot at the system level (which is not stored in the home partition), it may be a good idea to ***clone the system***, and ***Clonezilla*** is a good tool. If you clone the whole drive, the target drive must be of the same size or larger (not one single bit smaller). If there is a GUID partition table (GPT) you must also repair the partition table with ***gdisk*** (unless the target drive has exactly the same size).

In this case the drives have the same identities, and things might be damaged, if you reboot the system with both the source and target systems connected. So remove the source drive before trying to boot into the target drive.

4 - You can ***clone a partition (or partitions)***, and that way be able to clone parts of a system from a larger drive to a smaller drive, but it is more ***complicated***. In this case you must also make sure that there will be a bootloader and that it will work in the new computer.

---

### Post by Autodave on 2016-07-18
I repair computers for a hobby. And because of that, I often get older machines that for one reason or another are not worth repairing due to cost. So, I end up with a lot of pieces left over after scrapping them and keeping those parts that still work and assembling them to make a workable machine.  Sometimes, I suspect a failed HD as the culprit.  I have 2 HDs: one SATA and one PATA: each with Ubuntu 32 bit installed. No proprietary drivers. I can take them and put them in any machine (at least I have not run into one yet that won't work) and power them up. Boot time may take an extra 30+ seconds, but they will boot and run normally.

---

