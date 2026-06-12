---
title: "SSH setup issues"
date: 2021-03-19
forum: New to Ubuntu
---

### Post by netrix-g on 2021-03-19
I have tried to follow other posts on here but still haven't got very far unfortunately.

I have a new install of Ubuntu 20.04 LTS.

I have followed a couple of guides for setting up SSH - not even getting to RSA keys at the moment and having trouble.

so far on the Ubuntu server:
myusername is has elevated privileges, ie $ sign at command line.

**sudo systemctl status ssh **confirms active and running

I can connect using **ssh -p 54321 localhost **[I am asked for a password - I use the password for the user I am logged in with]
I cannot connect using **ssh -p 54321 myusername@IP address** [I get a connection refused message]

On the lan [from Macbook] using **ssh -p 54321 myusername@IP address **I also get a connection refused message
I can ping the IP address from the mac

The only update I have made to the sshd_config file is to change the ssh port number and set PermitRootLogin to no

the firewall [ufw] has these entries:
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere                  
54321/tcp                  ALLOW       Anywhere                  
OpenSSH (v6)               ALLOW       Anywhere (v6)             
54321/tcp (v6)             ALLOW       Anywhere (v6)   


Trying to troubleshoot via other threads is getting too confusing at present so I had to post here. I appreciate your help and I have a mental bet that I have missed something extremely fundamental !!
I will hold off posting logs at the moment as I have seen lots asked for at different stages in other threads, so I'll wait to post what is required for my issue, and hopefully learn a bit more as I go !
Thanks in advance

Netrix

---

### Post by CatKiller on 2021-03-19
> **netrix-g said:**
> I cannot connect using **ssh -p 54321 myusername@IP address** [I get a connection refused message]

On the lan [from Macbook] using **ssh -p 54321 myusername@IP address **I also get a connection refused message

If you're trying to use your Internet-facing IP address then there won't be a route to your machine unless you set up port forwarding on your router to create one.

If you're trying to use your LAN-facing IP address then it should already work if you've got things set up correctly.

---

### Post by netrix-g on 2021-03-19
Hi CatKiller,

In my post I am referring to the IP address of the Ubuntu server.

From the command line on that server or a terminal window on my macbook (same subnet) I get the connection refused message - so I am trying to find out where I have the issues in the SSH setup.

Regards

Netrix

---

### Post by ActionParsnip on 2021-03-19
Is the Mac and Ubuntu SSH server on the same subnet?

---

### Post by netrix-g on 2021-03-19
> **ActionParsnip said:**
> Is the Mac and Ubuntu SSH server on the same subnet?


Hiya
Yes, this is on my home network - class C network no subnets etc.
The mac can ping the Ubuntu server and server can ping mac

The more I fault find at the moment the more confused I get :( 

Regards

Netrix

---

### Post by ActionParsnip on 2021-03-19
Try running:
```

ssh -p 54321 -vvvvvv myusername@IP address

```
Read the output carefully from top to bottom and you should see where the issue is

---

### Post by netrix-g on 2021-03-19
> **ActionParsnip said:**
> Try running:
```

ssh -p 54321 -vvvvvv myusername@IP address

```
Read the output carefully from top to bottom and you should see where the issue is

Thank you for the pointer ...

I now know one of my mistakes was confusing the ssh and sshd config files  

I have changed the port again so my command was:

```
ssh -p 62662 -vvvvvv netrix@192.168.1.88
```
which returned:
>                          netrix@reulcsap028:~$ ssh -p 62662 -vvvvvv netrix@192.168.1.88
 OpenSSH_8.2p1 Ubuntu-4ubuntu0.2, OpenSSL 1.1.1f  31 Mar 2020
 debug1: Reading configuration data /etc/ssh/ssh_config
 debug1: /etc/ssh/ssh_config line 19: include /etc/ssh/ssh_config.d/*.conf **[COLOR=#ff0000]matched no files[/COLOR]**
 debug1: /etc/ssh/ssh_config line 21: Applying options for *
 debug2: resolve_canonicalize: hostname 192.168.1.88 is address
 debug2: ssh_connect_direct
 debug1: Connecting to 192.168.1.88 [192.168.1.88] port 62662.
 debug1: connect to address 192.168.1.88 port 62662: Connection refused
 ssh: connect to host 192.168.1.88 port 62662: Connection refused
  

I have no idea what this line is meant to be doing yet:
> debug1: /etc/ssh/ssh_config line 19: include /etc/ssh/ssh_config.d/*.conf **[COLOR=#ff0000]matched no files[/COLOR]**

So I hashed it out in the config file (this is where I realised one of my errors as I was looking in the wrong file)

With that line hashed out I still get a refused connection so I'm assuming that the line should be there but shouldn't return the "no files matched" error ? (Google isn't helping much)

> netrix@reulcsap028:~$ ssh -p 62662 -vvvvvv netrix@192.168.1.88
OpenSSH_8.2p1 Ubuntu-4ubuntu0.2, OpenSSL 1.1.1f  31 Mar 2020
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 21: Applying options for *
debug2: resolve_canonicalize: hostname 192.168.1.88 is address
debug2: ssh_connect_direct
debug1: Connecting to 192.168.1.88 [192.168.1.88] port 62662.
debug1: connect to address 192.168.1.88 port 62662: Connection refused
ssh: connect to host 192.168.1.88 port 62662: Connection refused



In the ssh_config file there is a line saying **Host * **which I assume is a wildcard - I replaced the ***** with 192.168.1.88 with no change to the debug messages.

Lastly - the ssh port number was originally only changed in the **sshd_config** file - it was hashed out in the **ssh_config **file - adding 62662 to the ssh_config file again made no difference to the debug messages.

To recap
```
ssh -p 62662 -vvvvvv netrix@192.168.1.88
```

Gives me this

```
 netrix@reulcsap028:~$ ssh -p 62662 -vvvvvv netrix@192.168.1.88
 OpenSSH_8.2p1 Ubuntu-4ubuntu0.2, OpenSSL 1.1.1f  31 Mar 2020
 debug1: Reading configuration data /etc/ssh/ssh_config
 debug1: /etc/ssh/ssh_config line 19: include /etc/ssh/ssh_config.d/*.conf matched no files
 debug1: /etc/ssh/ssh_config line 21: Applying options for *
 debug2: resolve_canonicalize: hostname 192.168.1.88 is address
 debug2: ssh_connect_direct
 debug1: Connecting to 192.168.1.88 [192.168.1.88] port 62662.
 debug1: connect to address 192.168.1.88 port 62662: Connection refused
 ssh: connect to host 192.168.1.88 port 62662: Connection refused
  
```

Any advice on next steps ??

Thanks and regards

Netrix

---

### Post by The Cog on 2021-03-19
Try the command:
```
ss -lntp
```
and look at the line for port 54321. Is it listening on 0.0.0 (meaning all addresses) or just on 127.0.0.1? 
The listening address is configured in /etc/ssh/sshd_config if you need to change it.
Connection refused suggests it's not a firewall problem, because firewalls normally just drop packets so you would get timeout. Connection Refused means you actually received a reply refusing the connection.

P.S.
In case it's not clear yet: 
- ssh_config is for your ssh client which you use for making outgoing calls
- sshd_config is for your sshd (ssh daemon) server, which listens for incoming connections.

---

### Post by netrix-g on 2021-03-19
Hi Cog,

> and look at the line for port 54321. Is it listening on 0.0.0 (meaning all addresses) or just on 127.0.0.1?

I have changed the port in the sshd_config file to 62662

The output from 
```
ss -lntp
```

is

```
netrix@reulcsap028:~$ ss -lntp
State       Recv-Q      Send-Q             Local Address:Port              Peer Address:Port      Process      
LISTEN      0           4096               127.0.0.53%lo:53                     0.0.0.0:*                      
LISTEN      0           5                      127.0.0.1:631                    0.0.0.0:*                      
[COLOR=#ff0000]**LISTEN      0           128                      0.0.0.0:62662                  0.0.0.0:*      **[/COLOR]                
LISTEN      0           5                          [::1]:631                       [::]:*                      
LISTEN      0           128                         [::]:62662                     [::]:*                      
```


Regarding the ssh_config file - should the port number be changed in there also to reflect new port number ?

---

### Post by TheFu on 2021-03-19
Why use non-standard ports internally?  Get everything working on port 22/tcp first, then screw around with any different ports, as needed.  I find that letting the router to port-translation on the public internet into the normal port for my internal ssh server is sufficient.  Then when I connect internally, I can choose to connect directly on the LAN or use the non-standard WAN port on the router like I'm outside.

sshd sorta just works.  When you install the ssh-server package, it is enabled and started on port 22.  If the firewall isn't already enabled, it will work.  Then any client on the same LAN should be able to connect.  But if the firewall is enabled, you'll need to disable it for quick testing or open the 22/tcp for inbound LAN connections

The ssh server should have a LAN static IP, if that hasn't been said already.  Static IPs on your LAN make things easier. I force my portable devices to have static IPs on my LAN because it is so much more convenience.  When they are on other networks, they get DHCP addresses. For computers that will never be on other LANs, those are locally configured -on-that-system- to have a static IP.  My internal DNS server knows where each system should be - name <----> IP xref.  If you have 5 systems or less, just copying 5 lines into the /etc/hosts file on each computer can achieve the same results as a DNS server.

If you've screwed around so much that you don't know what is what, maybe best to start over?  I can post 3 commands for the ssh server and 3 commands for a linux ssh client to have a working solution.  Just ask.  With 2 more commands, we can have the client create and setup ssh-key-based authentication which is very secure and extremely convenient.

---

### Post by The Cog on 2021-03-19
> Regarding the ssh_config file - should the port number be changed in there also to reflect new port number ? 
No. I would leave the ssh client config at default unless you have good reason and know why you want to change it.

The Debian server is listening on all addresses, so it's not the OS that is issuing rejections. Which makes me wonder what is doing the rejection.
Let's co back to basics and eliminate possible ssh oddities. Try these commands on the Ubuntu server:
```
nc -v 127.0.0.1 62662
nc -v 192.168.1.88  62662
```
Both of these should print the version number message from the server - you need to Ctrl-C to end the connection.
This shows that the ssh server is listening on the ports we think it is.
If the second doesn't work, use this command to check your IP addresses are what you think they are:
```
hostname -I
```

If the above all works as expected, let's look at the network traffic and see if it's your server that is actually rejecting the call. On the Ubuntu server:
Use the command "ip address" to list your local addresses and find the interface name that is the local LAN. Use that interface name in this command:
```
sudo tcpdump -nnt -i <interface name> tcp port 62662
```
Then on the mac, try to ssh the Ubuntu box. You should see traffic being reported by tcpdump. Post the output here so we can try figure out what's happening and where to go from there.

---

### Post by netrix-g on 2021-03-20
Hi Cog,

I'm just off to find the embarrassed smiley ................. here you go  :redface:
This failed ```
nc -v 192.168.1.88  62662
```

And this
```
hostname -I
```
Showed me my IP address **was not **192.168.1.88 :eek:

I've corrected that now [set static IP on Router for the server] and to explain my confusion, when I received the server it had Win2008 on it, and I was playing around with the ILO port to see what it could do etc That is where the 192.168.1.88 fixed IP address came from. The ILO port was left patched after the Ubuntu install hence why it would ping and the MAC address against 192.168.1.88 in the router, when checked online for the vendor, came back as HPE, fooling me into thinking that it was the correct IP for the Ubuntu Lan address. 

It is indeed a steep learning curve for me but doesn't help when I make school-boy type errors !! 

Thanks again for your patience/help - off now to secure the ssh by adding some keys - do I put them in the DVD drawer I wonder ??? :lol:

Regards

Netrix

---

### Post by ActionParsnip on 2021-03-20
Just to check, are you restarting the SSH service after updating the config file on the server side? This is needed to reread the new settings in the configuration file

---

### Post by netrix-g on 2021-03-20
Hi TheFu,

Thank you for the pointers and offer to help.

I had uninstalled Openssh and reinstalled, trying everything as default but had the same errors - but I am embarrassed to say that I had my IP address for the server noted down incorrectly - I was ssh'ing to the IP address for the ILO port of the server (I played around with the ILO port when I first received the server and set a static IP on it - it was running Win2008 then) Hence why it returned ping etc.

I have now rectified that (pretty basic) error and set a static IP for the lan nic of the server.

I'm off to set up a bit more security for ssh now - I may take you up on your offer of help but would like to try first :)

Thanks again,

Regards

Netrix

---

### Post by netrix-g on 2021-03-20
> **ActionParsnip said:**
> Just to check, are you restarting the SSH service after updating the config file on the server side? This is needed to reread the new settings in the configuration file

I am indeed, but thanks for checking !

Regards

Netrix

---

### Post by The Cog on 2021-03-20
Glad you got it sorted. Don't be embarrassed - that's a surprisingly common problem and an easy check once you think of it.
The Thread Tools pull-down at the top of the page lets you mark the thread as solved.

---

### Post by TheFu on 2021-03-20
> **The Cog said:**
> Glad you got it sorted. Don't be embarrassed - that's a surprisingly common problem and an easy check once you think of it.
The Thread Tools pull-down at the top of the page lets you mark the thread as solved.

+1 - exactly. You aren't the first person to think a service is running on an IP address.  This is part of the reason why I setup static IPs and DNS entries for all my new servers (physical and virtual) as part of the installation/setup.  Though I must admit, I setup ssh access FIRST ... so I can use a devops tool to change the IP to the static ones I've assigned on the different networks connected. Part of the devops tooling it ensuring the settings are correctly placed into all the impacted systems.  Consistency matters.

[https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) might be helpful.

---

