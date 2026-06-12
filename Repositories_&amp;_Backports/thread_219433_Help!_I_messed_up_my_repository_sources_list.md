---
title: "Help! I messed up my repository sources list"
date: 2006-07-20
forum: Repositories &amp; Backports
---

### Post by pinkfloyd65 on 2006-07-20
I was trying to update Totem with codecs so it can play avi files and saw this advice on a forum. It advised to add some lines into the repository list (via the Custom button). I may have screwed up something, becuase now if I go to the Synaptic Manager I get this error message:

"E: Malformed line 40 in source list /etc/apt/sources.list (dist parse)"

I can't download any updates and basically Synaptic is not working. 

How can I revert to my initial repository sources list or how can I repair this one?

I am running 6.06 Dapper Drake.

Any input is appreciated.

---

### Post by aysiu on 2006-07-20
If you want to repair it, post here the output of this command, so we can see what's malformed on line 40: ```
cat /etc/apt/sources.list
``` Otherwise, get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Titus A Duxass on 2006-07-20
Sudo pico /etc/apt/sources.list

Scroll down to line 40 (press Ctrl+C and it will tell you which line you are on), have a look and see what looks wrong.

If you cannot see anything, try hashing it out.

---

### Post by pinkfloyd65 on 2006-07-21
Sorry for the delay (had some connectivity issue and couldn't go online)

I was about to post the contents of the sources.list file (as you requested, **aysiu**), but then I went to the URL you mentioned, followed the instructions and....Voila! My repository sources list is back up!
Thank you!

BTW, thanks for the tip, **Titus A Duxass**: "press Ctrl+C and it will tell you which line you are on"....As a new Linux user, every such tip is extremely helpful. Thank you!

---

