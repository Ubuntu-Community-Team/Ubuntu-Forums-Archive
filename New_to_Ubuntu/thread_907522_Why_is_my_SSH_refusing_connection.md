---
title: "Why is my SSH refusing connection?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by alecwh on 2008-09-01
I installed OpenSSH a few days ago on my laptop. For some reason, when I attempt to SSH into it (from my Desktop, other laptop), I get a refused connection. Example:

```
alecwh@alecwh-laptop:~$ ssh alecwh@192.168.0.9
ssh: connect to host 192.168.0.9 port 22: Connection refused

```

Can someone tell me what's up? I don't know what to do from here (SSH is alien to me).

---

### Post by jamesrfla on 2008-09-01
Are you trying to access SSH outside your network? If you are you need to go into your router and port forward port 22. Also make sure your firewall isn't blocking it.

---

### Post by alecwh on 2008-09-01
No, it's all in this network. No firewalls that I'm aware of (fresh Ubuntu Hardy).

---

### Post by WRDN on 2008-09-01
[QUOTE=alecwh]No, it's all in this network. No firewalls that I'm aware of (fresh Ubuntu Hardy).[/QUOTE]

There is a firewall installed already, called "iptables".
You need to open port 22 in the Firewall. You can edit the firewall rules using UFW (Uncomplicated Firewall) which is already installed or Firestarter, if you want to use a GUI. In Firestarter, add a service for SSH on port 22, and allow the service for everyone or only your network. Now, apply the policy, and you should now be able to connect to SSH. Note that, you may need to restart SSH to get it to work:

```
sudo /etc/init.d/ssh restart
```

I would recommend you change the port for SSH, by typing:

```
gksudo gedit /etc/ssh/sshd_config
```

Now, change the line "Port 22" to something else. I personally use port 1025.

When you connect to SSH now, you need to add "-p [port]" to the end. For example, when I connect, I type:

```
ssh -X [IP_Address] -p 1025
```

You can leave "-X" out if you want. I use it so I can forward X11. In order for this to work, you must set "X11Forwarding" to yes in the sshd_config file.

---

### Post by Badoxide on 2008-09-01
Hello.All

@ WRDN

Sorry for stepping on this Thread, but had to ask I don't see anyone using a password here. ? or is it something that can be changed after login. I ask because on my iPhone I did just that as said above. Not saying your wrong in anyway just making sure before I go ahead, and do this for myself.

Thanks 

B-O

---

### Post by WRDN on 2008-09-01
> **Badoxide said:**
> Hello.All

@ WRDN

Sorry for stepping on this Thread, but had to ask I don't see anyone using a password here. ? or is it something that can be changed after login. I ask because on my iPhone I did just that as said above. Not saying your wrong in anyway just making sure before I go ahead, and do this for myself.

Thanks 

B-O

Sorry, I'm confused. What do you mean by, "I don't see anyone using a password here"? The password prompt appears after you attempt to connect to the SSH Server.

---

### Post by Badoxide on 2008-09-01
Hi.WRDN

Sorry its me, what I was trying to point out here in a bad way is that a user should change any default passwords. If any are used in SSH for ubuntu. Not sure if ubuntu has a default one, or not.

Thank you

B-O

---

### Post by WRDN on 2008-09-01
> **Badoxide said:**
> Hi.WRDN

Sorry its me, what I was trying to point out here in a bad way is that a user should change any default passwords. If any are used in SSH for ubuntu. Not sure if ubuntu has a default one, or not.

Thank you

B-O

The password used for SSH is the same as the user's password, so it's best to have a strong user password. You can then connect to SSH using any username/ password. When connecting, you can type:

```
ssh username@IP_Address
```

This will allow you to specify what user you want to login as.

---

### Post by Badoxide on 2008-09-01
Hey.WRDN

Yes thank you this is what I was trying to get to. The iPhone uses by default, for both root and user alpine so after login I changed both passwords. So I will do the same here for ubuntu.

Thank you

B-O

---

### Post by brian_p on 2008-09-02
> **alecwh said:**
> I installed OpenSSH a few days ago on my laptop.

Did you install openssh-server?

---

### Post by brian_p on 2008-09-02
> **WRDN said:**
> There is a firewall installed already, called "iptables".

Yes. Default rules are:

```
someone@laptop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```


> You need to open port 22 in the Firewall. 

No you don't.

---

### Post by Oldsoldier2003 on 2008-09-02
> **brian_p said:**
> Did you install openssh-server?

+1 

The server is not installed by default:
```
sudo apt-get install openssh-server
```

---

