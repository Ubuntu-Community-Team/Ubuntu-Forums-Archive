---
title: "New to Ubuntu - Samba &amp; Java"
date: 2016-07-06
forum: New to Ubuntu
---

### Post by inunex on 2016-07-06
Hi,

I have been running Ubuntu (16.04) for a few weeks now and so far; it seems to be a good replacement for personal use and work use on occasion. However, I have a few questions:

1) What is the best way to access a samba share (NAS) or should I set my NAS to have an nfs share?
I have tried to use the "connect to server" option through the file browser and specify the server IP like follows; smb://<ip address here> but this does not seem to work or return any sort of feedback. I understand that there are a few ways I can mount a share via the terminal but I have seen a lot of different information but all on older releases.

2) I have installed NetExtender & Java but how can I ensure that Java is kept up to date as well as NetExtender?
Will I get these updates automatically?

Hope this is the right place to ask these questions - if not please let me know!

---

### Post by nerdtron on 2016-07-06
Hello inunex,
Welcome to the forums.

1. If all your machines at home at running Linux, then setting the network share as NFS is a good option (and fast) option. But I'd suggest you stay with Samba since it is compatible with Windows computers and most Android explorer application can only access samba shares. 
You can mount a samba share from the command line using the following command:
```
 sudo mount.cifs //ip.address.x.x/ShareName /mnt/sambaFolder -o user=Administrator,pass=password 
```
Or via the Nautilus File Explorer smb://<ip.address>  just make sure your SMB server is accessible on the network and that the proper credentials are set.

2. I can't advise on NetExtender (VPN?). Which java package did you installed? Did you installed the one from the official repository from the Software Center? If yes, then you just need to run systems updates when they are available. The update manager will include systems updates for the all packages installed.

---

### Post by mastablasta on 2016-07-08
> **nerdtron said:**
> just make sure your SMB server is accessible on the network and that the proper credentials are set.

often overlooked in setup is that SAMBA shares have to be in same "workgroup". e.g. if windows is in workgroup called *workgroup*, then SAMBA share has to be in same group. then you should be able to see the server.

---

### Post by inunex on 2016-07-09
Thank for the help Nerdtron & mastablasta!

I have connected using Nautilus to the samba share and this is working great; unfortunately it was an oversight on my part by not specifying the share name after the IP address... I assumed for some reason that this would list the shares on the server.

NetExtender is an SSL VPN client for Dell Sonicwall firewalls. I installed the Oracle Java package from their website; as I understand OpenJDK does not work with this. However, if there isn't a repository for this - would it need to be manually updated?

---

### Post by mastablasta on 2016-07-09
> **inunex said:**
> 
NetExtender is an SSL VPN client for Dell Sonicwall firewalls. I installed the Oracle Java package from their website; as I understand OpenJDK does not work with this. However, if there isn't a repository for this - would it need to be manually updated?

which Java version you need? yes you likely need to manually update it. webupd8 has personal package archive ("personal repository") for Java - se that and Java updates will be made together with other regular updates.

---

### Post by inunex on 2016-07-09
The JRE from Oracle; which I have installed but if there is a repository which I can use to keep this up to date that would be handy as eventually I'd need to manually update this.

---

### Post by mastablasta on 2016-07-11
> **inunex said:**
> The JRE from Oracle; which I have installed but if there is a repository which I can use to keep this up to date that would be handy as eventually I'd need to manually update this.

like i said webupd8 PPA: [SIZE=2]http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html
[/SIZE]

---

### Post by inunex on 2016-07-11
Thanks for your help!

---

