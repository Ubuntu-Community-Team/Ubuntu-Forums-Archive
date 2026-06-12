---
title: "Low performance, eReader problems"
date: 2014-04-08
forum: New to Ubuntu
---

### Post by andy_h2 on 2014-04-08
I'm running a desktop with a Pentium 4 2.53GHz, 1.25gb of ram with XP, and since support is ending I figured I would try out Ubuntu as an alternative by installing a dual boot.  Needless to say I am rather underwhelmed...

I use the computer for a few simple things, but one is I use my laptop as an eReader.  I want to change the background of a document to something easy on the eyes, I want to be able to edit it and add notes, AND I want full screen WITHOUT the stupid idiot box hanging around reminding me how to esca pe from full screen mode!  I guess something this advanced is impossible?  LibreOffice can't do it.  Neither can Calligra Words.  I wasted hours trying to figure out how to do something this simple.  Does anyone know if this is possible?

Also it's running incredibly slow.  When I'm installing things it sometimes will freeze up entirely or take an inordinate amount of time to finish.  When I click on something and get no response I immediately start begging this OS; "I'm sorry, PLEASE, I didn't mean IT, don't freeze up again!"  At this point I have an instinctual dread of clicking on anything and wish I had a Ctrl+Alt+Delete option available every time I do!

I always heard this was a really fast operating system, light weight, no bloatware.  Well XP runs great on this machine, so I figured Ubuntu would run as good or better! I have no idea what I've done wrong here, unless of course this OS isn't as nimble as the 12 year old XP? On top of that this Software Center feels bloated like iTunes with too much flash that seems to slow down the search and install process.

I know this thing is free and all, but I've only got so much time to devote, not to LEARNING how to get use to it, but just make it do basic tasks.

Andy

---

### Post by sudodus on 2014-04-08
Welcome to the Ubuntu Forums :-)

Standard Ubuntu is made for more powerful computers, but there a flavours of Ubuntu with the same engine under the hood, but lighter desktop environment (graphics),

Lubuntu 13.10 with the ultra-light LXDE desktop environment
Xubuntu 12.04 LTS and 13.10 with the medium light XFCE desktop environment.

I suggest that you download the corresponding desktop iso files and try these two flavours of Ubuntu live (without installing) and select the one you like the best. I promise you will see a great improvement.

---

### Post by andy_h2 on 2014-04-08
Thanks for the reply, I will give those a try.  Still the eReader thing is a deal breaker for me.

Andy

---

### Post by sudodus on 2014-04-08
I don't know if there is an eReader or equivalent program in linux. Let us hope someone who knows can chip in and tell us about it.

---

### Post by 23dornot23d on 2014-04-08
You might be better off looking at Knoppix version 7.0.5 ...... its set up from the start
for the reasons you mention ....... adriane its called and installs very quickly and easily to flash
and older drives to try out and use. [http://www.knopper.net/knoppix-adriane/index-en.html](http://www.knopper.net/knoppix-adriane/index-en.html)

Just a thought - not to drive you away from here - but its an option ......

The same things can be set up - they just may take time to do ......... also orca is good
as a voice reader ...... this is also set up in knoppix from start off .......

There are readers included and packages are set up to make it easy to use.

Sounds as if the install you have is too much for the system - that is why I point you to something much lighter .......
___________________________________________________

But if you do stick with Ubuntu

sudo apt-get update
sudo apt-get install lxde

Then when you login - choose lxde - you may find it much quicker to use ........

also for ubuntu ......... [https://apps.ubuntu.com/cat/applications/fbreader/](https://apps.ubuntu.com/cat/applications/fbreader/)

---

### Post by ajgreeny on 2014-04-08
Regarding your eReader, it will depend very much what type of ereader files you have; Ubuntu will not be able to read any Kindle books that you may have, I'm afraid, though it may be OK for other types.

---

### Post by monkeybrain20122 on 2014-04-08
> **andy_h2 said:**
> Thanks for the reply, I will give those a try.  Still the eReader thing is a deal breaker for me.

Andy

[http://calibre-ebook.com/](http://calibre-ebook.com/)

It is very easy to install, there is an older version in the repository (but developer suggests not to use it as calibre updates every week)

There is also a ppa (for *buntu 13.10 only), it is a lot more updated than the one in the repo, but still a bit old
[https://launchpad.net/~n-muench/+archive/calibre](https://launchpad.net/~n-muench/+archive/calibre)
To use it add it to your sources list, update and install calibre. Depending on your desktop environment there are different guis to do it (synaptic, software centre), but the fastest way is to simply to it in the terminal, open a terminal, cut and paste the following commands and hit return one after another

```
sudo add-apt-repository ppa:n-muench/calibre 
sudo apt-get update
sudo apt-get install calibre
```

**Edited:** To use calibre with drmed ebooks such as kindle you need a plugin  [http://sharpeespace.blogspot.ca/2011/05/view-kindle-books-on-ubuntu-linux-1010.html](http://sharpeespace.blogspot.ca/2011/05/view-kindle-books-on-ubuntu-linux-1010.html)

---

### Post by andy_h2 on 2014-04-08
I forgot to mention in my first post that I installed Calibre too.  The problem isn't the file TYPES, I am use to converting epub and mobi files to RTF so I can read them in MS Word.  Every time I click to "View" a document in Calibre, it opens it in LibreOffice, which leads to me the real problem...

The problem isn't converting ebooks the problem the pop-up dialogue box in LibreOffice that won't go away in full screen mode which tells you how to exit from full screen mode.  I know how to press Esc.  If I could find a way to fix this, Ubuntu might be a viable alternative.

 
Andy

---

### Post by monkeybrain20122 on 2014-04-08
What popup box? I don't see any popup box when switch to full screen, only a button at the corner to toggle to exit full screen, and why would anyone want to read ebooks in word format?

---

### Post by andy_h2 on 2014-04-08
> **monkeybrain20122 said:**
> What popup box? I don't see any popup box when switch to full screen, only a button at the corner to toggle to exit full screen, and why would anyone want to read ebooks in word format?

Yeah, that button for exiting full screen is what I don't want.  It's distracting and annoying.  All I want is that to go away and there to just be flowing text.

When I read eBooks I make notes within the text and edit things.  Reading in Word allows me to set the background color, font, formatting, etc to whatever I want and get into the text and summarize chapters, add notes, point things out, etc.  Just put a symbol like ** beside my notes and later when I come back I can hit Ctrl+F and easily find them all.  If you know of another free program that will let me do this, save the book in a widely recognized format I can open later and quickly find my notes, I'm fine with that.


Andy

---

### Post by monkeybrain20122 on 2014-04-08
You can make notes and annotations with okular if the files are converted to pdf. There is no universal way to implement these functions because the standards are all different.

---

### Post by andy_h2 on 2014-04-08
> **monkeybrain20122 said:**
> You can make notes and annotations with okular if the files are converted to pdf. There is no universal way to implement these functions because the standards are all different.

I'm fine with using Calibre to convert different file formats to one format I can read in LibreOffice or some other program.  I do this all the time.

Andy

---

### Post by HermanAB on 2014-04-09
Probably the nicest program for reading and annotating PDF files is Xournal.

---

