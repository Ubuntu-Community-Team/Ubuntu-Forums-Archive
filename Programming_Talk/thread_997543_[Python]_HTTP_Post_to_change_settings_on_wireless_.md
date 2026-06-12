---
title: "[Python] HTTP Post to change settings on wireless router?"
date: 2008-11-29
forum: Programming Talk
---

### Post by OldGregory on 2008-11-29
I have a DD-WRT-eed Linksys wireless router and I would like to send an http POST to change settings on it, but something is going amiss.

After fiddling with urllib2, I was able to successfully request a page using basic authentication, but trying to post any data resulted in a "httplib.BadStatusLine" error. 

After some more googling, I came across this page: [http://www.russellbeattie.com/blog/is-this-a-canonical-python-http-post-with-basic-authentication](http://www.russellbeattie.com/blog/is-this-a-canonical-python-http-post-with-basic-authentication)
The author has almost the same problem I have, and he ended up using httplib2 after seeing a comment left on the blog, and it's no wonder: only three simple, no frills-attached lines of code are needed.

Anyway, here is what I am trying to do.  The get works. The post results in a httplib.BadStatusLine error, which means the router sent back a status line (like 200, 301, 401, 404, etc) that doesn't make any sense .[php]import urllib
import httplib2

http = httplib2.Http()
http.add_credentials( 'root', 'xxx' )
#result = http.request( 'http://192.168.1.1/Wireless_Basic.asp', 'GET' )
#result = http.request( 'http://192.168.1.1/Wireless_Basic.asp', 'POST', urllib.urlencode({ 'wl0_ssid':'lol' }) )

print result

exit()[/php]

So I'm pretty sure something is wrong with the data I'm trying to send, either it's not enough, or just wrong.  If you need to see the webpage source, just say so.

---

### Post by pp. on 2008-11-30
What we would need to see is the server's response. HTTP is just plain text, transmitted with TCP. Hence, it should not be all that difficult to read that string from TCP.

---

### Post by OldGregory on 2008-12-01
A netcat post resulted in no data returned at all.

I could figure this out pretty easily if I could see the http post firefox sends.  Does anyone know how I could do that?

---

### Post by OldGregory on 2008-12-02
Well, I just found this firefox script: [https://addons.mozilla.org/en-US/firefox/addon/1290](https://addons.mozilla.org/en-US/firefox/addon/1290)

It was exactly what I needed and all I needed to to was add the right data and now it works perfectly.

---

