---
title: "ssh not working"
date: 2013-05-27
forum: New to Ubuntu
---

### Post by adityaharish on 2013-05-27
[SIZE=3][SIZE=2]Cannot connect to my own pc using ssh..[/SIZE]

shraddesh@shraddesh-Samsung-Desktop-System:~$ ssh shraddesh@107.109.39.192
ssh: connect to host 107.109.39.192 port 22: Connection refused
shraddesh@shraddesh-Samsung-Desktop-System:~$ 
[/SIZE]

There is no problem with the network connection . So Please help me in solving this problem

Thanks & Regards 
Aditya

---

### Post by sudodus on 2013-05-27
- Are you running the ssh server on the other pc?

- Do you have a firewall, that has closed port 22?

---

### Post by zeljkojagust on 2013-05-27
Check if you have openssh-server package installed. Also check firewall (iptables or ufw) if port 22 is blocked.

---

### Post by lethall1 on 2013-05-27
from the ssh-server
```
sudo apt-get install nmap
nmap localhost
```

if you are sure, that openssh-server is installed, try run this:
```
sudo service ssh restart
ssh user@localhost
```

---

### Post by HermanAB on 2013-05-27
Turn debug messages on:
$ ssh -vvv shraddesh@107.109.39.192

---

### Post by adityaharish on 2013-05-27
Thanks all !!! 
It's working now . I re-installed openshh-server & nmap

---

### Post by adityaharish on 2013-05-27
Why do we get this message when we connect to another remote pc using ssh & What does this mean ??
[B]
Write failed: Broken pipe[/B]

When I connect to a server using ssh the above msg pop's up every time a few seconds after I login

---

### Post by Lars Noodén on 2013-05-27
> **adityaharish said:**
> I re-installed openshh-server & nmap

nmap will be of very limited value if you run it on the same machine you are scanning.  For best, most accurate results, you need to run it from a second machine.

---

### Post by adityaharish on 2013-05-27
I can't connect to my pc using ssh from a second machine . 
It's always showing this error 

[FONT=arial black]bash-4.1$ scp test.zip shraddesh@107.109.39.132:/home/shraddesh/
ssh: connect to host 107.109.39.132 port 22: Connection timed out
lost connection[/FONT]

I tried the above from another pc 

How can I solve this problem ??

---

### Post by Lars Noodén on 2013-05-27
Can you connect to 107.109.39.132 from any other pcs, or is it just the one giving the problem?

If you cannot connect from others, check that sshd is running on 107.109.39.132 and listening at port 22:

```

service ssh status
pgrep -lf sshd
sudo netstat -nltp | grep :22

```

The last two should have lines of output containing 'sshd'

If sshd is not running on 107.109.39.132 then try starting it.

```

sudo service restart

```

---

### Post by lethall1 on 2013-05-27
if nmap localhost shows 22 port open may be some reason to solve it:
1. ssh listen only localhost address or network ( look sshd.conf)
2. May be your firewall block connection on port 22 (look sudo iptables -L )

---

### Post by adityaharish on 2013-05-27
Lars Nooden

This is the Output I get when I run the above commands in 107.109.39.192 i.e my pc 

[B]shraddesh@shraddesh-Samsung-Desktop-System:~$ sudo service ssh status
ssh start/running, process 29643
shraddesh@shraddesh-Samsung-Desktop-System:~$ pgrep -lf sshd
29643 /usr/sbin/sshd -D
shraddesh@shraddesh-Samsung-Desktop-System:~$ sudo netstat -nltp | grep :22
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      29643/sshd      
tcp6       0      0 :::22                   :::*                    LISTEN      29643/sshd      
shraddesh@shraddesh-Samsung-Desktop-System:~$ [/B]
[B]shraddesh@shraddesh-Samsung-Desktop-System:~$ sudo service ssh restart
ssh stop/waiting
ssh start/running, process 32223
shraddesh@shraddesh-Samsung-Desktop-System:~$ [/B]


Even then I'm not able to connect to my pc from other pc's using ssh ..

---

### Post by Doug S on 2013-05-28
A few have already asked this, but I'll ask again: Do you have a firewall running? And it is blocking a new incoming TCP connection for port 22? Post the output from:```
sudo iptables -v -x -n -L
```

---

### Post by adityaharish on 2013-05-28
This the command

Code :  
                   *  sudo iptables -v -x -n -L*

Then the output is:
Code:

[B]shraddesh@shraddesh-Samsung-Desktop-System:~$ sudo iptables  -v -x -n -L
Chain INPUT (policy ACCEPT 24200 packets, 21021184 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 16096 packets, 1572431 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
shraddesh@shraddesh-Samsung-Desktop-System:~$ 
[/B]

---

### Post by adityaharish on 2013-05-28
This is what I'm getting now

[B]-bash-4.1$ scp adityatest.zip shraddesh@107.109.39.132:/home/shraddesh/
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
34:49:28:37:06:84:51:84:96:dc:5d:fd:59:7b:c2:f3.
Please contact your system administrator.
Add correct host key in /data1/stereo/.ssh/known_hosts to get rid of this message.
Offending key in /data1/stereo/.ssh/known_hosts:2
RSA host key for 107.109.39.132 has changed and you have requested strict checking.
Host key verification failed.
lost connection[/B]

What has changed ?

---

### Post by Doug S on 2013-05-28
O.K., so you do not have a firewall running. Is the computer behind a router and the router is actually 107.109.39.192? If yes, you would need port forwarding from the router to your computer. I.E. is the IP address of the computer you are trying to connect to 107.109.39.192? Or is it's IP address some other non-routable IP address, such as 192.168.XXX.XXX? If you are not sure, post the output of:```
ifconfig
```

Edit: Oh, I see you made another posting, and it seems to be connecting now. I do not know what has changed so that it now connects.

---

### Post by adityaharish on 2013-05-28
This is the output when I run the command

Code :
[B]shraddesh@shraddesh-Samsung-Desktop-System:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e8:11:32:36:d3:7c  
          inet addr:107.109.39.132  Bcast:107.109.39.255  Mask:255.255.255.0
          inet6 addr: fe80::ea11:32ff:fe36:d37c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:370600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108166927 (108.1 MB)  TX bytes:4245209 (4.2 MB)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4086 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:391235 (391.2 KB)  TX bytes:391235 (391.2 KB)
[/B]

Moreover I now I cannot connect , it shows the error msg I posted above 
[B]-bash-4.1$ scp adityatest.zip shraddesh@107.109.39.132:/home/shraddesh/
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@  @@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@  @@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
34:49:28:37:06:84:51:84:96:dc:5d:fd:59:7b:c2:f3.
Please contact your system administrator.
Add correct host key in /data1/stereo/.ssh/known_hosts to get rid of this message.
Offending key in /data1/stereo/.ssh/known_hosts:2
RSA host key for 107.109.39.132 has changed and you have requested strict checking.
Host key verification failed.
lost connection[/B]

how do I get rid pf this ??

---

### Post by HermanAB on 2013-05-28
You can simply delete the file data1/stereo/.ssh/known_hosts

and try ssh again.

---

### Post by adityaharish on 2013-05-28
Herman AB .. thanks man ..
It works .. But is it good to remove the file ? Don't we have any other options ??

---

### Post by sudodus on 2013-05-28
> **adityaharish said:**
> Herman AB .. thanks man ..
It works .. But is it good to remove the file ? Don't we have any other options ??

Check if a new instance with that file name was created again! (And look at its content, if it is there and you are curious)

---

### Post by Lars Noodén on 2013-05-28
> **adityaharish said:**
> Herman AB .. thanks man ..
It works .. But is it good to remove the file ? Don't we have any other options ??

Rather than deleting the whole file, you can remove a single key using [ssh-keygen](http://manpages.ubuntu.com/manpages/raring/en/man1/ssh-keygen.1.html)

```

ssh-keygen -R 107.109.39.132

```

Then then next time you connect you will be presented with the new key to verify before accepting or rejecting.  Make sure it really is the right one before accepting it.  Reject it if it is not the right key and let us know, that is also help in debugging.

---

### Post by adityaharish on 2013-05-28
checked it and modified the old file .. now it works fine ..
Thanks All

---

### Post by HermanAB on 2013-05-28
"But is it good to remove the file ?"
It is a check and warning system.  You have been warned and you are now testing things, so it is OK to remove the file, because you are now actively checking things and making sure it connects correctly.  SSH will make a new one again and will warn you next time it sees something funny.

---

### Post by Lars Noodén on 2013-05-28
> **HermanAB said:**
> It is a check and warning system.  You have been warned and you are now testing things, so it is OK to remove the file, because you are now actively checking things and making sure it connects correctly.  SSH will make a new one again and will warn you next time it sees something funny.

There can be large numbers of keys in a working ~/.ssh/known_hosts, and erasing the whole file nukes all of those keys even the ones that are still valid.  *known_hosts* can be instead edited by hand to remove the one offending key or else the work can be done by [ssh-keygen -R](http://manpages.ubuntu.com/manpages/raring/en/man1/ssh-keygen.1.html).  Either way still preserves the valid keys in *known_hosts*.

---

