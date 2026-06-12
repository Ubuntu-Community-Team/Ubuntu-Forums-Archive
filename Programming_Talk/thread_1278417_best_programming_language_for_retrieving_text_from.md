---
title: "best programming language for retrieving text from web page?"
date: 2009-09-29
forum: Programming Talk
---

### Post by Despot Despondency on 2009-09-29
Hi,

My question is in the title really. I'm wondering what the best language is for retrieving text from a web page. Any ideas opinions?

---

### Post by j.bell730 on 2009-09-29
If you understand [Regular Expressions]("http://en.wikipedia.org/wiki/Regular_Expression"), I recommend Python.

Save (as something.py) and run the following:
```
from urllib import urlopen
import re
p = re.compile('<div class=.*? id=.*?>.*?\n.*?\n(.*?)</div>') #string to search for on webpage (according to page source)
text = urlopen('http://ubuntuforums.org/showthread.php?p=8026441#post8026441').read() #url to look on
for message in p.findall(text):
    print '%s' % (message)  #print matches
```

[More]("http://docs.python.org/dev/howto/regex.html") about regular expressions.

---

### Post by chrisjsmith on 2009-09-29
I'll second that

---

### Post by Despot Despondency on 2009-09-29
Thanks for the response. I only know c++ and Java at the moment so I'll have to look into python.:)

---

### Post by doas777 on 2009-09-29
i wrote a parser in python, so i agree with the others. I did see an example once though, where a guy had done a pages worth of python in a single line sed command. it was amazing. not sure it's the best (boundraries and error conditions being what they are) but somthing to consider.

---

### Post by A_Fiachra on 2009-09-29
There is a library for Python called BeautifulSoup which makes reading HTML quite easy.

Here is an example:

```


seen = {}
splitter = re.compile("\\W*")
url = sys.argv[1]
if len(url) == 0 :
    print sys.stderr>> "Usage : " + sys.argv[0] + " <url>"
page = urllib2.urlopen(url)
soup = BeautifulSoup(page)

for title in soup('title'):
    seen = dict ( [(s.lower(),1) for s in splitter.split(title.contents[0]) if s != ''] )

for h in soup('h1') :
    content = gettextonly(h)
    for s in splitter.split(content) :
        W = s.encode('ascii', 'ignore')
        w = W.lower()
        if w != "" and  w not in StopWords :
            if w in seen.keys() :
                seen[w] += 1
            else :
                seen[w] = 1 


```

It's from a program that counts word frequencies grouped by HTML tag.

The cool thing is that you can say things like:

```

for d in soup.findAll('div', { 'id' : 'some-id' } ):
    do_domething_cool(d)

```

Perl has a few HTML parsers, I like HTML::Parser

```

HTML::Parser->new(api_version => 3,
          handlers    => [start => [\&tag, "tagname, '+1'"],
          end   => [\&tag, "tagname, '-1'"],
          text  => [\&text, "dtext"],
         ],
      marked_sections => 1,
)->parse($content) || die "Can't open file: $!\n";

```

Your register callbacks for each event (like a SAX parser).  Used with LWP::UserAgent, it's a pretty effective way of scraping web pages.

HTH

---

### Post by doas777 on 2009-09-29
> **A_Fiachra said:**
> There is a library for Python called BeautifulSoup which makes reading HTML quite easy.

Here is an example:

```


seen = {}
splitter = re.compile("\\W*")
url = sys.argv[1]
if len(url) == 0 :
    print sys.stderr>> "Usage : " + sys.argv[0] + " <url>"
page = urllib2.urlopen(url)
soup = BeautifulSoup(page)

for title in soup('title'):
    seen = dict ( [(s.lower(),1) for s in splitter.split(title.contents[0]) if s != ''] )

for h in soup('h1') :
    content = gettextonly(h)
    for s in splitter.split(content) :
        W = s.encode('ascii', 'ignore')
        w = W.lower()
        if w != "" and  w not in StopWords :
            if w in seen.keys() :
                seen[w] += 1
            else :
                seen[w] = 1 


```It's from a program that counts word frequencies grouped by HTML tag.

The cool thing is that you can say things like:

```

for d in soup.findAll('div', { 'id' : 'some-id' } ):
    do_domething_cool(d)

```Perl has a few HTML parsers, I like HTML::Parser

```

HTML::Parser->new(api_version => 3,
          handlers    => [start => [\&tag, "tagname, '+1'"],
          end   => [\&tag, "tagname, '-1'"],
          text  => [\&text, "dtext"],
         ],
      marked_sections => 1,
)->parse($content) || die "Can't open file: $!\n";

```Your register callbacks for each event (like a SAX parser).  Used with LWP::UserAgent, it's a pretty effective way of scraping web pages.

HTH

most Kewl! I'll have to revisit my manga grabber.

---

### Post by fiddler616 on 2009-09-29
Any scripting language should do (Python, Perl, Ruby, PHP...). Slavik is going to come in here and start talking about how wonderful Perl is, and he's probably right in that Perl can be very powerful if wielded appropriately. But for your purposes I recommend Python--almost everything in it is just going to be really clean, pseudo-codey Java, and the urllib/urllib2/re (regex) libraries are pretty straightforward. There's quite a few good tutorials--just Google the module (aka library) name.

---

### Post by mymiasma on 2009-11-04
If all you want is to convert the HTML to plain text there is a command line tool (html2text) that does a good job of it and it is available as an official Ubuntu package and can be easily installed with Synaptic.

However, if you want to do a more selective scrape of specific parts of a page and extract just the text you want then I agree on using the BeautifulSoup library under Python. Someone may be able to make good arguments for languages other than Python for specific tasks but, for my money, it is the best all round language for beginners and advanced programmers. BeautifulSoup is especially good at making sense of badly written HTML and XML.

Links:
html2text [http://man-wiki.net/index.php/1:html2text](http://man-wiki.net/index.php/1:html2text)
BeautifulSoup [http://www.crummy.com/software/BeautifulSoup/](http://www.crummy.com/software/BeautifulSoup/)

---

