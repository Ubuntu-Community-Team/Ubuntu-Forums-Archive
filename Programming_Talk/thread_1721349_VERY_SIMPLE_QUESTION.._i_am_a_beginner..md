---
title: "VERY SIMPLE QUESTION.. i am a beginner."
date: 2011-04-04
forum: Programming Talk
---

### Post by kenny0128 on 2011-04-04
I just started learning python and twitter tool. 
at the very early stage of my trial, i happened to receive this error message.
I am not too sure why the requested page dose not exit.

Any suggestion, i will be so happy to hear.

>>> import twitter
>>> twitter_search = twitter.Twitter(domain="search.twitter.com")
>>> trends = twitter_search.trends()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/site-packages/twitter-1.6-py2.7.egg/twitter/api.py", line 150, in __call__
  File "/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/site-packages/twitter-1.6-py2.7.egg/twitter/api.py", line 165, in _handle_response
twitter.api.TwitterHTTPError: Twitter sent status 404 for URL: 1/trends.json using parameters: ()
details: <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">

<html>
	<head>
		<meta http-equiv="content-type" content="text/html; charset=UTF-8" />
		<title>The page you were looking for doesn't exist (404)</title>
		<style type="text/css">
			body { background-color: #fff; font-family: Helvetica, sans-serif; }
			h1 { margin: 10px 0; }
			img { border: 0; }
		</style>
	</head>
	<body>
		<a href="/"><img src="/images/search/twitter-logo-large.png"></a>
    	<h1>The page you were looking for doesn't exist.</h1>
    	<p>You may have mistyped the address or the page may have moved.</p>
	</body>
</html>
>>>

---

### Post by cgroza on 2011-04-04
That function call tries to access a dead link. If you look into that HTML garbage you will notice the number 404 which means that the page is not found.

---

### Post by kenny0128 on 2011-04-04
thanks for the reply.

yes, i see the problem, but i dont know why im getting the dead link.

it should return search.twitter.com/trends.json according to twitter API.

Any clue?

---

### Post by Chimes on 2011-04-05
this almost certainly looks like an error originating with the API's specific interface. Either look at the API more closely to make sure you are doing it right (I will not RTM for you; I'm off the clock right now haha) or if you are sure you are following the API correctly (entering the kind of URL and page location that method might expect, etc), perhaps contact the twitter API developers about a possible bug.

---

