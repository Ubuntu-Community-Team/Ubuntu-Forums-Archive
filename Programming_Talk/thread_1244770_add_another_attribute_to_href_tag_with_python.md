---
title: "add another attribute to href tag with python"
date: 2009-08-19
forum: Programming Talk
---

### Post by mbeach on 2009-08-19
For the purposes described at:
[http://www.google.com/support/googleanalytics/bin/answer.py?hl=en&answer=55527](http://www.google.com/support/googleanalytics/bin/answer.py?hl=en&answer=55527)

I'm trying to add an onclick event to <a> tags in a particular string stored in the datastore.

So assuming I have a string
```

this is a <a href="http://www.somedomain.com">link</a> and 
so is <a href="home.html">this</a> and <a href="/home">this is too</a>

```
I want to add the first <a> tag to look like
```

<a href="http://www.somedomain.com" onClick="javascript: pageTracker._trackPageview('/outgoing/somedomain.com');">

```

but not the other links. So I'm playing around with searching for the "http" in a regex expression as that will determine an external link (for this site's setup anyway).

Still digging away at it but thought I'd throw up a post here in case someone knows a public function/library out there that already does just this.

Thanks,
mb.

---

### Post by myrtle1908 on 2009-08-19
Beautiful Soup ... [http://www.crummy.com/software/BeautifulSoup](http://www.crummy.com/software/BeautifulSoup)

For modifying some HTML see ... [http://www.crummy.com/software/BeautifulSoup/documentation.html#Modifying%20the%20Parse%20Tree](http://www.crummy.com/software/BeautifulSoup/documentation.html#Modifying%20the%20Parse%20Tree)

You could also do this fairly easily at runtime with JavaScript.

---

### Post by mbeach on 2009-08-20
I had started down the road figuring javascript should handle this easy enough, but couldn't seem to find much other than people attempting to pop up a window when someone left their site.

I'd be happy to find a javascript solution, but for now I'm taking a look at BeautifulSoup for a whole host of other reasons as well.

Thank you

---

### Post by mbeach on 2009-08-20
Continuing to toy away with this, have come up with this so far (almost posting here for my personal reference now) but I just need the url out of the href attribute value
[PHP]
from externals.bs import BeautifulSoup

content = """
this is a <a href="http://www.somedomain.com">link</a> and 
so is <a href="home.html">this</a> and <a href="/home">this is too</a>
"""

tracker = "javascript: pageTracker._trackPageview(\'%s\');"

soup = BeautifulSoup(content)

for i in range(len(soup('a'))):
  #add an if here to check if this is an external link
  #for now, adding to all links
  soup('a')[i]["onclick"] = tracker % 'baselinkurl'

print soup

[/PHP]

---

### Post by mbeach on 2009-08-20
there is probably a prettier way to handle the if statement here, but this seems to work as long as the http:// is in lower case.

[php]
from externals.bs import BeautifulSoup

content = """
this is a <a href="http://www.somedomain.com">link</a> and 
so is <a href="home.html">this</a> and <a href="/home">this is too</a>
"""

tracker = "javascript: pageTracker._trackPageview(\'%s\');"

soup = BeautifulSoup(content)

for i in range(len(soup('a'))):
  if soup('a')[i]['href'][0:7] == "http://":
    soup('a')[i]["onclick"] = tracker % ("/outgoing/" + soup('a')[i]['href'][7:])

print soup

[/php]

---

### Post by myrtle1908 on 2009-08-20
> **mbeach said:**
> I'd be happy to find a javascript solution ...

```

<script>
window.onload = function() {
	var a = document.getElementsByTagName('a');
	for (var i=0; i<a.length; i++) {
		var link = a[i];
		if (link.href.match(/^https?:\/\/.*/i)) {
			var re = /^https?:\/\/(www\.)?([^/]+)?/i;
			link.href.match(re);
			var domain = RegExp.$2;
			link.onclick = function() {
				pageTracker._trackPageview('/outgoing/' + domain);
			};
		}
	}
}
</script>

this is a <a href="http://www.somedomain.com">link</a> and 
so is <a href="home.html">this</a> and <a href="/home">this is too</a>

```

---

### Post by mbeach on 2009-08-20
thanks - I'll try that out - in my situation will work better, as I can place it in  the base template and be done. My python method was going to be a bit painful - not serious pain, but enough to cause some grief.

Good stuff,
mb.

---

### Post by myrtle1908 on 2009-08-20
> **mbeach said:**
> thanks - I'll try that out - in my situation will work better, as I can place it in  the base template and be done. My python method was going to be a bit painful - not serious pain, but enough to cause some grief.

Good stuff,
mb.

Can shorten to this ...

```
<script>
window.onload = function() {
	var a = document.getElementsByTagName('a');
	for (var i=0; i<a.length; i++) {
		var link = a[i];
		if (link.href.match(/^https?:\/\/(www\.)?([^/]+)?/i)) {
			var domain = RegExp.$2;
			link.onclick = function() {
				pageTracker._trackPageview('/outgoing/' + domain);
			};
		}
	}
}
</script>
```

I assume you are only interested in the domain name.  For example it wouldn't include '/abc/' in [http://www.somedomain.com/abc/](http://www.somedomain.com/abc/)'.

---

### Post by mbeach on 2009-08-20
yes, just trying to measure the amount of traffic I'm sending to a number of external links - domain is fine, no need for further path info.

thanks for your help.
mb.

---

