---
title: "Tickers- Where do they come from?"
date: 2011-05-19
forum: Programming Talk
---

### Post by chief30 on 2011-05-19
Most free embed codes for stock tickers come with ads.  No one likes ads, unless you're making money from them.  Question is: How can I stream my own tickers with my own code? Where is the source of the numbers come from?  There must be some link out there. 

Thanks!

---

### Post by oldfred on 2011-05-19
I have seen some python programs that do banners and the like, but have no current links. You cannot get current real time prices without subscriptions but can get the 20 minute delayed numbers from Yahoo or Google.

Python code:

```
import urllib
import re

def get_quote(symbol):
    base_url = 'http://finance.google.com/finance?q='
    content = urllib.urlopen(base_url + symbol).read()
    m = re.search('class="pr".*?>(.*?)<', content)
    if m:
        quote = m.group(1)
    else:
        quote = 'no quote available for: ' + symbol
    return quote

"""
Sample usage:


#!/usr/bin/env python

import stockquote

print stockquote.get_quote('goog')


Output:


>> 529.56
"""

``````

import urllib 
symbols = 'ibm jpm msft nok'.split() 
quotes = urllib.urlopen( 'http://finance.yahoo.com/d/quotes.csv?s='+ 
          '+'.join(symbols) + '&f=l1&e=.csv').read().split() 
print dict(zip(symbols, quotes))
```

---

### Post by chief30 on 2011-05-20
ah thank you very much!  Please forgive me, but I have never worked with python before.  Wht kind of extension do these receive? Thanks!

---

### Post by oldfred on 2011-05-20
It is .py.

I have been adding this as the first two lines to my programs so it knows they are python.

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
```I also found pytick is one I downloaded. Google finds many sites to download from.
There are also many python quote programs that use the above yahoo code but add features. I searched and found many before using python & stock prices tickers etc.

Also synaptic has smtm and ticker, but I have not tried them.

I could not get the google version to work and found the yahoo version as posted has spaces on the last couple of lines.

```
fred@fred-MavericDT:~/Projects/python$ python stockprice.py
  File "stockprice.py", line 2
    symbols = 'ibm jpm msft nok'.split()
    ^
IndentationError: unexpected indent
[COLOR=DarkRed]
 (edited out spaces in file)[/COLOR]
fred@fred-MavericDT:~/Projects/python$ python stockprice.py
{'jpm': '43.54', 'ibm': '169.81', 'msft': '24.65', 'nok': '8.3775'}
fred@fred-MavericDT:~/Projects/python$ 


```I will remove spaces in first post.

---

### Post by oldfred on 2011-05-20
I have not tried to do anything with a web page.

I just did a search in Google and there are many sites. You will have to see who has free and some bits of code to use. I am sure the first few may be sites that are paid or want to use ads.

My Google search:
tickers in website

See also this:
[http://finance.yahoo.com/badges/](http://finance.yahoo.com/badges/)

---

