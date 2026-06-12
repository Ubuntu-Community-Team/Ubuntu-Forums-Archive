---
title: "Filezilla FTP Error with PAM"
date: 2014-03-24
forum: New to Ubuntu
---

### Post by sniper8752 on 2014-03-24
When I add the following lines to my sshd_config file, I get a "network error: software caused connection abort" in Filezilla.  When I remove these lines, it works fine.  But the user can go outside of their directory.
Code:
```
AllowGroups sftpusers sftp
Match Group sftpusers
ChrooDirectory %h
AllowTCPForwarding no
ForceCommand internal-sftp

```
My users are part of the sftpusers group.
Any ideas as to why it isn't working?

---

### Post by sniper8752 on 2014-03-24
Yes, sorry.  Thanks.

---

### Post by Iowan on 2014-03-24
> **sniper8752 said:**
> 
```
AllowGroups sftpusers sftp
Match Group sftpusers
Chroo[COLOR="#FF0000"]t[/COLOR]Directory %h
AllowTCPForwarding no
ForceCommand internal-sftp

```
?Typo?

---

### Post by sniper8752 on 2014-03-25
Anybody have any ideas?

---

### Post by steeldriver on 2014-03-25
Wouldn't that be sftp rather than ftp?

Haven't we be around this before?

[http://ubuntuforums.org/showthread.php?t=2211154](http://ubuntuforums.org/showthread.php?t=2211154)

[http://ubuntuforums.org/showthread.php?t=2208476](http://ubuntuforums.org/showthread.php?t=2208476)

What has changed since those previous threads?

---

### Post by sniper8752 on 2014-03-25
Not sure - [http://www.techrepublic.com/blog/linux-and-open-source/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/](http://www.techrepublic.com/blog/linux-and-open-source/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/).  How would I limit a user to their home directory?
I updated [http://ubuntuforums.org/showthread.php?t=2208476&page=3&p=12968011#post12968011](http://ubuntuforums.org/showthread.php?t=2208476&page=3&p=12968011#post12968011).

---

