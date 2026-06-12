---
title: "Novice to Ubuntu/Linux"
date: 2021-02-06
forum: New to Ubuntu
---

### Post by nevillebartos on 2021-02-06
Hello Y'all from Texas.

I am a novice linux user.  I have been working diligently learning Raspberry Pi, Linux Ubuntu and OpenWRT.  I have a good feel were all the basic things are in the CLI and I have a basic understanding of the command syntax and usage.  

I have the latest version of ubuntu installed along side windows 10  on a dual boot machine (yay me...that was two weeks of frustration...but I digress)

I am running a linksys wrt1900ACS router with the latest version of OpenWRT

Here is my current dilema

I cannot for the figure out how to connect my ubuntu desktop to my network attached storage from the ubuntu UI.  I have the NAS setup and mounted through the router installation methods given by the OpenWRT forum.  

I know this could be a lengthy discussion.  

Thanks.

---

### Post by TheFu on 2021-02-07
a) Placing any storage on your WAN router is risky. There have been a number of security failures where router-connected storage became available to the entire internet. This impacted every brand, BTW.  Best to NEVER, EVER, connect storage to a WAN router.  OTOH, if this wifi-router is on your LAN, go for it!

b) network attached storage - can use multiple protocols or just 1.  You need to say which you are using.  In general, NFS should be used for Unix clients. Some of the other popular NAS protocols made changes to their defaults in 2020 which effectively prevent using a GUI tool for a connection. The only stable way to connect is by modifying the /etc/fstab for that specific mount, specific protocol, and remote device.  NFS would require this too, in general.  When it comes to accessing storage, the fstab is how to get the fastest, most stable, connection.  If you use a GUI, the storage access will often be 30% (or more) slower, if it works.

But first we need to know the protocol being used - and the exact version of the different OSes and any NAS protocols being used would mean we don't have to ask for that later.

Hook 'Em!
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a free beginner book on Linux.

---

### Post by nevillebartos on 2021-02-07
My wan and lan interfaces are separate

I can connect to the Samba share via windows 10.  

Ubuntu 20.04  is not so intuitive for me. I get connection refused when attempting to connect from the files "other locations"  SMB4K say the URL is not valid.

---

### Post by TheFu on 2021-02-07
> **nevillebartos said:**
> My wan and lan interfaces are separate

I mean the WAN router needs to be physically separate from the LAN router. A LAN-only router with storage is 1000x less of a concern. A WAN connected router is **always** a concern.

> **nevillebartos said:**
> I can connect to the Samba share via windows 10.  
Lots of things created and deployed by MSFT get tested by every company in the world. They go out of their way to avoid breaking things. 1% test with Linux.

> **nevillebartos said:**
> Ubuntu 20.04  is not so intuitive for me. I get connection refused when attempting to connect from the files "other locations"  SMB4K say the URL is not valid.

Don't use a GUI. Use the fstab with a CIFS mount.  There are plenty of examples in these forums "fstab cifs" is the search term.

---

### Post by nevillebartos on 2021-02-07
COOL!!

I have a separate router/firewall and cable modem.  

I will search fstab cifs.

I have also put up a post in OpenWRT

Thanks

---

### Post by mastablasta on 2021-02-10
if you are using samba then computers need to be in same workgroup to see them.

then (i use Kubuntu so file manager is Dolphin) i would go to network icon, browse to the location (we have several PC connected via samba) and then it will ask for password. you use local admin password and then it connects to storage. no user has to have permission on storage they connect to. you can first assign an empty folder where all permission (i mean read& write, not run) is given to all LAN users. that should make it easier to check if connection is working. after it is working all you need to mess arround with are permisisons for specific user and folder. 

NAS sometimes have their own clients or web browser access.

storage can also be accessed via sFTP. for example my 2 servers (media & file) are accessed via sFTP using filezilla. but i've also added Nextcloud on one so i can access some files via web browser and share them with family. access is limited as much as possible.

---

### Post by TheFu on 2021-02-10
+1 for using sftp.  There are sftp clients for every networked OS and support for it is built-into every Linux file manager that I know.  WinSCP is a Windows sftp client. It also supports scp.  Some versions of Filezilla have a major bug that prevents the sftp client from working. A few months ago, I was testing filezilla and found that it refused to connect to one of my sftp servers. That lead me to the filezilla bug.

I also have nextcloud hosted on my home network, but only allow access to it over a VPN that I run here for remote access.

SMB/Samba has become more and more difficult to use, while sftp *just works* and has for 25+ yrs.

I can't tell, but I really hope you didn't connect storage to your WAN router.

---

