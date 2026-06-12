---
title: "SSHFS Failure"
date: 2013-11-28
forum: New to Ubuntu
---

### Post by wolfenstein538 on 2013-11-28
Hello,

I want to remotely connect to an filesystem using SSHFS (same subnet). Installed SSHFS on both the machines, added the user which I use to connect to the remote computer to fuse, configured the permission on the folder I want to connect to (777) and changed the owner, yet I cannot connect to the remote folder. It keeps saying: "The folder "Foldername" cannot be opened on "xxx.xxx.xxx.xxx". What am I doing wrong?

Thanks in advance,

---

### Post by Lars Noodén on 2013-11-28
You should probably change the permissions back to 700 or 750 or 750 or something like that.  

Anyway, SSHFS is only needed on the client computer.  The remote computer needs only stock openssh-server installed and running.  If you can connect with the regular SFTP client, then you are ready to test SSHFS.

```

sftp user@server.example.org:/home/user/

``` 

If that doesn't work, you have to get it working because SSHFS uses SFTP underneath.  

If that does work, then try SSHFS.  If you plan to mount to /home/user/remote then do something like this:

```

sshfs user@server.example.org:/home/user/ /home/user/remote/

```

---

### Post by wolfenstein538 on 2013-11-28
Changed the permissions back.

Strangely I cannot connect to the server from the host using ssh [EMAIL="host@xxx.xxx.xxx.xxx(Connection"]host@xxx.xxx.xxx.xxx(Connection[/EMAIL] refused), but I can connect from the server to the host? Both the methods you described didn't work. Port 22 Connection refused" With the first one and "Missing host" by the second. Why does it display an error on port 22? I use a different port.

P.S FileZilla seems to work properly. I can upload and download files.

---

### Post by Lars Noodén on 2013-11-28
Connecting from the server to the host does not matter, because it's a different set up.  For SSHFS to work the other direction, SSH and SFTP need to work going from the client to the server.  You mention possibly using a non-standard port for SSH.  If you are not using 22 then you need to explicitly identify which port:

```

ssh -p 1234 user@server.example.org
sftp -P 1234 user@server.example.org
sshfs -p 1234 user@server.example.org:/home/user/ /home/user/somedir/

```

Note that sftp uses a capital P instead of a lowercase p.

---

### Post by Lars Noodén on 2013-11-28
FileZilla should also be using SFTP like the others.  If it falls back to FTP then that is because either by accident or on purpose you have an FTP server running on the remote host.  In most cases it is by mistake:

[http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

It is quite unsafe to have an FTP server in use, unless it is read-only, Anonymous FTP.

---

### Post by wolfenstein538 on 2013-11-28
[QUOTE=
```

ssh -p 1234 user@server.example.org
sftp -P 1234 user@server.example.org
sshfs -p 1234 user@server.example.org:/home/user/ /home/user/somedir/

```[/QUOTE]

1. Fails, Only sftp is allowed". That's because of "ForceCommand Internal-sftp" I suppose?
2. Fails, because of "Port 22: Invalid argument".
3. Fails, because of "Bad address".

---

### Post by wolfenstein538 on 2013-11-28
> **Lars Noodén said:**
> FileZilla should also be using SFTP like the others.  If it falls back to FTP then that is because either by accident or on purpose you have an FTP server running on the remote host.  In most cases it is by mistake:

[http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

It is quite unsafe to have an FTP server in use, unless it is read-only, Anonymous [FTP.]("ftp://ftp.")

I never use ftp, always sftp, because I know of the vulnerable state of ftp.

---

### Post by Lars Noodén on 2013-11-28
Yes if you have *ForceCommand* for all users (or at least your user or group) then regular ssh will fail.

The error message for #2 is strange.  What do you have in your server's /etc/ssh/sshd_config regarding *ForceCommand* or *Subsystem*?

---

### Post by Lars Noodén on 2013-11-28
> **wolfenstein538 said:**
> I never use ftp, always sftp, because I know of the vulnerable state of ftp.

Ok.  Good to hear.  Too many still use FileZilla for old FTP.

---

### Post by wolfenstein538 on 2013-11-28
> **Lars Noodén said:**
> Yes if you have *ForceCommand* for all users (or at least your user or group) then regular ssh will fail.

The error message for #2 is strange.  What do you have in your server's /etc/ssh/sshd_config regarding *ForceCommand* or *Subsystem*?

Regarding to ForceCommand, I only have "ForceCommand internal-sftp"
Regarding to Subystem, I have "Subsystem sftp internal-sftp"

I don't understand why it keeps refering to port 22? I changed it on both sides (host and server) and yet it is complaining about it.

P.S
Additional information regardering error 2:
2. Fails, because of "Port 22: Invalid argument
 Couldn't read packet, connection reset by peer.

---

### Post by Lars Noodén on 2013-11-28
Ok.  Those two configuration options look all right.

Where is it referring to port 22 still?  Can you post what the verbose output is from sftp so we can see the exact error?

```

sftp -v -P 1234 user@server.example.org

```

---

