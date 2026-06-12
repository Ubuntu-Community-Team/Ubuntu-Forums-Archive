---
title: "HOW TO: Setup Samba Over A Linux Network."
date: 2004-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Vulc on 2004-10-27
hey guys, I wanted to share a folder on my laptop with my desktop (both linux) how do I do it?

---

### Post by jdong on 2004-10-27
the most typical way is by configuring a program called **samba**. It's a Windows File Sharing server/client for Linux. There are plenty of guides on Google about how to do this.


I recommend that you use **SSH**. Though technically not a file sharing protocol, it's easy to set up, plus very simple to extend over a larger network. It's the best solution when both systems run Linux. Plus, traffic is encrypted, giving you an extra sense of security, *especially* if there's untrusted people on your network (or you're going through the internet!)

First, use **apt-get install ssh** to install the SSH server. Do this on both systems. 

Open up a file browser (using any folder on the Computer menu). Go to **File**, select **Connect to Server**. Choose SSH as the protocol, fill in appropriate login names and such.

---

### Post by FLeiXiuS on 2004-10-27
I wouldn't agree with SSH to share files.  Thats not the way you would want to go.  I would reccomend installing samba / swat.  (SWAT is optional)

First lets begin by setting up SAMBA!

**Installing...**
```
sudo apt-get install samba
```

**Configuring /etc/smb.conf**
We will be creating a whole new samba config because we are the guru's and it improves validity. :-P. 

[I]1. Rename /etc/smb.conf to /etc/smb.conf.old
2. Open /etc/smb.conf with your favorite text editor![/I]

```

; /etc/smb.conf
;
; Make sure and restart the server after making changes to this file, ex:
; /etc/rc.d/init.d/smb stop
; /etc/rc.d/init.d/smb start

[global]
; Uncomment this if you want a guest account
; guest account = nobody
   log file = /var/log/samba-log.%m
   lock directory = /var/lock/samba
   share modes = yes

[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mode = 0750

[tmp]
   comment = Temporary file space
   path = /tmp
   read only = no
   public = yes

```

NOTE: If your Samba server has more than one ethernet interface, the smbd may bind to the wrong one. If so, you can force it to bind to the intended one by adding a line that looks like this to the [global] section of /etc/smb.conf:

```
"interfaces = 192.168.1.1/24" 
```
Replace the IP above with the interfaces IP address.  Notice the /24 at the end.  This is the subnet default for a CLASS-C network.  It may vary depending on your network.

To share a directory with the public, create a clone of the [tmp] section above by adding something like this to smb.conf:

```

[public]
   comment = Public Stuff
   path = /home/public
   public = yes
   writable = yes
   printable = no

```

To make the above directory readable by the public, but only writable by people in group ubuntu, modify the entry like this:

```

[public]
   comment = Public Stuff
   path = /home/public
   public = yes
   writable = yes
   printable = no
   write list = @ubuntu

```

After this I would reccommend setting up samba for encrypted passwords.
In the [global] section of /etc/smb.conf, add the following lines:
```

encrypt passwords = yes
smb passwd file = /etc/smbpasswd

```
NOTE: If your clients and server are using encrypted passwords, you will not be able to browse the available shares on the server until an initial connection has been made with the appropriate authentication.

This should be all, save and exit.

**Starting SMB Daemons**
```
sudo /usr/sbin/smbd -D && /usr/sbin/nmbd -D
```

**Accessing Shared Folder on Another Linux Box**
To see which shares are available on a given host, run:
```

/usr/bin/smbclient -L host

Example:
/usr/bin/smbclient -L fleixius

```

Where 'host' is replaced with the hostname of the samba server on the network.  Unless the SMB server has no security configured, it will ask you for a password.  This should print back a service page.  Where services are what the host can share to you.

To view the shared folder 'public' on machine 'fleixius' (//fleixius/public) you will need to:
```

/usr/bin/smbclient service <password>

Example:
/usr/bin/smbclient ////fleixius/public  mypwd

```
Because of shell restrictions you have to escape the backslashes.

Now once your in the 'smb: \' console.   You can type 'h' for a help menu.

**Mounting a Shared Drive**
Using the examples above, lets say we want to mount a folder called "Ubuntu" shared on "fleixius" to a directory of "/home/Ubuntu" on the local box.  The typical mount command would be as following:

```

smbmount "\\\\fleixius\\Ubuntu" -U rtg2t -c 'mount /home/Ubuntu -u 1000 -g 1000'

```

Notice -u and -g.  UID and GID.  Replace those with your values also.

I hope this helps and solves the problems with samba.  Please send feedback!

---

### Post by Vulc on 2004-10-28
k I followed the guide as written but I get this error

vulcanon@Vulcari:/etc/samba $ sudo /usr/bin/smbclient -L Vulcari 
Password:
session setup failed: NT_STATUS_LOGON_FAILURE

gave the correct password too

---

### Post by strips on 2004-10-28
Why use samba in a pure linux relation?

If you don't need user auth, NFS is the solution.

It's much easyer than samba and you don't get the overhead as with SSH filetransfer.

Server:
[http://nfs.sourceforge.net/nfs-howto/server.html](http://nfs.sourceforge.net/nfs-howto/server.html) 

Client:
[http://nfs.sourceforge.net/nfs-howto/client.html](http://nfs.sourceforge.net/nfs-howto/client.html) 

Regards
Stian H. Larssen

---

### Post by strips on 2004-10-28
[QUOTE=Vulc]k I followed the guide as written but I get this error
vulcanon@Vulcari:/etc/samba $ sudo /usr/bin/smbclient -L Vulcari 
Password:
session setup failed: NT_STATUS_LOGON_FAILURE
gave the correct password too[/QUOTE]

Hi.

Did you add the samba password on the server for the correct user?

smbpasswd

---

### Post by FLeiXiuS on 2004-10-28
Yes, if a password was set, then enter the password, if not then just push enter.

---

### Post by emperor on 2004-10-28
I recommend "nfs" for share folders between native linux machines. Samba works great for Linux to windows. The "nfs" sharers must edit the "/etc/exports" file and the Share-e must mount the drive as defined in the "sharers" export file. You'll need to install "nfs" file utilities on each Linux machine too!
    
 If your UID is the same on both machines, you can read/write with no problem. In a multi-user environment you may not want everyone to be the same UID number (1000). In that case every user would be set to a different UID (1000, 1001, ...) on his machine and on the server side; in other words, a master list of username to UID would be used throughout the network. Every user would have a unique UID.
  
 I used to try and use SAMBA for both Linux and Windows machines, but there are too many "gottchas" with the "rights" thing with Samba and a Linux client.[img]http://www.ubuntuforums.org/images/smilies/eusa_wall.gif[/img]I spent too much time "trying" to force SAMBA on linux when "nfs" just works![img]http://www.ubuntuforums.org/images/smilies/icon_biggrin.gif[/img]

---

### Post by jdong on 2004-10-28
Funny thing; I've never had issues with Linux-to-Linux SAMBA. Especially with **cifs**, which supports POSIX extensions on top of smbfs! YAY

---

