---
title: "Malicious cookies placed automatically - Please help!"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-11-04
Hi Everyone,

I'm running a laptop with Crunchbang (Debian derivative) installed and my wife has a laptop with Ubuntu 11.04 installed.

We connect via a home wireless router with WPA2 encryption.
The network is now hidden and I've changed the name and passkey since this began.

I also wiped my hard drive and reinstalled Crunchbang from the CD tonight so I know that my machine is clean.

Beginning about 3 days ago both of us started having a problem with our browsers being redirected. I use Chromium and she uses Firefox. This seems to happen only when we hit a Japanese site.
It is not a specific site but the only thing all the sites have in common is that they are Japanese.

A few minutes ago I was working and refreshed a page at which time I was taken to a page that recommended popular search terms for a town in Michigan.  I live in Sweden and wasn't looking for anything related to Michigan or the US.  I just wanted to refresh a page.

I checked Chromium's cookies and there were about 50 cookies that should not have been there.  They had all been set about 3 minutes earlier.  I can delete the cookies and then go on with my work. I've since blocked all third party cookies without exception.  

**My question is how are the cookies for sites I've never visited getting there?  Is this a problem with my router? Or something else related to the websites we are viewing?** (None of the sites are sketchy - my wife visits a Japanese social networking site and I visit the site of a company I'm doing translation work for.)

I'd really appreciate any help!

---

### Post by gsmanners on 2011-11-04
I'm going to take a wild guess and say that those cookies are getting onto your browser's application data area via iframes (probably some kind of ad service that isn't doing due diligence and letting just anyone run their scam into the iframe). This is why I love adblock.

I still purge my cookies every day. Don't need to block third parties if you don't give them reliable data. It's people who don't purge or block cookies that data miners are interested in, anyway (and there's probably no shortage of them).

---

### Post by elgordodude on 2011-11-04
Well, in several ways, the web site may have been hacked by a third party, a hacker might have sent the cookies with a redirect and then sent you on to the site, the web site may be more malicious than you think, or the cookies may not be as malicious as they appear. 

I can get more than 100 cookies in a weekend, so keep an eye out, but 50 seems reasonable.

Good news is that there's pretty much no chance this has anything to do with your wireless network. A hacker is unlikely to go after a WPA2 home network when he knows there are open and WEP networks all over your neighborhood. Also, WPA2 is extremely difficult to crack, and the goal of wireless cracking is usually to capture packets with credit card and other personal info in them (or just free internet), not to inject cookies into your browser....

---

### Post by s1baker on 2011-11-04
Have you thought about using a host file that will not allow a lot of bad websites and ad servers?

 I use this host file from here:

[http://winhelp2002.mvps.org/hosts.htm]("http://winhelp2002.mvps.org/hosts.htm")

The host text file is where is says" "Download:hosts.zip"
Its just a zipped text file.
Some people don't like to filter out ads though.

Your host file is in your /etc directory. Save the original 
in case you want to put in back.

---

### Post by pqwoerituytrueiwoq on 2011-11-05
cookies can come from anything ie off site images (normally when php generated)/iframes/off ste flash objects (ads)
just disable 3ed party cookies
[[video]](http://www.mediafire.com/?ck1b349cwd3zgc9)
you may need to make exception for some sites (allow google if you use google toolbar)

---

### Post by GrouchyGaijin on 2011-11-05
> **elgordodude said:**
> 

Good news is that there's pretty much no chance this has anything to do with your wireless network. A hacker is unlikely to go after a WPA2 home network when he knows there are open and WEP networks all over your neighborhood. Also, WPA2 is extremely difficult to crack, and the goal of wireless cracking is usually to capture packets with credit card and other personal info in them (or just free internet), not to inject cookies into your browser....

Thank you everyone.  I appreciate the help.

I forgot to mention one thing.
Our apartment complex has Ethernet jacks in most of the rooms of each apartment.  Last week the complex was doing some work on the network.

For a brief time last week I was unable to connect via my router unless I disabled the wi-fi security.  So stupidly, I did disable the security while I was trying to figure out why I couldn't connect. ** The question is can a virus or malware "live" inside my router?  If so, would resetting it to the factory defaults remove it?**

---

### Post by pqwoerituytrueiwoq on 2011-11-05
> **GrouchyGaijin said:**
>  ** The question is can a virus or malware "live" inside my router?  If so, would resetting it to the factory defaults remove it?**
only way i can think of for a virus to get in would to be for you to update it with infected firmware in which care a reset would not do it reinstalling the firmware may get it (unless it was designed to reinstall install it self after)
it is very unlikely a virus is in there

---

### Post by GrouchyGaijin on 2011-11-06
Hi Guys.

The problem continues but I have more information.

It seems to redirect us to what my wife calls "the green page" telling us that the domain is not connected to a registered account and asking us if we want to search for things in the US state of Michigan, **only when we connect via our wireless router**, which is a D-Link 615.

When we connect via the Ethernet jacks that are in the bedrooms of this apartment we don't have any problem.

Until today the problem was with a couple of Japanese sites then my wife got a link from a friend via Facebook to a site in Finland and she got the same redirect.

When I hit the link connected via Ethernet and not the wifi I went to the correct site.

Any ideas???

---

### Post by coldraven on 2011-11-06
As a test you could change the settings for the DNS server in your router.
There are various companies that offer this like Opendns.com or Google
[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

I just found this page which lists some more
[http://theos.in/windows-xp/free-fast-public-dns-server-list/](http://theos.in/windows-xp/free-fast-public-dns-server-list/)

---

### Post by GrouchyGaijin on 2011-11-06
> **coldraven said:**
> As a test you could change the settings for the DNS server in your router.
There are various companies that offer this like Opendns.com or Google
[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

I just found this page which lists some more
[http://theos.in/windows-xp/free-fast-public-dns-server-list/](http://theos.in/windows-xp/free-fast-public-dns-server-list/)
Thank you.

I plugged the Google DNS addresses into the router's DNS fields and so far so good.  I'll know in a while I guess.

---

### Post by coldraven on 2011-11-07
It seems that this problem is happening in Brazil.
I thought that it had been patched a long time ago.
[http://www.theregister.co.uk/2011/11/07/brazilian_dns_cache_poisoing_attacks/](http://www.theregister.co.uk/2011/11/07/brazilian_dns_cache_poisoing_attacks/)

---

### Post by GrouchyGaijin on 2011-11-08
The problem in Brazil is similar to mine.
I only have a problem when connected via my router.
I'm not asked to download anything,but am just taken to a strange page similar to those used to park domains.
It usually happens with a couple of Japanese sites, but has also happened with a site in Finland.

A couple of weeks ago my Gmail was hacked and I had to shut it down.
The hack spammed my address book.

I had thought the hack came from checking my mail at school, but maybe it was through my own router?

---

### Post by coldraven on 2011-11-09
Read this [http://xkcd.com/936/](http://xkcd.com/936/) then change your router password :)

---

