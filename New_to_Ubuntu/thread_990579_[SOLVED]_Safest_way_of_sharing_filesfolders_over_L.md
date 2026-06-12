---
title: "[SOLVED] Safest way of sharing files/folders over Lan"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-11-22
I would like to know what is the safest way to share files and folders over the local network between 2 Ubuntu boxes, while completely blocking access from outside?

I'm currently using samba, but I'm a little bit paranoid with those "smbd" and "nmbd" listening services.

Is there a way to secure samba shares other than blocking iptables inbound connections on ports 137-139 and 445 from IPs outside the local network range, like configuring samba to accept connections from local IPs only?

---

### Post by fr.theo on 2008-11-22
you can use the GSambad which is a GUI interface for samba to configure and control security settings for samba, you can install it through your Synaptic package manager or goto Applications >> add remove programs.

---

### Post by hankinator on 2008-11-22
Id use and install XAMPP, or some form of a ftp server program. that way you can just do that, cause you can configure the ports and such, and through lan it should be fine.

---

### Post by iponeverything on 2008-11-22
sshfs

just go to Places -> "Connect to Server" and choose ssh.

---

### Post by lswb on 2008-11-22
Install ssh server and optionally sshfs on both boxes, it would be difficult to imagine a simpler method for connecting linux (or any unix-like) systems. Then you can connect through Main Menu/Places/Connect to Server menu as iponeverything suggests.

With sshfs installed, you can mount the remote system to a mountpoint similar to how a partition is mounted and then access the remote system with any file browser or command line tools you would use to access local files. 

If your local net is behind a router you can just configure a firewall to only allow incoming ssh access to addresses on your local net, usually in the 192.168.x.x range.

---

### Post by doas777 on 2008-11-22
> **lovinglinux said:**
> I would like to know what is the safest way to share files and folders over the local network between 2 Ubuntu boxes, while completely blocking access from outside?

I'm currently using samba, but I'm a little bit paranoid with those "smbd" and "nmbd" listening services.

Is there a way to secure samba shares other than blocking iptables inbound connections on ports 137-139 and 445 from IPs outside the local network range, like configuring samba to accept connections from local IPs only?


I assume you don't have a fire-walling router? the traditional answer is to put the two PCs on a separate subnet and firewall at the gateway, blocking NBT outbound and inbound. 

ssh and whatnot add layers of security (tunneled encryption and whatnot) and samba should be configured for encrypted authentication in any respect, but I need a router to prevent external access to a given resource. I won't expose a ssh server to the Internet for instance.

---

### Post by lovinglinux on 2008-11-23
> **fr.theo said:**
> you can use the GSambad which is a GUI interface for samba to configure and control security settings for samba, you can install it through your Synaptic package manager or goto Applications >> add remove programs.

Thank you very much. I was missing a lot of configuration options.

> **hankinator said:**
> Id use and install XAMPP, or some form of a ftp server program. that way you can just do that, cause you can configure the ports and such, and through lan it should be fine.

Thanks, but I think installing Apache, MySQL and PHP is a little bit of overkill just for file transfers. 

> **iponeverything said:**
> sshfs

just go to Places -> "Connect to Server" and choose ssh.

> **lswb said:**
> Install ssh server and optionally sshfs on both boxes, it would be difficult to imagine a simpler method for connecting linux (or any unix-like) systems. Then you can connect through Main Menu/Places/Connect to Server menu as iponeverything suggests.

With sshfs installed, you can mount the remote system to a mountpoint similar to how a partition is mounted and then access the remote system with any file browser or command line tools you would use to access local files. 

If your local net is behind a router you can just configure a firewall to only allow incoming ssh access to addresses on your local net, usually in the 192.168.x.x range.

Thank you. Sounds interesting. I read several post titles about ssh, but I thought it was more interesting when you need to access the remote machine from the Internet. I will give it a try and compare with samba.

> **doas777 said:**
> I assume you don't have a fire-walling router? the traditional answer is to put the two PCs on a separate subnet and firewall at the gateway, blocking NBT outbound and inbound. 

ssh and whatnot add layers of security (tunneled encryption and whatnot) and samba should be configured for encrypted authentication in any respect, but I need a router to prevent external access to a given resource. I won't expose a ssh server to the Internet for instance.

Actually, I have a fire-walled router, plus iptables rules blocking almost everything and moblock blocking IP lists. I'm just a little bit paranoid, specially when opening ports for torrents and other stuff.

---

