---
title: "Trying to SSH to Ubuntu"
date: 2012-02-28
forum: New to Ubuntu
---

### Post by UnknownFearNG on 2012-02-28
Hello all. I am trying to SSH into my Ubuntu computer, the one I am on now, from my Android phone via Terminal of course. I installed openssh and when I go to ssh into my computer by typing user@host, it hangs. No errors are given, it just sits there. For instance, I try typing "ssh bob@Darkan" and it just hangs. Any ideas for this? The only main developments I have on my computer is a LAMP server, but would this cause conflict? Thanks for all your help.

---

### Post by turinglabs on 2012-02-28
Hard to say without more details. Are you trying to connect from the internet, or from your LAN? Do you have a router doing port forwarding to your Ubuntu workstation? Is there a firewall enabled on your Ubuntu workstation?

---

### Post by collisionystm on 2012-02-28
> **UnknownFearNG said:**
> Hello all. I am trying to SSH into my Ubuntu computer, the one I am on now, from my Android phone via Terminal of course. I installed openssh and when I go to ssh into my computer by typing user@host, it hangs. No errors are given, it just sits there. For instance, I try typing "ssh bob@Darkan" and it just hangs. Any ideas for this? The only main developments I have on my computer is a LAMP server, but would this cause conflict? Thanks for all your help.


You should 

ssh [email]user@IP.ADDRESS.OF.UBUNTU[/email]

---

### Post by UnknownFearNG on 2012-02-28
> **turinglabs said:**
> Hard to say without more details. Are you trying to connect from the internet, or from your LAN? Do you have a router doing port forwarding to your Ubuntu workstation? Is there a firewall enabled on your Ubuntu workstation?

Tried both from Internet and LAN. Keeps saying either connection refused or just hangs. iptables displays nothing.

Tried purging and reinstalling openssh-server and -client with no luck :(

I can ssh from the same machine, but not from my phone.

---

### Post by collisionystm on 2012-02-28
> **UnknownFearNG said:**
> Tried both from Internet and LAN. Keeps saying either connection refused or just hangs. iptables displays nothing.

Tried purging and reinstalling openssh-server and -client with no luck :(

I can ssh from the same machine, but not from my phone.


Is your phone connected to WIFI on the same network?

Are you trying to SSH into the local IP of the server?

---

### Post by UnknownFearNG on 2012-02-28
> **collisionystm said:**
> Is your phone connected to WIFI on the same network?

Are you trying to SSH into the local IP of the server?

Yes, it is on the same WiFi. I tried both the host (Darkan), 127.0.0.1/127.0.1.1 and the local server as well. Still no dice. I also have tried using just the 3G connection, but also doesn't work.

---

### Post by collisionystm on 2012-02-28
> **UnknownFearNG said:**
> Yes, it is on the same WiFi. I tried both the host (Darkan), 127.0.0.1/127.0.1.1 and the local server as well. Still no dice. I also have tried using just the 3G connection, but also doesn't work.

on your computer, open terminal

type 

ifconfig

SSH to whatever the inet addr: is on eth0 or eth1


your hostname Darkan wont resolve unless you have it manually entered in DNS. 127.X.X.X is a loopback address and will take you no where but back to the phone itself.

---

### Post by Henkdroid on 2012-02-28
Did you set it up correctly? Type ```
sudo gedit /etc/ssh/sshd_config
``` and look at the instructions [here.]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

---

### Post by UnknownFearNG on 2012-02-28
> **collisionystm said:**
> on your computer, open terminal

type 

ifconfig

SSH to whatever the inet addr: is on eth0 or eth1


I tried doing ssh daniel@wlan0 (eth0 has no address) but it keeps saying connection refused. I have sshd_config setup correctly; this is a fresh reinstall.

Please do NOT think I actually put ssh @wlan0. I put the actual IP address, I'm not that dumb ;)

---

### Post by matt_symes on 2012-02-28
Hi

Connect using the -vvv switch. Post the output back here.

```
ssh -vvv user@ipaddress
```

Kind regards

---

### Post by collisionystm on 2012-02-28
are you using a firewall?

iptables? Ufw?

---

### Post by UnknownFearNG on 2012-02-28
No firewall, iptables comes up black with no tables whatsoever.

---

### Post by azmyth on 2012-02-28
Please do this and post the output here. This will tell what the problem is.

```
ssh -vvv user@ipaddress
```

---

### Post by UnknownFearNG on 2012-02-28
Output from 'ssh -vvv daniel@192.168.2.17':
```

TRACE (23267): non-flasg arg: 'daniel@192.168.2.17'
TRACE (23267): user='daniel' host='192.168.2.17' port='22'
TRACE (23267): enter connect_remote

```

---

### Post by UnknownFearNG on 2012-02-28
After awhile of this, it then put:

```

ssh: Exited: Error connecting: Connection timed out

```

---

### Post by azmyth on 2012-02-28
Can you ping it?

ping 192.168.2.17

---

### Post by UnknownFearNG on 2012-02-28
> **azmyth said:**
> Can you ping it?

ping 192.168.2.17

I can ping it from my Android phone on the same WiFi, yes. Least we know it can communicate back and forth :D

---

### Post by UnknownFearNG on 2012-02-28
Not sure if this will help any, but I did a netstat command while I did a ssh into my host. Here is the output:

```


daniel@Darkan:~$ netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0     39 Darkan.local:ssh        android-96f06e6cb:42461 ESTABLISHED
tcp        0      0 Darkan.local:47451      yyz06s05-in-f7.1e10:www TIME_WAIT  
tcp        0      0 Darkan.local:48787      iy-in-f102.1e100.ne:www ESTABLISHED
tcp        0      0 Darkan.local:55763      cbf02m01-in:xmpp-client ESTABLISHED
tcp        0      0 Darkan.local:50419      a96-6-120-16.deploy:www TIME_WAIT  
tcp        0      0 Darkan.local:57805      community.ca.dc.ope:www TIME_WAIT  
tcp        0      0 Darkan.local:47450      yyz06s05-in-f7.1e10:www ESTABLISHED
tcp        0      0 Darkan.local:41038      yyz06s06-in-f14.1e1:www ESTABLISHED
tcp        0      0 Darkan.local:45826      yyz06s06-in-f6.1e:https ESTABLISHED

```

---

### Post by kevdog on 2012-02-28
Do a port scan remotely to your server to see if port 22 is open.  You can either do this from the client using nmap of from a remote website that scans common ports on your computer.

---

### Post by UnknownFearNG on 2012-02-28
> **kevdog said:**
> Do a port scan remotely to your server to see if port 22 is open.  You can either do this from the client using nmap of from a remote website that scans common ports on your computer.

```


Starting Nmap 5.21 ( http://nmap.org ) at 2012-02-28 16:44 EST
Nmap scan report for Darkan (127.0.1.1)
Host is up (0.0011s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 0.27 seconds

```

Both ssh and http are open.

---

### Post by azmyth on 2012-02-28
Being able to ping it is a good start :p

Your output from this command doesn't look right.

Output from 'ssh -vvv daniel@192.168.2.17':

It should show trying to load your config file etc.

What does ps -A | grep ssh

produce.

Also, I'd try running ssh in debug mode

sudo service ssh stop
/usr/sbin/sshd -d

This will run ssh in a terminal and you can watch the output as you try to connect.

---

### Post by matt_symes on 2012-02-28
Hi

Is your ssh client on your phone dropbear ?

Kind regards

---

### Post by UnknownFearNG on 2012-02-28
Output of 'ps -A | grep ssh":
```


daniel@Darkan:~$ ps -A | grep ssh
 1763 ?        00:00:00 ssh-agent
18465 ?        00:00:00 sshd

```

I am using Better Terminal Emulator Pro. Same things happens on BotConnect as well.

---

### Post by kevdog on 2012-02-28
Are you trying to do this with a password or keys?  Have you tried on any other platform other than your phone?  Have you port forwarded port 22 from your router to the server computer? (I guess you would have based on nmap however I'm just checking). 

A dropbear client if using passwords should work with an openssh implementation.  If using keys you have to convert from dropbear format to openssh format (which is easy to do).  Stick with password for now.

Have you checked the server's syslog to see if anything is amiss?

sudo iptables -L  <----can you post this?

---

### Post by UnknownFearNG on 2012-02-28
> **kevdog said:**
> 
sudo iptables -L  <----can you post this?

Output from "sudo iptables -L":

```

daniel@Darkan:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

I am using a password instead of keys.

---

### Post by azmyth on 2012-02-28
I'd try running ssh in debug mode

sudo service ssh stop
/usr/sbin/sshd -d

It only works once so you have to restart after each try.

---

### Post by UnknownFearNG on 2012-02-28
> **azmyth said:**
> I'd try running ssh in debug mode

sudo service ssh stop
/usr/sbin/sshd -d

It only works once so you have to restart after each try.

Here's the output. This also has the connection from my phone:

```

daniel@Darkan:~$ sudo /usr/sbin/sshd -d
debug1: sshd version OpenSSH_5.8p1 Debian-7ubuntu1
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: read PEM private key done: type ECDSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.ECDSA-256
debug1: Checking blacklist file /etc/ssh/blacklist.ECDSA-256
debug1: private host key: #2 type 3 ECDSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
Set /proc/self/oom_score_adj from 0 to -1000
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.
debug1: Bind to port 22 on ::.
Server listening on :: port 22.
debug1: Server will not fork when running in debugging mode.
debug1: rexec start in 5 out 5 newsock 5 pipe -1 sock 8
debug1: inetd sockets after dupping: 3, 3
Connection from 192.168.2.21 port 33300

```

Does this give us anything useful to work with?

---

### Post by azmyth on 2012-02-28
Everything looks normal it just doesn't connect. You may try the info here.

[http://wiki.cyanogenmod.com/wiki/Howto:_Connect_to_Device_with_SSH](http://wiki.cyanogenmod.com/wiki/Howto:_Connect_to_Device_with_SSH)

I guess I'm out of ideas for you.

---

### Post by UnknownFearNG on 2012-02-28
> **azmyth said:**
> Everything looks normal it just doesn't connect. You may try the info here.

[http://wiki.cyanogenmod.com/wiki/Howto:_Connect_to_Device_with_SSH](http://wiki.cyanogenmod.com/wiki/Howto:_Connect_to_Device_with_SSH)

I guess I'm out of ideas for you.

Unfortunately, nothing on that page will help me as I do not run CyanogenMod or Dropbear. Very weird though. It should just work :(

---

### Post by azmyth on 2012-02-29
My mistake, I thought you were using dropbear.

Anyhow, maybe check the /var/log/auth.log after an attempted login.

---

### Post by UnknownFearNG on 2012-02-29
> **azmyth said:**
> My mistake, I thought you were using dropbear.

Anyhow, maybe check the /var/log/auth.log after an attempted login.

I checked the log file and it's blank. I even removed and reinstalled openssh-server and tried to ssh into it and then viewed the log file again, but there is nothing in the file. SSH is running as well.

---

### Post by kevdog on 2012-02-29
I don't get it.  Looking at what you posted, the last line states:

Connection from 192.168.2.21 port 33300

Doesn't this indicate a connection was made?

Hmm this might be a PAM problem..

---

### Post by UnknownFearNG on 2012-02-29
> **kevdog said:**
> I don't get it.  Looking at what you posted, the last line states:

Connection from 192.168.2.21 port 33300

Doesn't this indicate a connection was made?

I know, this is very weird!! Honestly, I've almost given up on trying. I only wanted to see if I could SSH into my computer to be able to run MySQL on my phone from the connection.

---

### Post by kevdog on 2012-02-29
What is your client you are using?

---

### Post by UnknownFearNG on 2012-02-29
> **kevdog said:**
> What is your client you are using?

The client, meaning the OS I am using to connect to Ubuntu? It's Android. I am using a terminal to try and SSH into my computer.

---

### Post by kevdog on 2012-02-29
Android to Ubuntu correct?  

Which client specifically by name?

---

### Post by UnknownFearNG on 2012-02-29
> **kevdog said:**
> Android to Ubuntu correct?  

Which client specifically by name?

That is correct. I'm sorry but I don't quite understand what you mean. However, I have tried to ssh into my computer from a different computer and it gets authenticated perfectly.

---

### Post by kevdog on 2012-02-29
Yes -- I know.  So at least the problem has been isolated to your phone.  What is the name of the program you are using on the phone? Terminal Emulator, ftpbot, sshbot, etc? Do you know who makes it (I'm assuming you've downloaded it from the market).  Is your phone rooted?

---

### Post by CharlesA on 2012-02-29
Not that it'll help much, but I use ConnectBot to ssh from my android.

---

### Post by UnknownFearNG on 2012-02-29
> **CharlesA said:**
> Not that it'll help much, but I use ConnectBot to ssh from my android.

This helped a LOT :) I am now able to ssh into my computer from my phone using ConnectBot!!! :D Works perfectly :) Now, I can ssh on wifi, but not on 3g. Is there a possibility I can ssh using 3g, or will do I have to use wifi? Least it works though :)

---

### Post by CharlesA on 2012-02-29
You'd need to have port forwarding set up to ssh from 3g, which is outside your local network.

---

### Post by UnknownFearNG on 2012-02-29
> **CharlesA said:**
> You'd need to have port forwarding set up to ssh from 3g, which is outside your local network.

Ah, makes sense. Thanks for the help.

---

