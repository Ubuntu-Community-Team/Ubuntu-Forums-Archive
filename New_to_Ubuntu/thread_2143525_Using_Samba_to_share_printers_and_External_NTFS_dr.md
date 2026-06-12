---
title: "Using Samba to share printers and External NTFS drive"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by Ant01 on 2013-05-09
Please can someone give me a simple solution to my problem or I have to uninstall Ubuntu before I begin.

I can't get to share my printer and external NTFS hard drive on my Ubuntu machine which I specifically set up to backup my windows documents and have a central location for my printers. I have tried everything from changing Ubuntu 12.04 to 12.10 back to 12.04 and back to 12.1
I have also tried all the Samba packages but none of them seem to work, some show me the external  hard drive but don't give me access and the printer once worked and then stopped and is not visible anymore.

I need as simple a solution as possible(idiots proof), please assist...

---

### Post by 2F4U on 2013-05-09
Samba needs to be configured and doesn't work by just installing a package. There is quite some documentation available on how to configure it and here is just one example:

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by Ant01 on 2013-05-09
Now i'm really confused :(

Is SAMBA being done away with (depreciated) and do I have to install something else (CIFS )

I assume i'm setting up a Ubuntu Server not a Ubuntu Client...
What is meant by Allow non-root users to mount SMB shares

---

### Post by bab1 on 2013-05-09
> **Ant01 said:**
> Now i'm really confused :(

Is SAMBA being done away with (depreciated) and do I have to install something else (CIFS )
Samba is not being done away with.  CIFS is the Windows name for the updated SMB protocol.  Whatever you want to call it Samba (3.6), Samba4 or CIFS, they all are variations on the SMB (server message block) protocol for remote file sharing.  For WORKGROUP type sharing I would use Samba 3.6.  Samba4 is for AD style domain servers. > 
I assume i'm setting up a Ubuntu Server not a Ubuntu Client...
Samba client software is installed by default with the Ubuntu desktop/laptop version.  You can install Samba server on either the Ubuntu desktop/Laptop versions or on the Ubuntu server version.  In this case the term server has 2 meanings Ubuntu server is not the same as Samba server.  Ubuntu server has a command line interface (CLI)and Ubuntu Desktop has a graphical user interface (GUI).> 
What is meant by Allow non-root users to mount SMB shares
Traditionally Samba shares required the root user (administrator) to configure shares via the /etc/samba/smb.conf file.  Later on the ability for a non-root user (non administrator) to create shares in their own home directory was added.  These are called *usershares*.  You can configure this type of share via the GUI interface (i.e. Nautilus, etc.) and the configuration file is located at /var/lib/samba/usershares.

---

### Post by squakie on 2013-05-10
Is the Windows computer a Windows 8 computer?  You probably have to assign the workgroup name in Windows as well - I *think* at least Windows 8 is using a different concept by default - homegroup.  This isn't the same as the workgroup - you have to manually change that via system/properties/change name.   I think you also have to have a NetBIOS name in the Samba config file - not sure, but I *think* it should match the system name.

---

### Post by bab1 on 2013-05-10
> **squakie said:**
> ...

I think you also have to have a NetBIOS name in the Samba config file - not sure, but I *think* it should match the system name.
When you install Samba 3 there are 2 daemons that start at boot time.  These are ***smbd*** (for file sharing) and ***nmbd***  (which provides name services).  The nmbd daemon will convert hostnames (in the hosts file) to NetBIOS names.  The only limitation is that the hostname must less than 15 characters long.  If you define the netbios name in the smb.conf file 2 things occur.  The NetBIOS name is not related (but may be the same) to the hostname and the nmbd name conversion function is turned off.

---

