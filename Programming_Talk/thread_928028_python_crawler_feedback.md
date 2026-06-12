---
title: "python crawler feedback"
date: 2008-09-23
forum: Programming Talk
---

### Post by mutenewt on 2008-09-23
I'm in the process of learning python.  For context, I'm still clueless when it comes to OOP.  At the moment, I'm focused writing code that interacts with the web (playing with urllib, urllib2, urlparse, beautifulsoup, etc).  

My latest project is a simple webcrawler.  Currently, it works exactly as intended.  It takes two inputs - starter site and number of trips.  It searches the starter site for URLs, prints the results, randomly picks a link and moves on - taking as many "trips" as indicated.

I have already identified two problems: (1) the crawler can get trapped inside a site and (2) sometimes I run into a dead-end (jpg files, etc).

I have ideas on how to address these problems but any input would be appreciated.  More generally, I'm looking for feedback on the current code.  I'd really like to get it as "clean" as possible before moving on.  Is there a better approach?

Thanks for the help!

```
#!/usr/bin/env python

# import modules
import urllib
import urlparse
import BeautifulSoup
import random

starter_site = "http://www.techmeme.com/"
trips = 10

def urlcollector(site,trips):
	# need to add error detection for deadends such as jpg files, RSS feeds, etc.
	# could limit to top level domains, would prevent getting trapped within a site
	new_site = site
	while trips > 0:
		page = urllib.urlopen(new_site)
		page_soup = BeautifulSoup.BeautifulSoup(page)
		seen = []
		for anchor in page_soup.fetch('a'):
			url = anchor.get('href')
			if url is None or url in seen:
				continue
			pieces = urlparse.urlparse(url)
			if pieces[0]=='http':
				link = urlparse.urlunparse(pieces)
				seen.append(link)
				print link				
		print ""
		new_site = random.choice(seen)
		print "my next starting point is: " + new_site
		print ""
		trips = trips - 1

def intro():
	print ""
	print "starting with the following url: " + starter_site
	print ""

def finished():
	print ""
	print "whew, I'm tired"
	print ""

def run():
	intro()
	urlcollector(starter_site,trips)
	finished()
		
if __name__ == "__main__":
	run()
```

---

### Post by LaRoza on 2008-09-23
[http://docs.python.org/tut/node10.html](http://docs.python.org/tut/node10.html)

For errors, this is a good time for learning exception handling.

---

### Post by artir on 2008-09-23
You can insert some checking before the crawler goes into a page.
url= [http://lolwut.images.es/pics/image.jpg](http://lolwut.images.es/pics/image.jpg)
convert that string into small trings using "/" as a divider

http:  lolwut.imags.es pics image.jpg
pick the url[-1] item

image.jpg

split again using .
image jpg
if url[-1] is jpg or jpeg or whatever:
 print "WHOOPS!"
else:
 keep executing the code ;P

---

### Post by mutenewt on 2008-09-23
quickly read the [http://docs.python.org/tut/node10.html]("http://docs.python.org/tut/node10.html") and modified the code a bit.  Not a long-term solution but a start.  Thx LaRoza

```
#!/usr/bin/env python

# import modules
import urllib
import urlparse
import BeautifulSoup
import random

starter_site = "http://www.techmeme.com/"
trips = 10

def urlcollector(site,trips):
	# need to add error detection for deadends such as jpg files, RSS feeds, etc.
	# could limit to top level domains, would prevent getting trapped within a site
	new_site = site
	try:
		while trips > 0:
			page = urllib.urlopen(new_site)
			page_soup = BeautifulSoup.BeautifulSoup(page)
			seen = []
			for anchor in page_soup.fetch('a'):
				url = anchor.get('href')
				if url is None or url in seen:
					continue
				pieces = urlparse.urlparse(url)
				if pieces[0]=='http':
					link = urlparse.urlunparse(pieces)
					seen.append(link)
					print link				
			print ""
			new_site = random.choice(seen)
			print "my next starting point is: " + new_site
			print ""
			trips = trips - 1
	except:
		print "sorry, I have encountered an error and cannot continue.  This usually happens when I ecounter a dead-end."
		
def intro():
	print ""
	print "starting with the following url: " + starter_site
	print ""

def finished():
	print ""
	print "whew, I'm tired"
	print ""

def run():
	intro()
	urlcollector(starter_site,trips)
	finished()
		
if __name__ == "__main__":
	run()
```

---

### Post by unutbu on 2008-09-23
Here is a slightly modified version which can escape dead ends:
[PHP]
#!/usr/bin/env python
__author__="mutenewt"
__source__="http://ubuntuforums.org/showpost.php?p=5842500&postcount=1"

import urllib
import urlparse
import BeautifulSoup
import random

starter_site = "http://www.techmeme.com/"
trips = 10

def urlcollector(site,trips):
    # need to add error detection for deadends such as jpg files, RSS feeds, etc.
    # could limit to top level domains, would prevent getting trapped within a site
    new_site = site
    links_visited={}
    while trips > 0:
        page = urllib.urlopen(new_site)
        page_soup = BeautifulSoup.BeautifulSoup(page)
        seen = []
        for anchor in page_soup.fetch('a'):
            url = anchor.get('href')
            if url is None or url in seen:
                continue
            pieces = urlparse.urlparse(url)
            if pieces[0]=='http':
                link = urlparse.urlunparse(pieces)
                seen.append(link)
                links_visited[link]=False
                print link                              
        print
        try:
            new_site = random.choice(
                [link for link in seen if not links_visited[link]])
            links_visited[new_site]=True
        except IndexError:
            print "Escaping deadend: Whee"
            try:
                new_site = random.choice(
                    [link for link in links_visited.keys() 
                     if not links_visited[link]])
                links_visited[new_site]=True
            except IndexError:
                print ("We've exhausted all links found. "+
                       "Hm... Better check if the internet is working :)")
                break
        print "my next starting point is: " + new_site
        print
        trips = trips - 1

def intro():
    print
    print "starting with the following url: " + starter_site
    print

def finished():
    print
    print "whew, I'm tired"
    print

def run():
    intro()
    urlcollector(starter_site,trips)
    finished()
                
if __name__ == "__main__":
    run()
[/PHP]

---

### Post by pmasiar on 2008-09-24
You need to read up on data structures and algorithms. This is trivial tree walker (visit all leaves), solved 40 or 50 years ago.

---

### Post by mutenewt on 2008-09-24
Thx artir and unutbu!  I'll play with this later today/tomorrow.  pmasiar I appreciate the feedback but I'm just a newb trying to learn programming/python, not trying to write an amazing crawler.  This is my first successful effort with writing code that interacts with the web.  I'm much more concerned with - if my code structure looks ok, if I'm using the modules correctly, etc - just the basics. On a related note, I have found your website and LaRoza's very helpful in this regard.  Thank you!!

---

