---
title: "[SOLVED] Python, urllib: Why does this hang?"
date: 2008-01-10
forum: Programming Talk
---

### Post by CptPicard on 2008-01-10
Could someone please try out the below from somewhere else and tell me if it gets stuck for some reason at httplib's _ssl.read? (*Yes, reading from SSL sockets seems to hang at the end of data for some reason, probably end of stream is not recognized or something... I chose to terminate reading at the html close tag and things work nicely...*)

I really don't understand what happened to this, I was happily making it multithreaded (at "process()") and it stopped working. The current version here has been returned to single-thread so it's not a threading issue. It fetches a couple of URLs and then just grinds to a halt. My own suspicion is that the server just chooses not to produce the response for me, but I'm a bit baffled by my ability to hit the same URLs by browser without trouble...

[php]
Snip, I don't think I'll leave my code here for Google.. ;)
[/php]

EDIT: Actually, it does not hang, but almost... it's awfully slow, while Firefox is completely snappy. Another question -- is urllib threadsafe? How about urllib2?

---

### Post by popch on 2008-01-10
I don't know if it has anything to do with your problem, buat what happened to '0', 'e' and 'f' in hexdigits?

[COLOR=#000000][COLOR=#0000BB]hexdigits [/COLOR][COLOR=#007700]= [[/COLOR][COLOR=#DD0000]'1'[/COLOR][COLOR=#007700],[/COLOR][COLOR=#DD0000]'2'[/COLOR][COLOR=#007700],[/COLOR][COLOR=#DD0000]'3'[/COLOR][COLOR=#007700],[/COLOR][COLOR=#DD0000]'4'[/COLOR][COLOR=#007700],[/COLOR][COLOR=#DD0000]'5'[/COLOR][COLOR=#007700],[/COLOR][COLOR=#DD0000]'6'[/COLOR][COLOR=#007700],[/COLOR][COLOR=#DD0000]'7'[/COLOR][COLOR=#007700],[/COLOR][COLOR=#DD0000]'8'[/COLOR][COLOR=#007700],[/COLOR][COLOR=#DD0000]'9'[/COLOR][COLOR=#007700],[/COLOR][COLOR=#DD0000]'a'[/COLOR][COLOR=#007700],[/COLOR][COLOR=#DD0000]'b'[/COLOR][COLOR=#007700],[/COLOR][COLOR=#DD0000]'c'[/COLOR][COLOR=#007700],[/COLOR][COLOR=#DD0000]'d'[/COLOR][COLOR=#007700]][/COLOR][/COLOR]

---

### Post by CptPicard on 2008-01-10
They are as they're supposed to be... they are not quite hexdigits, but close ;) If you format the URL wrong the server gives a very explicit error...

---

### Post by evymetal on 2008-01-11
Why are you using a lock "mutex" on those two lists? and what part of the code are you starting in a new thread?

I normally use thread rather than threading, but what I can see happening in process() is that the system has to wait for a lock, and release it, every time it gets a new item. This is only being called by one function in one thread, so this isn't needed. 

Then the next function (fetch) is being called in the same thread as the main function, so we have to wait for that before getting the locks for the other list.

---

### Post by CptPicard on 2008-01-11
The lock is there to protect the generator and the Set in the case of running in the multithreaded case, but as I said in the OP, this one has been returned into a singlethreaded case in order to examine the slowness of the http fetch in particular. Process() is dead code in the version presented.

I am mostly interested in whether I'm doing something wrong with urllib in a single thread in the first place (and as a follow-up, whether it's thread-safe).

Anyway, it seems like it might have something to do with using readlines() and it not knowing when to terminate -- something having to do with not knowing when at end of stream with SSL...

---

