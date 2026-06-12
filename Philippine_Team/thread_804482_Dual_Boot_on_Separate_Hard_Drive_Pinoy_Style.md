---
title: "Dual Boot on Separate Hard Drive Pinoy Style"
date: 2008-05-23
forum: Philippine Team
---

### Post by jmazaredo on 2008-05-23
Dual Booting Linux and Windows on different hard drive assuming you have installed linux and windows not touching each other upon installation.

```
Tagalog : Dalawang gumaganang sistema sa mag kaibang matigas na disk. mag kaibang instalasyon ang naganap. nag install muna nang linux tapos tinangal ang matigas na disk tapos naglagay nang panibagong matigas na disk at nag install nang windows
```
```

Magkaibang instalasyon. Gagawa tayo nang menu para pag pilian nalamang sa tuwing mag bubukas nang komputer!
```

1st Hard Drive - Ubuntu Linux 8.04 Hardy
2nd Hard Drive - Windows XP Pro

Primary Master is Linux
Primary Slave is Windows

We set Linux as the OS to Boot why? Because I want it.

Edit menu.list in /boot/grub

====================================================

> title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=1653c057-1c9d-4fac-a46e-fe9fa76e4b7b ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=1653c057-1c9d-4fac-a46e-fe9fa76e4b7b ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

title        Windows XP Pang Games 
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

====================================================
edit /grub/device.map


> (hd0)    /dev/hda
(hd1)    /dev/hdb
(hd2)   /dev/hdc


Enjoy!

---

### Post by marckie on 2008-05-23
Go Pare go...
Galing ng Pinoy! ^_^
:guitar:
rockenroll!

---

### Post by Samhain13 on 2008-05-23
Nung una ako sa Ubuntu (Edgy) ang ginawa ko, ni-install ko nga siya sa extra kong drive. Yung XP ko, untouched. Gumana naman.

---

### Post by Nessa on 2008-05-23
Sa aking walang grub-grub. F11 lang during bios hehe. Tamad kasi. Pano ba mag-edit ng Grub? Slave ang Linux drive ko. Primary ang XP. Merong may alam kung pano i-manipulate yung boot list ng windows para magtanong siya kung gusto ba sa siya or isang Gibbon?

---

### Post by nan0x01 on 2008-05-25
dati ang ginawa ko:
install windows first then ubuntu, then see the magic happens in front of you

---

### Post by wersdaluv on 2008-05-28
> **Nessa said:**
> Sa aking walang grub-grub. F11 lang during bios hehe. Tamad kasi. Pano ba mag-edit ng Grub? Slave ang Linux drive ko. Primary ang XP. Merong may alam kung pano i-manipulate yung boot list ng windows para magtanong siya kung gusto ba sa siya or isang Gibbon?

Try mo, pre [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by jmazaredo on 2008-05-28
> **Nessa said:**
> Sa aking walang grub-grub. F11 lang during bios hehe. Tamad kasi. Pano ba mag-edit ng Grub? Slave ang Linux drive ko. Primary ang XP. Merong may alam kung pano i-manipulate yung boot list ng windows para magtanong siya kung gusto ba sa siya or isang Gibbon?

Pag windows ang gusto mo mag simulang boot yung boot.ini sa c:\ drive

eto yung typical boot.ini nang standalone na windows

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

i think.. you just add it in here somewhere... i-google mo baby!

---

