---
title: "ASP not working on 8.04..."
date: 2008-05-21
forum: Programming Talk
---

### Post by Ch0p5t1ckB01 on 2008-05-21
Hey all!!

I know this is a common question being asked in this forum, but after reading many of the posts, I have yet to find an answer to my problem.

I've installed Mono with:
sudo apt-get install mono mono-gmcs mono-gac mono-utils monodevelop monodoc-browser monodevelop-nunit monodevelop-versioncontrol

Installed XSP Webserver with:
sudo apt-get install mono-xsp2 mono-xsp2-base asp.net2-examples

When I type "xsp2" I get the following output:

Listening on port: 8080 (non-secure)
Listening on address: 0.0.0.0
Root directory: /home/johnchen1986
Hit Return to stop the server.

Based on that I know that the webserver is up and running. My problem is that when I direct my web browser to //localhost:8080/

I get this error msg:
HTTP 404. System.Web.HttpException: Path '/' was not found.

I've tried the following command to see if it would fix the problem:
sudo cp /usr/share/asp.net2-demos/index.aspx /usr/share/asp.net2-demos/index2.aspx

But it doesn't seem to work. Any advice is much appreciated!!

---

### Post by LaRoza on 2008-05-21
> **Ch0p5t1ckB01 said:**
> 
Based on that I know that the webserver is up and running. My problem is that when I direct my web browser to //localhost:8080/

I get this error msg:
HTTP 404. System.Web.HttpException: Path '/' was not found.

I've tried the following command to see if it would fix the problem:
sudo cp /usr/share/asp.net2-demos/index.aspx /usr/share/asp.net2-demos/index2.aspx

But it doesn't seem to work. Any advice is much appreciated!!


What does this get you?

```

ping -c 1 127.0.0.1

```

Try that IP address in the browser also.

---

### Post by Ch0p5t1ckB01 on 2008-05-21
When I ping 127.0.0.1, I get the following msg:

PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.034 ms

--- 127.0.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.034/0.034/0.034/0.000 ms

And when I input that address into the browser, it fails to load the page.

---

### Post by LaRoza on 2008-05-21
> **Ch0p5t1ckB01 said:**
> When I ping 127.0.0.1, I get the following msg:

PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.034 ms

--- 127.0.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.034/0.034/0.034/0.000 ms

And when I input that address into the browser, it fails to load the page.

Try: ```
127.0.0.1:8080
```

I really haven't used that server, so I don't know much about it. Hopefully, someone here will.

---

### Post by sakabato on 2008-05-22
You must put a Default.aspx page in your root directory which is the exact path you run xsp2. In this case your /home/Jxxx directory

---

### Post by xlinuks on 2008-05-22
Why not using "rock solid and tested servers" like Apache (or Tomcat for that matter)?
Sorry I'm just curious..

---

### Post by sakabato on 2008-05-23
> **xlinuks said:**
> Why not using "rock solid and tested servers" like Apache (or Tomcat for that matter)?
Sorry I'm just curious..

Tomcat is a java servlet container. So normally you can't run ASP.NET (there are exceptions to that like MainSoft but that's another story)


You can use Apache for asp.net via mod_mono. But that would be overkill for simple test/development scenarios. So for basic stuff on asp.net **xsp2** is your best bet where as Apache is an 800 pounds gorilla.

---

### Post by Ch0p5t1ckB01 on 2008-05-23
> **LaRoza said:**
> Try: ```
127.0.0.1:8080
```

I really haven't used that server, so I don't know much about it. Hopefully, someone here will.

Tried that too, still doesn't seem to work.

---

