---
title: "Setting up OpenSSH with RSA keys"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by kwinsw on 2012-03-31
Hi,

I'm running Ubuntu server, mainly just as a file server at the moment. I want to move to remote administration (so my son can have the monitor when we get around to buying a Raspberry Pi).

I've OpenSSH working fine - I can log on remotely. But I want to use public and private keys as [described here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Where_to_From_Here.3F"). 

Possibly it's my lack of experience, but that page just seems to tell me how to generate the keys. Not how to use them with OpenSSH.


I want to be able to connect to my server, using OpenSSH via PuTTY from a Windows 7 client. Can anyone tell me how to implement the public and private keys with this setup? Or point me in the direction of a good how-to?

Any and all advice greatly appreciated.

Cheers

KW

---

### Post by winh8r on 2012-03-31
This might be of some use to you:

[http://www.linux-sxs.org/networking/openssh.putty.html]("http://www.linux-sxs.org/networking/openssh.putty.html")

Hope it helps

---

### Post by haqking on 2012-03-31
> **kwinsw said:**
> Hi,

I'm running Ubuntu server, mainly just as a file server at the moment. I want to move to remote administration (so my son can have the monitor when we get around to buying a Raspberry Pi).

I've OpenSSH working fine - I can log on remotely. But I want to use public and private keys as [described here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Where_to_From_Here.3F"). 

Possibly it's my lack of experience, but that page just seems to tell me how to generate the keys. Not how to use them with OpenSSH.


I want to be able to connect to my server, using OpenSSH via PuTTY from a Windows 7 client. Can anyone tell me how to implement the public and private keys with this setup? Or point me in the direction of a good how-to?

Any and all advice greatly appreciated.

Cheers

KW


That guide is all you need, it tells you how to generate them , copy them to client and login using them.

If it prompts you for password there is a problem usually to do with sshd_config, if it prompts you for passphrase you are using a key.

Thats it.

---

### Post by kwinsw on 2012-04-01
Hi,

Thank you for the help so far. I&#8217;ve tried it and I&#8217;m still a bit stuck. So far I have:

1. Generated the public and private keys using the commands,

mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa

This has left me with the files id_rsa and id_rsa.pub in the directory ~/.ssh . However, there the directory didn&#8217;t contain any file called authorized_keys.

2. So, I created authorized_keys using the following steps:

mkdir -p ~/.ssh
 	touch ~/.ssh/authorized_keys

3. Once this was done, I copied the contents of id_rsa.pub to authorized_keys using the command:

cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys

I opened authorized_keys in the nano text editor to make sure it they public key had been copied over successfully. It had.

4. Once this was done, I needed to copy the id_rsa file over to my local host (a Windows 7 PC) in order to make the connection. This was a bit difficult, as only the root account had rights to the file. 

So I changed the access privileges using the command:

	chmod 754 id_rsa

5. With this done, I copied the file over to my Windows PC and used puttygen to turn into something that PuTTY could work with. 

But still when I connect to server using OpenSSH I am not prompted for my passkey. If someone could tell me what I&#8217;m doing wrong, I&#8217;d really appreciate it. I&#8217;ve copied the contents of sshd_config below. 

Many thanks

KW

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

# 

Logging

SyslogFacility AUTH

LogLevel INFO



# Authentication:

LoginGraceTime 120

PermitRootLogin yes

StrictModes yes



RSAAuthentication yes

PubkeyAuthentication yes

AuthorizedKeysFile	~/ssh/%u/authorized_keys

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

# 

Change to yes to enable challenge-response passwords (beware issues with

# some PAM modules and threads)
ChallengeResponseAuthentication no



# Change to no to disable tunnelled clear text passwords

#PasswordAuthentication yes



# Kerberos options
#
KerberosAuthentication no

#KerberosGetAFSToken no

#KerberosOrLocalPasswd yes

#KerberosTicketCleanup yes



# GSSAPI options

#GSSAPIAuthentication no

#GSSAPICleanupCredentials yes



X11Forwarding yes

X11DisplayOffset 1
0
PrintMotd no

PrintLastLog yes
TCPKeepAlive yes

#UseLogin no



#MaxStartups 10:30:60

#Banner /etc/issue.net



# Allow client to pass locale environment variables

AcceptEnv LANG LC_*



Subsystem sftp /usr/lib/openssh/sftp-server



# Set this to 'yes' to enable PAM authentication, account processing,

# and session processing. If this is enabled, PAM authentication will

# be allowed through the ChallengeResponseAuthentication and

# PasswordAuthentication.  Depending on your PAM configuration,

# PAM authentication via ChallengeResponseAuthentication may bypass

# the setting of "PermitRootLogin without-password".

# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication

# and ChallengeResponseAuthentication to 'no'.

UsePAM yes

---

### Post by kwinsw on 2012-04-01
Got it:

1. Moved authorized_keys out of the home directory
2. Changed password authentication to "no" and uncommented that line (I thought I had done this, but clearly not)

Thank you winh8r and haqking.

---

### Post by haqking on 2012-04-01
> **kwinsw said:**
> Got it:

1. Moved authorized_keys out of the home directory
2. Changed password authentication to "no" and uncommented that line (I thought I had done this, but clearly not)

Thank you winh8r and haqking.

You are welcome

sorry i didnt respond earlier, glad you got it sorted.

---

