---
title: "proftpd cannot log in"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by jcr1 on 2008-06-17
Hi all,

I followed tis howto:

[http://ubuntuforums.org/showthread.php?t=79588&highlight=simple+ftp](http://ubuntuforums.org/showthread.php?t=79588&highlight=simple+ftp)

but I cannot connect. I am trying to connect from another machine on my network, using filezilla, i enter ip addy of machine, my username (set up as seperate user as per tutorial), password and port.

filezilla reports:

```
Status:	Connecting to 192.168.0.3:21...
Status:	Connection established, waiting for welcome message...
Response:	220 you're at home
Command:	USER jcrftp
Response:	331 Password required for jcrftp
Command:	PASS *******
Response:	530 Login incorrect.
Error:	Could not connect to server

```

all seems to go well untill Login incorrect... as if I have the password wrong or something...but i can't see how? I have gone over it many times.

Is it something to do with the UserAlias?

Here's my proftpd.conf:

```
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias jcrftp

ServerName			"jcrserver"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you 
#want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another 
#port for security reasons (choose here the port you want)
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/ftp-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser jcrftp
DenyALL
</Limit>

<Directory /home/ftp-shared>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/ftp-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/ftp-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

```

Is the "servername" important?

Thanks in advance.

---

### Post by superprash2003 on 2008-06-17
it would be easier to configure proftpd server by installing gproftpd the gui for proftpd..

---

### Post by jcr1 on 2008-06-18
I have to admit, I did have a look at that and was a bit lost. Wasn't sure what I was meant to be doing. Following the guide seemed straight forward, providing I just changed the relevant bits like username etc...

---

