---
title: "File locking problem"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by abosetti on 2008-09-24
Hi all and good morning
My name is Alessandro and I am new to linux.

I am having a problem with file locking and corruption in a mixed network enviroment on an Ubuntu Desktop 8.041 acting as a server. The uname -a command says:
2.6.24-21-generic i686 Gnu/linux

Some background infos:
After a few weeks of testing, a few days back I felt confident enough to replace our old Windows NT 4 with a Ubuntu server running Samba (my first linux server :), and sharing a few folders to about 30 pcs.

Everything went smoothly and fine (and overall still is) for the first few days, but I am now experiencing a problem that I didn't have on Windows.

The shares that samba publishes are mainly for Microsoft Fox Pro tables that are opened directly from the shares. I know it's AWFUL but there is nothing I can do about it.

Since I have moved the data to ubuntu, the windows clients (NT workstations and Windows 2000) sometime come up with 
errors that they cannot open a particular .dbf file because is in use by somebody else. Please note that these files are opened for writing by the clients, but are closed immediatly after the operation.

In 3 occasions (in a week) one of this files got corrupted behond repair. 

To get rid of the locking errors I haven't found any way round it but to restart the samba service.

I know that it's got to do with how I have setup Samba (I am an ABSOLUTE beginner, this is my first installation).

I had a look at the man pages and the documentation for Samba, but is really difficult to find anything that is obvious. In short, I don't know where to look or what to look for.

I know that I haven't given enough tecnical informations for anyone to actually solve the problem, but if you are willing to point me in the right direction I can give you everything that I can. 

Thank you in advance

Alessandro

---

### Post by Peter09 on 2008-09-24
Hey, I'm no expert here, but I wonder whether this is to do with different file systems (NTFS and ext?) using different locking methods. I have had similar experiences that I put down to this but never really got to the bottom of it.

---

### Post by Pelham123 on 2008-09-24
Dont know if you've had a look at the official HOWTO:

[http://us3.samba.org/samba/docs/Samba-HOWTO-Collection.pdf](http://us3.samba.org/samba/docs/Samba-HOWTO-Collection.pdf)

At over 800 pages, you would like to think it had your answer. There is a section on on File and Record Locking (Chapter 17).

Good luck


PS - have a look at the man page for 'fuser' - dont know if that will be of any help deciding if a process (if any?) is keeping the file(s) open

---

