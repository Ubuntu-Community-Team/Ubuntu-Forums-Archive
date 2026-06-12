---
title: "Ubuntu - Public Wifi Security?"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by mapes12 on 2012-10-11
I've been reading media reports about how unsafe public wifi hotspots can be with potential hackers getting access to your website usernames and passwords. Is there a way I can configure my Ubu laptop to make it secure on public wifi networks?

Mark

---

### Post by DuckHook on 2012-10-11
Ubuntu (and Linux in general) is especially suited to safe browsing on unencrypted public WIFI hotspots, but the details are rather complex for new users, and involve both extra (or modified existing) equipment and setting up your computer in a non-simple way.

Conceptually, it comes down to the following:

1. You buy a router (or change an existing one) at home capable of establishing what is called a VPN tunnel (Virtual Private Network). This is just a fancy term for an encryption technology that scrambles all of your data packets so that any bad guy listening in cannot decipher your data.

2. You activate the openVPN module that is already preloaded in Ubuntu, and make sure that you connect with your home VPN network as your first order of business whenever you are connecting from a public place.

*Voila*. You're as secure as you're realistically gonna get.

As I say, this is simple conceptually. The details are a little more involved and not really the sort of thing for an absolute beginners forum.

As a primer, try this:

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

Personally, I run a modified router loaded with openVPN capable of accepting tunnel requests from my laptop whenever I am on the road. There are details like subscribing to a DDNS service that are, again, beyond the scope of this forum. I understand that there are commercial services that will act in the same capacity as the home router, but I can't see myself paying for something that I can set up for myself. I would suggest searching through prior postings in the *Network and Wireless* forum. This topic comes up all the time there.

---

### Post by xedi on 2012-10-11
A simple improvement on both Linux and other OSes is to use the encrypted https protocol when surfing the web. Many websites support this but unfortunately often not per default. E.g. in facebook you have to activate it in their options or in the case of wikipedia you have to manually enter always [https://www.wikipedia.org/](https://www.wikipedia.org/)

Alternatively you can use the https everywhere plugin for firefox, chrome/chromium which forces the browser to use https wherever possible. [https://www.eff.org/https-everywhere](https://www.eff.org/https-everywhere)

---

### Post by CharlesA on 2012-10-11
It would be better to use a VPN or SSH tunnel instead of relying entirely on HTTPS. SSL can be stripped.

---

### Post by zhogan85 on 2012-10-11
> **CharlesA said:**
> It would be better to use a VPN or SSH tunnel instead of relying entirely on HTTPS. SSL can be stripped.

+1

Here's a recent life hacker article, with several VPN providers, several of which work well with linux.

[http://lifehacker.com/5935863/five-best-vpn-service-providers]("http://lifehacker.com/5935863/five-best-vpn-service-providers")

---

### Post by DuckHook on 2012-10-11
> **CharlesA said:**
> It would be better to use a VPN or SSH tunnel instead of relying entirely on HTTPS. SSL can be stripped.

Moreover, HTTPS does nothing for e-mail which, for most people using an e-mail client, is sent in the clear over POP/SMTL/IMAP.

It bears noting that perhaps the best strategy is to avoid using public hotspots altogether. I see people connecting their phones and tablets without a single security thought to unsecured WIFI all the time. It's not just laptops, which at least have the *potential* to be secured.

---

### Post by zhogan85 on 2012-10-11
> **DuckHook said:**
> It's not just laptops, which at least have the *potential* to be secured.

Some VPN providers provide android apps, so you can securely use your phone, too.

For my own mobile security, I typically avoid public wifi, and use my own mobile hotspot.

---

### Post by CharlesA on 2012-10-11
> **DuckHook said:**
> Moreover, HTTPS does nothing for e-mail which, for most people using an e-mail client, is sent in the clear over POP/SMTL/IMAP.

It bears noting that perhaps the best strategy is to avoid using public hotspots altogether. I see people connecting their phones and tablets without a single security thought to unsecured WIFI all the time. It's not just laptops, which at least have the *potential* to be secured.
Yep. Quite scary if you think about it. I prefer to tunnel my traffic if I am stuck using airport/starbucks/hotel wifi.

---

### Post by xedi on 2012-10-12
My suggestion about HTTPS was more intended as an easy thing you can do to have something which is better than nothing. Thanks for clarifying for others that this far from optimal, though.

---

### Post by Cheesemill on 2012-10-12
Have you seen this recent thread?

[http://ubuntuforums.org/showthread.php?t=2068130](http://ubuntuforums.org/showthread.php?t=2068130)

---

