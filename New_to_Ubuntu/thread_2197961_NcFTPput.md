---
title: "NcFTPput"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2014-01-06
Hi Guys,

I found that I can upload files to the server at my hosting company via a script using ncftpput.
Does anyone have experience with this program?
I read in the documentation that I can use a configuration file to specify my login credentials.
This works, but my question is even if ncftpput gets my user name and a password from a file that only I can access on my local machine, is that information still "visible" by anyone sniffing packets on the internet?

---

### Post by efflandt on 2014-01-06
Yes ftp (or telnet) is not encrypted, so passwords would go through the internet as plain text.

If you have **ssh** access to the server, **scp** or **sftp** would be much more secure, because they would all be encrypted. With ssh compression enabled in your ~/.ssh/config, scp or sftp may even be faster than ftp, despite encryption. While sftp in a text terminal looks similar to regular text ftp, for a graphic interface you could use the file manager in Ubuntu. File > Connect to Server..., and if you select SSH it would securely view and copy files to or from the server just like copying files around your hard drive.

For scripting you could use **scp**, although, you may need to use keys without a password with only the public key in ~/.ssh/authorized_keys on the server (make sure that any keys put into that file do NOT wordwrap). Note that ~/.ssh/ on any computer (client or server) should have 700 permission (drwx------) and any files in that dir should have 600 permission (-rw-------). This explains ssh keys [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by GrouchyGaijin on 2014-01-06
Thank you for the reply.  That is what I pretty much thought.
The thing is I have a really difficult time with ssh keys.
It didn't always used to be this way, once upon a time everything worked as it should.
Starting a few weeks ago, I started getting permission denied (Publickey) errors when trying to securely connect to the server.
The only thing I've found to stop the error, at least until the next reboot, is to run ssh-add and readd my key.
The key is in ~/.ssh and the directory is drwx------ 
The files in the directory are -rw-------

I don't know what the problem is, but it is really frustrating.  My hosting company's solution is to use Filezilla, which I have set to use my private key.
The thing is, I really want to upload from a script.

---

