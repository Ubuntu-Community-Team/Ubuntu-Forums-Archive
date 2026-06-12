---
title: "A script to filter an XML file."
date: 2007-10-12
forum: Programming Talk
---

### Post by musther on 2007-10-12
I've got a large xml file containing TV listings for my mythtv box, and I want to filter it so I'm left with just the channels I recieve.

It's in this form:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<!DOCTYPE tv SYSTEM "xmltv.dtd">
<tv lots=of tags=which give=basic_info>

<channel id="1012.dvb.guide">
	<display-name>Nat Geographic</display-name>
	<icon src="http://********/epg/icons/national_geographic.jpg" />
</channel>

#There are lots of the above channel sections, and then lots of the following programme sections.

<programme channel="1021.dvb.guide" start="20071013003000 +1300" stop="20071013012500 +1300">
	<title lang="eng">Sexiest Action Heroes</title>
	<desc>They are our sexy heroes and hell-raisers, the lucsious victors and vixens who play by their own rules and always hold the winning hand - smashing a few skulls in the process.</desc>
	<category>tvshow</category>
	<category>Reality</category>
	<rating system="SKY-NZ">
		<value>R16</value>
	</rating>
</programme>

</tv>

<!--
	[{'rating': '6', 'description': 'So then there's a bunch of footer info.....
```

So we have the sections;

```
Header stuff

Channels

Programmes

Footer stuff
```

So basically what I need to do is, from this, construct another file which has the header, the channels I have, the programmes on the channels I have, and then the footer stuff.

The difficult bit (as far as my bash text processing skills go) is filtering the channels and programmes.  I figure I'll put the channel ID's of the channels I want in a list in a file, from which the script can get them, then I suppose the best way would be to strip everything which doesn't match, so while I'll end up doing is:

Find a text string which goes:

```
<channel id="$i">******</channel>
```

and if $i isn't in the list, remove it, then do the same kind of thing for the programme entries.

---

### Post by thomasaaron on 2007-10-12
Doing that in Bash is probably going to be more trouble than it is worth.

Python has a couple of xml modules that will let you do this with a couple dozen lines of code.

Here is a tutorial on how to use on of them:
[http://pyxml.sourceforge.net/topics/](http://pyxml.sourceforge.net/topics/)

---

### Post by Wybiral on 2007-10-12
I wouldn't do this in BASH either. There is another good Python module designed to read feeds: [http://feedparser.org/](http://feedparser.org/)

EDIT:

Just noticed you didn't mention feed (I thought you did for some odd reason) and for plain XML there are several good parsers in Python.

---

### Post by pmasiar on 2007-10-14
ElementTree is excellent Python library for parsing XML. lightyears ahead of anything else I used. Whole tree is parsed into dict of dicts.

---

### Post by musther on 2007-10-14
Thank you, and thanks also to linuxquestions.org I've got a python and perl script which do the job nicely.

Now, which to use?  :-)

Thanks again.

---

### Post by pmasiar on 2007-10-14
I am not sure I understand: what is your question? You have two scripts and cannot decide which one to use? Which one you like more?

---

### Post by musther on 2007-10-14
I'm sorry, I didn't mean to mislead you, I was just joking about the two scripts.  But, if you're interested, I'm using the python as I'm busy learning it at the moment anyway.

Sorry about the misunderstanding :-)

---

### Post by pmasiar on 2007-10-15
OK no problem. I was not sure if you have more questions or if you are all set. Some people mark thread [Solved] when done. 

I bet that Python version is simpler to comprehend. :-)

---

