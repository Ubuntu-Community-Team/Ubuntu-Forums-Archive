---
title: "Getting Data From Webpage"
date: 2009-03-09
forum: Programming Talk
---

### Post by elbarto_87 on 2009-03-09
Hi,

I was hoping somebody here could point me in the right direction for writing scripts with python to get data off a web page.

For example, I would like to go to [http://www.goldencasket.com/results/latest.asp]("http://www.goldencasket.com/results/latest.asp") and download the latest lotto results (winning numbers) and print them to the command line.

Is this something simple to achieve or is the process more envolved then I think? I have had nil experience with web pages up to this point so I am trying to start somewhere.

Regards Elbarto

---

### Post by ghostdog74 on 2009-03-09
you can use ready available programs such as wget or lynx to get your web pages. Look up their documentation to see how to use them.
you can also use programming languages, such as Python or Perl/PHP (or others with web modules), that comes with ready web modules for getting web pages.

---

### Post by elbarto_87 on 2009-03-09
Thank You for the reply. Could you recommend a good place to start looking for python examples, I am doing a class which requires us to do an assignment soon and was thinking of trying to integrate something like that for a program idea.

Thanks for the wget suggestion also, I will look into that now.

Elbarto

---

### Post by elbarto_87 on 2009-03-09
I remembered seeing this command used for the 99 bottles of beer song and thought it was pretty crazy at the time:

wget -q -O - [http://99-bottles-of-beer.net/lyrics.html](http://99-bottles-of-beer.net/lyrics.html) | awk '/<p>/{gsub("<br>","\n");gsub(" *<[^>]+>","");print}' 

Haha turns out you were the author, thats pretty impressive. Where did you learn to write something like that???

---

### Post by ghostdog74 on 2009-03-09
please take a look at my sig for Python link, as well as awk.

---

### Post by cabalas on 2009-03-09
If you are wanting to write it in python you should have a look at the [python bindings of curl]("http://pycurl.sourceforge.net/") or at the python module [urllib]("http://docs.python.org/library/urllib.html") both handle the fetching of data located at a URL

---

### Post by elbarto_87 on 2009-03-09
Thank you all for the links. I am having a read through all the info now.

Does anybody have a "small" program that they have written in the past that is similar to what I am trying to achieve. I have not been able to find a decent example on the net just yet.

Thanks,

Elbarto

---

### Post by myrtle1908 on 2009-03-09
You are probably also going to have to parse some HTML if you want to retrieve the lotto numbers.  For this I recommend BeautifulSoup.

[http://www.crummy.com/software/BeautifulSoup/documentation.html](http://www.crummy.com/software/BeautifulSoup/documentation.html)

There's an example on the page above which does something similar to what you want:-

"Here's a real-world example. It fetches the ICC Commercial Crime Services weekly piracy report, parses it with Beautiful Soup, and pulls out the piracy incidents:"

[PHP]
import urllib2
from BeautifulSoup import BeautifulSoup

page = urllib2.urlopen("http://www.icc-ccs.org/prc/piracyreport.php")
soup = BeautifulSoup(page)
for incident in soup('td', width="90%"):
    where, linebreak, what = incident.contents[:3]
    print where.strip()
    print what.strip()
    print[/PHP]

---

### Post by unutbu on 2009-03-09
```
sudo apt-get install python-beautifulsoup

```
[PHP]#!/usr/bin/env python
import urllib
from BeautifulSoup import BeautifulSoup
contents=urllib.urlopen('http://www.goldencasket.com/results/latest.asp').read()
soup=BeautifulSoup(contents)
wn=soup.findAll('span',attrs={'class':'winning_numbers'})
for tag in wn:
    num=tag.find(text=True)
    print num
[/PHP]

Output:
```


2
6
12
34
39
41


3
8
11
26
29
33
35


1
5
14
25
27
38
10
18
19
22
36


6
10
12
17
26
34
5
2
0
1
2
4
484413653
E, Ormeau
```
The output clearly needs some work, but hopefully this points you in a right direction.

In order to improve on the above code snippet, I believe the place to start would be reading [this guide on how to use BeautifulSoup]("http://www.crummy.com/software/BeautifulSoup/documentation.html").

---

### Post by Wybiral on 2009-03-09
I agree with the urllib + beautifulsoup solution... It's the Python way

---

### Post by elbarto_87 on 2009-03-09
Thanks! That is pretty much what I am looking for so I will go with BeautifulSoup and see what I can learn.

Thanks Again,

Elbarto

---

