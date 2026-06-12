---
title: "Lamp &amp; dns"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by drfln on 2012-08-27
Hi,

I've just installed ubuntu on separate machine on my local network and its running fine - I can access test websites running apache, mysql, php locally.

 Is it possible to setup development environment in such a way that i can access number of different VirtualHosts that are run on ubuntu from another windows/mac machine within the network? Eg.

I have test-site.local running on ubuntu, how would i access it using the same url from another machine on the network? Is this DNS related?

Any help would be greatly appreciated.

Cheers :)

---

### Post by Szor3n on 2012-08-27
Yes, you would need a DNS server to access the different virtual hosts. Now if you simply have "test.local" you *should* be able to access it from any machine on your local network, so long as your router is behaving corectly.  Do you require multiple sites? or is simply having test.local accessable enough?

---

### Post by vandorjw on 2012-08-27
yws but if you dont know how to configure bind an easier and just as good of a aolution is to add the websites and corresponding ip address of the server to the host files on each of the computers on your network

cheers cc7

no dns is required if you have set up Apache virtual host correctly. just edit /etc/hosts or if windows c:\windows\system32\etc\hosts

you computers always check their own host files firsts. maintaining them becomes a pain and that is why dns were made

---

### Post by Szor3n on 2012-08-27
Configuring / updating hosts files for each machine would be so annoying.  At that point I would simply serve the pages on seperate ports, and remember then ports each site was served on D:

---

### Post by vandorjw on 2012-08-27
yep that might work well enough. just rember to open the ports you use for each site in the server firewall

---

### Post by drfln on 2012-08-27
> **Szor3n said:**
> Yes, you would need a DNS server to access the different virtual hosts. Now if you simply have "test.local" you *should* be able to access it from any machine on your local network, so long as your router is behaving corectly.  Do you require multiple sites? or is simply having test.local accessable enough?

I would like to access multiple sites(test1.local, test2.local, etc) from any machine within the network. At the moment i can only access the site via IP and not the host name(s). I think my router is configured correctly, never had an issue with it?

Editing windows/mac hosts file would be a nightmare down the track as number of sites grow.

Thanks for all your feedback so far

---

### Post by Szor3n on 2012-08-27
Seeing your question got me currious, and so I looked into it a bit more. It seems as if the only two options are to: 1) serve your sites on different ports, or modify your hosts files to direct that correct names to the IP of your server. Option 2 wouldn't be so bad if you made a python script or something to sync up the hosts files on each machine.  Otherwise I would stick with option 1, and then create named bookmarks of each 192.x.x.x:xyz so you could keep track of them.

---

### Post by drfln on 2012-08-27
Can i maybe point Windows/Mac to use Ubuntu DNS to lookup local sites first and if none found go to ISP DNS?

---

### Post by vandorjw on 2012-08-27
message removed

---

### Post by stmiller on 2012-08-29
> **drfln said:**
> Can i maybe point Windows/Mac to use Ubuntu DNS to lookup local sites first and if none found go to ISP DNS?

Yes - ideally this would be setup in your router, if it supports being a local DNS server. There you could make DNS entries for your local virtual hosts. 

This is probably too much trouble for what it is worth though...

---

