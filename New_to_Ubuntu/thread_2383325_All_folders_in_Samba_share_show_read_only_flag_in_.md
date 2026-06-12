---
title: "All folders in Samba share show read_only flag in Win 10"
date: 2018-01-23
forum: New to Ubuntu
---

### Post by alampnah on 2018-01-23
I am trying to share a NAS volume attached to my Ubuntu (16.0.4.3) machine with a Windows 10 Pro machine. The NAS volume was originally attached to Windows 10 Pro machine and is formatted with NTFS file system. I have succeeded in setting up the Samba service and configuring a share with password authentication. I can also connect to the share from my Windows 10 machine, however all folder have the read_only flag enabled on them and changing them in Windows 10 does not change them. This is causing several programs in Windows 10 to not function correctly. Below are section of the smb.conf file:

[global]
    workgroup = WORKGROUP
        security = user


[NAS-VOL1]
    path = /media/xxx/NAS-VOL1
        public = yes        
        available = yes    
        writeable = yes
    browseable = yes
        read only = no
    guest ok = no
    comment = Synology NAS
        valid users = xxx
        write list = xxx
;       create mask = 0777
;       directory mask = 0777


Any suggestions or help will be appreciated. Thanks.

---

### Post by HermanAB on 2018-01-24
Well, bear in mind that the combination of a Windows file system on a Linux server with a Windows clone network file server is about the most error prone thing you could possibly do.

I would set up an Anonymous FTP server instead, since that is the simplest network service that Windows can handle natively.

To debug your system, bear in mind that you have multiple layers in the onion and if any one layer has a problem, then nothing above it will work.  You are saying that you can read the files, but not write to them, so you are halfway there.  To get write access, the file system must allow access to the Windows user and Samba has to allow write access to that user.  

So log into your server as the Windows user and see whether you can write to the shared directory.  If you cannot log in, then that is the first problem and need to make an account on Linux.  If you can log in but cannot write, then that is the second problem and need to change the file system permissions.  Once you can do those two, try the program smbclient on Linux and only once that works, move over to the Windows machine and try from there.

---

### Post by alampnah on 2018-01-24
If I could, would you suggest that I convert the partition into an ext4 volume and then share it with Windows 10.

---

