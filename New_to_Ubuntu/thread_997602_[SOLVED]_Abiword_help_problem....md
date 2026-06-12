---
title: "[SOLVED] Abiword help problem..."
date: 2008-11-30
forum: New to Ubuntu
---

### Post by mesmith on 2008-11-30
In using Abiword I was inserting page numbers and clicked the Help button.  I got a Firefox msg that said it couldn't find the html doc at the path it was looking in:  /usr/share/abiword-2.6/AbiWord/help/en-US/interface/dialogpagenumbers.html

I took a look at the path and noticed that Abiword is looking for the file on a path that doesn't exist.  The path that does exist looks like this:  /usr/share/abiword-2.6/help/en-US/interface/dialogpagenumbers.html

Notice that the installed data path lacks the level /Abiword/ that follows /abiword-2.6/

Any fix for this?  Is there some way to change Abiword's path for help?

---

### Post by seren6ipity on 2008-11-30
Abiword should be looking at [http://www.abisource.com/help/en-US/interface/dialogpagenumbers.html](http://www.abisource.com/help/en-US/interface/dialogpagenumbers.html) rather that looking at /usr/share/

You can file a bug by going to document help - report a bug


> **mesmith said:**
> In using Abiword I was inserting page numbers and clicked the Help button.  I got a Firefox msg that said it couldn't find the html doc at the path it was looking in:  /usr/share/abiword-2.6/AbiWord/help/en-US/interface/dialogpagenumbers.html

I took a look at the path and noticed that Abiword is looking for the file on a path that doesn't exist.  The path that does exist looks like this:  /usr/share/abiword-2.6/help/en-US/interface/dialogpagenumbers.html

Notice that the installed data path lacks the level /Abiword/ that follows /abiword-2.6/

Any fix for this?  Is there some way to change Abiword's path for help?

---

### Post by mesmith on 2008-11-30
Many thanks.  Filed a bug report.  Seems weird that all these help docs are sitting on my hard drive when it wants to look for online help.  Maybe a change in philosophy, but why install all the files?  Do they expect everyone to be online at all times?

Thanks again,

Mike

---

### Post by seren6ipity on 2008-12-01
:-)
You have a very valid point, not every one is online all the time. I think they are still finishing things up.

---

