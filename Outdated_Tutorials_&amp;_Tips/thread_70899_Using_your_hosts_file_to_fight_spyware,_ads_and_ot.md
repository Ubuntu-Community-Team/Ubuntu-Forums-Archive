---
title: "Using your hosts file to fight spyware, ads and other malware!"
date: 2005-10-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Avi on 2005-10-01
Hi all,
Today I've posted on my blog what I think is a cool and super-productive security tip:
[Using your hosts file to fight spyware, ads and other malware!]("http://www.avidardik.com/2005/10/01/using-your-hosts-file-to-fight-spyware-ads-and-other-malware/")
> 
The hosts file exists in virtually every OS I know. Well every Windows and Linux OS I know.
To explain REALLY quickly: It’s a very simple text file that all it does is store a table that translates a computer NAME ([www.goodsite.com](www.goodsite.com)) to an IP address (10.56.23.12).
When your machine wants to do anything online, lets say browse to [http://www.goodsite.com](http://www.goodsite.com), it first checks if the IP address can be found in the hosts file, and only then goes out to the DNS server to get the IP address.
There are 2 obvious advantage of using the hosts file:
1. It is MUCH quicker then checking a DNS online – Virtually instantaneous
2. Allows you to “overrule” the addressing on the DNS. (I can, for example, store [www.goodsite.com’s](www.goodsite.com’s) IP address for the [www.badsite.com](www.badsite.com) name, thus preventing access to the bad site.)
There are other advantages and uses, but the two above are the ones I care about.
Anyhow, I’ve discovered another great way to fight ads and spyware.
Use your hosts file to block Internet access to known ads/spyware sites!
I’ve been familiar with hosts for many years, and the obvious conclusion of using it to essentially blacklist buggers has occurred to me before,
Only now I’ve found out for the first time that there are actually HUGE hosts files ready to be downloaded and used.
And I tell – they work like a charm!
Ok, I can go on about this for ever.
I’ve found quite a few really well known updated, maintained, verified and growing hosts file.
The 3 most well-known ones are:
* [http://www.hosts-file.net/](http://www.hosts-file.net/)
* [http://someonewhocares.org/hosts/](http://someonewhocares.org/hosts/)
* [http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)
All of them have THOUSENDS of addresses.
The one I chose was [http://www.hosts-file.net/](http://www.hosts-file.net/), simply because it was much larger than the other two, more than 40,000 (!!!) addresses!
I simply replaced my own hosts file with the one I’ve downloaded – And – No ads!!!
This is really cool. I have very little ads bothering me. I’ve added an extra layer of protection to my spyware/malware defense.
And all this while actually SAVING bandwidth and not wasting any system resource.
In my opinion having such a hostsfile is a MUST.
It probably shouldn’t be the ONLY line of defense, but it only adds and additional layer while SAVING resources.
There are even little apps that help you with maintaining this huge hosts file.
Hostsman seems to be a great one.
Personally – I chose to do this manually.
Note: If installing in Windows, make sure you disable the DNS Client service! (Read explanations in the sites I’ve mentioned for details…)
Highly recommended!

Also, if I'm already here, and if you haven't already, please check out my most popular series of posts:
[So I’ve decided to switch to Linux. Episode 1: Introduction]("http://www.avidardik.com/2005/02/13/so-ive-decided-to-switch-to-linux-episode-1-introduction/")
Shamless promotion, I know I know... :rolleyes:

---

### Post by UbuWu on 2005-10-01
For ads, I would prefer using the adblock extension for firefox.

---

### Post by imagine on 2005-10-01
And spyware and Adware... Where did you find spyware for your Linuxbox?
You should have at least mentioned where the hosts-file on Ubuntu is, because at the moment this is more of an explanation of the hosts-file than an Ubuntu How-to.

---

### Post by websavages on 2005-10-01
The big disadvantage being when a domain name changes ip. I had a tech support call from a customer who could not access our website. They had a large hosts file with the wrong ip for our domain.

I would not recommend this avenue of attack against spam, ad and malware

Cheers ws

---

### Post by m0biu5 on 2005-10-02
Use Adblock in conjuction with filterset.G ([http://www.pierceive.com.nyud.net:8090/filtersetg/)](http://www.pierceive.com.nyud.net:8090/filtersetg/)). Works like a charm.

---

### Post by ultramancool on 2005-10-02
Yes! This will definitely help me with all that linux spyware :D

---

### Post by frodon on 2005-10-02
What are you talking about !!!!!!!!
it's useless.

---

### Post by sinbad782 on 2005-10-02
privoxy is also good for HTML scrubbing. Certainly cleans ads from most web pages I have seen!

---

### Post by UbuWu on 2005-10-02
[QUOTE=m0biu5]Use Adblock in conjuction with filterset.G ([http://www.pierceive.com.nyud.net:8090/filtersetg/)](http://www.pierceive.com.nyud.net:8090/filtersetg/)). Works like a charm.[/QUOTE]

+ filerset.g updater: [https://addons.mozilla.org/extensions/moreinfo.php?id=1136](https://addons.mozilla.org/extensions/moreinfo.php?id=1136)

---

