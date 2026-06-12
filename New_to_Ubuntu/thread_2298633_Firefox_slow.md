---
title: "Firefox slow"
date: 2015-10-12
forum: New to Ubuntu
---

### Post by continuity2 on 2015-10-12
I've searched and there are dozens if not hundreds of threads about firefox being slow on ubuntu, so sorry for adding to the pile. However I have tried everything I could find suggested and am still having this issue.

Basically the problem is that although my internet connection is very fast (circa 15ms latency, 20-30Mbps down, 8Mbps up), Firefox intermittently takes forever to load a page, quite often the tab will show the spinning icon and "connecting" for some minutes, and sometimes down the bottom it will say "looking up" or something like that, and these are common sites that don’t have issues like bbc.co.uk and google.co.uk.

I dual boot windows 7 and I don't have the same issue there, I also don't see the same issue on any of my other computers or devices.

The most common advice I have seen is to disable ipv6, I've done that in firefox about:config and in /etc/sysctl.conf I have:
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

and in /etc/init/scip.conf I have:```
# description "Start sysctl at boot" 
 description "sysctl" 
 start on runlevel [2345] 
stop on runlevel [016]  
console log  
respawn 
respawn limit unlimited  
exec /sbin/sysctl -p
```

from the terminal
cat /proc/sys/net/ipv6/conf/all/disable_ipv6

Reports "1"

I don’t think an addin or plugin is to blame, as I’ve run about 5 different Ubuntu environments in the last couple of weeks and they all the the same issue even with firefox fresh from install (don't ask).

---

### Post by tristan16 on 2015-10-12
This question, again. I know this is Ubuntu, but Firefox has support forums as well: [https://support.mozilla.org/en-US/kb/get-community-support](https://support.mozilla.org/en-US/kb/get-community-support)

Firefox also has a lot of troubleshooting information available, so you might want to read this article: [https://support.mozilla.org/en-US/products/firefox/fix-problems/procedures-diagnose-and-fix-problems](https://support.mozilla.org/en-US/products/firefox/fix-problems/procedures-diagnose-and-fix-problems)

Now that that's out of the way, we can start to narrow it down. Do you have similar problems in other web browsers? Does your Wi-Fi have a bad signal? Does it have the same problem when plugged in to ethernet?

Personally, I'd say this sounds like either a bad signal, or a bad DNS. If it's the latter, try changing to a public DNS server like Google: [https://developers.google.com/speed/public-dns/docs/using](https://developers.google.com/speed/public-dns/docs/using)

---

### Post by continuity2 on 2015-10-12
I'm using wired Ethernet, so definitely not a wifi issue.  I'll try changing the DNS settings and see if that works.

---

### Post by vasa1 on 2015-10-12
Firefox has never been slow for me on *buntu. Maybe try some other distro? OTOH, your issue seems confined to one specific machine because of "I also don't see the same issue on any of my other computers or devices."

---

### Post by VMC on 2015-10-12
I get ubuntuforums slow to update pages at times; many times. But the op is complaining about other web sites. Other than here I have no issues with firefox.

---

### Post by continuity2 on 2015-10-14
Its not isolated to one computer, its isolated to ubuntu and firefox in ubuntu. I also run windows 7 on this same computer and that does not have this problem.

I tried adding in the google DNS addresses but it doesn't seem to have made any difference.

The problem seems to be intermittent so its hard to pin down.

---

### Post by tristan16 on 2015-10-14
> **continuity2 said:**
> Its not isolated to one computer, its isolated to ubuntu and firefox in ubuntu. I also run windows 7 on this same computer and that does not have this problem.

I tried adding in the google DNS addresses but it doesn't seem to have made any difference.

The problem seems to be intermittent so its hard to pin down.

Do you have the same problem with other web browsers?

---

### Post by continuity2 on 2015-10-18
OK i've been using chrome for a few days and it is definitely happening in chrome too, so I think that rules out any firefox extensions causing the problem.

I'm using a slightly unusual setup so i'm starting to wonder if that has anything to do with it, my wired internet is via a USB port replicator which has its own Ethernet adapter.

---

