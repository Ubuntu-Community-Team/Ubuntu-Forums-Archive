---
title: "using phyton to process sound from microphone to mysql databases"
date: 2007-02-18
forum: Programming Talk
---

### Post by kthakore on 2007-02-18
basically I wanted to make a python project, where it will process sounds from the microphone into a serialized form so it can be add to a mysql databases, and can be compared with other sounds later on. I need to know how I can achieve first the recording an processing in pyhton, and is stored the serialized sounds in Mysql databases the best way to go for this project? Also what packages would I need to do this (hopefully crossplatform). thx in advance!

---

### Post by Choad on 2007-02-18
> **kthakore said:**
> basically I wanted to make a python project, where it will process sounds from the microphone into a serialized form so it can be add to a mysql databases, and can be compared with other sounds later on. I need to know how I can achieve first the recording an processing in pyhton, and is stored the serialized sounds in Mysql databases the best way to go for this project? Also what packages would I need to do this (hopefully crossplatform). thx in advance!
python-gstreamer

the module is pygst

cant help you any further :(

---

### Post by kthakore on 2007-02-18
where can I find documentation for gstreamer, and will it process sound files so I can store them in a database

---

### Post by kthakore on 2007-02-18
I read the documentation, but the kinda suck. How do I record from the microphone on python 
gstreamer.

---

### Post by gh0st on 2007-02-18
I dunno if gstreamer-python will let you dump sound data into a database directly you would probably need to serialize it first using a python library like cPickle. You could then dump it in a database as a BLOB. There's quite a bit of info on cPickle in the Python Cookbook.

[http://aspn.activestate.com/ASPN/Python/Cookbook/](http://aspn.activestate.com/ASPN/Python/Cookbook/)

If you want to check out an established project that uses gstreamer-python for handling sound input you should check out Jokosher, I believe they have some cool code examples on their site as well.

[http://www.jokosher.org/contribute](http://www.jokosher.org/contribute)

There are links on that page to the Jokosher developers forum and those guys will know plenty about python and gstreamer development. Jokosher is a musicians recording application, it's built in python and uses gstreamer for pretty much everything. Hope that helps :)

---

### Post by kthakore on 2007-02-18
can you give a tutorial on how to use gstreamer on josher to record sounds in python. Josher seems more like a gui program, then a python module. Ps. thx for the tip on Cpickle

---

### Post by kthakore on 2007-02-19
bump

---

### Post by gh0st on 2007-02-19
> **kthakore said:**
> can you give a tutorial on how to use gstreamer on josher to record sounds in python. Josher seems more like a gui program, then a python module. Ps. thx for the tip on Cpickle

Hi, 

I don't really know anything about using gstreamer with Python personally as I've never done it, sorry. I just know Jokosher is a well developed project that uses it and I thought you might wanna look at it and maybe contact the developers for some pointers, they seem like friendly enough guys.

I did some hunting  around on the Jokosher development site and found this link to a pygst tutorial - [http://pygstdocs.berlios.de/pygst-tutorial/index.html](http://pygstdocs.berlios.de/pygst-tutorial/index.html)

Other than that I don't think I can really help sorry. I know a bit about Python but not in this kind of context. Hopefully the tutorial will be useful though :) 

Good luck

---

### Post by gh0st on 2007-02-19
I just found this document as well that might be of some use, it has some source code showing how Jokosher uses Gstreamer for channel controls. 

[http://jokosher.python-hosting.com/wiki/AudioSubsystem](http://jokosher.python-hosting.com/wiki/AudioSubsystem)

I dunno if you'll be able to pick anything from the code but it might be worth a look.

---

### Post by kthakore on 2007-02-20
using this gstreamer docs on the alsasrc plugins , and [this tutorial]("http://www.jonobacon.org/?p=750") I hacked together the script below. the orginal gstreamer pipeline is 
```
gst-launch-0.10 -v alsasrc ! audioconvert ! vorbisenc ! oggmux ! filesink location=alsasrc.ogg

``` 

it does work in the command line, but for some reason the script won't create a file in python.


```
#!/usr/bin/python

import pygst
pygst.require("0.10")
import gst
import pygtk
import gtk

class Main:
    def __init__(self):
        self.player = gst.Pipeline("player")
	source = gst.element_factory_make("alsasrc", "alsa-source")
	self.player.add(source)
	convert = gst.element_factory_make("audioconvert", "converter")
	self.player.add(convert)
	enc = gst.element_factory_make("vorbisenc", "vorbis-encoder")
	self.player.add(enc)
	create = gst.element_factory_make("oggmux", "ogg-create")
	self.player.add(create)
	fileout = gst.element_factory_make("filesink", "sink")
	fileout.set_property = ("location", "test.ogg")
	self.player.add(fileout)
	gst.element_link_many(source, convert, enc, create, fileout)


        self.player.set_state(gst.STATE_PLAYING)

start=Main()
gtk.main()


```

---

### Post by kthakore on 2007-02-20
when I run 
```
print self.player.get_state()
```


i get this output 
```
(<enum GST_STATE_CHANGE_FAILURE of type GstStateChangeReturn>, <enum GST_STATE_NULL of type GstState>, <enum GST_STATE_PLAYING of type GstState>)
```

---

### Post by kthakore on 2007-02-21
I fixed it, really just a bug:

```
   fileout.set_property("location", "test.ogg") 
```

how would I store this stream in a database using cPickle to convert it to a blob first.

---

### Post by gh0st on 2007-02-22
> **kthakore said:**
> I fixed it, really just a bug:

```
   fileout.set_property("location", "test.ogg") 
```

how would I store this stream in a database using cPickle to convert it to a blob first.

You would just have to import the cPickle library in your script and use it to serialize it, then use standard MySQL python and create a record in your database with one of the fields as a BLOB type. I'm not really sure if this is necessary though, you could just open the OGG file in binary read mode when you add your record to the DB. I'm not sure. Anyway here is a quick example of cPickle:

```
 
import cPickle
#open file in binary read
soundfile = open("mysound.ogg", 'rb')
#pickle data from file
binary = cPickle.dumps(soundfile, 2)
soundfile.close()

#you can now use "binary" to populate a field in a DB record
#you will need to find the appropriate Python code and setup you database code

#you might be able to do the same thing in one line with this code
binary = cPickle.dumps(open('mysound.ogg', 'rb'), 2)


```

I'm not very up on using MySQL and Python to store BLOB data sorry, you should really learn a bit about MySQL and then just use the OGG data to populate a binary field in a new record.

You might find this interesting: [http://forums.devshed.com/python-programming-11/storing-blob-in-mysql-db-116913.html](http://forums.devshed.com/python-programming-11/storing-blob-in-mysql-db-116913.html)

Hope that helps a bit.

---

### Post by kthakore on 2007-02-23
Thx a lot for your help ghost. Is there a way to compare serials of cPickle on runtime for changing pitches, volume, and other stuff in the sound file.

---

### Post by gh0st on 2007-02-24
> **kthakore said:**
> Thx a lot for your help ghost. Is there a way to compare serials of cPickle on runtime for changing pitches, volume, and other stuff in the sound file.

Sorry I don't know. There might be but you'd have to read the cPickle documentation and see. I have only used it for really small data tasks mostly. Just out of interest, why do you need to store your sound data in a database?? I don't think it will be a very efficient way to do it and may be more trouble than it's worth. Do you have some specific need to do it this way?

If it's because you want to be able to search the sound files and and use the query functionality of a database you could get the same functionality from using a normal folder on your hard drive.  Reading and writing data as BLOBs might slow the program down a lot. The tools Python has for indexing file systems and searching for stuff that way might be more efficient for you.

You could even go for a hybrid approach and store the files in a folder on your machine, then have a list of them in your database that you can search quickly and use. You could store extra data about the sound file in other fields in your records and just store the URLs for the files as a text field. That way you could search the database and just read the data from the file system.

Just a couple of suggestions they might not be any use to you I dunno. I haven't used BLOBs much but I heard they can be a pain for storing image files and I reckon sound files will be even bigger. It is an interesting idea though and I am interested to see if it works. Good luck with the program :)

---

