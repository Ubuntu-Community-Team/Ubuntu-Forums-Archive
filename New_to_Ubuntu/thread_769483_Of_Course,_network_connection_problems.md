---
title: "Of Course, network connection problems"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by fathercb on 2008-04-26
Thanks to anyone with smarts and thats everyone besides me.
Seems like internet connections are common with ubuntu.  I have read a lot of the post concerning connections.  

I really like ubuntu, all seems great, except I cannot connect to the internet.  I am using ubuntu over windows xp.  I am 50 yo and really really stupid concerning computer lingo. I absolutely hate  MS stuff and the way they disregard their customers.  I have been a customer of theirs since I had a commadore vic 20.  Anyway...  

I tried to disable the roaming and turn automatic.  I tried to manual set dns.  I pinged several places, nothing.  I went to terminal and typed in ifconfig eth1 and got nothing.  

I am using at&t through the phone through my router. I have a presario laptop with windows xp.  Going through xp I have no problems connecting.

Thanks to anyone that may be able to lead me through to a solution.  P.S. if you choose to help me, please remember my mind is old and does not compute like you younger folks do. Thank you.

---

### Post by Mazza558 on 2008-04-26
First of all, we need to know what Wireless card you're using. Open a terminal and type in 

> lspci

This'll give you a list of all the extra hardware like networking adapters connected to the PC. Copy and paste it here.

---

### Post by frup on 2008-04-26
This means you are using a wired connection right?

Do you know your routers IP (eg 192.168.1.2) see if you can connect to that via the browser. Sometimes I have had an issue where while it can connect to the router, it can't connect to the internet. The fix is simply adding the routers address to the DNS tab under the network tool.

If that doesn't fix the problem, what were you entering for the manual connection?

---

### Post by Mazza558 on 2008-04-26
First of all, we need to know what Wireless card you're using. Open a terminal and type in 

> lspci

This'll give you a list of all the extra hardware like networking adapters connected to the PC. Copy and paste it here.

---

