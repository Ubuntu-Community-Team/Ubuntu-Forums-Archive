---
title: "Rhythmbox Plugin for LED Cube"
date: 2009-04-17
forum: Programming Talk
---

### Post by Commander_Bob on 2009-04-17
Hello,

I built a 3D LED cube that uses and AVR ( ATmega168 ) to control the 27 RGB LED. The newest cube I have made has a serial port on it. I have only really done programming for microcontrollers, mostly in C, and I have a little experience with Linux programming.

What I would like to do is have the cube display visualizations based on music being played (preferably from Rhythmbox). I wanted to know the easiest/best way to go about doing this. Is there an easy way to generate the visualizations then send the data over serial to the cube?

Any help is great. As I said before, I am new to this kind of stuff and need some guidance.

You can see an older version of the cube on youtube [http://www.youtube.com/watch?v=_SO1J1kP3YQ]("http://www.youtube.com/watch?v=_SO1J1kP3YQ").

Thanks a lot,
Justin Rajewski

---

### Post by Commander_Bob on 2009-04-18
I made a little progress. Using this tutorial [http://live.gnome.org/RhythmboxPlugins/WritingGuide]("http://live.gnome.org/RhythmboxPlugins/WritingGuide") I was able to make a plugin that when it is started sends "Hello" over the serial port. I though that would be the hardest part. However now I don't know how to get the information I need to make the visual. I'd imagine I need something like sound intensity or frequency.

Is anyone familiar with python plugins for Rhythmbox and knows how to do this?

Here is what I have so far.
```
import rhythmdb, rb
import gobject, gtk
import serial

class SamplePython(rb.Plugin):

	def __init__(self):
		rb.Plugin.__init__(self)
			
	def activate(self, shell):
		print "activating sample python plugin"
		self.ser = serial.Serial('/dev/ttyS0', 115200, timeout=1)
		self.ser.write("hello")
		
	def deactivate(self, shell):
		print "deactivating sample python plugin"
		self.ser.close()
```

Thanks,
Justin Rajewski

---

### Post by evymetal on 2009-04-18
> **Commander_Bob said:**
> Is anyone familiar with python plugins for Rhythmbox and knows how to do this?

afraid not, but I believe that Rhythmbox uses Gstreamer, so you'd be working with that.

Here's a guide I found to making a rhythmbox visualisation, but it kind of assumes you already know how Gstreamer works.

[http://live.gnome.org/RhythmboxPlugins/WritingGuide#head-7a185be2a26176c61db014d8eeb8c980c95fbf15](http://live.gnome.org/RhythmboxPlugins/WritingGuide#head-7a185be2a26176c61db014d8eeb8c980c95fbf15)

---

### Post by DocForbin on 2009-04-18
cool. It might help to look at projectM

[http://projectm.sourceforge.net/](http://projectm.sourceforge.net/)

---

