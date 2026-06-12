---
title: "Grub bootloader not showing after windows update"
date: 2017-12-04
forum: New to Ubuntu
---

### Post by sheanan on 2017-12-04
i am new to ubuntu I am using windows+ubuntu dual boot. recently i updated my windows but after that boot loader showing rescue grub load(something).

I booted from ubuntu live usb (try ubuntu) and used these cmds for boot repair
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update sudo apt-get install -y boot-repair && boot-repair
and then recommended repair.
it show successful and this url 

[https://paste.ubuntu.com/26110694/](https://paste.ubuntu.com/26110694/)

now windows loads automatically 
and after this now it does no showed boot menu i uncheck fast boot in windows.and run all these command again.
output after=cmds-
[https://paste.ubuntu.com/26111096/](https://paste.ubuntu.com/26111096/)

Still the problem persist and now windows is loaded automatically without showing boot menu.Please Help me step by step as i am new to ubuntu. Thank you in advance.

---

### Post by Impavidus on 2017-12-04
When performing the update, your Windows has accidentally deleted your Ubuntu partition. It's a bug in Windows. Your data should still be there in the unallocated space in the first part of the extended partition (/dev/sda4), starting shortly after sector 206,393,342 and ending shortly before sector 1,936,953,344. You can probably recover your data. Read [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery), see under Lost Partition.

---

