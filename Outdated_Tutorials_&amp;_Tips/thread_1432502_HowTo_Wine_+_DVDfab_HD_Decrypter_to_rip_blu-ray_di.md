---
title: "HowTo: Wine + DVDfab HD Decrypter to rip blu-ray disks"
date: 2010-03-17
forum: Outdated Tutorials &amp; Tips
---

### Post by ultima on 2010-03-17
Quick Instructions

Install wine
Install DVDfab and choose HD Decrypter Free Edition.

DVDfab should automatically load your disk. 

If not then Copy the disk to your harddrive and open the iso in DVDfab

example: ```
dd if=/dev/sr0 of=~/blu-ray_movie.iso
```

Select Region Code.

Select Blu-ray to Blu-ray and Full disk.

Choose "target" by selecting the folder icon to rip to a folder or the image icon to create an iso image.

Add Volume Label if needed.

Click start.

---------------------------

Once Finished.

Navigate to folder

example: ```
cd ~/DVDFab/FullDisc/Name_of_Movie/BDMV/STREAM
```

```
ls -l
```

The largest file will be the movie.

play with mplayer or vlc.

If you created an iso image, mount with.

example: ```
sudo mount -o loop -t udf /path/to/image.iso ~/folder_to_mount_image
```

To unmount iso

example: ```
sudo umount -t udf /path/to/image.iso ~/folder_to_mount_image
```

Wine DVDfab page
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2377](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2377)

---

