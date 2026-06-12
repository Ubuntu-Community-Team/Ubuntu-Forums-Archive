---
title: "downloading a webpage..."
date: 2008-11-10
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-11-10
how would i download a webpage in C++ or C (doesnt matter which)...ill also take answers for perl since im learning it (kinda) and the answer in perl would probably be faster than C/C++

---

### Post by loell on 2008-11-10
in perl \\:D/
```


use LWP::Simple;
my $content = get('http://www.ubuntuforums.org');


```

---

### Post by jimi_hendrix on 2008-11-10
thanks...ive googled around but found nothing for C/C++...perl definitly looks like its the easiest...basically im trying to make my own web crawler...

---

### Post by kaivalagi on 2008-11-10
Just had a look at what the conky rss C code does, it uses curl libraries. To actually crawl the content is another matter, but Curl is probably a good choice for the comms as it should simplify things a little.

I did find some C examples with curl here: [http://curl.haxx.se/libcurl/c/example.html](http://curl.haxx.se/libcurl/c/example.html)

Further searches on curl and C should give you more info

Hope that helps

---

### Post by jimi_hendrix on 2008-11-10
well my algorithm (feel free to comment) would be:

download webpage
parse string for links
follow randomly selected link
repeat until out of links
backtrack rinse and repeat

---

### Post by LaRoza on 2008-11-10
> **jimi_hendrix said:**
> well my algorithm (feel free to comment) would be:

download webpage
parse string for links
follow randomly selected link
repeat until out of links
backtrack rinse and repeat

Well, I'd use more structured approaches.

I'd use a library for downloading it, a library for parsing html or xhtml, and follow each link.

String parsing and re's on structred markup is silly.

---

### Post by jimi_hendrix on 2008-11-10
is all that in cURL?

---

### Post by snova on 2008-11-10
> **LaRoza said:**
> String parsing and re's on structred markup is silly.

Not necessarily. If you only went by the HTML, you'd miss URLs in places otherwise.

On the other hand, a regular expression to find URLs doesn't sound particularly easy...

> is all that in cURL?

Curl is only an HTTP library, as far as I know.

---

### Post by jimi_hendrix on 2008-11-10
ok ill just use perl then...

---

### Post by jimi_hendrix on 2008-11-10
were would the best place to start crawling be?

---

### Post by jimi_hendrix on 2008-11-10
were would the best place to start crawling be?

---

### Post by jimi_hendrix on 2008-11-11
anyone know of a python lib that can do this...C and Perl both look complex (perl less so but still complex...i hate oop in perl...)

---

### Post by LaRoza on 2008-11-11
> **jimi_hendrix said:**
> anyone know of a python lib that can do this...C and Perl both look complex (perl less so but still complex...i hate oop in perl...)
A lib that can do what? Download? [http://ubuntuforums.org/showthread.php?t=889710](http://ubuntuforums.org/showthread.php?t=889710)

---

### Post by jimi_hendrix on 2008-11-11
and parse

---

### Post by loell on 2008-11-11
python's **urllib / urllib2** and **HTMLParser** :)

the downloading part is easy, but the parsing part, is well.. you'll gonna have to get the hang of it. ;)

---

### Post by jimi_hendrix on 2008-11-11
> **loell said:**
> python's **urllib / urllib2** and **HTMLParser** :)

the downloading part is easy, but the parsing part, is well.. you'll gonna have to get the hang of it. ;)
hehe i just need to parse out the URLs...how hard can that be?

---

### Post by loell on 2008-11-11
> **jimi_hendrix said:**
> hehe i just need to parse out the URLs...how hard can that be?

let me try to roughly splain to ya.. :D

HTMLParser is a base class so after importing it, you'll gonna have to define a class that inherits it.

```
class myparser(HTMLParser):
```

and you'll have to manipulate its methods

[B]def handle_starttag(self, tag, attrs):
def handle_data(self,data):
def handle_endtag(self, tag):[/B]

---

### Post by jimi_hendrix on 2008-11-11
will this get all the URLs in the page or just the one in the tags?

---

### Post by Phenax on 2008-11-11
I would definitely suggest using Perl, Python, or Ruby. Since you haven't investigated Ruby yet, I would suggest:
open-uri (built-in) and [hpricot]("http://code.whytheluckystiff.net/hpricot/") *or*
open-uri and [nokogiri]("http://github.com/tenderlove/nokogiri/tree/master") *or*
[WWW::Mechanize]("http://mechanize.rubyforge.org/mechanize/") (easiest - but uses hpricot and open-uri)

Here's an example of clicking on the first link of a page.
[php]
require 'rubygems'
require 'mechanize'

cl = WWW::Mechanize.new
url = 'http://www.google.com/'

cl.get(url) do |page|
	first_link = page.links[0]
	first_link.click
end
[/php]

Note: Ruby's WWW::Mechanize is actually based on Perl's WWW::Mechanize. Python has a WWW::Mechanize based on perl's too. They are similar, but not the same.

---

### Post by loell on 2008-11-11
> **jimi_hendrix said:**
> will this get all the URLs in the page or just the one in the tags?

the whole tag collection where **A** tag, usually has the link. unless its a forum content ie( hey i'll post the link###), but still doable through tag parsing manipulation.

---

### Post by jimi_hendrix on 2008-11-11
> **Phenax said:**
> I would definitely suggest using Perl, Python, or Ruby. Since you haven't investigated Ruby yet, I would suggest:
open-uri (built-in) and [hpricot]("http://code.whytheluckystiff.net/hpricot/") *or*
open-uri and [nokogiri]("http://github.com/tenderlove/nokogiri/tree/master") *or*
[WWW::Mechanize]("http://mechanize.rubyforge.org/mechanize/") (easiest - but uses hpricot and open-uri)

Here's an example of clicking on the first link of a page.
[php]
require 'rubygems'
require 'mechanize'

cl = WWW::Mechanize.new
url = 'http://www.google.com/'

cl.get(url) do |page|
    first_link = page.links[0]
    first_link.click
end
[/php]Note: Ruby's WWW::Mechanize is actually based on Perl's WWW::Mechanize. Python has a WWW::Mechanize based on perl's too. They are similar, but not the same.

in my quest to know every language i have encountered ruby...i thought it was ok but i will go with whatever is the easiest

---

### Post by jimi_hendrix on 2008-11-11
i give up on perl...i found a nice tutorial on a webcrawler but it needed me to know OOP and perl's oop = headache

---

### Post by loell on 2008-11-11
nice tip by phenax :)

[http://wwwsearch.sourceforge.net/mechanize/]("http://wwwsearch.sourceforge.net/mechanize/")

had i known about this, i would considered using it over HTMLParser module.

---

### Post by jimi_hendrix on 2008-11-11
i am trying to install mechanize through rubygems but am getting:

```
ERROR:  While executing gem ... (Errno::ENOENT)
    No such file or directory - /var/lib/gems/1.9.0/cache/hpricot-0.6.164.gem

```

---

### Post by Phenax on 2008-11-12
> **jimi_hendrix said:**
> i am trying to install mechanize through rubygems but am getting:

```
ERROR:  While executing gem ... (Errno::ENOENT)
    No such file or directory - /var/lib/gems/1.9.0/cache/hpricot-0.6.164.gem

```

try
```
gem cleanup; gem update; gem install hpricot; gem install mechanize
```

---

### Post by jimi_hendrix on 2008-11-12
still getting ```
ERROR:  While executing gem ... (Errno::ENOENT)
    No such file or directory - /var/lib/gems/1.9.0/cache/hpricot-0.6.164.gem
ERROR:  While executing gem ... (Errno::ENOENT)
    No such file or directory - /var/lib/gems/1.9.0/cache/hpricot-0.6.164.gem

```

---

### Post by Phenax on 2008-11-12
Use the stable version of Ruby (1.8.7)

---

