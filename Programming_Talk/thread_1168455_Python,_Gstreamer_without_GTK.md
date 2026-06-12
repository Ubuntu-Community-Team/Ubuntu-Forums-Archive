---
title: "Python, Gstreamer without GTK"
date: 2009-05-24
forum: Programming Talk
---

### Post by matmatmat on 2009-05-24
Is there a way, in python, to use Gstreamer without GTK (cli)?

---

### Post by crdlb on 2009-05-24
Why wouldn't you be able to? GStreamer has no dependency on gtk+.

You can use a gobject.MainLoop instead of gtk.main if that's the problem you're seeing.

---

### Post by matmatmat on 2009-05-24
So far I have found [this]("http://irrepupavel.com/documents/cli_player/") which gives the error:
```

$ python cliaudioplayer.py /home/matio/Music/wbell.ogg
Traceback (most recent call last):
  File "cliaudioplayer.py", line 22, in <module>
    bin.set_property ("location", sys.argv[1])
TypeError: object of type `GstPipeline' does not have property `location'

```
& all the other code uses gtk with a "player" objects, eg:
```

self.player = gst.element_factory_make("playbin", "player")

```

---

### Post by SledgeHammer_999 on 2009-05-24
the code mentioned does a **src**.set_property ("location", sys.argv[1])
and not a **bin**.set_property ("location", sys.argv[1]). src points to the "filesrc" element which has a "location" property. bin is the pipeline and doesn't have a "location" property.

Disclaimer: I don't know python.

---

### Post by matmatmat on 2009-06-02
Ok, I now have this:
```

import gst, gobject, sys, gconf
mainloop = gobject.MainLoop()
# 1. We need to get the default audio sink, which is
#    basically the output we are going to use in the
#    GStreamer backend
# Get the GConf object
conf = gconf.client_get_default ()
# Get the key holding the audio sink
sink = conf.get ("/system/gstreamer/%d.%d/default/audiosink" % gst.gst_version[:-1])
# Check if the property actually exists
if sink is None:
        print >> sys.err, "Error retrieving system audio ouput driver."
        print >> sys.err, "Defaultign to OSS driver."
        sink = "osssink"
else:
        # Get the value in the key
        sink = sink.get_string ()
# 2. Create the GStreamer object needed to play the music
bin = gst.parse_launch ("filesrc ! decodebin ! %s" % (sink,))
# 3. Get the file source object and set its location
src = bin.get_list ()[0]
bin.set_property ("location", sys.argv[1])
# 4. Create the loop and hook up the end
bin.connect ("eos", mainloop.quit)
# 5. Start playing
bin.set_state (gst.STATE_PLAYING)
gobject.idle_add (bin.iterate)
mainloop.run()

```
& when run:
```

$ python cliaudioplayer.py 
Traceback (most recent call last):
  File "cliaudioplayer.py", line 21, in <module>
    src = bin.get_list ()[0]
AttributeError: 'gst.Pipeline' object has no attribute 'get_list'

```

---

### Post by crdlb on 2009-06-02
I think that example might be a bit out of date. There's a recent pygst tutorial here: [http://pygstdocs.berlios.de/pygst-tutorial/](http://pygstdocs.berlios.de/pygst-tutorial/)

I don't know GStreamer too well, but this should work as an extremely minimal example: ```
import gst
bin = gst.element_factory_make("playbin")
bin.set_property("uri", "uri goes here")
bin.set_state(gst.STATE_PLAYING)
```

---

### Post by matmatmat on 2009-06-04
It doesn't seem to play anything

---

### Post by crdlb on 2009-06-04
It works for me. Did you give it a proper URI? i.e. ```
file:///path/to/file
```not ```
/path/to/file
```

---

### Post by matmatmat on 2009-06-06
Still doesn't work & i know that the file exists, does it matter on the format? Its an ogg

---

### Post by matmatmat on 2009-06-06
CODE:
```

import gst
bin = gst.element_factory_make("playbin")
bin.set_property("uri", "file:///home/matio/Music/wbell.ogg")
bin.set_state(gst.STATE_PLAYING)

```

---

### Post by monraaf on 2009-06-06
Is that all the code?

You did import gobject and add a gobject.MainLoop().run() to it?

---

### Post by matmatmat on 2009-06-06
Since i added the gobject.MainLoop().run() it worked, how do I check if its finished playing?

---

### Post by monraaf on 2009-06-06
You add a signal watch to the bus.

e.g.

```

def on_eos(bus, msg):
    print 'EOS'
    bin.set_state(gst.STATE_NULL)

bus = bin.get_bus()
bus.add_signal_watch()
bus.connect('message::eos', on_eos)

```

---

### Post by SledgeHammer_999 on 2009-06-06
Check the tutorial here: [link](http://pygstdocs.berlios.de/#documentation)
And maybe you need some theory from the original guide: [link](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/index.html), [link2](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-bus.html) (although the examples are in C)

Basically you need to use the bus of the pipeline and attach to it a "watch". This watch will call a function of yours and inform you which messages have been emitted on the bus. One of these messages is the "end-of-file".

EDIT: or what **monraaf** said :p

---

### Post by matmatmat on 2009-06-06
```

import gst
import gobject
def on_eos(bus, msg):
    print 'EOS'
    gobject.MainLoop().quit()

bin = gst.element_factory_make("playbin")
bin.set_property("uri", "file:///home/matio/Music/wbell.ogg")
bin.set_state(gst.STATE_PLAYING)
bus = bin.get_bus()
bus.add_signal_watch()
bus.connect('message::eos', on_eos)
gobject.MainLoop().run()
print "END"

```
when run it doesn't print END
when ^C:
```

(cliaudioplayer.py:12971): GStreamer-CRITICAL **: 
Trying to dispose element preroll_audio_src0, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(cliaudioplayer.py:12971): GStreamer-CRITICAL **: 
Trying to dispose element selector_audio_src0, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(cliaudioplayer.py:12971): GStreamer-CRITICAL **: 
Trying to dispose element vorbisdec1, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(cliaudioplayer.py:12971): GStreamer-CRITICAL **: Failed to deactivate pad typefind:src, very bad

(cliaudioplayer.py:12971): GStreamer-CRITICAL **: Failed to deactivate pad oggdemux0:sink, very bad

(cliaudioplayer.py:12971): GStreamer-CRITICAL **: 
Trying to dispose element typefind, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(cliaudioplayer.py:12971): GStreamer-CRITICAL **: 
Trying to dispose element decodebin0, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(cliaudioplayer.py:12971): GStreamer-CRITICAL **: 
Trying to dispose element oggdemux0, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(cliaudioplayer.py:12971): GStreamer-CRITICAL **: 
Trying to dispose element source, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(cliaudioplayer.py:12971): GStreamer-CRITICAL **: 
Trying to dispose element playbin0, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

```

---

### Post by monraaf on 2009-06-06
You are creating a new mainloop in the eos message, if you want to quit your app you have to save the original mainloop in a variable an call quit on that one in the eos message.

e.g.

```

def on_eos(bus, msg):
    print 'EOS'
    bin.set_state(gst.STATE_NULL)
    mainloop.quit()

[...]

mainloop = gobject.MainLoop()
mainloop.run()

```

---

### Post by matmatmat on 2009-06-06
Thanks

---

### Post by matmatmat on 2009-06-06
I'm trying to make my entry for the Beginners Programming Challenge #4 play music:
```

#!/usr/bin/python
# -*- coding: utf-8 -*-

import random
import sys
import gst
import gobject

songs = [line.strip().split(" | ") for line in open("my_songs.txt")]
ordered = songs[:]
shuffle = False
current = 0
repeat = False
bin = gst.element_factory_make("playbin")
bin.set_property("uri", "file:///home/matio/Music/wbell.ogg")
bus = bin.get_bus()

def on_eos(bus, msg):
    print 'EOS'
    main.quit()

def nowPlayingP(current):
    global playstring
    try:
    	playstring = "Playing: %s | %s" % (songs[current][2], songs[current][0])
        bus.add_signal_watch() 
        bus.connect('message::eos', on_eos)
        bin.set_state(gst.STATE_PLAYING)
        main = gobject.MainLoop()
        main.run()

    except:
	print "The number passed was not valid, please use a lower number"
	return
    print playstring

def nowPlaying():
    global playstring
    playstring = "Now playing: %s | %s" % (songs[current][2], songs[current][0])
    print playstring

def help():
	print "Play      \t\tStart playing"
	print "Next      \t\tPlay next track"
	print "Next [num]\t\tGo forward [num] amount of tracks"
	print "Prev      \t\tPlay previous track"
	print "Prev [num]\t\tGo back [num] amount of tracks"
	print "Repeat    \t\tEnable repeats"
	print "Shuffle   \t\tEnable shuffle"
	print "Status    \t\tPrint currently playing track & weather shuffle & repeat are enabled"
	print "List      \t\tList the songs in playlist"
	print "&&        \t\tUsed to join commands together (see examples)"
	print "Help      \t\tPrint this message out"
	print 
	print "Eg:"
	print "play && next 10 && list"
	print "status"
	print "play && shuffle && repeat"

while True:
    try:
        command = raw_input("Enter command: ").strip().lower()
    except (KeyboardInterrupt, EOFError):
        print 
        exit()

    if command == "play":
        nowPlaying()
    elif command == "pause":
        print "Paused"
    elif command == "next":
        if not repeat:
            current += 1
        nowPlaying()
    elif command == "prev":
	if not repeat:
	    current -= 1
	nowPlaying()
    elif command.split(" ")[0] == "next":
	oldcurrent = current
        current += int(command.split(" ")[1])
        if current > len(songs):
		print "The number you entered is more thant the number of songs!"  
		print "Just doing 'next' ('next 1') instead"           
		current = oldcurrent + 1		
        nowPlaying()
    elif command.split(" ")[0] == "prev":
	oldcurrent = current
        current -= int(command.split(" ")[1])
        if current > len(songs):
		print "The number you entered is invalid!"  
		print "Just doing 'prev' ('prev 1') instead"      
                current = oldcurrent - 1
	elif current < 0:
		print "The number you entered is invalid!"      
                current = 0		
        nowPlayingP(current)
    elif command == "shuffle":
        shuffle = not shuffle
        if shuffle:
            random.shuffle(songs)
            print "Shuffle: on"
        else:
            songs = ordered[:]
            print "Shuffle: off"
    elif command == "repeat":
        repeat = not repeat
        if repeat:
            print "Repeat: on"
        else:
            print "Repeat: off"
    elif command == "status":
        print playstring
        if shuffle:
                print "Shuffle: on"
        else:
                print "Shuffle: off"
        if repeat:
                print "Repeat: on"
        else:
                print "Repeat: off"
    elif command == "list":
	for l in songs:
		print l
    elif command == "help":
	help()
    elif len(command.split(" && ")) > 0:
	for i in command.split(" && "):
    		if i == "play":
        		nowPlaying()
   		elif i == "pause":
        		print "Paused"
    		elif i == "next":
        		if not repeat:
            			current += 1
        		nowPlaying()
		elif command == "prev":
			if not repeat:
	    			current -= 1
			nowPlaying()
    		elif i.split(" ")[0] == "next":
			oldcurrent = current
        		current += int(i.split(" ")[1])
        		if current > len(songs):
				print "The number you entered is more thant the number of songs!"  
				print "Just doing 'next' ('next 1') instead"      
				current = oldcurrent + 1
			nowPlaying()
    		elif i.split(" ")[0] == "prev":
        		current -= int(i.split(" ")[1])
			nowPlayingP(current)
    		elif i == "shuffle":
       		 	shuffle = not shuffle
        		if shuffle:
            			random.shuffle(songs)
            			print "Shuffle: on"
        		else:
            			songs = ordered[:]
            			print "Shuffle: off"
    		elif i == "repeat":
        		repeat = not repeat
        		if repeat:
            			print "Repeat: on"
        		else:
            			print "Repeat: off"
		elif i == "status":
        		print playstring
        		if shuffle:
                		print "Shuffle: on"
       		 	else:
                		print "Shuffle: off"
        		if repeat:
                		print "Repeat: on"
        		else:
               			print "Repeat: off" 
		elif i == "list":
			for l in songs:
				print l
		elif i == "help":
			help()
		else:
			print "Please enter a valid command"  
	
    else:
        	print "Please enter a valid command"  

```
nothing plays?

---

### Post by SledgeHammer_999 on 2009-06-06
> **matmatmat said:**
> I'm trying to make my entry for the Beginners Programming Challenge #4 play music:
```

#!/usr/bin/python
# -*- coding: utf-8 -*-

import random
import sys
import gst
import gobject

songs = [line.strip().split(" | ") for line in open("my_songs.txt")]
ordered = songs[:]
shuffle = False
current = 0
repeat = False
bin = gst.element_factory_make("playbin")
bin.set_property("uri", "file:///home/matio/Music/wbell.ogg")
bus = bin.get_bus()

def on_eos(bus, msg):
    print 'EOS'
    main.quit()

def nowPlayingP(current):
    global playstring
    try:
    	playstring = "Playing: %s | %s" % (songs[current][2], songs[current][0])
        bus.add_signal_watch() 
        bus.connect('message::eos', on_eos)
        bin.set_state(gst.STATE_PLAYING)
        main = gobject.MainLoop()
        main.run()

    except:
	print "The number passed was not valid, please use a lower number"
	return
    print playstring

def nowPlaying():
    global playstring
    playstring = "Now playing: %s | %s" % (songs[current][2], songs[current][0])
    print playstring

def help():
	print "Play      \t\tStart playing"
	print "Next      \t\tPlay next track"
	print "Next [num]\t\tGo forward [num] amount of tracks"
	print "Prev      \t\tPlay previous track"
	print "Prev [num]\t\tGo back [num] amount of tracks"
	print "Repeat    \t\tEnable repeats"
	print "Shuffle   \t\tEnable shuffle"
	print "Status    \t\tPrint currently playing track & weather shuffle & repeat are enabled"
	print "List      \t\tList the songs in playlist"
	print "&&        \t\tUsed to join commands together (see examples)"
	print "Help      \t\tPrint this message out"
	print 
	print "Eg:"
	print "play && next 10 && list"
	print "status"
	print "play && shuffle && repeat"

while True:
    try:
        command = raw_input("Enter command: ").strip().lower()
    except (KeyboardInterrupt, EOFError):
        print 
        exit()

    if command == "play":
        nowPlaying()
    elif command == "pause":
        print "Paused"
    elif command == "next":
        if not repeat:
            current += 1
        nowPlaying()
    elif command == "prev":
	if not repeat:
	    current -= 1
	nowPlaying()
    elif command.split(" ")[0] == "next":
	oldcurrent = current
        current += int(command.split(" ")[1])
        if current > len(songs):
		print "The number you entered is more thant the number of songs!"  
		print "Just doing 'next' ('next 1') instead"           
		current = oldcurrent + 1		
        nowPlaying()
    elif command.split(" ")[0] == "prev":
	oldcurrent = current
        current -= int(command.split(" ")[1])
        if current > len(songs):
		print "The number you entered is invalid!"  
		print "Just doing 'prev' ('prev 1') instead"      
                current = oldcurrent - 1
	elif current < 0:
		print "The number you entered is invalid!"      
                current = 0		
        nowPlayingP(current)
    elif command == "shuffle":
        shuffle = not shuffle
        if shuffle:
            random.shuffle(songs)
            print "Shuffle: on"
        else:
            songs = ordered[:]
            print "Shuffle: off"
    elif command == "repeat":
        repeat = not repeat
        if repeat:
            print "Repeat: on"
        else:
            print "Repeat: off"
    elif command == "status":
        print playstring
        if shuffle:
                print "Shuffle: on"
        else:
                print "Shuffle: off"
        if repeat:
                print "Repeat: on"
        else:
                print "Repeat: off"
    elif command == "list":
	for l in songs:
		print l
    elif command == "help":
	help()
    elif len(command.split(" && ")) > 0:
	for i in command.split(" && "):
    		if i == "play":
        		nowPlaying()
   		elif i == "pause":
        		print "Paused"
    		elif i == "next":
        		if not repeat:
            			current += 1
        		nowPlaying()
		elif command == "prev":
			if not repeat:
	    			current -= 1
			nowPlaying()
    		elif i.split(" ")[0] == "next":
			oldcurrent = current
        		current += int(i.split(" ")[1])
        		if current > len(songs):
				print "The number you entered is more thant the number of songs!"  
				print "Just doing 'next' ('next 1') instead"      
				current = oldcurrent + 1
			nowPlaying()
    		elif i.split(" ")[0] == "prev":
        		current -= int(i.split(" ")[1])
			nowPlayingP(current)
    		elif i == "shuffle":
       		 	shuffle = not shuffle
        		if shuffle:
            			random.shuffle(songs)
            			print "Shuffle: on"
        		else:
            			songs = ordered[:]
            			print "Shuffle: off"
    		elif i == "repeat":
        		repeat = not repeat
        		if repeat:
            			print "Repeat: on"
        		else:
            			print "Repeat: off"
		elif i == "status":
        		print playstring
        		if shuffle:
                		print "Shuffle: on"
       		 	else:
                		print "Shuffle: off"
        		if repeat:
                		print "Repeat: on"
        		else:
               			print "Repeat: off" 
		elif i == "list":
			for l in songs:
				print l
		elif i == "help":
			help()
		else:
			print "Please enter a valid command"  
	
    else:
        	print "Please enter a valid command"  

```
nothing plays?

If you are refering to this challenge: [link](http://ubuntuforums.org/showthread.php?t=1156310&highlight=Programming+Challenge)
It clearly says that you don't need to implement a **real** player
> In this programming challenge we are going to take the first steps for creating an mp3/ogg player. Our mp3 player won't play music, actually, but it will pretend that it is playing a playlist.

---

### Post by matmatmat on 2009-06-06
I know, just as a project.
Anyways i've started from scratch using m3us:
```

import os
import gst
import gobject
import random

def on_eos(bus, msg):
        print "hi"
        main.quit()

def play(f):
        print "Playing %s" % (f.rstrip())
        bin = gst.element_factory_make("playbin")
        bin.set_property("uri", "file://" + f.rstrip())
        bin.set_state(gst.STATE_PLAYING)
        bus = bin.get_bus()
        bus.add_signal_watch()
        bus.connect('message::eos', on_eos)
        global main
        main = gobject.MainLoop()
        main.run()
        print "g"

file = open("/home/matio/fav.m3u", "r")
count1 = 1
count = 1
files = []
for line in file.readlines():
        if count1 > 2:
                if count >= 2:
                    files.append(os.path.abspath(line))
                    count = 0
        count += 1
        count1 += 1

random.shuffle(files)
for audio in files:
        play(audio)

```
is there a way I could skip tracks?

---

### Post by matmatmat on 2009-06-06
eg Next fuction
ways could do it (if its possible)
have a queue 
use somthing other than gobject

---

### Post by SledgeHammer_999 on 2009-06-06
When the user presses the "next button", you should set the pipeline to the "NULL" state. Then give to playbin the new uri and set the pipeline to the "PLAY" state.

---

### Post by matmatmat on 2009-06-06
Will it work while im in the mainloop?

---

### Post by matmatmat on 2009-06-07
bump

---

### Post by SledgeHammer_999 on 2009-06-07
why don't you try it and see?

---

### Post by matmatmat on 2009-06-08
I'd have to find a way of accepting input with music playing, which i don't know about

---

### Post by SledgeHammer_999 on 2009-06-08
If you made a gui this wouldn't be hard. Now that you make cli, you should make a different thread asking how to accept events while a gobject mainloop runs.(I don't know the answer)

---

