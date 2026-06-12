---
title: "Setting up CIFS Mounts in /etc/fstab"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by Bob_Hartung on 2014-04-28
I am trying to setup "/etc/fstab" to automatically setup some CIFS file mounts on a Windows 2003 server. I initially set them up to work with just my user for testing purposes like this...[INDENT]
//main-ms4/dept /home/bhartung/WindowShares/dept cifs credentials=/home/bhartung/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 1 3[/INDENT]

This commmand works fine and does mount the share successfully during logon.

My next step was to make the mount applicable to any user logging in by using the env variables $HOME
[INDENT]
//main-ms4/dept $HOME/WindowShares/dept cifs credentials=$HOME/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 1 3
[/INDENT]

This line does not cause any errors but it fails to mount the windows share.

When I type $HOME at the prompt in Xterm, it echoes "/home/bhartung".

What am I missing?

Thanks.

---

### Post by TheFu on 2014-04-28
fstab mounts don't happen at login. They happen at boot.  It can be confusing.

/etc/fstab is a system level config file.  You need a per-user config file or a tool that understands different users. I know of 2 ways to accomplish this - **autofs** and through a gvfs client like nautilus.  [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)  should help.

---

### Post by Bob_Hartung on 2014-04-29
Thanks for the suggestion. I checked out autofs but it does not support connecting to CIFS shares that require authentication.

I'm doing a proof of concept project showing that older XP PCs could be updated to Lubuntu and be functional equivalents of XP. Part of that is being able to mount Windows shares based on user logins. In particular is mounting a share back to the user's home directory on a Windows share, their "My Documents" location.

So far, I've been able to do that on a PC setup for a single individual using /etc/fstab to mount the shares. It also relies on a file containing the username and password of a single individual to authenticate to the Windows server. However, dealing with multiple users on the same PC has been a challenge.

Is there a way to run a script automatically after the user has logged into Lubuntu so that env variables can be used to mount shares particular to the individual?

---

### Post by TheFu on 2014-04-29
I'm using autofs to mount a few CIFS shares with authentication. This is NOT for individual users - it is system-wide, so a little different than your needs, I believe.

Here's my /etc/auto.Data file:
```
D       -fstype=cifs,rw,iocharset=utf8,file_mode=0666,dir_mode=0777,credentials=/etc/samba/win-D.credentials  ://172.22.22.14/D
K       -fstype=cifs,rw,iocharset=utf8,file_mode=0666,dir_mode=0777,credentials=/etc/samba/win-D.credentials  ://172.22.22.14/K

```
and the resulting mounts:
```
//172.22.22.14/D  245G  154G   91G  64% /Data/D
//172.22.22.14/K   74G   35G   39G  48% /Data/K

```

I would hunt down the way that nautilus stores permanent mounts, then create a script that makes those for every userid on the system, if I was unable to get autofs working.

---

### Post by Morbius1 on 2014-04-29
You can use autofs with environment variables to allow each user to mount a share with his own credentials. Using TheFu's example:

```
D       -fstype=cifs,rw,iocharset=utf8,credentials=${HOME}/win-D.credentials,uid=${UID}  ://172.22.22.14/D


```

When morbius accesses /Data/D the username and password located at /home/morbius/win-D.credentials will be passed and the share will mount with morbius as owner. Just make sure every user has a win-D.credentials file in their respective home directory.

This assumes all these users are not concurrently logged in.

---

### Post by SeijiSensei on 2014-04-29
Another option is to [export the shares with NFS on the Windows 2003 Server](http://blogs.msdn.com/b/sfu/archive/2007/04/19/set-up-server-for-nfs-in-windows-server-2003-r2.aspx) and mount the shares with NFS on the clients.

---

