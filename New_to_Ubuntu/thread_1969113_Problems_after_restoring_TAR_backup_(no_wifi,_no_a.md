---
title: "Problems after restoring TAR backup (no wifi, no audio, ...)"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by vkmaxx on 2012-04-29
I have made TAR backup of my 11.10 before updating to 12.04 with following command:
```

sudo tar -cvpjf /media/Data/Kopia/maxx_`date +%F`.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev --exclude=/home/maxx/qBT_dir --exclude=/home/maxx/.gvfs / 
```After unsuccessful update to 12.04 (nVidia 295.xx driver problem) I tried to restore TAR backup. I have booted from CD and:

```
cd /media/bed5839a-c560-44d0-b414-a5cddbfc2921/
sudo rm -r ./*
sudo tar -xvpf /media/Data/Kopia/maxx_2012-04-27.tar.bz2 -C /media/bed5839a-c560-44d0-b414-a5cddbfc2921/
sudo mkdir ./proc ./lost+found ./sys ./mnt ./media 
cd ./home
sudo rm -r ./*
```I have my /home folder on different partition that's why I have removed content of /home form backup (I have even tried to move the content to my /home partition) but no matter what I do I can't boot. I need to repair my grub settings with boot-repair procedure:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

And after that I can boot but some settings are lost (no WiFi connection, no audio card, I can't access my NTFS partition - I don't see them in home folder).
What's wrong, how can I do full recovery to Ubuntu from my backup.

---

