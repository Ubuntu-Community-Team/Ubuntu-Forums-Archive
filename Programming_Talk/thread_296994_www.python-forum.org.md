---
title: "www.python-forum.org"
date: 2006-11-10
forum: Programming Talk
---

### Post by Andrew1234 on 2006-11-10
Does anyone know where [www.python-forum.org](www.python-forum.org) has gone:confused:  for the last two days I cannot load the index page?

---

### Post by whatintheworldisthat on 2006-11-10
works for me, thats weird. is the url you posted above the one that doesn't work, does for me.

---

### Post by Andrew1234 on 2006-11-10
Yes, I have used it for several weeks now what url are u using? As is still isn't working for me in IE7 or SeaMonkey or Firefox](*,)

---

### Post by Vex on 2006-11-10
Working fine for me. Using the link you've posted above.

---

### Post by AgenT on 2006-11-10
> **Andrew1234 said:**
> Yes, I have used it for several weeks now what url are u using? As is still isn't working for me in IE7 or SeaMonkey or Firefox](*,)
Website works fine in Firefox and ping. Try to ping the site yourself. Check your network (cables, router, modem, etc.). Here is the output:
```
$ ping -c 1 www.python-forum.org
PING python-forum.org (64.157.176.245) 56(84) bytes of data.
64 bytes from dreamlink.net (64.157.176.245): icmp_seq=1 ttl=49 time=1827 ms

--- python-forum.org ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1827.679/1827.679/1827.679/0.000 ms

```

---

### Post by Andrew1234 on 2006-11-11
I have Ping the website and get this:-

```
andrew@shopmail:~$ ping -c 1 www.python-forum.org
ping: unknown host www.python-forum.org
andrew@shopmail:~$ 

```

What I find strange is that I am using two different PC's and still cannot connect to the site?

---

### Post by AgenT on 2006-11-11
> **Andrew1234 said:**
> I have Ping the website and get this:-

```
andrew@shopmail:~$ ping -c 1 www.python-forum.org
ping: unknown host www.python-forum.org
andrew@shopmail:~$ 

```What I find strange is that I am using two different PC's and still cannot connect to the site?
Check your network (cables, router, modem, etc.). If you are sure it is not your network, call your ISP. This sounds like a DNS problem. It may be that your ISP's DNS servers are having problems. Or it may be that your router is having DNS problems or it is blocking certain traffic (doubtful if you can visit other websites). Note that calling your ISP may not yield much as the people may not know what to do or may not be willing to help you (if you live in the USA). In this case, find out DNS servers for your ISP and try manually changing your DNS settings in your router. Or, wait it out.

The best way to determine what the problem is is to use Wireshark (formally known as Ethereal). Launch it using to "root" version and sniff your traffic. You will probably see DNS errors.

---

### Post by DaveBorealis on 2006-11-11
> **Andrew1234 said:**
> 
```
andrew@shopmail:~$ ping -c 1 www.python-forum.org
ping: unknown host www.python-forum.org
andrew@shopmail:~$ 

```

Hello Andrew,

Try pinging the IP address (the one below I obtained by pinging 'www.python-forum.org'):
```
$ ping -c1 64.157.176.245
```
If this works, then it's definitely a DNS issue.

Dave

---

### Post by Andrew1234 on 2006-11-11
Thanks AgenT and Dave, 
Just ping using ping -c1 64.157.176.245 and I get a result back so it must be a DNS issue, I will contact my ISP first to see what issues there are. 
Thank you.

---

### Post by JayTee on 2006-11-11
In the meantime if you need to go there just type http://"ipaddress" and it'll take you there.

---

### Post by Andrew1234 on 2006-11-18
After several emails and phone calls I am not getting anywhere my ISP are saying it is an issue with the website so I need to contact the forum moderator, can anyone let me know the email address or any other ways around this problem.
Thanks

---

### Post by megadyptes on 2006-11-29
I seem to be suffering this problem with [www.python-forum.org]("www.python-forum.org") as well. Did you ever resolve the issue?

---

### Post by Andrew1234 on 2006-12-05
Hi 
In my case,this is an issue with Tiscali and BT from what I can understand, and Tiscali are a real pain in the neck to try to get things sorted out, I have taken a complaint up with them because of several issues and they say "their engineers are working on it" ???  ](*,).

Rome wasn't built in a day, but I could walk there quicker than they can fix this.(I live in North Lincolnshire,England)

Any case, I am moving to BT due to this and other issues I hope the service is better!

But if you are with Tiscali report it to Customer Service, but I will worn you you will be on the phone for hours and if you email them you will you will never get a straight answer reply](*,) ](*,)If you are with another ISP also contact them, to save you time do Trace and ping the site. If you need ip address let me know as I should have it.

---

### Post by megadyptes on 2006-12-05
Well, it's not unique to Tiscali as I'm with a different ISP. I can get round it by pointing the router away from their nameservers and at a public one, so I guess that's where the problem lies.

I wonder if they'll be any more accommodating when I mention it?

---

### Post by MattKemp on 2006-12-05
You could also put the following in your /etc/hosts file until then:

```

64.157.176.245    www.python-forum.org

```

which will tell your browser to go to this page no matter what. You'll run into trouble if they swap servers or something similar, but if it stops working again you just have to remove this line from your file and it should work (if your DNS is fixed).

---

