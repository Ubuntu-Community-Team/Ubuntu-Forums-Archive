---
title: "No longer can SSH into server."
date: 2008-10-25
forum: New to Ubuntu
---

### Post by ghandi69_ on 2008-10-25
Hey guys, I have a headless server in my basement that I use for numerous activities.  Last night, I loggin in through ssh in a terminal with a -Y(for x forwarding), and was editing a text file on the server.  Instead of exiting out of the program I was X-forwarding, I closed the terminal of the ssh.  I now can no longer ssh into the machine.  As I get the following error...

```

tony@Ubuntu:~$ ssh -Y adminz@xxx.xxx.xxx.xxx
ssh_exchange_identification: Connection closed by remote host

```

Now, my local machine is able to ssh into other ssh severs still, like my university linux boxes.  So far, I have the tried the following options, unsuccessfully after doing some searching.

1. I have restarted the ssh server running on the server.
2. I have physically rebooted the server by holding the power button for a  hard reboot. 
3. I have deleted all entries in my /home/user/.ssh/known_hosts file on the local machine. After doing this, it doesn't even ask for verification before getting the error.
4. I am certain I am not denying any users on the server.
5. Waited about 8 hours for connection to time out.

-- I can access some of the server still, through webadmin.  And here is a copy of my /etc/ssh/sshd_config file on the server.  I'm assuming this should be fine, being I never changed it since it was working for the past year,non stop.

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
PermitRootLogin no
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
AllowTcpForwarding yes
X11UseLocalhost yes
PrintMotd yes
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

Lastly, here is an output of what happens when I run .ssh$ ssh -v -Y [email]adminz@xxx.xxx.xxx.xxx[/email]

```
 
ssh -v -Y adminz@xxx.xxx.xxx.xxx
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to xxx.xxx.xxx.xxx [xxx.xxx.xxx.xxx] port 22.
debug1: Connection established.
debug1: identity file /home/tony/.ssh/identity type -1
debug1: identity file /home/tony/.ssh/id_rsa type -1
debug1: identity file /home/tony/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
```

any help would be much appreciated!

---

### Post by quirks on 2008-10-25
I just read that this is probably caused by too many open connections (see here: [http://www.raditha.com/blog/archives/000604.html](http://www.raditha.com/blog/archives/000604.html) ). You said you waited like 8 hours for the connections to be closed, right? Apparently they didn't. Do have the possibility to kill them manually (i.e., do you have access to the server by other means than ssh)?

---

### Post by ghandi69_ on 2008-10-25
Thanks for the reply quirks,

The only things I have done that could of possibly killed the connections manually, is when I rebooted the server (by physically walking to the room where the server is located, and hard rebooting by holding the power button,which you think would have killed any connections), and I also have restarted the ssh server itself while the machine is running, by using 'webadmin' which is installed on the machine.

---

### Post by quirks on 2008-10-25
It probably is not the case, but: have you checked the files /etc/hosts.allow and /etc/hosts.deny? They should be empty or contain only comments. I'm just asking, because it is mentioned in almost every result I find at Google.

I'll keep on searching ...

Another question: I don't know "webadmin". What is that? Does it allow you to access the shell of your server?

And yet another question: if you have shell access on your server, maybe you can find hints in /var/log/messages, /var/log/syslog or /var/log/auth.log.

---

### Post by ghandi69_ on 2008-10-25
Hey quirks... I appreciate you helping, I have spent a decent amount of time searching google as well, and I kept on getting mainly 3 things.

1. - too many connections, but I thought a reboot would have fixed that.
2. - something in deny/allow.  Although, I have not changed those files recently, and the ssh has been working on this machine for about a year.  Also.. according to webadmin, as you see in screenshot below ,everything should be allowed.
3. - something on local machine, which i thought would be solved by removing the known_host information on my local machine, but nothing.

Anyway.. webadmin is pretty cool, I use my server as a webserver as well, and its a way to graphically administer a server remotely by using a webpage... I'll attach some screen shots as well to give you an idea of what it looks like (just because its cool)

---

### Post by quirks on 2008-10-25
Thank you for the screenies of Webmin. It looks like a pretty comprehensive tool.

I could imagine that the problem is on the client side (your workstation). Have you tried logging in without the -Y option, i.e. just "ssh [email]adminz@xxx.xxx.xxx.xxx[/email]"? If this works, maybe your local X server is blocking connections. Have you rebooted your workstation every since?

---

### Post by ghandi69_ on 2008-10-25
Hey quirk...

I have tried with the -Y option as well, and I get the same result (-Y -v shows same debug output)

Also.. I went and installed putty on my roommates xp machine, and was able to ssh into the server no problem, so it definitely is on the client side.  I have restarted the computer numerous times since then.

---

### Post by ghandi69_ on 2008-10-25
Also.. here is a copy of my local ssh_config file.

---

### Post by Dr Small on 2008-10-25
Sounds like a problem with known_hosts in ~/.ssh/
How about trying this:
```
mv ~/.ssh ~/.ssh_bak
```

Now try connecting.

---

### Post by ghandi69_ on 2008-10-25
> **Dr Small said:**
> Sounds like a problem with known_hosts in ~/.ssh/
How about trying this:
```
mv ~/.ssh ~/.ssh_bak
```

Now try connecting.

Thanks for the reply Dr. Small.. 

I had already removed all entries from that known hosts file, with no luck.  I also just tried your recommendations of moving the entire .ssh directory, but still the same result.

---

### Post by ghandi69_ on 2008-10-25
Yeah... as mentioned, it is definitely an issue on the client side, as putty works on a different computer with the same login name.

Also, a program like filezilla is unable to connect via ssh either from my machine, although.. I don't know why I thought it might....

---

### Post by Mister.Vash on 2008-10-25
Have you looked at the system logs on the server?  They might provide some additional details as too what is going on.  I know you said you try via putty - have you also tried create a test user on your client as well and trying from that account?  
if that fails you could try running sshd on the server with the -d options to get additional information

---

### Post by quirks on 2008-10-26
What about the IP address of your client? Is it static or does the DHCP always give you the same IP? Maybe it helps, if you manually change the IP of your client.

Gosh, I hate this trial and error method ...

---

### Post by ghandi69_ on 2008-10-26
> **quirks said:**
> What about the IP address of your client? Is it static or does the DHCP always give you the same IP? Maybe it helps, if you manually change the IP of your client.

Gosh, I hate this trial and error method ...

something else new guys... ssh doesn't work from my client.... to anyway.. not just my local server

Which means it might be nice to just uninstall it and reinstall it.. however, apparently you need to uninstall ubuntu-desktop along with openssh client

---

### Post by Xiong Chiamiov on 2008-10-26
You can reinstall instead of uninstalling and installing, which won't get rid of the things that depend on it.  However, it won't get rid of any of the configuration files, and I don't think that you can purge and reinstall at the same time.
```

sudo aptitude reinstall openssh-client

```

Also, filezilla connects through FTP (or SFTP), not SSH.

---

### Post by ghandi69_ on 2008-10-27
Ok, none of the following has worked so far, but I have a little more information to provide.  My client machine is now working for other ssh servers, but other machines besides my workstation can ssh into my server besides me, its just the my client machine has problems in my server.. thats.. 

Tried to ssh into the server from the server itself.. and this output came out.

```

penSSH_4.6p1 Debian-5ubuntu0.6, OpenSSL 0.9.8e 23 Feb 2007
Pseudo-terminal will not be allocated because stdin is not a terminal.
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.110 [192.168.1.110] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.6p1 Debian-5ubuntu0.6
debug1: match: OpenSSH_4.6p1 Debian-5ubuntu0.6 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6p1 Debian-5ubuntu0.6
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: read_passphrase: can't open /dev/tty: No such device or address
Host key verification failed.

```

---

