---
title: "SSH Tunneling with Remote Server Port Forwarding"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by sysopl on 2008-05-26
Hello.

I have a server running ubuntu h.heron beta desktop edition.
My ISP blocks everything except standard stuff, ftp, ssh, telnet etc. I can't change ISP, there is only 1 here.
I want to set up a proxy tunneling service on it so I can bypass their firewall and be free to do anything.

I want to be able to use a proxy on my end which connects to the server and then the server forwards me the packets etc. Just like a proxy... I need SSL/encryption on it. Privacy is important here.

However, I also want it to be able to forward specific ports. So I appear to be 'connectible' on the internet from my end. this is so I can put in a socks proxy on my end, and have my apps work (if they need a specific port to be open)

I really have no idea how I could go about this, anyone have any idea or websites that could help?

Thank you!

---

### Post by quelx on 2008-05-26
Do you have a machine on the other end you will be connecting to which does not have these restrictions?

If so ```
ssh -L 8080:someinternetaddress:8080 remotehost
``` would do the trick.  Adjust for whatever service you are trying to connect to.  Point you local client to localhost:8080.  Adding the forward to the **~/.ssh/config** would make the forward active anytime you connected to that particular host.  Check out ```
man ssh
``` for all the nitty gritty.

You could check out openVPN

---

### Post by sysopl on 2008-05-26
Thanks for your post.

I don't understand exactly what you mean by

"Adjust for whatever service you are trying to connect to"

Also, I want all my types of traffic to go through the proxy, bittorrent, DC, IRC etc, not just web browsing...

Could you use the example of wanting HTTP and Bittorrent. 
As that will be my primary use. 

I will need the Bittorrent port of 25001 (the port i specify in my BT client) to be open, so peers can connect to me.

Hope you can help!

---

### Post by quelx on 2008-05-26
I think ```
ssh -L *:25001:localhost:25001 remotehost
``` would do the trick for the torrent, just add more **-L** options for each tunnel you wish to create, or edit the **config** file I mentioned.

---

### Post by sysopl on 2008-05-26
Ok. How do I do that command? on the client or server? sorry, im a noob to ubuntu.

I will try what you said and report back. Appreciate it!



hmm, I read somewhere that

ssh -2 -R 7654:localhost:7654 -A -D 1080 [email]root@theserver.org[/email]

would work, but this commands is for freebsd...

---

### Post by quelx on 2008-05-26
> **sysopl said:**
> Ok. How do I do that command? on the client or server? sorry, im a noob to ubuntu.

I will try what you said and report back. Appreciate it!



hmm, I read somewhere that

ssh -2 -R 7654:localhost:7654 -A -D 1080 [email]root@theserver.org[/email]

would work, but this commands is for freebsd...

The BSD command should work, (I think the linux ssh is a port from BSD land anyway) you can drop the -2 (ssh of late will only use v2)

That is a reverse forward, a backward if you will, so traffic coming to port 7654 on the remote machine will be redirected to port 7654 on your local machine.  I think you need a *****

```
ssh -R *:7654:localhost:7654 -A -D 1080
```

You should check out the man page for ssh it's quite enlightening and explains all the fun (if I can say that) ssh can bring to your life.

[http://www.openbsd.org/cgi-bin/man.cgi?query=ssh](http://www.openbsd.org/cgi-bin/man.cgi?query=ssh)

---

### Post by sysopl on 2008-05-26
Neither command worked.

I ran it on my mac in terminal, and it just says something like "SSH syntax is -R etc etc" and gives a list of commands

Is there no GUI that can configure this? Would be much easier...

---

### Post by quelx on 2008-05-26
OS X (BSD for that matter) is particular about the order of commands and I forgot to add the destination in my code...

```
ssh -R *:7654:localhost:7654 -A -D 1080 -l username servername
```

putty is a good ssh front end and it's in the repos

```
sudo apt-get install putty
``` though I don't know if it handles -D -A options...

---

### Post by sysopl on 2008-05-27
double post.

---

### Post by sysopl on 2008-05-29
I found a software for OS X that got me the right command:

ssh -N -p 22 -c 3des -D 1080 admin@server -R 31313/localhost/31313

This works, HOWEVER the remote port forwarding of 31313 does NOT work...

I want my server to listen on port 31313 for connections, and then forward them to my computer.
Anyone know how to do this???

My ISP blocks all incoming connections including 31313, and I know there is a way to use SSH tunneling to get around that!

---

