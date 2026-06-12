---
title: "Samba completely locks Oneiric up"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by markyb73 on 2011-09-02
Hi,

Have been playing around with Oneiric beta and thought i would try my adding my samba shares from a server i run with Lucid on it.

I have 3 directories on Oneiric /media/music /media/photos and /media/filestore

I only use the smbclient package to mount these dirs on boot to my Lucid server using entries in /etc/fstab

On Natty my entries looked like this: usernames and password masked :)

#Music
//192.168.1.200/music /media/music   smbfs  auto,username=xxx,password=xxx,uid=1000,umask=000,user   0 0

#Photos
//192.168.1.200/photos /media/photos   smbfs  auto,username=xxx,password=xxx,uid=1000,umask=000,user   0 0

#Filestore
//192.168.1.200/filestore /media/filestore   smbfs  auto,username=xxx,password=xxx,uid=1000,umask=000,user   0 0

With Oneiric as i understand it instead of using smbfs i need to use cifs now so i just replaced that in my lines on fstab.

If i try and then mount those "sudo mount -a" the whole machine locks up and the system also hangs on a reboot. When i try and reboot and look at the errors it seems the system is throwing out all sorts of kernel errors....i think.

I also dabble with arch and the above works fine on there.

Had anyone else had a problem with this?

Thanks :)

---

### Post by markyb73 on 2011-09-04
any samba experts? maybe i have something wrong :confused:

---

### Post by cariboo on 2011-09-04
Can you mount the shares via nautilus?

---

### Post by markyb73 on 2011-09-04
i can browse to my shares with nautilus fine. But i like to have them permanently mounted withing folders. Maybe i have my syntax wrong in /etc/fstab. But that is exactly how i have it working in natty.

Any ideas? :confused:

Thanks.

---

### Post by cariboo on 2011-09-04
There is another Samba thread [here]("http://ubuntuforums.org/showthread.php?t=1784437&highlight=samba"), there may be a solution to your problem in the thread.

---

### Post by effenberg0x0 on 2011-09-05
I have just installed Samba in two PCs with Oneiric Beta a couple hours ago. What I did was:

**On the Server:** sudo apt-get install samba

**On the Client:** sudo apt-get install samba smbfs

My client is auto-mounting the Server Samba share with this line in /etc/fstab:
```

#//Server_IP/Server_Share /existing/mount_point cifs credentials=/home/myself/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777,auto 0 0
//192.168.1.3/al /media/home-office cifs credentials=/home/al/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777,auto 0 0

```

It is working normally for me.

Regards,
Effenberg

**EDIT:** I just remembered I also had ufw running on the server, and so I had to open Samba ports to be able to connect to it.
```

sudo ufw enable
sudo ufw allow from 192.168.1.0/24 to any port 137
sudo ufw allow from 192.168.1.0/24 to any port 138
sudo ufw allow from 192.168.1.0/24 to any port 139
sudo ufw allow from 192.168.1.0/24 to any port 445
sudo service smbd restart

```

---

### Post by markyb73 on 2011-09-05
your syntax worked perfectly....thanks :D

---

