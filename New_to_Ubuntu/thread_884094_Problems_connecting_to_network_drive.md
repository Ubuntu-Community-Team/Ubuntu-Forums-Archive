---
title: "Problems connecting to network drive"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by kender42 on 2008-08-08
I have a network drive attached to a router which works fine most of the time. The problem is that when I shut down my winblows box I no longer can access the network drive. When I go to Place -> Network it won't even show up. But when the winblows box is turned on it shows up with no problem.

The drive is an Iomega Home Network Hard Drive. I tried to get support from them but they told me they don't support linux.

What can I do as workaround?

---

### Post by alpage2 on 2008-08-08
Curious!!

Can you post a list of the components of your network?

Does it include a separate modem/router which provides the DHCP server?

Or does your windows machine provide the DHCP server?

Do any other network devices on your network also disappear when your windows box is turned off?

Please also include the contents of your /etc/fstab file in your reply.

Alan

---

### Post by st33med on 2008-08-08
Hrm... This usually means that Windows is receiving the hard drive and broadcasting it across the network as a local drive. To confirm this behavior, the hard drive is usually accessible  through your network folder (eg: MSHOME).

---

### Post by kender42 on 2008-08-08
> **alpage2 said:**
> Curious!!

Can you post a list of the components of your network?

Does it include a separate modem/router which provides the DHCP server?

Or does your windows machine provide the DHCP server?

Do any other network devices on your network also disappear when your windows box is turned off?

Please also include the contents of your /etc/fstab file in your reply.

Alan


How do I get a list of network components.

The 2wire router (2701 series) gives the DHCP

Windows DHCP I don't know

Only my other ubuntu box shows up when windows box is turned off

/etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=7a39f04e-0933-41fd-81be-9354d3c43022 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=a7b3604b-61e1-4b0d-809c-720891bd4720 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by alpage2 on 2008-08-08
> How do I get a list of network components.

The 2wire router (2701 series) gives the DHCP

Windows DHCP I don't know

Only my other ubuntu box shows up when windows box is turned off

Thanks, that answered my question - sorry - I should have said network devices, rather than network components.

So - you have 2 ubuntu boxes, a windows box and a router, and the latter providing the DHCP server, which assigns an IP address to each box.

I see on the Iomega website that this network drive, although it has an embedded linux kernel, includes windows workgroup support, so I think the comment from st33med is very relevant.

When the windows box is on, what is the workgroup name - MSHOME perhaps? And does your network drive appear in the MSHOME folder?

Alan

---

### Post by kender42 on 2008-08-08
The network name is called HOME since that is the default network created by my 2wire router. When I try to connect to the network I get an icon that says 'Windows Network' but when I click on it (double click) I get no listings of any kind. The windows box is a laptop. But the drive was installed before the laptop was purchased. It worked on my old XP system and it works on the other Ubuntu box if I use PlayOnLinux for some reason. So I don't know what it's doing. But since the laptop is out of the area at the moment even that won't connect.

My old XP setup is on a dual boot. Laptop=vista

---

### Post by kender42 on 2008-08-08
bump still need a workaround

---

### Post by alpage2 on 2008-08-09
It may be that your network drive is pretending to be a windows device. Does the drive manual say anything about using it in a linux network, as opposed to a windows network?

Alan

---

### Post by madmaxnj on 2009-01-02
I have pretty much the same exact problem.  I have an iomega network hard drive, ethernet, 500G.  My router, providing DHCP, is a D-Link.  When my XP machine is on, I have to run the iomega app to find the drive and mount the folders.  Then I see it on my XP machine.  Then I turned on my ubuntu box and it would see the drives under Places-Network, but I couldn't see any of the subfolders or files.  When I tried to Places-Connect to Server the drive would show up on my desktop and then disappear immediately.

On the XP side, I'll look into figuring out a .bat to mount the drive.  But on Ubuntu I can't even see the files, ever.  And if the XP box is off, I can't see the network drive at all.  What's the deal?

I've been playing with Ubuntu now for about ~1 month.  At first I thought it was great since the initial setup and getting online was really quick.  But then I had problems with keyring, now with xulrunner 1.9, now I can't see my network drive.  I'm seriously considering dumping this exercise.

---

### Post by madmaxnj on 2009-01-11
Okay, I figured out a way to connect to the iomega home network hard drive.  Like others that have posted I had many problems trying to connect to it through traditional methods.  But I found a way. 

First, login to the admin utility of the drive.  Enable FTP.  On the FTP page create a user account, and then give the user read/write privileges.  I also created a password since all the attempts I've tried to connect ask for a password, even when on the smb settings I didn't set one.

Now, go to Places-Connect to Server.  Select:
-FTP (with login)
-Server: your shared drives IP address
-Port:  default on iomega is 21
-folder:  default is public
-user name:  whatever you setup in the first step
-add a bookmark so you don't have to do this every time.  The bookmark will show up in your Places drop down.

When you connect it will ask for the password you created in the first step.

Now, I get an keyring error, which I just x out of and then get an error that it didn't connect, even though it did and I have the folder icon on my desktop.  Its not elegant, but it works.  Now if I can fix the keyring and somehow make this try to autoconnect on bootup I'll be all set.

---

