---
title: "Python segfault?"
date: 2010-09-10
forum: Programming Talk
---

### Post by j.bell730 on 2010-09-10
How does this happen? I'm quite sure it's not a problem with my code (could it be a problem with the interpreter?) It screen scrapes a site to build an array of video game items and platforms (each array item is a string). It then displays a random string from the array. It uses threads and wx.

[PHP]#!/usr/bin/python

import wx, re, urllib, thread

# Define function for threading.
def GetVG(OutputMedium):
    GameLocations = []
    GamePlatform = []
    
    # Show status in read-only, multiline textbox.
    OutputMedium.AppendText('Getting games and platforms from the web...\n')
    # Screen scrape to get my list of video games on each platform.
    GameSite = urllib.urlopen('http://raptr.com/jbell730/games?src=hdr').read()
    try:
        Matches = re.compile('href="/game/(.*?)/(.*?)">.*?</a>')

        for Platform, Game in Matches.findall(GameSite):
            # Append string with Game and Platform to array.
            GameLocations.append('%s for %s' % (Game.replace('_', ' '), Platform))
            OutputMedium.AppendText('Got ' + Game + ' for ' + Platform)
        OutputMedium.AppendText('Done!\n')
    except:
        print 'Failed.'

class Raptr(wx.App):
    def __init__(self, redirect=False, filename=None):
        wx.App.__init__(self, redirect, filename)
        self.RaptrFrame = wx.Frame(None, wx.ID_ANY, title='Raptr Game Chooser', size=(640, 480))
        self.RaptrPanel = wx.Panel(self.RaptrFrame, wx.ID_ANY)
        
        self.OutputBox = wx.TextCtrl(self.RaptrPanel, style=(wx.TE_READONLY | wx.TE_MULTILINE), size=(632, 128), pos=(4, 348))
        self.GameList = wx.StaticText(self.RaptrPanel, label='Getting games and platforms...', pos=(450, 8))
        
        self.RaptrFrame.Show()
        
        # Create thread to get all games while displaying the GUI.
        thread.start_new_thread(GetVG, (self.OutputBox, ))

if __name__ == '__main__':
    app = Raptr()
    app.MainLoop()[/PHP]

This is the output I get (actually the output varies based on some unknown variable):
[PHP](python:2454): Gtk-WARNING **: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.
You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.
You can apply tags and insert marks without invalidating your iterators,
but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)
will invalidate all outstanding iterators

(python:2454): Pango-CRITICAL **: pango_layout_get_iter: assertion `PANGO_IS_LAYOUT (layout)' failed
Segmentation fault[/PHP]
This is just an exercise in GUI programming (obviously still unfinished), but if someone can spot something in my code that might be causing it, let me know!

---

### Post by juancarlospaco on 2010-09-10
Lulz, for some reason you are using GTK anyways *(?)*

"(python:2454): **Gtk**-WARNING **: Invalid text buffer iterator"

---

### Post by smartbei on 2010-09-11
I believe the problem is that GUI frameworks tend not to like their objects being updated by threads other than the main thread.

I would try changing the code so that the GetVG function updates a queue, and the main thread updates the GUI object itself. This can be accomplished with a timer every 50ms (for example), that checks if the queue is empty. If not, it updates the GUI.

---

### Post by j.bell730 on 2010-09-11
> **smartbei said:**
> I believe the problem is that GUI frameworks tend not to like their objects being updated by threads other than the main thread.

I would try changing the code so that the GetVG function updates a queue, and the main thread updates the GUI object itself. This can be accomplished with a timer every 50ms (for example), that checks if the queue is empty. If not, it updates the GUI.

You're right. Problem solved. Thank you.

---

