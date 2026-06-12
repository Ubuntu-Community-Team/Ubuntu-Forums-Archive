---
title: "Simple way to whitelist internet traffic?"
date: 2015-03-14
forum: New to Ubuntu
---

### Post by heebiejeebies2 on 2015-03-14
Hello all,

I've been searching like crazy trying to find a solution to a problem  that seems like it ought to be very simple.  All I want to do is block  all internet access at the system level, except for a handful of  hostnames.  OpenDNS cannot do this; Dan's Guardian is ridiculously  complicated, and I can't find a way to set up a proxy server at system  level, only at browser level.

Can you, for example, block all traffic in the hosts.deny file and  then add the needed sites to hosts.allow?  Or can it be done through  ufw?  I'm not averse to using the terminal but I'm a mere mortal who's recently switched from Windows so the solution does need to be within the realm of possibility for my pea-sized computer brain. :p


  Thanks very much

---

### Post by TheFu on 2015-03-14
Firewalls generally work at the IP level, not domainnames.

However, you can block all DNS and only place the hostname-to-IP lookup into your /etc/hosts file.  Most websites won't work well with this, since they include javascript from 3-30 other domains and some of those include javascript from 3-40 other domains so they can track everyone online.  Still, there's little risk to try it.

[B]sudoedit /etc/hosts
[/B]
Go for it.  I wrote an article semi-connected to this - but it was about blocking ad networks with the /etc/hosts. 
[http://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file](http://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file)
There's a newer version on my blog.

If you do the /etc/hosts thing - be certain to disable the DNS stuff wherever that got setup in your system. I'm a server guy - so, for me, that is in the /etc/network/interfaces file. I haven't a clue how the GUI does it.

---

### Post by heebiejeebies2 on 2015-03-14
You know, I think that might be just crazy enough to work! :p  Wonder why no-one suggested this before on all the threads I've read!  It'll probably take a bit of trial and error given the issue you mentioned about javascript and so on but I think this will work nicely.  Now I just need someone to toll me how to disable DNS!

---

### Post by TheFu on 2015-03-15
You know, there are both server and desktop ubuntu guides. Free. Web searches find them easily.

---

### Post by heebiejeebies2 on 2015-03-15
Yes, thank you *rolleyes*. It isn't always the easiest thing in the world to find specific answers like that. :p Still have not found the answer.

---

### Post by TheFu on 2015-03-15
A quick search found this: [http://askubuntu.com/questions/233222/how-can-i-disable-the-dns-that-network-manager-uses](http://askubuntu.com/questions/233222/how-can-i-disable-the-dns-that-network-manager-uses)
Does that not work? 

My search terms where "disable dns ubuntu"

---

### Post by heebiejeebies2 on 2015-03-16
I saw that, but does that completely disable DNS?  I thought dnsmasq was some sort of DNS caching.

---

### Post by heebiejeebies2 on 2015-03-16
Nup, no go.  That doesn't disable the DNS.

---

### Post by TheFu on 2015-03-16
If you disable the cache and remove the DNS settings - that should disable it.  Or you could just set the DNS to a bogus value 10.1.1.1.
Or ... how about editing the nsswitch.conf?
The line is:```

hosts:          files dns
```

make it just ```

# hosts:          files dns
hosts:          files
```

Of course, other systems may have a more complex line ... 
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns

```
so to things need to be removed.
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns
hosts:          files [NOTFOUND=return]

```

A few commands ignore this global setting, but most shouldn't. Lots of stuff will start breaking, so be prepared.

---

