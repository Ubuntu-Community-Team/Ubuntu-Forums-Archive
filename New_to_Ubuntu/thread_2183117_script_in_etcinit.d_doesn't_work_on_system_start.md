---
title: "script in /etc/init.d/ doesn't work on system start"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by Marchello_Lippi on 2013-10-23
Hi all! 
My need is to run script on system start, but it doesn't work. I must run it manually: 

$ sudo bash /etc/init.d/mount_from_ip_110 

it works ok this way. 

What is wrong? Why it doesn't work on system start? 


#!/bin/sh
#
# 
#
# 
# 
#
# 
# 

#sudo mount -t cifs //192.168.0.110/WD_VIDEO /mnt/wd_video -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //192.168.0.110/WD_MP3 /mnt/wd_mp3/ -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //192.168.0.110/SD_DOWNLOADS /mnt/sd_downloads -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //192.168.0.110/WD_INCOMING /mnt/wd_incoming/ -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //192.168.0.110/WD_TORRENT /mnt/wd_torrent/ -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //192.168.0.110/WD_VIDEO /mnt/wd_video/ -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

---

### Post by sandyd on 2013-10-23
> **Marchello_Lippi said:**
> Hi all! 
My need is to run script on system start, but it doesn't work. I must run it manually: 

$ sudo bash /etc/init.d/mount_from_ip_110 

it works ok this way. 

What is wrong? Why it doesn't work on system start? 


#!/bin/sh
#
# 
#
# 
# 
#
# 
# 

#sudo mount -t cifs //192.168.0.110/WD_VIDEO /mnt/wd_video -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //192.168.0.110/WD_MP3 /mnt/wd_mp3/ -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //192.168.0.110/SD_DOWNLOADS /mnt/sd_downloads -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //192.168.0.110/WD_INCOMING /mnt/wd_incoming/ -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //192.168.0.110/WD_TORRENT /mnt/wd_torrent/ -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //192.168.0.110/WD_VIDEO /mnt/wd_video/ -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

If you want something to start from /etc/init.d, you must create an init script for it.

If you want to mount the directories above, there are easier ways of doing it than creating an init script
 try translating it into the following format, and putting it into /etc/fstab
```

//192.168.0.110/WD_MP3 /mnt/wd_mp3/  cifs  guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,sec=ntlm  0  0

```
To test, unmount the directory, (i.e. /mnt/wd_mp3/) and run
```

mount /mnt/wd_mp3
```

---

