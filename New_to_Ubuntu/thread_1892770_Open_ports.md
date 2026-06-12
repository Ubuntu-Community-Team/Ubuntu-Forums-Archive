---
title: "Open ports"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by spillage2 on 2011-12-08
Hi All,

Just ran nmap to see what results I get and have found 

exim4   1478 Debian-exim    4u  IPv6   5282      0t0  TCP localhost:smtp (LISTEN)

Would it be best to remove exim4 altogether can only see its some sort of MTA.

I take it thats is not need for my email client (claws) to run correctly?

I now I shouldnt worry to much about viruses but like to know whats doing what and why..

Cheers,

Spill.

---

### Post by wolfen69 on 2011-12-08
Perhaps you could do a [Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2") test to see if your system has any vulnerabilities.

---

### Post by Dangertux on 2011-12-08
> **spillage2 said:**
> Hi All,

Just ran nmap to see what results I get and have found 

exim4   1478 Debian-exim    4u  IPv6   5282      0t0  TCP localhost:smtp (LISTEN)

Would it be best to remove exim4 altogether can only see its some sort of MTA.

I take it thats is not need for my email client (claws) to run correctly?

I now I shouldnt worry to much about viruses but like to know whats doing what and why..

Cheers,

Spill.

You need to realize if you're scanning localhost you're going to get locally bound services which this is. This is normal -- and not an internet accessible service.

Hope this helps.

---

### Post by spillage2 on 2011-12-12
Thanks all for the replies...Only ran this because my broadband is dire at the minute and was worried something was running that shouldnt be.....


Trying to resolve this now as I'm happy its not my comp..

Spill.

ps passed shields up with flying colours...:)

---

### Post by sandyd on 2011-12-12
> **spillage2 said:**
> Thanks all for the replies...Only ran this because my broadband is dire at the minute and was worried something was running that shouldnt be.....


Trying to resolve this now as I'm happy its not my comp..

Spill.

ps passed shields up with flying colours...:)
You know that even if you have ports open on your computer nowadays, they won't be accessable from the internet? Most people connect to the internet through a NAT Router, which will not allow access to computers inside the network unless you specifically allow it. So if you have a router, you should pass shields-up by default.

---

