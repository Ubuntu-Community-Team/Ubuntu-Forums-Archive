---
title: "Mounting NFS with username/password"
date: 2016-06-15
forum: New to Ubuntu
---

### Post by bchun on 2016-06-15
I realize that there have been several threads regarding this procedure:
[https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html)
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

The situation is that my workplace has a Synology diskstation NAS. In order to connect to it, I need to be on my workplace's VPN. I can access the server once on the VPN in my web browser by going to [http://1.2.3.4:5000](http://1.2.3.4:5000) (where the IP address is 1.2.3.4). In Windows, I'd map a drive using [http://serverURL/NAS01Shared](http://serverURL/NAS01Shared), and then I'd be prompted for my username and password. I can map the server using smb, but I can't access the files as if they were local (specifically, I'd to run Matlab code that accesses server files, but from what I gather SMB won't allow that, whereas NFS would). 

Based on what I've read of how to mount NFS, these are what I've attempted and the error messages I've received:
```
sudo mount 1.2.3.4:/NAS01Shared /mnt/share
mount.nfs: access denied by server while mounting 1.2.3.4:/NAS01Shared


sudo mount 1.2.3.4:5000/NAS01Shared /mnt/share
mount.nfs: access denied by server while mounting 1.2.3.4:5000/NAS01Shared
man mount


sudo mount 1.2.3.4:/NAS01Shared -o username=foo,password=bar /mnt/share
mount.nfs: an incorrect mount option was specified


sudo mount //1.2.3.4:/NAS01Shared -o username=foo,password=bar /mnt/share
mount.nfs: Failed to resolve server //1.2.3.4: Name or service not known


sudo mount //1.2.3.4:5000/NAS01Shared -o username=foo,password=bar /mnt/share
mount.nfs: Failed to resolve server //1.2.3.4: Name or service not known


sudo mount \\serverURL\NAS01Shared -o username=foo,password=bar /mnt/share
mount: special device \serverURLNAS01Shared does not exist


sudo mount //serverURL/NAS01Shared -o username=foo,password=bar /mnt/share
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


sudo mount -t cifs //serverURL/NAS01Shared -o username=foo,password=bar /mnt/share
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


sudo mount //1.2.3.4/NAS01Shared -o username=foo,password=bar /mnt/share
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

at this point I start aping this thread:[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
```
sudo mount -t cifs //1.2.3.4/NAS01Shared -o username=foo,password=bar /mnt/share
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


sudo mount -t cifs \\serverURL\NAS01Shared -o username=foo,password=bar /mnt/share
mount.cifs: bad UNC (\serverURLNAS01Shared)


sudo mount -t cifs /serverURL/NAS01Shared -o username=foo,password=bar /mnt/share
mount.cifs: bad UNC (/serverURL/NAS01Shared)


sudo mount -t cifs //serverURL/NAS01Shared -o username=foo,password=bar /mnt/share
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


sudo mount -t cifs //serverURL/NAS01Shared /mnt/share -o username=foo,password=bar
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


sudo mount -t cifs //serverURL/NAS01Shared /mnt/share -o username=foo,password=bar,iocharset=utf8,file_mode=0777,dir_mode=0777
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

What do I need to try in order to be able to access my files on diskstation server as if they were local on my machine?

---

### Post by SeijiSensei on 2016-06-15
Are you sure the NAS supports NFS and that the option is enabled?

Might it be easier to connect with SMB and simply copy over the files you need to your local machine?

---

### Post by bchun on 2016-06-15
> **SeijiSensei said:**
> Are you sure the NAS supports NFS and that the option is enabled?

Might it be easier to connect with SMB and simply copy over the files you need to your local machine?

Thanks for the suggestions.

I can check tomorrow, but this is the email I got when I got my account set up:
[FONT=Calibri]For Unix/MAC Access (NFS) a user must be on the <workplace> LAN.[/FONT]

I would hope that there would be an informative error message when I try to connect to a server doesn't support NFS... but it seems really easy to do:
[https://www.synology.com/en-us/knowledgebase/DSM/tutorial/File_Sharing/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS](https://www.synology.com/en-us/knowledgebase/DSM/tutorial/File_Sharing/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS)

It also seems like I'm even following the correct procedure the diskstation manufacturer recommends...

---

### Post by HermanAB on 2016-06-15
You can check whether the server supports NFS with telnet or netcat:

$ telnet serveraddress 2049

or 
$ nc serveraddress 2049

If there is a NFS server, then you will receive a banner.

---

### Post by bchun on 2016-06-15
Figured it out!

```

[FONT=arial]sudo mount -t cifs //serverURL/NAS01Shared --verbose -o username=foo,password=bar,sec=ntlm /mnt/share
mount.cifs kernel mount options: ip=someweirdIPbutdontcare,unc=\\serverURL\NAS01Shared,sec=ntlm,user=foo,pass=********
```

The important bit was changing the security argument - otherwise I had tried this above (as shown in my first post). 
> [http://manpages.ubuntu.com/manpages/xenial/en/man8/mount.cifs.8.html](http://manpages.ubuntu.com/manpages/xenial/en/man8/mount.cifs.8.html)

The default in mainline kernel versions prior to v3.8 was sec=ntlm.
           In v3.8, the default was changed to sec=ntlmssp.



[/FONT]

---

### Post by bab1 on 2016-06-15
> **bchun said:**
> Figured it out!

```

[FONT=arial]sudo **[COLOR="#FF0000"]mount -t cifs[/COLOR]** //serverURL/NAS01Shared --verbose -o username=foo,password=bar,sec=ntlm /mnt/share
mount.cifs kernel mount options: ip=someweirdIPbutdontcare,unc=\\serverURL\NAS01Shared,sec=ntlm,user=foo,pass=********
```

The important bit was changing the security argument - otherwise I had tried this above (as shown in my first post). 



[/FONT]
You do realize that this is not NFS at all.  It is SMB (CIFS).  See the red above.

---

