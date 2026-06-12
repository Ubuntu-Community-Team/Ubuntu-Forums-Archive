---
title: "Creating directories. Putty mkdir OK, WinSCP not."
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Swerve1000 on 2008-11-17
Hi,

I have just installed Ubuntu Server Edition, the services I installed during installation are:

OpenSSH
LAMP

I then changed the SSH port from 22 to another one in the 

/etc/ssh/sshd_config

file only, using nano and then rebooted the server.

From my Windows box I can login to the server using Putty and also create directories using:

sudo mkdir directoryname

However when I use WinSCP, I can login and view all the files and directories, using the port number I chose for SSH connections, but when I try to create a new file or directory, I get permission denied.

I'm using the same login details as I use for Putty. WinSCP says I am using SFTP.

How can I fix this issue?

Many thanks for any help, it's greatly appreciated!

---

### Post by karlr42 on 2008-11-17
Probably because you used sudo to mkdir, so they are owned by root, then you log into the box as non-root, hence "permission denied".

---

### Post by Swerve1000 on 2008-11-17
> **karlr42 said:**
> Probably because you used sudo to mkdir, so they are owned by root, then you log into the box as non-root, hence "permission denied".

Thanks karlr42!

So I just logged into the server with Putty using the account created during installation and used the command

mkdir directoryname

without the prefix 'sudo' and it was successful.

I then logged out, and logged back in again with WinSCP and was able to create the directory.

So am I correct in saying whoever creates the directory, can r/w/x within it, because they 'own' it/created it?

Hence why access to Ubuntu's root account is protected?

---

### Post by karlr42 on 2008-11-17
> **Swerve1000 said:**
> Thanks karlr42!

So I just logged into the server with Putty using the account created during installation and used the command

mkdir directoryname

without the prefix 'sudo' and it was successful.

I then logged out, and logged back in again with WinSCP and was able to create the directory.

So am I correct in saying whoever creates the directory, can r/w/x within it, because they 'own' it/created it?

Hence why access to Ubuntu's root account is protected?
Exactly, and you'll see all the important files are owned by root, so a normal user can't edit them. Unless they use sudo, which forces them to think "this might be dangerous". I believe that's the theory, anyway.

---

