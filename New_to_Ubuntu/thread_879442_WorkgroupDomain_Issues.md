---
title: "Workgroup/Domain Issues"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by kuragh on 2008-08-04
If anyone could enlighten me on this subject, i'd be much appreciated.
Please excuse my noobiness, have never touched linux at all before and am now doing it as a part of a computing course.

I have installed Ubuntu 8.0.4 and am running the Kubuntu GUI

I have set up the computer so it connects to the domain here at school. Everything is working fine, connects to the domain, can see others connected to the domain, detects proper proxy settings and all. However when i try and access this computer from other Windows XP computers on the same domain, my Kubuntu comp comes up as being in a workgroup, simply called "workgroup" rather than coming up in the domain listing. How do i change this so it is solely on the domain? Does this have something to do with Kubuntu or is it an Active Directory issue?:confused:

Any light on this subject would  be awesome. Thanks

---

### Post by cmnorton on 2008-08-05
Using your favorite editor -- this example uses vi --

sudo vi /etc/samba/smb.conf

Alter or add workgroup comment, and server string as shown below

#====================== Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

workgroup = <domain-name>

# server string is the equivalent of the NT Description field
    comment = <your-samba-server's-name>
    server string = Samba %v Server

---

### Post by jamesrfla on 2008-08-05
I know windows server environment they have this thing called a active directory so you can login on any Windows computer connect to the domain. Is their something similar for Linux like a Linux active directory?

---

