---
title: "Dolphin displaying to little free disk space"
date: 2020-08-28
forum: New to Ubuntu
---

### Post by totalynotanoob on 2020-08-28
Hi,

my SSD has about 100 GB free but Dolphin and df only show about 30. when I go into the trash folder it shows 75 GB. I had a full Drive after leaving siril running (it does stacking for astrophotography and needs alot of diskspace). when I deleted two Folders in Dolphin they didn't move to trash and the free space remained at 0 B but they should have been less than the missing 70 GB. I would guess they were about 10 to 20 GB.
when i went to see the properties of my disk it said used space:   132,1 TiB (145.290.737.414.939). so that is just ridiculus for a 1TB ssd.
I have attached three screenshots
[ATTACH=CONFIG]286826[/ATTACH][ATTACH=CONFIG]286827[/ATTACH][ATTACH=CONFIG]286828[/ATTACH]

I am pretty new to linux and only now the most basic commands (I only found out about df today).

I am running Kubuntu 20.04 on an Acer Aspire V 15 with a Samsung 970EVO (I think. something similar by samsung evo at least).



Update:
I have since found the "not really deleted" folders but don't know if it is save to delete them.
the other situation with the contradictory used and free space ramains.

---

### Post by mastablasta on 2020-08-29
use
```
df -h
```

for human readable format / output.

i haven't noticed any issue in dolphin on 18.04 or 20.04 regarding disk space.

---

### Post by totalynotanoob on 2020-08-29
I have done that also but I don't see how it would help me. it only makes everything a little nicer to read. I am still missing about 46GB with the df command.
here is the output:

```

Dateisystem    Größe Benutzt Verf. Verw% Eingehängt auf
udev            3,8G       0  3,8G    0% /dev
tmpfs           782M    1,8M  781M    1% /run
/dev/sda2       916G    648G  222G   75% /
tmpfs           3,9G     61M  3,8G    2% /dev/shm
tmpfs           5,0M    4,0K  5,0M    1% /run/lock
tmpfs           3,9G       0  3,9G    0% /sys/fs/cgroup
/dev/loop1       97M     97M     0  100% /snap/core/9804
/dev/loop2       55M     55M     0  100% /snap/core18/1880
/dev/loop3      141M    141M     0  100% /snap/gnome-3-26-1604/100
/dev/loop4       56M     56M     0  100% /snap/core18/1885
/dev/loop6       97M     97M     0  100% /snap/keepassxc/978
/dev/loop5      162M    162M     0  100% /snap/gnome-3-28-1804/128
/dev/loop7       44M     44M     0  100% /snap/snap-store/415
/dev/loop0       97M     97M     0  100% /snap/core/9665
/dev/loop8       63M     63M     0  100% /snap/gtk-common-themes/1506
/dev/loop9      129M    129M     0  100% /snap/sweethome3d-homedesign/9
/dev/loop10      97M     97M     0  100% /snap/keepassxc/1006
/dev/loop11      30M     30M     0  100% /snap/snapd/8790
/dev/loop12      30M     30M     0  100% /snap/snapd/8542
/dev/loop13      92M     92M     0  100% /snap/youtube-dl/2846
/dev/sda1       511M     11M  501M    3% /boot/efi
tmpfs           782M     16K  782M    1% /run/user/1000

```

I am assuming you can guess the german words. If you need a translation here it is:
Filesystem - Size - Used - Available - Used in % - Mounted to

I have also found someone with similar issues on askubuntu: [https://askubuntu.com/questions/1271079/diskspace-0-bytes-free](https://askubuntu.com/questions/1271079/diskspace-0-bytes-free)

---

### Post by Impavidus on 2020-08-29
5% of the filesystem, which is indeed 46GB, is reserved for the root user to use in emergencies and not listed as available, so it adds up. You can change that percentage, but it's best to keep some space free to prevent fragmentation (HDDs) or allow the wear-levelling to do its job (SSDs), so I wouldn't bother making that 5% available.

---

### Post by totalynotanoob on 2020-08-29
Oh ok. Thank you, I did not know about that.

Now my only remaining problems are:
-Dolphin shows 91.5 Gib free in the trash folder but 221.7 GiB everywhere else.
-Dolphin claims in the properties of my SSD that 128.6 TiB are used
-all the different applications and tools I used to look at my files and used space etc show different things.

I don't really mind any of this if there are no problems, they could cause.
And I understand that different apps estimate diskspace differently.

So unless anyone knows of a danger from just leaving it be and being mildly annoyed. I'll just leave the issue and might do a fresh install when I get some time.

Thanks for all your kind replies.

I consider this pretty much a closed issue (unless of course someone suspects there being bigger trouble ahead).

---

### Post by Impavidus on 2020-08-30
It seems strange that dolphin gives a different free space in the trash directory than anywhere else, because free space is a property of the filesystem and the trash directory is on the same filesystem as everything else. Unless there's a separate limit for the trash directory, managed by dolphin that other tools know nothing about. I don't use dolphin.

Maybe dolphin is somehow confused about the free space on your SSD. It is known to happen to some tools using some more advanced filesystems, but the default ext4 should work fine.

Whenever fancy GUI tools and simple command line tools tell you different things about your system, believe the command line tools.

---

### Post by Holger_Gehrke on 2020-08-30
Could it be that siril uses [sparse files]("https://en.wikipedia.org/wiki/Sparse_file") ? AFAIK ext4 supports those. A sparse file can easily be a lot bigger than the filesystem on which it resides because most blocks in such a file are empty and don't actually use any space on the disk ...
If Dolphin just sums up the file sizes instead of asking for the number of used blocks per file it could easily end up with with a number a lot bigger than the capacity of the drive.

Holger

---

### Post by mastablasta on 2020-08-31
> **totalynotanoob said:**
> 
-Dolphin claims in the properties of my SSD that 128.6 TiB are used


you have local language set to German, right? 

i have it set to GB. GB and US use point to denominate decimals, while we use commas. So perhaps something got mixed up here. though i would find it strange that no one noticed or reported, since i know many people in Germany use KDE and in fact a couple of companies that actively support KDE are from Germany.

---

### Post by SeijiSensei on 2020-08-31
What if you empty the trash?

---

