---
title: "A new search-engine to dethrone google ?"
date: 2010-04-01
forum: Programming Talk
---

### Post by nexx on 2010-04-01
Well this is mostly a dream as I think that google is impossible to dethrone and whats the need to do that anyway? But I am programming a small javaScript search-engine that is working very well and I have a few questions:

For now my code is on the web ([www.artimap.com](www.artimap.com)) but is not open-source I do want to make it open, but I would like to get something for the 6++ months it took me to program it. So the question is: How can I make money out of something that new and exclusive if everybody has the source code ? I am working nearly totally alone on that project and sure it would be fun and efficient to do that in a team. 

Also if everybody had an easy way of putting a fast search-engine in their web document, everybody would be competing with the giant search-engines. We can dream even more and think of a way to connect those micro-search engines together... Perhaps with some sort of bittorent-like protocol.

Well I know I am a dreamer ](*,)

---

### Post by Wybiral on 2010-04-01
The first step in making money from an open source project like this would be to get it popular, get it out there.

The best bet for making money would be if it got popular enough that some company would want to acquire it (think MySQL being acquired by Sun).

Other than that there's support fees, donations, ad money, or any other kind of service you can offer for the product.

---

### Post by nexx on 2010-04-02
Well, to make it popular, ther are things beyond coding, the visual design is also of paramount importance. I a trying a few new skins for the search-engine and should be able to post it soon.

I think I could begin with releasing the code block by block so it will be possible to explain it as the whole thing is very complex.

---

### Post by cubeist on 2010-04-02
That is a very innovative search engine, very cool.  The big issue for a search engine is not how to display the results (which yours does very well), but how well it can index a page.  If the backend of your code is as innovative as the frontend, it is not too far fetched to think you are onto something seriously cool!

PS.  Since I am all for open-source, I rarely offer this advice, but I would say keep your code private, maybe even think about a patent for your process.  Also, at the bottom of your page I would add a line saying your name, copyright, and the year.  This copyrights the design as it is viewed.

---

### Post by nexx on 2010-04-02
I changed the design again, cannot get satisfied...

Yhis search-engine is specialised in indexing the content of very large html documents. I wish to add some AJAX to be able to get content from the web.

---

### Post by LKjell on 2010-04-02
The math that google use is available to everyone. They use some matrix calculation. However, even if you know the math it does not mean that you can implement the same stuff.

---

### Post by nexx on 2010-04-02
Well, the maths I use for [www.artimap.com](www.artimap.com) is way simpler than what google uses. Of course that would not be able to scale if I wanted to index the web, but for indexing enormous html documents, that's nearly perfect. From the start I wanted methods (algorhytms) that are not perfect but gives a good answer most of the time. This micro-search engine is programmed in javaScript, it's a very slow language, so a method that would give perfect answers would be so complicated and slow...

The main difference between my search-engine and the google's one is that on mine searches are intantaneous (as you type) and that you can also double-click any words in the page to search for it instantly.

Also, all the html in the page is on microformats. Each div of informations is a vcard. It helps google, bing and yahoo robots to understantd the html, and hopefully display's better in their results.
The microformat html will also make possible to augment the power of the micro-search engine when somebody want to search only by adresse, phone number, country or street.

Thanks Cubeist, I followed your suggestion of adding a copyright notice at the bottom.

---

### Post by iansyngin on 2010-04-02
your site is down mate

---

### Post by nexx on 2010-04-02
The site seemed slow the last hour, but is back now.

---

### Post by sxmaxchine on 2010-04-02
wow very nice website good job.

your best chance at making money would be through advertisement or maybe if a company descides to buy your site.

---

### Post by sxmaxchine on 2010-04-02
> **sxmaxchine said:**
> wow very nice website good job.

sorry i just realised something, was [this]("http://www.artimap.com/") your site. if not can i get the link to your site if it is available.

---

### Post by juancarlospaco on 2010-04-02
There are open source working search engines, see Apache Lucene and derivatives

---

### Post by nexx on 2010-04-02
sxmaxchine, the adress is: [www.artimap.com](www.artimap.com)

---

### Post by nexx on 2010-04-02
juancarlospaco, these search-engines are for crawling the web. Mine is for indexing one very large html documents at a time(whitout images as images are loaded on demand depending on what is searched). It's a different concept, useful for navigating enormous web pages. It's page search on steroids.
Also these big search-engines work from the server, mine is entirely in javaScript, so it work in the browser.
It would be interesting to add some AJAX so the [www.artimap.com](www.artimap.com) micro-search engine could communicate with the server search-engine and google or yahoo API(s).

---

### Post by Reiger on 2010-04-03
Nope. Lucene is search. Also, you may want to look at Nepomuk (which is intended for usage on the desktop first, I know).

---

### Post by SoftwareExplorer on 2010-04-03
Have you heard of bee seek? That's what I'm hoping will dethone google someday.

---

### Post by nexx on 2010-04-03
The Beeseek search engine at [http://beta.beeseek.org/search/](http://beta.beeseek.org/search/) does not seem to work now, any search words I tried returns no results. Anyway it's a very interesting project, with a bittorent like protocol that make the information being shared on multiple users hard drives. That much more in line with open source ideas and freedom of access to information.

Another thing that I use intensively on my search-engine is Microformats ([http://microformats.org/](http://microformats.org/)) as they are a way to make information easily avalaible.

---

