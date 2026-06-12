---
title: "play sounds in python."
date: 2010-09-22
forum: Programming Talk
---

### Post by coolman98 on 2010-09-22
So I mas making a program (kind of a first) and I need to play a sound.
I have a function called on_water_pressed here is the source.
btw it is open source.

---

### Post by coolman98 on 2010-09-22
not wx please.

---

### Post by juancarlospaco on 2010-09-22
*OMG i forget how large things are on GTK, i use Python's built-in GUI, whatever...*
you can try:

```
os.system('mplayer file.ogg')
```

*Sorry if im wrong i dont have time to read it all.*

---

### Post by coolman98 on 2010-09-22
yhankx

---

### Post by coolman98 on 2010-09-22
where is the link.

---

### Post by coolman98 on 2010-09-22
it did not work

---

### Post by worksofcraft on 2010-09-22
If you want to use gstreamer there is a good tutorial for python... I look up the link in a mo. To get you started here is my gstreamet base class with little test program:
```

#!/usr/bin/python
import gst # gstreamer
import glib

class Playbin2:
	def __init__(self):
		self.idle = True # not playing at the moment
		# create a playbin2 pipe
		self.player = gst.element_factory_make("playbin2", "player")
		# connect a signal handler to it's bus
		bus = self.player.get_bus()
		bus.add_signal_watch()
		bus.connect("message", self.on_message)

	def on_message(self, bus, message):
		t = message.type
		if t == gst.MESSAGE_EOS:
			self.player.set_state(gst.STATE_NULL)
			self.idle = True
		elif t == gst.MESSAGE_ERROR:
			err, debug = message.parse_error()
			print >> sys.stderr, "Error: {0} {1}".format(err, debug)
			self.player.set_state(gst.STATE_NULL)
			self.idle = True
		return self.idle

	def play(self, stream):
		# abort previous play if still busy
		if not self.idle:
			print >> sys.stderr, 'audio truncated'
			self.player.set_state(gst.STATE_NULL)
		self.player.set_property("uri", stream)
		self.player.set_state(gst.STATE_PLAYING)
		self.idle = False # now playing

# a test program for our basic gstreamer class
# plays a standard system sound than hangs in message pump loop
# use Ctrl-C to get out
if __name__ == "__main__":
	Playbin2().play("File:///usr/share/sounds/gnome/default/alerts/drip.ogg")
	glib.MainLoop().run()

```

---

### Post by worksofcraft on 2010-09-22
OK so that tutorial link is:
[http://pygstdocs.berlios.de/pygst-tutorial/index.html](http://pygstdocs.berlios.de/pygst-tutorial/index.html)

oh and here is example how you can derive more specialized gstreamer class form the base one I provided above:
```


#!/usr/bin/python
from playbin2 import * # basic gstreamer pipe
from collections import deque # queue files to play
import sys # to read command line
import os # to test if file exists

# a GStreamer that specifically ditches unwanted video streams
class AudioFilePlayer(Playbin2):
	def __init__(self):
		Playbin2.__init__(self)
		# ditch the video into a fake sink element
		fakesink = gst.element_factory_make("fakesink", "fakesink")
		self.player.set_property("video-sink", fakesink)
		# a queue of files to play starts empty
		self.playQueue = deque([])

	def play_file(self, filepath):
		# avoid playing files that don't exist
		if filepath and os.path.isfile(filepath):
			uri = "file://" + filepath
			# start playing immediately if idle
			if self.idle:
				Playbin2.play(self, uri)
			# otherwise queue it
			else:
				self.playQueue.append(uri)
		# report when file not found
		else:
			print >> sys.stderr, 'audio file not found {0}'.format(filepath)

	def on_message(self, bus, message):
		# when becoming idle get next entry from the queue
		if Playbin2.on_message(self, bus, message):
			try:
				self.play(self.playQueue.popleft())
			except IndexError:
				# print ('queue empty')
				pass

# needs full path of files so test with something like
# ./audiofileplayer.py /usr/share/sounds/gnome/default/alerts/*.ogg
if __name__ == "__main__":
	# create an audio file player pipeline
	player = AudioFilePlayer()
	# queue all the files specified on command line
	for filepath in sys.argv[1:]:
		player.play_file(filepath)
	# run the message pump
	glib.MainLoop().run()

```

---

### Post by coolman98 on 2010-09-22
I put it in and now the gui doesn't start

---

### Post by coolman98 on 2010-09-22
sigh.........

---

### Post by coolman98 on 2010-09-22
bump

---

### Post by worksofcraft on 2010-09-23
What did you put in?

I tried to run your noise-machine but it just says
" File "./noise-machine.py", line 32, in <module>
    from noise_machine import (
ImportError: No module named noise_machine"

I don't really understand what you are trying to import there.

Did you try running AudioFilePlayer.py script I posted earlier? If you run it as main then it should play sound files you specify on the command line. When that works you can import it into your own script to play sound files as you need. OTOH if it isn't working... let me know what it says and perhaps I can work out what is going wrong.

---

### Post by coolman98 on 2010-09-23
oh yeah you need all the code
here is the new stuff

---

### Post by coolman98 on 2010-09-23
here is the rest.
sorry If I confused you im such an python nube.

---

### Post by juancarlospaco on 2010-09-23
60 Lines, no WX,
[SIZE="1"]Skin support*[COLOR="Gray"](?)[/COLOR]*, plays MP3, About dialog, Volume Slider, Open File Dialog, window Icon, dont need QT, dont need GTK, makes a Sandwich, tends to Entropy:[/SIZE]

```

#!/usr/bin/env python
# -*- coding: utf-8 -*-
# Dependencies: sudo apt-get install python-tk
# GPLv3
from Tkinter import *
import mp3play
import tkFileDialog
import tkMessageBox
import Tkinter
from tkColorChooser import askcolor
#
def open_file(): # Open dah file                             
    global music                               
    global mp3      
    filename.set (tkFileDialog.askopenfilename())
    mp3 = filename.get()
    music = mp3play.load(mp3)
    pieces = mp3.split("/")
    name.set (pieces[-1])            
def vol(event): # Volume 
    v = Scale.get(volume_slider)
    music.volume(v)
def Skin(): # Skin support
    (triple, hexstr)=askcolor()
    if hexstr:
        root.config(bg=hexstr)
        volume_slider.config(bg=hexstr) 
        file_name_label.config(bg=hexstr) 
        play_button.config(bg=hexstr)
        stop_button.config(bg=hexstr)
        open_file.config(bg=hexstr)
        skin.config(bg=hexstr)
        about.config(bg=hexstr)
        cloze.config(bg=hexstr)
# Base Window, title and icon 
root = Tk()
root.title("Music Player")
root.focus()
try:
    root.wm_iconbitmap('@'+'/usr/include/X11/bitmaps/icon')
except TclError:
    print " ERROR: Icon File not found... "
    pass
filename = Tkinter.StringVar()
name = Tkinter.StringVar()
# GUI
play_button = Button(root, width = 5, height = 1, text='&#8811;', font=("Times", 10, 'bold'), fg='blue', bd=0, relief=FLAT, cursor='hand2', command = lambda: music.play() )
play_button.grid(row=0, column=0, sticky = W)
stop_button = Button(root, width = 5, height = 1, text='&#9632;', font=("Times", 10, 'bold'), fg='blue', bd=0, relief=FLAT, cursor='hand2', command = lambda: music.stop() )
stop_button.grid(row=0, column=1, sticky = W)
open_file = Button(root, width = 5, height = 1, text = '&#9650;', font=("Times", 10, 'bold'), fg='blue', bd=0, relief=FLAT, cursor='hand2', command = open_file)
open_file.grid(row=0, column=3)
about = Button(root, bitmap='question', font=("Times", 10, 'bold'), fg='grey', bd=0, command = lambda: tkMessageBox.showinfo('About', 'Cool music player') )
about.grid(row=0, column=4)
skin = Button(root, width = 5, height = 1, text = 'Skin', font=("Times", 10, 'bold'), fg='blue', bd=0, relief=FLAT, cursor='hand2', command = Skin)
skin.grid(row=0, column=5)
cloze = Button(root, width = 5, height = 1, text = '&#10007;', font=("Times", 10, 'bold'), fg='blue', bd=0, relief=FLAT, cursor='hand2', command = lambda: root.destroy() )
cloze.grid(row=0, column=6)
volume_slider = Scale(root, label=' &#9601;&#9602;&#9603;&#9604;&#9605;&#9606;&#9607;&#9608; ', orient = 'horizontal', fg = 'black', bd=0, relief=FLAT, cursor='hand2', command = vol)
volume_slider.set('75')
volume_slider.grid(row=0, column=7)
file_name_label = Label(root, font=('Verdana', 8), fg = 'black', bd=0, relief=FLAT, wraplength = 300, textvariable= name )
file_name_label.grid(row=3, column=0, columnspan=8)
#
root.mainloop()

```

:P

---

### Post by worksofcraft on 2010-09-23
> **coolman98 said:**
> here is the rest.
sorry If I confused you im such an python nube.

Lol - me too I spend one week learning Python and I decided it's quite cute but I still prefer to program in C++. Anyway I downloaded those files and as soon as I get a moment I'll see if I can patch in some sounds for you.

p.s. update:
I tried just making everything run in the same folder to avoid problems with paths, but  I think it's still looking for a file called SoundMachineWindow.ui and I haven't got one so that's why no gui is appearing on my computer.

---

### Post by coolman98 on 2010-09-23
sorry none of those work thanks for thr help but I need the module.

---

### Post by coolman98 on 2010-09-24
bump.

---

### Post by OgreProgrammer on 2010-09-24
The most simple I have come across is this. 
```

#!/usr/bin/python
''' the library is called python-xine or some such '''
import pyxine
xine = pyxine.Xine()
stream = xine.stream_new()
stream.open('[unknown].ogg')
stream.play()

```The song will only play as long as the py file is running of course. and pyxine is not available for windows.

---

### Post by coolman98 on 2010-09-26
thank you I will try

---

### Post by coolman98 on 2010-09-26
```
Traceback (most recent call last):
  File "/usr/share/quickly/templates/ubuntu-application/run.py", line 63, in <module>
  File "/usr/bin/quickly", line 135, in <module>
    subprocess.call(command_line)
  File "/usr/lib/python2.6/subprocess.py", line 470, in call
    exit(main())
  File "/usr/bin/quickly", line 120, in main
    return(command.launch(os.getcwd(), opt_command[1:], opt_template))
  File "/usr/lib/python2.6/dist-packages/quickly/commands.py", line 453, in launch
    return Popen(*popenargs, **kwargs).wait()
  File "/usr/lib/python2.6/subprocess.py", line 1182, in wait
    [self.command] + command_args, cwd=project_path)
  File "/usr/lib/python2.6/subprocess.py", line 470, in call
    return Popen(*popenargs, **kwargs).wait()
  File "/usr/lib/python2.6/subprocess.py", line 1182, in wait
    pid, sts = _eintr_retry_call(os.waitpid, self.pid, 0)
  File "/usr/lib/python2.6/subprocess.py", line 455, in _eintr_retry_call
deleting Stream
    pid, sts = _eintr_retry_call(os.waitpid, self.pid, 0)
  File "/usr/lib/python2.6/subprocess.py", line 455, in _eintr_retry_call
    return func(*args)
KeyboardInterrupt
Stream deleted
AudioPort deleted
    return func(*args)
KeyboardInterrupt
VideoPort deleted
Xine deleted

```

---

### Post by coolman98 on 2010-09-27
bump.

---

### Post by OgreProgrammer on 2010-09-28
coolman, it looks like you are supplying subprocess.call with one parameter when it requires two. run.py on line 63. 

[http://docs.python.org/library/subprocess.html#subprocess.call](http://docs.python.org/library/subprocess.html#subprocess.call)

---

### Post by coolman98 on 2010-09-28
here is new output.```
params.c:OpenConfFile() - Unable to open configuration file "/home/christopher/.smb/smb.conf":
    No such file or directory
params.c:OpenConfFile() - Unable to open configuration file "/home/christopher/.smb/smb.conf.append":
    No such file or directory
deleting Stream
Stream deleted
AudioPort deleted
VideoPort deleted
Xine deleted
```

---

### Post by Nebelhom on 2010-09-29
I haven't looked at the code, but I had a similar issue to play sounds.

The options I found were:

- mp3play
- pyaudiere (although i could only get it to install correctly in windows. Maybe you get it to work in ubuntu)
- pygame

I ended up using pyaudiere in windows, because most of the people who would use the applet use windows anyways and the use of it is dirt easy, but I think pygame is also worth a shot.

hope that helps

---

### Post by coolman98 on 2010-09-29
sigh.

---

### Post by coolman98 on 2010-10-01
bump.

---

