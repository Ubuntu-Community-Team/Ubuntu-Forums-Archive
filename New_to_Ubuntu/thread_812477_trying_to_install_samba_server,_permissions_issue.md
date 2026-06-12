---
title: "trying to install samba server, permissions issue"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by badperson on 2008-05-29
Hi,

I'm going through a book and trying to install a samba server for the first time. I have two machines, one running ubuntu desktop, and another with ubuntu server (it also has the gnome dt environment on it). 

I'm at the point where I'm trying to establish a password. 

I get this: 

```
ubuntuserver@jasonServer:~$ sudo smbpasswd -a MSHOME
New SMB password:
Retype new SMB password:
Failed to modify password entry for user MSHOME
```

Here are the sections in the /etc/samba/smb.conf the book said to change:

   workgroup = MSHOME
   domain master = auto
   wins support = no
   dns proxy = yes
   name resolve order = lmhosts host wins bcast


is the MSHOME a problem? should I change the name? I don't have any experience setting up a domain. The machines I want to be able to use the network are the two machines I just described, plus a laptop (home network) that will all connect via wirless modem (laptop is wireless, the other machines have ethernet cables plugged in the wireless modem)

Also, the machines have dynamic ip's. 

thanks. 
bp

---

### Post by badperson on 2008-05-29
think I got it...

I started samba (duhhh....)
and then used this

sudo smbpasswd -L -a your_username

---

### Post by quelx on 2008-05-29
to use **smbpasswd** the user must be a system user or manually added to **/etc/samba/smbusers**

```
sudo nano -w /etc/samba/smbusers
```

and add a line like it suggests at the top **# Unix_name = SMB_Name1 SMB_Name2 ...** then try **smbpasswd** for your new user.

EDIT: Ha nevermind!

---

### Post by badperson on 2008-05-29
I think I'll still run across that when I need to create windows user, though. 
thanks for the reply!
bp

---

### Post by badperson on 2008-05-31
Hi,

so I got the server up and running, I was able to see the shared folder on the server from the windows machine, but I can't write to the folder from the windows machine...I think I have it set as r/w (I used the graphical tool on the server to set up the shared folder)

Here is the info listed in the smb.conf file:
[SAMBA_TEST]
path = /home/ubuntuserver/Documents/SAMBA_TEST
available = yes
browsable = yes
public = yes
writable = yes



thanks. 
bp

---

