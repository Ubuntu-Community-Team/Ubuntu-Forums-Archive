---
title: "[Python] Curses / Threading / Radio Tray"
date: 2012-10-20
forum: Programming Talk
---

### Post by Erik1984 on 2012-10-20
Hi all, sorry for the vague title but I couldn't think of a better one.

This is what I'm currently attempting: Take the Radio Tray source and strip it of references to the graphical parts (Systray.py and some GTK references). Then build a curses interface and connect it to the parts responsible for audio playback and state change events. I have succeeded in reducing the code but when I try to make a start with the curses part there is a problem. Curses seems to halt execution of the audio player.

The source of Radio Tray can be found here: [https://bitbucket.org/carlmig/radio-tray/src](https://bitbucket.org/carlmig/radio-tray/src) I use these files largely unmodified, the most modifications I have made to RadioTray.py

The [original code]("https://bitbucket.org/carlmig/radio-tray/src/f7722188acd024cbac1d373db3a0d30a5232b91f/src/RadioTray.py?at=default") initializes the state mediator, the audioplayer and then invokes systray.run() which contains the following GTK-code:
```

        gtk.gdk.threads_init()
        gtk.main()

``` 

I replaced that with a call to my own function
```

    self.startCurses()

```

Right now I have outcommented the curses part as there is a problem with that:
```

    def startCurses(self):
        #self.screen = curses.initscr()
        #self.screen.erase()
        s = ""
        while s != "quit":
            s = raw_input("> ")
            #s = self.screen.getstr(2,1)
            if s == "play":
               self.mediator.playUrl("http://somafm.com/poptron.pls")
        #curses.endwin()
                   
    def updateSong(self, data):
        #self.screen.addstr(1,1,"title: %s" % data['title'])
        print "title: %s" % data['title']
        
    def updateState(self, data):
        #self.screen.addstr(1,1,"state: %s" % data['state'])
        print "state: %s" % data['state']

```

In this form the code works. when typing 'play' the station from the fixed url is played. the updateState() and updateSong() methods are neatly called when there is new information. Which surprises me a bit as raw_input() is a blocking call just like curses' getstr() method. When I type play through the curses getstr method only the first "connecting" event is displayed then execution of the audio part seems to halt. This is confirmed by the log file where no new lines appears when normally the gstreamer part starts firing events on state changes of the radio stream. 

What I going on here? what makes curses different from the python code without curses?

I can also understand this post is way too vague and I can supply more code if necessary.

---

### Post by Erik1984 on 2012-10-22
Update bump: I'm a little closer now, curses is working with the stream playing on some background thread. I moved all curses stuff to a subclass of Thread called CursesThread. However I noticed that I have to call the GTK main loop after invoking the CursesThread. 

```

        t = CursesThread(self.mediator,self.provider)
        eventSubscriber.bind(EventManager.SONG_CHANGED, t.updateSong)
        eventSubscriber.bind(EventManager.STATE_CHANGED, t.updateState)
        t.start()
        
        gtk.gdk.threads_init()
        gtk.main()

```

If I uncomment the GTK lines the stream doesn't start playing when I invoke the playURL method from within the CursesThread.

---

### Post by Tony Flury on 2012-10-23
Why are you still using gtk threads when you aren't using a gtk gui ?

There are other threading framework that don't need gtk.

That may not be the source of the problem - but it wouldn't hurt to refactor to get rid of gtk completely.

---

### Post by Erik1984 on 2012-10-24
> **Tony Flury said:**
> Why are you still using gtk threads when you aren't using a gtk gui ?

There are other threading framework that don't need gtk.

That may not be the source of the problem - but it wouldn't hurt to refactor to get rid of gtk completely.

Thanks for replying.

Well if I remove the GTK threading calls then the curses thread will start but calls to the audioplayer (gstreamer) will hang at a certain point.

Can you point me to those other threading framework? I will take another look at the various .py files involved to strip it completely of GTK-depencies. 

The GTK dependencies must go indeed as I noticed that those dependencies also make the program require a running X server. Of course a curses app should never require X.

Just as a heads up, I've attached a screenshot of the current interface.

---

### Post by Tony Flury on 2012-10-24
WHat is wrong with the Python Threading library ?

[http://docs.python.org/library/threading.html](http://docs.python.org/library/threading.html)

I assume you have checked and you know for certain that the curses library and all the calls you use are thread safe ?

---

### Post by Erik1984 on 2012-10-25
There is nothing wrong with Python's threading library by itself but for me it doesn't play well with Gstreamer. I've found out that a gobject loop does the trick too:
```

        loop = gobject.MainLoop()
        gobject.threads_init()
        loop.run()
```I've removed all further gtk lines and imports now. Still when I run my program in tty1 I get lines like this: 
```
Command line `dbus-launch –autolaunch=eb95d80869be1ad62af36ec5502c41a1  –binary-syntax –close-stderr’ exited with non-zero exit status 1:  Autolaunch error: X11 initialization failed.\n
```While I can't spot any direct calls to dbus, so they must be made by gstreamer as those lines only appear when I start playing a radio stream. The music does play in TTY-mode though.

---

