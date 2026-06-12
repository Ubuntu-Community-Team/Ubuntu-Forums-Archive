---
title: "VNC works, SSH works, but how both together?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by candtalan on 2008-11-22
Using Ubuntu 8.04 on each computer:
I am trying to learn how I might support a relative's Ubuntu PC remotely, with some simple tests to start with.

Currently the relative's PC (192.168.1.6) is at home in my LAN.
I am using my main PC (192.168.1.3) to try to manage the relatives PC remotely.

The two machines are currently both inside my wired lan, with a wired router protecting from the internet. There are various switches between them but the switches seem to remain transparent.

VNC:
VNC works well. It is set up on (192.168.1.6) and is set at its most simple to begin with. On my main PC, in a terminal I can command
vncviewer 192.168.1.6
and I get a good gui display of (192.168.1.6) showing on (192.168.1.3)

SSH:
After closing that display I can connect ok using ssh:
ssh user1@192.168.1.6

and after the password request, I am given the user1 prompt:
user1@810L:~$

which I can use for commands such as 
ls which work ok.

What I cannot yet seem to find how to do is run the vncviewer from or through (?) the ssh connection:

user1@810L:~$ sudo vncviewer
VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: unable to open display ""

I have spent a long time searching and trying things, however, the wise words are typically 'use vnc over ssh'.

Mmm, ok, but how?
tia

---

### Post by eldragon on 2008-11-22
you need to set up a ssh tunnel that will send all traffic from computer A to computer B through the ssh tunnel.

so, if computer A has ip 10.0.0.2
and computer B has ip 10.0.0.3

and you want to establish a vnc session from computer A to computer B through ssh. do the following:

open a terminal and forward a port with
```

user@A$ ssh username@10.0.0.3 -L5900:localhost:5900

```

then open a new terminal and run
```

user@A$ vncviewer localhost

```

some explaining:

the -L5900:localhost:5900 command, tells the ssh client to forward all packets sent to the computer A's port 5900 to the computer B port 5900 through the shh tunnel. (remember this localhost, means computer B's 127.0.0.1 not A) if instead of localhost, you specify a different ip belonging to a computer in computer's B lan, then the packets would be forwarded to that computer instead of B.

now, when you ran from computer's A, vncviewer localhost. the ssh client at computer A, which is now listening to port 5900, grabs anything sent to that port, and sends it flying through the tunnel.

---

### Post by chazn85 on 2008-11-22
in addition you will need to set up some port forwarding on the target machine in addition to some possible dns forwarding

---

### Post by candtalan on 2008-11-23
> **eldragon said:**
> (snip)
then open a new terminal and run
```

user@A$ vncviewer localhost

```


I thought I had a problem because when I used
user@A$ vncviewer localhost
I kept getting an error response:
VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: unable to open display ""

However my mistake was in not initially noticing the need as you said, to open a NEW terminal..... :-) 

Then it all works. Thanks!

---

### Post by candtalan on 2008-11-23
I have found some more information about a VNC option -via, which is elegant in that it appears to include the use of ssh and an encrypted tunnel, with default local port forwarding. 

For my specific details in this thread (192.168.1.6 is my relative's machine while on test in my lan) - 

vncviewer -via user1@192.168.1.6 localhost:0

is successful :-) in giving me view of the 192.168.1.6 machine desktop
on condition of course that
1) the machine has had vnc set to allow viewing
system>preferences>remote desktop (allow others to view)
2) the -via option requires  use of ssh and ssh server and client are required to be installed previously. For 8.04 this means packages
openssh-client
openssh-server
this is necessary on the target machine (my relative's pc) although on my own PC I only seem to need the ssh-client I guess because I am using it to view another machine.

I have tried (as a test) to use the -via option when one machine or the other does not have ssh installed, and the connection is not created.

For reference, I came across this approach from the site:
[http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/](http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/)

Also useful are vncwiewer manpages eg
[http://linux.die.net/man/1/vncviewer](http://linux.die.net/man/1/vncviewer)

I note that at this stage of testing my arrangements, I have both machines in my lan, and not across the internet. Also that I have not made any effort yet to create key pairs. Initial (ssh?) connections asked if I wanted to continue with what was effectively unverified machines, but I was offered an RSA key fingerprint which was then added, such as
Warning: Permanently added 'ssh-server.example.com,12.18.429.21' (RSA) to the list of known hosts.
for more information see:
[http://www.securityfocus.com/infocus/1806](http://www.securityfocus.com/infocus/1806)

Tests continue......

---

### Post by candtalan on 2008-11-27
> **candtalan said:**
> I note that at this stage of testing my arrangements, I have both machines in my lan, and not across the internet

Tests continued, and for the record, I later used the full internet IP address of the target machine, (my relatives PC) which was the IP address which my router was using after being allocated from my ISP supplier. This was because th erelatives PC is temorarily at my own home in my LAN fo rset up and tests, before I deliver it. So the 
user1@192.168.1.6
became
user1@[internetIPaddress]
where internetIPaddress was the reported address either seen from my router administration panel or  from web sites such as 
[http://whatismyip.com/](http://whatismyip.com/)
I know  my ISP will change this address on an arbitrary basis, but that does not bother me at this stage, it has not changed for several days anyway (at least).

> Also that I have not made any effort yet to create key pairs.
 I later generated key pairs. I am using a laptop to try to connect with my relatives desktop PC. The first key pair I generated was generated on the laptop. I used information from
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
specifically
=============================
Tip: Generating Public Keys
To create your public and private SSH keys on the command-line, do:
mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -q -f ~/.ssh/id_rsa -t rsa
Then enter a password that will protect your private key while it's stored on the hard drive (or press enter to leave your private key unprotected).
Your public key is now available as .ssh/id_rsa.pub in your home folder. 
=============================
I used a pass phrase rather than just a password.

I believe the private key stays on the laptop, effectively identifying it. The other part of the pair, the public key, needed to be copied to the relatives PC into the .ssh/authorized_keys file (to be 'on all the computers you want to log in to')

Because I now began to understand that the private key identified the laptop, I also then realised that I also probably (?) needed an appropriate private key to reside on the relatives desktop. So I went to it, and ran the keygen process again, I left the new private key in place, then copied the new public key from the desktop across to the laptop, similarly as before.
My understanding here is that each machine will be sure that it is connected to the other.

---

### Post by candtalan on 2008-11-28
For reference for those starting out as I was:

In addition to this thread, other threads I have recently been using for aspects of my learning are:

ssh and simple (?) tests
[http://ubuntuforums.org/showthread.php?t=994365](http://ubuntuforums.org/showthread.php?t=994365)

and

Hardy 8.04 Remote Desktop - Encryption??
[http://ubuntuforums.org/showthread.php?t=989958](http://ubuntuforums.org/showthread.php?t=989958)

I will aim to summarise in a post soon, the few commands I expect to use in the real situation.

---

