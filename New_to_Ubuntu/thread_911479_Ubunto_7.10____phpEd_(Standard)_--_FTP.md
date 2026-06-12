---
title: "Ubunto 7.10  /  phpEd (Standard) -- FTP"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by E I Rutter on 2008-09-05
Hello,

Subject -- Ubunto 7.10  / NuSphere phpEd (Standard) -- FTP 

We have a LAN comprising a BT HGV2700 router, Windows XP PC and a UBUNTU 7.10 Server configuration (no screen, keyboard or mouse) with LAMP, SAMBA, SSH WEB and FTP servers installed. The Ubuntu Server is controlled from the Windows XP PC using PUTTY.

The Windows XP PC has NuSphere phpEd (Standard) installed for php development and I wish to use its file upload facility to transfer files to the Ubuntu Server using FTP (phpEd Standard does not suppport SFTP), just as one would to a remote server.

The problem is that when attemting the file upload, the following message ie received:

      Socket Error # 11004

Question:

Does anyone know how to fix this problem or can anyone suggest what mistakes we may have made to cause this error?

Many thanks,

IvanR

---

### Post by stoneybroke on 2008-09-06
Hi,

Error 11004 is caused by missing system files or broken system registry structures.

or  Socket Error 11004 means that the DNS server which VPOP3 is talking to does not have a record of the appropriate type for the computer name which it was looking up.

DNS supports many different types of data record -

    * 'A' records contain the IP address for a particular host name
    * 'MX' records contain the mail server for a particular host name/domain name
    * 'NS' records contain the DNS servers which hold authoritative information for a particular host name
    * etc 

An error 11004 can happen if, for instance, VPOP3 does a DNS lookup for a POP3 server at 'myisp.com', but the DNS server only holds an NS record or an MX record, but not an A record. This can happen if the DNS server is currently incorrectly configured (check with your ISP, or whoever is running the DNS server you are using) or because you should be using a different computer name (eg 'pop3.myisp.com') which would have an A record defined.

In some cases it can also happen because you are using the incorrect DNS server addresses (eg using the DNS servers of one ISP when you are dialing into a second ISP)

Try running a registry repair program to fix things first though.

Hope that helps

---

