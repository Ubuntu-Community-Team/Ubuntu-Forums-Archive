---
title: "Search Engine for Firefox that searches Ubuntuforums.org via Google"
date: 2007-01-05
forum: Outdated Tutorials &amp; Tips
---

### Post by kEinstein on 2007-01-05
Hi there!! 
I have found some time to put a little thingy together :D

[SIZE="4"]**[Search Engine]("http://austrian.n3rds.net/uploads/googleubuntu2.tar.gz") for Firefox to search Ubuntuforums.org via Google**[/SIZE]

Q: What does it do?
A: It uses Google to search Ubuntuforums.org via implementing a search engine in Firefox. The idea to use 'site:[http://ubuntuforums.org](http://ubuntuforums.org) foo' to search entries has been initiated by 23meg after a [small debate]("http://www.ubuntuforums.org/showthread.php?t=331483") on the 15 sec. time limit when performing searches via the searchbar. 

Q: Why should I use it?
A1: You might want to relief ubuntuforums' server load!
A2: You might want to perform searches without the 15 second limit for whatever reason.

Q: Can I have the code?
A: Of course. Feel free to make changes, improvements or whatever.

Q: Can I customize the plugin to perform searches on other sites?
A: Of course!!! Do the trick by substituting the 'www.ubuntuforums.org' to 'whatsoeverURL' in line 18.


The plugin is available here:
[SIZE="3"][Search Engine]("http://austrian.n3rds.net/uploads/googleubuntu2.tar.gz") for Firefox
[/SIZE]

As **sudo**, simply untar the content to the following location...
```
/usr/share/firefox/searchplugins
```
... restart Firefox and start using the search engine in the upper right corner (by default)


The archive includes a code 'googleubuntu.src' and a small image 'googleubuntu.gif' to make it look neat.




EDIT: (22-Jan-06) I have updated the source code, [see here for recent changes]("http://ubuntuforums.org/showthread.php?p=2050171#post2050171").




Cheers!
Hope you enjoy it!

PS: I have tested it using Firefox 2.0.0.1 - I hope it works for you too!

---

### Post by raul_ on 2007-01-05
It works! (i already knew but it's always good to have feedback) :rolleyes:

---

### Post by kEinstein on 2007-01-05
Thanks again! Honestly, the most challenging thing about this plugin has been my absolute 'inexperience' with gimp... Putting the two images together, using transparency, 2 layers :rolleyes: and 'Scale Image' was definitively a challenge.

---

### Post by kEinstein on 2007-01-05
Admittedly, there is one minor draw-back when using this search extension via Google.
Performing a search with 'site:URL foo' yields accurate results for content that has been posted up to a couple of hours ago. In case you are searching very recent entries (some seconds/minutes/hours) Google might not find them. Your search results depend on Google's cache timing - once the relevant forum entries are cached you'll find them instantly via the search plugin. In fact, the same applies to every single query you make via Google directly. If you know that an entry is somewhere out there but can't find it, comfort yourself - Google didn't know it either... 
Anyway, using this search engine will enable you to find appropriate matches to your queries. In the rare case you can't find a very recent match you are best off with Ubuntuforums' search bar.

---

### Post by stalefries on 2007-01-05
What's really saddening is that simple tutorials like this one will probably end 
up at the bottom of the heap, because they won't be bumped up by people with questions.

---

### Post by kEinstein on 2007-01-06
There is some fruitful input from a [thread]("http://ubuntuforums.org/showthread.php?p=1974205") about the appropriateness of the search time limit:
Of course, writing a plugin is one method to search the forums using google's cache. Another - yet simpler - way to perform a search can be implemented via making a shortcut in your browser's location bar.

See [po0f's post here]("http://ubuntuforums.org/showthread.php?p=1974205#post1974205")!

---

### Post by petermck on 2007-01-06
Cool. I like it. Thanks.

---

### Post by matthew on 2007-01-06
> **kEinstein said:**
> Hi there!! 
I have found some time to put a little thingy together :D:KS You rock! :KS
Thanks for contributing to the community. Your efforts are greatly appreciated. I love it when people find a way to help others and solve problems.

---

### Post by Buck2348 on 2007-01-06
Great job, kEinstein.  I've been missing a feature I had in Internet Explorer on the Yahoo toolbar:  an option to search only the site I happen to be on.  I'm reluctant to install more toolbars just for one feature because they take up space.  I'll bet you could make us a plugin to do that in about 10 minutes.

Cheers,
Buck

---

### Post by kEinstein on 2007-01-07
> **matthew said:**
> Thanks for contributing to the community. Your efforts are greatly appreciated. I love it when people find a way to help others and solve problems.

Thanks for the laurels! :redface: There has been so much proactive and fruitful input - putting a few lines of code together was just a logical consequence. Furthermore, it's an opportunity to give at least something back to the community.
Helping hands all over, great guides and informative threads - THAT's ubuntu in its veritable meaning. 

Therefore, kudos to ubuntuforums.org


:KS  Keep rockin'!  :KS

---

### Post by kEinstein on 2007-01-07
@ Buck: you definitley overestimated my programming skills... I've had some thoughts about your request, but unfortunately I have no straightforward solution at hand. IMHO the only thing you would need to find out is how to read the current domain name from within Firefox. Sounds fairly simple. I suggest, you might either raise a request in a separate thread or post in a Firefox/Mozilla forum. Unfortunately, Google & searching the Mozilla extensions didn't yield any appropriate results in my case.

 Anyway, please post your results in this thread - or paste a link to the solution!

---

### Post by Henry Rayker on 2007-01-07
Couldn't you solve this in a slightly different way by just right clicking the "search" field and selecting "Add Keyword to this search"? I mean...this way, you could set "Ubuntu" as the keyword and anytime you type "Ubuntu [Phrase]" in the location bar, it would search the forums.

It could just be that I don't like the search bar, though...I know some people LOVE it. I should keep quiet.

---

### Post by userundefine on 2007-01-07
> **Henry Rayker said:**
> Couldn't you solve this in a slightly different way by just right clicking the "search" field and selecting "Add Keyword to this search"? I mean...this way, you could set "Ubuntu" as the keyword and anytime you type "Ubuntu [Phrase]" in the location bar, it would search the forums.

It could just be that I don't like the search bar, though...I know some people LOVE it. I should keep quiet.
Yes, and that's my preferred method.  I don't like the searchbar because you can do it without a mouse/with fewer keystrokes from the URL bar (I've actually removed it from the UI).

To do this in the URL bar, add a new Bookmark with this as your URL:
> [http://www.google.com/search?q=%s](http://www.google.com/search?q=%s) site:ubuntuforums.org
Then add a keyword for it.  My keyword is "**gu**".  So, when I want to do this search, I hit Ctr+L to get to the URL bar, and then type "gu *search criterion*".

---

### Post by lukew on 2007-01-09
I saw this and it reminded me of this page....


[http://www.ubuntuforums.org/showthread.php?t=139996&highlight=firefox+search](http://www.ubuntuforums.org/showthread.php?t=139996&highlight=firefox+search)

---

### Post by aktiwers on 2007-01-09
Thanks worked great!! :)

---

### Post by kEinstein on 2007-01-09
Hi, I remember heaving read this thread a couple of days ago and heard of UDSF for the first time... What about UDSF at the moment? [http://doc.gwos.org/](http://doc.gwos.org/) does not work or am I doing sthg wrong? Also the search engine for UDSF fails...
Does someone know what happened here?

---

### Post by lukew on 2007-01-10
> **kEinstein said:**
> Hi, I remember heaving read this thread a couple of days ago and heard of UDSF for the first time... What about UDSF at the moment? [http://doc.gwos.org/](http://doc.gwos.org/) does not work or am I doing sthg wrong? Also the search engine for UDSF fails...
Does someone know what happened here?

Looks like it is down. This forum is incredible slow as I am typing this.......

Luke

---

### Post by lukew on 2007-01-10
> **kEinstein said:**
> Hi, I remember heaving read this thread a couple of days ago and heard of UDSF for the first time... What about UDSF at the moment? [http://doc.gwos.org/](http://doc.gwos.org/) does not work or am I doing sthg wrong? Also the search engine for UDSF fails...
Does someone know what happened here?

Hi,

Does work but very slow!!

Luke

---

### Post by kEinstein on 2007-01-22
Hi there!

Made some changes to the code which make the search bar look a bit nicer ;-)

```
# Firefox plugin file
#
# Google | Ubuntuforums.org search
# by kEinstein 
#
# Last updated: January 22, 2007

<search 
	name="Google | Ubuntuforums.org"
	description="Search Ubuntuforums.org with Google"
	action="http://www.google.com/search"
	searchForm="http://www.ubuntuforums.org/"
	queryEncoding="utf-8"
	queryCharset="utf-8"
	method="GET"
>

<input name="hl" value="en&domains=www.ubuntuforums.org">
<input name="btnG" value="Search&sitesearch=www.ubuntuforums.org">
<input name="q" user="">

</search>

```

You will be able to obersve that the "site:URL" string does no longer pop up in the Google search bar. Instead you will be given the option to either search "the Web" or "www.ubuntuforums.org".

I uploaded the latest version of the search engine to the [same link as before]("http://austrian.n3rds.net/uploads/googleubuntu2.tar.gz").

[IMG]http://austrian.n3rds.net/uploads/new_plugin.png[/IMG]

---

### Post by jake3988 on 2007-01-27
This is neat.

But... are you too lazy to type _My search words site:[www.ubuntuforums.org](www.ubuntuforums.org)_ at the google prompt?  :)

---

### Post by raul_ on 2007-01-27
Or we're too lazy to load google, type all that crap and then the crap we want to search for =) That's what the search bar is there for. you could always load the site and search from there. The Wikipedia search bar, for example, is really handy.

---

### Post by ShirishAg75 on 2008-03-16
Pardon me but why isn't this search engine posted at http:// addons.mozilla.org would make it great for ubuntu domination over the world ;)

---

