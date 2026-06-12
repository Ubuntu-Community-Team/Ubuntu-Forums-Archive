---
title: "Issues with Samba and installing DNS"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by HackOmikron on 2012-01-25
Hey folks, doing a few more installs on my server here.  I'm hitting a bit of a wall here, looking for some info if anyone would be willing to help out :)
 
I tried installing samba (apt-get install samba4) and it had issues installing.  It didn't fully install, so I removed it and tried again, at which point it said:
 
ProvisioningError: guess_names: 'realm =' was not specified in supplied /etc/samba/smb.conf.  Please remove the smb.conf file a let provision generate it.
 
So I removed the smb.conf file and tried again.  Same error.  I'm wondered if I could just leave the installation as is, and manually configure the smb.conf file.  Here is what I have thus far:
 
# Global parameters
[global]
 
server role = domain controller
workgroup = WORKGROUP
realm = 
netbios name = UBUNTU
 
[netlogon]
path = /var/lib/samba/sysvol/scripts
read only = No
 
[sysvol]
path = /var/lib/samba/sysvol
read only = No
 
[share]
comment = Share
path = /srv/samba/share
browseable = yes
guest ok = yes
read only = no
create mask = 0755
 
 
What is realm, and what typically goes there?  If I put something there, will it carry on as normal?
 
Thanks in advance.

---

### Post by lechien73 on 2012-01-25
"realm" is usually the domain name. Samba setup sets this by running:

```
hostname -d
```

Which returns blank if no domain is set.

If you look in /etc/hostname, do you have just a hostname (e.g.: *computer_name*) or is it a hostname and domain (e.g.: *computer_name.domain_name*)?

You can set the domain by editing /etc/hostname:

```
gksudo gedit /etc/hostname
```

Add a domain, and then reset the domain by typing:

```
sudo hostname --file /etc/hostname
```

Now add the domain name to *realm=* in smb.conf :)

Because your server role is domain controller, you need a domain to control. This is a good resource: [http://wiki.samba.org/index.php/Samba4/HOWTO](http://wiki.samba.org/index.php/Samba4/HOWTO)

---

### Post by HackOmikron on 2012-01-25
Excellent, thanks so much, this clears it all up!  +1 to you, good sir!

---

