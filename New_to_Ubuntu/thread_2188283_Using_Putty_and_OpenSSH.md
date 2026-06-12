---
title: "Using Putty and OpenSSH"
date: 2013-11-16
forum: New to Ubuntu
---

### Post by edencrow on 2013-11-16
I've just installed Ubuntu Server 12.04.3 LTS and am trying to set-up OpenSSH so that I can use Putty on my Windows 7 machine located on the same network to access the Linux machine.
Using '*ssh localhost*' on the Linux machine allows me to SSH into the same machine, however trying to access the Linux machine with Putty on the Windows 7 machine (using the IP address given under ifconfig's '*inet address*') results in the error '*server unexpectedly closed network connection*'.
OpenSSH is installed and the *sshd_config* file has been left with its default values as changing the values as suggested at [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring) gave the same result with Putty.

---

### Post by Lars Noodén on 2013-11-16
Are you using UFW or iptables to filter your server?  If so, then you'll need to open up port 22 (ssh)

```

sudo ufw allow ssh

```

---

### Post by edencrow on 2013-11-16
> **Lars Noodén said:**
> Are you using UFW or iptables to filter your server?  If so, then you'll need to open up port 22 (ssh)

```

sudo ufw allow ssh

```

I'm not sure if I'm using UFW or iptables, I've just got the default Ubuntu with LAMP installation, perhaps there is a way I can find out to tell you? Saying that, I entered the command you suggested and got the following:

```
Rules updated
Rules updated (v6)
```

This then changed my Putty error message to '*Network Error: Connection timed out*', what would I need to do next?

---

### Post by steeldriver on 2013-11-16
Do you still have the modified sshd_config file on the target server? does it allow PasswordAuthentication (I noticed the instructions you linked say to disable that option) - you will need that option at least until you set up key-based authentication

---

### Post by Lars Noodén on 2013-11-16
I'm not quite sure how to reproduce this problem.

Lack of keys would give an error something like 'Permission denied (publickey,keyboard-interactive)', when you have password authentication turned off but try anyway.

---

### Post by edencrow on 2013-11-16
> **steeldriver said:**
> Do you still have the modified sshd_config file on the target server? does it allow PasswordAuthentication (I noticed the instructions you linked say to disable that option) - you will need that option at least until you set up key-based authentication

Here is my sshd_config file currently, which has gone back to the original *server unexpectedly closed network connection*:

```

Host *
# ForwardAgent no
# ForwardX11 no
# ForwardX11Trusted yes
# RhostsRSAAuthentication no
# RSAAuthentication yes
PasswordAuthentication yes
# HostbasedAuthentication no
# GSSAPAuthentication no
# GSSAPIDelegateCredentails no
# GSSAPIKeyExchange no
# GSSAPITrustDNS no
# BatchMode no
# CheckHostIP yes
# AddressFamily any
# ConnectTimeout 0
# StrictHostKeyChecking ask
# IdentifyFile ~/.ssh/identity
# IdentifyFile ~/.ssh/id_rsa
# Identifyfile ~/.ssh/id_dsa
Port 22
# Protocol 2,1
# Cipher 3des
# Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfiur128,aes128-cbc,3des,cbc
# MACs hmac-md5,umac-64@openssh.com,hmac-ripem160
# EscapeChar ~
# Tunnel no
# TunnelDevice any:any
# PermitLocalCommand no
# VirtualHostKey no
# ProxyCommand ssh -q -W %h%p gateway.example.com
SendEnv LANG LC_*
HasKnownHosts yes
GSAPIAuthentication yes
GSSAPIDelegateCredentials no

```

---

### Post by steeldriver on 2013-11-16
That looks like /etc/ssh_config (the ssh **client** config file) - not /etc/ssh**d**_config (the **server** config file)

---

### Post by Lars Noodén on 2013-11-16
"GSAPIAuthentication yes" is not in the default and looks spelled wrong.  Can you rem that out or temporarily use a default configuration file?

```

Port 22
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 768
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes

```

You can test the configuration file's syntax with the -T option:

```

/usr/sbin/sshd -T

```

---

### Post by edencrow on 2013-11-16
> **steeldriver said:**
> That looks like /etc/ssh_config (the ssh **client** config file) - not /etc/ssh**d**_config (the **server** config file)

Ah, yes, it does indeed say 'This is the ssh client system-wide configuration file'. Many apologies, I am new at this. I've put the client configuration file back to its default values:

```

Host *
# ForwardAgent no
# ForwardX11 no
# ForwardX11Trusted yes
# RhostsRSAAuthentication no
# RSAAuthentication yes
# PasswordAuthentication yes
# HostbasedAuthentication no
# GSSAPAuthentication no
# GSSAPIDelegateCredentails no
# GSSAPIKeyExchange no
# GSSAPITrustDNS no
# BatchMode no
# CheckHostIP yes
# AddressFamily any
# ConnectTimeout 0
# StrictHostKeyChecking ask
# IdentifyFile ~/.ssh/identity
# IdentifyFile ~/.ssh/id_rsa
# Identifyfile ~/.ssh/id_dsa
# Port 22
# Protocol 2,1
# Cipher 3des
# Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfiur128,aes128-cbc,3des,cbc
# MACs hmac-md5,umac-64@openssh.com,hmac-ripem160
# EscapeChar ~
# Tunnel no
# TunnelDevice any:any
# PermitLocalCommand no
# VirtualHostKey no
# ProxyCommand ssh -q -W %h%p gateway.example.com
SendEnv LANG LC_*
HasKnownHosts yes
GSSAPIAuthentication yes
GSSAPIDelegateCredentials no

```

However, I can not seem to be able to find a file named 'sshd_config' within /etc/ssh or /etc/. Is there somewhere else on my system I should look or a default example that I can copy over?

EDIT: Lars, looks like we posted at the same time, am reading the response from you and The Cog atm.

---

### Post by The Cog on 2013-11-16
Turning on the firewall when you are already having connectivity issues isn't helpful. Let's turn it off again:
```
sudo ufw disable
```

Let's have a look at what ports are listening on the Ubuntu server. Please post the results of:
```
netstat -lnt
```

Please check that you are setting putty to use port 22 (should happen when you select ssh, but its default is for telnet on port 23). The symptoms you describe could be explained by putty trying to connect to telnet 23 instead of ssh 22.

---

### Post by Lars Noodén on 2013-11-16
> **edencrow said:**
> 
However, I can not seem to be able to find a file named 'sshd_config' within /etc/ssh or /etc/. Is there somewhere else on my system I should look or a default example that I can copy over?

ssh**d**_config should have been added when you installed the package openssh-server.  Among the things to check, are you sure you installed that package?  The client will be there by default, but the server is something have to deliberately add.

---

### Post by edencrow on 2013-11-16
[B]Lars:
[/B]GSSAPIAuthentication was spelt incorrectly as I was just copying it down by eye and wrote it incorrectly. However, it definitely has the default configuration that was supplied for the client file.
I have created a sshd_config file with your default values you suggested, resulting in Putty complaining that the connection timed out.
I may have deleted the sshd_config file by accident, I'm reasonably sure I installed the package openssh-server, but on using 'sudo apt-get install openssh-server' I get the following:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This means that the package is missing, has been obsoleted, or is only available from another source

E: Package 'openssh-server' has no installation candidate

```
[B]
The Cog[/B]:
I have turned off the firewall and here are the results for netstat -lnt:

```

Proto Recv-Q Send-Q Local Address            Foreign Address            State

```

Here is my Putty Configuration (I'm simply entering the IP addres then clicking 'Open':

[IMG]http://i.imgur.com/nXDPPIq.png[/IMG]

---

### Post by Lars Noodén on 2013-11-16
The package openssh-server didn't get installed.  The netstat output also confirms that nothing is listening.  Once you have it up and running, netstat should show something like this:

```

tcp        0      0 0.0.0.0:**22**              0.0.0.0:*               LISTEN     

```

Maybe the package database needs to be updated and then you can try again:  

```

sudo apt-get update
sudo apt-get -f install
sudo apt-get install openssh-server

```

---

### Post by edencrow on 2013-11-16
> **Lars Noodén said:**
> The package openssh-server didn't get installed.  The netstat output also confirms that nothing is listening.  Once you have it up and running, netstat should show something like this:

```

tcp        0      0 0.0.0.0:**22**              0.0.0.0:*               LISTEN     

```

Maybe the package database needs to be updated and then you can try again:  

```

sudo apt-get update
sudo apt-get -f install
sudo apt-get install openssh-server

```

The command *sudo apt-get update* doesn't seem to be able to connect to the internet(?). Here is the result upon entering it:
```

Err http://security.ubuntu.com precise-security Release.gpg
     Temporary failure resolving 'security.ubuntu.com'
Err http://gb.archive.ubuntu.com precise Release.gpg
     Temporary failure resolving 'gb.archive.ubuntu.com'
Err http://gb.archive.ubuntu.com precise-updates Release.gpg
     Temporary failure resolving 'gb.archive.ubuntu.com'
Err http://gb.archive.ubuntu.com precise-backportsRelease.gpg
     Temporary failure resolving 'gb.archive.ubuntu.com'
Reading package list... Done
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg Temporary failure resolving 'gb/archive.ubuntu.com'

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg Temporary failure resolving 'gb/archive.ubuntu.com'

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg Temporary failure resolving 'gb/archive.ubuntu.com'

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg Temporary failure resolving 'gb/archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by The Cog on 2013-11-16
Then we are looking at a straightforward internet connectivity problem.

Please post the output of these commands:
```
ifconfig
route -n
cat /etc/resolv.conf
ping -c3 91.189.94.12
ping -c3 ubuntuforums.com
```

---

### Post by edencrow on 2013-11-16
> **The Cog said:**
> Then we are looking at a straightforward internet connectivity problem.

Please post the output of these commands:
```
ifconfig
route -n
cat /etc/resolv.conf
ping -c3 91.189.94.12
ping -c3 ubuntuforums.com
```


[B]ifconfig
[/B]```

eth0      Link encap:Ethernet HWadder 00:14:85:64:2e:2b
             inet addr:192.168.0.103 Bcast:192.168.0.255 Mask:255.255.255.0
             UP BROADCAST MULTICAST MTU:1500 Metric:1
             RX packets:0 errors:0 dropped:0 overruns:0 frame:0
             TX packets:0 errors:0 dropped: 0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000
lo           Link encap:Local Loopback
             inet addr:127.0.0.1 Mask:255.0.0.0
             inet6 addr: ::1/128 Scope:Host
             UP LOOPBACK RUNNING MTU:65536 Metric:1
             RX packets:48 errors:0 dropped:0 overruns:0 frame:0
             TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:0
             RX bytes:4760 (4.7 KB)   TX bytes:4760 (4.7 KB)

```

[B]route -n
[/B]```

Kernel IP routing table
Destination    Gateway         Genmask          Flags    Metric    Ref    Use    Iface
0.0.0.0          192.168.0.1    0.0.0.0             UG       100       0       0       eth0
192.168.0.0   0.0.0.0           255.255.255.0  U         0           0       0       eth0

```

[B]cat /etc/resolv.conf
[/B]```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
# DO NOT EDIT THIS FILE BE HAND - YOUR CHANGES WILL BE OVERWRITTEN

nameserver 8.8.8.8
search ubuntu.domain

```

[B]ping -c3 91.189.94.12
[/B]```

PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
From 192.168.0.103 icmp_seq=1 Destination Host Unreachable
From 192.168.0.103 icmp_seq=2 Destination Host Unreachable
From 192.168.0.103 icmp_seq=3 Destination Host Unreachable

--- 91.189.94.12 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2015ms
pipe 3

```

[B]
ping -c3 ubuntuforums.com
[/B]```

ping: unknown host ubuntuforums.org

```

---

### Post by The Cog on 2013-11-16
Interface eth0 has no IP address. Also, it is missing the word RUNNING, which I believe means that it doesn't believe the link is up. 
It is as though the ethernet cable is not plugged in.

Can we double-check with the command:
```
ip -s link
```
but also look at what make of NIC and driver is is use with the command:
```
lspci -v
```
No need to post the whole output of lspci, just the paragraph about the network adapter.

---

### Post by edencrow on 2013-11-16
> **The Cog said:**
> Interface eth0 has no IP address. Also, it is missing the word RUNNING, which I believe means that it doesn't believe the link is up. 
It is as though the ethernet cable is not plugged in.

Can we double-check with the command:
```
ip -s link
```
but also look at what make of NIC and driver is is use with the command:
```
lspci -v
```
No need to post the whole output of lspci, just the paragraph about the network adapter.

Ah.... seems like someone had removed the ethernet cable and so it wasn't connected to my network at all ](*,)

I've plugged in the cable and tried Putty which gave the error 'Server unexpectedly closed network connection'.

Here are the command outputs now:

[B]
ifconfig
[/B]```

eth0      Link encap:Ethernet HWadder 00:14:85:64:2e:2b
             inet addr:192.168.0.103 Bcast:192.168.0.255 Mask:255.255.255.0
             inet6 addr: fe80::214:85ff:fe64:2e2b/64 Scope:Link
             UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
             RX packets:0 errors:0 dropped:0 overruns:0 frame:0
             TX packets:0 errors:0 dropped: 0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000
             RX bytes:14589 (14.5 KB) TX bytes:7482 (7.4 KB)
lo           Link encap:Local Loopback
             inet addr:127.0.0.1 Mask:255.0.0.0
             inet6 addr: ::1/128 Scope:Host
             UP LOOPBACK RUNNING MTU:65536 Metric:1
             RX packets:48 errors:0 dropped:0 overruns:0 frame:0
             TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:0
             RX bytes:5484(5.4 KB)   TX bytes:5484(5.4 KB)

```

[B]
route -n
[/B]Same

[B]cat /etc/resolv.conf
[/B]*Same*
[B]ping -c3 91.189.94.12
[/B]```

PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
64 bytes from 91.189.94.12: icmp_req=1 ttl=53 time=30.2 ms
64 bytes from 91.189.94.12 icmp_req=2 ttl=53 time=32.4 ms
64 bytes from 91.189.94.12: icmp_req=3 ttl=53 time=29.9ms

--- 91.189.94.12 ping statistics ---
3 packets transmitted, 3 recieved, 0% packet loss, time 2002ms
rtt min/aug/max/mdev = 29.920/30.877/32.458/1.126 ms

```
[B]
ping -c3  ubuntuforums.com
[/B][I]&#8203;Same

[/I]EDIT: sudo apt-get update is now working so I'll try installing the server package now

---

### Post by edencrow on 2013-11-16
Many apologies for making such a stupid earlier, however, internet connection has now been made and I have installed *openssh-server *and run */usr/sbin/sshd -T*, which failed to find any syntax errors with the ssd_config file as shown by Lars [here]("http://ubuntuforums.org/showthread.php?t=2188283&p=12849496#post12849496") (#8). Putty still gives the error 'Server unexpectedly closed network connection'. What would be my next step?

---

### Post by Lars Noodén on 2013-11-16
PuTTY and the Linux machine are on the same LAN presumably?    Check the current ip address to make sure you have the right one now that everything is installed.  

```

ifconfig eth0

```

Then try connecting to that address from the Linux machine itself.  Let's see if that's working first.

---

### Post by edencrow on 2013-11-16
> **Lars Noodén said:**
> PuTTY and the Linux machine are on the same LAN presumably?    Check the current ip address to make sure you have the right one now that everything is installed.  

```

ifconfig eth0

```

Then try connecting to that address from the Linux machine itself.  Let's see if that's working first.

They are on the same LAN. Connecting from the Linux machine itself via SSH also works as it should now.

---

### Post by Lars Noodén on 2013-11-16
All the standard tools are missing from Windows so I would have no guess where to start there.  You could watch what the server says for a single connection but that's going to be a wall of text as you try to connect.  This will allow one connection:

```

sudo service ssh stop
sudo /usr/sbin/sshd -Dd

```

Rerun sshd to try another connection attempt.  

Run "sudo service ssh start" to restore regular service.

---

### Post by The Cog on 2013-11-16
All the standard tools are missing from Windows so we can't do much from that side.
My next steps would be:
Check the ssh log to see if it is refusing the connection for some reason:
```
grep ssh /var/log/auth.log
```

And of that doesn't help, I would be to use tcpdump on the ubuntu box to see what is going on. Run this command to take a packet trace:
```
sudo tcpdump -np
```
and then try to connect from the windows PC. As soon as you get a response on the windows box, you can stop the trace on Ubuntu with Ctrl-C.
The trace may not mean much to you, so post it here and we'll have a look.

---

### Post by edencrow on 2013-11-16
> **Lars Noodén said:**
> All the standard tools are missing from Windows so I would have no guess where to start there.  You could watch what the server says for a single connection but that's going to be a wall of text as you try to connect.  This will allow one connection:

```

sudo service ssh stop
sudo /usr/sbin/sshd -Dd

```

Rerun sshd to try another connection attempt.  

Run "sudo service ssh start" to restore regular service.

I can use [Cygwin]("http://www.cygwin.com/") to use bash commands on my Windows computer (including trying to use SSH from there, which also just times out).
I'm not sure if I followed what your saying, but I think you meant that I should try to connect after running the two commands in the code box? If so, I did that and came out with the following:

```

debug1: sshd version OpenSSH_5.9p1 Debian-5ubuntu1.1
debug1: could not open key file '/etc/ssh/ss_host_rsa_key': No such file or directory
Could not load host key: /etc/ssh/ss_host_rsa_key
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /usr/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: could not open key file '/etc/ssh/ssh_host_ecdsa_key': No such file or directory
Could not load hostkey: '/etc/ssh.ssh_host_ecdsa_key
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug: rexec_argv[1]='Dd'
Set /proc/self/oom_score_adj from 0 to -1000
debug1: Bind to port 22 on 0.0.0.0
Server listning to port 22 on 0.0.0.0
debug1: Bind to port 22 on ::.
Server listening on :: port 22.

```

I then tried to connect, but the connection just times out and no more debug information is shown on the Linux machine.

---

### Post by Iowan on 2013-11-16
> **edencrow said:**
> 

```

debug1: sshd version OpenSSH_5.9p1 Debian-5ubuntu1.1
debug1: could not open key file '/etc/ssh/ss_host_rsa_key': No such file or directory
Could not load host key: /etc/ssh/ss_host_rsa_key
....
debug1: could not open key file '/etc/ssh/ssh_host_ecdsa_key': No such file or directory
Could not load hostkey: '/etc/ssh.ssh_host_ecdsa_key

```

....On my machine, those files are **/etc/ssh/ss[COLOR="#FF0000"]h[/COLOR]_host_rsa_key** and **/etc/ssh.ssh_host_dsa_key**
Check **/etc/ssh/sshd_config** for typos/corruption.

---

### Post by Lars Noodén on 2013-11-16
'/etc/ssh/ss_host_rsa_key' should be '/etc/ssh/ssh_host_rsa_key' and the line about ecdsa can be remmed out since  it is not relevant for version 5.9

Since the server makes no noise when you try to connect, I think you are not reaching the right port or maybe not even the machine at all.  So check The Cog's suggestion with tcpdump.

Then make sure you are trying port 22 in PuTTY.

Maybe if you have ssh in bash, you can try connecting with "ssh -v" to see what the client says.

---

### Post by The Cog on 2013-11-16
Is it possible that the windows firewall is blocking the outgoing connections? Or some antivirus program? I remember that I once had to remove some AV software from a windows PC because it was blocking outgoing emails.

A trace with tcpdump would tell us if packets from windows are even reaching the Ubuntu server.

---

### Post by steeldriver on 2013-11-16
The *is* actually a usable command-line telnet client in Windows 7 (at least in Pro) - you need to go to Control Panel --> Programs and Features --> Turn Windows features on or off. Then there should be a checkbox for Telnet Client.

You can then run cmd.exe and

```

C:\Users\steeldriver>telnet 192.168.1.102 22
SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1

```

That should rule out any possible PuTTY misconfig issue

---

### Post by Doug S on 2013-11-16
> **The Cog said:**
> All the standard tools are missing from Windows so we can't do much from that side.I agree that a lot of good stuff is missing from windows, but "ping" is there. I would be tempted to try it:```
ping 192.168.0.103
```An example from my windows computer:```
C:\Users\Doug\SPlot\SPlot>[COLOR=#ff0000]ping 192.168.111.112[/COLOR]

Pinging 192.168.111.112 with 32 bytes of data:
Reply from 192.168.111.112: bytes=32 time<1ms TTL=64
Reply from 192.168.111.112: bytes=32 time<1ms TTL=64
Reply from 192.168.111.112: bytes=32 time<1ms TTL=64
Reply from 192.168.111.112: bytes=32 time<1ms TTL=64

Ping statistics for 192.168.111.112:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```

Edit: I had not seen the post by Steeldriver when I posted. I also didn't know about the method for enabling telnet clients in windows, as I just tend to use one of my ubutnu computers for telnet type tests. Anyway, it took about 25 minutes to finish the enable, then I got just like steeldriver:```
C:\Users\Doug\SPlot\SPlot>[COLOR=#ff0000]telnet 192.168.111.112 22[/COLOR]
SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1
Protocol mismatch.     [COLOR=#ff0000]<<< After I type a carriage return, and as expected, since telnet protocol is not correct.[/COLOR]
Connection to host lost.
C:\Users\Doug\SPlot\SPlot>
```

---

### Post by edencrow on 2013-11-17
Pinging the server seems to work:
[IMG]http://i.imgur.com/VkNUSds.png[/IMG]

I've also edited /etc/ssh/sshd_config to correct the typo mentioned by Iowan and Lars.

The result from tcpdump seems to vary, so I ran it three times (sometimes via Cygwin, sometimes via command prompt) and got the following result: [http://i.imgur.com/9t6RpE3.jpg](http://i.imgur.com/9t6RpE3.jpg)

---

### Post by Doug S on 2013-11-17
It seems as though SSH packets are not even arriving at your computer. Consider post #27 above by The Cog. You would expect to get something like this for a PuTTY session start (up to asking for password):```
2013-11-17 08:06:07.100472 IP 192.168.111.101.20102 > 192.168.111.1.22: Flags [S], seq 3947282964, win 8192, options [mss 1460,nop,nop,sackOK], length 0
2013-11-17 08:06:07.100546 IP 192.168.111.1.22 > 192.168.111.101.20102: Flags [S.], seq 533083116, ack 3947282965, win 14600, options [mss 1460,nop,nop,sackOK], length 0
2013-11-17 08:06:07.100859 IP 192.168.111.101.20102 > 192.168.111.1.22: Flags [.], ack 1, win 64240, length 0
2013-11-17 08:06:07.110831 IP 192.168.111.1.22 > 192.168.111.101.20102: Flags [P.], seq 1:42, ack 1, win 14600, length 41
2013-11-17 08:06:07.125420 IP 192.168.111.101.20102 > 192.168.111.1.22: Flags [P.], seq 1:29, ack 42, win 64199, length 28
2013-11-17 08:06:07.125463 IP 192.168.111.101.20102 > 192.168.111.1.22: Flags [P.], seq 29:701, ack 42, win 64199, length 672
2013-11-17 08:06:07.125525 IP 192.168.111.1.22 > 192.168.111.101.20102: Flags [.], ack 29, win 14600, length 0
2013-11-17 08:06:07.125536 IP 192.168.111.1.22 > 192.168.111.101.20102: Flags [.], ack 701, win 15456, length 0
2013-11-17 08:06:07.126451 IP 192.168.111.1.22 > 192.168.111.101.20102: Flags [P.], seq 42:1026, ack 701, win 15456, length 984
2013-11-17 08:06:07.137034 IP 192.168.111.101.20102 > 192.168.111.1.22: Flags [P.], seq 701:717, ack 1026, win 63215, length 16
2013-11-17 08:06:07.139529 IP 192.168.111.1.22 > 192.168.111.101.20102: Flags [P.], seq 1026:1562, ack 717, win 15456, length 536
2013-11-17 08:06:07.339669 IP 192.168.111.101.20102 > 192.168.111.1.22: Flags [.], ack 1562, win 64240, length 0
2013-11-17 08:06:07.345838 IP 192.168.111.101.20102 > 192.168.111.1.22: Flags [P.], seq 717:1245, ack 1562, win 64240, length 528
2013-11-17 08:06:07.369687 IP 192.168.111.1.22 > 192.168.111.101.20102: Flags [P.], seq 1562:2666, ack 1245, win 16800, length 1104
2013-11-17 08:06:07.558086 IP 192.168.111.101.20102 > 192.168.111.1.22: Flags [.], ack 2666, win 63136, length 0
2013-11-17 08:06:07.574566 IP 192.168.111.101.20102 > 192.168.111.1.22: Flags [P.], seq 1245:1261, ack 2666, win 63136, length 16
2013-11-17 08:06:07.574831 IP 192.168.111.101.20102 > 192.168.111.1.22: Flags [P.], seq 1261:1325, ack 2666, win 63136, length 64
2013-11-17 08:06:07.574890 IP 192.168.111.1.22 > 192.168.111.101.20102: Flags [.], ack 1325, win 16800, length 0
2013-11-17 08:06:07.574947 IP 192.168.111.1.22 > 192.168.111.101.20102: Flags [P.], seq 2666:2730, ack 1325, win 16800, length 64
2013-11-17 08:06:07.776631 IP 192.168.111.101.20102 > 192.168.111.1.22: Flags [.], ack 2730, win 63072, length 0
```I used this command:```
sudo tcpdump -n -tttt -i eth0 port 22 >bbb
```And you would expect to see a related log entry:```
doug@doug-64:~$ [COLOR=#ff0000]tail -10 /var/log/auth.log[/COLOR]
Nov 17 08:05:42 doug-64 sudo:     doug : TTY=tty3 ; PWD=/home/doug ; USER=root ; COMMAND=/usr/sbin/tcpdump -n -tttt -i eth0 port 22
Nov 17 08:05:42 doug-64 sudo: pam_unix(sudo:session): session opened for user root by doug(uid=1000)
Nov 17 08:06:07 doug-64 sshd[13517]: Set /proc/self/oom_score_adj to 0
Nov 17 08:06:07 doug-64 sshd[13517]: [COLOR=#ff0000]Connection from 192.168.111.101 port 20102[/COLOR]
Nov 17 08:06:19 doug-64 sudo: pam_unix(sudo:session): session closed for user root  [COLOR=#ff0000]<<< End of tcpdump capture shown above[/COLOR]
Nov 17 08:06:36 doug-64 sshd[13517]: Accepted password for doug from 192.168.111.101 port 20102 ssh2 [COLOR=#ff0000]<<< I continued to log in[/COLOR]
Nov 17 08:06:36 doug-64 sshd[13517]: pam_unix(sshd:session): session opened for user doug by (uid=0)
Nov 17 08:06:36 doug-64 sshd[13517]: User child is on pid 13655
Nov 17 08:09:01 doug-64 CRON[13755]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 17 08:09:01 doug-64 CRON[13755]: pam_unix(cron:session): session closed for user root
```

Edit: I only redirected the output of tcpdump so that I could get at it to include herein. I also didn't specify the host as in Lars' example below because I knew there wouldn't be any other port 22 packets on my LAN.

---

### Post by Lars Noodén on 2013-11-17
That you can ping the computer is a start.  

About tcpdump, it needs to be run on the machine with the ssh server to use it to see what is coming from your other computer.  To trim down the traffic, you can restrict it to listen to one machine.

```

sudo tcpdump -n -tttt -i eth0 "port 22 and host 192.168.0.XX" | tee bbb

```

Where 192.168.0.XX would be filled in with the ip of the client machine you are trying to connect from.  The *[tee](http://manpages.ubuntu.com/manpages/saucy/en/man1/tee.1posix.html) bbb* part redirects the output to the file *bbb* while still showing output on the screen.  Turn on tcpdump and then try to connect from It might produce produce a lot of traffic.  You can review **bbb** with [less](http://manpages.ubuntu.com/manpages/saucy/en/man1/less.1.html).

```

less bbb

```
If you have ssh in Cygwin, you could try connecting with "ssh -v" instead of "ssh" to see any extra messages.

---

