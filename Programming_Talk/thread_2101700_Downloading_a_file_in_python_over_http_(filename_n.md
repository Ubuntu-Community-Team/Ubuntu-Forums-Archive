---
title: "Downloading a file in python over http (filename not known)"
date: 2013-01-05
forum: Programming Talk
---

### Post by 3v3rgr33n on 2013-01-05
Hi

I remember when I had to setup my wireless connection for the first time in ubuntu, it was hectic. I'm tryna get my friends to use ubuntu --- I also want to simplify their lives.

I can across this tutorial [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

I wanted to automate the task using python, perhaps also include a gui.

The problem however is that I have to download the latest stable version of ndiswrapper from here [http://sourceforge.net/projects/ndiswrapper/files/stable/](http://sourceforge.net/projects/ndiswrapper/files/stable/)

How do I download the latest file from that list?
I can't specify a file name as that will not give me the latest file.

---

### Post by ofnuts on 2013-01-05
> **3v3rgr33n said:**
> Hi

I remember when I had to setup my wireless connection for the first time in ubuntu, it was hectic. I'm tryna get my friends to use ubuntu --- I also want to simplify their lives.

I can across this tutorial [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

I wanted to automate the task using python, perhaps also include a gui.

The problem however is that I have to download the latest stable version of ndiswrapper from here [http://sourceforge.net/projects/ndiswrapper/files/stable/](http://sourceforge.net/projects/ndiswrapper/files/stable/)

How do I download the latest file from that list?
I can't specify a file name as that will not give me the latest file.
"http://sourceforge.net/projects/ndiswrapper/files/stable/" will contain the URLs to the files, so you can parse the page to retrieve these URLs (a regexp will likey be sufficient) and then you can parse these to find which corresponds to the latest version and then use it to download... but it will redirect you to a mirror... so things can get a bit complicated before you get the final download URL. Check the actual sequence with some took like LiveHTTPHeaders (firefox).

NDIS wrapper is GPLv2 so you can redistribute it freely, and nothing says future versions would be compatible with your script. 

But of course you could [have a look here ]("https://launchpad.net/ubuntu/+source/ndiswrapper")or wonder if the package isn't already in the standard Ubuntu repository :idea:
[ ]("https://launchpad.net/ubuntu/+source/ndiswrapper")

---

### Post by 3v3rgr33n on 2013-01-06
> **ofnuts said:**
> "http://sourceforge.net/projects/ndiswrapper/files/stable/" will contain the URLs to the files, so you can parse the page to retrieve these URLs (a regexp will likey be sufficient) and then you can parse these to find which corresponds to the latest version and then use it to download... but it will redirect you to a mirror... so things can get a bit complicated before you get the final download URL.


Do you mind giving me an example --- I'm not really a python guru.

---

### Post by ofnuts on 2013-01-06
> **3v3rgr33n said:**
> Do you mind giving me an example --- I'm not really a python guru.
```

urlPattern=re.compile('http://sourceforge.net/projects/ndiswrapper/files/stable/ndiswrapper-(\d+).(\d+).tar.gz/download')

latestUrl=''
latestVer=-1
latestRel=-1

with open(downloadsPage) as f:
    for line in f.readlines():
    match=urlPattern.search(line)
    if match:
        url=match.group(0)
        ver=int(match.group(1))
        rel=int(match.group(2))
        print url,ver,rel
        if ver>latestVer or (ver==latestVer and rel>latestRel):
            latestUrl=url
            latestVer=ver
            latestRel=rel
            
print "Best url: %s" % latestUrl

```

In practice the latest version is the first listed so you can exit the loop on the first match and use the simpler:

```

urlPattern=re.compile('http://sourceforge.net/projects/ndiswrapper/files/stable/ndiswrapper-\d+.\d+.tar.gz/download')

with open(downloadsPage) as f:
    for line in f.readlines():
    match=urlPattern.search(line)
    if match:
        latestUrl=match.group();
        break;
            
print "Best url: %s" % latestUrl

```

---

### Post by d347hm4n on 2013-01-08
I did it using the following python script. I'm still a begginer so constructive criticism is welcome.

```
import urllib2
import sre
import subprocess

address = 'http://sourceforge.net/projects/ndiswrapper/files/stable/'

try:     
    website = urllib2.urlopen(address) 
except urllib2.HTTPError, e:     
    print "Cannot retrieve URL: HTTP Error Code", e.code 
except urllib2.URLError, e:     
    print "Cannot retrieve URL: " + e.reason[1] 

matches = sre.findall('ndiswrapper-\d+.\d+.tar.gz', website.read()) 
print 'Latest Version: ' + matches[0]
value = -1
while value !='y':
    print 'Do you want to Download the latest version? y/n\r'
    value = raw_input()
    if(value == 'y'):
        subprocess.call(['wget', address + matches[0]])
        break
    elif(value == 'n'):
        break
```

d3

---

### Post by ofnuts on 2013-01-08
> **d347hm4n said:**
> I did it using the following python script. I'm still a begginer so constructive criticism is welcome.

```
import urllib2
import sre
import subprocess

address = 'http://sourceforge.net/projects/ndiswrapper/files/stable/'

try:     
    website = urllib2.urlopen(address) 
except urllib2.HTTPError, e:     
    print "Cannot retrieve URL: HTTP Error Code", e.code 
except urllib2.URLError, e:     
    print "Cannot retrieve URL: " + e.reason[1] 

matches = sre.findall('ndiswrapper-\d+.\d+.tar.gz', website.read()) 
print 'Latest Version: ' + matches[0]
value = -1
while value !='y':
    print 'Do you want to Download the latest version? y/n\r'
    value = raw_input()
    if(value == 'y'):
        subprocess.call(['wget', address + matches[0]])
        break
    elif(value == 'n'):
        break
```d3

- I would keep website.read() in the try/except block, it has about as many chances to fail as the urlopen() (network timeouts, etc....)
- "sre" is deprecated,  "re" should be used instead.
- I don't see much purpose in using findall() to only take the first one, better use re.search(pattern,flags)
- whether you use findall() or search(), since your pattern doesn't match a complete URL you won't be able to use the result for the download (and you cannot really tell if you are matching a URL or something else...)

---

### Post by 3v3rgr33n on 2013-01-08
> **ofnuts said:**
> ... In practice the latest version is the first listed so you can exit the loop on the first match and use the simpler:

```

urlPattern=re.compile('http://sourceforge.net/projects/ndiswrapper/files/stable/ndiswrapper-\d+.\d+.tar.gz/download')

with open(downloadsPage) as f:
    for line in f.readlines():
    match=urlPattern.search(line)
    if match:
        latestUrl=match.group();
        break;
            
print "Best url: %s" % latestUrl

``` 

I'm absolutely new to networking with python so forgive me. Can't you just simply read all the packages into a list and then pick the top one, assuming it will at position 0 in the list?

---

### Post by ofnuts on 2013-01-08
Yes you can, but if the page is a bit big it gets wasteful. Why parse the whole page when you can stop on the first hit? My code above is a simplification of the one I provided fr the very general case of unsorted URLs, but it can be even simpler:

```

urlPattern='http://sourceforge.net/projects/ndiswrapper/files/stable/ndiswrapper-\d+.\d+.tar.gz/download'

with open(downloadsPage) as f:
    wholePage=f.read()
    latestUrl=re.search(urlPattern,wholePage)

```or, with network retrieval:
```

import urllib2,re

downloadPage='http://sourceforge.net/projects/ndiswrapper/files/stable/'
downloadPattern='http://sourceforge.net/projects/ndiswrapper/files/stable/ndiswrapper-\d+.\d+.tar.gz/download'

try:     
    connection = urllib2.urlopen(downloadPage) 
    page=connection.read()
except urllib2.HTTPError, e:     
    print 'Cannot retrieve URL: HTTP Error %d' % e.code 
    exit(1)
except urllib2.URLError, e:     
    print 'Cannot retrieve URL: %s' % e.reason
    exit(1)

firstMatch=re.search(downloadPattern,page)
if firstMatch:            
    print 'Best download URL: %s' % firstMatch.group()
else:
    print 'No download URL found,  bad page URL?'

```

(note that on Sourceforge, you don't get a 404 error, but some other page up in the hierarchy)

---

