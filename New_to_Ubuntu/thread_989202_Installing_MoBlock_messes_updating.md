---
title: "Installing MoBlock messes updating"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Sitting Duck on 2008-11-21
Hello

I'm using Ubuntu 8.04 (Hardy Heron).  I reinstalled it yesterday and everything was working fine until I installed MoBlock this morning.  Since then, I can't do updates using the ADD/REMOVE utility or synaptic packet manager.  I can't get updates either.  I always get the same error message:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I follow the instructions, open a terminal and type:
> 
sudo dpkg --configure -a

But nothing seems to happen and all I get is a warning about MoBlock.  The text of the warning follows:

> WARNING: MoBlock may block your complete network/internet access!         &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; MoBlock starts automatically at system boot per default. Some             &#9618; 
 &#9474; preconfigured blocklists are updated once a day. Be warned, that MoBlock  &#9618; 
 &#9474; will not only block many unwanted IPs, but in most cases running MoBlock  &#9618; 
 &#9474; will result in a limited network availability. This includes your own     &#9618; 
 &#9474; LAN and router, many webpages, services like eMail, instant messaging or  &#9618; 
 &#9474; the "weather applet" and your machine's accessibility from the internet.  &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; There are many configuration options to prevent this. Per default         &#9618; 
 &#9474; traffic to your own LAN will always be allowed (whitelisted). This        &#9618; 
 &#9474; feature is still experimental. If you are on a public LAN, you probably   &#9618; 
 &#9474; want to disable this feature.                                             &#9618; 
 &#9474;                                                                           &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>  

I tried a few things, like stopping MoBlock, but nothing seems to work.

Any suggestion/solution?

Thanks in advance

---

### Post by Bios Element on 2008-11-21
```
sudo moblock-control stop
```
Should do the trick.

---

### Post by Sitting Duck on 2008-11-21
Hello Bios Element,

I agree with you that it *should* do the trick, but it doesn't.

Even after I stopped MoBlock, I still can't do updates or add new software.  I still get the same error message...

Thanks for the reply tho :)

---

### Post by jre on 2008-11-22
This is a regular (debconf) warning prompted to the user on installation. Just (read and) **confirm** it and the following questions.

Probably you have to toggle to "OK" by pressing TAB and the press RETURN.

---

