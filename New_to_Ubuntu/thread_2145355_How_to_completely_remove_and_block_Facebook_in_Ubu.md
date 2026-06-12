---
title: "How to completely remove and block Facebook in Ubuntu?"
date: 2013-05-15
forum: New to Ubuntu
---

### Post by D7Gd on 2013-05-15
I would like to completely remove and block anything that has to do with Facebook.

How do I block any Facebook tracking buttons (they call them "likes") that I see on webpages?

I've also noticed that some programs in Ubuntu suggest creating an account on Facebook. I would like to remove those programs, because I would prefer not having any contact with a company whose business model is based on abusing people's personal information.

Here are the reasons:
[https://en.wikipedia.org/wiki/Criticism_of_Facebook](https://en.wikipedia.org/wiki/Criticism_of_Facebook)

---

### Post by dayid on 2013-05-15
Since many sites host their own icons, etc to "link to"/"like" for/from Facebook, you're going to find it hard to completely get rid of it.

That said, use your firewall (or hosts file) and redirect facebook.com so that you're not getting any of the content from there (you may need to do the same for the thousands of sub-domains that facebook uses also). Manually remove any software you don't agree with - that's the freedom of choice.

---

### Post by mastablasta on 2013-05-15
use script blocker add-on on firefox. 

and why would buttons be a problem? they only connect to Facebook. and they matter only if you click on them.

also disable any cookies and make sure you unplug the internet since someone might be watching what you are doing.

---

### Post by Lars Noodén on 2013-05-15
You can easily [use iptables to block Facebook](http://www.howtoforge.com/blocking-facebook-web-trackers-at-the-firewall-for-extra-privacy) and other spy sites.  The main thing is to use the AS Number to look up all the subnets that might be in use.  Once you have the list, you can add it to your host's firewall configuration.  The exact method depends on how you are using iptables, but the article give some general pointers.  If you haven't chosen a method, then you might consider using UFW as the front end for iptables because that's what Ubuntu has chosen.

---

### Post by landersohn on 2013-05-15
Agree with the previous poster, the links in websites are placed by the site. Short of modifying your browser code and compiling your own custom browser that filters this, I don't see a way.
As for not allowing to access facebook that's a little tricky. I tried to block facebook for my son using dansguardian. Didn't work well: facebook has an http and https protocol. The http parts are easy to block, the https parts aren't since by definition https is encrypted, so neither your firewall, dansguardian or anything else can blok access. For my son I had to resort to blocking all https access which is possible. Not sure that's a workable solution for you, though.

---

### Post by Lars Noodén on 2013-05-15
> **landersohn said:**
> For my son I had to resort to blocking all https access which is possible. 

You're doing it wrong then.  HTTPS has nothing to do with Facebook itself.  Blocking Facebook only needs a list of the subnets that belong to Facebook.  You can enter them into iptables using UFW or, if you like graphics, using GUFW.  Doing it that way still allows HTTPS to all other sites but blocks HTTPS and anything else using TCP to or from the Facebook subnetworks.

---

### Post by Lars Noodén on 2013-05-15
Here is how we can find what belongs to Facebook so it can be added to UFW or GUFW.  We use [whois](http://manpages.ubuntu.com/manpages/raring/en/man1/whois.1.html) to find the subnets and use [sort](http://www.madboa.com/geek/sort-addr/) to put them in the right order.

Also, when you make your firewall rules, be sure to use REJECT instead of DENY so that you don't end up wasting a lot of time for connections to time out.  It is in your best interest to use REJECT.

If we are using UFW or GUFW, we can load the subnets into the rules stored in */lib/ufw/user.rules*

```

$ host www.facebook.com
www.facebook.com is an alias for star.c10r.facebook.com.
star.c10r.facebook.com has address 31.13.64.1
star.c10r.facebook.com has IPv6 address 2a03:2880:10:8f01:face:b00c::9
star.c10r.facebook.com mail is handled by 10 msgin.t.facebook.com.

$ whois -h whois.radb.net 31.13.64.1
route:      31.13.64.0/24
descr:      Facebook, Inc.
origin:     AS32934
mnt-by:     MAINT-AS32934
changed:    jj@fb.com 20111025
source:     RADB

$ whois -h whois.radb.net '!gAS32934' | tr " " "\n" | sort -n -t . -k 1,1 -k 2,2 -k 3,3 -k 4,4 
A939
C
31.13.24.0/21
31.13.64.0/18
31.13.64.0/19
31.13.64.0/24
31.13.65.0/24
31.13.66.0/24
31.13.67.0/24
31.13.68.0/24
31.13.69.0/24
31.13.70.0/24
31.13.71.0/24
31.13.72.0/24
31.13.73.0/24
31.13.74.0/24
31.13.75.0/24
31.13.76.0/24
31.13.77.0/24
31.13.78.0/24
31.13.79.0/24
31.13.80.0/24
31.13.82.0/24
31.13.83.0/24
31.13.84.0/24
31.13.85.0/24
31.13.86.0/24
31.13.87.0/24
31.13.88.0/24
31.13.89.0/24
31.13.90.0/24
31.13.91.0/24
31.13.92.0/24
31.13.93.0/24
31.13.94.0/24
31.13.95.0/24
31.13.96.0/19
66.220.144.0/20
66.220.144.0/20
66.220.144.0/21
66.220.152.0/21
66.220.159.0/24
69.63.176.0/20
69.63.176.0/20
69.63.176.0/20
69.63.176.0/21
69.63.176.0/21
69.63.176.0/24
69.63.178.0/24
69.63.184.0/21
69.63.184.0/21
69.63.186.0/24
69.171.224.0/19
69.171.224.0/20
69.171.239.0/24
69.171.240.0/20
69.171.253.0/24
69.171.255.0/24
74.119.76.0/22
103.4.96.0/22
173.252.64.0/18
173.252.64.0/19
173.252.70.0/24
173.252.96.0/19
204.15.20.0/22
204.15.20.0/22

```

---

### Post by Kopkins on 2013-05-15
In the past I've used privoxy to block websites. It also blocks many advertisements, but can break some webpages so requires some configuration to work perfectly.

---

### Post by sandyd on 2013-05-15
I agree with the fact that you cannot block custom facebook images, but you can block facebook completely if you block all of the ipv4 address blocks at [http://bgp.he.net/AS32934#_prefixes](http://bgp.he.net/AS32934#_prefixes) and all of the ipv6 address blocks at [http://bgp.he.net/AS32934#_prefixes6](http://bgp.he.net/AS32934#_prefixes6)

---

### Post by pootan on 2013-05-15
Firefox add-ons


  Adblock Plus add on with subs from this page [https://www.fanboy.co.nz/](https://www.fanboy.co.nz/)

 Ghostery add on

 Cookie Monster add on manager and disable all cookies in Firefox settings. This allows you to blacklist and whitelist cookies and anything else you want to do.

Better privacy add on will delete flash cookies that track you across the web.

Those should keep Facebook and companies they own you don't know about off your back.

Privacy on the internet is a fallacy though.

---

### Post by SeijiSensei on 2013-05-15
If you use Firefox with the [Ghostery]("http://www.ghostery.com/") add-on, a lot of the Facebook links and the like will be suppressed.

---

### Post by vasa1 on 2013-05-15
> **Kopkins said:**
> In the past I've used **privoxy** to block websites. It also blocks many advertisements, but can break some webpages so requires some configuration to work perfectly.
AFAIK, Privoxy doesn't affect http**s**.

---

