---
title: "[network] How to access LAN server"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by theblackalchemist on 2012-11-17
Hi,

In windoze, we can type in the ip address of the LAn server in the "run" box and access our data by the usual explorer interface

How to achieve the same in ubuntu?

TBA

---

### Post by Ms. Daisy on 2012-11-17
what kind of server is it- windows or linux? Has the administrator of the server given you permissions to the server?

---

### Post by Calinou on 2012-11-17
We need more info, you didn't even tell us which protocol you are using.

---

### Post by theblackalchemist on 2012-11-17
Oops, my bad

Yes, its a windows based server and I have access... not too sure about the protocol in use though...

TBA

---

### Post by bab1 on 2012-11-17
> **theblackalchemist said:**
> Oops, my bad

Yes, its a windows based server and I have access... not too sure about the protocol in use though...

TBASMB/CIFS is the protocol and Samba is what you need to use with Ubuntu.

---

### Post by El Tito on 2012-11-17
under nautilus, ctrl+L, and then write down:

smb://ip (or name of the server)/folder or resource

for example:

smb://192.168.251.240/docs

Hope this helps!

---

### Post by theblackalchemist on 2012-11-17
> **bab1 said:**
> SMB/CIFS is the protocol and Samba is what you need to use with Ubuntu.

> **El Tito said:**
> under nautilus, ctrl+L, and then write down:

smb://ip (or name of the server)/folder or resource

for example:

smb://192.168.251.240/docs

Hope this helps!

Thanks mate,

Cheers,
TBA

---

