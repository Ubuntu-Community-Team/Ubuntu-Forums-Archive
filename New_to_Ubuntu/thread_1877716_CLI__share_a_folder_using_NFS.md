---
title: "CLI : share a folder using NFS?"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by honeybear on 2011-11-08
Hello,

I would like to use the commmand line to configure /etc/export to share a given folder : 

Server 192.134.28.100: /mnt/nfsshare to /mnt/nfsshare on any Ubuntu boxes over the intranet 192.134.28.* (without with root protection for commands on any pc such as : su - ; chmod 777 /mnt/nfsshare)

Which export line would you advice me? For stability and working? 

Thank you

---

### Post by Jose Catre-Vandis on 2011-11-08
**NFS Howto**

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by honeybear on 2011-11-08
> **Jose Catre-Vandis said:**
> **NFS Howto**

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

I know it already. but your advice based on your own use/config/xp?

there async is certainly not reliable

---

### Post by Jose Catre-Vandis on 2011-11-09
Don't try and use nfs shares with Windows - it can be done but its complex and unreliable - use samba for Windows.

I use nfs to share to my linux clients - workstations and media centre. Solid as a rock.

---

### Post by honeybear on 2011-11-09
> **Jose Catre-Vandis said:**
> Don't try and use nfs shares with Windows - it can be done but its complex and unreliable - use samba for Windows.

I use nfs to share to my linux clients - workstations and media centre. Solid as a rock.

I dont really understand the meaning of your post? :confused::confused:

- I did not mentioned any OS'ses in my post as far as I know ... ?   

> 
Hello,

I would like to use the commmand line to configure /etc/export to share a given folder :

Server 192.134.28.100: /mnt/nfsshare to /mnt/nfsshare on any Ubuntu boxes over the intranet 192.134.28.* (without with root protection for commands on any pc such as : su - ; chmod 777 /mnt/nfsshare)

Which export line would you advice me? For stability and working?

Thank you

PC's are solely *nix, to make you more comfortable with this subject.


- besides, you did not reply the first post either, since it is intended to have an advice based on existing configurations of user / ubuntu forum users.

---

### Post by Jose Catre-Vandis on 2011-11-10
OK

xp (in your post) = experience and not Windows XP - got that.

Did you follow the tutorial?

Have you got nfs shares working? If so what did you put in your  /etc/exports and what did you put in your client?

Lets assume you have portmap and nfs-common installed on the clients and nfs-kernel-server installed on the server

What problems are you experiencing that I am not (having used the info from the tut for the last three years)?

Do you want to share on the fly or all the time?

Do you want to make the share available on the fly from the server or from the client?

Do you want your clients to connect automatically when an nfs share is available?

If you are clear about what you want to achieve I can help you reach your goal :)

---

### Post by honeybear on 2011-11-14
Thank you. 


You, user passing by here this thread, could you post please the file content of a working NFS share client/server? what would give please on your working configuration: 



_**On the NFS server side:**_

```
cat /etc/fstab
```
??

```
cat /etc/exports
```
??



_**On the NFS client side:**_

```
cat /etc/fstab
```
??



Thank you. I hope that someone can reply.

---

### Post by Miljet on 2011-11-14
Here is a link to another how-to for using NFS. It doesn't get any more simple than this.

[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

---

### Post by honeybear on 2011-11-15
> **Miljet said:**
> Here is a link to another how-to for using NFS. It doesn't get any more simple than this.

[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

so visibly no one want to post a secret configuration ...

---

### Post by Jose Catre-Vandis on 2011-11-15
Give a man a fish..........

Work your way through the two howtos posted you'll get your answers. Just seeing other peoples config files won't help if you are not set up to serve or receive nfs shares in the first place.

---

### Post by oldfred on 2011-11-15
I use my desktop most of the time, but have laptop configured almost the same, so I use NFS to copy the data to my laptop when we travel & copy back when we return. I think found when I install a new system some settings were missing so I added those to a script for a new install.

Once I figured out how to do it, created scripts. I have one for my new install, one to mount the nfs shares when I connect my laptop or desktop (slight differences) and an rsync to copy data.

I only share two folders that are exactly the same in both systems, to try to know which is which I append LT or DT to mount:

From my new install script:
```
#NFS setup
fname_exp=/etc/exports
nfs1="/mnt/data 192.168.1.0/24(rw,no_root_squash,async)"
nfs2="/mnt/shared    192.168.1.0/24(rw,no_root_squash,async)"
echo $nfs1 >> $fname_exp
echo $nfs2 >> $fname_exp

```
And my new system install script includes this:
```
# For NFS /etc/exports already edited
apt-get install nfs-kernel-server nfs-common portmap
#
dpkg-reconfigure portmap
exportfs -a
service portmap restart


```
To mount, my desktop has a fixed IP - .20, but I have to adjust for laptop as it may not:

```
#!/bin/bash

sudo mkdir /mnt/data_DT
sudo mkdir /mnt/shared_DT
sudo mount 192.168.1.20:/mnt/data /mnt/data_DT
sudo mount 192.168.1.20:/mnt/shared /mnt/shared_DT

```
then I sync data from one to the other. I have two versions one with LT and the other DT.

```
#!/bin/bash
# run Mount_NFS.sh first
rsync -aruvP /mnt/data_DT/Documents /mnt/data
rsync -aruvP /mnt/data_DT/Projects /mnt/data
rsync -aruvP /mnt/data_DT/PDF /mnt/data
rsync -aruvP /mnt/data_DT/kmymoney /mnt/data
#
rsync -aruvP /mnt/shared_DT/OfficeFiles /mnt/shared
rsync -aruvP /mnt/shared_DT/mozilla /mnt/shared
rsync -aruvP /mnt/shared_DT/Photos/All2011 /mnt/shared/Photos

```

---

### Post by honeybear on 2011-11-15
> **oldfred said:**
> I use my desktop most of the time, but have laptop configured almost the same, so I use NFS to copy the data to my laptop when we travel & copy back when we return. I think found when I install a new system some settings were missing so I added those to a script for a new install.



Thank you very much !! You cannot believe how much it helps. 

So, thus, it means that my configuration is correct. I will certainly survey the bug report. 

The quality of your reply is adapted to the section "Absolute Beginner Talk ". 

Besides I have about 10 y. experience with Linux as well as Debian NFS sharing (which one specific user here, - without mentioning any name, in this thread had no idea). 


I would like to thank you, oldfred, for the quality of your answer.

---

### Post by oldfred on 2011-11-15
Glad you have it worked out. 

Sometimes it is a combination of standard procedures as in the guides and a more specific example to fully understand things.

---

### Post by Jose Catre-Vandis on 2011-11-16
> **honeybear said:**
> Besides I have about 10 y. experience with Linux as well as Debian NFS sharing (which one specific user here, - without mentioning any name, in this thread had no idea). 


I am mortally offended :frown:

But you have benefited from the wonderfulness of this forum that there are greater people than I who can interpret obtuse questions with little back up information and come up with a solution, even though it did include async which was previous frowned upon. You failed to provide any info on where you were in the process so how the hell was I supposed to know you had "10 years experience in linux and Debian NFS sharing" (so still a newb then :)) and you wanted scripts to run shares???

Rant over - end of..

---

