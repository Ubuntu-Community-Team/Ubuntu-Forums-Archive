---
title: "XML/XSL for a beginner"
date: 2007-09-25
forum: Programming Talk
---

### Post by DouglasAWh on 2007-09-25
After much beating of head against wall, I've gotten fairly comfortable moving stuff around in an XSL file and know where that content is going to go in an XML file, as long as those things are direct decendents of the tag I'm in.  I need to do decendents of those tags though.  I'm using oXygen XML editor, but I don't understand the "descendant-or-self::" autofill that they offer.  If I put a "." where I want this item to go, the entire entry will show up, including HTML tags that are being parsed as HTML.  If I put a / the entire document shows up for each list item.  

I've been looking at [http://www.zvon.org/xxl/XSLTutorial/Output/contents.html](http://www.zvon.org/xxl/XSLTutorial/Output/contents.html) and [http://24ways.org/2006/beautiful-xml-with-xsl](http://24ways.org/2006/beautiful-xml-with-xsl), but still can't figure it out.  I am, infact, trying to transform an atom file, as in the second URL, and while that helps for most, it hasn't solved the last problem.  Since this is for class, I don't want to post all the code immediately, because I want to try to figure it out myself, but if my description is not clear, I'll post the original atom feed to give you some idea of what I'm trying to transform.

Thanks!

---

### Post by kostkon on 2007-09-25
OK, maybe I will be able to help you (if the XML is not very complex), but it would be better to paste here some code from the XSLT stylesheet and XML files.

I am saying this because I understand somehow where your problem is, but it would be difficult for me to give you a general solution.

I can see that you are not searching for a ready solution, but you want to learn. :)

---

### Post by DouglasAWh on 2007-09-25
The issue I am having, specifically, is with name tag which is deeper than the one directly in root.  Here's the original XML:

```

<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="googleLin.xsl"?> 
<feed xmlns="http://www.w3.org/2005/Atom" xmlns:openSearch="http://a9.com/-/spec/opensearchrss/1.0/"
	xmlns:feedburner="http://rssnamespace.org/feedburner/ext/1.0">
	<id>tag:blogger.com,1999:blog-10861780</id>
	<updated>2007-09-18T06:35:42.526-07:00</updated>
	<title type="text">Official Google Blog</title>
	<link rel="alternate" type="text/html" href="http://googleblog.blogspot.com/"/>
	<link rel="next" type="application/atom+xml"
		href="http://www.blogger.com/feeds/10861780/posts/default?alt=atom&amp;start-index=26&amp;max-results=25&amp;redirect=false"/>
	<link rel="http://schemas.google.com/g/2005#feed" type="application/atom+xml"
		href="http://googleblog.blogspot.com/feeds/posts/default"/>
	<author>
		<name>Eric Case</name>
	</author>
	<generator version="7.00" uri="http://www.blogger.com">Blogger</generator>
	<openSearch:totalResults>759</openSearch:totalResults>
	<openSearch:startIndex>1</openSearch:startIndex>
	<openSearch:itemsPerPage>25</openSearch:itemsPerPage>
	<link rel="self" href="http://feeds.feedburner.com/blogspot/MKuf" type="application/atom+xml"/>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-3863348694334304034</id>
		<published>2007-09-18T06:34:00.000-07:00</published>
		<updated>2007-09-18T06:35:42.562-07:00</updated>
		<title type="text">Google Reader goes multilingual</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Kevin Systrom, Product
			Marketing Manager&lt;/span&gt;&lt;br /&gt;&lt;br /&gt;I've been
			traveling a bunch in the past few days, and the one thing I've noticed is the variety of
			newspapers you're offered on every flight in Europe. In London, where I am now, my hotel has
			between 10 and 15 newspapers in the lobby from around the world in different languages. So I
			started thinking about how news plays an increasingly important role across the
			world.&lt;br /&gt;&lt;br /&gt;Of course, blogs have also become an
			international phenomenon. They're not constrained by language or nationality â€” in fact, blogs
			have become an important way to bring rise to independent reporters and writers. And there are
			more and more people who wish to read blogs in other languages. Up until now, our blog and
			news site service, Google Reader, was only available in English. As of today, it supports
			these languages: French, Italian, German, Spanish, English (UK), Chinese (Traditional and
			Simplified), Japanese, and Korean.&lt;br /&gt;&lt;br /&gt;With this
			announcement (you might enjoy &lt;a
			href="http://googlereader.blogspot.com/2007/09/breaking-up-isnt-hard-to-do.html"&gt;this
			take&lt;/a&gt; from the Reader blog), I'm also happy to tell you that we're removing
			the "Labs" label from Google Reader. It's a small textual change, but we believe it solidifies
			our commitment to make reading blogs and news sites easier than ever. So try &lt;a
			href="http://www.google.com/reader"&gt;Google Reader&lt;/a&gt; and get all your
			blogs and news sites in one place.&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/158072935" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/158072935/google-reader-goes-multilingual.html"
			title="Google Reader goes multilingual"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/3863348694334304034/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/3863348694334304034"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/3863348694334304034"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/09/google-reader-goes-multilingual.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-519245895647048145</id>
		<published>2007-09-17T20:38:00.000-07:00</published>
		<updated>2007-09-17T20:38:31.063-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="apps"/>
		<title type="text">Our feature presentation</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Attila Bodis, Software
			Engineer&lt;/span&gt;&lt;br /&gt;&lt;br /&gt;In April we announced
			that we were working to &lt;a
			href="http://googleblog.blogspot.com/2007/04/were-expecting.html"&gt;bring presentations
			to Google Docs&lt;/a&gt;. (Astute readers may recall learning about this &lt;a
			href="http://googlesystem.blogspot.com/2007/02/google-presently.html"&gt;even
			earlier&lt;/a&gt;, which caused a bit of excitement around here.) And today we're
			unveiling the new Google Docs presentations feature and invite you to try it at &lt;a
			href="http://docs.google.com/"&gt;documents.google.com&lt;/a&gt;. Maybe more than
			any other type of document, presentations are created to be shared. But assembling slide decks
			by emailing them around is as frustrating as it is time-consuming. The new presentations
			feature of Google Docs helps you to easily organize, share, present, and collaborate on
			presentations, using only a web browser.&lt;br /&gt;&lt;br /&gt;Starting
			today, presentations -- whether imported from existing files or created using the new slide
			editor -- are listed alongside documents and spreadsheets in the Google Docs document list.
			They can be edited, shared, and published using the familiar Google Docs interface, with
			several collaborators working on a slide deck simultaneously, in real time. When it's time to
			present, participants can simply click a link to follow along as the presenter takes the
			audience through the slideshow. Participants are connected through Google Talk and can chat
			about the presentation as they're watching. Not wanting anyone to feel left out, we've made
			the presentation feature available in 25 languages; &lt;a
			href="http://www.google.com/a/"&gt;Google Apps&lt;/a&gt; customers can also access
			it as part of Google Docs.&lt;br /&gt;&lt;br /&gt;We hope the millions of
			people who already create and share documents and spreadsheets will find presentations a
			welcome addition to the Google Docs family, and we can't wait to add even more features and
			enhancements.&lt;br /&gt;&lt;br /&gt;If you're new to Google Docs, watch this
			video to learn more about creating and collaborating on documents (and now
			presentations!).&lt;br /&gt;&lt;br /&gt;&lt;object width="425"
			height="350"&gt;&lt;param name="movie" value="
			http://www.youtube.com/v/eRqUE6IHTEA"&gt;&lt;/param&gt;&lt;embed
			src="http://www.youtube.com/v/eRqUE6IHTEA" type="application/x-shockwave-flash" width="425"
			height="350"&gt;&lt;/embed&gt;&lt;/object&gt;&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/157896163" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/157896163/our-feature-presentation.html"
			title="Our feature presentation"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/519245895647048145/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/519245895647048145"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/519245895647048145"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/09/our-feature-presentation.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-4730631630197184687</id>
		<published>2007-09-13T20:29:00.000-07:00</published>
		<updated>2007-09-13T20:29:24.457-07:00</updated>
		<title type="text">Australia readies itself for a Google election</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Julian Sonego and Rob
			Shilkin, Google Australia&lt;/span&gt;&lt;br /&gt;&lt;br /&gt;Looking
			from down under, the long U.S. election cycle ensures that there is no shortage of political
			headlines generated more than a year out from the actual Presidential election. Many of you
			may not realise that Australia is also readying itself to enter campaign mode. A federal
			election is anticipated to be held before the end of the year. You can be sure as the
			Australian parties get out on the hustings, babies will be kissed, doors knocked and hands
			vigorously shook -- but this election campaign is already a lot different to others, with
			digital media playing a new and important role.&lt;br /&gt;&lt;br /&gt;Today,
			in Sydney, we announced the launch of a &lt;a
			href="http://www.google.com.au/election2007"&gt;Google Australia election
			website&lt;/a&gt;, so that Australian voters can have an intimate look at the parties,
			candidates and election issues, all in one Google location. These services, spanning Search,
			Maps, News, video, Earth, Trends, and iGoogle, enable voters to organise, find and share
			Australian election information more easily than ever.&lt;br /&gt;&lt;br
			/&gt;We created a &lt;a href="http://picasaweb.google.com/auelection"&gt;Picasa
			Web Album &lt;/a&gt;to showcase all the elements, and we're pleased to offer these
			world-first tools that were developed in our Australian office. Here's hoping Australians will
			find them useful and even fun. It's our view that democracy on the web works -- and the web
			can work for democracy.&lt;br /&gt;&lt;br /&gt;&lt;object height="350"
			width="425"&gt;&lt;param name="movie"
			value="http://www.youtube.com/v/07yLauixFkM"&gt;&lt;param name="wmode"
			value="transparent"&gt;&lt;embed src="http://www.youtube.com/v/07yLauixFkM"
			type="application/x-shockwave-flash" wmode="transparent" height="350"
			width="425"&gt;&lt;/embed&gt;&lt;/object&gt;&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/156247271" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/156247271/australia-readies-itself-for-google.html"
			title="Australia readies itself for a Google election"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/4730631630197184687/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/4730631630197184687"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/4730631630197184687"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/09/australia-readies-itself-for-google.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-5064626033397356442</id>
		<published>2007-09-13T15:07:00.000-07:00</published>
		<updated>2007-09-13T15:09:09.277-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="apps"/>
		<title type="text">We've officially acquired Postini</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Dave Girouard, Vice
			President &amp;amp; General Manager, Google Enterprise&lt;/span&gt;&lt;br
			/&gt;&lt;br /&gt;As of today, &lt;a
			href="http://www.postini.com/index.php"&gt;Postini&lt;/a&gt; becomes a wholly
			owned subsidiary of Google, and we couldnâ€™t be happier about it. (Here's the &lt;a
			href="http://services.google.com/blog_resources/FINAL_Google_Postini_acquisition_FAQ.pdf"&gt;FAQ&lt;/a&gt;.)
			Since July 9, when we announced the &lt;a
			href="http://www.google.com/intl/en/press/pressrel/postini_20070709.html"&gt;agreement&lt;/a&gt;
			to acquire Postini, plenty of businesses have told us how much they respect Postini and how
			the acquisition makes sense for customers of both companies.&lt;br /&gt;&lt;br
			/&gt;We view this as welcome news, but also a sign of things to come. With the more than
			100,000 businesses on &lt;a href="http://www.google.com/a/"&gt;Google
			Apps&lt;/a&gt;, 35,000 businesses and more than 10 million users of Postini products,
			we see great potential on both sides. We're committed to continue to deliver the type of
			innovative and useful business products our customers have come to expect. And we plan to
			announce even more product offerings in the very near future.&lt;br /&gt;&lt;br
			/&gt;Separately, both companies shared a vision for what the world of hosted applications
			can become for businesses of all sizes. Together, we look forward to achieving it.&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/156149362" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/156149362/weve-officially-acquired-postini.html"
			title="We've officially acquired Postini"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/5064626033397356442/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/5064626033397356442"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/5064626033397356442"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/09/weve-officially-acquired-postini.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-3409732768288652022</id>
		<published>2007-09-13T10:58:00.000-07:00</published>
		<updated>2007-09-13T11:02:31.234-07:00</updated>
		<title type="text">Fly me to the moon</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Alan Eustace, Senior VP
			of Engineering&lt;/span&gt;&lt;br /&gt;&lt;br /&gt;In 1961, &lt;a
			href="http://en.wikipedia.org/wiki/Yuri_Gagarin"&gt;Yuri Gagarin&lt;/a&gt; became
			the first man to go into space and orbit the Earth. Two years later, &lt;a
			href="http://en.wikipedia.org/wiki/Valentina_Tereshkova"&gt;Valentina
			Tereshkova&lt;/a&gt; became the first woman in space (she orbited the earth 48 times
			-- take that, Yuri). By the end of the decade, the &lt;a
			href="http://en.wikipedia.org/wiki/Apollo_program"&gt;Apollo&lt;/a&gt; teams,
			rising to President Kennedy's &lt;a
			href="http://www.youtube.com/watch?v=L8Q4g-iINWU"&gt; challenge&lt;/a&gt;, made
			Neil Armstrong and Buzz Aldrin the first human beings to walk on the Moon.&lt;br
			/&gt;&lt;br /&gt;Great things can happen when you reach for the stars. That's why
			we're thrilled to be sponsoring the &lt;a href="http://www.xprize.org/"&gt;Lunar
			X-PRIZE&lt;/a&gt;, which will award a total of $30 million to teams competing around
			the world to land privately funded spacecraft on the Moon.&lt;br /&gt;&lt;br
			/&gt;Why does &lt;a href="http://www.google.com/space/"&gt;Google love
			space&lt;/a&gt;? Well, for one thing, we just think it's cool. More seriously, space
			exploration has a remarkable history of producing technological breakthroughs, from ablative
			heat shields and asteroid mining to invisible braces and Tang; the X-PRIZE, too, could lead to
			important developments in robotic space exploration, a whole host of new space-age materials,
			precision landing control technology, and who knows what else.&lt;br /&gt;&lt;br
			/&gt;Finally, we hope the contest will help renew public interest in fields like math,
			engineering and computer science, especially among the young people on whom we'll all be
			depending to tackle tomorrow's technical challenges, whether they're on the web or &lt;a
			href="http://earth.google.com/sky/skyedu.html"&gt;among the
			stars&lt;/a&gt;.&lt;br /&gt;&lt;br /&gt;As Neil Armstrong famously
			&lt;a href="http://www.phrases.org.uk/meanings/324100.html"&gt;pointed
			out&lt;/a&gt;, small steps lead to giant leaps. We hope that our &lt;a
			href="http://googlelunarxprize.org/"&gt;sponsorship&lt;/a&gt; of the Lunar X-PRIZE
			is one of those small steps, and we can't wait to see what giant leaps result. By the way,
			just so the teams can scout locations and plan accordingly, &lt;a
			href="http://www.google.com/moon/"&gt;Google Moon&lt;/a&gt; &lt;a
			href="http://google-latlong.blogspot.com/2007/09/new-moon.html"&gt;just went
			live&lt;/a&gt;. For more information, visit the &lt;a
			href="http://www.googlelunarxprize.org/"&gt;Google Lunar X-PRIZE
			site&lt;/a&gt;.&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/156053888" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/156053888/fly-me-to-moon.html"
			title="Fly me to the moon"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/3409732768288652022/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/3409732768288652022"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/3409732768288652022"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/09/fly-me-to-moon.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-6515352582932282858</id>
		<published>2007-09-12T09:33:00.000-07:00</published>
		<updated>2007-09-13T09:53:38.205-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="search"/>
		<title type="text">Get your cricket scores here</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Sadeesh Duraisamy,
			Software Engineer, and Alok Goel, Business Product Manager&lt;/span&gt;&lt;br
			/&gt;&lt;br /&gt;With the start of the &lt;a
			href="http://news.google.com/news?q=Twenty20+world+championship&amp;hl=en&amp;amp;rls=GGLD,GGLD:2007-24,GGLD:en&amp;um=1&amp;amp;ie=UTF-8&amp;sa=X&amp;amp;oi=news_result&amp;resnum=1&amp;amp;ct=title"&gt;Twenty20
			world championship&lt;/a&gt;, cricket fever is upon legions of enthusiasts. To make it
			easier for you to indulge your interest in a game John Fowles characterized as "chess made
			flesh," we've simplified your search for cricket scores. Just type [&lt;a
			href="http://www.google.com/search?source=ig&amp;hl=en&amp;amp;q=cricket&amp;btnG=Google+Search"&gt;cricket&lt;/a&gt;]
			in a Google search box and you'll see a brief score of all the current cricket matches. A
			single click will also give you access to a detailed cricket score card.&lt;br
			/&gt;&lt;br /&gt;If you're a diehard India fan, then type [&lt;a
			href="http://www.google.com/search?source=ig&amp;amp;hl=en&amp;q=cricket+india&amp;amp;btnG=Google+Search"&gt;cricket
			india&lt;/a&gt;] or [&lt;a
			href="http://www.google.com/search?ie=UTF-8&amp;oe=UTF-8&amp;amp;sourceid=gd&amp;q=cricket+score+India+England&amp;amp;hl=en&amp;rls=GGLD,GGLD:2007-24,GGLD:en&amp;amp;wxob=0"&gt;cricket
			score India England&lt;/a&gt;] to get results for Indian matches. Of course, feel free
			to replace India with the country of your choice for country-specific results.&lt;br
			/&gt;&lt;br /&gt;&lt;a onblur="try {parent.deselectBloggerImageGracefully();}
			catch(e) {}"
			href="http://bp0.blogger.com/_Ap14FtNN91w/RugUqi5Mg5I/AAAAAAAAAQM/9FoWdUcelOQ/s1600-h/Cricket_India.jpg"&gt;&lt;img
			style="cursor: pointer;"
			src="http://bp0.blogger.com/_Ap14FtNN91w/RugUqi5Mg5I/AAAAAAAAAQM/9FoWdUcelOQ/s320/Cricket_India.jpg"
			alt="" id="BLOGGER_PHOTO_ID_5109356498405589906" border="0"
			/&gt;&lt;/a&gt;&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/155562325" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/155562325/get-your-cricket-scores-here.html"
			title="Get your cricket scores here"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/6515352582932282858/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/6515352582932282858"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/6515352582932282858"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/09/get-your-cricket-scores-here.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-5777841291404099749</id>
		<published>2007-09-12T08:54:00.000-07:00</published>
		<updated>2007-09-17T20:40:33.835-07:00</updated>
		<title type="text">A new Google.org RFP</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Kirsten Olsen, Project
			Manager, Google.org&lt;/span&gt;&lt;br /&gt;&lt;br /&gt;Today,
			&lt;a href="http://google.org/"&gt;Google.org&lt;/a&gt; has issued a &lt;a
			href="http://www.google.org/recharge/rfp/"&gt;request for proposals&lt;/a&gt; to
			the tune of $10 million in order to advance sustainable transportation solutions. We're
			inviting entrepreneurs and companies to show us their best ideas on how they can contribute to
			this important cause. We need catalytic investments to support technologies, products and
			services that are critical to accelerating plug-in vehicle commercialization.&lt;br
			/&gt;&lt;br /&gt;There's &lt;a
			href="http://blog.google.org/2007/09/drivers-start-your-batteries.html"&gt;more about
			this&lt;/a&gt; on the Google.org blog.&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/155549569" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/155549569/new-googleorg-rfp.html"
			title="A new Google.org RFP"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/5777841291404099749/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/5777841291404099749"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/5777841291404099749"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/09/new-googleorg-rfp.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-8706182472681715213</id>
		<published>2007-09-10T16:55:00.000-07:00</published>
		<updated>2007-09-10T16:56:05.281-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="developers"/>
		<title type="text">Our plans for Code Jam</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Bartholomew "Ruberik"
			Furrow, Technical Lead &lt;/span&gt;&lt;br /&gt;&lt;br /&gt;What do
			you do if you've got a head full of good ideas, and nothing interesting to do with them? You
			might need a good dose of competitive programming. During a programming competition you
			contort your brain, trying desperately to figure out that tiny trick that will let your
			program run a thousand times faster, or searching for the elusive mathematical fact that will
			lead you to the solution. Then you tell your computer what to do, and watch it solve that
			torturous problem faster than you can blink. If you're like me, you eagerly participate in
			every coding competition that comes along.&lt;br /&gt;&lt;br /&gt;Since 2003,
			we have supported the fun and intensity of competitive programming around the world by
			offering code jams powered by TopCoder. Contests like the ACM ICPC, the TopCoder Open and our
			TopCoder-powered code jams have formed a great community of contests and contestants; now
			we're excited to join that community in our own right, by producing a Google Code Jam of our
			own! There aren't too many details to share yet, but we have some big plans: there are quite a
			few super-competitive programmers here, and we've put them to work preparing challenges for
			you.&lt;br /&gt;&lt;br /&gt;So start brushing up with &lt;a
			href="http://services.google.com/blog_resources/Google_CodeJam_Practice.pdf"&gt;a couple
			of practice problems&lt;/a&gt; -- and it's well worth checking out some old problems
			from the &lt;a href="http://acmicpc-live-archive.uva.es/nuevoportal/"&gt;ACM
			ICPC&lt;/a&gt; and &lt;a
			href="http://www.topcoder.com/tc"&gt;TopCoder&lt;/a&gt; too. We're also excited to
			hear what you think would make for a great Google-run programming contest, so send us your
			&lt;a
			href="mailto:Programmingcontest-feedback@google.com"&gt;feedback&lt;/a&gt; -- and
			get ready for a challenge.&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/154802446" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/154802446/our-plans-for-code-jam.html"
			title="Our plans for Code Jam"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/8706182472681715213/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/8706182472681715213"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/8706182472681715213"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/09/our-plans-for-code-jam.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-9091481903403169508</id>
		<published>2007-09-06T14:45:00.001-07:00</published>
		<updated>2007-09-06T14:46:46.176-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="search"/>
		<title type="text">Find a needle in a feedstack with Google Reader</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Ben Darnell, Google
			Reader Engineer&lt;/span&gt;&lt;br /&gt;&lt;br /&gt;The fundamental
			problem with information is that there's too much of it, and this is probably why we all go to
			our trusted sources to learn what we &lt;i&gt;really&lt;/i&gt; need to know.
			Your sources filter out the noise and present the most interesting bits to you in a useful
			way. For many of us, these sources include newspapers, magazines, and of course blogs. We
			built &lt;a href="http://reader.google.com/"&gt;Google Reader&lt;/a&gt; as a
			way for you to see all of your online sources in one place.&lt;br /&gt;&lt;br
			/&gt;So if you want to keep up with the chatter about the new iPods or
			&lt;i&gt;Superbad&lt;/i&gt;, now you can. We've added a familiar search box to
			the top of Google Reader so you can search across all the blogs and sites to which you're
			subscribed.&lt;br /&gt;&lt;br /&gt;&lt;a onblur="try
			{parent.deselectBloggerImageGracefully();} catch(e) {}"
			href="http://bp3.blogger.com/_Ap14FtNN91w/RuB0vOe5_gI/AAAAAAAAAPY/rl3o-UjOL1o/s1600-h/Reader_search.jpg"&gt;&lt;img
			style="cursor: pointer;"
			src="http://bp3.blogger.com/_Ap14FtNN91w/RuB0vOe5_gI/AAAAAAAAAPY/rl3o-UjOL1o/s320/Reader_search.jpg"
			alt="" id="BLOGGER_PHOTO_ID_5107210332128542210" border="0"
			/&gt;&lt;/a&gt;&lt;br /&gt;&lt;br /&gt;See if this doesn't help
			with your information overload. And by the way, if you want to learn more about feed readers,
			here's a great explanation:&lt;br /&gt;&lt;br /&gt;&lt;object height="350"
			width="425"&gt;&lt;param name="movie"
			value="http://www.youtube.com/v/0klgLsSxGsU"&gt;&lt;param name="wmode"
			value="transparent"&gt;&lt;embed src="http://www.youtube.com/v/0klgLsSxGsU"
			type="application/x-shockwave-flash" wmode="transparent" height="350"
			width="425"&gt;&lt;/embed&gt;&lt;/object&gt;&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/153159657" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/153159657/find-needle-in-feedstack-with-google.html"
			title="Find a needle in a feedstack with Google Reader"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/9091481903403169508/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/9091481903403169508"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/9091481903403169508"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/09/find-needle-in-feedstack-with-google.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-1694590194029875721</id>
		<published>2007-09-06T06:33:00.000-07:00</published>
		<updated>2007-09-06T06:34:54.491-07:00</updated>
		<title type="text">Collect, share, and discover books</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Adam Mathes, Product
			Manager&lt;/span&gt;&lt;br /&gt;&lt;br /&gt;Books often live a vibrant
			life offline, and through digitization Google Book Search tries to help them live an even more
			exciting life online through full text search. Today we're launching some new features that go
			beyond search so you can collect, share, and discover new books.&lt;br /&gt;&lt;br
			/&gt;To start, you can create your own personal collection on Book Search, and use it to
			help find just the right book from your collection for any occasion. Other people can view
			your library, so you can share your collection &lt;a
			href="http://booksearch.blogspot.com/2007/09/my-own-library-on-book-search.html"&gt;as
			Bethany has done&lt;/a&gt;. Or take a look at some &lt;a
			href="http://books.google.com/googlebooks/mylibrary/"&gt;other interesting
			collections&lt;/a&gt;.&lt;br /&gt;&lt;br /&gt;Digitized text is useful
			beyond search, too. It enables us to infer connections between books through shared passages.
			For example, &lt;a
			href="http://books.google.com/books?id=F201AAAAMAAJ&amp;pg=PA158&amp;amp;sig=MRlRSfXVKcRYQGwql0xrCKdbahk&amp;source=gbs_quot&amp;amp;vq=%22Sir+Isaac+Newton,+a+little+before+he+died,+said,+I+don%27t+know+what+I+may+seem+to+the+world%3B+but%22"&gt;Sir
			Isaac Newton&lt;/a&gt; once said:&lt;br /&gt;&lt;blockquote&gt;
			&lt;span style="font-style: italic;"&gt;I know not what I may appear to the world; but
			to myself I seem to&lt;/span&gt;&lt;br /&gt;&lt;span style="font-style:
			italic;"&gt;have been only like a boy playing on the sea shore, and
			diverting&lt;/span&gt;&lt;span style="font-style: italic;"&gt; myself in now
			and then finding a smoother pebble or a prettier shell&lt;/span&gt;&lt;span
			style="font-style: italic;"&gt; than ordinary, whilst the great ocean of truth lay all
			undiscovered&lt;/span&gt;&lt;span style="font-style: italic;"&gt; before
			me.&lt;/span&gt;&lt;/blockquote&gt;This quote has resonated and &lt;a
			href="http://books.google.com/books?id=F201AAAAMAAJ&amp;amp;qtid=37e78a8"&gt;been used
			in hundreds of books&lt;/a&gt; from the early 1800s to 2007. You can discover
			connections between books through quotations like this in a feature we call "Popular
			passages." Read more and &lt;a
			href="http://booksearch.blogspot.com/2007/09/dive-into-meme-pool-with-google-book.html"&gt;dive
			into the meme pool&lt;/a&gt;.&lt;br /&gt;&lt;br /&gt;We've also
			launched a way to let users, select, copy and embed segments of public domain books (like the
			Newton quote) in any web page. We hope to make it as easy to blog and quote from a book as it
			is from any web page. Like many innovations at Google, a stellar &lt;a
			href="http://booksearch.blogspot.com/2007/08/share-and-enjoy.html"&gt;summer intern worked
			on this&lt;/a&gt; .&lt;br /&gt;&lt;br /&gt;We hope these new features
			help you discover, collect, and share some of the great truths just waiting to be discovered
			(or maybe re-discovered) in the great ocean of books before us.&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/152970281" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/152970281/collect-share-and-discover-books.html"
			title="Collect, share, and discover books"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/1694590194029875721/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/1694590194029875721"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/1694590194029875721"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/09/collect-share-and-discover-books.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-3695200839384448476</id>
		<published>2007-08-31T13:40:00.000-07:00</published>
		<updated>2007-08-31T13:42:39.581-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="user experience and usability"/>
		<title type="text">Speaking in more languages</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Vlad Patryshev,
			software engineer&lt;/span&gt;&lt;br /&gt;&lt;br /&gt;Many Google
			products (&lt;a href="http://www.google.com/"&gt;Google.com&lt;/a&gt;,
			&lt;a href="http://www.blogger.com/"&gt;Blogger&lt;/a&gt;, &lt;a
			href="http://earth.google.com/"&gt;Google Earth&lt;/a&gt;, and others) currently
			support more than 170 languages, from Abhazian to Zulu. Translations into most of these
			languages are done by volunteers from around the world who are eager to help people view and
			search the web in their own native language. To facilitate how we go about getting these
			languages, we created a volunteer translation program: &lt;a
			href="http://www.google.com/transconsole"&gt;Google In Your
			Language&lt;/a&gt;.&lt;br /&gt;&lt;br /&gt;Anybody can sign up as a
			volunteer translator by visiting the &lt;a
			href="http://www.google.com/language_tools?hl=en"&gt; Language Tools&lt;/a&gt;
			page and then clicking on the &lt;a
			href="http://www.google.com/transconsole"&gt;Google in Your Language
			link&lt;/a&gt;. After verification, you'll be offered a list of products to translate,
			including the main search site, Gmail, iGoogle, Google Maps, and many others&lt;br
			/&gt;&lt;br /&gt;Although the amount of translation for each project is not
			overwhelming, it usually takes weeks for an individual volunteer to finish translating one
			site. Once a reasonable percentage of translations for Google pages in a given language is
			submitted, we'll add your language to production and, after a bit of time, you'll be able to
			see them in yet another language.&lt;br /&gt;&lt;br /&gt;Some "volunteer"
			languages are well represented and are nearly finished being translated, i.e. Armenian,
			Estonian, Slovenian are 95% complete; even Latin has 70% of its translations done.
			Representatives of other languages are not as active, i.e. Abhazian has been available for
			several years, but so far we don't have enough translations completed to release it into
			production. Tibetan, Inupak, Inuktikut, Wolof, Zhuang all have less than 10% of their content
			translated. Interestingly, each of those has more speakers than Faroese, which has 74% of
			texts translated.&lt;br /&gt;&lt;br /&gt;Recently we have added a bunch of new
			languages to the Google In Your Language program, including Navajo, Filipino, several Russian
			Federation languages (Avaric, Chechen, Chuvash, Komi), and some African languages (Akan,
			Bambara, Gikuyu, Kongo, Ndebele, Ndongo, Nyanja, Venda). Our hope is to attract even more
			volunteers to participate in this program so that Google can speak all the world's languages
			one day.&lt;img src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/150688016" height="1"
			width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/150688016/speaking-in-more-languages.html"
			title="Speaking in more languages"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/3695200839384448476/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/3695200839384448476"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/3695200839384448476"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/09/speaking-in-more-languages.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-1233373937503419841</id>
		<published>2007-08-31T08:51:00.001-07:00</published>
		<updated>2007-08-31T08:52:04.402-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="search"/>
		<title type="text">Google Desktop for the Mac in 9 more languages</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Rose Yao, Mac Product
			Manager&lt;/span&gt;&lt;br /&gt;&lt;br /&gt;In April we &lt;a
			href="http://googlemac.blogspot.com/2007/04/google-desktop-for-mac_04.html"&gt;launched
			Google Desktop for the Mac&lt;/a&gt; to further our goal of delivering great products
			on the Mac and making them universally available on all platforms. A big thanks to all of you
			for using Desktop for the Mac, and for sharing your feedback. Today we're tackling the second
			part of that "universal" goal: now Google Desktop for the Mac is available in 9 more
			languages: Chinese Simplified and Traditional, Dutch, UK English, French, German, Italian,
			Japanese, and Spanish. There's more on this on the &lt;a
			href="http://desktop.google.com/mac"&gt;Desktop for Mac site&lt;/a&gt;.&lt;br
			/&gt;&lt;br /&gt;We look forward to lots more of you trying it and sending us
			feedback from all over, and in different languages. We hope you like it, and encourage you to
			watch for more updates from our &lt;a href="http://googlemac.blogspot.com/"&gt;Google
			Mac team&lt;/a&gt;.&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/150586892" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/150586892/google-desktop-for-mac-in-9-more.html"
			title="Google Desktop for the Mac in 9 more languages"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/1233373937503419841/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/1233373937503419841"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/1233373937503419841"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/08/google-desktop-for-mac-in-9-more.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-4703420817400419981</id>
		<published>2007-08-29T07:36:00.001-07:00</published>
		<updated>2007-08-29T07:42:12.274-07:00</updated>
		<title type="text">Supporting GrandCentral's Project CARE</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Craig Walker and
			Vincent Paquet, Product Managers&lt;/span&gt;&lt;br /&gt;&lt;br
			/&gt;For homeless people and others in need, not having a stable phone number can be
			crippling: you need one to follow up on medical appointments, keep in touch with friends and
			loved ones, and hear back from prospective employers.&lt;br /&gt;&lt;br
			/&gt;When we &lt;a
			href="http://googleblog.blogspot.com/2007/07/all-aboard.html"&gt;acquired&lt;/a&gt;
			GrandCentral Communications last month, we were pleased to embrace their Project CARE
			initiative, which provides a permanent local phone number and unlimited voicemail service to
			people who need a way to stay connected.&lt;br /&gt;&lt;br /&gt;GrandCentral
			has been operating Project CARE ("Communications and Respect for Everybody") since April 2006,
			and with the help of more than &lt;a
			href="http://www.grandcentral.com/about/projectcare/"&gt;20 community outreach
			partners&lt;/a&gt; has provided more than 5,000 phone numbers and served close to
			100,000 voicemail messages to homeless and needy people in the Bay Area. Someone calling a
			number from Project CARE will have the same experience as someone calling a standard phone
			number, and voicemail messages can be stored as long as they're needed.&lt;br
			/&gt;&lt;br /&gt;A big part of Project CARE has been GrandCentral's participation
			in San Francisco's &lt;a
			href="http://www.sfconnect.org/AboutUs/index.php/homeless_connect/phc_our_mission.html?"&gt;Project
			Homeless Connect&lt;/a&gt; events. Every other month, these gatherings bring service
			providers like GrandCentral together with volunteers at an all-day fair to provide services to
			the homeless. In fact, &lt;a
			href="http://www.sfconnect.org/specialevents/viewSpecialEvent.php?_mode=eventDetail&amp;_action=eventDetail&amp;amp;ixSpecialEvent=10"
			id="opyx"&gt;there's an event today&lt;/a&gt;, starting at 8:30 AM (PDT) at
			&lt;a
			href="http://maps.google.com/maps?f=q&amp;hl=en&amp;amp;geocode=&amp;q=Bill+Graham+Auditorium+99+Grove+Street+94012&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;ie=UTF8&amp;ll=37.778415,-122.418122&amp;amp;spn=0.022183,0.028968&amp;z=15&amp;amp;amp;amp;amp;amp;amp;amp;amp;iwloc=A&amp;amp;om=1"
			id="i9cy"&gt;Bill Graham Civic Auditorium&lt;/a&gt;. If you're in San Francisco,
			please stop by our booth or even &lt;a
			href="http://www.sfconnect.org/AboutUs/index.php/volunteer.html"&gt;volunteer&lt;/a&gt;.&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/149676215" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/149676215/supporting-grandcentrals-project-care.html"
			title="Supporting GrandCentral's Project CARE"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/4703420817400419981/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/4703420817400419981"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/4703420817400419981"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/08/supporting-grandcentrals-project-care.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-8735902339103408049</id>
		<published>2007-08-28T17:23:00.001-07:00</published>
		<updated>2007-08-28T17:57:15.474-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="apps"/>
		<category scheme="http://www.blogger.com/atom/ns#" term="user experience and usability"/>
		<title type="text">Lights, camera, Gmail</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Bill Kee, Associate
			Product Marketing Manager&lt;/span&gt;&lt;br /&gt;&lt;br /&gt;Last
			month, we &lt;a
			href="http://googleblog.blogspot.com/2007/07/like-making-videos-love-gmail.html" id="d4i0"
			title="invited you"&gt;invited you&lt;/a&gt; to join the Gmail collaborative
			video, pull out your video cameras and help us imagine how an email message travels around the
			world. Two &lt;a href="http://www.youtube.com/watch?v=gZIgdq9dp2M" id="ufek"
			title="Rubik's"&gt;Rubik's&lt;/a&gt; &lt;a
			href="http://www.youtube.com/watch?v=HEhhzJB3n00" id="xy:r"
			title="cubes"&gt;cubes&lt;/a&gt;, a few jaunts &lt;a
			href="http://www.youtube.com/watch?v=ZKeD4J70jqM" id="djq9" title="in a bottle"&gt;in a
			bottle&lt;/a&gt;, beautiful &lt;a
			href="http://www.youtube.com/watch?v=BFQdGkFZcE4" id="lqs1" title="sand animation"&gt;sand
			animation&lt;/a&gt;, and one &lt;a
			href="http://www.youtube.com/watch?v=ULwrZ22FJF8" id="ualc" title="dog's trip"&gt;dog's
			trip&lt;/a&gt; to the Southernmost point of the continental US later, we'd received
			more than &lt;span style="color:#3333ff;"&gt;&lt;a
			href="http://www.youtube.com/video_response_view_all?v=VfDW7qAdFGk" id="c41." title="1,100
			fantastic clips"&gt;1,100 fantastic clips&lt;/a&gt;&lt;/span&gt; from
			Gmail fans from &lt;span style="background-color: rgb(255, 255, 255);"&gt;more than 65
			&lt;/span&gt;countries. It was impossible to fit all of the great submissions into one
			cut, but after hours of fun watching &lt;a
			href="http://www.youtube.com/watch?v=OuEAjqyQ2qM" id="wudp"
			title="jugglers"&gt;jugglers&lt;/a&gt;, &lt;a
			href="http://www.youtube.com/watch?v=_0QlJJ_aF-E" id="aa1j"
			title="firemen"&gt;firemen&lt;/a&gt;, &lt;a
			href="http://www.youtube.com/watch?v=gKX82dsXWew" id="ly:n"
			title="camel-riders"&gt;camel-riders&lt;/a&gt;, and original &lt;a
			href="http://www.youtube.com/watch?v=dIvQMk4k6JU" id="o151"
			title="animation"&gt;animation&lt;/a&gt;, we edited highlights together into this
			video and used the &lt;a href="http://www.google.com/apis/maps/index.html" id="m.lo"
			title="Google Maps API"&gt;Google Maps API&lt;/a&gt; to put together a map showing
			where many of the clips came from (you can also see these at &lt;a
			href="http://mail.google.com/mvideo" id="g332"
			title="http://mail.google.com/mvideo"&gt;http://mail.google.com/mvideo&lt;/a&gt;):&lt;br
			/&gt;&lt;br /&gt;&lt;span style="color:#ff0000;"&gt;&lt;object
			height="353" width="425"&gt;&lt;param name="movie"
			value="http://www.youtube.com/v/qKAInP_tmHk"&gt;&lt;param name="wmode"
			value="transparent"&gt;&lt;embed src="http://www.youtube.com/v/qKAInP_tmHk"
			type="application/x-shockwave-flash" wmode="transparent" height="353"
			width="425"&gt;&lt;/embed&gt;&lt;/object&gt;&lt;/span&gt;&lt;br
			/&gt;&lt;span style="color:#ff0000;"&gt;&lt;br
			/&gt;&lt;/span&gt;&lt;span style="color:#ff0000;"&gt;&lt;iframe
			width="95%" height="400" frameborder="no" scrolling="no" marginheight="0" marginwidth="0"
			src="http://maps.google.com/maps?f=q&amp;hl=pl&amp;amp;geocode=&amp;q=http:%2F%2Fservices.google.com%2Fearth%2Fmvideo.kml&amp;amp;ie=UTF8&amp;om=1&amp;amp;t=k&amp;s=AARTsJoT5oBjk9IHzTkEDj634yygZbvLFQ&amp;amp;ll=31.952162,-36.914062&amp;spn=105.832053,158.203125&amp;amp;z=2&amp;output=embed"&gt;&lt;/iframe&gt;&lt;br/&gt;&lt;a
			href="http://maps.google.com/maps?f=q&amp;amp;hl=pl&amp;geocode=&amp;amp;q=http:%2F%2Fservices.google.com%2Fearth%2Fmvideo.kml&amp;ie=UTF8&amp;amp;om=1&amp;t=k&amp;amp;ll=31.952162,-36.914062&amp;spn=105.832053,158.203125&amp;amp;z=2&amp;source=embed"
			style="color:#0000FF;text-align:left;font-size:small"&gt;View Larger
			Map&lt;/a&gt;&lt;/span&gt;&lt;span
			style="color:#ff0000;"&gt;&lt;br /&gt;&lt;br /&gt;&lt;/span&gt; A
			big thank you to everyone who participated -- your creativity is astounding!&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/149439742" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/149439742/lights-camera-gmail_28.html"
			title="Lights, camera, Gmail"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/8735902339103408049/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/8735902339103408049"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/8735902339103408049"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/08/lights-camera-gmail_28.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-8407752280293398456</id>
		<published>2007-08-28T13:12:00.000-07:00</published>
		<updated>2007-08-28T13:12:21.456-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="developers"/>
		<title type="text">Google Web Toolkit: Towards a better web</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Bruce Johnson and Dan
			Peterson, Google Web Toolkit team&lt;/span&gt;&lt;br /&gt;&lt;br
			/&gt;We're very pleased to tell you that the &lt;a
			href="http://code.google.com/webtoolkit/"&gt;Google Web Toolkit&lt;/a&gt; (GWT) is
			no longer in beta as of &lt;a
			href="http://googlewebtoolkit.blogspot.com/2007/08/gwt-14-release-and-out-of-beta.html"&gt;today's
			release of GWT 1.4.&lt;/a&gt; For Java developers who have used GWT to create high-end
			web applications over the last year, this may not seem all that surprising. But if you haven't
			yet heard the story behind GWT, this seems like the perfect time...&lt;br
			/&gt;&lt;br /&gt;If you've been in the technology industry for a while, you
			probably remember when enterprises and software vendors had to think pretty hard about whether
			to develop locally-installed desktop applications or web-based browser applications. These
			days, whether you're building &lt;a
			href="http://code.google.com/gme/"&gt;mashups&lt;/a&gt;, &lt;a
			href="http://code.google.com/apis/gadgets/"&gt;gadgets&lt;/a&gt;, or full-blown
			applications, it's a no-brainer: the browser is the delivery platform of choice. However,
			users expect more from the up-and-coming generation of web applications than the simple
			click-and-wait of yesterweb. And if you're a web developer, you know that this requires
			&lt;a
			href="http://en.wikipedia.org/wiki/Ajax_%28programming%29"&gt;AJAX&lt;/a&gt;, the
			cluster of technologies including JavaScript and dynamic HTML that can make browsers do
			backflips.&lt;br /&gt;&lt;br /&gt;But the stark reality of AJAX applications
			is that, although they can deliver sexy features and great usability, they are unusually hard
			to engineer. Browser quirks and the anything-goes nature of JavaScript will inevitably
			frustrate even the most dedicated developers and add risk to your schedule with every line of
			code written. If you do eventually manage to construct a complex AJAX application that works,
			you're likely to find that maintaining it over time can be a major challenge. And all that
			doesn't even scratch the surface of testing, optimizing, securing and internationalizing your
			application. (If you are currently working on an ambitious AJAX project and haven't yet come
			to this conclusion, please re-read this post in six months when you're further
			along!)&lt;br /&gt;&lt;br /&gt;We've learned a lot from our experiences
			building web applications, and we're happy to share the tools we've created. Google Web
			Toolkit is an open source project that helps Java developers harness the richness of AJAX in a
			cross-platform, web-friendly environment. The magic trick is that GWT cross-compiles Java
			source code into standalone JavaScript that you can include in any web page. Instead of
			spending time becoming JavaScript gurus and fighting browser quirks, developers using GWT
			spend time productively coding and debugging in the robust Java programming language, using
			their existing Java tools and expertise. Naturally, GWT is also a great way to easily take
			advantage of the latest-and-greatest Google APIs and browser enhancements, such as &lt;a
			href="http://code.google.com/apis/gears/"&gt;Google Gears&lt;/a&gt;.&lt;br
			/&gt;&lt;br /&gt;In addition to making debugging far easier, GWT's unique
			compilation-based approach to AJAX has the nice property that it rewards developers for good
			software engineering practices. Java source code that is clear and organized can be easily
			optimized by the GWT compiler, which is a nice antidote to the frequent hack-and-slash
			approach that's all too common in JavaScript development. As your application grows, the GWT
			compiler begins to pay off in even bigger ways. Unused code is automatically removed so that
			scripts are smaller and pages load faster. Complex code can be automatically coalesced and
			simplified. Most importantly, because the Java language is statically typed, many common
			errors can be caught during development rather than production. You can observe the
			high-performance results yourself in GWT's &lt;a
			href="http://gwt.google.com/samples/Mail/Mail.html"&gt;sample Mail
			application&lt;/a&gt;.&lt;br /&gt;&lt;br /&gt;Technical details aside,
			GWT makes it easy to develop fast, friendly web apps that users love â€” which is, after all,
			the point.&lt;br /&gt;&lt;br /&gt;&lt;a
			href="http://code.google.com/webtoolkit/download.html"&gt;Download GWT
			1.4&lt;/a&gt;.&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/149349405" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/149349405/google-web-toolkit-towards-better-web.html"
			title="Google Web Toolkit: Towards a better web"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/8407752280293398456/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/8407752280293398456"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/8407752280293398456"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/08/google-web-toolkit-towards-better-web.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-1899710609860044524</id>
		<published>2007-08-24T10:03:00.000-07:00</published>
		<updated>2007-08-24T11:24:45.833-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="accessibility"/>
		<title type="text">First year of Google WiFi</title>
		<content type="html">&lt;span class="byline-author"&gt;By Minnie Ingersoll, Chris Sacca
			&amp; Larry Alder, Alternative Access Team&lt;/span&gt;&lt;br
			/&gt;&lt;br /&gt;Our Mountain View WiFi network just celebrated its &lt;a
			title="first anniversary"
			href="http://googleblog.blogspot.com/2006/08/free-citywide-wifi-in-mountain-view.html"
			id="g7.:"&gt;first anniversary&lt;/a&gt;, and we thought you'd appreciate a few
			data points. The network's 400+ mesh routers &lt;a
			href="http://wifi.google.com/city/mv/apmap.html"&gt;cover about 12 square
			miles&lt;/a&gt; and 25,000 homes to serve approximately 15,000 unique users each
			&lt;strike&gt;week&lt;/strike&gt; &lt;span style="font-weight:
			bold;"&gt;month&lt;/span&gt;. Since the beginning of 2007, traffic has grown
			almost 10 percent each month, and the network now handles over 300 gigabytes of data each day,
			sent to over 100 distinct types of WiFi devices. Virtually the entire city has been taking
			advantage of the network, with 95 percent of the mesh routers being used on any given
			day.&lt;br /&gt;&lt;br /&gt;Around the globe and across the U. S., many people
			are still not able to access the online services that are increasingly helpful, if not
			essential, tools for our daily lives. This is why we're committed to promoting alternative
			platforms for people to access the web, no matter where you are, what you're doing or what
			device you're using.&lt;br /&gt;&lt;br /&gt;For those who have been following
			&lt;a href="https://home.feather.net/sanfrancisco" id="c03t"&gt;the
			effort&lt;/a&gt; to create a free wireless network in San Francisco, we continue to
			hope that EarthLink and The City will find a way to enable all San Franciscans to enjoy the
			free WiFi network they deserve. On a broader scale, we hope that the success of the Mountain
			View model will encourage others to think creatively about how to address access issues in
			many other communities.&lt;br /&gt;&lt;br /&gt;&lt;span
			style="font-weight: bold;"&gt;&lt;span style="font-style:
			italic;"&gt;Update:&lt;/span&gt; &lt;/span&gt;Corrected usage from "week"
			to "month."&lt;img src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/147785484"
			height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/147785484/first-year-of-google-wifi.html"
			title="First year of Google WiFi"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/1899710609860044524/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/1899710609860044524"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/1899710609860044524"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/08/first-year-of-google-wifi.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-6830172786772282502</id>
		<published>2007-08-22T08:26:00.000-07:00</published>
		<updated>2007-08-22T08:27:43.172-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="search"/>
		<title type="text">The view from the Sky</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by
			&lt;/span&gt;&lt;span class="byline-author"&gt;&lt;a
			href="http://en.wikipedia.org/wiki/Sally_Ride"&gt;Sally Ride&lt;/a&gt;, Ph.D.,
			former astronaut&lt;/span&gt;&lt;span class="byline-author"&gt;&lt;br
			/&gt;&lt;br /&gt;It's true: astronauts have a great view! When I was &lt;a
			href="http://starchild.gsfc.nasa.gov/docs/StarChild/whos_who_level2/ride.html"&gt;orbiting
			Earth in the space shuttle&lt;/a&gt;, I had the unbelievable experience of being able
			to float over to a window and look back down at our planet, then off into space at the stars.
			Absolutely spectacular!&lt;br /&gt;&lt;br /&gt;These days my feet are closer
			to the ground, and my mission doesn't involve circling the Earth. I run a science education
			company, &lt;a href="http://www.sallyridescience.com/"&gt;Sally Ride
			Science&lt;/a&gt;, that creates entertaining science materials for elementary and
			middle school students and classrooms, so I'm always looking for cool tools that can engage
			kids and help them learn more about our world. &lt;a
			href="http://earth.google.com/sky"&gt;Sky in Google Earth &lt;/a&gt;is great, and
			we plan on using it in some of our programs. (Read more on
			the&lt;/span&gt;&lt;span class="byline-author"&gt; &lt;a
			href="http://google-latlong.blogspot.com/2007/08/sky-final-frontier.html"&gt;Google Lat
			Long blog&lt;/a&gt;.)&lt;/span&gt;&lt;br /&gt;&lt;span
			class="byline-author"&gt;&lt;br /&gt;&lt;/span&gt;&lt;span
			class="byline-author"&gt;As you can probably tell from the video I did on Sky with a
			Google engineer&lt;/span&gt;&lt;span class="byline-author"&gt;, I always loved
			astronomy. I even put together (OK, with the help of some folks at Sally Ride Science and
			Google) a special KML showcase of some of my favorite extra-solar places -- nebulae where
			stars are born, remnants of exploding stars, and even a bunch of stars that have ... planets
			orbiting around them! (No, scientists haven't found any like Earth yet.)&lt;br
			/&gt;&lt;br /&gt;If you know any kids or teachers who like astronomy, send them to
			Sky (the &lt;a href="http://earth.google.com/sky/skyedu"&gt;resource
			page&lt;/a&gt; is a good start) -- and tell them to check out the Sally Ride Science
			KML feature.&lt;br /&gt;&lt;br /&gt;&lt;/span&gt;&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/147162401" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/147162401/view-from-sky.html"
			title="The view from the Sky"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/6830172786772282502/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/6830172786772282502"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/6830172786772282502"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/08/view-from-sky.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-6620110423379055944</id>
		<published>2007-08-20T20:55:00.000-07:00</published>
		<updated>2007-08-20T20:55:38.615-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="video"/>
		<title type="text">An update on Google Video feedback</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Bindu Reddy, Google
			Video Product Manager &lt;/span&gt;&lt;br /&gt;&lt;br /&gt;When your
			friends and well-intentioned acquaintances tell you that you've made a mistake, it's good to
			listen. So we'd like to say thank you to everyone who wrote to let us know that we had made a
			mistake in the case of &lt;i&gt;Google Video's Download to Own/Rent Refund Policy vs.
			Common Sense&lt;/i&gt;.&lt;br /&gt;&lt;br /&gt;To recap: we decided to
			end the Google Video download to own/rent (DTO/DTR) program, and are now refocusing our Google
			Video engineering efforts. The week before last, we wrote to Google Video DTO/DTR program
			customers to let them know that videos they'd already bought would no longer be
			playable.&lt;br /&gt;&lt;br /&gt;We planned to give these users a full refund
			or more. And because we weren't sure if we had all the correct addresses, latest credit card
			information, and other billing challenges, we thought offering the refund in the form of
			Google Checkout credits would entail fewer steps and offer a better user experience. We should
			have anticipated that some users would see a Checkout credit as nothing more than an extra
			step of a different (and annoyingly self-serving) kind. Our bad. Here's how we're hoping to
			fix things:&lt;br /&gt;&lt;br
			/&gt;&lt;ul&gt;&lt;li&gt;&lt;span style="background-color: rgb(255,
			255, 255);" &gt;We're giving a full refund -- as a credit card refund -- to everyone who
			ever bought &lt;/span&gt;&lt;span style="background-color: rgb(255, 255, 255);"
			&gt;a video. We'll need you to make sure we have your most recent credit card information,
			but once we know where to send the money, you'll get
			it.&lt;/span&gt;&lt;/li&gt;&lt;/ul&gt;&lt;ul&gt;&lt;li&gt;You
			can still keep the Google Checkout credit that you've received already. Think of it as an
			additional 'we're sorry we goofed' credit.
			&lt;/li&gt;&lt;/ul&gt;&lt;ul&gt;&lt;li&gt;We're going to
			continue to support playing your videos for another six months. We won't be offering the
			ability to buy additional videos, but what you've already downloaded will remain playable on
			your computer. &lt;/li&gt;&lt;/ul&gt; We take pride in moving quickly, and we
			think this philosophy helps to create lots of new and innovative products. But it also leads
			to errors that -- upon reflection and your feedback -- we need to rectify. This was one of
			them. We make mistakes; we do our best not to repeat them -- and we really do try to fix the
			ones we make. That said, the very least that our users should expect from us is that our
			mistakes be new and innovative, too. ;)&lt;br /&gt;&lt;br /&gt;We appreciate
			your responses, and hope our actions convey just how seriously we take everyone's
			feedback.&lt;img src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/146362431"
			height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/146362431/update-on-google-video-feedback.html"
			title="An update on Google Video feedback"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/6620110423379055944/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/6620110423379055944"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/6620110423379055944"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/08/update-on-google-video-feedback.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-7624384470156706803</id>
		<published>2007-08-20T06:48:00.000-07:00</published>
		<updated>2007-08-20T06:48:56.254-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="Asia"/>
		<category scheme="http://www.blogger.com/atom/ns#" term="search"/>
		<title type="text">Google Labs India</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by M T Raghunath and Gokul
			Nath Babu Manoharan, Software Engineers&lt;/span&gt;&lt;br /&gt;&lt;br
			/&gt;Keeping up with the spirit and celebrations of India's 60th year of Independence, we
			present to you a new platform that showcases our favourite ideas for Indian users: &lt;a
			title="http://labs.google.co.in/" href="http://labs.google.co.in/"
			target="_blank"&gt;Google India Labs&lt;/a&gt;. Enthusiastic bloggers noted our
			initial announcement on 15th August; now here's the full story.&lt;br /&gt;&lt;br
			/&gt;Though 60 years young, India has a history dating back to the dawn of civilization.
			The incredible diversity of this great nation is the kind of challenge Google loves. And in
			line with our mission of making information universally accessible, we're now offering an
			easier way to search in 14 Indian and South Asian languages. You don't need a special keyboard
			or software; all you need is a web browser, a mouse, and a Unicode font for your language. So
			whether you speak à¦…à¦¸à¦®à§€à¦¯à¦¼à¦¾ (&lt;a
			title="http://www.google.com/ig/adde?moduleurl=http://www.google.com/ig/modules/assamese_keyboard.xml"
			href="http://www.google.com/ig/adde?moduleurl=http%3A//www.google.com/ig/modules/assamese_keyboard.xml"&gt;Assamese&lt;/a&gt;),
			à¦¬à¦¾à¦‚à¦²à¦¾ (&lt;a
			title="http://www.google.com/ig/adde?moduleurl=http://www.google.com/ig/modules/bengali_keyboard.xml"
			href="http://www.google.com/ig/adde?moduleurl=http%3A//www.google.com/ig/modules/bengali_keyboard.xml"&gt;Bengali&lt;/a&gt;),
			àª—à«àªœàª°àª¾àª¤à«€ (&lt;a
			title="http://www.google.com/ig/adde?moduleurl=http://www.google.com/ig/modules/gujarati_keyboard.xml"
			href="http://www.google.com/ig/adde?moduleurl=http%3A//www.google.com/ig/modules/gujarati_keyboard.xml"&gt;Gujarati&lt;/a&gt;),
			à¤¹à¤¿à¤‚à¤¦à¥€ (&lt;a
			title="http://www.google.com/ig/adde?moduleurl=http://www.google.com/ig/modules/hindi_keyboard.xml"
			href="http://www.google.com/ig/adde?moduleurl=http%3A//www.google.com/ig/modules/hindi_keyboard.xml"&gt;Hindi&lt;/a&gt;),
			à²•à²¨à³à²¨à²¡ (&lt;a
			title="http://www.google.com/ig/adde?moduleurl=http://www.google.com/ig/modules/kannada_keyboard.xml"
			href="http://www.google.com/ig/adde?moduleurl=http%3A//www.google.com/ig/modules/kannada_keyboard.xml"&gt;Kannada&lt;/a&gt;),
			à´®à´²à´¯à´¾à´³à´‚ (&lt;a
			title="http://www.google.com/ig/adde?moduleurl=http://www.google.com/ig/modules/malayalam_keyboard.xml"
			href="http://www.google.com/ig/adde?moduleurl=http%3A//www.google.com/ig/modules/malayalam_keyboard.xml"&gt;Malayalam&lt;/a&gt;),
			à¤®à¤°à¤¾à¤ à¥€ (&lt;a
			title="http://www.google.com/ig/adde?moduleurl=http://www.google.com/ig/modules/marathi_keyboard.xml"
			href="http://www.google.com/ig/adde?moduleurl=http%3A//www.google.com/ig/modules/marathi_keyboard.xml"&gt;Marathi&lt;/a&gt;),
			à¤¨à¥‡à¤ªà¤¾à¤²à¥€ (&lt;a
			title="http://www.google.com/ig/adde?moduleurl=http://www.google.com/ig/modules/nepali_keyboard.xml"
			href="http://www.google.com/ig/adde?moduleurl=http%3A//www.google.com/ig/modules/nepali_keyboard.xml"&gt;Nepali&lt;/a&gt;),
			à¬“à¬¡à¬¼à¬¿à¬† (&lt;a
			title="http://www.google.com/ig/adde?moduleurl=http://www.google.com/ig/modules/oriya_keyboard.xml"
			href="http://www.google.com/ig/adde?moduleurl=http%3A//www.google.com/ig/modules/oriya_keyboard.xml"&gt;Oriya&lt;/a&gt;),
			à¨ªà©°à¨œà¨¾à¨¬à©€ (&lt;a
			title="http://www.google.com/ig/adde?moduleurl=http://www.google.com/ig/modules/punjabi_keyboard.xml"
			href="http://www.google.com/ig/adde?moduleurl=http%3A//www.google.com/ig/modules/punjabi_keyboard.xml"&gt;Punjabi&lt;/a&gt;),
			à¤¸à¤‚à¤¸à¥à¤•à¥ƒà¤¤à¤®à¥ (&lt;a
			title="http://www.google.com/ig/adde?moduleurl=http://www.google.com/ig/modules/sanskrit_keyboard.xml"
			href="http://www.google.com/ig/adde?moduleurl=http%3A//www.google.com/ig/modules/sanskrit_keyboard.xml"&gt;Sanskrit&lt;/a&gt;),
			à·ƒà·’à¶‚à·„à¶½ (&lt;a
			title="http://www.google.com/ig/adde?moduleurl=http://www.google.com/ig/modules/sinhala_keyboard.xml"
			href="http://www.google.com/ig/adde?moduleurl=http%3A//www.google.com/ig/modules/sinhala_keyboard.xml"&gt;Sinhala&lt;/a&gt;),
			à®¤à®®à®¿à®´à¯ (&lt;a
			title="http://www.google.com/ig/adde?moduleurl=http://www.google.com/ig/modules/tamil_keyboard.xml"
			href="http://www.google.com/ig/adde?moduleurl=http%3A//www.google.com/ig/modules/tamil_keyboard.xml"&gt;Tamil&lt;/a&gt;),
			or à°¤à±†à°²à±à°—à± (&lt;a
			title="http://www.google.com/ig/adde?moduleurl=http://www.google.com/ig/modules/telugu_keyboard.xml"
			href="http://www.google.com/ig/adde?moduleurl=http%3A//www.google.com/ig/modules/telugu_keyboard.xml"&gt;Telugu&lt;/a&gt;),
			we can help you find content on the web in your language. To get started, add one or more of
			these &lt;a title="http://labs.google.co.in/indic.html"
			href="http://labs.google.co.in/indic.html" target="_blank"&gt;iGoogle
			gadgets&lt;/a&gt; to your personalized iGoogle home page. You can use these gadgets to
			compose queries, and ask Google to search the vast Internet in your very own
			language.&lt;br /&gt;&lt;br /&gt;&lt;div style="text-align:
			left;"&gt;&lt;a onblur="try {parent.deselectBloggerImageGracefully();} catch(e) {}"
			href="http://bp3.blogger.com/_Ap14FtNN91w/RsXAMJPYiFI/AAAAAAAAANk/XwjJjR4OtbM/s1600-h/INDIA_languages.jpg"&gt;&lt;img
			style="cursor: pointer;"
			src="http://bp3.blogger.com/_Ap14FtNN91w/RsXAMJPYiFI/AAAAAAAAANk/XwjJjR4OtbM/s320/INDIA_languages.jpg"
			alt="" id="BLOGGER_PHOTO_ID_5099693467938359378" border="0"
			/&gt;&lt;/a&gt;&lt;br /&gt;&lt;/div&gt;&lt;br
			/&gt;&lt;div style="text-align: justify;"&gt;If you're interested in writing in
			Hindi, we have brought out the transliteration feature from &lt;a
			title="http://www.blogger.com/hindi" href="http://www.blogger.com/hindi"
			target="_blank"&gt;Blogger &lt;/a&gt;into an independent product of its own:
			&lt;a title="http://www.google.com/transliterate/indic/"
			href="http://www.google.com/transliterate/indic/" target="_blank"&gt;Google Indic
			Transliteration&lt;/a&gt;. This tool will let you type in Hindi, using an English
			keyboard. Type out words phonetically, and let Google convert them into the correct Hindi
			word. For example, type "Bharat" to see "à¤*à¤¾à¤°à¤¤". You'll soon discover that our sophisticated
			transliteration technology makes it&lt;a
			title="http://big.corp.google.com/~anupama/wahwah/transliteration-729266.bmp"
			href="http://big.corp.google.com/%7Eanupama/wahwah/transliteration-729266.bmp"&gt;
			&lt;/a&gt;really easy to compose in Hindi. Our algorithm might get the occasional word
			wrong, but it is always willing to learn. You can teach it by clicking on the wrong word and
			correcting it. This is also available as an &lt;a id="ki:6"
			title="http://www.google.com/ig/directory?hl=en&amp;url=indic_transliteration.xml iGoogle
			Gadget"
			href="http://www.google.com/ig/directory?hl=en&amp;amp;url=indic_transliteration.xml"&gt;iGoogle
			Gadget&lt;/a&gt;.&lt;br /&gt;&lt;br /&gt;&lt;a onblur="try
			{parent.deselectBloggerImageGracefully();} catch(e) {}"
			href="http://bp0.blogger.com/_Ap14FtNN91w/RsXBSZPYiGI/AAAAAAAAANs/KUPUk5CGEvY/s1600-h/INDIA-snippet.jpg"&gt;&lt;img
			style="cursor: pointer;"
			src="http://bp0.blogger.com/_Ap14FtNN91w/RsXBSZPYiGI/AAAAAAAAANs/KUPUk5CGEvY/s320/INDIA-snippet.jpg"
			alt="" id="BLOGGER_PHOTO_ID_5099694674824169570" border="0"
			/&gt;&lt;/a&gt;&lt;br /&gt;&lt;/div&gt;&lt;br /&gt;We've
			really enjoyed bringing these products to you, and we're &lt;a
			title="mailto:indialabs@google.com" href="mailto:indialabs@google.com"
			target="_blank"&gt;eager to hear from you&lt;/a&gt;. There is a new &lt;a
			title="http://groups.google.com/group/google-india-labs/"
			href="http://groups.google.com/group/google-india-labs/" target="_blank"&gt;user
			community&lt;/a&gt; for discussion around our new technologies, and we'll keep adding
			new things to our Labs page, so please visit us often.&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/146123399" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/146123399/google-labs-india.html"
			title="Google Labs India"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/7624384470156706803/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/7624384470156706803"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/7624384470156706803"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/08/google-labs-india.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-1149657540488555494</id>
		<published>2007-08-14T19:08:00.000-07:00</published>
		<updated>2007-09-05T14:59:42.791-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="Asia"/>
		<title type="text">Namaste India!</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by M T Raghunath and Gokul
			Nath Babu Manoharan, Software Engineers&lt;/span&gt;&lt;br /&gt;&lt;br
			/&gt;Happy 60th birthday, India! We can't wait to celebrate, but we're going to wait a few
			days for the formal unwrapping of our gift to Indian users. Check back and we'll have news
			shortly.&lt;img src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/144246010" height="1"
			width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/144246010/namaste-india.html"
			title="Namaste India!"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/1149657540488555494/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/1149657540488555494"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/1149657540488555494"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/08/namaste-india.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-304265446997713827</id>
		<published>2007-08-10T23:47:00.000-07:00</published>
		<updated>2007-09-05T14:58:00.532-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="ads"/>
		<category scheme="http://www.blogger.com/atom/ns#" term="policy and issues"/>
		<title type="text">Online ad-serving tests</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Alex Kinnier, Group
			Product Manager&lt;/span&gt;&lt;br /&gt;&lt;br /&gt;We're always
			experimenting and testing ways to deliver relevant and new kinds of ads, and as part of that,
			we recently started running a test of an ad serving technology that will help us understand
			online ad serving better, and allow us to experiment with some new approaches to privacy for
			third-party ad servers. The privacy features we'll test in these experiments follow some
			recently-announced policies, such as a &lt;a
			href="http://googleblog.blogspot.com/2007/07/cookies-expiring-sooner-to-improve.html"
			id="h-8r"&gt;shorter expiration date for the cookie&lt;/a&gt; set on your computer
			and &lt;a
			href="http://googleblog.blogspot.com/2007/06/how-long-should-google-remember.html"&gt;anonymization
			of the logs data after 18 months&lt;/a&gt;.&lt;br /&gt;&lt;br /&gt;In
			our ad-serving tests, we're introducing an &lt;a
			href="http://www.google.com/ads/gcc_privacy.html"&gt;opt-out mechanism&lt;/a&gt;
			so people can opt out of the test ad-serving cookie if they wish. In addition, weâ€™re going to
			experiment with ways the industry could provide improved transparency for consumers and
			providing users with additional controls over the data gathered by ad servers. Some of the
			ideas we're exploring include:&lt;br /&gt;&lt;ul&gt;&lt;li&gt;using
			"crumbled" cookies, so that the data typically associated with one unique identifying number
			or "cookie ID" will be broken up among multiple different cookies and diffuse the ad history
			of individual users;
			&lt;/li&gt;&lt;/ul&gt;&lt;ul&gt;&lt;li&gt;providing better
			forms of notice within ads, to help users understand who is serving the ads they see, and what
			data is being collected;
			and&lt;/li&gt;&lt;/ul&gt;&lt;ul&gt;&lt;li&gt;giving users the
			ability to provide feedback to us about the ads they like and don't like.
			&lt;/li&gt;&lt;/ul&gt;Like all experiments, these ideas may or may not work
			out. And they won't be effective unless the industry adopts them -- we are not likely to
			implement these ideas alone. But we are excited to start innovating in this area for our
			advertising customers and for our users. We welcome your &lt;a
			href="mailto:testadserving@google.com"&gt;feedback.&lt;/a&gt;&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/142842194" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/142842194/online-ad-serving-tests.html"
			title="Online ad-serving tests"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/304265446997713827/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/304265446997713827"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/304265446997713827"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/08/online-ad-serving-tests.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-5577095166600060902</id>
		<published>2007-08-09T16:04:00.001-07:00</published>
		<updated>2007-09-05T14:57:36.744-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="apps"/>
		<title type="text">A simple way to get more storage</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Ryan Aquino, Software
			QA Engineer Lead, Picasa Web Albums&lt;/span&gt;&lt;br /&gt;&lt;br
			/&gt;As someone who tests Google products daily, I know that the simplest solution is
			often the one that works best. In the case of online storage, whether it's a picture, a video
			or an email, you should just, well, be able to store it without having to worry about whether
			you've got enough space in each particular product. That's why the Picasa team is pleased to
			tell you that in a few hours we'll be rolling out extra storage that you can purchase to use
			across several Google products (today, Picasa Web Albums and Gmail; soon, other applications
			like Google Docs &amp; Spreadsheets). That will help make storage really useful, like
			letting you upload lots of full resolution images to Picasa Web Albums.&lt;br
			/&gt;&lt;br /&gt;When you reach the limit of free storage (i.e., 1GB for Picasa
			Web Albums, 2.8GB for Gmail), consider this your overflow solution. Plans start at $20/year
			for 6GB (yes, $5 cheaper than before), with larger plans ranging up to 250GB. If only testing
			everything were this easy. &lt;p&gt;&lt;/p&gt;We'll update this post as soon
			as we're ready to take your order.&lt;br /&gt;&lt;br /&gt;&lt;span
			style="font-weight: bold; font-style: italic;"&gt;Update:&lt;/span&gt; And we're
			live! To buy more storage, &lt;a href="https://www.google.com/accounts/ManageStorage"
			title="Manage Storage" target="_blank" onclick="return
			top.js.OpenExtLink(window,event,this)"&gt;go here.&lt;/a&gt;&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/142535792" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/142535792/simple-way-to-get-more-storage.html"
			title="A simple way to get more storage"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/5577095166600060902/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/5577095166600060902"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/5577095166600060902"/>
		<author>
			<name>A Googler</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/08/simple-way-to-get-more-storage.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-446357771847432890</id>
		<published>2007-08-09T07:25:00.000-07:00</published>
		<updated>2007-08-09T07:25:49.945-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="search"/>
		<title type="text">Finding fresh results</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Peeyush Ranjan,
			Engineering Manager and Hong Zhang, Software Engineer&lt;/span&gt;&lt;br
			/&gt;&lt;br /&gt;We work hard to keep our search results as fresh as possible so
			that they reflect the most up to date content on the web. However, given the immense medium
			the Internet is, it's hard to find all those pages that have just come into existence and make
			them available when people come looking for the latest information on new topics, whether it's
			a highly anticipated cell phone launch, news about a popular celebrity or the latest political
			maneuvers. What makes providing the latest information harder is the small amount of time we
			have between the page creation and when we'd like to serve those results to you.&lt;br
			/&gt;&lt;br /&gt;Despite these challenges, one thing should not be hard: finding
			the freshest results on the page. To make it easier for you to spot the newer pages among the
			search results, we are now going to tell you how long ago we've seen a page containing what we
			think you're looking for.&lt;br /&gt;&lt;br /&gt;For example, if on August 6th
			you were searching on Google.com for latest financial information following the Friday
			financial sector action, here's how that result would have looked in the past:&lt;br
			/&gt;&lt;br /&gt;&lt;a onblur="try {parent.deselectBloggerImageGracefully();}
			catch(e) {}"
			href="http://bp2.blogger.com/_Ap14FtNN91w/RriVrQizDmI/AAAAAAAAANA/TU4s-s-7ggA/s1600-h/Fresh+result-old.jpg"&gt;&lt;img
			style="cursor: pointer;"
			src="http://bp2.blogger.com/_Ap14FtNN91w/RriVrQizDmI/AAAAAAAAANA/TU4s-s-7ggA/s320/Fresh+result-old.jpg"
			alt="" id="BLOGGER_PHOTO_ID_5095987548777549410" border="0"
			/&gt;&lt;/a&gt;&lt;br /&gt;&lt;br /&gt;From this you could only
			see that we crawled this page at a day level granularity. But now when you do this search you
			will also be able to tell how long ago we noticed this page, so you can quickly pinpoint which
			of these is results is likely to contain more recent information. Here's the same example
			showing the annotation that tells you there's something new in the results we've seen
			recently.&lt;br /&gt;&lt;br /&gt;&lt;a onblur="try
			{parent.deselectBloggerImageGracefully();} catch(e) {}"
			href="http://bp1.blogger.com/_Ap14FtNN91w/RriWRAizDoI/AAAAAAAAANQ/0S-7GyFMtBM/s1600-h/fresh+result-new.jpg"&gt;&lt;img
			style="cursor: pointer;"
			src="http://bp1.blogger.com/_Ap14FtNN91w/RriWRAizDoI/AAAAAAAAANQ/0S-7GyFMtBM/s320/fresh+result-new.jpg"
			alt="" id="BLOGGER_PHOTO_ID_5095988197317611138" border="0"
			/&gt;&lt;/a&gt;&lt;br /&gt;&lt;br /&gt;So if you're looking for
			the most recent content on the web, this change should make it easier to find. And if you're a
			webmaster looking to tell us about all the new content on your site we haven't looked at yet,
			check out our support for &lt;a
			href="http://googlewebmastercentral.blogspot.com/2006/11/joint-support-for-sitemap-protocol.html"&gt;sitemaps&lt;/a&gt;.&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/142189976" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/142189976/finding-fresh-results.html"
			title="Finding fresh results"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/446357771847432890/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/446357771847432890"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/446357771847432890"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/08/finding-fresh-results.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-2188629670704479693</id>
		<published>2007-08-09T04:05:00.000-07:00</published>
		<updated>2007-08-09T04:06:24.258-07:00</updated>
		<category scheme="http://www.blogger.com/atom/ns#" term="environment"/>
		<title type="text">Is black the new green?</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Bill Weihl, Green
			Energy Czar&lt;/span&gt;&lt;br /&gt;&lt;br /&gt;Reducing climate
			change by saving energy is an important effort we should all join, and that's why we're very
			glad to see the innovative thinking going into a variety of solutions. One idea, suggested by
			the site called "Blackle" (which is not related to Google, by the way, though the site does
			use our &lt;a href="http://www.google.com/coop/cse/"&gt;custom search
			engine&lt;/a&gt;), is to reduce energy used by monitors by providing search with a
			black background. We applaud the spirit of the idea, but our own analysis as well as that of
			&lt;a
			href="http://blogs.wsj.com/numbersguy/does-a-darkened-google-really-save-electricity-104/"&gt;others&lt;/a&gt;
			shows that making the Google homepage black will not reduce energy consumption. To the
			contrary, on flat-panel monitors (already estimated to be 75% of the market), displaying black
			may actually &lt;span&gt;&lt;i&gt;increase
			&lt;/i&gt;&lt;/span&gt;energy usage. &lt;a
			href="http://techlogg.com/content/view/360/31/"&gt;Detailed results&lt;/a&gt; from
			a new study confirm this.&lt;br /&gt;&lt;br /&gt;As computers become a bigger
			part of more people's lives, they will consume an increasing amount of energy, which is why
			we've invested so much in &lt;a title="making our data centers efficient"
			href="http://googleblog.blogspot.com/2006/09/towards-more-efficient-computing.html"&gt;making
			our data centers efficient&lt;/a&gt; and we've &lt;a title="joined with others"
			href="http://googleblog.blogspot.com/2007/06/climate-savers-computing-initiative.html"&gt;joined
			with others&lt;/a&gt; to launch Climate Savers Computing, which has a goal of reducing
			total power consumption by more than 50% for all computers by 2010.&lt;br
			/&gt;&lt;br /&gt;There &lt;span&gt;are&lt;i&gt;
			&lt;/i&gt;&lt;/span&gt;some things you can do now to reduce the energy used by
			your computer, such as:&lt;br /&gt;&lt;ul&gt;&lt;li&gt;turn on the
			power management features. Virtually all computers today have the ability to switch into
			low-power modes automatically when they're idle; very few computers have this capability
			enabled! &lt;a
			href="http://www.microsoft.com/windowsxp/using/setup/learnmore/russel_02march25.mspx"&gt;Here's
			how &lt;/a&gt;to do it on computers running Windows
			XP.&lt;/li&gt;&lt;/ul&gt;&lt;ul&gt;&lt;li&gt;turn off your
			monitor and computer when you're not using
			them&lt;/li&gt;&lt;/ul&gt;&lt;ul&gt;&lt;li&gt;turn down the
			brightness on your
			monitor&lt;/li&gt;&lt;/ul&gt;&lt;ul&gt;&lt;li&gt;make sure
			your next computer meets the efficiency standards of &lt;a title="Climate Savers
			Computing" href="http://www.climatesaverscomputing.org/"&gt;Climate Savers Computing
			(&lt;/a&gt;an efficient computer uses up to 50% less energy than a conventional
			one)&lt;/li&gt;&lt;/ul&gt;&lt;ul&gt;&lt;li&gt;to find the most
			efficient PCs available today, look for the words "EnergyStar 4.0
			compliant."&lt;/li&gt;&lt;/ul&gt;&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/142383169" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/142383169/is-black-new-green.html"
			title="Is black the new green?"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/2188629670704479693/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/2188629670704479693"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/2188629670704479693"/>
		<author>
			<name>Karen</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/08/is-black-new-green.html</feedburner:origLink>
	</entry>
	<entry>
		<id>tag:blogger.com,1999:blog-10861780.post-5354141344931111537</id>
		<published>2007-08-08T17:54:00.000-07:00</published>
		<updated>2007-08-08T17:57:09.912-07:00</updated>
		<title type="text">Google Checkout back-to-school offers</title>
		<content type="html">&lt;span class="byline-author"&gt;Posted by Susan Taing, Associate
			Product Marketing Manager&lt;/span&gt;&lt;br /&gt;&lt;br /&gt;Checkout
			stores are offering &lt;a
			href="http://www.google.com/checkout/promotions.html#utm_source=google_blog%22"&gt;up to
			$20 in savings&lt;/a&gt; for the back-to-school season. Find out more on &lt;a
			href="http://googlecheckout.blogspot.com/2007/08/save-time-and-money-with-checkout-back.html"&gt;the
			Checkout blog&lt;/a&gt;.&lt;img
			src="http://feeds.feedburner.com/~r/blogspot/MKuf/~4/142189974" height="1" width="1"/&gt;</content>
		<link rel="alternate" type="text/html"
			href="http://feeds.feedburner.com/~r/blogspot/MKuf/~3/142189974/google-checkout-back-to-school-offers.html"
			title="Google Checkout back-to-school offers"/>
		<link rel="replies" type="application/atom+xml"
			href="http://googleblog.blogspot.com/feeds/5354141344931111537/comments/default"
			title="Post Comments"/>
		<link rel="self" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/5354141344931111537"/>
		<link rel="edit" type="application/atom+xml"
			href="http://www.blogger.com/feeds/10861780/posts/default/5354141344931111537"/>
		<author>
			<name>Molly Graham</name>
		</author>
		<feedburner:origLink>http://googleblog.blogspot.com/2007/08/google-checkout-back-to-school-offers.html</feedburner:origLink>
	</entry>

</feed>


```

---

### Post by kostkon on 2007-09-25
Could you please give your *XSLT* for every *entry* element?

---

### Post by DouglasAWh on 2007-09-26
I've got the code working in Opera (Linux) and IE (Windoze).  Still no luck with Firefox (Win or Lin).  If someone has a quick fix for Firefox, I'd love to hear it.

---

