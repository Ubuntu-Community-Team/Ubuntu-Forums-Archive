---
title: "Accessing file via openssh"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by mtotton on 2012-03-28
Hi,

I have ubuntu 11.10 and want to allow some friends to access a couple of directories remotely. I have set up openssh, and using Filezilla from Windows 7 to access the server. When testing (locally) I found that the user account gives unrestricted access to the machine! I can't seem to restrict the access. Obviously I have done something fundamentally wrong, but I can't find any help via google and it is driving me mad. Can anyone point me in the right direction? (I have not enable public/private keys yet).
The user I am testing with is not admin, it is just a normal user

Thanks
Mark

---

### Post by dfreer on 2012-03-28
The newest version of openssh has built-in chroot functionality to restrict SFTP users to their home directory. This would keep them out of other parts of the filesystem. You would have to turn it on in the config options.

As for unrestricted access, most of the files and directories in the filesystem allow users to read from the files, and SSH honors filesystem permissions. Check and verify that the normal user you logged in with cannot look at or download /etc/shadow (which by default does not allow the world to read it since it contains the encrypted password hashes). 

If they can, post the contents of your /etc/ssh/sshd_config file and also the output of the following command:
```
ls -l /etc/shadow
```

If they cannot read the file, then SSH should be working normally. If you don't want your remote users poking around, either use chroot to bind them to their home directories or set more restrictive permissions on folders you want to keep them out of (be careful you don't break any programs!).

P.S. Note that if they can SFTP in, they likely can SSH in as well which is bad. You will need to either disable their login shells in /etc/passwd by changing them to /bin/false or /sbin/nologin (which may break SFTP so test first), or edit your /etc/ssh/sshd_config to disallow shell SSH access and only SFTP access (not sure if possible).

---

### Post by MG&amp;TL on 2012-03-28
That is very bad. When you say 'unrestricted access'-they can access things that aren't in $HOME? (their homefolder) Or just things they are not supposed to elsewhere in the user's homefolder?

---

