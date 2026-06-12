---
title: "SSH TCP Forwarding"
date: 2013-12-04
forum: New to Ubuntu
---

### Post by wolfenstein538 on 2013-12-04
Hello,

I have two questions:


1. I'm still struggling with ssh. Keep receiving "ssh: connect to host host port 22: Connection refused when I use a different portnumber, but when I changed it back to the default, it  solved the connection refused issue on one machine, but not with the other. 

2. I'm using SSH TCP forwarding to bypass my router, just as an experiment. I enter ssh -L 8080:[www.google.com:80]("http://www.google.com:80") (username) in a terminal, prompted for a password and then I receive "Permission denied, please try again."

(The ports are open, because I was able to connect through ssh [EMAIL="user@IP"]user@IP[/EMAIL] Address)

It looks like an permission issue, but where? On my username which I use to connect? Or somewhere else?

Thanks in advance

---

### Post by The Cog on 2013-12-04
You will have to explain what you are trying to do. I have no idea what is trying to connect to what. If you are trying to connect ssh through a NAT router, you will need to configure the router to forward port 22 incoming from the internet to the address of the SSH server.

for 2: please post the whole command and the response.

---

### Post by jimmyh1972 on 2013-12-05
The Cog is right - usually when you use ssh port 22 is default 
in addition to that you should port forward your router to port 22.
ssh is for remote access to servers & clients and not suppose to work from port 80 (or 8080)
is you want to change port no. try 2222

---

### Post by kulen19 on 2013-12-10
As pointed as above, it's a little confusing to interpret what you're saying and trying to do. Here is some thing which can point you in the right direction though:

1) SSH default port is 22, and you shouldn't change that unless you are required to for some reason.
2) Portforwarding(i.e. port 22) will make it possible for devices outside of your LAN to connect to the service listening on that port.
3) [Portforward.com]("http://portforward.com/english/routers/port_forwarding/routerindex.htm") can be of great help if you're not sure how to open ports for a specific router. These are walkthroughs. Have a look.
4) If you are unsure what port SSH is running on, you can install nmap and do a "sudo nmap localhost -p-" (change localhost for the internal ip adress to the correspending ip adress for the computer you want to check) and you will get information on all running services on this specific computer computer. You can then determine what port the SSH-server is currently listening to.
6) "Permission denied, please try again." is probably a authentication-problem, as you pointed out. "Connection refused" probably means, in this context, that there isn't a SSH-server(or that it doesn't listen on that specific port). As mentioned above, try a nmap scan do determine what port it *is* listening on.

Feel free to expand/clarify your question, so we can help you more. Best of luck

---

### Post by wlraider70 on 2013-12-10
I disagree with point 1. Changing ports provides a bit of security through obscurity.

---

### Post by kulen19 on 2013-12-11
> **wlraider70 said:**
> I disagree with point 1. Changing ports provides a bit of security through obscurity.

Yeah, that's a good point. Security through obscurity is controversial though, as I'm sure you're aware of. Especially if you're using it as the only security measure(which is not the case here).

---

