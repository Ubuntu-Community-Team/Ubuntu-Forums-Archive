---
title: "how do I keep urls up to date - without Dreamwaever?"
date: 2007-12-29
forum: Programming Talk
---

### Post by ICEcoffee on 2007-12-29
Hi all. I've stopped using Dreamweaver since switching to Ubuntu Linux and I have found two reasonable replacements: Quanta Plus and Aptana, but none have an automatic URL manager, so if I change the name of a link, rename or delete a file, any link that has a reference to it, will be automatically updated. I've never had to worry about managing links before. 

So I need to know how all you hardcore web developers manage? what do you do or use to make sure you don't run into any problems?

---

### Post by Ramses de Norre on 2007-12-30
Change it with sed? If you change *home.html* to *home2.html* you can run this on all your files:

```
sed -i -e 's/home.html/home2.html/g' *.html
```

You can tweak the regexp to your needs.

---

### Post by LaRoza on 2007-12-30
> **ICEcoffee said:**
> Hi all. I've stopped using Dreamweaver since switching to Ubuntu Linux and I have found two reasonable replacements: Quanta Plus and Aptana, but none have an automatic URL manager, so if I change the name of a link, rename or delete a file, any link that has a reference to it, will be automatically updated. I've never had to worry about managing links before. 

So I need to know how all you hardcore web developers manage? what do you do or use to make sure you don't run into any problems?

I use a PHP framework that I wrote, that avoids this issue.

I only have to manage one file, and the URI's stay the same.

I wouldn't say I am hardcore, and none of my sites are large.

---

### Post by ICEcoffee on 2007-12-30
> I use a PHP framework that I wrote, that avoids this issue.

I only have to manage one file, and the URI's stay the same.


Can you explain what this framework does, how does it work? is it easier than the other post's suggested command: 
> sed -i -e 's/home.html/home2.html/g' *.html

---

### Post by LaRoza on 2007-12-31
Basically, I create a PHP object (it will work in any client side language) that is a WebPage.

See [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home)

View the URI for each page, and you will see that the actuall document doesn't change.

The code for each "page" is actually a single file that just has the unique content on it and the content is loaded depending on the query string.

All common elements are part of the PHP and the links (on the side and top) are in an array. The code to write those links is part of the PHP object.

[php]
$page->writeLinks($links);
[/php]

Where $page is the object that is the web page, and $links is an array of the page available. I use other methods for writing the links also, like writeBottomLinks() and writeTopLinks().

All I have to do is keep the array up to date and every page.

Also, each page file (with the content) has the same name as the query string given.

This works best for small pages and if you alread know what you want. I could make the objects more complicated and have many page layouts automatically available, but at the moment, I just have the one.

It is not my intention to make a framework for general use (yet).

---

### Post by ICEcoffee on 2007-12-31
Are there any other methods or is PHP/Mysql (and similar) the only sensible solution, to URL management?

---

### Post by evymetal on 2008-01-03
Not sure why you would ever want to change the url to a document without redirecting to the new page (google "javascript redirect" or "301 redirect"), but here are my thoughts:

For "small" sites (1-20 pages), sed is probably the best option . Using Templates is a good method too. i.e. for navigation links have a section in your code:

[HTML]
<!--- BEGIN NAVIGATION --->
<bla></bla>
<!--- END NAVIGATION --->
[/HTML]

Then when you change your navigation, just copy the whole block between the comments over between files.

If it is for a list of "recent changes" etc, I would use server side includes (google them), or a script of some kind (you could write the list into the page with javascript).

For "medium" sites (20-1,000 pages) you are probably going to be using some kind of CMS (content management system) like wordpress / zope with plone / turbogears etc. This kind of handles most of this for you (or does not change urls)

For "Large" sites (1000 - 1 million) you would normally have your own backend system, and you would think about this problem when designing it, same for even larger sites.

---

### Post by ICEcoffee on 2008-01-03
Thanks evyMetal (cool user name), for taking the time for adding the helpful info in your post.

I always thought that with site sizes (as you describe them) more than 200+, even the mighty Dreamweaver template and URL manager/updater (recent versions only), is going to struggle.

The only way I could see managing URL's for larger sites is via a script and database to manage URL's, which is what most CMS's do anyway.

I might have a bash at building a generic one for myself, and add it to my library.

---

