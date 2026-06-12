---
title: "Need help!!! Car manufacturer and model database."
date: 2007-03-08
forum: Programming Talk
---

### Post by cunawarit on 2007-03-08
I am working on website and I need to develop a form to collect car information, websites like [www.autotrader.co.uk](www.autotrader.co.uk) have forms with DropDownLists that allow you to select a car manufacturer and a model, I want something like that.

Are there any publicly available databases to do this? I have limited funds, so free or very cheap would be good!!!!

PS: I am interested in a British specific car data.

---

### Post by phossal on 2007-03-08
The cheap database to use is MySQL. You can't get much cheaper than free. You actually want the data though? Maybe *ask* the webmasters of those sites if they'll a) share theirs, or b) will tell you whether or not they compiled their own. I suspect they did. Good luck.

---

### Post by laxmanb on 2007-03-09
Information is money these days. Don't expect them to part with it anytime soon...

but you have Wikipedia, which keeps track of all the Manufacturers and their models... why don't you build your own DB?? It can't be too much work...

---

### Post by cunawarit on 2007-03-09
> The cheap database to use is MySQL. You can't get much cheaper than free.

I'll be using MySQL, but the website will be running on a Windows 2003 box with SQL Server in it anyway... I'll use MySQL because I may want to run the DB in a Linux box in the future.  

> You actually want the data though? Maybe *ask* the webmasters of those sites if they'll a) share theirs

I have, no luck so far...

> but you have Wikipedia, which keeps track of all the Manufacturers and their models...

It isn't very country specific or accurate. I have obtained a list of all car models for the last two years from the department of transport. However, what I need is a list for the last 20 to 25 years.

---

### Post by pmasiar on 2007-03-09
> **cunawarit said:**
> (wikipedia) isn't very country specific or accurate. I have obtained a list of all car models for the last two years from the department of transport. However, what I need is a list for the last 20 to 25 years.

Wikipedia is as accurate as it's users care for. Every inaccuaracy is a bug, and anyone can fix it, including you. Same as free software - don't whine, do something about it.

If you will yourself forced to create your own databse, you can do it in wiki spirit: set up a wiki somewhere, open it for editing by other people who care about the issue. You may set up some screening process before allowing people to edit it - but any screening will mean less contributors, not more. 

There are many wikifarms where you can get own wiki website for free - I use [http://www.pbwiki.com](http://www.pbwiki.com) and I like it. Make sure you disable GUI editor - that way, pages will be plain text with simple markup, easier to parse and use as fundament to your car database. You can get basic wiki for free, and paid upgrade adds you loads of features.

---

### Post by cunawarit on 2007-03-09
> **pmasiar said:**
> Wikipedia is as accurate as it's users care for. Every inaccuaracy is a bug, and anyone can fix it, including you. Same as free software - don't whine, do something about it.

erm... whatever.... I already contribute to it plenty.

---

### Post by phossal on 2007-03-09
Why not get users of your site to contribute? Depending on what information/service you're providing, try to do so for the limited data you have, and then begin compiling more and more as users submit manufacturer's models. Build your data *from* your users, which will make it more consistent with what they need anyway.

---

### Post by cunawarit on 2007-03-09
phossal, sounds like a good idea in the long run. 

I think that is what Autotrader does, whenever someone submits a new car for sale it goes into the database. I am guessing, but I think that's why you get all the popular cars and a few truly odd ones.

---

### Post by pmasiar on 2007-03-09
> **cunawarit said:**
> erm... whatever.... I already contribute to it plenty.

Usually people who know they can edit pages and contribute do not complain about inaccuracies - if they see them, they fix them. Sorry for misunderstanding.

If you understand the wiki way, you should be more open gathering your data by group effort using wiki (if you will not get the data from someone, for free). If your pages are stored in wiki markup (with minimal formatting), downloading whole wiki as text files and parsing them to check for format/other structure elements is rather simple. So you avoid efforts to build web-based front-end to create/categorize data. Just an idea.

---

### Post by drubin on 2008-12-22
> **jaypeg said:**
> here is a free one, the source on the autotrader website is clearly visible, just parse it into a format you want...

[http://www.niautotrader.co.uk/templates/autotrader-ni-v2/_make_model.js](http://www.niautotrader.co.uk/templates/autotrader-ni-v2/_make_model.js)

Not sure the legality of coping their javascript... very questionable limits here.

---

### Post by Elfy on 2009-06-23
Thread closed - this is over 2 years old. Start again if you so wish.

---

