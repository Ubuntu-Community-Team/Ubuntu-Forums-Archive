---
title: "finding IP address of computer that is ssh'd into server"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by hookitup on 2012-11-06
Hello folks, so i am sshing into a ubuntu server (this server is just for me to mess around in)

is there a command i can run on the server that will show the IP address of the computer that is currently SSHed into the server.?


if you need me to explain a little more let me know.

---

### Post by papibe on 2012-11-06
Hi hookitup.

This could help:
```
who --ips
```
Let us know how it goes.
Regards.

---

### Post by drmrgd on 2012-11-06
I'm partial myself to the 'w' command, that gives a little more information.  Literally just type 'w' in the terminal and you'll get info on who's logged in, their IP address, when they logged in, and what they're doing currently.

---

### Post by hookitup on 2012-11-06
great thanks folks.

---

### Post by Lars Noodén on 2012-11-06
So you have yet another choice, you can also look the output of [last](http://manpages.ubuntu.com/manpages/precise/en/man1/last.1.html).  

```

last -n 5

```

For your own ssh session you can look at the variables $SSH_CLIENT and $SSH_CONNECTION.  Those will give you the port numbers too but will include the ip number.

---

### Post by papibe on 2012-11-06
Just to be a little more precise ;-)

If you have a well setup dhcp/dns server combo, all these commands ('who', 'w' and 'last') will report by default the hostname of the remote host (using reverse lookup).

For instance, they'll show something like:
```
remote_host_name.localnet
```
You can explicitly ask  both 'who' and 'last' to show ip addresses  by using additional options:
```
who [COLOR="Red"]**--ips**[/COLOR]

last -5[COLOR="Red"]**i**[/COLOR]
```

Best Regards.

---

### Post by hookitup on 2012-11-06
Papib

so what your saying is i can possible have it displace the IP address and hostname of the user remoting in?

---

### Post by papibe on 2012-11-06
If you are scripting, you should be careful.

For instance, this are the results on my server (assuming just one user).

With no options:
```
$ who  | awk '{print $NF}'
(vaughan.localnet)

```
However, with options:
```
$ who --ips | awk '{print $NF}'
192.168.1.101
```

---

