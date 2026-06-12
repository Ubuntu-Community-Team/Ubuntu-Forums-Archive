---
title: "chroot lock"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by sniper8752 on 2013-05-08
what is the easiest way to do a chroot lock for a user?  i am using vsftpd, and don't want the user to be able to traverse out of their home directory.

Update: I tried the first two parts of this tutorial:

[http://www.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229](http://www.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229)


Subsystem     sftp   internal-sftp
Match Group sftp
    ChrootDirectory %h
    ForceCommand internal-sftp
    AllowTcpForwarding no
# usermod -G sftp joe
# usermod -s /bin/false joe
# chown root:root /home/joe
# chmod 0755 /home/joe
I login with the user and password in filezilla.  I get this:

Error:    Connection closed by server with exitcode 1
Error:    Could not connect to server

I login to the account via the terminal, and it shows me the motd, and then asks me for my login information again.  I checked the /home/username file, and I only saw one file.  Why would it be doing this?

Also, how do I block users from using vsftpd, like a root user account?  I tried this:


Match User bob
Subsystem   sftp  /bin/falsein /etc/ssh/sshd_config

but I am still able to use sftp using filezilla with this user.  (source: [URL="http://serverfault.com/questions/290843/how-to-disable-sftp-for-some-users-but-keep-ssh-enabled"]http://serverfault.com/questions/290843/how-to-disable-sftp-for-some-users-but-keep-ssh-enabled)
[/URL][COLOR=#222222][FONT=Verdana]
Also, am I on the right track, with this?[/FONT][/COLOR]

---

