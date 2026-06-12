---
title: "HOWTO: Surf remotely using your home computer and IP"
date: 2008-01-10
forum: Outdated Tutorials &amp; Tips
---

### Post by markyb86 on 2008-01-10
[SIZE="5"][B]HOWTO: Surf remotely using your home computer and IP
[/B][/SIZE]
This is going to be a two-part process.

First we need to set up the computer you use at home with internet access.
goto [http://www.whatismyip.com]("http://www.whatismyip.com") and write your home ip down. (YOU NEED THIS LATER)

next, create a new user,
System > Administration > Users and Groups

create a new user and give this user a strong password.

Then, open a terminal and run

```
sudo apt-get install open-ssh
```

This will install Open ssh.

you need to edit /etc/ssh/sshd_config .

```
gksudo gedit /etc/ssh/sshd_config
```

look for Port 22 and change it to Port 443.
(this step is taken because some isps or firewalls block port 22, and this is easier to change then the firewalls settinfgs.)

save, exit and reboot your computer.


and this part is done.

Next you need to set up your computer that is away from home.



[SIZE="5"]**If you are using windows**[/SIZE]

you need to download putty.
at this link.

You will need to configure putty to use your current internet connection/proxy.

On the proxy option on the left when you first open putty,
is where this is. Set it, go back to the sessions page, save the session and exit putty.

open up notepad. copy and paste these lines into the notepad:

```
putty -D 8080 -P 443 -ssh 0.0.0.0
```

replace the 0.0.0.0 with the ip address you wrote down earlier, and save the file as ssh.bat, by selecting "all files" at the bottom of the save as window, and save it in the same folder you downloaded putty to. close notepad.

When you double click the ssh.bat file it should connect to your home computer and ask for your user name. this is good. log in and then minimize the terminal window. your almost done. 

open up your web browser, chat program, anything that you need to use that was blocked. and 

goto where you can set your proxy settings. (in firefox this is Edit > Preferences > Advanced > 

Connections, or Tools > Options > Advanced > Connections.) Set the SOCKS5 proxy to 127.0.0.1 port 8080 and make sure all the other fields are blank.

hit ok and get out of the settings window, and you should be as free as a downloaded linux iso!!


[SIZE="5"]**If you are using linux**[/SIZE]

you are going to open a terminal and type the following:

```
ssh -D 8080 -p 443 -l username 0.0.0.0
```

remember to replace the 0.0.0.0 with your ip address that you wrote down earlier, and username with the username we created at the beginning.

proceed to log in.

when you are at the default shell prompt, you can run any application from your home computer just by typing its command. for instance typing in firefox, will open firefox as if it were running on your computer natively.


**[SIZE="5"]Troubleshooting[/SIZE]**
Firstly if you get no connection at all, try using port 80 where i specified port 443. you will have to change that number in the command you use to connect as well.

If you have no internet access at all, where you are at, this will not work either.

on your home computer make sure you are editing sshd_config and not ssh_config

---

### Post by K.Mandla on 2008-01-10
As a staff note, this is a perfectly legitimate procedure, however some locations may have policies regarding bypassing filters in this manner. Please speak with the appropriate IT representative before using this technique.

---

### Post by utnalove on 2008-10-10
please delete -  mistake

---

### Post by utnalove on 2008-10-10
Hi All,

from the location A I can use the ports 25 and 110 to connect to the internet and download the post.

I would like to connect to my location B to port 25 or 110 and then be able to surf the internet from location A using those ports on the browser.

Did I give you the idea?

Maybe it's something like a web server running on port 25, when I connect from location A to [http://myhomeip:25](http://myhomeip:25) I should be able to enter the website I need to surf, and then surf, using my location B computer...

How can I do that? At location B I can have both Windows and Linux server...

Thanks

---

### Post by lukjad on 2008-10-10
Thanks! I'll be using this!

---

### Post by utnalove on 2008-10-10
How should I configure the file?

```
#	$OpenBSD: sshd_config,v 1.74 2006/07/19 13:07:10 dtucker Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/local/sbin:/usr/sbin:/sbin:/usr/local/bin:/usr/bin:/bin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options change a
# default value.

Port 22
#Protocol 2,1
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

# HostKey for protocol version 1
#HostKey /etc/ssh/ssh_host_key
# HostKeys for protocol version 2
#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_dsa_key

# Lifetime and size of ephemeral version 1 server key
#KeyRegenerationInterval 1h
#ServerKeyBits 768

# Logging
# obsoletes QuietMode and FascistLogging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:

#LoginGraceTime 2m
#PermitRootLogin yes
#StrictModes yes
#MaxAuthTries 6

#RSAAuthentication yes
#PubkeyAuthentication yes
#AuthorizedKeysFile	.ssh/authorized_keys

# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#RhostsRSAAuthentication no
# similar for protocol version 2
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# RhostsRSAAuthentication and HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

# To disable tunneled clear text passwords, change to no here!
#PasswordAuthentication yes
#PermitEmptyPasswords no

# Change to no to disable s/key passwords
#ChallengeResponseAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

# Set this to 'yes' to enable PAM authentication, account processing, 
# and session processing. If this is enabled, PAM authentication will 
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
#UsePAM no

#AllowTcpForwarding yes
#GatewayPorts no
#X11Forwarding no
#X11DisplayOffset 10
#X11UseLocalhost yes
#PrintMotd yes
#PrintLastLog yes
#TCPKeepAlive yes
#UseLogin no
#UsePrivilegeSeparation yes
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS yes
#PidFile /var/run/sshd.pid
#MaxStartups 10
#PermitTunnel no

# no default banner path
#Banner /some/path

# override default of no subsystems
Subsystem	sftp	/usr/libexec/sftp-server

# Example of overriding settings on a per-user basis
#Match User anoncvs
#	X11Forwarding no
#	AllowTcpForwarding no
#	ForceCommand cvs server
```



I ask because I can see that by default it's all commented with #### ... but I can remotely connect to my SSH....

Should be working fine if I change the port to some other and leave the rest commented or should I edit something else?

---

### Post by kevdog on 2008-10-11
The defaults are listed by the comments.  

What I usually do to remember the defaults is the following (using the port line as the example.

Keep the original default commented
#Port 22

But add your modification of the port statement below:

#Port 22
Port 222

This would change the listening port of the ssh server from 22 to 222.

---

### Post by kevdog on 2008-10-11
I would also like to add that although this method is described correctly with more detail, another description that users may want to consult is here:

[http://ubuntuforums.org/showthread.php?t=723025&highlight=forwarding+ssh](http://ubuntuforums.org/showthread.php?t=723025&highlight=forwarding+ssh)

---

### Post by utnalove on 2008-10-11
thank you!! it works!

---

### Post by durand on 2008-10-12
Thanks! Works great!

---

