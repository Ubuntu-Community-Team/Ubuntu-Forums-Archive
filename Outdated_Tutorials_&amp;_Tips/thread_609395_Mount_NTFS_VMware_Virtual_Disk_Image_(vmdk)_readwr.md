---
title: "Mount NTFS VMware Virtual Disk Image (vmdk) read/write"
date: 2007-11-10
forum: Outdated Tutorials &amp; Tips
---

### Post by MrFSL on 2007-11-10
I do a lot of software development and testing and commonly use a Windows virtual machine to work natively in Windows.

Usually I use bridged networking samba to transfer files between my Ubuntu Desktop and my XP virtual machine. The problem is that often I have a LARGE amount of development data to transfer and the speed stinks!

Vmware server comes with a little utility to mount the VMware virtual file systems called ***_vmware-mount.pl_***. This utility works pretty well but mounts all NTFS partitions as Read Only!

Outlined below is a process to mount .vmdk files Read/Write.

***_Requirements_***
[LIST]
[*]vmware-loop
[*]nbd module
[*]ntfs-3g
[/LIST]
Vmware-loop is provided by the free vmware server. Instructions for installing can be found [HERE]("https://help.ubuntu.com/community/VMware/Server").
The nbd (Network Block Device) module should be provided already by Ubuntu. 
Ntfs-3g can be installed using:```
sudo apt-get install ntfs-config
```

***_Making It Work_***
1) Step one is to load the nbd module
```
sudo modprobe nbd
```
2) Next we use vmware-loop, the "Virtual Hard Disk to Network Block Device mapper". This is done using *vmware-loop /path/to/VirtualDisk Partition# Device*. For example:
```
sudo vmware-loop /home/MrFSL/VirtualDisk.vmdk 1 /dev/nbd0
```
3) Finally we open a new terminal and mount in the usual way:
```
sudo mount -t ntfs-3g /dev/nbd0 /mnt/
```

***_Conclusions_***
If you are having permission issues you might want to adjust permissions on the mount point or device:
```
sudo chmod 777 /mnt
sudo chmod 777 /dev/nbd0
```

When you are done unmount with a simple:
```
sudo umount /dev/nbd0
```

Hope this helps someone. I apologize if this has already been posted. I couldn't find it anywhere. ;)

---

### Post by OliW on 2007-11-18
Thank you! I tried doing this last week and I ran into problems with their script screating 17 netblock devices and none of them working. Turned out I needed to do the modprobe. You're a star.

---

### Post by myle on 2008-05-11
It works! Great! Thank you! It's the simplest way for file transfer. The only problem that I have is that after step two I have not to close the terminal in which I executed the command. Next time I'll try the & at the end of the line.

```
-------------------------------------------------------------------
Virtual Hard Disk to Network Block Device mapper
Version: Releasebuild-56528
Copyright 1998-2003 VMware, Inc.  All rights reserved.
-------------------------------------------------------------------

Server: Ready to handle the connection on port 1024
Client: Got partition size: 16755732 sectors (8181 MB)

Client: The partition is now mapped on the /dev/nbd0 Network Block Device.


```
After this, the bash doesn't listen to any command and I have to open another terminal.
Thanks anyway.

---

### Post by kplese on 2008-05-13
Type this in .vmx file:

mainmem.UseNamedFile = "FALSE"

It worked for me.

---

