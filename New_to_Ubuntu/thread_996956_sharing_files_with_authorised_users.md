---
title: "sharing files with authorised users"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by mike_new_boy on 2008-11-29
I Am new to Linux and have a box with Ubuntu 8.10 and Samba on my Windows network.   I am trying to set it up with 2 shares.
Share 1) Visible to all the windows machines on the network, every one can read but with write access only to authorised users
Share 2) to be mapped by authorised users only who will have read / write access

I have tried to achieve that by editing smb.con file adding

[Share 1]
path = path/to/folder 
browseable = yes
guest ok = yes
read only = yes
write list = myname another yet-another

[Share 2]
path = path/to/folder 
browseable = no
guest ok = no
valid users = myname another yet-another

I doesn’t seem to work and I don’t know why. They get unrestricted read / write access on the first and I cannot connect on the second. 
Two particular things puzzle me. Firstly there is another configuration file at /var/lib/samba/usershares/ do I need to do anything with that? Secondly do the windows users have to have Ubuntu user account, a samba account, or both. What name do I use in the write list & valid users, Ubuntu or windows?

---

### Post by cmnorton on 2008-11-30
For the second entry, were any of the users created by running smbpasswd?

I believe the first entry works, because you've said guests can access the share.

Samba is powerful, but is also heady stuff. It takes a bit of information grazing to digest its full power, especially the diagnostic use of smbclient if you are trying connections off your Linux box. That's not pertinent here, but I am listing it as one of the many interesting reads you'll come across.

---

