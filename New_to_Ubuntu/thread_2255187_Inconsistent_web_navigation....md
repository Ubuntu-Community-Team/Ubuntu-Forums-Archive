---
title: "Inconsistent web navigation..."
date: 2014-12-02
forum: New to Ubuntu
---

### Post by Innernet on 2014-12-02
Hi all.
Sometimes, a web site is fetched very fast.  Sometines it takes ~30+ seconds, sometimes times out and displays "Server not found"  At "Try again", sometimes loads the page, sometimes not.

Running 14.04 + Gnome + Wifi hotspot puck only.  Tried another wireless provider at my local public library; behaves better but eventually shows the same misbehavior.  Was not like that a month ago.
Searching for clues on what could be wrong, I found/read this ----> [http://www.linuxquestions.org/questions/mandriva-30/10-1-official-long-delay-during-name-resolution-by-web-browser-262955/](http://www.linuxquestions.org/questions/mandriva-30/10-1-official-long-delay-during-name-resolution-by-web-browser-262955/)
Which points to some wrong setting? in my IPv6?

Got these attached results testing such; how do I fix it if you believe that is the problem ?   Is it my compfuser or is it the internet provider, or ?      ...Am not skilled in tweaking, need your kind guidance.
Also, what is 'nameserver', how do I find/edit/fix if needed ?

---

### Post by papibe on 2014-12-02
Hi Innernet.

Just like your LAN IPv4 LAN address (192.168.1.2), the IPv6 address assigned is a LAN address (fe80::/10).

If you don't see an IPv6 **public** address assigned to you in test-ipv6.com, is because your ISP does not provide you with one.

Hope it helps.
Regards.

---

### Post by Innernet on 2014-12-02
Thanks, papibe.
So it may not be a problem in my compfuser/browser/settings/Wifi ?  Should I request IPv6 to my ISP ?
I never use wired LAN; should that (fe80::/10) be erased/changed ?

---

### Post by papibe on 2014-12-02
> **Innernet said:**
> Should I request IPv6 to my ISP ?
You may ask.

I don't think they offer that service to regular home users, but it wouldn't hurt to ask.
> **Innernet said:**
> I never use wired LAN; should that (fe80::/10) be erased/changed ?
If you are behind a modem/router you'll be assigned a LAN address by default. I wouldn't worry about it.

BTW, if you want to speed up access to the Internet, here are a few ideas:
[LIST]
[*]If you are using your default ISP DNS, try checking out Google Public DNS, or OpenDNS.
[*]Install namebench, benchmark your DNS alternatives, and select the fastest one.
[*]Install your own DNS software like bind or dnsmasq.
[*]Use a DNS caching software like dnsmasq.
[/LIST]
Hope it helps. Let us know if you have more questions.
Regards.

---

