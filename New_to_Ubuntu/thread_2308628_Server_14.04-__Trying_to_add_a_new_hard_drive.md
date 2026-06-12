---
title: "Server 14.04-  Trying to add a new hard drive"
date: 2016-01-04
forum: New to Ubuntu
---

### Post by steve239 on 2016-01-04
Hello all...

First let me say that I am a complete noob.... I am running Ubuntu Server 14.04 on a Xen Hypervisor and want to add more hard drives.  This machine will be my Plex server.

I have been googling and found this:  [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

when i run the             sudo lshw -C disk        command, i show that the OS thinks it is a DVD drive

 *-cdrom
       description: SCSI CD-ROM
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       capabilities: audio
       configuration: status=nodisc

there is no DVD drive currently connected....... any thoughts?

---

