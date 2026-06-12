---
title: "How to handle proxy at work but not at home?"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by javafanboy on 2012-01-04
At first I had a lot of problems with how to specify a proxy. I would have liked to specify a proxy.pac file in one place and had it take effect for all applications (Firefox and apt-get for starters) but it seems like there is no single standard for specifying this or have I missed how to do it?

I do however have a more serious problem - At home I do not use a proxy but at work I must specify one. Unfortunatly it seems like when I have a proxy specified (to make things as needed when at work) it will not work when I am at home (apt-get complain that the proxy server cant be found).

Is there a way to make things work automatically both at home and at work, i.e. both with and without a proxy server?

/Javafanboy

---

### Post by mike555 on 2012-01-04
You could use two different browsers , one at work ,then a different one at home....... set one to use proxy and the other not to.

or something like the Firefox add-on Foxyproxy

---

### Post by javafanboy on 2012-01-04
Thanks for the quick reply!

I forgot to mention that I am using 11.10. 

No other more generic sugestion that would work for both apt-get and browser (preferably without having to use two browsers - that seemed like a work-around)?

Surely there must be lots of people with laptops that have run into this problem before?

/Javafanboy

---

### Post by audiomick on 2012-01-04
> **javafanboy said:**
> ...
Is there a way to make things work automatically both at home and at work, i.e. both with and without a proxy server?

/Javafanboy
I dare say you would have to create a new network connection in the network manager for each case, but that is really a guess... :-k

---

### Post by wollac on 2012-01-04
I don't know about apt but firefox is an easy fix. There is an addon called [Toggle Proxy ]("https://addons.mozilla.org/en-US/firefox/addon/toggle-proxy-51740/") which enables you to switch the proxy on and off with a button or a simple keyboard shortcut.

I'm sure there must be a way of solving this system-wide I just cannot think at the moment how you would do it.

---

