---
title: "[python] - automated login failed"
date: 2010-07-28
forum: Programming Talk
---

### Post by ApEkV2 on 2010-07-28
Hey there, I just started learning Python and am having difficulty getting my script to login to a website.
It completes fine, but the final page says I must be logged in to view it so I know it failed.
I don't know what I'm doing wrong. Any help would be appreciated.

```
#!/usr/bin/env python

import sys, urllib, urllib2, cookielib

def execute_mission():
	username = '**********'
	password = '**********'

	host = 'www.hackthissite.org'
	user_agent = 'Mozilla/4.0 (compatible; MSIE 6.0)'
	referer = 'http://www.hackthissite.org/user/login'
	content_type = 'application/x-www-form-urlencoded'
	accept_encoding = 'gzip,deflate'

	body = {'username' : username, 'password' : password}

	ckj = cookielib.CookieJar()
	values = {'Host': 'www.hackthissite.org',
		'User-Agent':'Mozilla/4.0 (compatible; MSIE 8.0)',
		'Referer':'http://www.hackthissite.org/user/login',
		'Content-Type':'application/x-www-form-urlencoded',
		'Accept-Encoding':'gzip,deflate',}
	
	try:
		opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(ckj))
		login_data = urllib.urlencode(body)
		request = urllib2.Request(referer, login_data, values)
		page1 = urllib2.urlopen(request)
	except urllib2.URLError, error:
		print 'Request failed, returned %d' % error
		return False
	finally:
		url = "http://www.hackthissite.org/missions/prog/11/"
		page2 = urllib2.urlopen(url)
		print page1.info(), "\n------------------\n", page2.read()
		return True

if __name__ == '__main__':
	retval = execute_mission()
	print 'mission returned %s' % retval
	sys.exit(not retval)
```
Here is the page1 info.
```
Server: Apache
Set-Cookie: PHPSESSID=* * *; path=/
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
Pragma: no-cache
Connection: close
Transfer-Encoding: chunked
Content-Type: text/html
```

---

### Post by ApEkV2 on 2010-07-30
Fixed the above problem by setting a referer. Now I have a new problem.
My login and the following page request works fine, I do the operation and send my answer to the website.
But it fails saying TypeError request() got an unexpected keyword argument 'data', except it's exactly the same as the other requests.
The error occurs on line 45. If anyone could help, also I'm using httplib2 now.
[php]#!/usr/bin/env python

import re, sys, urllib, httplib2

def isprime(n):
	if n == 2:
		return True
	if n < 2 or not n & 1:
		return False
	for x in range(3, int(n**0.5)+1, 2):
		if not n % x:
			return False
	return True

def perform_operation(nlist):
	inc = 0
	prmval = 0
	numval = 0
	for x in nlist:
		x = int(x)
		if isprime(x):
			prmval += x
		elif x > 2:
			numval += x
		inc += 1
	return (prmval * numval)
			
def execute_mission():
	url = 'http://www.hackthissite.org/user/login'
	body = {'username': '*****', 'password': '*****'}
	headers = {'Content-type': 'application/x-www-form-urlencoded',
		'Referer':'http://www.hackthissite.org/'}
	
	http = httplib2.Http()
	response, content = http.request(url,'POST',headers=headers,body=urllib.urlencode(body))
	headers['Cookie'] = response['set-cookie']
	url = 'http://www.hackthissite.org/missions/prog/12/'
	response, content = http.request(url, 'GET', headers=headers)
	
	string = re.findall("value=\"(.*)\"", content)
	string = re.findall("([0-9]*[0-9]+)", string[0])
	answer = perform_operation(string)
	
	data = {'solution': answer, 'submitbutton': 'Submit'}
	url = 'http://www.hackthissite.org/missions/prog/12/index.php'
#
	response, content = http.request(url,'POST',headers=headers,data=urllib.urlencode(data))
#
	print content, "\n------------------\n", response
	
	if response.status in [200, 301]:
		return True
	else:
		return False

if __name__ == '__main__':
	retval = execute_mission()
	print "\n------------------\n", 'Mission returned %s' % retval
	sys.exit(not retval)[/php]

---

### Post by StephenF on 2010-07-30
Well, data is not a valid keyword argument but body is. Interesting site by the way.

---

### Post by ApEkV2 on 2010-07-30
Thanks for the reply StephanF, I don't know why I didn't try using body first or at all.
I'll have to try that when I switch back over to Ubuntu.
(now I know about keyword arguments) a bit different than C

That site is interesting. I don't have this script finished for that particular mission though.

Edit: it works XD

---

