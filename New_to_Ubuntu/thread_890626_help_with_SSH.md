---
title: "help with SSH"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by wintersnows on 2008-08-15
hiya, I need to remote access a server from my machine to do some work. I have install the sudo apt-get install ssh and it seems fine. Then, I am trying to remote access a server by typing the command as e.g.:

ssh [email]server@ubuntu.lboro.ac.uk[/email] or ssh server@[ IP address ]

but it doesn't work. I am new to Ubuntu. COUld someone tell me how to conficure it? Thanks you

---

### Post by theyranos on 2008-08-15
What's the message that **ssh** gives you when you run it? Also, is **server** your username at **ubuntu.lboro.ac.uk**?

---

### Post by nothingspecial on 2008-08-15
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by djxcon on 2008-08-15
When you are trying to access the remote machine you will want to use username@ip_address (not literally but fill in the blanks).  If you have everything configured properly, this will bring you to the password prompt for the username that you chose.  Note: the username should be a valid username on the server that you are trying to access.  

Are you able to hit the server directly, or are you using the IP address of the router?  If this server is behind a router, than you will need to configure the router to forward port 22 to the server. To access the server you will use username@routers_ip_address

If this is not working, please post the error message.

---

### Post by croniksoft on 2008-08-15
is your server connected to a router? because if you do you will need to enable port forwarding in your router to route every request that comes on port 22 to the correct Sever.


NOTE:i picked port 22 because is the default port used by ssh,however i do recommend you change that port to something else, that will save you lot of trouble with all these hackers wanna be.

Sorry for my poor writing

---

### Post by wintersnows on 2008-08-15
ssh [email]leo@ubuntu.lboro.ac.uk[/email] it gaves me the error of:

ssh: ubuntu.lboro.ac.uk: Name or service not known

yes, leo is the username at ubuntu.lboro.ac.uk

---

### Post by Too Late on 2008-08-15
Do you know the exact IP address for that server?

---

### Post by ingeva on 2008-08-15
> **wintersnows said:**
> ssh [EMAIL="leo@ubuntu.lboro.ac.uk"]leo@ubuntu.lboro.ac.uk[/EMAIL] it gaves me the error of:

ssh: ubuntu.lboro.ac.uk: Name or service not known

yes, leo is the username at ubuntu.lboro.ac.uk

Many servers don't allow you to use ssh. Have you checked?

---

### Post by Vivaldi Gloria on 2008-08-15
> **wintersnows said:**
> ssh [email]leo@ubuntu.lboro.ac.uk[/email] it gaves me the error of:

ssh: ubuntu.lboro.ac.uk: Name or service not known

yes, leo is the username at ubuntu.lboro.ac.uk

Are you sure that ubuntu.lboro.ac.uk is reachable?

```
vivaldi@narval:~$ whois ubuntu.lboro.ac.uk

No such domain ubuntu.lboro.ac.uk

vivaldi@narval:~$ ssh leo@ubuntu.lboro.ac.uk
ssh: connect to host ubuntu.lboro.ac.uk port 22: No route to host
```

---

### Post by wintersnows on 2008-08-15
I have not configure for my laptop as vi /etc/network/interfaces to state all the address, broadcast, netmask, network, gateway.

The server address is 192.168.11.65. Should I make it to be 192.168.11. something? Besides this, should I make something same related to it?

Yes, the username is valid. I can't hit the server directly. The IP address is all connected to a switch and there is no router.

---

### Post by rampageoberon on 2008-08-15
Just to check what is the following commands output?

```
nmap -A 192.168.11.65
```

Or replace 192.168.11.65 with the server ip if its incorrect.

---

### Post by croniksoft on 2008-08-15
if you dont have a DNS server you will not be able to do that, i dont think linux works the same way as windows wen it comes down to PC names, please someone correct me on this if i am worng,not really sure about it

---

### Post by wintersnows on 2008-08-15
what is nmap use for? I don't think we need DNS server.

**I am new in Ubuntu. I appreciate someone could help me. Thanks!!**

---

### Post by wintersnows on 2008-08-15
I tried with nmap -A 192.168.11.65 but it comes out as:


Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-08-15 14:44 BST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.090 seconds

what does this means?

---

### Post by fahadsadah on 2008-08-15
Replace 192.168.11.65 with the server ip

---

### Post by croniksoft on 2008-08-15
Nmap is a  port scanner that can scan your network or just a single machine and tell you what ports are open and even tell you what applications are runing on those port.

i need you to tell me if you get a reply from the machine when you ping it by hostname (server.com) and wen you ping it by IP (192.1.1.1)

ex:

ping yourservername

ping 192.1.1.1

---

### Post by Vivaldi Gloria on 2008-08-15
Is this your server? 
Is it up?
How do you know that the ip of the server is 192.168.11.65?
Are you trying to reach this server drom the same lan?
What's the result of "ifconfig" in the server?
Is "ssh localhost" possible in the server?

---

### Post by wintersnows on 2008-08-15
[Replace 192.168.11.65 with the server ip]

what is the command for this?

**I am new in Ubuntu. I appreciate someone could help me. Thanks!!**

---

### Post by brian_p on 2008-08-15
> **wintersnows said:**
> hiya, I need to remote access a server from my machine to do some work. I have install the sudo apt-get install ssh and it seems fine. Then, I am trying to remote access a server by typing the command as e.g.:

ssh [email]server@ubuntu.lboro.ac.uk[/email] or ssh server@[ IP address ]

but it doesn't work. I am new to Ubuntu. COUld someone tell me how to conficure it? Thanks you

lboro.ac.uk is Loughborough University in the UK. ubuntu is a host on their network. The university controls access to it (if it exists and is up and running). What makes you think you have access to it with ssh?

---

### Post by croniksoft on 2008-08-15
ok, go physically up to the server and type in the command line "ifconfig" and paste the results here.

---

### Post by wintersnows on 2008-08-15
> **croniksoft said:**
> Nmap is a  port scanner that can scan your network or just a single machine and tell you what ports are open and even tell you what applications are runing on those port.

i need you to tell me if you get a reply from the machine when you ping it by hostname (server.com) and wen you ping it by IP (192.1.1.1)

ex:

ping yourservername

ping 192.1.1.1

I can ping myservername but when I comes to ping 192.1.1.1 
PING 192.1.1.1 (192.1.1.1) 56(84) bytes of data.
It don't response at all. 

**I am new in Ubuntu. I appreciate someone could help me. Thanks!!**

---

### Post by wintersnows on 2008-08-15
> **Vivaldi Gloria said:**
> Is this your server? 
Is it up?
How do you know that the ip of the server is 192.168.11.65?
Are you trying to reach this server drom the same lan?
What's the result of "ifconfig" in the server?
Is "ssh localhost" possible in the server?

I know the server IP address by typed vi /etc/network/interfaces into the server. I tried ssh localhost on my machine and server machine, both is fine.

---

### Post by wintersnows on 2008-08-15
I actually wanted to remote access the server far from uni. Anyone has the ideas for it?
 Thank you

---

### Post by brian_p on 2008-08-15
> **wintersnows said:**
> I actually wanted to remote access the server far from uni. Anyone has the ideas for it?


It is difficult to have ideas when you do not respond to all the questions posed but here is my guess. There is a machine in a student residence at Loughborough University. It has been named ubuntu. You think it can be accessed with the the domain name ubuntu.lboro.ac.uk. It can't - you do not control the network it is on.

---

### Post by DGortze380 on 2008-08-15
You're not reaching the server. So you either have the wrong IP, or the server is not up and running, or something is getting in the way.

You could try the traceroute command (**DISCLAIMER** Legality of using this command in your country is unknown **END**) to find out how you're accessing the server. If there is a firewall or switch between you that is configured to stop access on port 22 (or just not configured to forward to the correct machine on port 22) you will not be able to access the server.

---

### Post by CautionaryX on 2008-08-16
> **nothingspecial said:**
> [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Make sure you set it up correctly. 

If you're a student and/or work at that university, you might want to talk to the IT department.

EDIT: 192.168.*.* is reserved for **Intra**net connections. Accessing this IP address outside of the university will most likely fail.

---

### Post by howlingmadhowie on 2008-08-16
if you really want to get this to work, you should have a look at reverse ssh tunneling.

---

### Post by ingeva on 2008-08-16
> **howlingmadhowie said:**
> if you really want to get this to work, you should have a look at reverse ssh tunneling.

The server at loughboro (lboro.ac.uk) is quite OK.

The subdomain ubuntu is not available from the Net. Maybe it is from the inside of the uni network.

As I have said before, ssh is normally disabled at any webserver because they consider it a security risk.

You need to talk to the IT people at loughboro to resolve this. If they'll let you.

---

