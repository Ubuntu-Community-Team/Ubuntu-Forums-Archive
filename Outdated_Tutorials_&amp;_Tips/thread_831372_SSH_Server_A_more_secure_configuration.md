---
title: "SSH Server: A more secure configuration"
date: 2008-06-16
forum: Outdated Tutorials &amp; Tips
---

### Post by gaten on 2008-06-16
[SIZE=3][B][SIZE=2]by gaten guess: gaten [dot] net [at] gmail [dot] com[/SIZE]
[/B][/SIZE]

I personally believe that SSH is the best thing since sliced bread. It's easy to use, easy to setup, reliable encrypted internet traffic. That's hard to come by. What could be better, you ask? A more secure configuration.

The default sshd_config that ships with Ubuntu is fairly secure, but we can make it a lot better, so that's what we're going to do.

This guide assumes a few things:[INDENT]1. You understand the basics of the ssh server. If you don't, here's some reading material:

[LIST]
[*][COLOR=Blue]Ubuntu SSH Documentation:[/COLOR] [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[/LIST]

[LIST]
[*][COLOR=Blue]OpenSSH[/COLOR]: [http://www.openssh.org/](http://www.openssh.org/)
[/LIST]

[LIST]
[*][COLOR=Blue]Wikipedia Entry:[/COLOR] [http://en.wikipedia.org/wiki/Secure_Shell/]("http://en.wikipedia.org/wiki/Secure_Shell")
[/LIST]
2. You are comfortable editing config files and using the command line. No GUIs here.

3. You've updated sshd and your keys, and have used **ssh-vulnkey **(and others) to make sure your keys do not belong to the vulnerable set. See [http://www.ubuntu.com/usn/usn-612-2](http://www.ubuntu.com/usn/usn-612-2)

4. You have your public and private key system already set up. If you restart your sshd server with the configuration below and do not have your keys in place, you will not be able to login remotely. If you need help setting this up, see:  [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

5. You understand that these are my *personal* recommendations for security. If you disagree and/or have an improvement, please let me know!

[/INDENT]On with the tutorial!


For the impatient, here's the complete sshd_config
```
# user modified sshd_config
# See the sshd(8) manpage for details

#### Networking options ####

# Listen on a non-standard port > 1024
Port 50000

# Restrict to IPv4. inet = IPv4, inet6 = IPv6, any = both 
AddressFamily inet

# Listen only on the internal network address
ListenAddress 192.168.1.0

# Only use protocol version 2
Protocol 2

# Disable XForwarding unless you need it
X11Forwarding no

# Disable TCPKeepAlive and use ClientAliveInterval instead to prevent TCP Spoofing attacks
TCPKeepAlive no
ClientAliveInterval 600
ClientAliveCountMax 3

#### Networking options ####


#### Key Configuration ####

# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key

#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Use public key authentication
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys

# Disable black listed key usage (update your keys!)
PermitBlacklistedKeys no

#### Key Configuration ####


#### Authentication ####

# Whitelist allowed users
AllowUsers user1 user2

# one minute to enter your key passphrase
LoginGraceTime 60

# No root login
PermitRootLogin no

# Force permissions checks on keyfiles and directories
StrictModes yes

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes

# similar for protocol version 2
HostbasedAuthentication no

# Don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Disable challenge and response auth. Unessisary when using keys
ChallengeResponseAuthentication no

# Disable the use of passwords completly, only use public/private keys
PasswordAuthentication no

# Using keys, no need for PAM. Also allows SSHD to be run as a non-root user
UsePAM no

# Don't use login(1)
UseLogin no

#### Authentication ####


#### Misc ####

# Logging
SyslogFacility AUTH
LogLevel INFO

# Print the last time the user logged in
PrintLastLog yes

MaxAuthTries 2

MaxStartups 10:30:60

# Display login banner
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

#### Misc ####

```[LEFT]Now we'll go through it, section by section.



[/LEFT]
[CENTER][SIZE=3][COLOR=Red][B]#### Networking Options ####

[/B][/COLOR][/SIZE][/CENTER]
**Port 5000**

[LIST]
[*]Using something other than the default port (22) for the ssh server can help avoid attacks by script kiddies. I can't tell you how many attempts per day my IDS picks up attacking port 22. Some might argue that security by obscurity is a bad idea, but I think it works in this case (so does my IDS).
[/LIST]

**AddressFamily inet**

[LIST]
[*]Specifically limit traffic to IPv4. I don't use IPv6, so I see no reason to allow ssh to run over it. I've also disabled IPv6 on all my computers, so using it for ssh would be pointless. You're also limiting the attack vectors, which is always a good thing.
[/LIST]

**ListenAddress 192.168.1.0**

[LIST]
[*]Only listen to the internal address. An entry like **ListenAddress 0.0.0.0 **means listen on all interfaces, including external ones. With our entry, we're only listening on internal addresses and the server cannot be accessed from the internet unless you set up port forwarding on your router/computer. It's just an extra layer of precaution, and defense in depth is the name of the game.
[/LIST]

[B]Protocol 2
[/B]
[LIST]
[*]Force protocol version 2. This is the default entry on Ubuntu, and there is no reason to use version 1, due to the security vulnerabilities discovered with it.
[/LIST]

[B]X11Forwarding no
[/B]
[LIST]
[*]Disable X forwarding. I use VNC tunneled over ssh if I need to see my desktop, so I have no need of X forwarding. Please note that disabling this option may break some services, such as LSTP ([http://www.ltsp.org/](http://www.ltsp.org/)).
[/LIST]

[B]TCPKeepAlive no
[/B]
[LIST]
[*]Disable TCP KeepAlive messages. These messages are spoofable and are sent outside of the encrypted channel, and **ClientAliveInterval **is an encrypted, unspoofable (that I know of) alternative, so I see no reason to use **TCPKeepAlive.**
[/LIST]

[B]ClientAliveInterval 60
[/B]
[LIST]
[*]The secure alternative to **TCPKeepAlive. **60 means after 60 seconds, the sshd server will send a message to the client expecting a response.
[/LIST]

**ClientAliveCountMax 3**

[LIST]
[*]The number of times the sshd server will attempt to illicit a response from the ssh client before disconnecting it. Using our configuration, an unresponsive ssh client will be disconnected after 3 minutes (**ClientAliveCountMax * ****ClientAliveInterval**).
[/LIST]


[CENTER] [SIZE=3][COLOR=Red]**#### Key Configuration ####**[/COLOR][/SIZE]
[/CENTER]

[B]HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
[/B]
[LIST]
[*]RSA and DSA host (server) keys. This is the Ubuntu default
[/LIST]

[B]UsePrivilegeSeparation yes
[/B]
[LIST]
[*]Splits up server processes in an attempt to prevent privilege escalation exploits.
[/LIST]

[B]PubkeyAuthentication yes
[/B]
[LIST]
[*]Use public key authentication. In my opinion this option, combined with the **PasswordAuthentication no** option is the most important security enhancement you can make to your ssh server. When you disable password authentication and enable this option, the user will be required to have his or her public key stored on the server, and will need their private key (and passphrase for that key) in order to login. Using this combination will reduce script kiddy attacks tremendously, and brute for password attacks completely. Now an attack will have to brute force the key, which is almost impossible (in theory).
[/LIST]

[B]AuthorizedKeysFile      %h/.ssh/authorized_keys
[/B]
[LIST]
[*]The default public key file for the user.
[/LIST]

**PermitBlacklistedKeys no**

[LIST]
[*]Don't allow black listed keys to be used to login to the server. Due to the recent Debian/Ubutu ssh vulnerability, I see no reason not to enable this.
[/LIST]


[CENTER][B][SIZE=3][COLOR=Red] #### Authentication ####[/COLOR][/SIZE]
[/B][/CENTER]

**AllowUsers user1 user2**

[LIST]
[*]White list the users you want to allow to login to your system. This is a space separated list, in this case **user1** and **user2** are the only users allowed to login to the ssh server. Black lists are a stupid idea and should be avoided if at all possible.
[/LIST]

[B][COLOR=Black]LoginGraceTime 60
[/COLOR][/B]
[LIST]
[*]The number of seconds the user has to login to the system once prompted. I don't have such a long passphrase that I can't type it in a minute!
[/LIST]

 **PermitRootLogin no**

[LIST]
[*]Disable root logins completely. Ubuntu's root account is locked by default, but I don't care. I see no reason that you would need to login as root, or even why this needs to be enabled by default. Create a normal user account and give it sudo privileges.
[/LIST]

 [B]StrictModes yes
[/B]
[LIST]
[*]Require that users set the correct permissions on their key files and the directories that they are stored in. In order for keys to pass strict mode, they must not be writable by anyone but the owner. I'd suggest a chmod of 600 for the keyfile.
[/LIST]

[B]IgnoreRhosts yes
[/B]
[LIST]
[*]Ignore Rhosts authentication for .rhosts and .shosts files in RhostsRSAAuthentication or HostbasedAuthentication. /etc/hosts.equiv is still used if the **HostbasedAuthentication** option is not disabled.
[/LIST]

**HostbasedAuthentication no**

[LIST]
[*]Decides if rhosts or /etc/hosts.equiv and a public key are allowed (host-based authentication). We're relying on public keys only.
[/LIST]

 [B]IgnoreUserKnownHosts yes
[/B]
[LIST]
[*]Decide whether the server should ignore the users ~/.ssh/known_hosts during Host based or Rhost authentication. As we're disabling both, there is no reason to enable known_host authentication.
[/LIST]

[B]PermitEmptyPasswords no
[/B]
[LIST]
[*]Do not allow empty passwords. If they want to get into your system, they'll need a key with a password.
[/LIST]

 [B] ChallengeResponseAuthentication no
[/B]
[LIST]
[*]Disable challenger response authentication. We're not using login(1) or password authentication, so there's no reason to set it.
[/LIST]

   ** PasswordAuthentication no**

[LIST]
[*]As stated in the key section, this is a very important option. By disabling password authentication, you will require the user to have a public key on the system to login. This will eliminate brute force dictionary password attacks. This of course means you will need to transfer the keys to the system before hand, or you will lock yourself out of your system.
[/LIST]

 [B]UsePAM no
[/B]
[LIST]
[*]We're not using password authentication, so we don't need to use PAM. Also, this will allow sshd to run as an unprivileged user.
[/LIST]

 [B]UseLogin no
[/B]
[LIST]
[*]Don't use the traditional login(1) service to log in users. Because we are using privilege separation, as soon as the user logs in ths login(1) service is disabled.
[/LIST]


[CENTER] **[SIZE=3][COLOR=Red]#### Misc ####[/COLOR][/SIZE]**

[/CENTER]
[B] 
SyslogFacility AUTH
[/B]
[LIST]
[*]Log sshd messages to the AUTH syslog facility, which stores its messages in **/var/log/auth.log** by default in Ubunutu. The following command should print you out a list of sshd messages contained in that file:```
 grep sshd /var/log/auth.log
```
[/LIST]

[B] LogLevel INFO
[/B]
[LIST]
[*]Defines what verbosity level to use for login. Available options are (removing redundant options): SILENT, QUIET, FATAL, ERROR, INFO, VERBOSE, DEBUG, DEBUG2, and DEBUG3. INFO is the default.
[/LIST]

[B] PrintLastLog yes
[/B]
[LIST]
[*]When the user logs into the system, print the last time they logged in. If you see a time or date that you don't remember logging in, time to do some checking!
[/LIST]

**MaxAuthTries 2** 

[LIST]
[*]Maximum times a user can attempt to login per connection. Failures are logged after half the number is reached.
[/LIST]

[B] MaxStartups 10:30:60
[/B]
[LIST]
[*]Specifies the maximum number of concurrent unauthenticated connections to the SSH daemon (the number of users still logging in). See the man page for more info.
[/LIST]

[B]  Banner /etc/issue.net
[/B]
[LIST]
[*]Message to display when a user logins in. You may want to replace the standard Ubuntu issue.net with something warning people that only authorized users are allowed in the system. Some people claim this can help in prosecuting people who break into your systems, but I have no idea if that's viable advice or not. At the least make it look cooler than the default ;)
[/LIST]

[B] AcceptEnv LANG LC_*
[/B]
[LIST]
[*]Which environmental variables to accept from the client. As mentioned in the sshd_config man page, take care which variables to accept. These are the Ubuntu defaults.
[/LIST]

[B] Subsystem sftp /usr/lib/openssh/sftp-server
[/B]
[LIST]
[*]External file transfer daemon to use for sftp requests. This is the Ubuntu default.
[/LIST]

** In summary, we've changed the following:**

[LIST=1]
[*]Disabled any authentication but key authentication
[*]Disabled X Forwarding
[*]Disabled unencrypted KeepAlive messages
[*]Disabled the use of Black listed keys
[*]Disabled root logins of any kind
[*]Changed the port the server listens on
[*]Forced the server to listen to only the internal network interface
[/LIST]
In general, I'd say we have a pretty secure ssh server. Any comments, corrections or suggestions? Please PM me on here or email me: **gaten [dot] net [at] gmail [dot] com.**

Here's some further reading material on the subject. I've pulled heavily from these sources for this tutorial.[INDENT] [COLOR=Blue]Ubuntu Advanced SSH Server Guide:[/COLOR] [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

[COLOR=Blue]Debian "Secure SSH" article:[/COLOR] [http://www.debian-administration.org/articles/455](http://www.debian-administration.org/articles/455)

[COLOR=Blue]The Ultimate SSH Security Tutorial: [/COLOR]
[http://tuxtraining.com/2008/05/14/the-ultimate-ssh-security-tutorial/](http://tuxtraining.com/2008/05/14/the-ultimate-ssh-security-tutorial/)

[COLOR=Blue]Ubuntu SSH Documentation:[/COLOR] [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[COLOR=Blue]OpenSSH:[/COLOR] [http://www.openssh.org/](http://www.openssh.org/)

[COLOR=Blue]Wikipedia Entry:[/COLOR] [COLOR=Blue][http://en.wikipedia.org/wiki/Secure_Shell/]("http://en.wikipedia.org/wiki/Secure_Shell")[/COLOR]

[COLOR=Blue] sshd_config man page[/COLOR]
[/INDENT]

---

