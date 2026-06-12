---
title: "urllib2 Woes"
date: 2007-11-02
forum: Programming Talk
---

### Post by ankursethi on 2007-11-02
I mentioned before that indexer I'm building in Python. Well, I've run into a problem.

A function getPage() gets the (plain text) page the URL of which I pass to it. That works fine and dandy, but what if I simply pass "http://www.google.com"? It then has no idea about the filename it must use to store the page and hence the script breaks.

The reason for this is that I'm using a regex to remove the "http://www." from the URL and then using the functions from os.path to find out the file and directory names respectively. Since "http://www.google.com" does not mention a file name at the end, the file name becomes blank. That raises an error.

Now, I found out that typing "http://www.google.com" in my browser redirects me to "http://www.google.co.in" (something which urllib handles gracefully). The page on the server has the name "index.html". How on Earth can I find the *actual* URL of the *page* I have opened? Can I examine the HTTP headers to find that out?

I've hit a wall here. Many URLs floating around the web simply point to a particular website's base URL, not to a particular page. This limits me to crawling one website at a time, since my script would be unable to follow any external URLs.

Yelp!

---

### Post by skeeterbug on 2007-11-02
> **ankursethi said:**
> I mentioned before that indexer I'm building in Python. Well, I've run into a problem.

A function getPage() gets the (plain text) page the URL of which I pass to it. That works fine and dandy, but what if I simply pass "http://www.google.com"? It then has no idea about the filename it must use to store the page and hence the script breaks.

The reason for this is that I'm using a regex to remove the "http://www." from the URL and then using the functions from os.path to find out the file and directory names respectively. Since "http://www.google.com" does not mention a file name at the end, the file name becomes blank. That raises an error.

Now, I found out that typing "http://www.google.com" in my browser redirects me to "http://www.google.co.in" (something which urllib handles gracefully). The page on the server has the name "index.html". How on Earth can I find the *actual* URL of the *page* I have opened? Can I examine the HTTP headers to find that out?

I've hit a wall here. Many URLs floating around the web simply point to a particular website's base URL, not to a particular page. This limits me to crawling one website at a time, since my script would be unable to follow any external URLs.

Yelp!


I guess I am confused about what you are trying to do. Are you trying to save a http request to a local file, using the end of the extension on the URL as a file name correlation? If so, you are going to run into many problems with all kinds of sites that don't use common extensions (Django and Ruby on Rails don't use extensions at all). Maybe using the domain name is a better idea.

Think of this table relationship:

|Table Sites|
ID| Name
1 | google.com

|Table Site_Index|
Site_ID | other columns

Then you can go back and pull up all the pages your indexer crawled for a given site. You could always go with SQLite and not have to worry about installing a server.

---

### Post by ankursethi on 2007-11-03
Nope. You really don't get me.

See, I extract a link from the page that says "http://www.reallydandywebsite.com/reallydandyfolder/reallydandypage.html". Then I knock off the "http://www" off using a regular expression. Then I use functions from os.path to extract the directory name (which in this case would be reallydandywebsite.com/reallydandyfolder) and the filename (which would be reallydandypage.html).

Now, if I pass in "http://www.google.com", urllib will open the page "index.html" that resides somewhere on Google's servers. But how the heck am I supposed to know that it opened index.html? For all os.path cares, there is no file name after "google.com/". It's just a directory name. So the filename becomes blank, and I cannot save the page.

Anyway, I found a way around the problem. If the filename is blank, I'll simply ignore that particular page and move on to other pages that are linked to it. At least ONE other page is bound to contain references to the nameless page. Problem (sort of) solved.

(I still don't think I'm getting across very well, but that's because teh Interweb iz brokenn!)

---

### Post by ankursethi on 2007-11-03
All right! I found a better way to do the above using the urlparse module which, it turns out, is hidden inside urllib2 itself.

That is not to say that further comments are not welcome.

---

