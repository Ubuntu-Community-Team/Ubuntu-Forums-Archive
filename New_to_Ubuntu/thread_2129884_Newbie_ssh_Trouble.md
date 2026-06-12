---
title: "Newbie ssh Trouble"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by capnChris on 2013-03-27
Hi there,

First time poster, first time user. Total linux noob, although I've kicked around the idea for a while. Anyway, can't find a real answer after hours of searching.

I wanted to fool around with having a home server. I have an old windows laptop I'm not using, so I figured I'd use that. I download the latest ubuntu server edition and install it correctly. I get intimidated by just having the command line and go ahead and download the latest (12.10) ubuntu desktop version and install it. Everything is great, install all the necessary updates including openssh.

My plan was to get to this point and walk away and begin doing the rest via ssh from my other home computers (I am also a ssh noob). I begin on my mac laptop because it's easier than installing putty on my windows desktop. I try to connect like this: 

```
ssh -l [yourusername] [your server's hostname]
```

That doesn't work, I get a message saying something to the effect of that hostname doesn't exist (I assure you. it does). Then I tried it like this:

```
ssh -l [yourusername]@[ipaddress]
```

After trying to connect via my servers dynamic ip address, it looks like it's working and then I am greeted with "connection timed out".

Did some research figured I needed to change the port on the server and forward the port on my router. Change the config on the server to port 2222, then forward port 2222 on my router using my servers ip address.

For the heck of it I also installed putty on my windows desktop and proceeded to try it with the new port. I was greeted with the exact same results. 

All I want to do is initially set up a safe server in my home that I can use to share media amongst my home computers. Can someone please help me set up ssh appropriately?? I cannot figure it out. Thanks.

---

### Post by nothingspecial on 2013-03-27
Have you got openssh-server installed on the laptop ?

You should not need to mess about with ports.

---

### Post by capnChris on 2013-03-27
Yes, as far as I know. Once the OS was installed I typed this


```
sudo apt-get update 

sudo apt-get install openssh-server
```

I assumed after that was done it was installed.

---

### Post by steeldriver on 2013-03-27
If you're doing this within a single LAN subnet there should be no need to either change the default port (22) or forward ports

You can check whether the ssh server is running and listening using

```
sudo netstat -nlp | grep ssh
```

(on the machine you're tryng to connect to) - as well, make sure your server's firewall is either disabled or configured to allow ssh traffic

```
sudo ufw status
```

You can start the ssh client in verbose mode to get more info about why it's failing

```
ssh **[COLOR=#006400]-vvv[/COLOR]** -l [yourusername] [your server's LAN IP]
```

[In my experience, LAN hostnames are flaky - unless you have explicitly set them in your hosts files they rely on avahi services and a cooperative router]

---

### Post by capnChris on 2013-03-27
Alright, well I will certainly report back once I'm home. Just to clarify, do I type these commands on the server or on the computer I'm trying to connect to the server through (client?)

---

### Post by steeldriver on 2013-03-27
first 2 on the server

last one on the client

---

### Post by capnChris on 2013-03-28
After switching the config back to the default port 22, I tried these commands last night. Here are the results:

Server:
```

[username]@[hostname]:~$ sudo netstat -nlp | grep ssh
[sudo] password for [username]:
unix  2      [ ACC ]     STREAM     LISTENING     13987    1803/ssh-agent      /tmp/ssh-hDPZHqidWIFi/agent.1768
unix  2      [ ACC ]     STREAM     LISTENING     14262    1757/gnome-keyring- /run/user/[username]/keyring-XTv26L/ssh
[username]@[hostname]:~$ sudo ufw status
Status: inactive

```

Client:
```

[name]:~ [name]$ ssh -vvv  -l [username] [server ip]
OpenSSH_5.2p1, OpenSSL 0.9.8r 8 Feb 2011
debug1: Reading configuration data /etc/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to [server ip] [server ip] port 22.
debug1: connect to address [server ip] port 22: Operation timed out
ssh: connect to host [server ip] port 22: Operation timed out

```

Does that help at all? What am I doing wrong?

---

### Post by steeldriver on 2013-03-28
It looks like there is no ssh server running on the target machine - you should see something like

```
$ sudo netstat -nlp | grep ssh
[COLOR=#ff0000]tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2422/sshd
tcp6       0      0 :::22                   :::*                    LISTEN      2422/sshd
[/COLOR]unix  2      [ ACC ]     STREAM     LISTENING     1654639  24955/gnome-keyring /tmp/keyring-ULu0Jf/ssh
unix  2      [ ACC ]     STREAM     LISTENING     1654946  25001/ssh-agent     /tmp/ssh-abMMOgi24966/agent.24966
```

You can also check with 
```
$ service ssh status
ssh start/running, process 2422
```

If it doesn't appear to be started you can try manually with

```
sudo service ssh start
```

To check that the package is actually installed

```
dpkg -l | grep openssh
```

(which will show both the openssh-server and openssh-client packages if they are installed) or

```
apt-cache policy openssh-server
```

---

### Post by capnChris on 2013-03-28
Thanks, I'll try those out later. In the future, will I have to manually start openssh every time I want to access it on a client?

---

### Post by steeldriver on 2013-03-28
no it should start automatically, if it's failing to start for some reason we will need to figure out why

---

### Post by capnChris on 2013-03-28
Here's what happened with that:

```

$ service ssh status
ssh stop/waiting

$ sudo service ssh start
ssh start/pre-start, process 2837

```

After that I tried "service ssh status" again and it still said "ssh stop/waiting".

I also checked to make sure it was installed as per your instructions:

```

$ dpkg -l | grep openssh
ii  openssh-client                            1:6.0p1-3ubuntu1                          i386         secure shell (SSH) client, for secure access to remote machines
ii  openssh-server                            1:6.0p1-3ubuntu1                          i386         secure shell (SSH) server, for secure access from remote machines 

```

Then for the heck of it I did this again:

```

$ sudo netstat -nlp | grep ssh
unix  2      [ ACC ]     STREAM     LISTENING     14294    1802/ssh-agent      /tmp/ssh-BlbpOyh7occ5/agent.1767
unix  2      [ ACC ]     STREAM     LISTENING     14569    1756/gnome-keyring- /run/user/[username]/keyring-DyljOH/ssh

```

I know next to nothing, but it seems something is not right here...

---

### Post by steeldriver on 2013-03-28
Did you revert your changes to the /etc/ssh/sshd_config file? the default port (22) should be fine within your LAN and it's possible the alternative port you chose is already in use so sshd can't bind to it

Not sure where sshd startup errors would go - you could try dmesg e.g. (on the server)

```
dmesg | grep ssh
```

to see if there's any indication why it failed (NB that might not be the correct log file)

---

### Post by capnChris on 2013-03-28
Well, long story short I uninstalled openssh using purge and reinstalled it reseting the config file to the default port 22. Now here's what I get:

```

$ sudo netstat -nlp | grep ssh
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      501/sshd        
tcp6       0      0 :::22                   :::*                    LISTEN      501/sshd        
unix  2      [ ACC ]     STREAM     LISTENING     13865    1762/ssh-agent      /tmp/ssh-CRrBQUq7eATN/agent.1727
unix  2      [ ACC ]     STREAM     LISTENING     14140    1716/gnome-keyring- /run/user/[username]/keyring-Vr59BB/ssh
$ service ssh status
ssh start/running, process 501

```

It seemed like everything was going fine, but when I tried to connect with the client it is still timing out:

```

$ ssh -vvv -l [username] [server ip]
OpenSSH_5.2p1, OpenSSL 0.9.8r 8 Feb 2011
debug1: Reading configuration data /etc/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to [server ip] [server ip] port 22.
debug1: connect to address [server ip] port 22: Operation timed out
ssh: connect to host [server ip] port 22: Operation timed out
$ ssh -l [username] [server hostname]
ssh: Could not resolve hostname [server hostname]: nodename nor servname provided, or not known

```

---

### Post by steeldriver on 2013-03-28
Hmm

Well everything looks OK on the server side - are you 100% sure you have the correct IP for the server? can you at least ping the it from the client (by IP) e.g.

```
ping -c4 192.168.1.102
```

(btw there's no need to obscure your IP if it's a private LAN IP behind a NAT router like mine). Are they both on the same LAN subnet?

Next step would be to probe the server port from the client - either using telnet, like

```
telnet 192.168.1.102 22
```

or using nmap

```
nmap -p 22 192.168.1.102
```

(I don't think either nmap or telnet are installed by default - you'd need to install them first)

---

### Post by capnChris on 2013-03-29
I tried pinging the server from my mac, and the packets were not received. Then for the heck of it, I plugged the server into the router instead of connecting via wi fi. Of course when I tried ssh using the new ip address it connected. Was I suppose to connect via ethernet? is that common knowledge I just didn't know?

---

### Post by steeldriver on 2013-03-29
no it shouldn't matter whether it is wired or wireless - provided the IP is correct and there is no firewall / iptables rule preventing the connection on a per-interface basis

---

