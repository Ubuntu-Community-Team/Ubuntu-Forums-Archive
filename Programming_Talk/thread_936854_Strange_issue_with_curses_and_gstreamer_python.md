---
title: "Strange issue with curses and gstreamer :python"
date: 2008-10-03
forum: Programming Talk
---

### Post by Xavieran on 2008-10-03
I am experimenting with gstreamer in python, using this tutorial:[http://pygstdocs.berlios.de/pygst-tutorial/pipeline.html]("http://pygstdocs.berlios.de/pygst-tutorial/pipeline.html")

I decided to set myself an exercise, to translate the first code example into a curses application.

I have done so...but when I run the program, I get this error message:
```
Unhandled exception in thread started by <bound method CLI_Main.main of <__main__.CLI_Main instance at 0x81b2a0c>>

```

I have tracked it down to be something to do with curses, and I have noticed that curses does not event display the strings I have told it to...

Code here:
```
#!/usr/bin/env python
#
#Command line example of gstreamer pipelines

import sys,os,time,thread
import gobject
import pygst
import gst
import curses

class CLI_Main:
    def __init__(self):    
        self.screen=curses.initscr()
        curses.echo()
        curses.cbreak()
        self.player=gst.Pipeline('player')

        source=gst.element_factory_make('filesrc','file-source')
        decoder=gst.element_factory_make('mad','mp3-decoder')
        conv=gst.element_factory_make('audioconvert','converter')
        sink = gst.element_factory_make("alsasink", "alsa-output")
        self.player.add(source,decoder,conv,sink)
        gst.element_link_many(source,decoder,conv,sink)

        bus=self.player.get_bus()
        bus.add_signal_watch()
        bus.connect("message",self.on_message)
    	    
    def on_message(self,bus,message):
        t=message.type
        if t == gst.MESSAGE_EOS:
            self.player.set_state(gst.STATE_NULL)
            self.playmode=False
        if t == gst.MESSAGE_ERROR:
            self.player.set_state(gst.STATE_NULL)
            err,debug =message.parse_error()
            print 'Error: %s'%err,debug
            self.playmode=False
            
    def main(self):
        self.screen.addstr(1,1,'MP3 Player')
        self.screen.addstr(3,1,'File:')
        self.screen.addstr(4,1,'Press f to change file')
        self.screen.addstr(5,1,'Press s to toggle between started and stopped')
        self.screen.addstr(7,1,'=>')
        self.screen.addstr(8,1,'Not Playing')
        while 1:
            self.move(7,3)
            key=chr(self.screen.getch())
            if key=='f':
                self.move(3,6)
                filepath=self.screen.getstr()
                self.player.get_by_name("file-source").set_property(\
                "location",filepath)
                self.player.set_state(gst.STATE_PLAYING)
                self.screen.move(8,1)
                self.screen.clrtoeol()
                self.screen.addstr(8,1,'Playing')
            elif key=='s':
                if self.player.get_state()[0]==gst.STATE_PLAYING:
                    self.player.set_state(gst.STATE_NULL)
                    self.screen.addstr(8,1,'Not Playing')
                elif self.player.get_state()[0]==gst.STATE_NULL:
                    self.player.set_state(gst.STATE_PLAYING)
                    self.screen.move(8,1)
                    self.screen.clrtoeol()
                    self.screen.addstr(8,1,'Playing')
            else:pass
                    
mainclass=CLI_Main()
thread.start_new_thread(mainclass.main,())
gobject.threads_init()
loop=gobject.MainLoop()
loop.run()

        
```

---

### Post by Xavieran on 2008-10-03
Bump.

---

