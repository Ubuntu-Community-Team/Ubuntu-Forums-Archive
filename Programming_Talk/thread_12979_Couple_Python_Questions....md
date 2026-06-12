---
title: "Couple Python Questions..."
date: 2005-01-28
forum: Programming Talk
---

### Post by DirtDawg on 2005-01-28
So, forgive me for my ignorance, but I'm by no means a good programmer. I am strictly a tinkerer.

First: is there anyway to produce a "beep" from a linux box in Python? I would like to use a sound as an alarm after a set amount of time, but the Docs say nothing about a "beep" function. I did find a few modules concerning sound (sndhdr, I think was one. A couple others), but after experimenting with a few files, screwing them up bigtime in the process, I realized I had no idea how to utilize those tools whatsoever. 

Second: Gedit. I know this may not be the forum, but I can't figure out how to use auto-indents in gedit. I checked the auto indent buttons in the options menu, and I have the highlighting mode in "python", but there is no auto tabbing. Any suggestions?

Third: I just remembered this one. After creating a .py document, and chmoding (if that's really a word) the executive privledge, when I double click the python icon, I get a prompt asking if I would like to run the program or edit the file. Is there anyway to set them so they launch on the selection? Maybe deactivate the "write" privledge (hmm, i just thought of that)? 

Anyway, sorry I'm a huge n00b and thanks in advance for any help. 
  Gratz.  :)

---

### Post by Quest-Master on 2005-01-28
First: If you install the package "beep" from apt-get, you can do a exec("beep") from Python and it should produce a system beep.

Second: Use ScITE. sudo apt-get install scite ;)

Third: I just keep a terminal open in the directory where my Python file is and just type in python filenamere.py whenever I want to run it.

---

### Post by DirtDawg on 2005-01-28
ahHA! 

First: My Linux Box isn't hooked up to the internet. But I'm assuming I can find and download that package from the Ubuntu repository. I'm not entirely sure about the "exec(beep)" command. But I'll do my best to figure it out. (That is, after all, how one learns. Is it not?  :D ) Thank you!

Second: SciTE, eh? I'll try ScITE. Also in the repository, i suppose. Thank You!

Third: Keeping a terminal open seems a good idea. I've been doing that more and more lately. Seems natural with the Linux box. Mainly I want to use the icon run for my girlfriend, who wants nothing to do with a command line. Maybe I can use some kind of shortcut script or something. I haven't tried my "no write" priv theory yet. Haven't had the chance. But I'm thinking out loud now. Either way.. Thank you!

Linux people rock. Ubuntu people rock the house!

---

### Post by Buffalo Soldier on 2005-01-28
[QUOTE=DirtDawg]First: is there anyway to produce a "beep" from a linux box in Python? I would like to use a sound as an alarm after a set amount of time, but the Docs say nothing about a "beep" function. I did find a few modules concerning sound (sndhdr, I think was one. A couple others), but after experimenting with a few files, screwing them up bigtime in the process, I realized I had no idea how to utilize those tools whatsoever.[/QUOTE]

I'm not sure if this is the kind of beep that you want, but this is what I use. Maybe your're looking for something that sounds nicer for the alarm.
```
print "\a"
```
example
```
#!/usr/bin/python
print "Game Over"
**print "\a"**
raw_input("\n\nPress the enter key to exit.")
```

---

### Post by DirtDawg on 2005-01-28
That's right! I remember the "/a" trick now. That's exactly what I was looking for. I think I also remember reading another post from you stating you were learning Python. I hope that's going well for you. Can't be going too bad, as you're giving  pointers already. 
   Thank you!!  :D

---

### Post by DirtDawg on 2005-01-28
Oops. I mean the "\a" trick...

---

### Post by Buffalo Soldier on 2005-01-28
[QUOTE=DirtDawg]That's right! I remember the "/a" trick now. That's exactly what I was looking for. I think I also remember reading another post from you stating you were learning Python. I hope that's going well for you. Can't be going too bad, as you're giving  pointers already. 
   Thank you!!  :D[/QUOTE]

Darn, I was hoping no one would notice I was repeating the same script here :)

I'm doing fine. Python is cool and the community has been great. But progress has been slow, not much free time. Hope in a month time I can learn enough to create some simple program. Been thinking about a simple snake & ladder game using pyGTK. Just to test what I've learned.

---

### Post by DirtDawg on 2005-01-29
[QUOTE=Buffalo Soldier]Darn, I was hoping no one would notice I was repeating the same script here :)

I'm doing fine. Python is cool and the community has been great. But progress has been slow, not much free time. Hope in a month time I can learn enough to create some simple program. Been thinking about a simple snake & ladder game using pyGTK. Just to test what I've learned.[/QUOTE]

ha! I actually didn't know you posted the same script twice. (gave yourself away). I actually remember the '\a' trick from awhile ago when I was first learning Python. But I tried it on the Linux Box and it didn't work! :( It just prints a blank line. I don't think my sound is configured exactly right, so that may be the problem.

It's nice to hear someone's on about the same level as I as far as programming goes. I've written a few simple programs, but I'm pretty bad at it. Still, it's fun to dink around when I have the time (like you, my scheduale's pretty full). Let me know when you get around to writing some code. In particular, I'd like to see that Snakes and Ladders code. Sounds interesting. 
  
By the way, check out this site if you haven't already. It's got some interesting, amusing, and fairly simple, scripts that are interesting to browse through. Good for learning.
Useless Python: [http://www.uselesspython.com/](http://www.uselesspython.com/)

Peace

---

### Post by Buffalo Soldier on 2005-01-29
[QUOTE=DirtDawg]ha! I actually didn't know you posted the same script twice. (gave yourself away).[/quote]

Double darn. I must have left my brains on my bed when I woke up today. I hope this serves as a reminder to people not to read too much into this  "Ubuntu Guru" title :)
  
[QUOTE=DirtDawg]By the way, check out this site if you haven't already. It's got some interesting, amusing, and fairly simple, scripts that are interesting to browse through. Good for learning.
Useless Python: [http://www.uselesspython.com/](http://www.uselesspython.com/)

Peace[/QUOTE]

Thanks for the URL. Browsing it write now. I prefer useless python over 'usefull' VB anytime of the day :)

---

