---
title: "Hi guys newbie samba question"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by RiotSloth on 2012-10-04
Hi fellas

I am setting up a samba server at work to be a fileserver for our windows network.  It's all very basic, we have a mix of laptops and desktops running mainly windows 7 and a few Vista.  Some connect wirelessly to the router, and the desktop and Ubuntu Server are on Cat 5.

I installed Ubuntu server yesterday and installed it with samba.  I also installed the desktop and GADMIN-SAMBA.

I can now see the server on the network, but if I try to access it from a windows PC it asks for a user name and password, and nothing I enter is accepted - the root, my server logon, or any of the users I added via GADMIN-SAMBA.

We are all connected to windows via WORKGROUP ie default.

Can anybody help me please?!

many thanks

RiotSloth (Robsa)

---

### Post by newb85 on 2012-10-04
In the file /etc/samba/smb.conf, in the authentication section, do you have a line

> security = user

not commented out?  That would require anyone connecting to the server to have a user account on the server and to log in using those credentials.

---

### Post by sahabcse on 2012-10-04
Add and enable the samba user

ex)
useradd test
smbpasswd -a test

---

### Post by sahabcse on 2012-10-04
Add a user to a Samab share

By default user gets access to /home/test from windows system. Let us say you want to give user "test" access to /data/samba (make sure directory /data/samba exists) directory. Open /etc/samba/smb.conf file and add/modify share called 


[accounts]
comment = Accounts data directory
path = /data/samba
valid users = test sahab
public = no
writable = yes

---

