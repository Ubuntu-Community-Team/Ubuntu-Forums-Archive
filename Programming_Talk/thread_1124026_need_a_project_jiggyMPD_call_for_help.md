---
title: "need a project? jiggyMPD call for help"
date: 2009-04-12
forum: Programming Talk
---

### Post by DocForbin on 2009-04-12
I've seen a few requests lately asking for projects to join, so thought I would use that as an opportunity to plug my project ;)

I really could use some help. And it's a fun little project :)

[http://bitbucket.org/cubiczee/jiggympd](http://bitbucket.org/cubiczee/jiggympd)

---

### Post by myrtle1908 on 2009-04-14
I could possibly assist with slapping a nicer front-end on the thing.  I would use ExtJS and require data be shipped in JSON format.

For example, it would be fairly trivial to make the screen @ [http://img217.imageshack.us/img217/3505/jiggy5.png](http://img217.imageshack.us/img217/3505/jiggy5.png) look alot better with the use of a decent UI kit like Ext.

All depends on your target audience and whether your product is open source etc.

I've been using Ext since it's inception.  I've attached a screenshot of some of the work I do with it.

My time is scarce but would be willing to assist even if in a minor capacity.

Good Luck.

---

### Post by yoasif on 2009-04-14
[don't use extjs]("http://pablotron.org/?cid=1556").

---

### Post by myrtle1908 on 2009-04-14
> **yoasif said:**
> [don't use extjs]("http://pablotron.org/?cid=1556").

Here we go.  Another buffoon touting ridiculous statements.

Are you aware that Ext recently released Ext Core which is MIT open source?  Are you aware that the commercial licence is relatively cheap (<300USD)?  Did you know that their support forums are outstanding and that their API documentation is second to none?  Do you know how extensible Ext is?  How slick their API is?  Have a look at the source code, it is genius.

Show me a toolkit that comes even close.  Don't even think about mentioning JQuery ... whilst very good in its own right it doesn't offer even half of what Ext does (especially Widget wise).

The beauty of Ext is that its development is managed and scrutinized by a very small bunch of extremely intelligent people.  With this, cleanliness, continuity, and ease of use are ensured.

No, I do not work for Ext nor am I affiliated with them in any way.

---

### Post by yoasif on 2009-04-14
was not aware of the new version, but it's not as if you said ext core, you said extjs. 

as far as their code being genius, i copied and pasted this from another site, feel free to refute it though. 

> I didn&#8217;t so much miss the point as I just neglected to mention it in my article, so perhaps I&#8217;ll add it in and I realize not everything can be tested for (document.execCommand(backgroundImageCache)).

But what features or performance related implementations are you eluding to? I think you&#8217;ll find many reliable tests here [http://yura.thinkweb2.com/cft/](http://yura.thinkweb2.com/cft/). And just look at what jQuery did with version 1.3 - the features they were able to detect. And it isn&#8217;t just detecting features but working around them such as with jQuery&#8217;s ready function.

It isn&#8217;t an elegant solution, but it&#8217;s a solution none the less. The fact of the matter is ExtJS doesn&#8217;t even try, electing instead for the quick shortcut. In my book that is of far greater concern than performance, **all it took was an upgrade to one of their &#8220;supported browsers&#8221; to learn that lesson**.[http://ajaxian.com/archives/ext-core-released-as-mit-library](http://ajaxian.com/archives/ext-core-released-as-mit-library)

---

### Post by myrtle1908 on 2009-04-14
I'm not sure what your point is.  I am aware of the discussions at Ajaxian and have read the posts you are referring to.

What I mean by "genius" is the way Ext Component Model was put together in v2 and the great amount of thought that has gone into its development.  I am yet to find a better toolkit for web application development.  Note that I say "application", not be confused with your average website which needs a tree or a grid here and there.  Obviously this is my personal opinion and I'm certainly not trying to force anything upon anybody.

Thread has probably gone way of topic.  Apologies to the OP.

---

### Post by DocForbin on 2009-04-14
It doesn't really matter. I'm using mootools, and it would be more work for me than help to change js frameworks for the sake of ui improvements (that are very much needed though).

---

### Post by DocForbin on 2009-04-14
p.s. is it just me or does everyone seem to want their apps to look like outlook these days

---

### Post by yoasif on 2009-04-14
for what it's worth, i thought the screenshots that myrtle1908 posted looked horrific, and i thought the way your design looked already looked better than what he had done. 

it looks like a pretty neat project, i need to set up mpd again so i can play with it... any chance we'll see a ppa/deb anytime soon? that would probably increase the uptake as people can try it out and perhaps decide to get involved.

---

### Post by DocForbin on 2009-04-15
> **yoasif said:**
> for what it's worth, i thought the screenshots that myrtle1908 posted looked horrific, and i thought the way your design looked already looked better than what he had done. 

it looks like a pretty neat project, i need to set up mpd again so i can play with it... any chance we'll see a ppa/deb anytime soon? that would probably increase the uptake as people can try it out and perhaps decide to get involved.

thanks for the input yoasif. If you have probs or otherwise need any help getting it setup for now, feel free to pm me or just post here.

---

### Post by DocForbin on 2009-04-15
if it helps. this is off the top of my head :)

sudo apt-get install mercurial
hg clone [https://cubiczee@bitbucket.org/cubiczee/jiggympd/](https://cubiczee@bitbucket.org/cubiczee/jiggympd/) jiggyMPD
sudo mv jiggyMPD/jiggyMPD-Web /var/www (your web root)
edit var/www/Config/config/php if needed

if you want to use the tray icon without compiling you can grab a jar from google code linked to in the project page. Then run with java -jar tray.jar.

There are some more install notes on the project page.

---

### Post by myrtle1908 on 2009-04-15
> **DocForbin said:**
> p.s. is it just me or does everyone seem to want their apps to look like outlook these days

Unfortunately, in the corporate world, yes.

---

### Post by myrtle1908 on 2009-04-15
> **yoasif said:**
> for what it's worth, i thought the screenshots that myrtle1908 posted looked horrific, and i thought the way your design looked already looked better than what he had done.

Fair enough.  It is not to everyone's taste.  Our clients seems to like it however.  Also, it is a test system with rubbish data, fields, layout, theme etc.

---

### Post by DocForbin on 2009-04-18
I'm now bundling an executable jar in the dist folder of desktop to make it easier to try out the tray.

Made a bunch of commits today, including lyrics support :)

---

### Post by samfuzz on 2010-10-10
i'm trying, to use jiggy mpd, but i've only a blank page,

how to do ?

---

