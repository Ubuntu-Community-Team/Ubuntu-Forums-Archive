---
title: "Filling in web forms using a Python bot"
date: 2008-06-10
forum: Programming Talk
---

### Post by -grubby on 2008-06-10
I'm interested in bots, and I'm trying to make one that connects to a website and fills in forms. I'm using a [manual on urllib2](http://www.voidspace.org.uk/python/articles/urllib2.shtml), but it doesn't seem to be working out. My source code is as follows:

[php]
import urllib
import urllib2

url = 'http://grubbn.com/fluxbb/post.php?tid=180'

user_agent = 'Mozilla/4.0 (compatible; MSIE 5.5; Windows NT)'

values = {
# req_username, req_email, req_message
# Guest name:, Guest e-mail:, Write message:
'req_username' : 'Grubbot',
'req_email' : 'nathangrubb@grubbn.com',
'req_message' : 'this is a test message from a bot'
 }
headers = { 'User-Agent' : user_agent }

data = urllib.urlencode(values)
req = urllib2.Request(url, data)
response = urllib2.urlopen(req)
the_page = response.read()
[/php]

---

### Post by fred.reichbier on 2008-06-10
It works for me on [http://www.rentbayarea.com/post_test.php](http://www.rentbayarea.com/post_test.php). Maybe you have forgot a hidden field or something?

---

### Post by -grubby on 2008-06-11
Still to no avail. I'm not sure I'm getting the fields right, though. What part of the HTML markup is supposed to be the name of the form in this?

---

### Post by Wybiral on 2008-06-11
> **nathangrubb said:**
> Still to no avail. I'm not sure I'm getting the fields right, though. What part of the HTML markup is supposed to be the name of the form in this?

I don't have time to dive too deeply into the markup, but I see, at least:
```

<input type="hidden" name="form_sent" value="1" />
<input type="hidden" name="form_user" value="Guest" />

```

---

### Post by -grubby on 2008-06-11
I'm pretty sure that it's either the name or value attribute. I'll try both and tell you how it goes

[color=red]***Edit:***[/color] Maybe I'm not so sure..those are hidden input items and they don't even include enough for all 3 input areas. I'll just delvage into the source code and see what I can find

---

### Post by -grubby on 2008-06-11
Ok, well I tried some different methods:
[php]
import urllib
import urllib2

url = 'http://grubbn.com/fluxbb/post.php?tid=180'

values = {
# req_username, req_email, req_message
# Guest name:, Guest e-mail:, Write message:
# form_sent, forum_user
# Guest, 1
'Guest name:' : 'Grubbot',
'Guest e-mail:' : 'nathangrubb@grubbn.com',
'Write message:' : 'this is a test message from a bot'
 }

data = urllib.urlencode(values)
resp = urllib2.urlopen(url, data)
response = urllib2.urlopen(resp)
response.read
[/php]

which resulted in the following python output:
```

  File "bot.py", line 18, in <module>
    response = urllib2.urlopen(resp)
  File "/usr/lib/python2.5/urllib2.py", line 124, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 373, in open
    protocol = req.get_type()
AttributeError: addinfourl instance has no attribute 'get_type'

```

Any ideas?

---

### Post by Can+~ on 2008-06-11
```

  File "bot.py", line 18, in <module>
    response = urllib2.urlopen(resp)
  File "/usr/lib/python2.5/urllib2.py", line 124, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 373, in open
    protocol = req.get_type()
AttributeError: addinfourl instance has no attribute 'get_type'

```

Try with:

[PHP]import urllib
import urllib2

url = 'http://grubbn.com/fluxbb/post.php?tid=180'

values = {
# req_username, req_email, req_message
# Guest name:, Guest e-mail:, Write message:
# form_sent, forum_user
# Guest, 1
'req_username' : 'Grubbot',
'req_email' : 'nathangrubb@grubbn.com',
'req_message' : 'this is a test message from a bot'
 }

data = urllib.urlencode(values)
resp = urllib2.urlopen(url, data)

print resp.read()[/PHP]

It posted back the same page.

---

### Post by -grubby on 2008-06-11
Indeed, it posted back the source code. But how does this help me?

---

### Post by -grubby on 2008-06-16
I'm going to bump this, I still haven't figured it out

---

### Post by skeeterbug on 2008-06-16
> **nathangrubb said:**
> I'm going to bump this, I still haven't figured it out


<div class="main-content message">
		<p>You do not have permission to access this page.</p>
</div>

*EDIT*
I guess I will elaborate. First you need to login, urlib2 has support for cookies, so logging in first, then doing the rest should work fine.

---

### Post by -grubby on 2008-06-16
Erm, sorry about any confusion, my forum settings used to let guests posts, when I was testing this bot, now they don't, I forgot about that. Thanks for the alert. I'll make it so guests can post

---

