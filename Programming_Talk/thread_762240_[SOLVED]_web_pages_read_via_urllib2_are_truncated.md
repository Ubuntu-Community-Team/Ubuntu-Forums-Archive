---
title: "[SOLVED] web pages read via urllib2 are truncated"
date: 2008-04-21
forum: Programming Talk
---

### Post by twisted_steel on 2008-04-21
I have some Python code that is downloading a page with urllib2 and then doing a *read()* on the resulting object.  I have been printing out the page by redirecting the output to a file and using tail -f.  For some reason, the page is never complete.  Sometimes it will display up to just before the footer, other times it will be an earlier part in the page.  Looking at the [urllib2 documentation]("http://docs.python.org/lib/module-urllib2.html") and all of the examples I have found, I don't believe this should be happening unless it somehow thought there was an end of file (EOF) in the page itself.

I have a method that sets the request variable to a *urllib2.Request*.

```
request = urllib2.Request(self.pageURL)
```Another method is then passed this request and does the following (sans try/except block):

```
response = urllib2.urlopen(request)
...
# Save the HTML of the resulting page
self.resultPage = response.read()
response.close
```After that, I have been printing out the *resultPage* for debugging.  Any idea why this would be happening?  The HTML is intact if I download the page with Firefox.

---

### Post by twisted_steel on 2008-04-21
](*,)

Apparently for some reason or another, the closing tags were not being shown in the output of tail -f (I even had two types of terminals going), but did exist in the actual redirected file.  Good times.  Marking this one as solved :p

---

### Post by nanotube on 2008-04-22
> **twisted_steel said:**
> ](*,)

Apparently for some reason or another, the closing tags were not being shown in the output of tail -f (I even had two types of terminals going), but did exist in the actual redirected file.  Good times.  Marking this one as solved :p

some notes:

"response.close" should be "response.close()" :)

one reason why the last bits of the file may not have been showing is if you haven't closed or flushed the file write buffer. by default python's file writes are buffered. don't know if that was the case for you, since you haven't included your actual file writing code, but just throwing it out there.

---

### Post by twisted_steel on 2008-04-22
All I was doing to 'write' the file was use print statements in my code.  I then ran the program and redirected the output to a file.

```
./myprogram.py > output.txt
```

I was then watching the output in a terminal with:

```
tail -f output.txt
```

As a side note, any idea where the link to mark a thread solved went?

---

