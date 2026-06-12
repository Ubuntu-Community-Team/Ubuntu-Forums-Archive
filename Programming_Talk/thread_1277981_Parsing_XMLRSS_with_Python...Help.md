---
title: "Parsing XML/RSS with Python...Help"
date: 2009-09-29
forum: Programming Talk
---

### Post by Amstell on 2009-09-29
I'm trying to parse some buoy data from : [http://www.ndbc.noaa.gov/data/latest_obs/46231.rss](http://www.ndbc.noaa.gov/data/latest_obs/46231.rss)

The main problem I am having is trying to output the specific data that is enclosed with <strong></strong>.

Can someone help get me started on just outputting this information.  I've worked on feedparser.py, butit won't let me access the actual data.  I am only able to grab the title and description but not the actual data, which is enclosed in <strong></strong>

feedparser.py : [http://www.feedparser.org/](http://www.feedparser.org/)

Thanks for any help you can provide.  I'm just trying to process some data for surf reports and display them into conky.  This is just the first step and I'm stumped.  

Cheers

---

### Post by wmcbrine on 2009-09-29
The "strong" tags are just HTML embedded within the description, basically for decoration. They're not technically part of the RSS. And in the description I'm looking at from that URL right now, the stuff enclosed by "strong" tags is *not* the actual data, but rather the field names, plus the date.

What exactly do you want to end up with?

P.S. One possibility, as a one-liner -- assumes you have the description in a string named "description", and that they're all formatted the same way:

```

dict([[z.strip() for z in y.split(':')] for y in [x.strip() for x in description.replace('<strong>', '').replace('</strong>', '').split('<br />')[1:] if x.strip()]])

```

---

### Post by Amstell on 2009-09-30
I'm looking to pull all of the data off of the buoy:  Height, temp, wind, swell direction.  I need all of that, but I can't figure out how to parse the exact xml doc they provide and then just display it or write it to a text file.

Thanks for the help.

---

### Post by A_Fiachra on 2009-09-30
There are many ways to skin this cat.

The data that you want is in the CDATA section of the feed -- I have no idea why RSS allows this --- I mean -- the point of Really Simple Syndication is, one assumes, to be really simple???  So why the !@#$ do people put html tags in their feeds??

Don't get me started.


There is an excellent library for parsing html called BeautifulSoup.

```

$ wget -O 41nt0.rss http://www.ndbc.noaa.gov/data/latest_obs/41nt0.rss
python
Python 2.6.2 (r262:71600, Aug 28 2009, 10:27:49)
[GCC 4.1.2 20070626 (Red Hat 4.1.2-14)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>
>>> import feedparser
>>> doc = feedparser.parse("/home/alee/src/NDBC/41nt0.rss")
>>> for k in doc.keys():
...     if k == 'entries':
...             print doc[k]
...
[{'summary_detail': {'base': '', 'type': 'text/html', 'value': u'<strong>September 29, 2009 2200 UTC</strong><br />\n ....


```


Ok -- that much you have figured out, clearly.

So let's try:

```

$ wget -O 41nt0.rss http://www.ndbc.noaa.gov/data/latest_obs/41nt0.rss
python
Python 2.6.2 (r262:71600, Aug 28 2009, 10:27:49)
[GCC 4.1.2 20070626 (Red Hat 4.1.2-14)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>
>>> import feedparser
>>> doc = feedparser.parse("/home/alee/src/NDBC/41nt0.rss")
>>> for k in doc.keys():
...     if k == 'entries':
>>> for k in doc.keys():
...     if k == 'entries':
...             dict = doc[k][0]
...
>>> soup = BeautifulSoup.BeautifulSoup(dict['summary_detail']['value'])
>>> ''.join(soup.findAll(text=True))
u'September 29, 2009 2200 UTC\nLocation: 14.817N 52W\nWind Direction: NE (50&#176;)\nWind Speed: 7.8 knots\nAtmospheric Pressure: 29.94 in (1014.0 mb)\nAir Temperature: 82.9&#176;F (28.3&#176;C)\nDew Point: 73.9&#176;F (23.3&#176;C)\nWater Temperature: 84.6&>>> for k in doc.keys():
...     if k == 'entries':
...             dict = doc[k][0]
...
>>> soup = BeautifulSoup.BeautifulSoup(dict['summary_detail']['value'])
>>> ''.join(soup.findAll(text=True))
u'September 29, 2009 2200 UTC\nLocation: 14.817N 52W\nWind Direction: NE (50&#176;)\nWind Speed: 7.8 knots\nAtmospheric Pressure: 29.94 in (1014.0 mb)\nAir Temperature: 82.9&#176;F (28.3&#176;C)\nDew Point: 73.9&#176;F (23.3&#176;C)\nWater Temperature: 84.6&#176;F (29.2&#176;C)'


```


Ok -- that is still UGLY ... but at least the html tags are gone.

Unfortunately, you still have to deal with the html entities -- but that's easy with Python's htmlentitydefs ... or you can just roll your own dictionary of html entities to ascii or latin-1 characters:

```

entityMap = { '&#176' : ' degrees ' }

```

Or ... looking at this html -- it's pretty basic.

Try a regex:

```

>>> strip_html = re.compile(r'<strong>(.*)</strong>(.*)<br />', re.M)

```

Then you can one of BeautifulSoups iterators to create a dict:

```

>>> for l in soup.extract():
...     print ''.join(l)

```

...


ok --- I'm too tired to get this all done ... but those are some ideas that, I hope, are helpful.

hth

---

### Post by Reiger on 2009-09-30
How about looking at your actual source data?
```

<?xml-stylesheet type="text/xsl" href="/rss/ndbcrss.xsl"?>

```

[Now, what could that possibly be?]("http://www.ndbc.noaa.gov/rss/ndbcrss.xsl")

---

