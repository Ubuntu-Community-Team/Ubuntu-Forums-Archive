---
title: "Samba, guest access and browse share"
date: 2013-12-18
forum: New to Ubuntu
---

### Post by sonus.faber on 2013-12-18
I am moving from a DLink NAS to an HP MicroServer with Ubuntu Server.
Just SSH and SAMBA are installed.

Everything works almost fine, but there are some annoying little problems.

I have defined two shares: one is RW with one allowed user (contains most of my stuff, but audio\video) the other one is read only with guest access.



security = user


[discoA]
browseable = yes
read only = no
path = /media/discoA
valid users = stef


[media]
browseable = yes
read only = yes
path = /media/discoA/media
guest ok = yes



1) Browse shares.
Even if shares are defined as browseable and I can see the Ubuntu on the home network from Windows PC, media players, TVs, ect. I can not browse the shares without providing user and password.
I would like to browse shares without autentication and provide user and password just if I wish to connect to the RW share

2) guest access
Sincerely I can not understand how to get read only access to a share without providing user and password.

Any suggestions?

---

### Post by Morbius1 on 2013-12-18
I might be able to explain the Windows part of this dilemma.

Windows passes the current login user's user name and password when it browses for shares. That forces the Linux Samba server to deal with it in some way - at the host level not the share level:

*** If you don't have that user set up on the Linux server and / or haven't given him a samba password then he will automatically be converted to the guest account ( assuming you have "map to guest = Bad User" in your smb.conf ) and will be able to at least see the available shares.

*** If you have set up the user in Linux but have a different samba password then the Windows user will be prompted for credentials - again at the host level.

*** If you have set up the user in Linux and have a samba password that matches his login password exactly he will not be prompted for credentials since they have already been given.

You might want to create another user, say ... stefsmb. Give him the samba password, disable the samba password for stef, and reset your share so that stefsmb is the only valid user.

---

### Post by tfrue on 2013-12-18
So you are wanting to browse the [media] share without credentials, right? Otherwise, you cannot browse the [discoA] share without providing credentials since you explicitly defined security = user, and defined valid user = stef on [discoA].
 
My Window's Laptop only had to authenticate once to my shares and now I don't have to re-authenticate unless my server shut's down or I restart the Samba service.
  
I'm not 100% sure about this, but try and mount the [media] share under a different path. It looks like you are having to authenticate because you are trying to mount the [discoB] under [discoA] which has to authenticate. 

So change the path in your [media] share to something like "/media/discoB," and use mkdir to create the new path you defined in the [media] share. Otherwise, we will create a new directory with read-only permissions, and change the ownership to Nobody for an open share.
 
You will need root privileges so we use sudo:

```
 sudo mkdir -m 777 -p /media/discoB
```
We use -m to change the directory mask, and -p to make parent directories if needed.

Then change the the owner to nobody:
```
sudo chown -R nobody /media/discoB
```
We use -R for Recursive use, and we are going to use Nobody to try and remedy you having to authenticate.

Now we need to change the smb.conf to map the guest account to Nobody. Under the [global] share we need to define the guest account. So add:
```

guest account = nobody

```

Now modify your [media] share to look something like this (Assuming you're going to change the path):
```

[media]
comment= Guest Share
browseable = yes
read only = yes
path = /media/discoB
guest ok = yes

```

I tested this on own machine and here is what my smb.conf file looks like, and I will show you the permissions on my shared folder.(Note that I used /mnt/no instead of /media/discoB on my share. I also omitted a lot of output to make this easier to read. Notice "map to guest = bad user." Make sure that is also un-commented.):
```

#======================= Global Settings =======================


[global]


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP


# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


guest account = nobody


####### Authentication #######


# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = user


# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam


   obey pam restrictions = yes


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes


# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes


# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user




# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups


#======================= Share Definitions =======================


[test]
    comment= test share
    path = /mnt/no
    browsable = yes
    read only = yes
    guest ok= yes
```

And here is the permissions assigned to my /mnt/no folder:
```
chris@ubuntu:/mnt$ ls -ll
total 4
drwxrwxrwx 2 nobody root 4096 Dec 18 10:51 no
chris@ubuntu:/mnt$

```

Even with the permissions set to 777, the read only option defined in the share overrides being able to create new files and folders. You will have to use the Ubuntu machine to add files and folders.

Hope that helps!

---

### Post by tfrue on 2013-12-18
Be sure to do:
```
sudo service smbd restart
```
and
```
sudo service nmbd restart
```

---

