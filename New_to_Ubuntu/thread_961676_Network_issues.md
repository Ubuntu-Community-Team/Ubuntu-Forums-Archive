---
title: "Network issues"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by y_not on 2008-10-28
Help! How do I tune my internet access for fast load speed? I have a 100 Mb/s connection that works great in XP, but not in Ubuntu.

Hello all,
I'm yet another newbe eager to join the ranks of the Linux-initiated.
I'm a self-help kinda guy, but I'm having trouble with my core reference: the  internet.

So I installed Ubuntu and found a very clean XP-reminiscent environment. Hardware works from all I can tell, but my pageloads in firefox are terribly slow. I watched the 'System Monitor' for a while and it seems like there are short spikes of activity (send and read) but they only register in the 'Total' after repeated attempts. How do I speed things up?!

---

### Post by eentonig on 2008-10-28
Is the network slow, or is it just the perception that Firefox is slow?

Try to do some pings with various mtu sizes from both windows and Ubuntu to see if there's any difference.

To be honest, I also find Firefox to be significantly slower under Linux in comparison to Windows.

---

### Post by xpod on 2008-10-28
I`m not sure if it`s entirely what your looking for but i find using the OpenDNS servers makes our 20Mb connection much snappier,certainly as far as the browsing and page load times are concerned anyway.
I dont have any problems reaching the 20Mb speeds themselves,regardless of who`s DNS i use but OpenDNS does make the browsing that bit faster.Most of the time anyway:)

---

### Post by y_not on 2008-10-28
Thanks; so what's the fastest way to initiate a ping?

---

### Post by xpod on 2008-10-28
> Thanks; so what's the fastest way to initiate a ping? 

There is a Network Tools utility in your menus that you could use but your probably better using the Terminal like most others do.You`ll find that in your menu`s too via Applications/Accessories.

Heres a couple of quick Googles on the subject....For Ubuntu
[http://onlyubuntu.blogspot.com/2008/07/how-to-optimize-your-internet.html](http://onlyubuntu.blogspot.com/2008/07/how-to-optimize-your-internet.html)

And one for Windows
[http://help.expedient.com/broadband/mtu_ping_test.shtml](http://help.expedient.com/broadband/mtu_ping_test.shtml)

---

### Post by y_not on 2008-10-28
So I did a couple of pings. XP and Ubutu returned very similar times. (85-87 ms to en.wikipedia.org)

Following the tutorial from [http://onlyubuntu.blogspot.com/2008/...-internet.html](http://onlyubuntu.blogspot.com/2008/...-internet.html)
I established an ideal MTU of 1472 (+28)

Before I go further into detail such as manually setting the MTU and/or RWIN as discussed in the link, I wonder if this tells you more about my problem?
Please consider that I'm not just impatiently frustrated with some small lag.  It takes 18-30 seconds to load a simple page on this forum.

---

### Post by y_not on 2008-10-28
sorry, thats 1472+28 MTU, not 1472+smileyface

---

### Post by xpod on 2008-10-29
> Before I go further into detail such as manually setting the MTU and/or RWIN as discussed in the link, I wonder if this tells you more about my problem?
Please consider that I'm not just impatiently frustrated with some small lag. It takes 18-30 seconds to load a simple page on this forum.

If your response times are as fast/slow on both Windows & Ubuntu then i`d mabey check with my ISP to see what they say.Mabey try another network card if possible.I`m not sure what else other than that 
At the moment my own response times to Wikipedia are less than half what yours are but then i have seen them much slower,evenings and weekends usually.

There are a couple of other tips for speeding FF up here you could try.
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

