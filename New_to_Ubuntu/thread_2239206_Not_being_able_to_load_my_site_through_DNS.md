---
title: "Not being able to load my site through DNS"
date: 2014-08-12
forum: New to Ubuntu
---

### Post by aliy2 on 2014-08-12
Hello, recently i switched Operating Systems from Windows 8 to Ubuntu. Everything is running perfectly except that I cannot load my own website (aliscode.com) via the firefox web browser I can only load it if i type in the IP address. While on my Nexus 5 (which is also running firefox) I can load the website through the domain. 
My current addons are Adblock Edge, Clean Links, DoNotTrackMe: Online Privacy, Ubuntu Firefox modifications, Youtube High Definition.

Thank you in advance
- Ali Y.
P.S i apologize if I have posted this thread in the wrong section

---

### Post by nerdtron on 2014-08-12
Let's troubleshoot. What is the output of the following commands:

```
ping aliscode.com
```

```
nslookup aliscode.com
```

```
dig aliscode.com
```

```
cat /etc/hosts
```

---

### Post by aliy2 on 2014-08-12
Here is the output of the commands 

--- aliscode.com ping statistics ---
75 packets transmitted, 75 received, 0% packet loss, time 73996ms
rtt min/avg/max/mdev = 0.012/0.026/0.048/0.009 ms
-----
Server:        127.0.1.1
Address:    127.0.1.1#53

Non-authoritative answer:
Name:    aliscode.com
Address: 216.224.177.125

-------

127.0.0.1    localhost
127.0.1.1    aliscode.com    aliscode

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

-----
; <<>> DiG 9.9.5-3-Ubuntu <<>> aliscode.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 41832
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;aliscode.com.            IN    A

;; ANSWER SECTION:
aliscode.com.        207    IN    A    216.224.177.125

;; AUTHORITY SECTION:
aliscode.com.        207    IN    NS    ns1.myhosting.com.
aliscode.com.        207    IN    NS    ns2.myhosting.com.
aliscode.com.        207    IN    NS    ns.myhosting.com.

;; Query time: 2 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Tue Aug 12 21:42:47 EEST 2014
;; MSG SIZE  rcvd: 120

---

### Post by nerdtron on 2014-08-12
```
127.0.0.1    localhost
[COLOR=#ff0000][B]127.0.1.1    aliscode.com    aliscode
[/B][/COLOR]
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

Unless your computer is the aliscode.com website itself, I see this is as a problem. Is the website installed on your computer? If not, you should change this line.

---

### Post by aliy2 on 2014-08-12
The website is hosted on another host how do i change that specific line? Do i just have to open up the /etc/hosts and change it there?

---

### Post by nerdtron on 2014-08-12
Edit the /etc/hosts file:
```
sudo nano /etc/hosts
```

Enter your password and navigate to the line in question.
Add a # on the beginning of the line to comment it out.
```
127.0.0.1    localhost
[COLOR=#ff0000][B]#127.0.1.1    aliscode.com    aliscode
[/B][/COLOR]
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

Press Ctrl+O to save and Ctrl+X to exit.
Now re-open your browser and let's see if you can browse the site.

---

