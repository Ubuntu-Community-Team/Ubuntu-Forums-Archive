---
title: "Parsing HTML with C++"
date: 2010-04-11
forum: Programming Talk
---

### Post by Drone022 on 2010-04-11
I'm using libcurl to give an html dump of a webpage. I then want to go through the html and find the lists, so I'm only looking for stuff between <li> and <\li>.

I thought it would be easier to do this myself than download a library to do this (libxml is for this stuff right?). I'm basically too lazy to download and link in another library. Libcurl gave me a few headaches but I got them sorted.

The problem is how do I deal with the escape character? '\' is just ignored in my string. Also, wierdly, my 'g' turn out as a smiley face, I have no idea why.

Can I do this myself or should I find an html parsing lib?

---

### Post by CptPicard on 2010-04-11
How about just regular expressions?

---

### Post by Some Penguin on 2010-04-12
libxml isn't recommended; HTML is a looser standard, structurally speaking.

Regular expressions will work, although you may have to consider whether you'll need to handle lists within lists and other more complex cases.

---

### Post by lukeiamyourfather on 2010-04-12
I realize the post is asking about C++ but maybe there's a better tool for parsing this kind of information (e.g. Python or Perl). Its worth noting I'm not very familiar with C++ but I am with Python, so I'm a little biased. Cheers!

---

### Post by gmargo on 2010-04-12
> **Drone022 said:**
> so I'm only looking for stuff between <li> and <\li>.

The problem is how do I deal with the escape character? '\' is just ignored in my string. 

Is there some forward/backward slash confusion here? HTML uses a forward slash to terminate tags, not a backslash; <li> ... </li>.

Regarding the parsing: I do this sort of thing in Perl with the HTML::TreeBuilder module.  Also http fetching is easy with the LWP::UserAgent module.

---

### Post by phrostbyte on 2010-04-12
Qt includes a pretty powerful HTML/XML parser. Eg:

```

QDomDocument d;
d.setContent(someFile);
QDomNodeList e = d.elementsByTagName("li");
for (int i=0; i<e.length(); i++) {
   // e.item(i).toElement().text() 
}

```

---

### Post by myrtle1908 on 2010-04-13
If you must parse foreign HTML (by foreign I mean that you did not compose it), then consider first tidying it up with HTMLTidy [http://tidy.sourceforge.net/](http://tidy.sourceforge.net/).

As someone else pointed out, doing this in Perl or Python is trivial and either language would be a better fit for your problem.

In Perl you can simply grab everything in between the '<i></i>' tags if you go list context eg.

```
use strict;
use warnings;
my $s = '<i>hello</i> there <i>world</i>';
my @p = ($s =~ m/<i>(.*?)<\/i>/g);
print join '|', @p;
```

Yields:-

```
hello|world
```

If you go with Python, have a look at BeautifulSoup [http://www.crummy.com/software/BeautifulSoup/](http://www.crummy.com/software/BeautifulSoup/).

---

