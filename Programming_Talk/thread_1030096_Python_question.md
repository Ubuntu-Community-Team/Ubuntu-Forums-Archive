---
title: "Python question"
date: 2009-01-04
forum: Programming Talk
---

### Post by GammaPoint on 2009-01-04
Hi, I had a question about how to do something in Python. Let's say that I had a Amazon.com product number (called an ASIN). If you enter one of these numbers into the Amazon search bar you come to the page where that product is located.  How could I get a python script to search for a particular ASIN number and take me to that html page?  

I've used urllib before to look at the content of a webpage, but I've never interacted with a webpage in this manner.

Any clues would be greatly appreciated :)

---

### Post by ghostdog74 on 2009-01-04
yes, urllib, urllib2 and other web client modules that can help you get web pages. The product ID number is up to you to parse with the web contents gathered, in which case ,simple string manipulation, indexing/slicing, regular expression or HTML parser tools can be used.

---

### Post by ssam on 2009-01-04
i have heard people say that [Beautiful Soup]("http://www.crummy.com/software/BeautifulSoup/") is very good for parsing information out of HTML.

---

