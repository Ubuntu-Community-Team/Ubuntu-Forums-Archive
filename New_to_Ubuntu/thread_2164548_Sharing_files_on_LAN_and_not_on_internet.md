---
title: "Sharing files on LAN and not on internet"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by TLD98541 on 2013-07-31
This is what i'm trying to accomplish, My computer with Ubuntu is a HTPC that shares it's internet connection with 2 other windows computers, it has 2 Ethernet cards, eth1 is connected to a switch that connects to the 2 windows computers, I want to share movie files that are on the Ubuntu machine on NTFS formatted HDs with the windows machines and be able to add movie files to the Ubuntu machine from the windows machines. 

I also need to be able to backup the windows machines to the NTFS formatted HDs on the Ubuntu machine without using passwords.

There is NO need for any passwords and the users of the windows machines need to have total access (read. write, modify, delete) to the files on the Ubuntu machine, What i want is like a network drive or NAS so all the computers on the LAN can have full access all the files on the Ubuntu machine without using passwords

On the other hand eth0 us connected to a modem to the internet and I don't want there to be any file or printer sharing of any kind on that Ethernet card. 

Is there a way to accomplish this setup?

---

### Post by bootedguy on 2013-07-31
Seems overly complicated.  Why two ethernet cards and why NTFS on the Ubuntu machine? You would need to configure Samba on the Ubuntu machine, and that would be about it.

---

### Post by TLD98541 on 2013-08-01
Won't [COLOR=#000000]Samba share files over both [/COLOR][COLOR=#000000]Ethernet cards?

EDIT: This setup is what i have running now. only it's all windows machines.[/COLOR]

---

### Post by matt_symes on 2013-08-01
Hi

> **TLD98541 said:**
> Won't [COLOR=#000000]Samba share files over both [/COLOR][COLOR=#000000]Ethernet cards?

You can specify an interface to bind to using samba.

Take a look at smb.conf and 

[/COLOR]> interfaces (G)                                                                                                                 
                                                                                                                                      
           This option allows you to override the default network interfaces list that Samba will use for browsing, name              
           registration and other NetBIOS over TCP/IP (NBT) traffic. By default Samba will query the kernel for the list of all       
           active interfaces and use any interfaces except 127.0.0.1 that are broadcast capable.
[COLOR=#000000]
[/COLOR]> bind interfaces only (G)                                                                                                       
                                                                                                                                      
           This global parameter allows the Samba admin to limit what interfaces on a machine will serve SMB requests. It affects     
           file service smbd(8) and name service nmbd(8) in a slightly different ways.

[COLOR=#000000]
You can further lock things down using iptables to be doubly sure.

For shearching without password, set up a guest account. After a quick glance at this page, this is the basic technique by the looks of it.

[/COLOR][http://amazingrando.wordpress.com/2007/06/03/share-folders-via-samba-without-a-password-easy/](http://amazingrando.wordpress.com/2007/06/03/share-folders-via-samba-without-a-password-easy/)
[COLOR=#000000]
Kind regards
[/COLOR]

---

### Post by nerdtron on 2013-08-02
Why don't you just  connect the modem directly to the switch and connect the Ubuntu and 2 other PCs on that switch also to make sure they are all on the same network. Also, you probably don't have any public IP so don't worry about sharing ay files over the internet.
Now you'll just need to create a samba share on the ubuntu machine and let the two other pcs connect to it. Plain and simple.

---

### Post by TLD98541 on 2013-08-02
> **matt_symes said:**
> Hi



You can specify an interface to bind to using samba.

Take a look at smb.conf and 

[/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000]
You can further lock things down using iptables to be doubly sure.

For shearching without password, set up a guest account. After a quick glance at this page, this is the basic technique by the looks of it.

[/COLOR][http://amazingrando.wordpress.com/2007/06/03/share-folders-via-samba-without-a-password-easy/](http://amazingrando.wordpress.com/2007/06/03/share-folders-via-samba-without-a-password-easy/)
[COLOR=#000000]
Kind regards
[/COLOR]

Thanks very much matt that helped me get it worked out.

---

