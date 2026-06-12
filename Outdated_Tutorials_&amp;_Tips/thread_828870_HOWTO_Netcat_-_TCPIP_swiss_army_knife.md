---
title: "HOWTO: Netcat - TCP/IP swiss army knife"
date: 2008-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by uljanow on 2008-06-14
This article describes some netcat applications and demonstrates how to use netcat which is one of the most useful network tools.

**_0. HTTP Server_**
This is a simple HTTP server which listens on port 8080. The -l option puts netcat into listen mode and -c specifies the command to execute after a connection is established. The server respond can be viewed with a browser at [http://localhost:8080](http://localhost:8080).
```
#!/bin/bash

handle_req()
{
        read req file proto
        echo -e "HTTP/1.1 200 OK\r\nContent-Type: text/html\r\n\r\n"
        echo -e "<html><h1>Hello World</h1></html>"
}

typeset -fx handle_req

nc -l -p 8080 -c handle_req
```

**_1. HTTP Client_**
This example will fetch the latest kernel version from kernel.org (similar to finger(1) ). Note that netcat prints also the HTTP header.
```
echo -e "GET /kdist/finger_banner HTTP/1.0\r\n" | \
nc www.kernel.org 80 | grep latest
```

**_2. Remote Terminal_**
This example shows how to connect to a remote shell without using telnet or ssh. The terminal server which runs on <host>:
```
nc -l -p 4000 -e /bin/sh
``` and the client :
```
nc <host> 4000
```

**_3. Port Scanning_**
netcat can also be used for port scanning (with zero-I/O option). 
```
nc -v -z www.kernel.org 80 21
# or with port ranges
nc -v -z www.kernel.org 21-23

```

**_4. File Transfer_**
Sending a file "foobar" on port 4000 can be achieved like this:
```
cat foobar | nc -l -p 4000
``` The client would receive the file from <host> with this command:
```
nc <host> 4000 > foobar
```

**_5. Torifying Netcat_**
The tor package includes **torify**, a wrapper for tsocks and tor, which can be used to anonymize network traffic :
```
echo -e "GET /iponly/ HTTP/1.0\r\n" | torify nc ipid.shat.net 80
``` This should print the IP address of the Tor exit-node that is used.

**_6. Chat_**
A simple one-to-one chat server can be started like this:
```
nc -lp 8080
```
Afterwards a client can connect to the server:
```
nc <host> 8080
```

---

### Post by Panos on 2008-09-19
Hello

I need some help to achieve this:

I need to start an application in my headless server (hardy 64bit) which will always wait for some input.
I need to send the input from my desktop pc to the server and, after it is processed by the application on the server, have the output on the desktop pc.

I tried with faucet/hoses and netcat but to no avail. netcat gives me errors about refused connection.

Any help will be greatly appreciated.

Thanks

Panos

---

### Post by falstaff on 2008-11-16
Hello,

Ive a problem to follow your netcat howto on intrepid ibex. As soon as i use echo "something" | netcat, netcat gives absolutly NO output! Any idea? Is this a bug?

Example:
echo -e "GET /kdist/finger_banner HTTP/1.0\r\n" | \
nc [www.kernel.org](www.kernel.org) 80

Doesnt work for me, but
nc [www.kernel.org](www.kernel.org) 80  and type GET /kdist/finger_banner HTTP/1.0 and press enter works!

Bye
falstaff

---

### Post by falstaff on 2008-11-16
Hm, this seem to be 64-Bit bug in intrepid ibex, can somebody verfy this with 32-Bit and someone with 64-Bit Ibex installation?

---

### Post by DagMan on 2008-12-02
It works fine in 32 bit Intrepid.

```
 $ echo -e "GET /kdist/finger_banner HTTP/1.0\r\n" | nc www.kernel.org 80

HTTP/1.1 200 OK
Date: Tue, 02 Dec 2008 09:22:58 GMT
Server: Apache/2.2.9 (Fedora)
Last-Modified: Tue, 02 Dec 2008 08:16:29 GMT
ETag: "4927cfcc-1a4-45d0bf1c3b140"
Accept-Ranges: bytes
Content-Length: 420
Connection: close
Content-Type: text/plain; charset=UTF-8

The latest stable version of the Linux kernel is:           2.6.27.7
The latest prepatch for the stable Linux kernel tree is:    2.6.28-rc7
The latest 2.4 version of the Linux kernel is:              2.4.37
The latest 2.2 version of the Linux kernel is:              2.2.26
The latest prepatch for the 2.2 Linux kernel tree is:       2.2.27-rc2
The latest -mm patch to the stable Linux kernels is:        2.6.28-rc2-mm1
```

---

### Post by nemoinis on 2009-03-23
I had the same problems with Intrepid, but on the 32-bit version.
I think it's a Ubuntu Hardy->Intrepid upgrade bug.
I found had 2 netcat packages on my machine:
netcat-openbsd 1.89-3ubuntu1  (which provides netcat)
netcat 1.10-38 (which also provides netcat)

/bin/netcat -h showed that this was the openbsd version, and it did not work right (the symptoms posted above, and others)

removing netcat-openbsd fixed it for me.
/bin/netcat -h now shows version 1.10-38 and the program behaves normally.

---

### Post by kkady32 on 2009-03-30
in 8.10 64 bit  work fine too

---

### Post by patrick38894 on 2010-09-17
when i try to use the -e /bin/bash extension it says 

nc: getaddrinfo: nodename nor servname provided, or not known

suggestions?

---

### Post by metodk on 2010-09-29
Howdy!

I've also run into issue of empty output with netcat-openbsd on Lucid Lynx 32-bit. nc was called from bash script. If script was run manually (from valid login environment), output was OK. If script ran as cron job, output was empty.

Installing netcat (the non-openbsd variant) did the trick.

---

### Post by LocoDelAs_embly on 2011-01-27
Hi, 
Sorry if this is not the best place to post this but it looked a nice place since it involves one of the items in the how to. 

I'm using Ubuntu 10.04 Server and on older versions, doing something like this: echo -e "GET /kdist/finger_banner HTTP/1.0\r\n" | nc [www.kernel.org](www.kernel.org) 80 

Showed the page contents in the console but now nothing happens. However, nc.traditional works (after installing it of course) 

This is my current state:
loco@ubuntu:~$ lsb_release -d
Description:	Ubuntu 10.04.1 LTS
loco@ubuntu:~$ echo -e "HEAD / HTTP/1.0\r\n" | nc [www.kernel.org](www.kernel.org) 80
loco@ubuntu:~$ echo -e "HEAD / HTTP/1.0\r\n" | nc.openbsd [www.kernel.org](www.kernel.org) 80
loco@ubuntu:~$ echo -e "HEAD / HTTP/1.0\r\n" | nc.traditional [www.kernel.org](www.kernel.org) 80
HTTP/1.1 200 OK
Date: Thu, 27 Jan 2011 20:43:26 GMT
Server: Apache/2.2.17 (Fedora)
Accept-Ranges: bytes
Connection: close
Content-Type: text/html; charset=UTF-8

Does the openbsd version has some way to provide the same output nc.traditional does? Please note that the man pages still say that doing the echo stuff you'll be able to see the output in stdout and even suggest ways to remove the HTTP headers, but there is no mention that you should use the traditional version (or I missed that part?)

For now I'll simple use nc.traditional, but I just wanted to let you now about this so maybe something can be done.

Thanks

---

### Post by LocoDelAs_embly on 2011-01-31
A friend of mine directed me to the answer: [https://bugs.launchpad.net/ubuntu/+source/netcat-openbsd/+bug/544935](https://bugs.launchpad.net/ubuntu/+source/netcat-openbsd/+bug/544935)

This works for me:
loco@ubuntu:~$ lsb_release -d
Description:    Ubuntu 10.04.1 LTS
loco@ubuntu:~$ echo -e "HEAD / HTTP/1.0\r\n" | nc [www.kernel.org]("http://www.kernel.org") 80 -q -1
HTTP/1.1 200 OK
Date: Mon, 31 Jan 2011 07:53:54 GMT
Server: Apache/2.2.17 (Fedora)
Accept-Ranges: bytes
Content-Type: text/html; charset=UTF-8
Connection: close

---

