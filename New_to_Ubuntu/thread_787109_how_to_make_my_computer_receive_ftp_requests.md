---
title: "how to make my computer receive ftp requests"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by GoCool on 2008-05-08
I have a scanner and it has an option of ftp'ing to a file share.
I have created a directory and shared it (opted for NFS) and gave the ip of the scanner in allowed hosts. But still its not ftp'ing the documents here, 

what else I do I need to configure?

I have a BizHub C250 Konica Minolta printer cum scanner.

---

### Post by Cypher on 2008-05-08
You're talking different protocols here..FTP and NFS. For NFS you need to install the Kernel or Userspace NFS Server and share a particular directory. A client would then mount that directory given the IP address.

For FTP, you will want to install a FTP server (like proftpd). This can be easily done with
```

sudo apt-get install proftpd

```
When (if) given the option, choose to start the FTP server as a standalone daemon and it will start up and wait for requests.

If the scanner is indeed using FTP, then you might have to give it username/password credentials to login to your PC, or setup anonymous FTP.

IF the scanner is using NFS, then you just need to make sure that the directory is accessible to everyone or at the least to the scanner's IP address..

---

### Post by GoCool on 2008-05-08
> **Cypher said:**
> You're talking different protocols here..FTP and NFS. For NFS you need to install the Kernel or Userspace NFS Server and share a particular directory. A client would then mount that directory given the IP address.

Oops...thank you for educating me on this one.

> **Cypher said:**
> 
For FTP, you will want to install a FTP server (like proftpd).

Yep...I installed proftpd.

> **Cypher said:**
> 
When (if) given the option, choose to start the FTP server as a standalone daemon and it will start up and wait for requests.

I'll do that.

> **Cypher said:**
> 
If the scanner is indeed using FTP, then you might have to give it username/password credentials to login to your PC, or setup anonymous FTP.

It did give me lots of options which I wasnt sure on what it is (like anonymouse, passive etc). And yes it asked for username and password and I did give my computers username and password (hope that is what it requires)

> **Cypher said:**
> 
IF the scanner is using NFS, then you just need to make sure that the directory is accessible to everyone or at the least to the scanner's IP address..
I am not sure how to know whether the scanner uses the NFS, but I have created the directory and added the ipaddress of the scanner as a trusted host.

---

### Post by Cypher on 2008-05-08
I just looked up the Scanner and it does use FTP. So you have a couple of options..one) use your username/password and, if possible, have it send all files to a particular directory in your home directory. 2) Create a new user just for the scanner and that way all of the files are cataloged seperatly.

---

