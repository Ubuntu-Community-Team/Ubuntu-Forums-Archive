---
title: "ruby cgi question, apparently i'm slow"
date: 2006-03-26
forum: Programming Talk
---

### Post by oldmanstan on 2006-03-26
when i run this code on my server i get weird behavior... this
```

#! /usr/bin/ruby
require 'cgi'

cgi = CGI.new
cgi_vars = cgi.params

print "Content-type: text/html\n\n"

val1 = cgi_vars['val1']
puts val1

```
prints whatever i stuck in val1 in the url, however this
```

#! /usr/bin/ruby
require 'cgi'

cgi = CGI.new
cgi_vars = cgi.params

print "Content-type: text/html\n\n"

val1 = cgi_vars['val1'].to_i
puts val1.to_s

```
doesn't print anything when i make val1 and integer (the difference is the .to_i and .to_s method calls) i've searched through the documentation and the pragmatic book but i can't find a single reason why this wouldn't work

anybody have any ideas? maybe i'm just slow, or i've been staring at it too long... thanks!

---

### Post by oldmanstan on 2006-03-26
Never mind, figured it out... cgi.params returns a hash of arrays, not a hash of strings, cgi[] itself is the hash of strings... the pragmatic online book didn't make this clear but i found it in the ruby-doc.org site

---

