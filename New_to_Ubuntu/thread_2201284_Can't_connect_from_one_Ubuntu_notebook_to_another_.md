---
title: "Can't connect from one Ubuntu notebook to another Ubuntu notebook via SSH"
date: 2014-01-23
forum: New to Ubuntu
---

### Post by khurtsiya on 2014-01-23
Hi!

I installed openssh-server on Ubuntu notebook and from another Ubuntu notebook trying to connect by SSH:

```
bronepoezd@bronenout:~$ ssh -p 25 -v -v -v root@94.248.79.130
OpenSSH_6.1p1 Debian-4, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 94.248.79.130 [94.248.79.130] port 25.
debug1: connect to address 94.248.79.130 port 25: Connection timed out
ssh: connect to host 94.248.79.130 port 25: Connection timed out

```

Any help appreciated!

---

### Post by khurtsiya on 2014-01-24
any help?

---

### Post by The Cog on 2014-01-24
SSH normally uses port 22, not 25. Are you sure the server is listening for SSH on port 25?

You could run this command on the server to check what ports are listening:
```
sudo netstat -lntp
```

Also, check any firewall settings on the server. If the server wasn't listening you should have been told connection refused, not timeout (which indicates that packets are being dropped somewhere).

---

### Post by khurtsiya on 2014-01-24
Thanks for the answer!

I reinstalled Ubuntu from 13.10 to 12.04 since keyboard layout changing bug kills me...

So now I have brand new installation.

I installed also openssh-server.

sshd listening to port 22
service ssh status is start/running
ufw is inactive

any thoughts?

---

### Post by The Cog on 2014-01-24
Do you still get a timeout error? 
If so, can you even ping it?
Timeout is a sign of a networking or firewall problem - packets not reaching their destination.

---

### Post by steeldriver on 2014-01-24
Are the machines on the same LAN? it looks like you are trying to connect via a public IP

---

### Post by khurtsiya on 2014-01-24
One notebook (client) connected to internet via wi-fi to my home router and another notebook (server) is connected to internet via wi-fi to 3G modem
The idea is to connect to server-notebook anytime from anywhere via internet

---

### Post by The Cog on 2014-01-24
Good point, steeldriver. 
If both machines are on a private LAN and you are trying to connect to the public NATted IP address, that generally doesn't work. For connections between hosts on the provate LAN, you need to use the local non NATted addresses.

---

### Post by The Cog on 2014-01-24
When I try to ssh to that public address, I get connection refused. Not timeout.

BEWARE
A public SSH server (once it is accepting connections) will be subjected to persistent password guessing bots. 
Make sure ALL your passwords are strong ones, and preferably configure for passwordless authentication only (this uses keys for authentication). 
[http://askubuntu.com/questions/46930/how-can-i-set-up-password-less-ssh-login](http://askubuntu.com/questions/46930/how-can-i-set-up-password-less-ssh-login)

---

### Post by khurtsiya on 2014-01-24
I guess they are not on a private LAN... Though I am not a network expert...

I can not ping it - freeze at f

> ~$ ping 94.248.64.153
PING 94.248.64.153 (94.248.64.153) 56(84) bytes of data.

---

### Post by khurtsiya on 2014-01-24
any suggestions?

---

### Post by steeldriver on 2014-01-24
You may have better luck putting the server on the home wifi network and trying with the client connected via your 3G service - not forgetting to set up the appropriate port forwarding on your home router of course

---

### Post by khurtsiya on 2014-01-24
is there a way to do this without port forwarding?
and what if server is moving and sending me actual IP - can't I connect to it, assuming SSH is configured and I have password?

---

### Post by The Cog on 2014-01-25
> **khurtsiya said:**
> any suggestions?

Try pinging the server to see if there is any basic network connectivity.

---

### Post by wlraider70 on 2014-01-25
Can you give us the output of ifconfig

---

### Post by fosterD on 2014-01-25
There are two things you can try:
1- SSH server and client are running fine
2- The connectivity between your home laptop and remote laptop (using 3G)

I suggest that you should connect both laptops into a private network (your home network, e.g 192.168.0.x)
Suppose your remote laptop's ip address in 192.168.0.10
```
ssh <remote-user>@192.168.0.10
```
By default, ssh uses port 22, if it is configured to use another port number, you can use '-p <port-number>'
At this stage, you can confirm that ssh is running fine

Then you can try to use external ip address

- Make sure your external ip address (3G) is correct ([https://www.google.com.au/#q=what+is+my+ip+address](https://www.google.com.au/#q=what+is+my+ip+address)). It should be pingable.
- You need to configure your home router to forward ssh packets (port 22) from external to your home laptop. Configuring port forwarding is an easier approach here.

Hope this could help

---

### Post by khurtsiya on 2014-01-30
Hi! Finally connection established, thanks to this short and clear article: [http://linuxwave.blogspot.com/2008/05/creating-ssh-reverse-tunnel.html](http://linuxwave.blogspot.com/2008/05/creating-ssh-reverse-tunnel.html)

But! Now I have this error:

> ~$ ssh -vvvv k@91.111.136.30 -p 7777
k@91.111.136.30's password: 
debug3: packet_send2: adding 64 (len 52 padlen 12 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.

Looked many other articles with this problem and fotums, but none of the solutions helped. Any suggestions much appreciated.

---

### Post by khurtsiya on 2014-01-30
Here is the instruction from that article:

> 
1. Create a tunnel from middle to target and leave it open when you are still at the office. You cn also ask your colleague at the office to do this. The below command will open port 12000 on middle for listening and forward all request on port 12000 on middle to port 22 of target
```
[COLOR="#FF0000"]user@target $ ssh -R 12000:localhost:22 middleuser@middle[/COLOR] 
```
2. Now you can access to port 12000 on middle from current and you will be forwarded to port 22 on target
```
[COLOR="#FF0000"]user@current $ ssh targetuser@middle -p 12000[/COLOR]
```
3. If somehow you cannot access, access middle first, then connect to port 12000 of localhost
```
[COLOR="#FF0000"]user@current $ ssh middleuser@middle
user@middle $ ssh targetuser@localhost -p 12000[/COLOR]
```
You are now in the target server

---

