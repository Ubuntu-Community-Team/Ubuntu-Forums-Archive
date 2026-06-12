---
title: "XML Newbie (youtube api) from Bash"
date: 2013-05-09
forum: Programming Talk
---

### Post by Valpskott on 2013-05-09
So, as the title suggests, I have no experience in XML.
However, I do need a reliable way to get data via the youtube api's. I've tried grep/sed-ing the shizzle out of it, thought I got it to work, but when I tried to get data from a youtube-channel with the new layout, my grep/sed combos failed on some of the data.

I have a PHP script that handles the youtube-api just fine, but I really need to do all of this from within bash (preferably without running a webserver).

I'm not sure, but, I think I need to "parse XML", I have no idea where to begin, I don't know how XML works nor what "parsing" is (some kind of formatting?). I tried google but the examples I found where either for people already familiar with this or implementation in java or php.

It would be much appreciated if someone could point me to something like a "XML for dummies"-guide.

Or if any Youtube-API-ninja reads this, how do I get the following info from a youtube-channel:
Subscriber Count, Total Channel Views, Latest Video(title + url + thumbnail).

---

### Post by Vaphell on 2013-05-09
parsing is a process of getting the logical structure of the document according to the rules of its language, "understanding what it says" in plain english. To extract relevant data you need to know where to find it, so you need to know the structure, right? There are xml parsers available that make it easy.
Parsing is the proper way to do such things, but sometimes if the document is predictable and has a simple structure you can hack it with text processing tools like grep, sed or awk, completely ignoring the grammar, though it is a viable approach only in the simpliest of cases.

So what do you have in that xml and what do you want to get from it?

---

### Post by epicoder on 2013-05-09
Google has some documentation on their API which you can get here: [https://developers.google.com/youtube/2.0/developers_guide_protocol_profiles#Retrieving_a_profile](https://developers.google.com/youtube/2.0/developers_guide_protocol_profiles#Retrieving_a_profile)
As for parsing XML, it would probably be better to write a small program to do so for you. Python would be good for this, as it has a simple parser with DOM built in. [http://docs.python.org/2/library/xml.html](http://docs.python.org/2/library/xml.html)

---

### Post by Valpskott on 2013-05-09
> **Vaphell said:**
> 
So what do you have in that xml and what do you want to get from it?

Instead of my own confused speculations on what needs to be done (xml parsing and what not), let me restate what I want, and you can work from there.

I want to be able to pull data such as latest Video Titles, Video URLs and Video Thumb Nails, as well as amount of subscribers and amount of total views, from any youtube account.

My bash script for collecting this (sometimes failing) looks like this:
```

#!/bin/bash

antal="$1"
ytname="$3"
fil1="/home/myusername/SCRIPTS/players/$ytname.stats"
fil2="/home/myusername/SCRIPTS/players/$ytname.video"

if [ -e "$fil1" ]; then
        rm $fil1
fi
if [ -e "$fil2" ]; then
        rm $fil2
fi

curl -s "https://gdata.youtube.com/feeds/api/users/$ytname" > $fil1
curl -s "http://gdata.youtube.com/feeds/api/users/$ytname/uploads?max-results=$antal" > $fil2

title=$(grep "categories.cat" $fil2 | grep "title type" | sed -e 's/.*categories.cat//g' | sed -e "s/.*.title type=.text..//g" | sed -e "s/..title.*//g" | head -n $antal | tail -n 1)
urlid=$(grep "categories.cat" $fil2 | grep "title type" | sed -e 's/.*gdata.youtube.com.feeds.api.videos.//g' | sed -e 's/<.id>.*//g' | head -n $antal | tail -n 1)
url=$(echo "http://www.youtube.com/watch?v=$urlid")
bild="http://i2.ytimg.com/vi/$urlid/mqdefault.jpg"
sub=$(grep "berCou" $fil1 | sed -e "s/.*berCount='//g" | sed -e "s/' videoWat.*//g" )
views=$(grep "berCou" $fil1 | sed -e "s/.*viewCount='//g" | sed -e "s/' total.*//g" )

echo "=== $ytname ==="
echo "Subs = $sub"
echo "Views = $views"
echo "URL-id: $urlid"
echo "URL: $url"
echo "Bild: $bild"
echo "Title: $title"

rm $fil1
rm $fil2

```

---

### Post by Vaphell on 2013-05-09
these files are indeed quite hardcore to parse by hand. Try something like this:

```
#!/usr/bin/env python

import sys
import urllib2
import xml.etree.ElementTree as ET

# param1 = user, param2 = result count
url = 'https://gdata.youtube.com/feeds/api/users/{0}/uploads?max-results={1}'.format( sys.argv[1], sys.argv[2] )

req = urllib2.Request( url )
f = urllib2.urlopen( req )
xmlroot = ET.fromstring( f.read() )

for entry in ( x for x in xmlroot if x.tag.endswith( '}entry' ) ):   # entry tags are about clips
  for elem in entry:
    tag = elem.tag.split('}')[-1]
    if tag=='link' and elem.get('rel')=='self':  
      print 'video_id: '+elem.get('href').split('/')[-1]
    elif tag=='title':
      print 'title: '+elem.text
    elif tag=='statistics':
      print 'view count: '+elem.get('viewCount' )
  print


```

in action:
```
$ ./yt.py IGNEntertainment 3
title: IGN News - Activision Has No Debt, $4.6 Billion in Cash
video_id: GwbnUwQ_A50
view count: 10525

title: Injustice: Gods Among Us - Lobo Combos 1
video_id: 1k8N8bVYVD4
view count: 9741

title: GTA V Screenshots, Stars Wars/Battlefield/FIFA Updates, & Avengers 2 Woes - IGN Daily Fix 05.08.13
video_id: j_iSJ1KSrbU
view count: 21480

```

i used this to parse the xml
[http://docs.python.org/2/library/xml.etree.elementtree.html](http://docs.python.org/2/library/xml.etree.elementtree.html)

---

