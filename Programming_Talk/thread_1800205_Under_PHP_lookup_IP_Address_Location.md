---
title: "Under PHP lookup IP Address Location ?"
date: 2011-07-08
forum: Programming Talk
---

### Post by honeybear on 2011-07-08
Hello, 

One can do that with Linux or using simply the site [http://whatismyipaddress.com/](http://whatismyipaddress.com/). Ok. Sometimes it may be useful to have a protect computer, and track the auth log file. For your APACHE or also for an hosted website on any provider, using PHP, how can one do that simply with PHP? 

Then one would have the city in the PHP loging... 

Google does not propose so much solution as far as I found..

thx:popcorn:

---

### Post by megabytemonster on 2011-07-08
You have to reference some form of database which relates the two, you can't just use the stock PHP functions magically. Useful reading: [http://en.wikipedia.org/wiki/Geolocation_software](http://en.wikipedia.org/wiki/Geolocation_software)

A free webservice you can send your IP address to and retrieve the location back as data: [http://freegeoip.appspot.com/](http://freegeoip.appspot.com/)

---

