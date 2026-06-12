---
title: "Accessing a back up server"
date: 2009-01-21
forum: Philippine Team
---

### Post by randytan on 2009-01-21
Hi All!

We are currently using a Synology back up server in the office to store our big file and to prevent our notebook hard drives from getting full.

When I was still using xp, we would access it by entering it's IP address either in the "run" area or by making a shortcut to it.

Now that I'm using Ubuntu, how do I go about connecting to this server? Can I do it wirelessly or must I be connected via Ethernet?

Do I go through Places > Connect to Server? Or Places > Network?

Thanks for all your help, it's all very much appreciated!

Best regards!

---

### Post by loell on 2009-01-21
try accessing it in nautilus..

```
smb://<name>/share
```
 you can either supply the network name or the IP address.

---

### Post by kiminaiseah on 2009-01-21
NAS(Network Attach Stored) po ba yan "Synology"

make sure magkaparehas ang workgroup name nung mga clients or workstation sa nka assign sa NAS, kasi ang windows may automatic search ng neighbor computer so miski di moto i set sa windows nakikita sa automatically sa linux u need specify a workgroup,

firstly u need samba-common

sudo apt-get install samba-common -y

dpkg-reconfigure samba-common 

system ask u some credentials about network setting...

might help....

---

### Post by randytan on 2009-01-23
Hi Guys!

loell:
Um, where do I find Nautilus?

kiminaiseah:
Yes, Synology is an NAS. I already installed all the samba related stuff via synaptic manager. Am I still missing something?

Will it be better if I just re-download everything from the codes you gave?

Once I have, how do I proceed on accessing Synology?

Thanks.

Hope to hear from you guys again soon.

Best regards!

---

### Post by loell on 2009-01-23
> **randytan said:**
> 
Um, where do I find Nautilus?


its the default File browser that comes with ubuntu, uniformly one can access it in Places menu --> Home Folder.

---

### Post by kiminaiseah on 2009-01-23
@randytan

actually i done something without using GUI's it makes me lazy.. 

at terminal 
1. sudo apt-get install smbfs
2. answer question what system ask about the workgroup name
3. sudo mkdir -p /path/folder
4. sudo mount -t smbfs -o username=null,password=null //ipaddress/shared-folder-or-disk /path/folder
5. sudo df -h (verify it mounted perfectly)

to add automount every bootup edit /etc/fstab
1. sudo nano /etc/fstab
2. add this into a line 
//ipaddress/shared-folder-or-disk /path/folder smbfs username=null,password=null 0 0
3. reboot
4. df -h (to verify)

to unmount
umount /path/folder

---

### Post by randytan on 2009-01-24
> **loell said:**
> its the default File browser that comes with ubuntu, uniformly one can access it in Places menu --> Home Folder.

I tried looking for this but still cannot connect for some reason.

We tried pinging the Synology and it replies, I just can't get to it ](*,)

---

### Post by randytan on 2009-02-26
Hi Guys!

We need to have access to two servers in the office, one is the aforementioned Syology and the other is a box running windows 2000 Server with SP4.

Both are NTFS.

When I click on Places > Network, all I see are the Macs and the workgroup. when I click on the workgroup, nothing comes out.

How do I access them?

loell said I should run the smb://IP/share in Nautilus, but I can't find it (Nautilus).

Can someone give me an idiot's guide on how to access them?

I kinda screwed up the installation in my office system and accidentally deleted some stuff. I'm planning a reinstall to get everything back to default. Hopefully, I can once again see the other stuff and that may yield the elusive apps.

Your support, input, and assistance needed.

If I can get this to work with me, everyone in the office using windows will be changed over to Ubuntu.

Thanks.

Hope to hear from y'all again soon.

Maraming salamat po! :guitar:

---

### Post by randytan on 2009-03-04
Hi All!

After I reinstalled Ubuntu into my office notebook, all seems well and faster.

Also, I can now see everyone including the back up servers by just clicking on network!

YAY!

Thanks for your assistance and patience. :D

---

