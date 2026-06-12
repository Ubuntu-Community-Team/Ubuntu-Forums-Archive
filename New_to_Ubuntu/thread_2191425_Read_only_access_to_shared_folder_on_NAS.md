---
title: "Read only access to shared folder on NAS"
date: 2013-12-02
forum: New to Ubuntu
---

### Post by esgrim on 2013-12-02
I've got a Synology NAS set up with a shared folder called Video. This folder has been mounted on my Ubuntu desktop and I can see this folder just fine from my desktop. I've got various programs that have been set up to automatically transfer files from my Ubuntu desktop Desktop to the shared folder on the NAS. However it appears the programs do not have write access. When the file transfer fails I naturally get an error message saying Access denied, could not write to shared folder/filename. The file then remains on the Desktop. If I either with a GUI interface or terminal manually copy the file to the mounted shared folder all works fine.

I've edited the fstab (see below) to include the mount point so that it mounts automatically when the machine boots. 

//xxx.xxx.x.xxx/video /home/linux/WD cifs guest,_netdev,noperm 0 0

The local folder (/home/linux/WD) where I have pointed the mount point was created with a local user. However when the the shared folder is mounted permissions change for the mount point to root.
When mounted
drwxrwxrwx 11 root  root        0 Dec  2 21:43 WD/

When unmounted
drwxrwxrwx 11 linux linux        0 Dec  2 21:43 WD/

This used to work no problems before but after I upgraded to an newer than v10.x there seems to have arisen a permissions problem. Current Ubuntu version is 13.10

Any help on this is much appreciated.

---

