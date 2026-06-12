---
title: "[SOLVED] Php SimpleXMLElement()"
date: 2008-11-14
forum: Programming Talk
---

### Post by Dr Small on 2008-11-14
Greetings, I am messing around with extracting different stuff from both Atom and RSS feeds, and have got it mostly figured out, but have this one problem when attempting with Atom.

I'll give you some examples of what I am trying to do, and then maybe you can help me.

I have this XML:
```
<entry>
		<author>
			<name>K.Mandla</name>
						<uri>http://kmandla.wordpress.com/</uri>
					</author>
		<title type="html"><![CDATA[Internet Explorer balks at Firefox download link]]></title>
		<link rel="alternate" type="text/html" href="http://kmandla.wordpress.com/2008/11/13/internet-explorer-balks-at-firefox-download-link/" />
		<id>http://kmandla.wordpress.com/?p=2041</id>
		<updated>2008-11-13T11:15:25Z</updated>
		<published>2008-11-13T11:15:25Z</published>
		<category scheme="http://kmandla.wordpress.com" term="Arch Linux" /><category scheme="http://kmandla.wordpress.com" term="Linux" /><category scheme="http://kmandla.wordpress.com" term="Ubuntu" />		<summary type="html"><![CDATA[This is amusing to me; I&#8217;m sure there&#8217;s a very good, very rational reason for this issue and I&#8217;m probably just not sharp enough to catch it.
But on a clean installation of Windows XP (don&#8217;t ask; it&#8217;s a long story), Internet Explorer 6 claims there&#8217;s an error on the GetFirefox.com download page, and refuses to [...]]]></summary>
		<content type="html" xml:base="http://kmandla.wordpress.com/2008/11/13/internet-explorer-balks-at-firefox-download-link/"><![CDATA[<div class='snap_preview'><br /><p>This is amusing to me; I&#8217;m sure there&#8217;s a very good, very rational reason for this issue and I&#8217;m probably just not sharp enough to catch it.</p>

<p>But on a clean installation of Windows XP (don&#8217;t ask; it&#8217;s a long story), Internet Explorer 6 claims there&#8217;s an error on the GetFirefox.com download page, and refuses to allow a click on the download button.</p>
<p>A screenshot is the best I can do here, since I don&#8217;t really have any other way of proving it won&#8217;t work. I restarted IE and tried twice, but both times I get a supposed &#8220;error report&#8221; for that page (see the bottom left of the IE status bar) and double-clicking that gives the error report on the upper right. The pointer does not turn into a &#8220;hand&#8221; anywhere near the giant green download button.</p>
<p>I&#8217;ve highlighted and put a red oval around the offending &#8220;line 190&#8243; from the page source.</p>

<p align="center"><a href="http://xs.to/xs.php?h=xs233&amp;d=08464&amp;f=line-190-943.jpg" target="_blank"><img src="http://xs233.xs.to/xs233/08464/line-190-943.jpg.xs.jpg" /></a></p>
<p>If there&#8217;s an error in that line, I don&#8217;t know enough Web code to see it. Somebody smarter please clue me in.</p>
<p>For the record, that&#8217;s a fresh SP2 installation from a legitimate disc, and I haven&#8217;t done any upgrades except for the first round, as was suggested by the update notifier &#8230; or whatever Microsoft is calling it these days. It would be ironic if the first thing that little yellow shield did was hard-code IE to ignore the GetFirefox page. Of course, I wouldn&#8217;t put it past them.</p>

<p>I could still follow the links to the interior of the site and download it from the list of language selections. And yes, the same page with the same code at the same line works fine in Firefox, of course.</p>
<p>I will admit it gave me a laugh for a second though. </p>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<a rel="nofollow" href="http://feeds.wordpress.com/1.0/gocomments/kmandla.wordpress.com/2041/"><img alt="" border="0" src="http://feeds.wordpress.com/1.0/comments/kmandla.wordpress.com/2041/" /></a> <a rel="nofollow" href="http://feeds.wordpress.com/1.0/godelicious/kmandla.wordpress.com/2041/"><img alt="" border="0" src="http://feeds.wordpress.com/1.0/delicious/kmandla.wordpress.com/2041/" /></a> <a rel="nofollow" href="http://feeds.wordpress.com/1.0/gostumble/kmandla.wordpress.com/2041/"><img alt="" border="0" src="http://feeds.wordpress.com/1.0/stumble/kmandla.wordpress.com/2041/" /></a> <a rel="nofollow" href="http://feeds.wordpress.com/1.0/godigg/kmandla.wordpress.com/2041/"><img alt="" border="0" src="http://feeds.wordpress.com/1.0/digg/kmandla.wordpress.com/2041/" /></a> <a rel="nofollow" href="http://feeds.wordpress.com/1.0/goreddit/kmandla.wordpress.com/2041/"><img alt="" border="0" src="http://feeds.wordpress.com/1.0/reddit/kmandla.wordpress.com/2041/" /></a> <img alt="" border="0" src="http://stats.wordpress.com/b.gif?host=kmandla.wordpress.com&blog=353512&post=2041&subd=kmandla&ref=&feed=1" /></div>]]></content>
		**<link rel="replies" type="text/html" href="http://kmandla.wordpress.com/2008/11/13/internet-explorer-balks-at-firefox-download-link/#comments" thr:count="11"/>**
		<link rel="replies" type="application/atom+xml" href="http://kmandla.wordpress.com/2008/11/13/internet-explorer-balks-at-firefox-download-link/feed/atom/" thr:count="11"/>
		<thr:total>11</thr:total>
	</entry>
```

I want to extract the part from the XML which is in **bold**. If I try the following, I extract the first <link>, but since Atom names it's objects the same, I am finding it difficult to get the comments link.
[php]$link        = (string)$item->link['href'];[/php]

Of course, that is just taking the first <link> and echoing it on the page. Is there any way to do what I want to do?

Dr Small

---

### Post by drubin on 2008-11-15
RSS readers are very specialized xml readers much the same with html. I would recommend using a RSS/Atom reader for this. :)

Here is the one I would use.
[http://magpierss.sourceforge.net/](http://magpierss.sourceforge.net/)
[http://www.scriptol.com/rss/rss-reader.php](http://www.scriptol.com/rss/rss-reader.php)

I will take a look at your problem with the xml reader though and get back to you.

---

### Post by drubin on 2008-11-15
> **Dr Small said:**
> Greetings, I am messing around with extracting different stuff from both Atom and RSS feeds, and have got it mostly figured out, but have this one problem when attempting with Atom.

I'll give you some examples of what I am trying to do, and then maybe you can help me.

I have this XML:
```
		**<link rel="replies" type="text/html" href="http://kmandla.wordpress.com/2008/11/13/internet-explorer-balks-at-firefox-download-link/#comments" thr:count="11"/>**
		<link rel="replies" type="application/atom+xml" href="http://kmandla.wordpress.com/2008/11/13/internet-explorer-balks-at-firefox-download-link/feed/atom/" thr:count="11"/>
		<thr:total>11</thr:total>
	</entry>
```

[php]$link        = (string)$item->link['href'];[/php]

Try this.
[http://www.php.net/simplexml-element-attributes#73811](http://www.php.net/simplexml-element-attributes#73811)

You bassically need to get an array of links; or maybe $item->next();
If these don't work I will take a closer look later for you.

---

### Post by Dr Small on 2008-11-15
> **drubin said:**
> Try this.
[http://www.php.net/simplexml-element-attributes#73811](http://www.php.net/simplexml-element-attributes#73811)

You bassically need to get an array of links; or maybe $item->next();
If these don't work I will take a closer look later for you.
Since I was already in a foreach() loop, I just went ahead and changed it to:
[php]$link        = (string)$item->link[1]['href'];[/php]

And it worked perfectly, as expected. It's generally the simple things that nag and trip me up for awhile. Thanks for responding and sending me to those links, drubin. Problem Resolved :)

Basically, I am writing my own RSS/Atom reader and working on it from there. I guess I am reinventing the wheel, by not using magpierss, but hey, I like to learn the inner workings of the engine to see how the wheel spins :D

---

### Post by drubin on 2008-11-15
> **Dr Small said:**
> Since I was already in a foreach() loop, I just went ahead and changed it to:
[php]$link        = (string)$item->link[1]['href'];[/php]

And it worked perfectly, as expected. It's generally the simple things that nag and trip me up for awhile. Thanks for responding and sending me to those links, drubin. Problem Resolved :)
Glad it worked and it is always the simple things that mess us up :)

> **Dr Small said:**
> 
Basically, I am writing my own RSS/Atom reader and working on it from there. I guess I am reinventing the wheel, by not using magpierss, but hey, I like to learn the inner workings of the engine to see how the wheel spins :D
"I would re-invent the wheel 100 times over if it meant I would learn some thing from it." (Not my quote but very appropriate)

---

