---
title: "I just made dual boot with ubuntu and win10 and i cant get win10 to boot"
date: 2021-03-02
forum: New to Ubuntu
---

### Post by stevethenoob on 2021-03-02
To be more specific i was able to boot win10 with grub disk, but every time i try to load from grub it just goes on a black screen and goes back to grub, leaving me with ubuntu the only option. I should also mention that i created a new partition to install ubuntu on. This is my win 10 boot sequence that i got from grub customizer:

insmod part_msdos
insmod ntfs
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  FC282AD2282A8BA8
else
  search --no-floppy --fs-uuid --set=root FC282AD2282A8BA8
fi
parttool ${root} hidden-
drivemap -s (hd0) ${root}
chainloader +1

---

### Post by yancek on 2021-03-02
Was windows 10 preinstalled on the computer?  If it was, it was almost certainly installed in UEFI mode.  Did you installed Ubuntu in UEFI mode.  The entry for windows which you posted is a Legacy boot menuentry. For Grub to boot a UEFI of windows, it must be installed UEFI.  If you run the command below, you should see an entry for both windows and Ubuntu:

```
sudo efibootmgr
```    

Before installing Ubuntu, did you read the official documentation on dual booting Ubuntu with windows, link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

