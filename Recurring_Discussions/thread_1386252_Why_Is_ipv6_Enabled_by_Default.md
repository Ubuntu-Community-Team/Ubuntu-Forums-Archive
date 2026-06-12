---
title: "Why Is ipv6 Enabled by Default?"
date: 2010-01-20
forum: Recurring Discussions
---

### Post by moore.bryan on 2010-01-20
Can anyone explain this one to me? I'm trying to understand why Ubuntu chooses to enable ipv6 by default if *very few* ISP's even provide ipv6. Shouldn't it be *disabled* as the default until ipv6 takes-over? I just read so many threads/posts about "my internet is slow" and the resulting "actions" are to disable ipv6 lookups.

Just wondering...

---

### Post by wojox on 2010-01-20
Not sure, but you can disable it here [http://wojox.homelinux.net/?p=4](http://wojox.homelinux.net/?p=4)

---

### Post by moore.bryan on 2010-01-20
> **wojox said:**
> Not sure, but you can disable it here [http://wojox.homelinux.net/?p=4](http://wojox.homelinux.net/?p=4)
Can I assume this is tongue-in-cheek? ;-)

I've already done that... this is more an academic debate.

---

### Post by wojox on 2010-01-20
Gotcha ;)

---

### Post by Lars Noodén on 2010-01-20
@ moore.bryan : IPv6 is there by default because a majority of today's networking security problems would be averted by using IPv6.  

That includes the "[Kaminsky DNS vunlerability](http://unixwiz.net/techtips/iguide-kaminsky-dns-vuln.html)" which probably cost billions during its day.  Also because IPv6 solves a number of other problems through better routing, improved multicasting, simplified but extensible packet headers, **built-in IPSec**, stateful and stateless address configuration eliminate need for DHCP, less header overhead and so on.  

In short it is desirable to steer users towards IPv6 and we can't want another decade while Microsoft Windows continues to hold networking back like it did the WWW or drag it down like it did e-mail or networked storage.  

Besides Linux, BSD, Solaris, and OS X have supported IPv6 out of the box for years.  So it works in a heterogeneous environment.

If your ISP does not yet support IPv6, there are three steps to take.

1) Check if there is a competing ISP in your area that supports it.  If so, then try negotiating a discount for defecting from your current ISP.

2) Formally reqest IPv6 support from your ISP, it will save them work in the end anyway.  

3) Tunnel using [miredo](http://www.debian-administration.org/articles/621) or some other kit.

---

### Post by sanderj on 2010-01-20
An ISP supporting IPv6 is nice, but you can do without. Just type

```

sudo apt-get install miredo
```

and chances are big that you have IPv6 to the outside. To check, visit (or ping6) ipv6.google.com

---

### Post by moore.bryan on 2010-01-20
> **Lars Noodén said:**
> @ moore.bryan : IPv6 is there by default because a majority of today's networking security problems would be averted by using IPv6.  
I agree, but without ISP's that offer ipv6, isn't this moot?
> stateful and stateless address configuration eliminate need for DHCPHmm... never heard this about DHCP; how so?
> 
In short it is desirable to steer users towards IPv6 and we can't want another decade while Microsoft Windows continues to hold networking back like it did the WWW or drag it down like it did e-mail or networked storage.Once again, I agree, but fall back on the ISP issue. 
> 
If your ISP does not yet support IPv6, there are three steps to take.It does not
> 
1) Check if there is a competing ISP in your area that supports it.  If so, then try negotiating a discount for defecting from your current ISP.No dice; both Comcast and Verizon (in my area, I guess, because it isn't this way for others I've spoken to) say they do not now and "do not in the foreseeable future" think they will support ipv6.
> 
3) Tunnel using [miredo]("http://www.debian-administration.org/articles/621") or some other kit.
What's the benefit to this?

Thanks for all the input!

---

### Post by moore.bryan on 2010-01-20
So, I installed miredo and have some new questions:

[LIST=1]
[*]It would seem the ipv6 name resolution is taking an extraordinary length of time; is there any way to shorten the timeout before ipv4 fallback?
[*]How exactly does miredo do what it does? I've read the man and docs, but still don't quite get it.
[/LIST]

---

### Post by JackRock on 2010-01-20
> **moore.bryan said:**
> No dice; both Comcast and Verizon (in my area, I guess, because it isn't this way for others I've spoken to) say they do not now and "do not in the foreseeable future" think they will support ipv6.

Then they're fools or liars (I suspect both).  Without IPv6, the internet, and all network communication will soon be limited to a certain amount of computers.

> **moore.bryan said:**
> What's the benefit to this?

It allows an exponentially higher amount of computers to connect to the internet without the need for intermediary connector devices (such as routers).

---

### Post by cariboo on 2010-01-20
This isn't a support question, more a general discussion on ipv6. Moved to the Cafe

---

### Post by Xbehave on 2010-01-20
slowdown from ipv6 lookups is minimal
fix for slight speed-up is easy
having it working when needed out weights the tiny downside

---

### Post by lovinglinux on 2010-01-21
> **wojox said:**
> Not sure, but you can disable it here [http://wojox.homelinux.net/?p=4](http://wojox.homelinux.net/?p=4)

Thanks for that. I have updated my Firefox tutorial to include your link. Some users might want to disable ipv6 system wide, instead of using a Firefox preference.

---

### Post by sanderj on 2010-01-21
> **moore.bryan said:**
> So, I installed miredo and have some new questions:

Good! Very good!

> **moore.bryan said:**
> 
[LIST=1]
[*]It would seem the ipv6 name resolution is taking an extraordinary length of time; is there any way to shorten the timeout before ipv4 fallback?
[*]How exactly does miredo do what it does? I've read the man and docs, but still don't quite get it.
[/LIST]

What's "extraordinary"; how many millisecs? You can benchmark with the code below. It could be your first configured nameserver does not respond.

```
time host news6.xs4all.nl
time host news6.xs4all.nl 8.8.8.8

```


EDIT: About Miredo: it's an implementation of Teredo, which is an ingenious system of Teredo Client, Teredo Server and Teredo Gateway communicating together. The result is that you get IPv6 connectivity (based on a 2001:0: address) behind (cone and restricted) NAT devices.
See description here: [http://technet.microsoft.com/en-us/network/cc917486.aspx](http://technet.microsoft.com/en-us/network/cc917486.aspx) I needed to read the spec a few times before I understood it.

---

### Post by siimo on 2010-01-21
> **Lars Noodén said:**
> 

In short it is desirable to steer users towards IPv6 and we can't want another decade while Microsoft Windows continues to hold networking back like it did the WWW or drag it down like it did e-mail or networked storage.  


Stop spreading FUD.  Windows has had IPV6 enabled by default since Vista and it is possible to easily install IPV6 on XP in less than 10 minutes.  Yes this is an OS from 2001.

---

### Post by sanderj on 2010-01-21
> **siimo said:**
> Stop spreading FUD.  Windows has had IPV6 enabled by default since Vista and it is possible to easily install IPV6 on XP in less than 10 minutes.  Yes this is an OS from 2001.

Correct. Microsoft is quite pro-IPv6 since WinXP. In Vista, IPv6 is on by default, including Teredo connectivity. In Win7, MS has delivered a complete access service based on IPv6-only.

One correction: it takes 10 **seconds** (not 10 minutes) to enable IPv6 & Teredo on WinXP:

```
netsh interface ipv6 install
netsh interface ipv6 set teredo client
```


;-)

---

### Post by Dayofswords on 2010-01-21
personally... i wish we just switch and get it over with...

---

### Post by Lars Noodén on 2010-01-21
@ siimo : Just because you don't like it doesn't mean it's FUD.  The statement of fact is not meant to hurt your feelings, it is meant to work towards a solution.  The solution means ditching Windows.

Windows does not support IPv6:

[http://www.networkworld.com/news/2007/060707-microsoft-vista-ipv6-incompatible.html](http://www.networkworld.com/news/2007/060707-microsoft-vista-ipv6-incompatible.html)

[http://searchnetworking.techtarget.com/tip/0,289483,sid7_gci1265994,00.html](http://searchnetworking.techtarget.com/tip/0,289483,sid7_gci1265994,00.html)

[http://www.tech-linkblog.com/network-connectivity-and-vistas-tcpipv6/](http://www.tech-linkblog.com/network-connectivity-and-vistas-tcpipv6/)

Yes, *some* IPv6 is there, apparently enough to survive a shallow LAN-based experiment and fool some people.  That is easy, because most Windows users cannot be called the most knowledgeable.  The remainder tend to be predatory on the first group.

---

### Post by Techsnap on 2010-01-21
> That is easy, because most Windows users cannot be called the most knowledgeable. 

Not all Ubuntu users are particularly knowledgeable you know. 

Also not only are those articles old from Vista RTM time but they're also just random blogs, heck if someone posted the same thing about a Linux system they'd be saying the same thing about them being old.

---

### Post by siimo on 2010-01-21
> **Lars Noodén said:**
> @ siimo : Just because you don't like it doesn't mean it's FUD.  The statement of fact is not meant to hurt your feelings, it is meant to work towards a solution.  The solution means ditching Windows.

Windows does not support IPv6:

[http://www.networkworld.com/news/2007/060707-microsoft-vista-ipv6-incompatible.html](http://www.networkworld.com/news/2007/060707-microsoft-vista-ipv6-incompatible.html)

[http://searchnetworking.techtarget.com/tip/0,289483,sid7_gci1265994,00.html](http://searchnetworking.techtarget.com/tip/0,289483,sid7_gci1265994,00.html)

[http://www.tech-linkblog.com/network-connectivity-and-vistas-tcpipv6/](http://www.tech-linkblog.com/network-connectivity-and-vistas-tcpipv6/)

Yes, *some* IPv6 is there, apparently enough to survive a shallow LAN-based experiment and fool some people.  That is easy, because most Windows users cannot be called the most knowledgeable.  The remainder tend to be predatory on the first group.

Those links are all Vista related, some of them pre service pack.  What about Windows 7.

I admit to not knowing much about ipv6 networking, I was just pointing out that Windows had it. 

When ipv6 use goes widespread and global, you keep thinking the worlds most used OS won't be ready then the joke will be on you.  Linux is the only solution forward - haha what a joke.  I am a Linux user but you are just spreading FUD.

This kind of reminds me of:
[img]http://imgs.xkcd.com/comics/supported_features.png[/img]

---

### Post by chuina on 2010-01-21
I have a similar question:

[COLOR="MediumTurquoise"][COLOR="Purple"]Why ipv6 slows the internet connection ?[/COLOR][/COLOR]

Since, it is not invented to slow down any internet connection.
But why ?

Thanks.

---

### Post by lovinglinux on 2010-01-21
> **siimo said:**
> [img]http://imgs.xkcd.com/comics/supported_features.png[/img]

:lol:

---

### Post by arrancaru on 2010-01-21
The problem is not the ipv6 default thing but the big timeout when ipv6 is not avaiable and the system fall back to ipv4. In Windows Vista/7 this problem don't occurs. It's like 30 sec in my machine. And searching for a ipv6 ISP is not an option in most countries or regions.

---

### Post by 3rdalbum on 2010-01-21
In order for any operating system or piece of software to be considered for use in the US government, it MUST be IPv6 compliant, and I believe that actually means "IPv6 by default". Other countries' governments might have similar requirements. Ubuntu has always had IPv6 by default which suggests to me that there are other countries that have had this requirement since before the US government implemented it.

According to some researchers, this is the year when we'll run out of allocatable IPv4 addresses. Remember, big blocks of addresses have been assigned to various organisations that might not be using them all, but still can't be assigned to you or me. I think it's best that everyone start the push for IPv6 right now, before the aeroplanes start falling out of the sky.

---

### Post by Xbehave on 2010-01-21
> **arrancaru said:**
> The problem is not the ipv6 default thing but the big timeout when ipv6 is not avaiable and the system fall back to ipv4. In Windows Vista/7 this problem don't occurs. It's like 30 sec in my machine. And searching for a ipv6 ISP is not an option in most countries or regions.
If it's taking 30s something is wrong, the easiest way to fix is to blacklist the inet6 module but the delay should be far less than a second so if it really is 30s and your not just exaggerating you should figure out why and file a bug report.

---

### Post by sanderj on 2010-01-21
> **arrancaru said:**
> The problem is not the ipv6 default thing but the big timeout when ipv6 is not avaiable and the system fall back to ipv4. 

Can you explain what happens? Is the timeout in de DNS-lookup? Can you do:

```

time host ipv6.google.com
time host ipv6.google.com 8.8.8.8

```

and post the output here?


> **arrancaru said:**
> 
In Windows Vista/7 this problem don't occurs. It's like 30 sec in my machine. 

Probably because Vista/7 do not lookup AAAA addresses.

> **arrancaru said:**
> 
And searching for a ipv6 ISP is not an option in most countries or regions.

As said: "sudo apt-get install miredo" and you should be fine.

---

### Post by moore.bryan on 2010-01-22
[QUOTE=sanderj]
What's "extraordinary"; how many millisecs? You can benchmark with the code below. It could be your first configured nameserver does not respond.
[/QUOTE]
```

bryan@blue-asus:~$ time host news6.xs4all.nl
news6.xs4all.nl has IPv6 address 2001:888:0:4::119:119
news6.xs4all.nl mail is handled by 100 .

real    0m0.717s
user    0m0.012s
sys    0m0.012s
bryan@blue-asus:~$ time host news6.xs4all.nl 8.8.8.8
Using domain server:
Name: 8.8.8.8
Address: 8.8.8.8#53
Aliases: 

news6.xs4all.nl has IPv6 address 2001:888:0:4::119:119
news6.xs4all.nl mail is handled by 100 .

real    0m0.122s
user    0m0.004s
sys    0m0.016s

```This shows very little "wait" time, but I clocked it on my watch (I know, very scientific!) and it took 5 seconds from "Resolving host" (IPV6) to IPV4 fallback. Strange? Oh, by the way, I use [namebench]("http://code.google.com/p/namebench/") to figure-out the best DNS servers... I enabled IPV6, installed miredo, and *then* ran namebench.

---

### Post by moore.bryan on 2010-01-22
> **JackRock said:**
> Then they're fools or liars (I suspect both).  Without IPv6, the internet, and all network communication will soon be limited to a certain amount of computers.
I would also assume both! :-)

> **cariboo907 said:**
> This isn't a support question, more a general discussion on ipv6. Moved to the Cafe
Thanks, Cariboo907; I was originally going to post this in the cafe, but wasn't sure.

> **Xbehave said:**
> slowdown from ipv6 lookups is minimal
fix for slight speed-up is easy
having it working when needed out weights the tiny downside
Not always true *and* the point is there shouldn't need to be any "fix."

> **Dayofswords said:**
> personally... i wish we just switch and get it over with...
Completely agree!

> **chuina said:**
> I have a similar question:
[COLOR=MediumTurquoise][COLOR=Purple]Why ipv6 slows the internet connection ?[/COLOR][/COLOR]
Since, it is not invented to slow down any internet connection.
But why ?

Excellent question chuina!

> **arrancaru said:**
> The problem is not the ipv6 default thing but the big timeout when ipv6 is not avaiable and the system fall back to ipv4. In Windows Vista/7 this problem don't occurs. It's like 30 sec in my machine. And searching for a ipv6 ISP is not an option in most countries or regions.
This also seems to be my problem... like I wrote before, am I missing something?

> **Xbehave said:**
> If it's taking 30s something is wrong, the easiest way to fix is to blacklist the inet6 module but the delay should be far less than a second so if it really is 30s and your not just exaggerating you should figure out why and file a bug report.
In my case, 5 seconds is accurate and even *that* is ridiculous!

---

### Post by KeLa on 2010-01-22
Here something about ipv6 for those who don't like to disable it.
[http://www.cert.fi/en/reports/2010/vulnerability341748.html](http://www.cert.fi/en/reports/2010/vulnerability341748.html)
It's fresh today's publication of "CERT-FI Advisory on Linux IPv6 Jumbogram handling"

---

### Post by sanderj on 2010-01-23
> **moore.bryan said:**
> This shows very little "wait" time, but I clocked it on my watch (I know, very scientific!) and it took 5 seconds from "Resolving host" (IPV6) to IPV4 fallback. Strange? 

Strange indeed.

What's the output of:

```

date; time host news6.xs4all.nl ; date

```

---

### Post by d3v1150m471c on 2010-01-23
I wouldn't disable ipv6 on your system. Instead, disable it in your browser so that it's easily reversed if you screw something up. There are tutorials for this all over google for various browsers.

---

### Post by moore.bryan on 2010-01-23
> **sanderj said:**
> Strange indeed.

What's the output of:

```

date; time host news6.xs4all.nl ; date

```
Once again, all results *appear* normal, but the time lag as DNS drops from IPV6 to IPV4 is hovering around 5 "clock" seconds...
```

bryan@blue-asus:~$ date; time host news6.xs4all.nl ; date
Sat Jan 23 07:20:51 EST 2010
news6.xs4all.nl has IPv6 address 2001:888:0:4::119:119
news6.xs4all.nl mail is handled by 100 .

real    0m0.559s
user    0m0.004s
sys    0m0.008s
Sat Jan 23 07:20:52 EST 2010

```

---

