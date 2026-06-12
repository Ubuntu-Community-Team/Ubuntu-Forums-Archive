---
title: "Python HTML Processing/Manipulating"
date: 2010-05-04
forum: Programming Talk
---

### Post by km0r3 on 2010-05-04
Hello Forum,

I'm having trouble processing/manipulating HTML with Python.

I have a script which should do, for example, these things:

1) Convert these fragments:
```
<div>Hello, world</div>
<div class="spam">Hello, you!</div> 
```
to something like this on the fly:
```
<div class="newClass">Hello, world</div>
<div class="spam newClass">Hello, you!</div> 
```

2) Make this fragment:
```
<span title="Hello!">Hello, world!</span>

```look like this
```
<span title="Hello!" class="hasTitleAtt">Hello, world!</span>
```

Actually, those things can be done by great libraries like BeautifulSoup or lxml for Python.

I've tried myself on that with BeautifulSoup. See here:

```
import re
import sys
import BeautifulSoup


TAGS_TO_SEARCH = ['title', 'p', 'h1', 'h2', 'h3', 'h4', 'h5']

def has_content(s):
    if s.contents == []:
        return None
    return s

def translate(soup):
    for tag in soup:
        # Check that it has content
        if has_content(tag) is not None:
            try:
                if tag['class'] == None or tag['class'] == u'':
                    # Returns key error if `class` attribute wasn't defined
                    pass
                # Check if class attribute already contains 'translate'
                elif tag['class'] and 'translate' in tag['class']:
                    pass
                elif tag['class'] and 'translate' in tag['class']:
                    tag['class'] += ' translate'
            except KeyError:
                tag['class'] = 'translate'
            print tag

def write(s):
    pass

if __name__ == "__main__":
    try:
        html = sys.argv[1]
    except IndexError:
        print "Please specify a HTML input file!"
        sys.exit(-1)

    soup = BeautifulSoup.BeautifulSoup(open(html))
    soup = soup.findAll(TAGS_TO_SEARCH)

    translate(soup)

```

My only problem is that it's not possible to write that on the fly to the HTML.

I ask for your help, suggestions or advice.

This is no homework assignment.

---

