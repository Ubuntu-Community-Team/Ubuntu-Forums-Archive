---
title: "FreeNx problem"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by Xzinum on 2008-09-25
Hey,

I had FreeNx working beautifully on my previous machine. I since got a new drive and re-installed the whole Os from scratch. I have been trying to get FreeNx working again but i'm have such a difficult time doing so.

I followed all the instructions on this thread
[http://ubuntuforums.org/showthread.php?t=620057](http://ubuntuforums.org/showthread.php?t=620057)

and yet, i'm still getting an error when trying to connect with !M NX client for windows. 

From what i read in the FreeNX thread, it's a classic error but i can't seem to find the information i need to get it fixed. 

```
NX> 105 /usr/bin/nxserver: line 1531: 12612 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/username/.nx/F-C-ubuntu-1000-3C3FE74C75F1FAF795964BE2551C3D5D/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
Can't open /var/lib/nxserver/db/running/sessionId{3C3FE74C75F1FAF795964BE2551C3D5D}: No such file or directory.
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{3C3FE74C75F1FAF795964BE2551C3D5D}': No such file or directoryNX> 1006 Session status: closed

NX> 1001 Bye.
NX> 280 Exiting on signal: 15
```

On a side note, when i try the "ssh -X myserver; /usr/lib/nx/nxnode --agent" i get this error

```
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: not detected)
NX> 716 Starting NX Agent ...
/usr/lib/nx/nxnode: line 1523: /usr/bin/nxagent: No such file or directory
NX> 716 NX Agent exited with status: 127
NX> 1001 Bye.

```

NXagent is installed but it is in /usr/lib/nx and not in /usr/bin like the error says.

Can anyone help me or point me to some information on this issue?

---

### Post by Peter09 on 2008-09-25
Is the server set up correctly, have you a system that logs into the server ok?

Have you installed nxnode on the server?

---

### Post by Xzinum on 2008-09-25
I can ssh into it and i was also able to setup a samba server which also works ok. I also get the same error if i try freenx on the local machine.

---

### Post by Peter09 on 2008-09-25
Note my addition - you need to install the nxserver and the nxnode software.

---

### Post by Xzinum on 2008-09-25
everything is installed. here's the apt-cache results that are relevant. Apt-get says nxnode is refered to by another package.
```

libnxcl-bin - NX X compression client library---runtime
libnxcl-dev - NX X compression client library---headers
libnxcl1 - NX X compression client library
qtnx - NX client for QT
freenx - The FreeNX application/thin-client server based on NX technology
freenx-media - The FreeNX application/thin-client server based on NX technology
freenx-nxredir - Transitional package - please remove
freenx-rdp - The FreeNX application/thin-client server based on NX technology
freenx-server - The FreeNX application/thin-client server based on NX technology
freenx-session-launcher - The FreeNX application/thin-client server based on NX technology
freenx-vnc - The FreeNX application/thin-client server based on NX technology
libxcomp-dev - NoMachine NX - NX compression library
libxcomp3 - NoMachine NX - NX compression library
libxcompext-dev - NoMachine NX - NX compression library
libxcompext3 - NoMachine NX - NX compression library
libxcompshad - NoMachine NX - NX compression library
libxcompshad-dev - NoMachine NX - NX compression library
nxagent - NoMachine NX - nesting X server with roundtrip suppression
nxagent-dev - NoMachine NX - nesting X server with roundtrip suppression
nxclient - NX Client
nxlibs - NoMachine NX - common agent libraries
nxlibs-dev - NoMachine NX - common agent libraries
nxproxy - NoMachine NX - X protocol compression proxy
freenx-nxviewer - The FreeNX application/thin-client server based on NX technology
freenx-nxdesktop - The FreeNX application/thin-client server based on NX technology
```

---

### Post by Peter09 on 2008-09-25
Not sure where you are looking.
You need to install the freenx client on the client, and two packages on the server,FreeNX server and FreeNX node.

Looking at your error it appears it cant find the node application.

---

### Post by rscheideman on 2008-09-25
have you added the user using /usr/NX/bin/nxserver --useradd *username*

---

### Post by Xzinum on 2008-09-25
Ok, i got it working. I had the software installed, everything was supposed to work. The problem was that the nxnode was looking for nxagent in the wrong location. So i created a symbolic link in /usr/bin/ to point to nxagent in /usr/lib/nx/

I connected and everything looks fine. Although i am wondering if it's a problem with the software not looking in the right place or my install not doing it right and not putting nxagent where the soft is expecting to find it.

---

### Post by Peter09 on 2008-09-25
I think the defaults in the Ubuntu package are different to the defaults from the FreeNX site. Perhaps you mixed and matched :)

---

### Post by cwmoser on 2008-10-01
My NXServer which has been working perfectly for some time has also stopped.  Somthing to do with authentication failing.

I've tried reinstalling NXServer but to no avail.

Appears to be something to do with ssh

Anyone have any ideas?

Carl

---

### Post by Peter09 on 2008-10-01
Try logging in with the command

```
ssh -vX youruser@yourserver xterm
```

this should give debug output to the terminal.

---

### Post by cwmoser on 2008-10-02
> **Peter09 said:**
> Try logging in with the command

```
ssh -vX youruser@yourserver xterm
```

this should give debug output to the terminal.



I get this:

carl@klaatu:~$ ssh -vX carl@klaatu xterm
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to klaatu [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/carl/.ssh/identity type -1
debug1: identity file /home/carl/.ssh/id_rsa type 1
debug1: identity file /home/carl/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'klaatu' is known and matches the RSA host key.
debug1: Found key in /home/carl/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/carl/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/carl/.ssh/identity
debug1: Trying private key: /home/carl/.ssh/id_dsa
debug1: Next authentication method: password
carl@klaatu's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Requesting X11 forwarding with authentication spoofing.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending command: xterm
debug1: client_input_channel_open: ctype x11 rchan 3 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 47695
debug1: channel 1: new [x11]
debug1: confirm x11


and a teminal window appears.

Looks like it is showing that Password authentication is working.
Exactly what is this telling me about the keys?

Thanks

Carl

---

