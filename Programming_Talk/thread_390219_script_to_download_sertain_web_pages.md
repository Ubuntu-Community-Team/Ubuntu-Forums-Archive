---
title: "script to download sertain web pages"
date: 2007-03-21
forum: Programming Talk
---

### Post by theorem_hunter on 2007-03-21
hi, 

im not sure if this is the right place to ask this but i need a bit of help for a 3rd year project. 

i need to get a list of airports & airport codes, runway length, longatude & latitude, just like on this page.

[http://www.world-airport-codes.com/south-africa/oliver-reginald-tambo-international-11374.html](http://www.world-airport-codes.com/south-africa/oliver-reginald-tambo-international-11374.html)

at the moment i just need all the south african air ports & the map from google, but hybrid & zoomed in enough so the runway & surrounding buildings are visable.

other information that would help is, any petrol stations in the area, shopping malls, banks, car rental fasilities, cell phone coverage for all networks (although this will mostly be covered) & places of interest.

so how can i write something that can extract that automatically from that web site or is there a tool that already exists that can do that?

thanks

---

### Post by lnostdal on 2007-03-21
I've used Drakma for this on several occasions: [http://weitz.de/drakma/](http://weitz.de/drakma/)

---

### Post by pmasiar on 2007-03-21
> **lnostdal said:**
> I've used Drakma for this on several occasions: [http://weitz.de/drakma/](http://weitz.de/drakma/)

Looks like Drakma is in Lisp. It might be your favorite language (I know for sure that it's lnostdal's fav) and you can run the script OK.

It should not be that hard to write your own program to get data: in Python, urllib2 will download you page from any URL, just parse out juicy bits. Depends if you prefer to play with code (and possibly reinvent the wheel), or read documentation of a tool written by someone else.

This looks like a perfect learning opportunity to reinvent the wheel :-)

BTW: "3rd year" - does it mean you study programming, and this is your course project?

---

