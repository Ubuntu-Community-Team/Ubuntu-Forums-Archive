---
title: "fstab cifs differences 16.04 vs 18.04??"
date: 2019-11-30
forum: New to Ubuntu
---

### Post by maxburn on 2019-11-30
I have a existing 16.04 VM with the line below in /etc/fstab and it is working. Same exact line in 18.04 results in the error below. What is wrong here, I thought this would be easy to copy?

```
//192.168.100.123/freenas /mnt/freenas cifs credentials=/home/myuser/freenaspasswords,vers=3.0,iocharset=utf8,sec=ntlm,uid=myuser 0 0
```

```
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

/mnt/freena exists and the password file exists with same contents and permissions as on the other server. So switching things up a little I try this; 

```
//192.168.100.123/freenas /mnt/freenas cifs username=username,password=password,iocharset=utf8,sec=ntlm 0 0
```

Same error. I originally used this page to put the commands together on the first server, which worked. 
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

I can see the old server is cifs version (2:6.4-1ubuntu1.1) and the new one is version (2:6.8-1). I used "sudo apt-get install cifs-utils" to get cifs on the new server.

---

### Post by TheFu on 2019-11-30
Last week, I had to removed iocharset=utf8 option on my 16.04 cifs connections into Win7 machines to get any shares to work.  Win7 supports vers=2.1 only. Also, sec=ntlmv2 is working.

From the  mount.cifs manpage: 
```
The default in mainline kernel versions prior to v3.8 was sec=ntlm.
           In v3.8, the default was changed to sec=ntlmssp.

```

Credentials files are still working.

Don't know if any of this is helpful or not.

---

### Post by maxburn on 2019-12-01
The part that is confusing me is this is the same NAS device I'm getting  in to with two different Ubuntu versions with the same command. One  works and the other doesn't. I could totally understand if the NAS  changed something in an update that drove a need for client side  changes. None of my windows boxes have problems getting into it either.

---

### Post by Morbius1 on 2019-12-01
sec=ntlm is inconsistent with vers=3.0. If I add sec=ntlm to an already working cifs mount expressions of a modern server I too will get the [highlight]Invalid Argument[/highlight] error.

**vers=1.0,sec=ntlm** makes sense. **vers=3.0,sec=ntlm** dos not.

The version of the Linux Kernel that comes with 18.04 is designed to negotiate with the sever the best smb dialect ( i.e., vers ) to use from vers=2.1 to vers=3.0 automatically.

---

### Post by maxburn on 2019-12-02
> **Morbius1 said:**
> sec=ntlm is inconsistent with vers=3.0. If I add sec=ntlm to an already working cifs mount expressions of a modern server I too will get the [highlight]Invalid Argument[/highlight] error.

**vers=1.0,sec=ntlm** makes sense. **vers=3.0,sec=ntlm** dos not.

The version of the Linux Kernel that comes with 18.04 is designed to negotiate with the sever the best smb dialect ( i.e., vers ) to use from vers=2.1 to vers=3.0 automatically.

Ah! Newer version seems much smarter, I was able to get rid of the explicit switches and it worked; 

```
//192.168.100.123/freenas /mnt/freenas cifs credentials=/home/myuser/freenaspasswords,iocharset=utf8,uid=myuser 0 0
```

I remember lots of trouble getting it to work under 16.04 so that's why I wound up with that combo.

---

### Post by TheFu on 2019-12-02
> **maxburn said:**
>  
I remember lots of trouble getting it to work under 16.04 so that's why I wound up with that combo.

The SMB combinations are many.  Clients, servers, minimal servers, old servers, new servers .... and clients from any vendor or F/LOSS project out there.  At some point it will "just work", hopefully.  

Or with FreeNAS and any Unix-based system, just use NFS.  Basically, NFS "just works" and has little overhead for clients.  For video streaming, NFS is recommended by OSMC and Kodi teams.

If this thread is solved, please use the Thread Tools button near the top to mark it that way. Greatly helps out the community, both people seeking answers and those wanting to help.

---

