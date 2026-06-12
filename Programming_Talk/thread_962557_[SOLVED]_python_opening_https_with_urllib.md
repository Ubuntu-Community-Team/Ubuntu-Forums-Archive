---
title: "[SOLVED] python opening https with urllib"
date: 2008-10-29
forum: Programming Talk
---

### Post by troutbum13 on 2008-10-29
I have a script that I wrote to consolidate rss feeds of television shows from multiple sites. I use urllib and elementTree to parse the xml. I now want to add a "feed" from my tivo, which has an xml file of stored shows.

typically I would just use:
```

import urllib ElementTree as ET
feed_url = urllib.urlopen('http://MyRssFeed')
tv_tree = ET.parse(feed_url)
tv_root = tv_tree.getroot()
tv_iter = tv_root.getiterator('SomeElement')
...

```

My problem is that the tivo XML file is through an https connection...when I try the above with
 [https://192.168.0.xxx//TiVoConnect?Command=QueryContainer&Container=%2FNowPlaying&Recurse=Yes](https://192.168.0.xxx//TiVoConnect?Command=QueryContainer&Container=%2FNowPlaying&Recurse=Yes) 
it throws
```

Traceback (most recent call last):
  File "./tivo.py", line 30, in <module>
    feed_url = urllib.urlopen('https://192.168.0.xxx')
  File "/usr/lib/python2.5/urllib.py", line 82, in urlopen
    return opener.open(url)
  File "/usr/lib/python2.5/urllib.py", line 190, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.5/urllib.py", line 391, in open_https
    if not host: raise IOError, ('https error', 'no host given')
IOError: [Errno https error] no host given

```

Can someone point me in the right direction? As you can tell I am new at this :D

---

### Post by ghostdog74 on 2008-10-29
what is xxx?? make sure its an actual ip number. Also, you are using the wrong library. use urllib2. See the documentation for examples on how to use urllib2 together with https

---

### Post by troutbum13 on 2008-10-29
yes I am using a real IP, and the errors are the same with either urllib or urllib2

---

### Post by wmcbrine on 2008-10-29
To open a connection to the TiVo, you need something like this:

```
def open_tivo(address, mak):
    "Open the Now Playing page at 'address', with Media Access Key 'mak'"
    import urllib2
    url = 'https://%s/TiVoConnect?Command=QueryContainer&Container=/NowPlaying&R
ecurse=Yes'
    pm = urllib2.HTTPDigestAuthHandler()
    pm.add_password('TiVo DVR', address, 'tivo', mak)
    opener = urllib2.build_opener(pm)
    return opener.open(url % address)
```

Alternatively (the way I did it originally):

```
def open_tivo(address, mak):
    "Open the Now Playing page at 'address', with Media Access Key 'mak'"
    import urllib2
    url = 'https://%s/TiVoConnect?Command=QueryContainer&Container=/NowPlaying&R
ecurse=Yes'
    pm = urllib2.HTTPPasswordMgrWithDefaultRealm()
    pm.add_password(None, address, 'tivo', mak)
    opener = urllib2.build_opener(urllib2.HTTPDigestAuthHandler(pm))
    return opener.open(url % address)
```

---

### Post by curvedinfinity on 2008-10-29
Heya, here's how I did it:

```

params = urllib.urlencode({"Command":"QueryContainer",
                    "Container":"/NowPlaying",
                    "Recurse":"Yes"})
r = urllib2.Request("https://192.168.0.xxx/TiVoConnect",params)
f = urllib2.build_opener().open(r)
response = f.read()

```

Make sure openssl is installed. Also, its secure to show your subnet IP. Its behind a NAT, so its not like anyone can get to it without first compromising your router, which we don't know the IP of.

---

### Post by wmcbrine on 2008-11-01
curvedinfinity, that doesn't work. You have to give it the password (the MAK) somehow. Your code just gives a 401 error on the "open" line.

---

### Post by troutbum13 on 2008-12-08
sorry it took me awhile to post again....

Thanks for the example wmcbrine...here is the code I got to work
```

import urllib2, ElementTree as et

def parseTivo(address, mak):
			url = 'https://%s/TiVoConnect?Command=QueryContainer&Container=/NowPlaying&Recurse=Yes'
			pm = urllib2.HTTPDigestAuthHandler()
			pm.add_password('TiVo DVR', address, 'tivo', mak)
			opener = urllib2.build_opener(pm)
			nowPlaying=opener.open(url % address)
			tivo_tree = et.parse(nowPlaying)
			tivo_root = tivo_tree.getroot()
			tivoBit = '{http://www.tivo.com/developer/calypso-protocol-1.6/}'
			t_iter = tivo_root.getiterator(tivoBit + 'Item')
			for line in  t_iter:
				seriesName = line.findtext(tivoBit+'Details/'+ tivoBit + 'Title')
				episodeName = line.findtext(tivoBit + 'Details/'+ tivoBit + 'EpisodeTitle')
				tivoLink = line.findtext(tivoBit + 'Links/'+ tivoBit +'Content/'+ tivoBit + 'Url')
				tivoHD = line.findtext(tivoBit + 'Details/'+ tivoBit + 'HighDefinition')
				TivoDL(address, mak, tivoLink)

```

I am now pretty stuck with with downloading the actual .tivo files...
I keep getting 401: auth errors...

here is the code I have that is not working....
```

def TivoDL(address, mak, link):
	pm = urllib2.HTTPDigestAuthHandler()
	pm.add_password('TiVo DVR', address, 'tivo', mak)
	opener = urllib2.build_opener(pm)
	download=opener.open(link)
	f=open(some_path, "w")
	f.write(download)
	f.close()

```

anyway thanks for your help, and if anyone sees what I am doing wrong on the .tivo file I would love to know...;) trying to teach myself as I go.

---

### Post by wmcbrine on 2008-12-09
You're just passing a (pseudo-)file handle to f.write(). There are certain contexts where that kind of thing works in Python, but this isn't one of them -- you'd need something like "f.write(download.read())" instead. But that's no good, either, since I think it would read in the whole file before writing it out, and these files are huge. What you want is probably something like:

```
import shutil

shutil.copyfileobj(download, f)
```

Also, I'd open that file in "wb" mode.

---

### Post by troutbum13 on 2008-12-09
> **wmcbrine said:**
> You're just passing a (pseudo-)file handle to f.write(). There are certain contexts where that kind of thing works in Python, but this isn't one of them.

Thanks, I am sure that is the case and I'll look into using shutil, but the line that is throwing errors is bolded below, so I have not been able to get that far...

```

def TivoDL(address, mak, link):
	pm = urllib2.HTTPDigestAuthHandler()
	pm.add_password('TiVo DVR', address, 'tivo', mak)
	opener = urllib2.build_opener(pm)
	**download=opener.open(link)**
	f=open(some_path, "w")
	f.write(download)
	f.close()

```


here is the output...
```

Traceback (most recent call last):
  File "testing.py", line 33, in <module>
    if __name__ == '__main__': TivoDL('192.168.0.16', '123456789', 'http://192.168.0.16:80/download/Nature.TiVo?Container=%2FNowPlaying&id=1224369')
  File "testing.py", line 28, in TivoDL
    download=opener.open(link)
  File "/usr/lib/python2.5/urllib2.py", line 387, in open
    response = meth(req, response)
  File "/usr/lib/python2.5/urllib2.py", line 498, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.5/urllib2.py", line 425, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.5/urllib2.py", line 360, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.5/urllib2.py", line 506, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 401: Authorization Required


```
Like I said I am trying to teach myself as I go, but the urllib2 docs aren't exactly descriptive... I am going to make some time to look around and see if someone hasn't already cooked up a tivo module somewhere...:)

---

### Post by troutbum13 on 2008-12-19
just to close this out...two things were causing problems, the link that I was extracting from the xml, included the port ([http://192.168.0.100:80/](http://192.168.0.100:80/)...) for some reason this caused problems...also after looking at the headers when you query the tivo for the XML, it uses digest auth, but when you try to download the actual binaries, it uses digest auth and sends a cookie. Anyway here is how I got it working.

```

import os
import shutil
import cookielib
import urllib2
COOKIE_FILE = 'path/to/file/cookies.lwp'
def getTivo(link, mak):
		link = link.replace(':80', '')
		cj = cookielib.LWPCookieJar()
		if os.path.isfile(COOKIE_FILE):
			cj.load(COOKIE_FILE)
		authhandler = urllib2.HTTPDigestAuthHandler()
		authhandler.add_password('TiVo DVR', link, 'tivo', mak)
		cookiehandler=urllib2.HTTPCookieProcessor(cj)
		opener = urllib2.build_opener(authhandler, cookiehandler)
		urllib2.install_opener(opener)
		try:
			req = urllib2.Request(link)      
			handle = urllib2.urlopen(req)                              
		except IOError, e:
			if hasattr(e, 'code'):
				print 'Error code - %s.' % e.code
			elif hasattr(e, 'reason'):
				print "Error object reason:", e.reason
				sys.exit()
				
		else:

			dlpath = os.path.join('path/to/write/file', '.tivo')
			dl = open(dlpath, "wb")
			shutil.copyfileobj(handle, dl)
			dl.close()
			missing.link = link
			cj.save(COOKIE_FILE)


```

---

### Post by pippo79 on 2009-04-25
Dear all,


I have read the VERY INTERESTING post regarding opening HTTPS links with urlib. 
Since I have noticed that you are a really very experienced Python developers I would like to kindly as you a quick information regarding an issue that I do have with Python.

I would like to access automatically (and download) from my google finance portfolio the following link (web page):

[https://www.google.com/accounts/ServiceLogin?hl=en&service=finance&nui=1&continue=http%3A%2F%2Fwww.google.com%2Ffinance](https://www.google.com/accounts/ServiceLogin?hl=en&service=finance&nui=1&continue=http%3A%2F%2Fwww.google.com%2Ffinance)


I tryed a million of solutions but I am getting crazy and I am not able to:

- automatic login with python
- download of the above link with python 


How could I modify your code above in order to do the same thing with Google Finance ?
Could you please help me to perform this operation ? I'm really getting crazy with this stuff...I never had any problem with automatic download, but with a HTTPS I'm not able to find a solution.


Thank you very much !

Pippo

---

