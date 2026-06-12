---
title: "restrictive ssh problem (ForceCommand, ChrootDirectory): Write failed: Broken pipe"
date: 2010-05-13
forum: Programming Talk
---

### Post by Eugene_Bondarenko on 2010-05-13
Hi, 

I want to set up a restrictive ssh account which will not allow user to leave his home folder. I've read some manuals and decided to follow ForceCommand/ChrootDirectory way. Here is my current ssh config file

/etc/ssh/sshd_config
```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem       sftp    internal-sftp

UsePAM yes

Match user igor
    ForceCommand internal-sftp
    ChrootDirectory /home/igor

```


And these are permissions of the folder where I chroot the user
```

drwxr-xr-x  4 igor    igor        4096 2010-05-13 11:59 igor

```

And finally that's the output I get for sftp:
```

eugene@eugene-desktop:/home$ sftp igor@localhost
Connecting to localhost...
igor@localhost's password: 
Write failed: Broken pipe
Couldn't read packet: Connection reset by peer

```

and here is verbose ssh:
```

eugene@eugene-desktop:/home$ ssh -vvv igor@localhost
OpenSSH_5.3p1 Debian-3ubuntu3, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
...
debug1: Next authentication method: password
igor@localhost's password: 
debug3: packet_send2: adding 64 (len 55 padlen 9 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug3: Wrote 144 bytes for a total of 2487
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug3: Wrote 128 bytes for a total of 2615
debug3: Wrote -1 bytes for a total of 2615
Write failed: Broken pipe

```


I am totally lost about this issue, please let me know if you have any ideas about what I can try to fix or debug this further.

---

### Post by rockorequin on 2010-08-09
See the last bit of [http://wiki.archlinux.org/index.php/SFTP-chroot](http://wiki.archlinux.org/index.php/SFTP-chroot). You get a broken pipe error after logging in if the home folder is not owned by root (in fact the chain of folders leading down to it must be owned by root) or if it has write permissions for 'group' or 'other'.

The openssh server in Ubuntu 9.10 didn't have this restriction but the one in Lucid does.

There is some discussion as to why here:

* [http://lists.mindrot.org/pipermail/openssh-unix-dev/2009-May/027651.html](http://lists.mindrot.org/pipermail/openssh-unix-dev/2009-May/027651.html)

* [https://bugzilla.redhat.com/show_bug.cgi?id=522141](https://bugzilla.redhat.com/show_bug.cgi?id=522141)

although it does seem that there is only a problem if you allow ssh access for chroot'd users - if you allow sftp-only access by setting the user's shell to /bin/false, I don't think the security problem would exist.

---

### Post by narcisgarcia on 2010-10-03
Note that the owner of the destination directory must be "root", and group/other users cannot have write permissions. The same with all the directory path:
```

chown root /path/to/destination
chown root /path/to
chown root /path

chmod g-w,o-w /path/to/destination
chmod g-w,o-w /path/to
chmod g-w,o-w /path

```

Alternatively, you can use a symbolic link to replace the real path:
```

chown root /path/to/destination
ln -s /path/to/destination /destination
chown root /destination

chmod g-w,o-w /path/to/destination
chmod g-w,o-w /destination

```

---

### Post by foguinho.peruca on 2010-11-17
Hi!

I got this problem too. I am using ubuntu 10.04. Someone know any workaround for it?

Thanks
Jeff

---

### Post by narcisgarcia on 2010-11-17
After learning from a lot of tutorials, here my compendium for optimal configuration in both clients and servers:

[http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses](http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses)

(special care of users and permissions)

---

