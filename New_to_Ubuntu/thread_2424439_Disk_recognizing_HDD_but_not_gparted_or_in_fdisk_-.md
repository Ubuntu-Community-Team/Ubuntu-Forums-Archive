---
title: "Disk recognizing HDD but not gparted or in fdisk -lu (helping copying files)"
date: 2019-08-08
forum: New to Ubuntu
---

### Post by hyder123 on 2019-08-08
So im trying to copy eveything from an HDD plugged into my PC through USB JMicron device to a new SDD with twice the space (HDD should be 128g and SSD 250). When i look in "disk" i see JMicron device called /dev/sda but it does not show the size or content and if i look for it in fdisk -lu, gparted, or df -h it doesnt show up. I tried to use the dd command to copy everything since i knew the device name but when doing so it says 0 bytes were copied. Any idea why no information is showing up for the HDD and why its not copying over?

(I dont know anything about linux so a really dumbed down explaination/aid would be appreciated ive gotten as far as i could through youtube and forums)

---

### Post by Dennis N on 2019-08-08
You have Linux installed on the SSD? And you are copying your data files from the HDD to your new install? Why not just use two file manager windows to do the copying. One open to the HDD and one to the SSD. gparted or fdisk are not for copying files. They are disk management utilities.

---

### Post by oldfred on 2019-08-08
I have an USB to SATA adapter. It works great for my SSD, but only has USB power and will not bring HDD up. You need an adapter with separate power supply.

Often better to just do a new install and then copy your backups to new install. Good way to confirm your backups are complete and you still have old drive to go back to if your backup is not complete. Drives will eventually fail, so backups are required.

---

