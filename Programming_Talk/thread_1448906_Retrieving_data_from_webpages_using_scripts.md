---
title: "Retrieving data from webpages using scripts"
date: 2010-04-07
forum: Programming Talk
---

### Post by metafractal on 2010-04-07
Hi guys,

Here is my situation: For a project I am doing at uni, I need to monitor petrol prices in my home city of Melbourne. Luckily the relevant data is posted online daily at the following websites so that I don't need to drive out to the petrol stations every day:

[http://motormouth.com.au/pricesearch.aspx](http://motormouth.com.au/pricesearch.aspx)

[http://www.racv.com.au/wps/wcm/connect/Internet/Primary/my+car/advice+_+information/fuel/petrol+prices/?CACHE=NONE](http://www.racv.com.au/wps/wcm/connect/Internet/Primary/my+car/advice+_+information/fuel/petrol+prices/?CACHE=NONE)

Now it is awfully tedious to collect all the necessary data manually every day. I'd like to write a script to retrieve the data automatically.

If the pages were just plain POST method PHP then one could theoretically just wget the pages and do some regex parsing of the HTML (I imagine there must also be a more elegant way of doing this too, but that is what came to mind). However, the pages seem to use GET so that one can not just wget a given web page with the relevant search terms in the web address.

Is there a way to easily do this with a bash script or something similar? I have some experience programming and am quick at picking up new languages, so that's not a problem. I just need someone to point me in the right direction. A skeleton of how the script would look would be ideal, but any tips are appreciated.

Cheers,
meta

---

### Post by Reiger on 2010-04-07
Wget works with both POST and GET data.

GET uses the query string affixed to the URL directly; POST is an additional option: --post-data.

---

### Post by tgalati4 on 2010-04-07
Do a google search on web page scraping techniques.

Also:

apt-cache search curl

sudo apt-get install curl

man curl

---

### Post by gmargo on 2010-04-07
I do that sort of thing in Perl with the HTML::TreeBuilder module.

---

### Post by metafractal on 2010-04-07
Great! Thanks for all your advice, that's just the kind of thing I was looking for.

---

