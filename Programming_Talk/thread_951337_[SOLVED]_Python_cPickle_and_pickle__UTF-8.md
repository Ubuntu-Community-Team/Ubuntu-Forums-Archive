---
title: "[SOLVED] Python: cPickle and pickle / UTF-8"
date: 2008-10-18
forum: Programming Talk
---

### Post by kumoshk on 2008-10-18
I'm making a flashcard program using the UTF-8 encoding.

Quite some time ago, I used the same code to save and load and it worked fine.

Now, however (my operating system, and consequently probably my Python version, have been updated extensively since), I get weird errors I never used to get (depending on whether I use pickle or cPickle):
 File "/usr/lib/python2.5/pickle.py", line 858, in load
    dispatch[key](self)
KeyError: u"p0\n(dp1\nS'numSides'\np2\nI2\nsS'shown'\np3\nI1\nsS'prevCard'"

File "main.py", line 129, in LoadList
    loadedList = cPickle.load(FILE)
cPickle.UnpicklingError: pickle data was truncated


Can anyone else using Hardy Heron and Python 2.5.2 get cPickle or pickle to work to both save and load UTF-8? If so, how do you manage it?

I think it might be a bug relating to the encoding.

---

### Post by loell on 2008-10-18
i hope its not related to this,..

[To Python, Unicode looked a lot like 8-bit binary byte strings, which could be passed along to the interpreter as part of the output from another program. In some cases, the interpreter would confuse binary data with Unicode-encoded strings, and it would choke, big-time.]("http://www.linux.com/feature/150399")

i doubt it, but still worth looking at.

---

### Post by kumoshk on 2008-10-21
Finally worked this one out.

Here's the code that seems to work:
    def SaveState(self, fileName):
        FILE = codecs.open(fileName, 'w', "utf-8")
        cPickle.dump(self, FILE)
        FILE.close()

    def LoadState(self, fileName):
        theList=CardList()
        FILE = codecs.open(fileName, 'r')
        theList = cPickle.load(FILE)
        FILE.close()
        return theList

Before, I had the "utf-8" thing on the LoadState function, as well&#8212;it brings up all sorts of errors with it, and the UTF-8 seems to work without it.

Also, I had a few other problems. I had some Group() objects initialized with the instance variables (I have no idea why, but I must have had a reason), and for some reason that caused problems with the loading. Initializing them in the constructor fixed the problem. The Group objects were things I used instead of lists, for added convenience (derived from the PyGame Sprite module).

I'm not sure how I got it working before, as I think it was that way before, but then, when I downloaded the old version to try it out, it had the same result as with the new version.

---

