---
title: "SSH Authorized keys"
date: 2015-10-27
forum: New to Ubuntu
---

### Post by eddiefiggie on 2015-10-27
I am using Ubuntu 14.x LTS desktop as my SSH Server/Host.  Mostly just tinkering with it so to learn and understand its uses.  I'm fascinated so far!  Then I'm attempting to connect to it over my LAN from my laptop (Linux based OS).  I was able to connect with basic password authentication with no problem.  I was also, from my laptop (client), able to create the key and move the key manually to the HOST with:
```

scp ~/.ssh/id_dsa.pub username@somethinglocal:.ssh/authorized_keys
```

I then set the CHMOD rights as follows:

```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

Then I adjusted my sshd_config file like this:

```
# Package generated configuration file
# See the sshd_config(5) manpage for details

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
HostKey /etc/ssh/ssh_host_ed25519_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 1024

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 30
PermitRootLogin without-password
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile    %h/.ssh/authorized_keys

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
PasswordAuthentication no

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

#MaxStartups 2:30:10
Banner /etc/issue.net

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

```

Followed up with:

```
sudo restart ssh
```

Now, I'd love to send you the log, but I may have broke that.  =P  in an attempt to find the action where I log in and get denied, I selected all the text and deleted it.  Then saved the file.  Ever since, it hasn't added new messages to the log file.  At least the last time I checked.

But in a nut shell, when I try and connect now, I am simply [SIZE=3]**Permission Denied (publickey)**[/SIZE].

Can someone help?!  =)

---

### Post by Lars Noodén on 2015-10-27
You can get some of the details by increasing the verbosity of your client.

```

ssh -vv ~/.ssh/id_dsa username@somethinglocal

```

But it sounds like the solution will include the initial step of turning passwords back on until you get the keys sorted.  You might consider using RSA, ECDSA or Ed25519 instead of DSA.  From what I gather, DSA is on the way out because it is now considered weak.

---

### Post by tgalati4 on 2015-10-27
I use *seahorse* to manage my keys.  It seems to perform all the correct steps.  Yes, leave passwords turned on until you have it sorted out, because if there is a problem, you will get a denial message, then the password query will show up, so at least you are not locked out.

If you do use this for outside (WAN) access, you will want to set up port knocking that redirects some high number port to port 22.  Don't leave port 22 open on a WAN.

---

### Post by jim_deadlock on 2015-10-28
```
sudo restart ssh
```

That doesn't look right, try this instead:

```
sudo service sshd restart
```

---

### Post by watchpocket on 2015-10-29
> **tgalati4 said:**
> I use *seahorse* to manage my keys.

I'm also using Seahorse, on Ubuntu-MATE 14.04 LTS.  But Seahorse does not recognize or otherwise work with ed25519 ssh keys.  

Is there perhaps a newer version of Seahorse that that can be installed on Trusty and that *does* work with ed25519 keys?

Or, in the absence of an ed25519-accommodating Seahorse, would anyone know a good agent that handles the ed25519 key format and can be used instead that might be available from synaptic or a PPA?

---

### Post by tgalati4 on 2015-10-29
I was under the impression that 14.04 had the latest ssh (Version 6.6) and support for ed25519 was added in 6.5 according to:  
[http://chneukirchen.org/blog/archive/2014/02/the-road-to-openssh-bliss-ed25519-and-the-identitypersist-patch.html](http://chneukirchen.org/blog/archive/2014/02/the-road-to-openssh-bliss-ed25519-and-the-identitypersist-patch.html)

> 

  tgalati4@Mint17 ~ $ apt-cache policy openssh-client
openssh-client:
  Installed: 1:6.6p1-2ubuntu2.3
  Candidate: 1:6.6p1-2ubuntu2.3
  Version table:
 *** 1:6.6p1-2ubuntu2.3 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:6.6p1-2ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages



It's not clear to me why the cypher method would affect *seahorse*, since it is just managing the keys supported by the version of ssh that you are running.  Apparently the current version of *seahorse* [can't create ed25519 keys]("https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/1420522"), so you will have to manually create them.  

I use really, really large RSA keys with my servers, haven't used ed25519 keys yet; perhaps it is time to ratchet up security.

---

### Post by watchpocket on 2015-10-29
OpenSSH itself is at version 7.1.  I don't know if 7.1 can be installed  on Trusty or if you need the newest Ubuntu for 7.1.  I'm currently  running 6.6 on Trusty.  (I'd love to put 7.1 on Trusty but only if  that's a safe thing to do, only if there's no reason not to.)  

Yes, ssh supports ed25519, ssh is  not the problem.  But have you tried to save an already-created ed25519  key in seahorse?  It only handles dsa & rsa, as far as I can tell --  unless I'm dong something wrong.  I'd like a seahorse (or something  like seahorse) that can accommodate ed25519 ssh keys.

(btw, how  big is a really, really big RSA key?  4096-bit?  That's the size I've  generally been using, but I'd like to move all my keys to ed25519.)

---

