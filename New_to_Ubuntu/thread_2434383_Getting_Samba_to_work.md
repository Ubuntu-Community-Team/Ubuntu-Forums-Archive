---
title: "Getting Samba to work"
date: 2020-01-04
forum: New to Ubuntu
---

### Post by davidgonterman on 2020-01-04
Hey there people.  How are things?

I had some spare computer parts and decided to combine them to form a file server for my computers.  For backups and cloud computing.

I got Ubuntu Server installed.
I got it to mount two of my shares (/media/Disk1 and /media/Disk2) automatically at boot-up
I got it so I can remotely control the terminal from Windows 10, so I won't need a screen for my server.

And now I got Samba installed and running.

Now the problem:  How to get a public Samba share set up so I can access it from Windows 10?  While I know my way around the Unix terminal, judging by how I got this far, I'll need a bit of help with Samba.

Any assistance here will be greatly appreciated.  Thanks in advance.

---

### Post by Morbius1 on 2020-01-05
[1] Make sure samba is installed:
```
sudo apt install samba
```
[2] Edit /etc/samba/smb.conf and at the bottom of the file add this:
```
[Disk1]
path = /media/Disk1
read only = no
guest ok = yes
```
[3] Save smb.conf and restart smbd:
```
sudo service smbd restart
```
[4] Now run this command:
```
hostname
```

On the Win10 machine open explorer and enter the network path to that share substituting hostname with the one from step [4] and adding a .local at the end:
```
\\hostname.local\Disk1
```

The ability of the Win10 client to actually write to that share depends on the Linux permissions of /media/Disk1. If it's owned by root with read only access to everyone else you will not be able to write for example. If it's owned by a user on the server and since this is a public share you can use something like a "force user" in the share definition.

Notes on the state of Samba and SMBv1:

Win10 disables SMBv1 on the client ( and server ) side and host discovery by NetBIOS name doesn't work without it. What that means is that when you go to Explorer > Network it will never be able to see your Linux server. You can still access the server but it has to be done explicitly:

Either by ip address: [highlight]\\192.168.0.X[/highlight]
Or as we did earlier by it's mDNS hostname: [highlight]\\hostname.local[/highlight]

There is another way using WS-Discovery which Win10 itself uses but that takes a bit to set up.

---

