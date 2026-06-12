---
title: "Parsing Website in Python"
date: 2008-03-05
forum: Programming Talk
---

### Post by Nevon on 2008-03-05
I have this idea of getting the TV-guide in my conky, and I think I've figured out a way to do it. Sadly I don't know Python, and I only have a simple general understanding of programming. 
My idea is that I single out the elements I want from a certain website, and display them on my conky. I found a script called Beautiful Soup, which might be of use.
> Beautiful Soup is an HTML/XML parser for Python that can turn even invalid markup into a parse tree. It provides simple, idiomatic ways of navigating, searching, and modifying the parse tree.
There are examples of the website: [http://www.crummy.com/software/BeautifulSoup/](http://www.crummy.com/software/BeautifulSoup/) of how it can single out certain elements from a website, and display them as strings. 
I've installed Beautiful Soup at home and it seems to be working, but I need some help with writing a script. 
This site would be the source: [http://www.tv.nu/](http://www.tv.nu/) and I would only need it to display the current program on a few of the channels, and the one after that, and at what times they start.

Any thoughts on this? Is it even possible?

---

### Post by nhandler on 2008-03-05
I don't know about python, but I know you could easily do this task with perl. Perl has a module called LWP::Simple (or LWP::UserAgent) which can be used to retrieve the page. You can then use a regex (or two, or three, or a LOT) to parse the data.

---

### Post by Nevon on 2008-03-05
That sounds good. The problem would be writing regular expressions that would give me what I want. And then how do I print that in Conky?

---

### Post by lnostdal on 2008-03-05
yes, this is possible and it should be easy once you know python and the tool(s) you mention .. or, you can also use regular expressions to do this .. you might find that this might be a quick (but possibly dirty; not that this always matters) shortcut to your goal

oh, and btw. Cheater: you know perfectly well that almost any language has support for these things and that both python and perl are equally suitable for this task .. (disclaimer: i don't use python, or perl) .....

---

### Post by pmasiar on 2008-03-05
It is exactly as easy to do it in Python as is in Perl, or even easier.

parsing HTML by regex is a sucker's game. This is exactly why BeatifulSouplibrary was created. Regex is another language, and a friendly one.

Python has exactly the powers of Perl, but code is more user friendly and readable. See sticky FAQ about perl and Python, so we don't have to re-figth that flamewars here again.

Python has urllib to fetch the page.

---

### Post by slavik on 2008-03-05
HTML/XML is a speacial case of text. If you want to process text, use the tool designed for it (Perl).

and \\\\ to match a backslash is not friendly regex (this is what you have to do in Python).

---

### Post by skeeterbug on 2008-03-05
Whichever language you use, don't use regex to parse it.

Perl:
[http://search.cpan.org/~gaas/HTML-Parser-3.35/Parser.pm](http://search.cpan.org/~gaas/HTML-Parser-3.35/Parser.pm)

Python:
[http://docs.python.org/lib/module-htmllib.html](http://docs.python.org/lib/module-htmllib.html)

---

### Post by mssever on 2008-03-05
> **slavik said:**
> HTML/XML is a speacial case of text. If you want to process text, use the tool designed for it (Perl).

and \\\\ to match a backslash is not friendly regex (this is what you have to do in Python).

Parsing HTML/SGML/XML like you might parse a generic Linux config file would be a mistake. The easiest way to manipulate HTML data is through the DOM. I've tried to use regexps before on HTML, and they quickly become unreadable and buggy.

The right tool for the job applies here, and the right tool is some sort of DOM library.

(I'm saying this as someone who uses regexps extensively in nearly every program. In fact, one of the reasons I prefer Ruby over Python is because Python imposes awkward syntax on regexps.)

---

### Post by Nevon on 2008-03-05
Here's some example code from BeautifulSoup's documentation.
```
import urllib2
from BeautifulSoup import BeautifulSoup

page = urllib2.urlopen("http://www.icc-ccs.org/prc/piracyreport.php")
soup = BeautifulSoup(page)
for incident in soup('td', width="90%"):
    where, linebreak, what = incident.contents[:3]
    print where.strip()
    print what.strip()
    print

```
Wouldn't this be fairly easy to modify to get the elements that I want? Now, as I said, I'm not programmer, but there seems to be some pretty neat search functions in the library, for example "find" and "findall". Now, what I would need is to be able to find a li tag with a certain CSS class. "po" is the name of the class for the current show. So to search for this would be something like:
```
soup.find("li", { "class" : "po" })
```
Still, my source is not optimal for this, as you can see by the source code from [www.tv.nu](www.tv.nu). The entry for the current show looks like this:
> <li class="po" id="Stargate SG 1">18:00 <a href="#" onclick="j('12047364003735', this); return false">Stargate SG 1</a></li>
Nothing that can really help me single out the time and the name of the show, or even what channel it's on.

EDIT: This is what the complete listing for a single channel looks like:
[HTML]<div class="listing" style="clear:both">
<div class="tabla_container"> 
  <div class="tabla_topic">
  <img src="/_graphics/logos/TV6.gif" class="tabla_kanal" alt="TV6" />
  <p>TV6</p>
  </div> 
  <div class="tabla_content"> 
    <ul class="prog_tabla"> 
      <li class="pg" id="Star Trek">08:30 <a href="#" onclick="j('12047022003721', this); return false">Star Trek: The 	next gene...</a></li>
      </-- more shows that have already been. Identical to the one above, except of course for the javascript, time and name -->      
      <li class="po" id="Stargate SG 1">18:00 <a href="#" onclick="j('12047364003735', this); return false">Stargate SG 1</a></li> </-- The current show -->
      <li class="py" id="Cops">19:00 <a href="#" onclick="j('12047400003736', this); return false">Cops</a></li> </-- A show that has not yet started -->
      </-- More shows that have not yet started. Identical to the one above, except for the javascript, time and name. -->
    </ul>
  </div> 
</div>[/HTML]

---

### Post by pmasiar on 2008-03-05
> **slavik said:**
> HTML/XML is a speacial case of text. If you want to process text, use the tool designed for it (Perl).

Your logic does not make sense at all - you contradict yourself. OP has special case of text, specific enough that tool optimized for the job was created (BeautifulSoup), why you suggest generic text processing solution where all regex will need to be designed and debugged from the ground up?

Exactly as you said: "**use the tool designed for it**", which is BeautifulSoup. 

Seems like you promote Perl regardless if it does not make sense, even according your own advice. :-)

---

### Post by lnostdal on 2008-03-05
> **slavik said:**
> HTML/XML is a speacial case of text. If you want to process text, use the tool designed for it (Perl).


right .. this is the part where i leave this thread

Nevon: good luck .. and, well, try to ignore some of the kids here

---

### Post by nhandler on 2008-03-05
Well, I regret suggesting a language (I knew as I hit submit that it would start a perl/python debate). As most people here are probably aware, my prefered language would by perl. Even though it is similar to python, I never took the time to get familiar with it. Currently, I have some free time. If you (Nevon) could provide specific details about what sections of the tv guide you want, I would be willing to code something up. It would be in perl, but it would work. If you are interested, please send me an email (See my profile for my email address)/pm. That will insure I see it. I will be sure to post the final product in this thread for everyone to see.

As for your question about getting this stuff into conky, this is how I would do it. You would use a script to retrieve and parse the guide. The script will store the information that you want in a text file (formated the way you want). You would then configure conky to run the script (or you could use cron) and load the text file.

---

### Post by pmasiar on 2008-03-05
Cheater, you as Perl expert could learn Python in one afternoon. Just try it.

[Why Raymond switched from Perl to Python](http://www.linuxjournal.com/article/3882) in couple hours, cold turkey.

Tim Berners-Lee siad he likes Python because you can learn it in flight on one set of batteries :-)

---

### Post by slavik on 2008-03-05
> **pmasiar said:**
> Your logic does not make sense at all - you contradict yourself. OP has special case of text, specific enough that tool optimized for the job was created (BeautifulSoup), why you suggest generic text processing solution where all regex will need to be designed and debugged from the ground up?

Exactly as you said: "**use the tool designed for it**", which is BeautifulSoup. 

Seems like you promote Perl regardless if it does not make sense, even according your own advice. :-)
Don't take quotes out of context, please. :)

```

<html><body>
<div id="646">127.0.0.1</div>
<div id="646">FF:FF:FF:FF:FF:FF</div>
</body></html>
```

parse out the IP address from the above. :)

you either need to process XML or text, if you want to process XML, use a library, if you want to process text, use Perl. I also only suggest Perl when there is text processing involved.

here's another one, writing a customized crawler to do a dynamic to static backup and changing the pages that get stored (by actually editing them) ... would you still use a library for it? or a simple s/stuff//gis line?

yet, here is another example: you have a page and want to get rid of all the forms:
```
$page = LWP::Simple::get($url); $page =~ s|<form.*?</form>||gis;
```

---

### Post by nhandler on 2008-03-05
> **pmasiar said:**
> Cheater, you as Perl expert could learn Python in one afternoon. Just try it.

[Why Raymond switched from Perl to Python](http://www.linuxjournal.com/article/3882) in couple hours, cold turkey.

Tim Berners-Lee siad he likes Python because you can learn it in flight on one set of batteries :-)

I know python wouldn't be that difficult to learn. I've fooled around with it on several occasions. I just am not as familiar with it as I am with perl. Eventually, I'll probably switch to python, but for now, I'll stick with perl.

---

### Post by LaRoza on 2008-03-06
> **slavik said:**
> Don't take quotes out of context, please. :)

```

<html><body>
<div id="646">127.0.0.1</div>
<div id="646">FF:FF:FF:FF:FF:FF</div>
</body></html>
```

parse out the IP address from the above. :)

you either need to process XML or text, if you want to process XML, use a library, if you want to process text, use Perl. I also only suggest Perl when there is text processing involved.


It depends on the structure of the code.

The question refers to a "website", a "website" should be using markup to describe logic, and thus using tools to access the page in that manner would make sense.

If the markup is not logical, and is just a mix of characters, then regular expressions would be best (and the designer should have their keyboard taken away).

Python could be used to process text as well, there is no reason to learn another language for it.

---

### Post by pmasiar on 2008-03-06
> **slavik said:**
> Don't take quotes out of context, please. :)


I guess I'll follow lnostdal...

C U in some other thread :-)

---

### Post by Wybiral on 2008-03-06
I'm not entirely sure what you need, but it does sound like BeautifulSoup should be able to handle it. Here's an example of parsing each channel and finding the orange colored link (are those the ones playing? I'm not sure...)

It shouldn't be hard too play around with this until you get what you need out of it:

```
from urllib2 import urlopen
from BeautifulSoup import BeautifulSoup

url = "http://www.tv.nu/"

show_attrs = {"class": "po"}
topic_attrs = {"class": "tabla_topic"}
channel_classes = ["tabla_container", "tabla_container tcr"]

for channel in BeautifulSoup(urlopen(url)).findAll("div"):

    if channel.has_key("class") and channel["class"] in channel_classes:

        for topic in channel.findAll("div", topic_attrs):
            name = topic.p.string.strip()
            print "Channel: %s" % name

        for show in channel.findAll("li", show_attrs):
            time = show.contents[0].strip()
            name = show.a.string.strip()
            print "    Show (%s): %s" % (time, name)

```

---

### Post by Nevon on 2008-03-06
Hey Wybiral, cool! That's an excellent start. Is it possible to filter out all channels except 1, 2, 3, 4, 5, 6, and MTV?

---

### Post by Wybiral on 2008-03-06
> **Nevon said:**
> Hey Wybiral, cool! That's an excellent start. Is it possible to filter out all channels except 1, 2, 3, 4, 5, 6, and MTV?

Sure, you can just make a simple "whitelist" of the channels you want, something like this should do:

```
from urllib2 import urlopen
from BeautifulSoup import BeautifulSoup

url = "http://www.tv.nu/"

show_attrs = {"class": "po"}
topic_attrs = {"class": "tabla_topic"}
channel_classes = ["tabla_container", "tabla_container tcr"]

allowed_channels = ["SVT 1", "SVT 2", "TV3", "TV4", "TV5", "TV6", "MTV"]

for channel in BeautifulSoup(urlopen(url)).findAll("div"):

    if channel.has_key("class") and channel["class"] in channel_classes:

        topic = channel.find("div", topic_attrs)

        name = topic.p.string.strip()

        if name not in allowed_channels:
            continue

        print "Channel: %s" % name

        for show in channel.findAll("li", show_attrs):
            time = show.contents[0].strip()
            name = show.a.string.strip()
            print "    Show (%s): %s" % (time, name)

```

---

### Post by Nevon on 2008-03-06
Hey, cool, it actually works! :D I have a question though. In the last line of the script, it says ```
print "    Show (%s): %s" % (time, name)"
``` What's with %s twice? When it's printed I get the result "Show (11:00): Don't stop the music", so what does the second %s stand for? 
Also, is there any way to make it display the next show in the list? Meaning the one that will start after the current show?

---

### Post by Wybiral on 2008-03-06
> **Nevon said:**
> Hey, cool, it actually works! :D I have a question though. In the last line of the script, it says ```
print "    Show (%s): %s" % (time, name)"
``` What's with %s twice? When it's printed I get the result "Show (11:00): Don't stop the music", so what does the second %s stand for? 
Also, is there any way to make it display the next show in the list? Meaning the one that will start after the current show?

When you use a tuple on the right side of the modulus operator, such as "string % (a, b, c)" you have to tell it where to put the objects in the string (in this case using "%s" since the objects are strings). The order the objects appear in the tuple is the order they replace the "%s"s in the string.

It's pretty trivial to grab the next one using the "findNextSibling" method of "show" in the loop at the bottom. I've already implemented it myself, but in case you want to do it for a learning experience, I will leave that for you. If not, I would be happy to post it since it's already written, but you should give it a shot first :)

---

### Post by Nevon on 2008-03-06
Like I said, the closest thing to programming experience I've got is a little bit of PHP and even less Ruby, and I've managed to forget most of that. I don't have any experience with desktop programming. One day, when I've got enough time on my hands to really focus my attention on it, I'll learn. But for now I would appreciate it if you'd post your implementation of it. 
If nothing else, then at least I'll learn something from studying the code.

---

### Post by Wybiral on 2008-03-06
OK. I would probably do it something like this:

```

from urllib2 import urlopen
from BeautifulSoup import BeautifulSoup

url = "http://www.tv.nu/"

show_attrs = {"class": "po"}
topic_attrs = {"class": "tabla_topic"}
channel_classes = ["tabla_container", "tabla_container tcr"]

allowed_channels = ["SVT 1", "SVT 2", "TV3", "TV4", "TV5", "TV6", "MTV"]

for channel in BeautifulSoup(urlopen(url)).findAll("div"):

    if channel.has_key("class") and channel["class"] in channel_classes:

        topic = channel.find("div", topic_attrs)

        name = topic.p.string.strip()

        if name not in allowed_channels:
            continue

        print "Channel: %s" % name

        this_show = None
        for show in channel.findAll("li", show_attrs):
            this_show = show
            this_time = this_show.contents[0].strip()
            this_name = this_show.a.string.strip()
            print "    Show (%s): %s" % (this_time, this_name)

        if this_show:
            next_show = this_show.findNextSibling("li")
            if next_show:
                next_time = next_show.contents[0].strip()
                next_name = next_show.a.string.strip()
                print "    Next (%s): %s" % (next_time, next_name)

```

(well, I would probably wrap it in a class or something if I intended to reuse it, but for this simple application this will probably do)

---

### Post by Nevon on 2008-03-06
That's awesome. Now, how would I go about to implement this in my Conky, and have it refresh the data every minute or so?

EDIT: Also, it would be good if there was some way to divide the data into several elements (I'm really lacking the proper vocabulary for this), so that it will be easier to format once printed in Conky.

---

### Post by Wybiral on 2008-03-06
Someone else will have to help you there, I've never used conky before.

---

### Post by Nevon on 2008-03-06
Someone else mentioned saving it in a text file and having Conky get the information from there. I don't know if that would be the best way to do it, but it should work. How would I go about to save the info from this script into a text file in the same folder as the script? Also, it might be helpful to save each piece of information on a separate line, or with some kind of divider anyway, so that each part can be printed on its own (making it easier to format).

---

### Post by Wybiral on 2008-03-06
Writing it is easy:

```

import codecs
from urllib2 import urlopen
from BeautifulSoup import BeautifulSoup

url = "http://www.tv.nu/"
show_attrs = {"class": "po"}
topic_attrs = {"class": "tabla_topic"}
channel_classes = ["tabla_container", "tabla_container tcr"]
allowed_channels = ["SVT 1", "SVT 2", "TV3", "TV4", "TV5", "TV6", "MTV"]

outfile = codecs.open("schedule.txt", "w", "utf-8")

for channel in BeautifulSoup(urlopen(url)).findAll("div"):

    if channel.has_key("class") and channel["class"] in channel_classes:

        topic = channel.find("div", topic_attrs)

        name = topic.p.string.strip()

        if name not in allowed_channels:
            continue

        outfile.write("channel: %s\n" % name)

        this_show = None
        for show in channel.findAll("li", show_attrs):
            this_show = show
            this_time = this_show.contents[0].strip()
            this_name = this_show.a.string.strip()
            outfile.write("show (%s): %s\n" % (this_time, this_name))

        if this_show:
            next_show = this_show.findNextSibling("li")
            if next_show:
                next_time = next_show.contents[0].strip()
                next_name = next_show.a.string.strip()
                outfile.write("next (%s): %s\n" % (next_time, next_name))

outfile.close()

```

You can worry about the format whenever you figure out how you'll be loading it in Conky (as it is, you can just check what the line starts with and use that to parse the info).

---

### Post by Nevon on 2008-03-06
Sweet! So I should probably be able to run this every couple of minutes as a cronjob, and then just get the information from the text file. I don't know if it's a very efficient way of doing it, but it should work.
Now all that's left is figuring out how to get it into Conky.

EDIT: Although I suppose it would be possible to run the script directly in Conky using execi (excecutes a shell command and prints the output at a specific interval), even if I wouldn't be able to format it much.

---

### Post by Nevon on 2008-03-06
Sorry about double posting, but I tried using the script directly in Conky, and it works - almost.
One of the shows that are supposed to be printed contains a special character in its name. So I get this error message: 
> File "/home/nevon/.scripts/tv.py", line 30, in <module>
    print "    Show (%s): %s" % (this_time, this_name)
UnicodeEncodeError: 'ascii' codec can't encode character u'\xe4' in position 23: ordinal not in range(128)

I did a google search for it, and came up with a forum post that said that you had to encode it to UTF-8, which makes sense. The problem is that I have no idea how to do this :(
Anyone?

---

### Post by Can+~ on 2008-03-06
> **Nevon said:**
> Sorry about double posting, but I tried using the script directly in Conky, and it works - almost.
One of the shows that are supposed to be printed contains a special character in its name. So I get this error message: 


I did a google search for it, and came up with a forum post that said that you had to encode it to UTF-8, which makes sense. The problem is that I have no idea how to do this :(
Anyone?

[http://evanjones.ca/python-utf8.html](http://evanjones.ca/python-utf8.html)

---

### Post by Nevon on 2008-03-06
> **Can+~ said:**
> [http://evanjones.ca/python-utf8.html](http://evanjones.ca/python-utf8.html)

Yes, thank you. I've already read through that though, and from what I could tell, you're supposed to start your script with ```
# -*- coding: utf-8 -*-
``` and do .```
.encode(utf-8)
``` on all your strings. Sadly I don't know how to properly implement this in my current script.

Also, I translated part of the script into Swedish, but the word for "next" is "nästa" which uses a special character. How would I fix that?
The script i'm using is this one:
```
# -*- coding: utf-8 -*-
from urllib2 import urlopen
from BeautifulSoup import BeautifulSoup
url = "http://www.tv.nu/"

show_attrs = {"class": "po"}
topic_attrs = {"class": "tabla_topic"}
channel_classes = ["tabla_container", "tabla_container tcr"]

allowed_channels = ["SVT 1", "SVT 2", "TV3", "TV4", "TV5", "TV6", "MTV"]

for channel in BeautifulSoup(urlopen(url)).findAll("div"):

    if channel.has_key("class") and channel["class"] in channel_classes:

        topic = channel.find("div", topic_attrs)

        name = topic.p.string.strip()

        if name not in allowed_channels:
            continue

        print "Kanal: %s" % name

        this_show = None
        for show in channel.findAll("li", show_attrs):
            this_show = show
            this_time = this_show.contents[0].strip()
            this_name = this_show.a.string.strip()
            print "    Nu (%s): %s" % (this_time, this_name)

        if this_show:
            next_show = this_show.findNextSibling("li")
            if next_show:
                next_time = next_show.contents[0].strip()
                next_name = next_show.a.string.strip()
                print "    Nästa (%s): %s" % (next_time, next_name)
```

---

### Post by Nevon on 2008-03-07
Bump. 

Doesn't anyone know how to do this?

---

