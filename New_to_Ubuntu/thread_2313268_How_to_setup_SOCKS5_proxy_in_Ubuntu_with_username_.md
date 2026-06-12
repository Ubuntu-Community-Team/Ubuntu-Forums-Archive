---
title: "How to setup SOCKS5 proxy in Ubuntu with username and password? Please Help"
date: 2016-02-11
forum: New to Ubuntu
---

### Post by raman07 on 2016-02-11
Hi, I just started to use ubuntu a few days ago and I need to setup SOCKS5 proxy in my Ubuntu VPS. I found few article on google and one of the article work for me but that is not what i want.

Here is what i tried.
I use this command &#8220;ssh -N -D 0.0.0.0:1080 localhost&#8221; and then iptables.
iptables -A INPUT &#8211;src 1.2.3.4 -p tcp &#8211;dport 1080 -j ACCEPT
iptables -A INPUT -p tcp &#8211;dport 1080 -j REJECT


To allow socks proxy connection only to my ip address but problem is i have dyanmic ip address and i lost access to my socks proxy server when my ip changes. So is there any better way to install socks proxy server in ubuntu?

I also tried dante-server but i failed to configure it to make it work.
What i did in dante conf file is:


I uncommented following lines. I did not change anything else :


internal: eth0 port = 1080
external: eth0




method: username                              # DO i need to write something else on place of username?
user.notprivileged: nobody




client pass {                                                  # where to write pass and which pass?
from: 0.0.0.0/0 port 1-65535 to: 0.0.0.0/0
}




pass {
from: 0.0.0.0/0 to: 0.0.0.0/0
protocol: tcp udp
}



But it did not work.


--------------------------------------------------------------------------------------------------------------------------------------------

Okay here is what i want to acchive. I want to access my all ips address of my ubuntu vps as socks5 proxy from my firefox with username and password enabled on them so no one else can use my ip address without my permission.
Please tell me what is best way to do this? I need to handle my YouTube accounts and i do not want to know youtube that all the socks5 connection coming from same ubuntu vps. So is it possible to handle multiple socks5 proxy from single vps without reveal a website that all the request coming from same source/vps?

Please help me i need it urgently

---

### Post by sandyd on 2016-02-11
What OS are you trying to connect to the SOCKS proxy from?

It may be more handy to use SSH as a SOCKS proxy.

For Windows, you can use putty, for Linux/Mac, you can use the command (replace *username* and *server*)
```

ssh -D 8080 *username*@*server*
```

SOCKS proxy will be created at 127.0.0.1:8080

Make sure that in /etc/ssh/sshd_config on the server, AllowTcpForwarding is enabled, as like below.
```

AllowTcpForwarding yes
```

Restart the ssh server if you needed to update that value.

---

### Post by raman07 on 2016-02-11
> **sandyd said:**
> What OS are you trying to connect to the SOCKS proxy from?
Does it matter which OS i use if i want to use SOCKS5 proxy only in FireFox? I use window OS.

> It may be more handy to use SSH as a SOCKS proxy.
What i know is SSH and SOCKS are same thing. Is not it? I might need SSH enabled Ubuntu VPS before approaching to SOCKS, right?

> For Windows, you can use putty, for Linux/Mac, you can use the command (replace *username* and *server*)
```

ssh -D 8080 *username*@*server*
```
Would not it will open my SOCKS5 proxy to the whole world to use? People will scan my proxy and will start using to spam site. So i might need more configuration to secure my SOCKS5 proxy from people. That's why i want to enable access to my SOCKS proxy only via username and pass.

---

### Post by sandyd on 2016-02-11
The OS matters mainly because you will need a ssh client to create the socks proxy - on windows, there is no ssh by default.

You can use SSH port forwarding to simulate a SOCKS proxy. What the command does is that the SSH client opens an internal port on your computer (In this case, port 8080), and sends all traffic that is sent to that port through the SSH tunnel between the SSH client and server, and then to the SSH server that you are connected to.

You will need the Ubuntu VPS, as that will be the SSH server.

As the internal port will only be created on your system, and is tunneled through SSH, no one other than the computer that the SSH client is running on can access it. It will only be avaliable for people who can SSH to your server. To make it more secure, you can setup SSH keys, which will allow you to login using a "key" instead of a username/password which is more secure as passwords can be guessed.

---

### Post by raman07 on 2016-02-11
Yes I have Ubuntu VPS and i am trying to install socks5 proxy in it. In my first post i already mentioned it. Then i will access this socks proxy from my window OS Firefox.

I want to enable all my IPs to act like socks proxy in ubuntu vps with username and pass enabled. So no one else can use them without me.

Are you trying to say me that i need to install Putty in my window os so i can access my socks proxy in my win os in firefox browser?

This single command " ssh -N -D 0.0.0.0:1080 localhost" turn my ubuntu vps into socks5 proxy but it also make my ubuntu vps ip to allow without any pass and anyone in the world will be able to use my ip address. How i can enable user & pass on this?

---

### Post by sandyd on 2016-02-12
You do not need any special configuration on the Ubuntu VPS except for making sure AllowTcpForwarding is enabled - instructions for enabling are on post #2. 

That being said, you do not run the SSH command posted above on the Ubuntu VPS, the command is for a Linux/Mac system which requires a SOCKS proxy. The command will create a SOCKS proxy using the SSH client on the system. Windows does not have a SSH client, so instead of running the command, we can use putty.

This setup is secure because you do not create a open SOCKS proxy on the VPS; you create it on your computer with a SSH client. The client tunnels your traffic to the VPS, which allows you to use the VPS IP address.

Instructions for using Putty to setup a SOCKS proxy which will tunnel traffic to your VPS is available at [https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-tunneling-on-a-vps#example-3-socks-proxy](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-tunneling-on-a-vps#example-3-socks-proxy)

---

