---
title: "Help Needed: Making My Own Search Engine"
date: 2011-04-01
forum: Programming Talk
---

### Post by coljohnhannibalsmith on 2011-04-01
Hello,

I'm interested in the possibilty of making my own search engine rather than relying on the existing ones like Google, Bing, and Dogpile.  I'm interested in doing this for a variety of reasons; to overcome censorship, geographical and language filtering, and to maximize privacy.  Does anyone have any ideas about how to do this?

I suspect I would probably want to dedicate a machine for this purpose, and of course some kind of web-crawler application would have to be installed to crawl the web, looking for web sites to index. Also, I suspect that I would probably have to let such an application run uninterrupted, pretty much continuously.  I've tried searching the web for pre-existing applications or scripts to do this, but I just haven't found anything.  Perhaps I don't know the vocabulary and am not entering the correct search terms. 

Any help or suggestions appreciated.


Thanks, Hannibal

---

### Post by jennybrew on 2011-04-01
Gosh!!!
You must be a genius.
Do you not have to come up with search algorithms etc, ets?

---

### Post by matt_symes on 2011-04-01
> **jennybrew said:**
> Gosh!!!
You must be a genius.
Do you not have to come up with search algorithms etc, ets?

and a big, fat, optimised database....

Stick to google.

---

### Post by coljohnhannibalsmith on 2011-04-01
For the afore mentioned reasons, I'd prefer not to. Also, I suspect much of the things you've mentioned have already been done by others; so I don't think I'd have to completely re-invent the wheel, as you seem to suggest. Additionally, I would expect that this forum would attract individuals of that calibre.  So for the moment at least, I don't think I'm in the wrong place.:confused:  Also, for the moment, this is just a thought experiment...
why such strong reactions?

Any 'constructive' replys appreciated.


Thanks, Hannibal

---

### Post by matt_symes on 2011-04-01
Hi

As i said, start off by setting up large, optimised database. MySQL is a good start.

Read this.

[http://www.webopedia.com/DidYouKnow/Internet/2003/HowWebSearchEnginesWork.asp](http://www.webopedia.com/DidYouKnow/Internet/2003/HowWebSearchEnginesWork.asp)

If you are worried about privacy, have you considered TOR ?

Can you administer a database and write code ?

Kind regards

---

### Post by juancarlospaco on 2011-04-01
You dont need to do that, theres already open source search engines,
in example see Apache** Lucene **and derivatives...  :D

---

### Post by uRock on 2011-04-01
Moved to programming talk.

Please do not create support threads in the Community Cafe.

---

### Post by |{urse on 2011-04-01
The undertaking of creating your own search engine would be ridiculously complex to nigh impossible to implement unless you have tons of dollars and some amazing coders at your disposal.

Thats as constructive as I can be on this.

---

### Post by matt_symes on 2011-04-01
Hi

> the moment, this is just a thought experiment...
why such strong reactions?

No strong reactions. I think you misunderstand me. 

It is just a huge, huge job and you need more than one skill set to do it.

Kind regards

---

### Post by coljohnhannibalsmith on 2011-04-02
> **matt_symes said:**
> Hi



No strong reactions. I think you misunderstand me. 

It is just a huge, huge job and you need more than one skill set to do it.

Kind regards


Thank you Matt,

Perhaps I did misunderstand You.  You're probably very right that this is a very complex undertaking. I am however very interested in how this can be done and I have admitted my naivety about this topic.  Also, these kinds of challenges are my 'Raison d'etre,' or something.  I've always found the available search engines, not just a potential source of insecurity, but also a massive and distracting generator of advertising, and disappointing in terms of relevent results.

Thank you for the informative information link you provided; I will study it as soon as I get the chance.  BTW the poster from Buenos Aires suggested something close to what I was hoping for:

"You dont need to do that, there's already open source search engines,
in example see Apache** Lucene **and derivatives...  :grin:"

I'm sure this is still a complex solution, and I'll try not to underestimate it.  BTW, I can code a 'little.'  I'm very comfortable compiling code, and somewhat comfortable modifying small errors in other peoples code.

'uRock,' sorry about posting in the wrong forum.  I didn't know where else to post this thread, and I figured that it would be better to 'start' here, and then get moved, than to start the post in a more specific forum.  Perhaps 'General Help' would have been a better starting point?


Thanks, Hannibal

---

### Post by rg4w on 2011-04-02
Really, Lucene is the answer.  I've toyed with all manner of custom search engines, and while doing so can provide a good education and even be fun, performance and storage requirements make them unsuitable for all but a very few highly vertical tasks. There's a reason Google invented their own file system. ;)

If you want to proceed, Lucene is an excellent start.  That, and several terrabytes of storage, which will let you index about 0.0001% of the web, which may be enough to learn what you want to learn.

---

### Post by coljohnhannibalsmith on 2011-04-02
Oh BTW,

I've tracked this down a little more and discovered the following site:

[http://lucene.apache.org/java/docs/features.html](http://lucene.apache.org/java/docs/features.html)

Also, I'm in the process of dowloading 'Lucene in Action,' in pdf format.  I'll give this a good and thorough read.


Thanks, Hannibal


PS, what does '[rg4w]("http://ubuntuforums.org/member.php?u=962490")' stand for, if you don't mind?

---

### Post by Arndt on 2011-04-02
> **coljohnhannibalsmith said:**
> For the afore mentioned reasons, I'd prefer not to. Also, I suspect much of the things you've mentioned have already been done by others; so I don't think I'd have to completely re-invent the wheel, as you seem to suggest. Additionally, I would expect that this forum would attract individuals of that calibre.  So for the moment at least, I don't think I'm in the wrong place.:confused:  Also, for the moment, this is just a thought experiment...
why such strong reactions?

Any 'constructive' replys appreciated.


Thanks, Hannibal

Maybe this is interesting: [http://webglimpse.net/](http://webglimpse.net/)

---

### Post by rg4w on 2011-04-02
> **coljohnhannibalsmith said:**
> PS, what does '[rg4w]("http://ubuntuforums.org/member.php?u=962490")' stand for, if you don't mind?
Not at all:  it's a combination of my initials and the initials of my company name.

---

### Post by simeon87 on 2011-04-02
Anyone remotely capable of building a search engine wouldn't ask about the basics in these forums. Crawling the web, ranking webpages and quickly answering queries are vast subjects in their own right. The size of the internet also makes it very hard for an individual to crawl even a small part of the web without some decent hardware purchases. If you still want to go ahead, you should read about PageRank and how other search engines are ranking pages, about web crawling technology and how to produce a ranking of pages based on a query.

---

### Post by Some Penguin on 2011-04-02
Lucene isn't suited for general-purpose web search engines unless you're willing to shove a LOT of hard work and magic into the analyzer.  It's reasonably suited for intranet documentation where you have reasonable expectations that everything you're indexing is worthy and you're just interested in inverted indexing, but the Web is full of spam and garbage.

---

### Post by NathanB on 2011-04-02
Plenty of open-source options exist.

[http://swish-e.org/](http://swish-e.org/)

[http://xapian.org/](http://xapian.org/)

[http://www.htdig.org/](http://www.htdig.org/)

to name just a few from the huge list of search engines...

Can't find it now, but there is one out there that will let you download their compressed database of everything their crawler/bot has collected.  With a little searching, you can stumble into lots of neat tools/resources.

---

### Post by coljohnhannibalsmith on 2011-04-07
Thanks to all of you for your kind and generous help.

While stumbling through Synaptic, I've discovered that all of these packages, with the exception of Web-Glimpse, are available in the repository.  Oh, happy day.:guitar:

That's not to say that it won't be a challenge to configure and run these applications.


One of you suggested that I do the following:

"If you still want to go ahead, you should read about PageRank and how  other search engines are ranking pages, about web crawling technology  and how to produce a ranking of pages based on a query."

I think this is sound advice since for web documents there will be, as I was warned, plently of spam and other useless material.


Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2011-04-07
While searching for information about Webcrawlers I discovered the following:

[http://en.wikipedia.org/wiki/Web_crawler](http://en.wikipedia.org/wiki/Web_crawler)


The ones that look the most interesting are:


crawer4j

[http://code.google.com/p/crawler4j/](http://code.google.com/p/crawler4j/)




Nutch, which is used with Lucene:

[http://en.wikipedia.org/wiki/Nutch](http://en.wikipedia.org/wiki/Nutch)


and,


YaCy (Yah, See) which claims to do most of the things I'm interested in:

[http://yacy.net/en/](http://yacy.net/en/)

I'm downloading this now.  I can't wait to try it.:lolflag:

---

### Post by coljohnhannibalsmith on 2011-04-07
YaCy Rocks!!!:guitar:
[http://yacy.net/en/](http://yacy.net/en/)

This is an out-of-the-box solution, and it even searchs the 'hidden-web,' and just like they promise, NO ADVERTISING, and NO CENSORSHIP!!!

Hoo-Yah.


I'm still going to experiment with Lucene & Nutch though!


Hannibal

---

### Post by coljohnhannibalsmith on 2011-05-17
[COLOR=Blue]***It appears that this problem is now solved!!!***[/COLOR]

[IMG]http://tshirtgroove.com/wp-content/uploads/2008/10/problem-solved-tshirt.jpg[/IMG]

---

