---
title: "Which language/libs to use: web-based app"
date: 2010-04-21
forum: Programming Talk
---

### Post by Aped on 2010-04-21
So I'm going to make a new serverside script to monitor several blogs at once and create a 'metablog' - it's going to be very specific and niche and will probably be a pet project with no viable outcome over the next few years. 

The script will, basically:
- get information from certain blogs
- parse/analyze links and
- potentially get information from linked blogs. Then
- create/update a page & database with several fields for each blog (update time, salient content, link, bla bla)

and that's about it.

I have until now been building it in several distinct chunks. I had a bash script on cron that used a series of wget and 'case' statements to get all of the information and etc etc, basically quickly realized that this was a poor way to go. Scrapped it. Now, going for something new, extensible, little more portable. 

Being new to web development, I feel it's probably best to just jump in and start GOING, but before I invest too heavily, I want to make sure I'm doing this right. My questions, then, if you're still reading and have the expertise:

- Language: Perl, I know some. Python, I know some. Ruby/RoR, I know zip. Same goes for PHP. 
- Databasing: I could use a formatted/csv text file but I feel an SQL database is probably called for, since I wanna do it RIGHT. It's worth learning, right? 
- The setup: One script to rule them all? Several which call each other? One to GET, one to sort, one to create a page? Probably just one to get/sort into a database and then a second to update/create a page based on that, non?
- Libraries used: Basically I think I'm looking at curl here. Anyone have experience with it and/or similar things? Any suggestions? 

And am I missing anything out? I just wanna do it right from the get-go and am in the planning phase now... anyway, thanks a ton in advance for any and all help.

---

### Post by slavik on 2010-04-22
language - "anything with an rss library" I think. unless you want to crawl the html page in which case, curl is it.
db - yes, stick a db behind it
setup - separate the process as needed, easier to maintain. make sure to setup - define simple interfaces (small magic happens in one function, not one big magic in one function)
libraries - yes, curl if you want the raw html vs. rss

---

### Post by Aped on 2010-04-22
Well I don't necessarily want it to be dependent upon someone having an RSS feed, so html crawling seems to be the best solution? 

I guess I'm leaning towards perl here, since I don't think I've ever seen python used to generate a webpage.

---

### Post by Some Penguin on 2010-04-22
RSS ain't valid HTML, and vice versa.

Personally, I'd probably use Java for the crawler, perhaps within a servlet to facilitate monitoring and control, having it dump content somewhere; then perhaps Java (likely) or Perl (possibly) to do the processing of crawled pages; and probably a JSP/servlet combination to service the front end.  All the servlets sit on Apache Tomcat.  Relevant libraries abound (rome for RSS, for instance; Apache httpclient-4.0 isn't complete crap, although the dev team apparently can't be bothered to write reasonable or accurate documentation;  plenty of XML parsers for more low-level RSS work; quite a few HTML DOM extractors as well) and you get to learn more when you notice that the authors of JDBC connection pools aren't interested in following even simple JDBC specifications and other fun.

Choice of data store really depends on what you want from it.  Pure key-value stores for instance  have a gazillion options, but you might find yourself making use of a SQL db's capabilities.  Tokyo Cabinet's nifty in some ways, MySQL is fairly friendly, Postgresql is capable as well.

---

### Post by ja660k on 2010-04-22
+1 
for the use of perl.
maybe even python, i know it has alot of modules for reading html, parsing have a look at:
[http://docs.python.org/c-api/](http://docs.python.org/c-api/)

But the 1337 people do it in perl.
GoodLuck

---

### Post by slavik on 2010-04-22
use rss where you can if applicable, crawl html otherwise.

html is much easier to change that breaks your code than rss.

---

### Post by Cracauer on 2010-04-22
The way to pick a language for a specific task like this is to study the available libraries. In this case the html parsing helpers. Then pick the language which has the best library.

---

### Post by slavik on 2010-04-22
dump the html into this and then use an rss reader.

[http://search.cpan.org/~bashi/XML-RSS-FromHTML-0.05/lib/XML/RSS/FromHTML.pm](http://search.cpan.org/~bashi/XML-RSS-FromHTML-0.05/lib/XML/RSS/FromHTML.pm)

---

### Post by Aped on 2010-04-24
Thanks for the help guys, I feel like I'll be using two perl scripts (one to crawl html and save data to a DB, and one cgi to deliver that DB content as a webpage). Thanks so much to everyone who's opined here. It's going to be a cool project, I'll post here in a few years when/if I finish it :3

---

