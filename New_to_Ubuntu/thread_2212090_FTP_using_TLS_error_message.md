---
title: "FTP using TLS error message"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by sniper8752 on 2014-03-19
I am using Filezilla to connect to my server, and get this error message:
```
Error:    GnuTLS error -15: An unexpected TLS packet was received.
Error:    Could not connect to server
```
Here is my sshd_config file:
```
# Package generated configuration file# See the sshd_config(5) manpage for details


# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes
AllowUsers bob
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
#AuthorizedKeysFile    %h/.ssh/authorized_keys


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


X11Forwarding no
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no


#MaxStartups 10:30:60
Banner /etc/issue.net


# Allow client to pass locale environment variables
AcceptEnv LANG LC_*


Subsystem sftp internal-sftp -f AUTH -l VERBOSE


# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
#UsePAM yes # Started commenting out here
#AllowGroups sftpusers sftp
#Match Group sftpusers
#    ChrootDirectory %h
#    AllowTCPForwarding no
#ForceCOmmand internal-sftp


# also added by me...
# ClientAliveInterval 300
# ClientAliveCountMax 0



```

---

### Post by Lars Noodén on 2014-03-19
Are you connecting on port 22?  That's the port for SSH and SFTP runs over SSH.  Try connecting on port 22 with FileZilla and if you can then you can probably remove the FTP server and just stick with SFTP/SSH.  

FTPS is something different.  That is FTP over TLS or SSL.  If you have SFTP already then you probably don't need or want FTPS and can remove it.

---

### Post by sniper8752 on 2014-03-19
When I changed it to port 22 I got this error message:
```
Response:	SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1Error:	Cannot establish FTP connection to an SFTP server. Please select proper protocol.
Error:	Critical error
Error:	Could not connect to server
```

---

### Post by Lars Noodén on 2014-03-19
It looks like it is still trying FTP instead of SFTP.  Are you using Quick Connect?  

If so then you can try temporarily disabling the FTP server and try reconnecting.  It should find the SSH server then.

Or in Filezilla,  File->Site Manager->New Site->Protocol SFTP, etc.

---

### Post by sniper8752 on 2014-03-19
ah, it worked.  thought I did that before, but thanks!

---

