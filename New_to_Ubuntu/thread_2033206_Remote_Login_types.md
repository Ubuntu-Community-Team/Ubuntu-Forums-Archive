---
title: "Remote Login types"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by sushy on 2012-07-25
I was just wondering what are the different types of remote login.
I know of ssh and telnet. Basically I wish to disable remote login to a server and I have found ways of blocking ssh and telnet. But I am not sure if there are other ways to log in.

---

### Post by cariboo on 2012-07-25
> **sushy said:**
> I was just wondering what are the different types of remote login.
I know of ssh and telnet. Basically I wish to disable remote login to a server and I have found ways of blocking ssh and telnet. But I am not sure if there are other ways to log in.

It really depends on what services you have running on the server. A default Ubuntu server install, is only the operating system, and nothing else. The install process allows you to choose what services to install.

An easy way to see what services are running and open on your server,is to install nmap on another system running a linux distribution, then at the prompt type:

```
nmap <server_ip_address>
```

running nmap on one of servers results in the following output:

```
nmap likely

Starting Nmap 6.00 ( http://nmap.org ) at 2012-07-25 15:16 PDT
Nmap scan report for likely (192.168.1.240)
Host is up (0.00081s latency).
Not shown: 998 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
8200/tcp open  trivnet1

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
```

This particular server runs headless without a gui, and as you can see the only two services runiing and open are:

[LIST]
[*]ssh
[*]minidlna
[/LIST]

In my case I administer the server via ssh, which uses private keys with no password, and minidlna serves streaming media to various devices and computers in my household.

---

### Post by sushy on 2012-07-25
Thanks for the reply. The nmap output in my case is 

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2012-07-25 15:30 PDT
Interesting ports on beantown.aaaaaa.com (10.10.12.12):
Not shown: 990 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
80/tcp   open  http
111/tcp  open  rpcbind
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
389/tcp  open  ldap
445/tcp  open  microsoft-ds
1024/tcp open  kdm
6000/tcp open  X11

Nmap done: 1 IP address (1 host up) scanned in 0.09 seconds

It would be really difficult to block out on all these services. Infact in case I have a new service installed and I forget to block it I am leaving a security hole. Is there a way that can make me block a particular server to remote access to a particular group of users?

---

### Post by yuvraj23 on 2012-07-25
You know anyone can hack your computer if he gets an exploit for the services that are currently in 'listening' state..  rule of thumb is to disable all stray services. You will be safe



Note: Firewall doesn't works in this case

---

### Post by cosmoshell on 2012-07-25
deleted

---

### Post by sushy on 2012-07-26
Is there a way that can make me block a particular server to remote access to a particular group of users?

---

### Post by Lars Noodén on 2012-07-26
> **sushy said:**
> Is there a way that can make me block a particular server to remote access to a particular group of users?

If you're talking about SSH at least, then the answer is yes.  You can allow access with the [font=Courier New]AllowGroups[/font] directive.  You set it in /etc/ssh/[sshd_config](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html).  Be sure not to lock yourself out when changing sshd_config.

---

### Post by sushy on 2012-07-26
Thanks for the reply but I was looking for a solution that would make that user unable to access this server(ie not even telnet/ftp,etc). In short completely shutdown from the server.

---

### Post by Lars Noodén on 2012-07-26
Locking users out like that would have to be configured on a service by service basis.  TCP does not carry user information.  

For SSH, it is simple, any user not in one of the allowed groups is blocked from access.

For FTP, unless you are using virtual users, you can remove it completely and use instead SFTP which is built into the SSH server.  Which FTP server are you using?  VSFTP?

For HTTP/HTTPS, that is open to any and all unless you put your pages behind some kind of [authentication](https://httpd.apache.org/docs/2.2/howto/auth.html).  But unless you go to great lengths it will not be the same as the system users and groups.

It's easier to block IP numbers if you want that.  It is done using  UFW or directly using IPtables.

---

### Post by sushy on 2012-07-26
I really appreciate your quick response. I will work on blocking out services. But everytime I add a new service (for eg ssh I know this is a lame example :)) does that mean I need to go and block out that service to that set of users?

---

### Post by Lars Noodén on 2012-07-26
> **sushy said:**
> I really appreciate your quick response. I will work on blocking out services. But everytime I add a new service (for eg ssh I know this is a lame example :)) does that mean I need to go and block out that service to that set of users?

Yes, blocking users needs to be done on a service by service basis.  If you take a look at [font=Courier New]AllowGroups[/font] and [font=Courier New]DenyGroups[/font] for SSH, you'll see two methods of controlling access.  Some services will have more options, others less.

---

### Post by sushy on 2012-07-26
Thank you so much. Will definitely try this.

---

