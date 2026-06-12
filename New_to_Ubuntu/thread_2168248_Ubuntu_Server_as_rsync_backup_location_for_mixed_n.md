---
title: "Ubuntu Server as rsync backup location for mixed network and possible webserver"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by Jeremy_Hughes on 2013-08-17
Hi there.

I have a box which I have installed Ubuntu Server 12.04.2 LTS. The primary purpose of this is to function as a backup location for some form of rsync-style backup for the devices on my home network. The network has a variety of different operating systems: three Windows 8 devices, one Windows 7 device, and one Ubuntu desktop device. 

The current implementation has just the one user on the server, and on SAMBA, which I'm using to login on each computer to access a shared folder. I am then using the tool Synkron to backup the windows computers to their own folders in the share. 

There are 2 main issues I'm unsure about:
1. I cannot seem to use an GUI based tool (for instance the Linux version of Synkron) to select the server from the Ubuntu computer to back up to the server with, and I don't understand how to use the rysnc command line to access the server, then sync regularly, automatically starting when the system is booted.
2. I want to have a shared 'drop box' as well as a shared media folder. However, in some cases, permissions have restricted others from using files someone else puts in them. Is there a way of automatically stripping ownership of files put in these folders?

One last thing. At a later stage, I would be interested in running a small web server from the box. When setting up these shares, are there particular considerations needed to keep them secure (so they cannot be accessed externally) or only accessed via password?

In regards to answers: it does not bother me entirely re-installing the system to ensure that everything is set up correctly without leaving behind a mess of unused programs or left over configuration files. It is also not an issue to use a different version. 
Essentially, what is the best way of achieving the system I want.

Thanks

Jeremy

---

