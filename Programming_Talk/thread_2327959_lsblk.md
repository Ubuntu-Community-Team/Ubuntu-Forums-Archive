---
title: "lsblk"
date: 2016-06-16
forum: Programming Talk
---

### Post by MikeCyber on 2016-06-16
Hi
any idea on how to avoid lsblk showing usb devices? I only need the first hd. Simply lsblk /dev/sda is not good, as I don't know the device and it must work also on osx.
Thanks

---

### Post by Bucky Ball on 2016-06-16
> **MikeCyber said:**
> ... lsblk /dev/sda is not good, as I don't know the device ...

How do you mean you don't know the device? You mean you're not sure if it's sda or sd something else?

If this is the case, ironically, run lsblk and have a look, then try your other command again as that will work fine to identify the drive, once you know which one you want to know about.

For more detail, try 'sudo blkid'.

---

### Post by sudodus on 2016-06-16
Maybe you can use **/dev/disk/by-id** for example like this to find usb drives

```
ls -l /dev/disk/by-id | tr -s ' ' '\t' |cut -f9- | grep ^usb
usb-SanDisk_Cruzer_Blade_200429068118E7C2CFFD-0:0	->	../../sdd
usb-SanDisk_Cruzer_Blade_200429068118E7C2CFFD-0:0-part1	->	../../sdd1
usb-SanDisk_Cruzer_Blade_200429068118E7C2CFFD-0:0-part2	->	../../sdd2
```

and like this to find ata drives

```
ls -l /dev/disk/by-id | tr -s ' ' '\t' |cut -f9- | grep ^ata
ata-HL-DT-STDVD+-RW_GSA-H21L	->	../../sr0
ata-OCZ-AGILITY3_OCZ-LG1P09233GJ67M09	->	../../sdb
ata-OCZ-AGILITY3_OCZ-LG1P09233GJ67M09-part1	->	../../sdb1
ata-OCZ-AGILITY3_OCZ-LG1P09233GJ67M09-part2	->	../../sdb2
ata-OCZ-AGILITY3_OCZ-LG1P09233GJ67M09-part4	->	../../sdb4
ata-OCZ-AGILITY3_OCZ-LG1P09233GJ67M09-part5	->	../../sdb5
ata-SAMSUNG_HD322HJ_S17AJ90QB00683	->	../../sda
ata-SAMSUNG_HD322HJ_S17AJ90QB00683-part1	->	../../sda1
ata-SAMSUNG_HD322HJ_S17AJ90QB00683-part2	->	../../sda2
ata-SAMSUNG_HD322HJ_S17AJ90QB00683-part4	->	../../sda4
ata-SAMSUNG_HD322HJ_S17AJ90QB00683-part5	->	../../sda5
ata-SAMSUNG_HD322HJ_S17AJ90QB00683-part6	->	../../sda6
ata-SAMSUNG_HD322HJ_S17AJ90QB00683-part7	->	../../sda7
ata-SAMSUNG_HD322HJ_S17AJ90QB00683-part8	->	../../sda8
ata-WDC_WD1003FBYZ-010FB0_WD-WCAW36973968	->	../../sdc
ata-WDC_WD1003FBYZ-010FB0_WD-WCAW36973968-part1	->	../../sdc1
ata-WDC_WD1003FBYZ-010FB0_WD-WCAW36973968-part2	->	../../sdc2
ata-WDC_WD1003FBYZ-010FB0_WD-WCAW36973968-part5	->	../../sdc5
ata-WDC_WD1003FBYZ-010FB0_WD-WCAW36973968-part6	->	../../sdc6
ata-WDC_WD1003FBYZ-010FB0_WD-WCAW36973968-part7	->	../../sdc7
```

And when you know, you can run lsblk for those drives (maybe automatically in a script file).

---

### Post by MikeCyber on 2016-06-16
In my c++ app I currently do:
getMach.append(exec("lsblk -I 8"));//windows diskpart mac diskutil list

now this gets also usb which I don't want.
Thanks

---

### Post by sudodus on 2016-06-16
```
ls -l /dev/disk/by-id | tr -s ' ' '\t' |cut -f9- | grep ^ata
```

does *not* get usb pendrives. Try it.

***Edit:*** But if you have SATA drives connected via USB, it might find such drives.

---

