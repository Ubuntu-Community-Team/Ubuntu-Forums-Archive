---
title: "How to load a web page faster, using http://ip_address or http://hostname ?"
date: 2009-10-19
forum: Programming Talk
---

### Post by diffuser78 on 2009-10-19
Hi,

I trying to analyse that if the browser (Firefox, Safari or IE) have the ip address of the hostname, will it load faster ? I am assuming that IP of the hostname if not cached, and browser has to DNS look up the IP for hostname every single time ?

For example: which will load faster in a browser assuming IP is not cached in OS's DNS resovler's cache ?

[http://216.205.76.38/](http://216.205.76.38/)

or 

[http://9278.com/](http://9278.com/)


I am interested in this problem because I am doing this over several million URLs, and even a small saving of half a second will prove to be substantial savings.


Any comments, opinions or feedback ?

Thanks

---

### Post by slavik on 2009-10-19
you can always do the conversion yourself. but why are you doing this over a million URLs? I am pretty sure Google doesn't do DNS caching when crawling.

---

### Post by diffuser78 on 2009-10-19
> **slavik said:**
> you can always do the conversion yourself. but why are you doing this over a million URLs? I am pretty sure Google doesn't do DNS caching when crawling.

I am doing some experiments to understand that if we have million urls and we have their ip's cached so that we by pass the dns caching stage in the browser, we can indeed load page faster. The saving per url would be very less but over a million pages could be substantial.

I just wanted to know if there are any other caveats. For example I want to know if there is anything like that no matter if we have IPs cached, browsers do reverse dns look up etc ? In such case, my experiments will not provide me any gains.

I want to gain opinion from folks who can throw some light on it.

I appreciate your response.

Thanks.

---

