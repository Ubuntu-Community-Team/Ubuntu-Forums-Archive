---
title: "Is there any program or library that lets you send POST request to http servers?"
date: 2008-01-31
forum: Programming Talk
---

### Post by Fixman on 2008-01-31
Yes, there it is, but could any of you say some?

---

### Post by LaRoza on 2008-01-31
[http://docs.python.org/lib/module-urllib.html](http://docs.python.org/lib/module-urllib.html)

[http://docs.python.org/lib/module-urllib2.html](http://docs.python.org/lib/module-urllib2.html)

Python is good for this. It has good standard libraries for networking and the web.

[http://docs.python.org/lib/internet.html](http://docs.python.org/lib/internet.html)

---

### Post by lnostdal on 2008-01-31
yeah, i use [http://weitz.de/drakma/](http://weitz.de/drakma/) and it's great

---

### Post by LaRoza on 2008-01-31
@OP You are going to get answers that reflect what language **we** use. Do you have a specific language in mind?

---

### Post by ThinkBuntu on 2008-01-31
Is the poster just asking about POST request? If so, PHP's superglobal ($_POST[]) array would work fine. Use it for webforms all the time.

---

### Post by a9bejo on 2008-01-31
You can also use the program curl to send POST requests from the command line like  this:

```

kafka% curl http://tagthe.net/api -d 'text=Ubuntu is sponsored by Canonical Ltd, owned by South African entrepreneur Mark Shuttleworth. The name of the distribution comes from the southern African concept of ubuntu which may be rendered roughly as "humanity toward others", "we are people because of other people", or "I am who I am because of who we all are", though other meanings have been suggested.'

```


In Ruby, the easiest way I know is the rest-open-uri library:

[php]
require 'rest-open-uri'
open('http://tagthe.net/api',:method=> :post, :body => "text=Ubuntu is sponsored by...").read
[/php]

---

### Post by lnostdal on 2008-02-01
> **ThinkBuntu said:**
> Is the poster just asking about POST request? If so, PHP's superglobal ($_POST[]) array would work fine. Use it for webforms all the time.

no, he means initiating a HTTP POST request, from a clients point of view .. like a web browser

---

### Post by Fixman on 2008-02-02
Too late...I was thinking on C++, or a console program.

---

### Post by pmasiar on 2008-02-02
Why you need C++? It will no way be fast, it talks over http, so performance is least of your worries. Lot of pain for no real gain at all. Doing it in Python is 100 times simpler, python was designed to do this kind of tasks. See LaRoza's comments above.

---

### Post by a9bejo on 2008-02-03
> **Fixman said:**
> Too late...I was thinking on C++, or a console program.

the console program I mentioned above (curl) is only a wrapper around a C library called libcurl. This library has many bindings to different languages, including C++. See: [http://curl.haxx.se/libcurl/cplusplus/](http://curl.haxx.se/libcurl/cplusplus/). 

You can, of course,  also create the HTTP POST request manually and send it over a TCP socket to the server  port 80.  That is not really difficult - HTTP is pretty simple.

---

### Post by lnostdal on 2008-02-03
..and here are links to some to-the-point tutorials on doing this: 
[http://jmarshall.com/easy/http/](http://jmarshall.com/easy/http/)
[http://beej.us/guide/bgnet/](http://beej.us/guide/bgnet/)

---

