---
title: "Display weather on web site - python cgi"
date: 2005-12-12
forum: Programming Talk
---

### Post by anthro398 on 2005-12-12
I wrote a little python cgi script to parse National Weather Service Internet Weather Source data and display specified fields on my web site.  I thought it may be useful to anyone else who might be annoyed by the corporate graphics and lack of control over display offered by the avaiable applets.  It's reasonably fast and robust and can be extended to any of the available IWS data fields.  I couldn't find any free and open source, parsable xml weather data so I wrote this.  Give it a look.  Suggestions would be appreciated.

See it in action at: [http://www.braggtown.com/webcam.html]("http://www.braggtown.com/webcam.html")
Download it at: [http://www.braggtown.com/projects.html]("http://www.braggtown.com/projects.html")

My display of the data is quite plain, but looking at the script you'll see that it's very easy to modify it to your site design.  Enjoy.

nb.  I should have noted that this script will only work for the US National Weather Service including the United States and it's territories.  My apologies to the rest of the world.

Please post back if you decide to use it.  I'd love to see how extensible it is.

---

### Post by GazaM on 2005-12-12
Thanks anthro398. I have been looking for info on python web programming and have been getting pretty agitated... this has helped a lot. I don't actually want the weather info, I am interested in making a script for displaying my Last.fm last played songs on my website without using any PHP. If you would like to create the script for me that would be fine ;) I am wondering though, how would I go about calling on the script from my html page, I don't understand anything about cgi scripting (although I am fine with xHTML and CSS). Are there any hosts which provide Python support or will I need my own web server?

---

### Post by anthro398 on 2005-12-12
The first, and probably most important, question is are you serving the web site from the same computer you're listening to music on.  That would make this whole thing a lot easier.   If they are one and the same machine the following might get you started.

You could use the [open]("http://python.org/doc/2.4.2/tut/node9.html#SECTION009200000000000000000") call to open the fm file and read it, parse the contents for the song and put that into a variable. 

Depending on the structure of the fm file (I've never seen one), you could also use  [commands.getoutput()]("http://python.org/doc/2.4.2/lib/module-commands.html") in combination with cat and grep, which might be faster.

---

### Post by GazaM on 2005-12-12
anthro... Audioscrobbler now have 'data feeds' online to make this kind of thing much easier. My recent tracks list is available in plain .txt, .xml and .rss online. I'm assuming that the xml version would allow for much more control on formatting and precision because of it having the data split into tags (eg. <artist>Audioslave</artist>. I am only learning Python and so find myself confused easily when trying to learn how to properly parse the files, even just plain text files. Here is a link to an example recent-tracks xml... [link]("http://ws.audioscrobbler.com/1.0/user/RJ/recenttracks.xml"). I'd appreciate some help with this if you know how to do this and could spare the time, but not to worry if you can't, I am happy with your script as reference at least. My MSN and Yahoo are in my profile, if you want any other contact details just PM me.

<edit>I have made a basic script which parses the information from the .txt version of the data feed and prints as '<li>track</li>' which is what I wanted. The only thing I need now is hosting on which I can test it :P I doesn't work locally and my current free hosting doesn't support PHP let alone Python cgi scripting... I may be able to test it out soon though. Anthro398, I'd still be interested if you could teach me some stuff about cgi scripting and maybe help me improve the script to include some missing stuff, such as displaying 'no recent tracks' when the text file is empty.

---

### Post by GazaM on 2005-12-13
Ok, I've been reading up on xml parsing and have made a first-draft of a script. This is MUCH more flexible than the txt version as it allows you to split the elements for formatting and include any more data as you see fit. I don't yet have an appropriate host, but it works fine in the terminal as does the weather.cgi script provided by anthro. Here it is:

```
#!/usr/bin/python
#Python Last.FM recent played tracks v 0.1
#author - GazaM
from urllib import urlopen
from xml.dom import minidom

#here is where we set the user variable and open the appropriate xml file from the internet and parse it
user = 'GazaM' #change this to your own username!
web = urlopen('http://ws.audioscrobbler.com/1.0/user/'+user+'/recenttracks.xml')
xmldoc = minidom.parse(web)
web.close()
print "Content-Type: text/html\n"
#this is where we find the appropriate tags in the xml file and create the html code from the data
#note that thanks to the ease of use of the python xml module it would be very easy to extend this script
#to include other info, such as date, link etc... but this is minimal as I want it to fit into the sidebar of my blog
tagartist = xmldoc.getElementsByTagName('artist')
tagsong = xmldoc.getElementsByTagName('name')
for i in range(0, 10):
    print '<li><b>'+tagartist[i].childNodes[0].data+' - </b>'+tagsong[i].childNodes[0].data+'</li>'
#This script is the very first draft, I will include funcionality to display a 'no recent tracks' message if the file
#is empty, once I get the time / knowledge :P
```

---

### Post by GazaM on 2005-12-14
<edit>Removed plea for help, figured it out! Turns out apache uses /usr/lib/cgi-bin for the cgi-bin and not /var/www/cgi-bin like I had expected. It is now working perfectly! I will include a screenshot later. I'm also going to start work on adding the functionality to use a cached file instead of retrieving it from audioscrobbler every single time, maybe by checking to see how old the cached file is and retrieving and overwriting the cached version if it is over a certain time in minutes (if this is possible).

PS. Sorry for hijacking your thread anthro, I really appreciate you posting your script and making me realise that this type of thing is possible with python. It is something for which I found it extremely hard to find tutorials, maybe I should create one on my site once it goes live! If/when I release this script on audioscrobbler forums or elsewhere I'll be sure to give you a mention, unless you'd rather not.
```
#!/usr/bin/python
#Python Last.FM recent played tracks v 0.2
#author - GazaM
#Changelog - added support for a 'no recently played tracks' message when no tracks are listed in the file,
#changed the way in which tracks are printed which now doesnt call an error when there are less than ten tracks played
from urllib import urlopen
from xml.dom import minidom

#here is where we set the user variable and open the appropriate xml file from the internet and parse it
user = 'GazaM' #change this to your own username!
web = urlopen('http://ws.audioscrobbler.com/1.0/user/'+user+'/recenttracks.xml')
xmldoc = minidom.parse(web)
web.close()
print "Content-Type: text/html\n"
#this is where we find the appropriate tags in the xml file and create the html code from the data
#note that thanks to the ease of use of the python xml module it would be very easy to extend this script
#to include other info, such as date, link etc... but this is minimal as I want it to fit into the sidebar of my blog
tagartist = xmldoc.getElementsByTagName('artist')
tagsong = xmldoc.getElementsByTagName('name')
track = xmldoc.getElementsByTagName('track')
if len(xmldoc.toxml()) < 100:
    print '<li>No recently played tracks</li>'
else:
    i = 0
    for line in track:
        print '<li>'+tagsong[i].childNodes[0].data+' - <i>'+tagartist[i].childNodes[0].data+'</i></li>'
        i = i+1

```

---

### Post by Van_Gogh on 2005-12-14
I just like to say thanks to GazaM for posting his script. I've been trying to get a simple understanding of Python & XML, but haven't been able to 'get'. Untill now, I think:p .

Anyway, it looks simpler than most other XML things I've looked at(a good thing), clean and Pythonic. Good stuff :cool:

---

### Post by GazaM on 2005-12-14
Thanks Van Gogh, appreciate the good comment. I am only beginning to learn Python, and it is also the first programming language I am learning. I'm enjoying it so far, it's very rewarding to see your own code actually working. I got most of my info on xml parsing through the diveintopython free book (comes with ubuntu afaik, but i just got the pdf from the website before i noticed it was preinstalled :P)... the book isn't really beginner friendly, but the xml chapters are fairly straightforward, you should check it out to get an understanding, or just add me to your IM or PM me, I wouldn't mind sharing tips with another learning Python, co-operation can only lead to more ideas! also check out the free online book biteofpython, it's great for beginning, but doesnt really feature any xml. I'm gonna post this on Audioscrobbler forums now, but I better get cracking on including some sort of caching function!

---

### Post by Van_Gogh on 2005-12-14
Oh, I'm not *completely* new to Python, I meant to say that I have difficulties using Python with XML. Anyway, I started learning Python about a year ago or so. So I think I'm probably on a average(or is that mediocre :rolleyes: ) level.

I remember I used *A Bite of Python* too. It's a really great beginner's book, I liked it a lot. The second one I did was *Think like a Computer Scientist*. It was a bit more difficult, but also more in-depth, which is great for a second book. Maybe you could look into it, if *Dive into Python* is too difficult. I've rever really read *Dive into Python* myself. A bit strange, as I've heard a lot of good things about it, so I think I will start to read it soon, or at least the XML part.

I don't really do IM much, but when I do I use Skype, where I'm TerjiCPH. I normally don't mind helping people out if I can. :KS 

Regards and good luck with your Python programming

---

### Post by Van_Gogh on 2005-12-15
Just one more thing about that XML-script. I think this may be slightly better:

```

#!/usr/bin/python
#Python Last.FM recent played tracks v 0.2
#author - GazaM
#Changelog - added support for a 'no recently played tracks' message when no tracks are listed in the file,
#changed the way in which tracks are printed which now doesnt call an error when there are less than ten tracks played
from urllib import urlopen
from xml.dom import minidom

#here is where we set the user variable and open the appropriate xml file from the internet and parse it
user = 'GazaM' #change this to your own username!
web = urlopen('http://ws.audioscrobbler.com/1.0/user/'+user+'/recenttracks.xml')
xmldoc = minidom.parse(web)
web.close()
print "Content-Type: text/html\n"
#this is where we find the appropriate tags in the xml file and create the html code from the data
#note that thanks to the ease of use of the python xml module it would be very easy to extend this script
#to include other info, such as date, link etc... but this is minimal as I want it to fit into the sidebar of my blog
track_tags = xmldoc.getElementsByTagName('track')
if not track_tags:
    print '<li>No recently played tracks</li>'
else:
    for track in track_tags:
        tagartist = track.getElementsByTagName('artist')[0]
        tagsong = track.getElementsByTagName('name')[0]
        print '<li><b>'+tagartist.childNodes[0].data+' - </b>'+tagsong.childNodes[0].data+'</li>'

```

What you are really interested in are the track-nodes and their contents, working with them is probably better than directly with the artist- and song-nodes. it also makes exiting("the IF not track_tags" part) more elegant, I think.

Anyway, you can take it for what it's worth.:)

---

### Post by GazaM on 2005-12-15
Ok... new release time. First off I'd like to say a BIG thanks to Van Gogh for helping me out for almost 2 hours this morning, without him the script would be nowhere near the quality it is now! Van Gogh, I look forward to hearing your comments on the cache functionality you left me implementing earlier. Ok, so first here is the code:
```
#!/usr/bin/python
#Python Audioscrobbler Recently Played Script v 0.8
#authors - GazaM, Van Gogh
#special thanks - anthro398

import os
from time import time
from urllib import urlopen
from xml.dom import minidom

print "Content-Type: text/html\n"

xmlfile = '/var/www/test/recentcache.xml' #change this to point to the cache file you create
cache_age = os.path.getmtime(xmlfile)
if (time() - cache_age)/60 <15:
    xmldoc = minidom.parse(xmlfile)
    track_tags = xmldoc.getElementsByTagName('track')
    if not track_tags:
        print '<li>No recently played tracks</li>'
    else:
	for track in track_tags:
            tagartist = track.getElementsByTagName('artist')[0]
            tagsong = track.getElementsByTagName('name')[0]
            print '<li>'+tagsong.childNodes[0].data+'<i> - '+tagartist.childNodes[0].data+'</i></li>'
else:
    user = 'GazaM' #change this to your own username!
    web = urlopen('http://ws.audioscrobbler.com/1.0/user/'+user+'/recenttracks.xml')
    f = open(xmlfile, 'w')
    f.write(web.read())
    web.close()
    f.close()
    xmldoc = minidom.parse(xmlfile)
    track_tags = xmldoc.getElementsByTagName('track')
    if not track_tags:
        print '<li>No recently played tracks</li>'
    else:
        for track in track_tags:
            tagartist = track.getElementsByTagName('artist')[0]
            tagsong = track.getElementsByTagName('name')[0]
            print '<li>'+tagsong.childNodes[0].data+'<i> - '+tagartist.childNodes[0].data+'</i></li>'

```
Ok, and here's the screenshot I promised. I don't yet have a live example, but I'm working on getting myself a server to host my own site soon. But sure there's the code for you to use yourself. Please note that the script is extremely flexible in the output of the html, so using css it is possible to have virtually any look you want, the one in the screenshot is just one I made quickly for testing purposes, not very nice.

[[IMG]http://img209.imageshack.us/img209/729/screenshot40dk.th.png[/IMG]](http://img209.imageshack.us/my.php?image=screenshot40dk.png)

Ok, there are a few things which I still want to implement. First off I'd like to be able to create a cache file if none is present. At the moment, the user has to get the xml from ws.audioscrobbler... and write it to the desired directory and filename. This isn't ideal for unexperienced users, even though it's only a once off occurrence and the script will take care of it forever after that. 

I would also like to include some kind of function to auto-detect the folder to put the cached file in... I myself was confused by the fact that you have to refer to the full *nix file location in the script, as opposed to just in relation to the root of the webfolders.

Other than that I think it is pretty much done, it's extremely flexible and customisable to boot. Hope to be back soon with an update.

<edit>Forgot to explain the cache implementation... the script now basically checks to see if the cached xml file is 15 minutes or more old compared to the current time; if it is, the script will get the updated file from the audioscrobbler site, overwrite the cache file with it and then parse the xml file etc... if the file is less than 15 minutes old, the script will simply read from the cache and not download anything from the web. This helps speed up loading of the web page a lot!

---

### Post by Van_Gogh on 2005-12-15
I see you're keeping yourself busy, that's great.

I took a quick look at your code and there are some issues(there always are). For one thing, you don't ever load the web-based XML-file - only the diskbased one(the "xmldoc = minidom.parse(xmlfile)"-part in the "else"-part is wrong). I corrected that. Also there is some code fluff that I removed and lastly I moved the "user = 'GazaM' #change this to your own username!"-part up to the start of the file, where userinput variables belong and I moved the first print-statement down, so all the print stuff is collected. That last part is of course *very strictly* IMHO and a matter of mere coding style, but it divided the code into four distinct parts: (1) imports, (2) path & username declaration, (3) XML-parsing and (4)outputting. I think that's nice.
Anyway, the code is so small so if you don't like it you can just move stuff back again:p 

The new code is:
```

#!/usr/bin/python
#Python Audioscrobbler Recently Played Script v 0.8
#authors - GazaM, Van Gogh
#special thanks - anthro398

import os
from time import time
from urllib import urlopen
from xml.dom import minidom

xmlfile = '/var/www/test/recentcache.xml' #change this to point to the cache file you create
user = 'GazaM' #change this to your own username!

cache_age = os.path.getmtime(xmlfile)
if (time() - cache_age)/60 <15:
    xmldoc = minidom.parse(xmlfile)
else:
    web = urlopen('http://ws.audioscrobbler.com/1.0/user/'+user+'/recenttracks.xml')
    f = open(xmlfile, 'rw')
    f.write(web.read())
    xmldoc = minidom.parse(f)
    f.close()
    web.close()

print "Content-Type: text/html\n"
track_tags = xmldoc.getElementsByTagName('track')
if not track_tags:
    print '<li>No recently played tracks</li>'
else:
    for track in track_tags:
        tagartist = track.getElementsByTagName('artist')[0]
        tagsong = track.getElementsByTagName('name')[0]
        print '<li>'+tagsong.childNodes[0].data+'<i> - '+tagartist.childNodes[0].data+'</i></li>'

```

Of course it can be made even better, but I think I have meddled enough already: the fun of programming is a lot about the fun of learning new stuff and you don't learn if someone does everything for you ;)

---

### Post by GazaM on 2005-12-15
Hey Van Gogh, those are some really nice changes. I was going to put the user variable to the top like you did, but had to get away from the computer for a break, so just decided to leave it until the next update. I really like the way you cleaned up the code and shortened it a lot.

By the way, the "xmldoc = minidom.parse(xmlfile)" in the else part does in fact work, you'll notice that I have updated the cache file with the new file just beforehand and so the file it is reading is in fact the latest one, but you're style is still a massive improvement IMO.

I ensure you that I'm learning a TON from your input, even looking at your style of coding has got me constantly thinking of ways to clean up my code, before I even write it. I'm going to take another break from the pc, I'm tired and my eyes are burning from looking at the screen :P. I'll get to work on implementing the features I talked about earlier later on, and then hopefully when Audioscrobbler.net is back up we can post it on the dev web services forums, which are packed with PHP scripts, in fact I think this is the first Python script of it's kind, but don't hold me to that, I just have never seen or heard of another on the audioscrobbler forums.

<edit>Van Gogh, I'm getting an error when using your script, so I'm gonna have to look over it later when I get back.

---

### Post by Van_Gogh on 2005-12-15
oh, I seemed to introduce a bug into your code by trying to correct a bug :o .
I completely misunderstood your code. Sorry.

So, you could go back to your version and it will be fine, or you could do:
```

cache_age = os.path.getmtime(xmlfile)
if (time() - cache_age)/60 >15:
    web = urlopen('http://ws.audioscrobbler.com/1.0/user/'+user+'/recenttracks.xml')
    f = open(xmlfile, 'w')
    f.write(web.read())
    web.close()
    f.close()
xmldoc = minidom.parse(xmlfile)

```

removing even more fluff.

Finally, I might tell you that you don't need to save the xml-file to harddisk, you could just keep it in memory as a string, which will simplify your code even more. Anyway, it's fine as it is now, so just do it if you want to.

---

### Post by GazaM on 2005-12-15
Van Gogh, the point of writing the file to memory if the older one is longer than 15 minutes old is to replace the old one... so that if the file is under 15 minutes old the script will read the file directly from the hard-drive thus taking away the time taken to fetch the file from audioscrobbler... it 'is' the point of the caching function.

---

### Post by Van_Gogh on 2005-12-15
Hmm, ok. My plan was that the program was going to run continously in a simple while loop, but now I think about it, AFAIK cgi scripts are only run when they are called, so my idea doesn't seem to work.

Anyway, as I said it wasn't a big deal and now it is even less of a big deal;)

---

### Post by GazaM on 2005-12-15
Ok, I've been looking at both my and Van Gogh's code and I think I have managed to clean the script up nicely, along with making it work pretty efficiently. I think you'll agree Van Gogh, at least I hope so, as I spent quite some time trying to figure out the issues (but maybe that's just because of my novice python knowledge :p ). Here's the new improved code,
```
#!/usr/bin/python
#Python Audioscrobbler Recently Played script v 0.8.5
#authors - GazaM, Van Gogh
#special thanks - anthro398

import os
from time import time
from urllib import urlopen
from xml.dom import minidom

xmlfile = '/var/www/test/recentcache.xml'
user = 'GazaM'
cache_age = os.path.getmtime(xmlfile)

if (time() - cache_age)/60 >15:
    web = urlopen('http://ws.audioscrobbler.com/1.0/user/'+user+'/recenttracks.xml')
    f = open(xmlfile, 'w')
    f.write(web.read())
    web.close()
    f.close()

xmldoc = minidom.parse(xmlfile)
track_tags = xmldoc.getElementsByTagName('track')

print 'Content-Type: text/html\n'

if not track_tags:
    print '<li>No recently played tracks</li>'

else:
    for track in track_tags:
        tagartist = track.getElementsByTagName('artist')[0]
        tagsong = track.getElementsByTagName('name')[0]
        print '<li>'+tagsong.childNodes[0].data+'<i> - '+tagartist.childNodes[0].data+'</i></li>'
```

I'm pretty sure this code is pretty good, at least it's the best I can think of in my tired state :smile: . Anyways, comments, feedback and suggestions are not just welcome, they're encouraged!

GazaM

---

### Post by Van_Gogh on 2005-12-15
Looking good and ready to roll :cool:. Maybe you want to do some checks to see if the "/var/www/test/recentcache.xml"-file exists or not and then take the appropriate action. Or you could just use it as it is now and just correct eventual errors as they come along :o.

Good luck with your website and future programming.

---

### Post by anthro398 on 2006-01-06
I've been playing around with the minidom parser and thought I'd write a little python cgi that parses rss feeds and displays them on a web site.  I know there are some php and python scripts out there for this but that wouldn't be a learning experience.  I've got it up and working at [http://www.prairienet.org/~jtuttle/rss.html]("http://www.prairienet.org/~jtuttle/rss.html") .  I'd love to hear comments.  I just saw in this thread a way to check cache time.  I'm sure it would speed up the load if I didn't have to pull each link each time the page is visited.    You can see that there is a problem with unicode characters, but I'll try to work that out later.

```

#!/usr/bin/python

# XML/RSS parser to grab and display feeds on web page
# WISH LIST:
## dynamic table of contents with links to page sections
## cgi selector form to allow user to select catagories like tech, politics, world



### Import Python modules
from urllib import urlopen
from xml.dom import minidom

### Set application variables here
feeds = ["http://osnews.com/files/recent.rdf", "http://rss.slashdot.org/Slashdot/slashdot", "http://distrowatch.com/news/dw.xml", 
"http://news.zdnet.com/2509-1_22-0-20.xml"]
# http://osnews.com/files/recent.rdf, http://thinkprogress.org/feed/, http://rss.slashdot.org/Slashdot/slashdot, http://www.atimes.com/atimes/atol.xml, http://distrowatch.com/news/dw.xml
super_item_object_list = []
feed_list = []

# getFeedTitle  Aquire the title of each rss feed
def getFeedTitle(rss_xml):
	channel_element = rss_xml.getElementsByTagName('channel')
        feed_title = (channel_element[0].getElementsByTagName('title')[0]).childNodes[0].data
        feed_link = (channel_element[0].getElementsByTagName('link')[0]).childNodes[0].data
        feed_list_object = [feed_title, feed_link]
	feed_list.append(feed_list_object)
	
	

# getChildNodes takes list of items and append child nodes of each item to list
def getChildNodes(item_list):
	item_object_list = []
        for item in item_list: 
        	try:
        		title = (item.getElementsByTagName('title')[0]).childNodes[0].data
        		link = (item.getElementsByTagName('link')[0]).childNodes[0].data
			description = (item.getElementsByTagName('description')[0]).childNodes[0].data
			item_object = [title, link, description]
			item_object_list.append(item_object)

		except:
			print "Failed item"
			pass
	super_item_object_list.append(item_object_list)
			
			
for url in feeds:
	try:			
		content = urlopen(url).read()
		rss_xml = minidom.parseString(content)
		getFeedTitle(rss_xml)
		item_list = rss_xml.getElementsByTagName('item')
		feed_items = getChildNodes(item_list)		
	except IOError:
		print " No valid feed at ", url
		pass				

i = 0
print "Content-Type: text/html\n"
for feed in feed_list:
	print '<br /><h1 align="center"><a href="%s">%s</a></h1>' % (feed[1], feed[0])  #(link, title)
	for story in super_item_object_list[i]:
		try:
			print '<a href="%s">%s</a><br />%s<br /><br >' % (story[1], story[0], story[2])  #(link, title, description)
	        except:
			pass

	i += 1	
	print "<hr />"
				


```

---

### Post by anthro398 on 2006-01-06
Now that I've had a moment to look at the problem with my rss parser script I see that it fails to grab any text after ascii codes (eg, &amp;) in xml elements that containt these codes.  I don't really understand why mindom would fail there.  It should pull all of the text out of the element including these codes. 

I guess I could use regular expressions to search for and replace/remove these but I really don't want to and I don't understand why this is an issue.  If anyone has any ideas about this please share them.  Thanks.

---

### Post by GazaM on 2006-01-06
Hey anthro398, good to see you return to your original thread! I've been working on the audioscrobbler script and some other big projects which is why there's been such a long delay with me releasing a version 1.0 of the Audioscrobbler script. I'll be making an 'official' thread about it this week.

I've been doing a WHOLE lot of work with web development and python for my new website, which I'll also hopefully link to within the new Audioscrobbler thread soon. Basically I've been pain-stakingly designing myself a new website, and making it look nice too (yeah I'm into art too, hopefully I'll have some of that to put on my website as well)! Python is at the heart of this new website, and I'm interested in using Python to create a range of web applications and scripts. I'm actually developing a simple GTK blogging client in Python too, but there's no underlying 'blogging api' to my site, simply a file into which the posts are put, then are included into the main page using a server side include.

I'd be very interested in getting any help available in developing these applications and service, maybe even creating our own proper secure blogging api. I'll post more about it within the Audioscrobbler thread as soon as I get to creating it.

PS. Anthro, I had problems dealing with non-standard characters in my script also, which turned out to be extremely easy to fix. All it required for me was a .encode('utf-8') call after getting the text, eg:

```
track.getElementsByTagName('artist')[0].childNodes[0].data.encode('utf-8')
```

This, pretty obviously, encodes the text into the appropriate encoding for your website... so just switch the ('utf-8') in your script to whichever encoding type your site uses. Hope that helps, and fair play on the script, funnily enough it is something I was planning on doing... we should definitely work together on creating a few nice web scripts. I'll be back with some more helpful critique soon, but it's 1.40am here and I have work early in the morning :P

---

### Post by anthro398 on 2006-01-06
GazaM,

Collaboration sounds like fun.  I'm just goofing off really, though.  I'm looking around at ways to convert FGDC metadata from geospatial data into Qualified Dublin Core and METS metadata for preservation at work.  I'm trying to decide how to implement either Python, XSLT, or both for parsing out the XML.

Anyway, thanks for the encoding tip, but I don't think that's my problem.  The getElementsByTagNames seems to stop reading the text data from elements when it encounters a single or double quote so I was thinking perhaps I should triple quote the print statement, but I tried that and it didn't work.  I still get this in the output:
```
>Highlights: EuroBSDCon 2005</a><br />"<br /><br >
```
The line should start with a quote, but continue past it.

You know, in grad school another student and I wrote a full-text indexer and search engine in perl for a class project.  It worked great on structured XML documents.  You could search by keyword, author, journal, or date.  We even got boolean and word poximity searching, which made the results pretty accurate.

Thanks for the help.

---

### Post by anthro398 on 2006-01-06
Do you ever feel like an idiot replying to your own posts?  Anyway...

Here's the magic line:
```
rss_xml.normalize()
```

So, altogether I have: 
```

#!/usr/bin/python

# XML/RSS parser to grab and display feeds on web page
# WISH LIST:
## dynamic table of contents with links to page sections
## cgi selector form to allow user to select categories like tech, politics, world



### Import Python modules
from urllib import urlopen
from xml.dom import minidom

### Set application variables here
feeds = ["http://osnews.com/files/recent.rdf", "http://rss.slashdot.org/Slashdot/slashdot", "http://distrowatch.com/news/dw.xml",
"http://news.zdnet.com/2509-1_22-0-20.xml", "http://fxfeeds.mozilla.org/rss20.xml"]
# http://osnews.com/files/recent.rdf, http://thinkprogress.org/feed/, http://rss.slashdot.org/Slashdot/slashdot, http://www.atimes.com/atimes/atol.xml, http://distrowatch.com/news/dw.xml
super_item_object_list = []
feed_list = []

# getFeedTitle  Aquire the title of each rss feed
def getFeedTitle(rss_xml):
        channel_element = rss_xml.getElementsByTagName('channel')
        feed_title = (channel_element[0].getElementsByTagName('title')[0]).childNodes[0].data.encode('iso-8859-1')
        feed_link = (channel_element[0].getElementsByTagName('link')[0]).childNodes[0].data.encode('iso-8859-1')
        feed_list_object = [feed_title, feed_link]
        feed_list.append(feed_list_object)



# getChildNodes takes list of items and append child nodes of each item to list
def getChildNodes(item_list):
        item_object_list = []
        for item in item_list:
                try:
                        title = (item.getElementsByTagName('title')[0]).childNodes[0].data.encode('iso-8859-1')
                        link = (item.getElementsByTagName('link')[0]).childNodes[0].data.encode('iso-8859-1')
                        description = (item.getElementsByTagName('description')[0]).childNodes[0].data.encode('iso-8859-1')
                        item_object = [title, link, description]
                        item_object_list.append(item_object)

                except:
                        print "Failed item"
                        pass
        super_item_object_list.append(item_object_list)


for url in feeds:
        try:
                content = urlopen(url).read()
                rss_xml = minidom.parseString(content)
                rss_xml.normalize()
                getFeedTitle(rss_xml)
                item_list = rss_xml.getElementsByTagName('item')
                feed_items = getChildNodes(item_list)
        except IOError:
                print " No valid feed at ", url
                pass

i = 0
print "Content-Type: text/html\n"
for feed in feed_list:
        print """<br /><h1 align="center"><a href="%s">%s</a></h1>""" % (feed[1], feed[0])  #(link, title)
        for story in super_item_object_list[i]:
                try:
                        print """<a href="%s">%s</a><br />%s<br /><br >""" % (story[1], story[0], story[2])  #(link, title, description)
                except:
                        pass

        i += 1
        print "<hr />"

```

You can see that it works correctly now.  [http://braggtown.com/scgi-bin/rss.cgi]("http://braggtown.com/scgi-bin/rss.cgi").  Now I need to implement the selector form to choose categories and/or individual feeds.  I was thinking of creating a text box to allow users to add feeds, but that's a little thought showed that to be a bad idea.  I'd also like to create a dynamic table of contents with links down the page to each feed title.

---

### Post by anthro398 on 2006-01-07
Had some time this afternoon and thought I'd play around with this again.  I have a pretty nice working model up at [http://braggtown.com/scgi-bin/rss.cgi]("http://braggtown.com/scgi-bin/rss.cgi").  I still need to implement the display options which will be easy.  I got the dynamic table of contents named anchors up.  It's kind of a mess and I had to import some html template pages to get it to look like the rest of my site without putting a great deal of html in the script.  It isn't terribly stable, however.  There are so many sites that use wonky rss feeds and I don't want to have to code for every possibility.

So, it's highly site dependent presently.  I'd like to clean it up, make it more portable, take out any hard-coded parameters, and make it available.  Let me know what you think.

One question I have is, how can I pass parameters from the form with the post method to the script without passing directly to the script.  What I mean is, I prefer to hide cgi scripts as server side includes in xhtml pages.  I can't pass to an embedded cgi that way, though.  I don't think so anyway.  I admit I didn't try it.  Just doesn't seem like it would work.  Maybe I can pass as parameters in the url and have the cgi parse the url for parameters.

```

#!/usr/bin/env python

# rss_parser.cgi  www.prairienet.org/~jtuttle/  1/2006
# XML/RSS parser to grab and display feeds on web page
# WISH LIST:
## Still need to implement display choices and clean up this mess


### Import Python modules
import cgi, cgitb; cgitb.enable()
from urllib import urlopen
from xml.dom import minidom

# Global.  Class to hold global variables.  Aleviates having to pass references between functions.  
class Global:
	feeds = []
	super_item_object_list = []
	feed_list = []	
	url_dict = {"slashdot": "http://rss.slashdot.org/Slashdot/slashdot", "osnews": "http://osnews.com/files/recent.rdf", \
		"distorwatch": "http://distrowatch.com/news/dw.xml", "zdnet": "http://news.zdnet.com/2509-1_22-0-20.xml", \
		"bbc": "http://fxfeeds.mozilla.org/rss20.xml", "thinkprogress": "http://thinkprogress.org/feed/", \
		"asiatimes": "http://www.atimes.com/atimes/atol.xml", "ucimc": "http://indymedia.us/main-features-content.rss", \
		"crooks": "http://www.crooksandliars.com/rss.xml", "guardian": "http://www.guardian.co.uk/rssfeed/0,,12,00.xml"}
	feed_urls = []

# checkForm  Parse out variables passed from form.
def checkForm(form):
	feed = form['feed']							# Set feed var to object containing all feeds selected
	if type(feed) is type([]):						# Feed var is list. Multiple RSS feeds selected.		
		for item in feed: 				
			Global.feeds.append(item.value)	
	else:									# Feed var is string.  Single RSS feed selected.						
		Global.feeds.append(feed.value)

# printForm  Print selector form
def printForm():
	template_file = open('../includes/select_form.html', 'r')
	print "Content-Type: text/html\n"
	print template_file.read()

# nameToUrl  Take feed name, return feed url
def nameToUrl():
	for name in Global.feeds:
		Global.feed_urls.append(Global.url_dict[name])

# getAnchors  Get list of names for named anchors for page navigation
def getAnchors():
	anchor_list = "| "
	for feed in Global.feed_list:
		anchor_list = anchor_list + """<a href="#%s">%s</a> | """ % (feed[0], feed[0])
	return anchor_list
	

# main parser logic
def parser():
	for url in Global.feed_urls:
		try:			
			content = urlopen(url).read()
			rss_xml = minidom.parseString(content)
			rss_xml.normalize()
			getFeedTitle(rss_xml)
			item_list = rss_xml.getElementsByTagName('item')
			feed_items = getChildNodes(item_list)		
		except IOError:
			print " No valid feed at ", url
			pass	
	top = open('../includes/display_feeds_top.html', 'r')			# Stupid workaround for template
	bottom = open('../includes/display_feeds_bottom.html', 'r')		# Stupid workaround for template
	anchor_list = getAnchors()				
	i = 0
	print "Content-Type: text/html\n"
	print top.read()
	print """<p align="center">%s</p>""" % (anchor_list)
	print """<br /><br />"""
	for feed in Global.feed_list:
		print """<br /><h1 align="center"><a name="%s"><a href="%s">%s</a></a></h1>""" % (feed[0], feed[1], feed[0])  #(title, link, title)
		for story in Global.super_item_object_list[i]:
			try:							# name, url, name
				print """<a href="%s">%s</a><br />%s<br /><br >""" % (story[1], story[0], story[2])  
	        	except:
				pass
		i += 1	
		print "<hr />"
	print bottom.read()

# getFeedTitle  Aquire the title of each rss feed
def getFeedTitle(rss_xml):
	channel_element = rss_xml.getElementsByTagName('channel')
        feed_title = (channel_element[0].getElementsByTagName('title')[0]).childNodes[0].data.encode('iso-8859-1')
        feed_link = (channel_element[0].getElementsByTagName('link')[0]).childNodes[0].data.encode('iso-8859-1')
        feed_list_object = [feed_title, feed_link]
	Global.feed_list.append(feed_list_object)
		
# getChildNodes takes list of items and append child nodes of each item to list
def getChildNodes(item_list):
	item_object_list = []
        for item in item_list: 
        	try:
        		title = (item.getElementsByTagName('title')[0]).childNodes[0].data.encode('iso-8859-1')
        		link = (item.getElementsByTagName('link')[0]).childNodes[0].data.encode('iso-8859-1')
			description = (item.getElementsByTagName('description')[0]).childNodes[0].data.encode('iso-8859-1')
			item_object = [title, link, description]
			item_object_list.append(item_object)

		except:
			pass
	Global.super_item_object_list.append(item_object_list)

# main application logic
def main():							
	form = cgi.FieldStorage()
	if form.has_key('feed'):						# Selector has been called previously.  Show feeds.
		feeds = checkForm(form)
		nameToUrl()
		parser()
	else:									# Selector has not been called.  Print form.
		printForm()
	

### Call main function				
if (__name__ == "__main__"):
   main()


```

---

### Post by GazaM on 2006-01-08
Hey, that's some great work, allowing us to choose the feeds we'd like to display. By the way, if you'd like to be able to deal with all versions of RSS with your script, check out the link here [http://www.xml.com/pub/a/2002/12/18/dive-into-xml.html?page=2]("http://www.xml.com/pub/a/2002/12/18/dive-into-xml.html?page=2"), it actually writes it's rss parsing tutorial in Python using minidom! Great resource I've found.

> One question I have is, how can I pass parameters from the form with the post method to the script without passing directly to the script. What I mean is, I prefer to hide cgi scripts as server side includes in xhtml pages. I can't pass to an embedded cgi that way, though. I don't think so anyway. I admit I didn't try it. Just doesn't seem like it would work. Maybe I can pass as parameters in the url and have the cgi parse the url for parameters.


I'm trying to accimplish the EXACT same thing myself, in order to be able to display variable content within the same template, without having to include all of the html in the script. So, for example I'd like to link to 'http://my-homepage/blog.shtml?post 5', in that case sending me to the usual blog.shtml but sending the arguments post and 5 to the cgi script. Unfortunately this doesnt work as expected... I have only managed to get it working by putting the arguments in the url link to the cgi script embedded in the html file, which defeats the purpose of what I wanted. If you find anything I'd appreciate the info, and I'll be sure to let you know if I find anything too.

---

### Post by anthro398 on 2006-01-08
GazaM,

Would you mind posting a link to your site.  I saw the capture of your recent playlist and it looked very nice.  I'd like to see the rest.  Thanks for the link, perhaps I'll work on that.

---

### Post by Van_Gogh on 2006-01-08
Hi, I've read the script and I think it's great, though I don't understand everything(I'm pretty weak on web-stuff(CGI, HTML etc)), but I'd like to learn it :). Anyway, I got some comment om some stuff.

First Python and Unicode. If you're almost always are going to convert a string a a particular version of Unicode(e.g. latin-1), it's a bit of a hazzle having to do the "string.encode('iso-8859-1')" every single time. Instead you should declare the default unicode right after the "#!/usr/bin/env python" line. The first two line would then be:```

#!/usr/bin/env python
# -*- coding: iso-8859-1 -*-
```
See for example Dive into Python's [Unicode chapter]("http://diveintopython.org/xml_processing/unicode.html")(example 9.17).
This should mean that e.g in the getFeedTitle you could drop the "encode"-method, e.g.
```
#note that the ".encode('iso-8859-1')" is gone
title = (item.getElementsByTagName('title')[0]).childNodes[0].data
```
This I think is less error-prone and no stupid thing will happen if you forget to encode a particular string.


Secondly, I think your coding style makes it a bit hard to understand the code, because of the use of implicit variables as inputs and outputs. Stuff quickly gets spaghetti-like and makes the reader(and you(the author), see below) misunderstand the code. For example, in the main-function function you have a line that says:
```
feeds = checkForm(form)
```
This doesn't make any sense and misleads the reader as to what the code does, because the checkForm-function doesn't return any value, but only manipulates a output-variable implicitly(did I mention this is evil?). You could change the line to just "checkForm(form)", but I'd prefer to change the whole checkForm-function like this:

```
# checkForm  Parse out variables passed from form.
def  populateFeeds(form): #the name checkForm may indicate a boolean True/False return value
	feed = form['feed']							# Set feed var to object containing all feeds selected
	if type(feed) is type([]):			
		item_list = [item.value for item in feed]
	else:									# Feed var is string.  Single RSS feed selected.						
		item_list = [item.value]
	return item_list
```

and then in the main-function rewrite 
```
feeds = checkForm(form)
```
to
```
Globals.feeds += populateFeeds(form)
```
this way you can explicitly *SEE* what variable are manipulated by the checkForm-function, instead of having to remember it. 
As a sidenote, do you know the Zen of Python? if not try "import this" in the interpreter. Well, one of poem's lines says "Explicit is better than implicit" and the above is exactly what he's talking about. Personally I would even change it to "Explicit is *much, much* better than implicit" :)

So, do yourself a favour and be explicit about function inputs and outputs. You will be grateful when you re-read your code later on.

---

### Post by anthro398 on 2006-01-09
Van_Gogh,

I plead guilty as charged.  It's a mess and I apologize.  I'm now officially ashamed of doing such ugly work.  I really just wanted to get it up before I had to go yesterday.  I'll try to clean up the logic.  By the way, that function originally returned a boolean value, but that got nixed somewhere along the way.  Your advice is greatly appreciated and obviously needed.  

Thanks very much.

GazaM or Van_Gogh, is one of you from the Faroes?  If so, or whoever here is, I'd love to talk to you about them.  PM me if you care to.

---

### Post by anthro398 on 2006-01-11
I've made the changes suggested and it is easier to read.  Thanks very much.

I've been toying with templates.  You can see in the earlier iterations of this script I've been reading in the top and bottom half of my template html page and printing the top, then my rss content, then the bottom.  There's been too much html hard-coded into the cgi, though, and it's inelegant, at best.

I was playing with Template ( from string import Template), which allows you to place variables in the html template file to be substituted at runtime with values.  Unfortunately, my host is running Python 2.2.2 and string.Template isn't available.   However, I thought others might find it useful if they don't already know about it.  

The cgi below demonstrates how this works.  After the selector form is read, the values parsed out, the feeds gathered and parsed, the code below would read in a template designed to mimic the look or your site with variables in it to hold the place of the values (rss feeds) that get passed in from the selector form.  The variables start with dollar signs as in perl.  Eg., $story or $title.  Very nifty module, template is.  Of course, were this to work, you wouldn't hard-code a string into title_string or story_string, but would write the collected and parsed titles and stories to those variables as long strings.

```

#!/usr/bin/env python 

import cgi, cgitb; cgitb.enable()
#from urllib import urlopen
#from xml.dom import minidom
from string import Template  		# Prairienet is running Python 2.2.2 & doesn't include this module

# set form_template to the location of the template users will select feeds from.  eg, "../select.html"
select_template = "select.html"
# set display_template to the location of the template you in which the stories will be displayed . eg, "../display.html"
display_template = "index.html"	
title_string = "This just in"
story_string = "I heard it through the grapevine."

template_file = open(display_template, 'r')
template = template_file.read()
template_object = Template(template)
output_string = template_object.safe_substitute(title = title_string, story = story_string)

print output_string

```

---

### Post by GazaM on 2006-01-11
Anthro, thanks for letting me know about the Template module, this will come in REALLY handy for my site! On that note, I'm glad you thought that my site looked good from seeing just that small screenshot... although it has been completely (and i mean completely!) changed. I don't really want to post a link here on the forums just yet, as it's going through some heavy development and it's being hosted on another's web space, so I wouldn't like to take up any of their bandwidth. I'll be getting my own hosting and domain name soon, but if you must see the site, just PM me or IM me using one of the accounts listed or PM me for my other IM account details. (msn and yahoo are my least used, so I dont really care who I give them out to)

PS. Maybe it's just me, but shouldn't you close the file once you've put the read() string into another value and have no more need for the file to be open?

---

### Post by anthro398 on 2006-01-12
I'll probably get contradicted here, but I thought that as part of Python's memory management process it would close the file at the end of the script.  Since it's such a short script I didn't really worry about it, but I'm sure you're right in that it's a good idea.  

Well, let us know when your public roll-out takes place so we can have a look at your site.

---

### Post by GazaM on 2006-01-13
Sorry anthro, you are right... if the file is done with at the start of a script then it is a good idea to close it, but since yours is at the end, it is fine to leave Python to close it itself... the site is coming along nicely, and I've even made a flickr script for it now too, which uses the easy flickr api to grab images and anything I want... currently I have it setup to display the three last images marked as 'interesting' and link to the photos page on flickr, but once I get my own photos online it will display my most recent uploaded pics... the source is coming up once It's finished or nearly there.

As for the Template module, my current host only has Python 2.3, so I have the same problems using it as you... although I have the exact same functionality by just having the file, and using .replace('$whatever', whatever).replace etc... a little less readable but works just fine nonetheless.

I'll be back soon with some updates, but I've had school and been working every day this week, so I haven't had time to make as much progress as I'd like.

---

### Post by Van_Gogh on 2006-01-13
Hi again,
Edit: Never mind the the first part, I messed up

GazaM pointed out that my encoding advice doesn't do what I thought it does. So, ```
# -*- coding: iso-8859-1 -*-
``` only sets the *default* unicode in the script, but if the unicode it set somehwere else, e.g. in the XML document :eek: , the default unicode is overridden, which is fair enough I guess.

Regards.

---

### Post by anthro398 on 2006-01-14
Ok, I've made the suggested changes.  The results look the same, I think, at [http://braggtown.com/scgi-bin/rss.cgi]("http://braggtown.com/scgi-bin/rss.cgi") It isn't any shorter, but I think it's easier to read and using Python's string.replace() is a much better way to format html ouput.  I'd rather use HTML Template, but I don't have that option.  So, I think it's easier to include the RSS feeds in a web page.  You only have to put a variable, $FEEDS, in the page and the cgi replaces it with the RSS feeds.

I'd be grateful for any advice on improvements or suggestions for features I could add to make it more useful.  Thanks GazaM and Van_Gogh for your help so far.  This has been fun.

I am disappointed tjat there are some feeds I can't parse.  For instance, Google News always crashes the script.  There are also some sites that include the whole story in the the description element, which makes the description too long for practical display.  I was thinking of cutting off the description after x characters, but there is so much HTML and garbage in some descriptions that I wouldn't know where to begin.  The problem with Google News RSS may be that each description is formatted with tables, though I don't know why that should force an exception.

Anyway, thanks.

```

#!/usr/bin/env python
# -*- coding: iso-8859-1 -*-

# rss_parser.cgi  www.prairienet.org/~jtuttle/  1/2006
# XML/RSS parser to grab and display feeds on web page
# To add or remove feeds add a unique name and the rss url to the url_dict in the global class. 
# Don't forget to also add an option with that same feed name to your selector form.
# The feed display works be using Python's string.replace().  The cgi replaces a variable, $FEEDS, with the gathered feed information.
# Make sure that you place $FEEDS in your web page at the location you'd like the rss feeds displayed.

# Thanks to GazaM and Van_Gogh from ubuntuforums.org for their contributions.


### Import Python modules
import cgi, cgitb; cgitb.enable()
from urllib import urlopen
from xml.dom import minidom


# Global.  Class to hold global variables.  Alleviates having to pass references between functions.  
class Global:
	feeds = []
	super_item_object_list = []
	feed_list = []
	feed_urls = []	
	url_dict = {"slashdot": "http://rss.slashdot.org/Slashdot/slashdot", "osnews": "http://osnews.com/files/recent.rdf", \
		   "distorwatch": "http://distrowatch.com/news/dw.xml", "zdnet": "http://news.zdnet.com/2509-1_22-0-20.xml", \
		   "bbc": "http://fxfeeds.mozilla.org/rss20.xml", "thinkprogress": "http://thinkprogress.org/feed/", \
		   "asiatimes": "http://www.atimes.com/atimes/atol.xml", "ucimc": "http://indymedia.us/main-features-content.rss", \
		   "crooks": "http://www.crooksandliars.com/rss.xml", "guardian": "http://www.guardian.co.uk/rssfeed/0,,12,00.xml", \
		   "npr": "http://www.npr.org/rss/rss.php?id=1012", "bbctech": "http://newsrss.bbc.co.uk/rss/newsonline_world_edition/technology/rss.xml#", \
		   "google": "http://news.google.com/?output=rss", "freepress": "http://www.freepress.net/news/rss/news_all.rss"}


# populateFeeds.  Parse out variables passed from form
def populateFeeds(form):
	feed = form['feed']							# Set feed var to object containing all feeds selected
	if type(feed) is type([]):						# Feed var is list. Multiple RSS feeds selected		
		for item in feed: 				
			Global.feeds.append(item.value)	
	else:									# Feed var is string.  Single RSS feed 						
		Global.feeds.append(feed.value)

# printForm.  Print selector form
def printForm(form_template):
	form_template = open(form_template, 'r')
	print "Content-Type: text/html\n"
	print form_template.read()
	form_template.close()

# nameToUrl.  Take feed name, return feed url
def nameToUrl():
	for name in Global.feeds:
		Global.feed_urls.append(Global.url_dict[name])

# getAnchors.  Get list of names for named anchors for page navigation
def getAnchors():
	anchor_str = "| "
	for feed in Global.feed_list:
		anchor_str += """  <a href="#%s">%s</a> | """ % (feed[0], feed[0])	#(name, name)
	return anchor_str
	
# getFeeds. parser logic
def getFeeds(rss_icon, display_template):
	for url in Global.feed_urls:
		try:			
			content = urlopen(url).read()
			rss_xml = minidom.parseString(content)
			rss_xml.normalize()
			getFeedTitle(rss_xml)
			item_list = rss_xml.getElementsByTagName('item')
			getChildNodes(item_list)		
		except IOError:
			print " No valid feed at ", url
			pass	
	display_template = open(display_template, 'r')
	display_template_str = display_template.read()
	display_template.close()	
	anchor_str = getAnchors()				
	i = 0
	feed_output = """ <a name="top"> <p align="center">%s</p>""" % (anchor_str) + """<br /><br />"""
	for feed in Global.feed_list:										#(title, link, title)
		feed_output += """<br /><h1 align="center"><a name="%s"><a href="%s">%s</a></a></h1>""" % (feed[0], feed[1], feed[0])  
		for story in Global.super_item_object_list[i]:
			try:								
				if rss_icon:
					feed_output += """<img src="%s" border="0" />&nbsp; """ % (rss_icon)# name, url, name
				feed_output += """<a href="%s">%s</a><br />%s<br /> <br />""" % (story[1], story[0], story[2])  
	        	except:
				pass
		i += 1
		feed_output += """<p align="center">""" + """<a href="#top">Back to top</a>""" + "</p>" + "<hr />"
	print "Content-Type: text/html\n"
	print display_template_str.replace('$FEEDS', feed_output)

# getFeedTitle  Aquire the title of each rss feed
def getFeedTitle(rss_xml):
	channel_element = rss_xml.getElementsByTagName('channel')
        feed_title = (channel_element[0].getElementsByTagName('title')[0]).childNodes[0].data.encode('iso-8859-1')
        feed_link = (channel_element[0].getElementsByTagName('link')[0]).childNodes[0].data.encode('iso-8859-1')
        feed_list_object = [feed_title, feed_link]
	Global.feed_list.append(feed_list_object)
		
# getChildNodes takes list of items and append child nodes of each item to list
def getChildNodes(item_list):
	item_object_list = []
        for item in item_list: 
        	try:
        		title = (item.getElementsByTagName('title')[0]).childNodes[0].data.encode('iso-8859-1')
        		link = (item.getElementsByTagName('link')[0]).childNodes[0].data.encode('iso-8859-1')
			description = (item.getElementsByTagName('description')[0]).childNodes[0].data.encode('iso-8859-1')
			item_object = [title, link, description]
			item_object_list.append(item_object)
		except:
			pass
	Global.super_item_object_list.append(item_object_list)

# main application logic
def main():	
	### Set the following variables
	form_template =	"../includes/select_form.html"		# Set to location of your selection form
	rss_icon = "../images/rss.png"	# Set to location of icon displayed next to titles. Change to False (no quotes) if no icon desired.	
	display_template = "../includes/display_feeds.html"	# Set to location of page feeds displayed in
	###		
	form = cgi.FieldStorage()
	if form.has_key('feed'):				# Selector has been called previously.  Show feeds.
		populateFeeds(form)#ok
		nameToUrl()#ok
		getFeeds(rss_icon, display_template)
	else:							# Selector has not been called.  Print form.
		printForm(form_template)
	
### Call main function				
if (__name__ == "__main__"):
   main()

```

As always, the most recent version can be downloaded at [http://braggtown.com/projects.html]("http://braggtown.com/projects.html")

---

### Post by Van_Gogh on 2006-01-17
I got a question about the script that I'm curious to have answered. In your main-function you have
```

    form = cgi.FieldStorage()
    if form.has_key('feed'):
        #something

```
Now, when I run this in iPython, variable called *form* never has a key called 'feed', because it just got created! What's going on here? Does the cgi.FieldStorage take parameters from standard input or what? Sorry, I've never worked with cgi-scripts before and would like to understand this...

---

### Post by anthro398 on 2006-01-18
The first thing the cgi does is check for data in the cgi.FieldStorage() container.  If there is no data in it or the container is not present that means either the script is being called for the first time or the user did not select any feeds to display.  In either case the cgi displays the selection form to the user.  However, if the container is present and contains values in the feed field that means that the user has already seen the selection form and has chosed some feeds to display.

The reason for the specific field name "feed" is that I chose that field name to describe it's contents.  See the snippet of html from the selection form below.
```
     
 <li><input type="checkbox" name="feed" value="slashdot" /> Slashdot</li>

```
See that I named the input field "feed".  I could have named it something else and that's why it isn't present in your cgi.  You'll choose your own input field names and access the values in those fields with the name you chose.  If I'm not mistaken the cgi.FieldStorage() container is similar to a dictionary and you access with keys.  So, every "feed" selected with my selection form gets packed into a Python data dictionary-like object with the key "feed" and I access those values by looking up the key "feed" in that dictionary-like object.

---

### Post by Van_Gogh on 2006-01-19
Ok, thanks for the answer. I'm still not sure I get it, though. I probably should read up on it to understand, but the thing I don't understand is where does the script fetch the form data from? When you call the script, do you call it with some command line arguments that contain the form data or is there some other way the form gets into the script?

Sorry for asking stupid questions...

---

### Post by GazaM on 2006-01-19
When you go to his RSS script, you're presented with various choices as to which feeds you'd like to view. This is a 'form'... the form has a 'function' associated with it, basically meaning he has just pointed the 'submit' button to his cgi script. When you press the submit button on the form (or whatever he has labelled it), it sends the form data you've entered using the HTTP 'POST' method to the cgi script and runs the script. This is how the script get's the form data.

It's up to whoever's writing the script to figure out what to do with the form data though, but that is the basics of how data is sent from a form to a script.

---

### Post by anthro398 on 2006-01-19
I couldn't have said it better myself.  If the cgi doesn't get any data via the POST method, it can assume that it's being called the first time and execute the conditional logic statement to show the selection form.  I could have put in a hidden field to have a 3 option conditional logic statement for situations in which people hit submit but didn't check select any options.  

Is anyone using this thing?  I was thinking of breaking down and implementing Mark Pilgrim's [excellent feed parser]("http://diveintomark.org/projects/feed_parser") and writing a wrapper around that.  It's internals are pretty complicated, but I read that it works quite well.

---

### Post by Van_Gogh on 2006-01-19
Ok, I understand now. The form's action atribute is "rss.cgi" which is called both before and after the user submits his/hers choices. Thanks for explaining it, guys.

---

### Post by Van_Gogh on 2006-01-19
Ok, I understand now. The form's action attribute is "rss.cgi" which is both the original page and the the page returned when the user submits his/hers choices. 

Thanks for explaining it, guys.

---

### Post by anthro398 on 2006-07-31
GazaM and Van_Gogh,

I know this thread has been inactive for quite some time, but I thought you'd be pleased to know that it's still useful.  I rewrote the weather parsing cgi to take advantage of the NOAA National Weather Service data available in XML now and recycled some of your work to use a local cache at the request of someone at NWS.  I'll post it below and it's also available at [http://braggtown.com/projects.html]("http://braggtown.com/projects.html").  You can see it in action at [http://www.braggtown.com/webcam.html]("http://www.braggtown.com/webcam.html").  Thanks for the help.

Improvements include more accurate parsing (XML instead of HTML), keeping a local cache of the XML and icons, checking the cached XML age and retrieving a fresh version only when the cached version is greater than 30 minutes old.  That makes it much faster, I think, especially when the NWS server is responding slowly. 

```
#!/usr/bin/env python

# xmlweather.cgi is a python cgi script that parses National Weather Service XML weather data and displays it in a web page.
# Set the url variable with the weather station of your choice.  I include this in webpages using server-side includes with the
# following statement: <!--#include FILE="cgi-bin/xmlweather.cgi"--> 
# Enjoy.  http://www.prairienet.org/~jtuttle

## Import Python modules
import cgi, cgitb; cgitb.enable()
from urllib import urlopen, urlretrieve
from xml.dom import minidom
from sys import exit
import os
from os.path import exists, join, split
from time import time

## Set url variable.  Get url from http://www.nws.noaa.gov/data/current_obs/
url = "http://www.nws.noaa.gov/data/current_obs/KRDU.xml"
## Set cache variable to True to use local cache, False to always retrieve newest file
useCache = True
## Set variable to location of locally cached xml file
cache = "/home/jtuttle/public_html/weather_cache.xml"
## Set image directory.  This reduces network latency by utilizing local image directory.  Set to False if no local images.
imgDir = "/home/jtuttle/public_html/images/weather_icons"
imgDirUrl = "http://www.prairienet.org/~jtuttle/images"

# Acquire, parse, and normalize xml from NWS.  Return xml tree object
def getWebXML(url):
	try:			
		content = urlopen(url).read()
		xml = minidom.parseString(content)
		xml.normalize()	
		return 	xml
	except IOError:
		print "Content-Type: text/html\n"
		print " No valid data at ", url
		exit()

# Aquire, parse, and normalize xml from local cached file.  Return xml tree object
def getCacheXML(cache):
	xml = minidom.parse(cache)
	xml.normalize()
	return xml

# Parse out selected elements and populate variables.  Return variable dictionary
def getElements(xml):
	root = xml.getElementsByTagName('current_observation')
	imgroot = xml.getElementsByTagName('image')
	location = (root[0].getElementsByTagName('location')[0]).childNodes[0].data.encode('iso-8859-1')
	weather = (root[0].getElementsByTagName('weather')[0]).childNodes[0].data.encode('iso-8859-1')
	temperature_string = (root[0].getElementsByTagName('temperature_string')[0]).childNodes[0].data.encode('iso-8859-1')
	relative_humidity = (root[0].getElementsByTagName('relative_humidity')[0]).childNodes[0].data.encode('iso-8859-1')
	wind_string = (root[0].getElementsByTagName('wind_string')[0]).childNodes[0].data.encode('iso-8859-1')
	heat_index_string = (root[0].getElementsByTagName('heat_index_string')[0]).childNodes[0].data.encode('iso-8859-1')
	observation_time = (root[0].getElementsByTagName('observation_time')[0]).childNodes[0].data.encode('iso-8859-1')
	credit = (root[0].getElementsByTagName('credit')[0]).childNodes[0].data.encode('iso-8859-1')
	credit_URL = (root[0].getElementsByTagName('credit_URL')[0]).childNodes[0].data.encode('iso-8859-1')
	img_url = (imgroot[0].getElementsByTagName('url')[0]).childNodes[0].data.encode('iso-8859-1')
	if (imgDir) and exists(imgDir):
		img_url = cacheIcons(imgDir, img_url, imgDirUrl)	
	img_title = (imgroot[0].getElementsByTagName('title')[0]).childNodes[0].data.encode('iso-8859-1')
	img_link = (imgroot[0].getElementsByTagName('link')[0]).childNodes[0].data.encode('iso-8859-1')
	icon_url_base = (root[0].getElementsByTagName('icon_url_base')[0]).childNodes[0].data.encode('iso-8859-1') 
	icon_url_name = (root[0].getElementsByTagName('icon_url_name')[0]).childNodes[0].data.encode('iso-8859-1')
	icon_url = join(icon_url_base, icon_url_name)
	if (imgDir) and exists(imgDir):
		icon_url = cacheIcons(imgDir, icon_url, imgDirUrl)	

	elDict = {'location': location, 'weather': weather, 'temperature_string': temperature_string, 'relative_humidity': relative_humidity,\
	'wind_string': wind_string, 'heat_index_string': heat_index_string, 'observation_time': observation_time, 'credit': credit, \
	'credit_URL': credit_URL, 'img_url': img_url, 'img_title': img_title, 'img_link': img_link, 'icon_url': icon_url} 

	return elDict

# Determine if local cache of icon exists.  If not, copy to image cache directory
def cacheIcons(imgDir, url, imgDirUrl):
	path, icon = split(url)
	if not exists(join(imgDir,icon)):
		urlretrieve(url, join(imgDir, icon))
	return join(imgDirUrl, icon)	

# Format results and xhtml in verbose fashion
def formatDataVerbose(elDict):
	print "Content-Type: text/html\n"
	print """<img src="%s" border="0" alt="weather icon" align="left" width="32" height="32" /><br />\n""" \
	% (elDict["icon_url"])
	print "<h2>Local conditions at %s : %s </h2><br />\n" % (elDict["location"], elDict["observation_time"])
	print "The weather is %s and the temperature is %s." % (elDict["weather"].lower(), elDict["temperature_string"])
	print "The heat index is %s, the relative humidity is %s, and the wind is %s.<br />\n" % (elDict["heat_index_string"].lower(), \
	elDict["relative_humidity"].lower(), elDict["wind_string"].lower())
	print """<br /><a href="%s" title="%s"><img src="%s" alt="%s" border="0" /></a>""" % (elDict["img_link"], elDict["img_title"], \
	elDict["img_url"], elDict["img_title"])

# Format results and xhtml in succint fashion
def formatDataSuccinct(elDict):
	print "Content-Type: text/html\n"
	print """<img src="%s" border="0" alt="weather icon" width="32" height="32" /><br /><br />""" \
	% (elDict["icon_url"])
	print "<strong>Local conditions at %s : %s </strong><br />\n" % (elDict["location"], elDict["observation_time"])
	print "Current conditions: ", elDict["weather"], "<br />"
	print "Temperature: ", elDict["temperature_string"], "<br />"
	print "Relative Humidity: ", elDict["relative_humidity"], "%<br />"
	print "Heat Index: ", elDict["heat_index_string"], "<br />"
	print "Wind: ", elDict["wind_string"], "<br />\n"
	print """<br /><a href="%s" title="%s"><img src="%s" alt="%s" border="0" /></a><br />""" % (elDict["img_link"], elDict["img_title"], \
	elDict["img_url"], elDict["img_title"])

# Determine age of cached file. If older than 1 hour, retrieve new data
def checkCacheAge(url, cache):
	cache_age = os.path.getmtime(cache)
	if ((time() - cache_age)/60 > 30):
   		content = urlopen(url)
   		f = open(cache, 'w')
   		f.write(content.read())
  		content.close()
   		f.close()


## main logic
if (useCache) and (exists(cache)):
	checkCacheAge(url, cache)
	xml = getCacheXML(cache)

else:	
	xml = getWebXML(url)

elDict = getElements(xml)
#formatDataVerbose(elDict)
formatDataSuccinct(elDict)

```

Note:  As I make changes, I won't update this page.  However, the latest version should always be available on my website.  Let me know if you use this or if you find it useful.

---

