---
title: "[SOLVED] Home Network with Ubuntu Only?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by nakama85 on 2008-11-21
I have no need to connect any windows computers.

I just need to share files in between my wireless laptop and my wired desktop. 

Could someone tell me how this is done. Or at least point me in the direction of a how-to.

Thanks for any help:)

---

### Post by nothingspecial on 2008-11-21
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by nakama85 on 2008-11-21
> **nothingspecial said:**
> [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Thanks. I am looking at this now. I just have 1 Question. Is this degree needed. I mean is there an easier way to graphically share files. It sound like this setup is for remote access to another computer. I am hoping to just be able to drag and drop files in between computers. Thanks Again!

---

### Post by y@w on 2008-11-21
I think the section of the page you're looking for is this:

> Using GNOME

Click Places -> Connect to Server. Select SSH for Service Type, write the name or IP address of the computer you're connecting to in Server, the user you'd like to connect as in User Name, and a name for the connection if you wish.

Files can be copied by dragging and dropping between this window and other windows. 

Actually, on my Ubuntu system, I click on Places in the menu and it listed my other computer (with only SSH open) as a fileshare and let me connect to it via SSH. I could then move files back and forth graphically.

---

### Post by nakama85 on 2008-11-21
> **y@w said:**
> I think the section of the page you're looking for is this:



Actually, on my Ubuntu system, I click on Places in the menu and it listed my other computer (with only SSH open) as a fileshare and let me connect to it via SSH. I could then move files back and forth graphically.

When I try this I get this error msg. "Connection refused by server"

---

### Post by Zack McCool on 2008-11-21
While that degree is not needed, it will provide the best performance.

There are a variety of methods you can use to share files between your machines.  

NFS Share: You'll have to install nfs-client nfs-common and nfs-server, then set up the folder(s) you want to share in the /etc/exports file and mount the share on the other machine in the /etc/fstab file.

SAMBA Share: This is Windows file sharing, but it works fine in linux, too.  Install samba, samba-common and samba-client.  Again, configure the share in /etc/samba/samba.conf and mount it on the other machine in /etc/fstab.

SSHFS: Set up and configure SSH on each machine, then connect to the filesystem by setting up a mount in /etc/fstab.

With all 3 of these methods, once you set it up, the shares will always be there when you boot the machines, and you will always be able to access them through nautilus as a graphical interface.  There will be some config work with any of them, so feel free to make a choice and if you can't find the detailed info you need to set it up, ask for help.  For most people, I would recommend SSHFS.  It is no harder to set up than the other options, and it is 2-3x faster, in my experience.

If you run into a wall, drop me an e-mail or start a new thread here and you'll get all the help you need.

---

### Post by nakama85 on 2008-11-21
> **Zack McCool said:**
> While that degree is not needed, it will provide the best performance.

There are a variety of methods you can use to share files between your machines.  

NFS Share: You'll have to install nfs-client nfs-common and nfs-server, then set up the folder(s) you want to share in the /etc/exports file and mount the share on the other machine in the /etc/fstab file.

SAMBA Share: This is Windows file sharing, but it works fine in linux, too.  Install samba, samba-common and samba-client.  Again, configure the share in /etc/samba/samba.conf and mount it on the other machine in /etc/fstab.

SSHFS: Set up and configure SSH on each machine, then connect to the filesystem by setting up a mount in /etc/fstab.

With all 3 of these methods, once you set it up, the shares will always be there when you boot the machines, and you will always be able to access them through nautilus as a graphical interface.  There will be some config work with any of them, so feel free to make a choice and if you can't find the detailed info you need to set it up, ask for help.  For most people, I would recommend SSHFS.  It is no harder to set up than the other options, and it is 2-3x faster, in my experience.

If you run into a wall, drop me an e-mail or start a new thread here and you'll get all the help you need.

Thanks I will give this a shot then...

---

### Post by sub_par11 on 2008-11-26
I was having troubles also finding any easy way to share folders between my laptop and desktop both running Ubuntu. This was by far the easiest way [http://thanhsiang.org/faqing/node/114](http://thanhsiang.org/faqing/node/114)

---

