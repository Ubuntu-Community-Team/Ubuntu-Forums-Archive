---
title: "Auto Mount NAS with fstab Not Working"
date: 2019-11-11
forum: New to Ubuntu
---

### Post by seandavidson on 2019-11-11
So i am new to linux and Ubuntu came over from MacOS. I have a NAS that I need to auto mount at reboot since my media server uses it for media. i have setup cifs and edited the fstab file with the following but it will not auto mount. But when i run ```
sudo mount -a
``` it will mount fine.

```
//xxx.xxx.xxx.xxx/public /media/NAS cifs vers=2.0,uid=1000,gid=1000,username=username,password=password,_netdev,file_mode=0777,dir_mode=0777 0 0
```

I am running Ubuntu 19.10

Any thoughts?

Sean

---

### Post by TheFu on 2019-11-11
I don't have 19.10.  We are LTS-only here.  Mounting at boot and automounting are different things, but that isn't important.

I don't see anything clearly wrong with the fstab line.  I use autofs so storage doesn't get mounted until requested using the automount daemon. The options I use are:

```
rw,iocharset=utf8,vers=2.1,uid=tf,gid=tf,file_mode=0664,dir_mode=0775,credentials=/root/win7lap-D.credentials
```

Again, I think your options should be fine, though I'd have to check the vers=2.0 to see what that means.```

           ·   2.0 - The SMBv2.002 protocol. This was initially introduced in
               Windows Vista Service Pack 1, and Windows Server 2008. Note
               that the initial release version of Windows Vista spoke a
               slightly different dialect (2.000) that is not supported.
```
That's from the mount.cifs manpage.  BTW, I should probably add _netdev to my options, but because autofs is used, nothing gets mounted until requested.

Did the log files show anything on the NAS?  Should be in /var/log/samba/ ... somewhere.

If the NAS supports NFS, I'd use that for a number of reasons rather than CIFS.

---

### Post by seandavidson on 2019-11-12
@ThFu Thanks for the info. I will take a look at the NAS logs and NFS.

---

### Post by Morbius1 on 2019-11-12
> //xxx.xxx.xxx.xxx/public /media/NAS cifs vers=2.0,uid=1000,gid=1000,username=username,password=password,_netdev,file_mode=0777,dir_mode=0777 0 0
Probably the easiest route is to invoke autofs by adding two more options to your list:
> //xxx.xxx.xxx.xxx/public /media/NAS cifs vers=2.0,uid=1000,gid=1000,username=username,password=password,file_mode=0777,dir_mode=0777[COLOR=#0000cd]**,noauto,x-systemd.automount**[/COLOR] 0 0

After editing fstab unmount the share: [highlight]sudo umount /media/NAS[/highlight]

Then do the systemd 3-step:
```
sudo systemctl daemon-reload
sudo systemctl restart remote-fs.target
sudo systemctl restart /media/NAS
```

To test things run [highlight]mount | grep NAS[/highlight]

You should get something that starts with something that tells you the autofs process is running:
> systemd-1 on /media/NAS [COLOR=#0000cd]**type autofs**[/COLOR]
Followed by the actual mount parameters:
> /xxx.xxx.xxx.xxx/public on /media/NAS type cifs (rw,relatime .....

Note: autofs works by mounting on demand when accessed and just about anything can trigger it.

Note2: You can also go all the way with a systemd-autofs by having it automatically unmount when it's not required but you will have to change your mount point for that. Autofs and udisks2 don't play well together and udisks2 will make it so anything mounted under /media or your home directory will never unmount because autofs will think it's never idle. .... Come to think of it you should probably change your mount point anyway to say ... /mnt/NAS ... but that's up to you.

---

### Post by TheFu on 2019-11-12
If you have things working, ignore what I've written below.  It is just some things I've learned from senior Unix admins over the decades.

The **autofs** process has config files in /etc/ usually tied to auto.master and auto.nfs/auto.cifs which have a specific, sometimes odd, format.  No need to touch the fstab - I'd not heard of autofs using the fstab before today.  The autofs manpage:
```
OPERATION
       autofs   will   consult  a  configuration  file  /etc/auto.master  (see
       auto.master(5)) by default to find mount points on the system. For each
       of  those mount points automount(8) will mount and start a thread, with
       the appropriate parameters, to manage the mount point.
```
Perhaps systemd changed something, again?!  There is no mention of automout in the fstab manpage.

The main reason I prefer using autofs is that unused network storage mounts aren't mounted. This is very handy with the  remote storage may not be powered on or for a laptop that might not be on the home network.  It is also helpful with USB storage devices that might not be connected all the time.
<rant>
I'm a little old-school, so new x-...... additions to mount options in the fstab file seem like too many cooks in the kitchen.  Whenever that happens, the chances of problems increases.  resolvconf is an example where things were working great, but "someone" decided to make it more flexible and DNS has never worked right since then. The last few releases, the systemd team has been trying to "fix" the issue ---- only to make it worse.  IMHO.

Searching the manpages, systemd.automount does say something about using the fstab.  
```
FSTAB
       Automount units may either be configured via unit files, or via
       /etc/fstab (see fstab(5) for details).

       For details how systemd parses /etc/fstab see systemd.mount(5).

       If an automount point is configured in both /etc/fstab and a unit file,
       the configuration in the latter takes precedence.

```
Once again, too many cooks, IMHO.
</rant>

For network mounts, I like to keep the mount point on the source system the same as the mount point on each client to prevent confusion.
/D on the NFS host is  /D on each client.  1-for-1 mapping, but I'm a little slow sometimes. For example:
```
$ df .
Filesystem      Size  Used Avail Use% Mounted on
istar:/D        3.5T  3.5T   42G  99% /D
```
istar is the hostname of the NFS server where /D is a 4TB partition.
On the current machine, I made an empty directory, /D, which serves as the mount point for the NFS storage.

If you are doing media streaming from the NAS and see any stuttering over CIFS, Kodi MP recommends switching to NFS which seems to help assuming the NAS is 100Mbps wired ethernet or faster.

---

### Post by Morbius1 on 2019-11-12
@seandavidson

There needs to be some clarification here or else you will end up with a mess. There are 2 autofs processes available to you.

** There's the original one where you have to install something and set up configurations in a couple of files. It works. I've used it myself in the past.

** Then there is the new way made possible by systemd that offers a number of options which is invoked in fstab itself. It's been available for years now so new is in the eye of the beholder. There is nothing else to install and no files to configure. Only add systemd options to fstab.

If you are still using cifs I would suggest the systemd method first since it's easy enough to set up and if it doesn't do what is advertised move on the the old way - but only after removing your fstab entry. 

If you have moved to using NFS I can't comment either way. I haven't used NFS in 20 years.

---

### Post by seandavidson on 2019-11-28
I wanted to come back and state I got it working. I had to add the noperm to the fstab 

//xxx.xxx.xxx.xxx/public /media/NAS cifs uid=1000,gid=1000,username=username,password=password,noperm,_netdev,file_mode=0777,dir_mode=0777 0 0

---

### Post by Morbius1 on 2019-11-28
You did more than add noperm you removed [COLOR=#0000cd][B]vers=2.0.


[/B][/COLOR]That allowed cifs to mount at SMB3 ( vers=3.0 ) if it wanted to. The Linux kernel dictates which version of smb to use and does so by negotiating with the server to find the optimal value between vers=2.1 and vers=3.0 automatically. Maybe your server ( NAS ) didn't like or was more up-to-date than vers=2.0.

---

