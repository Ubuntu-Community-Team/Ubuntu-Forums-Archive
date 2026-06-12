---
title: "Python, Google Maps API - read, delete, write to file"
date: 2006-01-28
forum: Programming Talk
---

### Post by anthro398 on 2006-01-28
I remember bumping up against this when I first started learning Python, but have forgotten how I might have gotten around it.  I want to open an xml file and add an element to it.  Open it in append mode, you say?  No, won't work.  You see the xml file has a closing element.
```

<visitors>
        <visitor><point lng="-78.923271" lat="36.01212"/></visitor>
</visitors>

```
See, if I append another visitor element it will follow the visitors element and that won't work.  I have to insert the new element before the closing parent element.  I guess I could open the xml file, read it into memory, modify it in memory, write it out to a temporary file, close both files, and move the temporary file to the name of the original file.  How inelegant!  Besides, it's a cgi and I'd like to keep the reads and writes to a minimum for the sake of speed.  

This is to dynamically generate point for the Google Maps API to geolocate the ip addresses of visitors.  I've written the functions to capture the ip address, geolocate it for the latitude and longitude, and now I need to write the lat and long to the xml data file that Google Maps API uses to generate icons on the map overlay to represent visitors to my web site. 

Anyone else using Google Maps API to build custom applications?  Using Python to do it?

---

### Post by dabear on 2006-01-28
use the seek method of files.
```

>>> fi = open('visit.xml', 'rw+')
>>> fi.seek(-(len('</visitors>')+1 ),2 )
>>> fi.write('<-- more xml--></visitors>')
>>> fi.close()

```
or somethinf like that..

---

### Post by gord on 2006-01-28
you could also check out the xml parsing modules python has, allthough im not sure how good they are, i try to stay away from xml

---

### Post by anthro398 on 2006-01-28
Hey, the seek suggestion was great: thanks very much.  I'm having trouble getting the lines to insert correctly.  
```

#!/usr/bin/env python

import os, string

lng = "blue"
lat = "red"
new_point = '\n\t<visitor><point lng="%s" lat="%s"/></visitor>' % (lng, lat)
f = open('visitors.xml', 'rw+')


f.seek(-(len('</visitors>')+1 ),2 ) # seek from the end of the file, move forward 12 (</visitors> +1)

f.write(new_point)
f.write("\n</visitors>")
#f.write("</visitors>")
f.close()

```

So, this is just a little test script to focus on the problem area.  This works, but only after the first run.  The first run gives me a blank line.  
So, starting with this:
```

<visitors>
	<visitor><point lng="blue" lat="red"/></visitor>
</visitors>

```
And then I have this after the first run:
```

<visitors>
	<visitor><point lng="blue" lat="red"/></visitor>

	<visitor><point lng="blue" lat="red"/></visitor>
</visitors>

```
And this on the second run:
```

<visitors>
	<visitor><point lng="blue" lat="red"/></visitor>

	<visitor><point lng="blue" lat="red"/></visitor>
	<visitor><point lng="blue" lat="red"/></visitor>
</visitors>

```
I've played around with the new line characters and can't get it to work every time.  When I take the new lines out, the inserted line ends up on the same line as the previous entry.

Any suggestions?

---

### Post by Van_Gogh on 2006-01-29
I'd suggest using an XML module, either something in the standard library, or outside it. Amara is the best module(=easisest and most pythonic), but is not included in the standard library, so if that's an issue, I'd choose minidom(as I don't know SAX :KS ).

So, with minidom to append a node you could do:
```

from dom import minidom
from urllib import urlopen  #used to directy access a net resource

xml = minidom.parse("url_of_the_site")

#the name of the node to append
new_node = xml.createChild("new_node") 

#create and append the inner text of the new node
new_text = xml.createTextNode("new_text")   
new_node.appendChild(new_text)

#print "<new_node>new_text</new_node>"
print new_node.toxml()  

#append the new node at the end
root = xml.documentElement
root.appendChild(new_node)

#show xml-file *with* appended node
print xml.toxml()  

```

As you can see, dom is not exactly elegant, but it'll get the job done and as a bonus, if you know how to use dom in Python, you'll know how to use it in Java(Script) too! It's almost exactly the same.

Hope that helps.

As a sidenote, I hope they make XML easier to work with in Python 2.5. As it is now, you really have to experiment, work and google for solutions until you 'get' mindom. For example, try to delete a node. My bet is you won't figure it out without consulting newsgroups or googling for the answer.

---

### Post by anthro398 on 2006-01-30
Hey Van_Gogh,

Yeah, I was hoping to avoid minidom for the sake of simplicity, but that might not be possible.  I'm working on a server that's running 2.2 and on which I can't install modules, but thanks for that tip.  

You know what I hate?  I hate when you have a neat idea to build something and you find out that it's been done.  I was going to build a place that my friends from school could register with, could display personal information, and that would be displayed on a Google Map.  Then my wife showed me [frappr]("http://www.frappr.com/"), which is exactly what I had envisioned.  Dang!  That's life, huh?

Thanks again for the tip.  I'll give it a shot.

---

### Post by anthro398 on 2006-01-30
Van_Gogh,

Upon looking at your code again, I realized that, while using minidom does get around writing new lines in the wrong place, it doesn't get around the need to write the new file to a temporary location and then replace the original xml file with it.  It would be really nice to be able to open a file, read it, modify it, and save it.  I must be missing something here.

---

### Post by Van_Gogh on 2006-01-30
I'm not really sure if I understand, but I thought you wanted to manipulate an xml-file downloaded from Google? Anyway, if you use a local file I don't think you have to use temporary files. Something like
```

from xml.dom import minidom

f = open(some_file, 'r+') #note the '+' sign
xml = minidom.parse(f)
do something with the xml-file
f.write(xml.toxml())
f.close()

```
should work. Does it(I haven't tried it)? Maybe you'll have to use f.seek(0) or something. Else you could more tediously do

```

f = open(some_file, 'r') #only read permisson
xml = minidom.parse(f)
f.close()
do something with the xml-file
f = open(some_file, 'w') #writing this time
f.write(xml.toxml())
f.close()

```
The above should definately work. And no, I still don't claim it's pretty :p

---

### Post by anthro398 on 2006-02-15
I rewrote this in PHP and MySQL.  It's now located a snip!  No longer up.  Can probably still see code at [http://braggtown.com/projects.html]("http://braggtown.com/projects.html")

---

### Post by anthro398 on 2006-11-10
The code for this project is available at  [http://braggtown.com/projects.html]("http://braggtown.com/projects.html")  Please let me know if you find it useful.

**Update:** I've been getting some traffic looking for the Python Google Maps CGI I wrote so I've also made that code available on my projects page.

---

