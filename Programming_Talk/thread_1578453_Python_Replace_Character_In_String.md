---
title: "Python: Replace Character In String"
date: 2010-09-20
forum: Programming Talk
---

### Post by Sailor5 on 2010-09-20
Ahoy Sailors!

So I'm downgrading my Python script to 2.3, Where rsplit no longer exists, And I need to extract the name and extension from a url. I've used os.path.splitext on the url which comes back with

[http://www.website.org/Image](http://www.website.org/Image)
&
png
However now I need to get the name from the url (Image), before I used rsplit```
 tra,nme = line.rsplit('/',1)
```But how can I do such without rsplit?

Thanks Bye!

---

### Post by Bachstelze on 2010-09-20
.split('/')[-1]

```

>>> s
'http://www.website.org/Image.png'
>>> os.path.splitext(s)[0].split('/')[-1]
'Image'

```

---

### Post by StephenF on 2010-09-20
```

>>> import urlparse
>>> urlparse.urlparse("http://www.website.org/Image.png")
ParseResult(scheme='http', netloc='www.website.org', path='/Image.png', params='', query='', fragment='')

```
It's not a named tuple in Python 2.3 I'll wager.

---

### Post by mo.reina on 2010-09-21
with regex:

```
>>> s
'http://www.website.org/Image.png'
>>> urlpattern = re.compile(r'^(\D+)/(\D+)$')
>>> urlpattern.search(s).groups()[1].split('.')[0]
'Image'

```

---

