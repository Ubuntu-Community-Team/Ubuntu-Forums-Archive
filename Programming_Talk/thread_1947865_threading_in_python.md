---
title: "threading in python"
date: 2012-03-27
forum: Programming Talk
---

### Post by krecoun on 2012-03-27
Hi, I want to create a python wrapper for mplayer, which will read subtitles for movies through speech dispatcher. It is mainly for visually impaired people like me. I am using mplayer.py module for controlling mplayer in slave mode and pysub module for accessing .srt files. I want to create simple ncurses interface, which will just wait for certain keyboard shortcuts for quitting, pausing, stopping, changing of voice rate etc. But now how to do this? I have two loops: curses waiting for keypresses and another waiting for right time, mplayer for the time of movie. I have put the second loop into thead and it looks like this:   class threadsub(threading.Thread):      def __init__(self):          super(threadsub, self).__init__()          self._stop = threading.Event()      def stop(self):          self._stop.set()      def stopped(self):          return self._stop.isSet()      def run(self):          global playing          for i in range (0, len(subs) - 1):              ms = float(subs[i].start.milliseconds)              ms = round(ms / 1000,1)              time = subs[i].start.hours * 3600 + subs[i].start.minutes * 60 + subs[i].start.seconds + ms              while playing == True:                  if time == round(p.time_pos,1):                      s.speak(subs[i].text)                      break                  if self.stopped() == True:                      playing = False              if self.stopped() == True:                  break   When i exit the program, i end curses and call threadsub.stop() But it doesn't stop, nor it raises an error. Can you please gi me an advice, how to do this properly? Or can you suggest other method for achieving this?  Forgive my possible mistakes when pasting code, I am posting something like this for the first time. Thank you.

---

### Post by Zugzwang on 2012-03-27
@OP: Please start by making your code more readable. Put your code between "CODE" tags and make sure that the indentation is kept. If not, edit your post afterwards. After this process, we can actually see what is happening in your code.

---

### Post by CynicRus on 2012-03-28
[http://jdolan.dyndns.org/trac/wiki/Pymp](http://jdolan.dyndns.org/trac/wiki/Pymp)

---

### Post by Zugzwang on 2012-03-28
> **CynicRus said:**
> [http://jdolan.dyndns.org/trac/wiki/Pymp](http://jdolan.dyndns.org/trac/wiki/Pymp)

You might want to elaborate on how this link is supposed to help the OP, as that tools cannot do what the OP wants to achieve with his/her project.

---

### Post by CynicRus on 2012-03-28
> **Zugzwang said:**
> You might want to elaborate on how this link is supposed to help the OP, as that tools cannot do what the OP wants to achieve with his/her project.
> I want to create simple ncurses interface, which will just wait for  certain keyboard shortcuts for quitting, pausing, stopping, changing of  voice rate etc. But now how to do this?The project is the link contains all the necessary information to work with mpla&#1085;er with python. But I could misunderstand the question, English is not my native language, (

---

### Post by krecoun on 2012-03-29
Well, I am satisfied with my mplayer solution with provided module.
But I can't convince my program to exit in normal way, I think that the thread is still running, however, I am not experienced enough with debugging to prove it.
I am attaching the code.
Thank you.

---

### Post by krecoun on 2012-03-29
Here it is:-) sorry, I am confused of this forum.

---

### Post by krecoun on 2012-03-29
attachment

---

### Post by CynicRus on 2012-03-29
If you need force kill thread - read [http://docs.python.org/library/threading.html#threading.Thread.daemon](http://docs.python.org/library/threading.html#threading.Thread.daemon)

---

### Post by Zugzwang on 2012-03-29
> **CynicRus said:**
> If you need force kill thread - read [http://docs.python.org/library/threading.html#threading.Thread.daemon](http://docs.python.org/library/threading.html#threading.Thread.daemon)

There is an easier, and probably better way: make "running" a class attribute of "threadsub". You would then have a code that looks like this:

[PHP]
...
class threadsub(threading.Thread):
    running = True	
    def run(self):
        playing = True
        for i in range (0, len(subs) - 1):
            ...
[/PHP]

Then, when you call "endcurses()", you could set "t.running = False". The next time your thread executes the line "if running == False", it will take the "if" and end the thread. You might need to replace that line by "if self.running == False", though.

---

### Post by Tony Flury on 2012-03-29
> **Zugzwang said:**
> There is an easier, and probably better way: make "running" a class attribute of "threadsub". You would then have a code that looks like this:


I am not sure that remembering to set flag when your main thread exits (for any reason) and ensuring that your sub-thread detects the flag and exits is in anyway easier than :

```

thread.daemon = True

```
As suggested by CynicRus 

No flags to set or test for - threads die automatically when the main thread exits (for whatever reason).

The only reason for the more complictated option of flags etc might be if you have some clean up that the thread needs to do when closing.

---

