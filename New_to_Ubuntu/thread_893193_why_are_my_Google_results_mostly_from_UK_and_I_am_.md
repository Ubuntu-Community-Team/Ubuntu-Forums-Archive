---
title: "why are my Google results mostly from UK and I am from U.S."
date: 2008-08-18
forum: New to Ubuntu
---

### Post by MeTylerDurden on 2008-08-18
U.K results seem like an awful lot of them.

---

### Post by Loaded.len on 2008-08-18
Work for a company that has restricted site access to a lot of your favourites, so you use their European proxy to skirt their filter?

I used to do it all the time. :)

---

### Post by nicedude on 2008-08-18
I don't understand the question now, are you in the USA and using your home internet and most searches are comming up with UK sites? Or are you at a company doing searches and this is happening? Or lastly are you searching for BBC TV shows and this is happening :-)

You could always run a traceroute to a known USA web address and see where your data is going to get there, Like traceroute Microsoft or Google and look at the route and see if it jumps from USA to Europe and back.

---

### Post by MeTylerDurden on 2008-08-18
I am in USA doing home internet searches. For instance, if I search for Ebay on google it will come up with UK ebay  .. I have to search for U.S. Ebay to get a result for United States. Yes, I live here.

---

### Post by Loaded.len on 2008-08-18
Odd, I'm in Canada, but when I switch from google.ca to google.com and search for ebay, the first 3 hits are:

Search Results

   1.
      eBay - New & used electronics, cars, apparel, collectibles ...
      Buy and sell electronics, cars, clothing, apparel, collectibles, sporting goods, digital cameras, and everything else on eBay, the world's online ...
      Show stock quote for EBAY - Filter - History
      [www.ebay.com/](www.ebay.com/) - 54k - Cached - Similar pages - Note this
   2.
      eBay - The UK's Online Marketplace
      Visit eBay UK and register to buy or sell new and used books, cars, computers, digital cameras, DIY, DVD, jewellery and music. Auction or Fixed Price.
      [www.ebay.co.uk/](www.ebay.co.uk/) - 74k - Cached - Similar pages - Note this - Filter - History
   3.
      eBay Australia - Buy or sell practically anything on eBay, the ...
      Visit eBay, Australia's online marketplace for cars, clothing, electronics, digital cameras, sports, DVDs, toys and more. Buy and sell almost anything on ...
      [www.ebay.com.au/](www.ebay.com.au/) - Similar pages - Note this - Filter - History


Maybe Google has some load balancing issues and it's fetching results from European datacenters??


NOTE: not one single UK hit when searching google.ca

---

### Post by MeTylerDurden on 2008-08-18
here is a screenshot of my ebay search on Google

---

### Post by Loaded.len on 2008-08-18
look in your address bar.  google.co.uk

you're searching from the Ubuntu start page aren't you?  Set your homepage to google.com and happy searching

---

### Post by MeTylerDurden on 2008-08-18
Here is a search for "tools"

---

### Post by aktiwers on 2008-08-18
You are on Google.co.uk !!!!! :D

[SIZE=-1][Try this one ... Click!]("http://www.google.com/ncr")[/SIZE]

---

### Post by MeTylerDurden on 2008-08-18
> **Loaded.len said:**
> look in your address bar.  google.co.uk

you're searching from the Ubuntu start page aren't you?  Set your homepage to google.com and happy searching

sad times take care of themselves and good times must be divided with others... thanks

---

### Post by Loaded.len on 2008-08-18
Yes, as I said... Ubuntu start page google applet, goes through the UK servers.  don't use it.

---

### Post by nicedude on 2008-08-18
That is very strange if you are not using any proxy connections ( TOR for example ). Did you install a firefox plugin called TOR or any other things that promised to anonomize your internet? If not then I would recommend installing traceroute from the repositories and using it to traceroute to [www.google.com](www.google.com)

here is the command to install it

sudo apt-get install traceroute

then run this in a terminal to list where your data goes

traceroute [www.google.com](www.google.com)

Here is output of mine, minus the first three hops which contain my private address :-) yours should look similar as in a bunch of hops through your Internet providers network then a few hops thru a internet backbone provider and then google. If it looks considerably different then you will need to find out who the last steps before google.com are and where they are located you can do this on the Internet with a Whois search of the addresses. If you do what I am suggesting and post say #4 on up I will look it up for you and tell you where your data is going.

 4  ixc00sdf-ge-1-0-1.bellsouth.net (205.152.133.82)  53.524 ms  55.668 ms  58.587 ms
 5  ber01bgk-pos-2-0-0.bellsouth.net (205.152.161.49)  61.247 ms  62.960 ms  65.641 ms
 6  205.152.161.64 (205.152.161.64)  68.534 ms  37.100 ms  38.710 ms
 7  ixc01tys-pos-7-0-0.bellsouth.net (205.152.161.62)  41.379 ms  31.409 ms  33.501 ms
 8  ixc00tys-ge-1-0-0.bellsouth.net (205.152.45.64)  35.896 ms  38.316 ms  40.741 ms
 9  ixc01cha-pos-7-0-0.bellsouth.net (65.83.239.103)  39.970 ms  42.642 ms  45.314 ms
10  axr01aep-so-3-0-0.bellsouth.net (65.83.239.28)  50.698 ms  53.651 ms  56.038 ms
11  axr01aep-ge-5-1-0.bellsouth.net (65.83.238.37)  86.832 ms  87.016 ms  45.196 ms
12  pxr00asm-3-0-0.bellsouth.net (65.83.236.6)  33.339 ms  35.460 ms  30.398 ms
13  65.83.237.221 (65.83.237.221)  34.236 ms  35.153 ms  38.322 ms
14  72.14.233.56 (72.14.233.56)  41.248 ms  43.176 ms  46.123 ms
15  72.14.232.215 (72.14.232.215)  49.008 ms 72.14.232.213 (72.14.232.213)  51.437 ms 72.14.232.215 (72.14.232.215)  53.377 ms
16  209.85.253.161 (209.85.253.161)  65.434 ms 209.85.253.157 (209.85.253.157)  34.564 ms 209.85.253.169 (209.85.253.169)  44.802 ms
17  yw-in-f147.google.com (74.125.47.147)  36.849 ms  39.275 ms  41.699 ms

---

### Post by nicedude on 2008-08-18
OK I see someone else solved this bugger and I learned something. I had no idea Ubuntu homepage linked to google in UK that is good to know, I just never used that as a homepage and therefore had no idea. Good tidbit in case I ever see this behavior and wonder why.

---

