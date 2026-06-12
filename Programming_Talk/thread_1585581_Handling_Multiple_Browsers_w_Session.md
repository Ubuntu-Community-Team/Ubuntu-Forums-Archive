---
title: "Handling Multiple Browsers w/ Session"
date: 2010-09-30
forum: Programming Talk
---

### Post by era86 on 2010-09-30
Greetings!  I'm calling out to my web dev wizards.

I've got a web app that currently does product configuration (i.e. configuring a pizza) and stores the information of the configuration in the session.  This is all done via asynch javascript.  Now, I'd like to handle the case where multiple browser windows are open on the same page doing the same type of configuration.

For example:
browser1 is configuring a pepperoni pizza
browser2 is configuring a sausage pizza

Since each browser shares the same session, they mangle each other since they share the same config in the session.

I've googled around and found that passing an ID from each browser to modify the right config in the session might be the way to go for this.  I just wanted to see if anyone else had any magical solutions out there.  Also, if the user closes a window, doesn't that ID and config hang in the session?  Is there a way to send a call to the server if a window closes?  Via javascript perhaps?

I imagine the session would just store a key/value pair of IDs to configs.  But that's implementation details I wouldn't want to bore anyone with... ;)

Thanks in advanced!
:guitar:

---

### Post by ssam on 2010-10-01
i wish more web devs took this into account. trying to compare 2 train journeys on the nationalrail site always annoys me.

i am not sure of the solution, but maybe you could have some sort of subsession ID that you append to all the links/action on the each page that can be scaped out of the URL. if you see a user with a session ID but no subsession ID (the have opened a new window), then you can show them a list of the pizzas that they have in each subsession.

---

### Post by worseisworser on 2010-10-01
```

----------------------------------------------
|                 session-1                  |        
|                                            |
|   ------------------   ------------------  |
|   |   viewport-1   |   |   viewport-2   |  |
|   ------------------   ------------------  |
|                                            |
----------------------------------------------

```

Each *session* is designated by a cookie ID sent with each request, and each *viewport* is also designated by an ID sent with each request. So this is not very hard after all.

You deal with the lifetime of *viewport*s in pretty much the exact same way *session*s are dealt with; you set a timeout for when the *viewport* is to be "GCed". Trusting *onclose* events is way too risky; you will end up leaking memory, but you might consider depending on it as an optimization; to free memory earlier. Stuff like hash-tables with support for weakness is good, and a language/environment with support for GC features such as finalization etc. is also good.

The ID for the *viewport* is created in a <script> tag at the top of each page, then sent with the cookie/session ID for each request.

My SymbolicWeb project handles all this stuff (..and more..) transparently or as if "by magic"; [http://www.nostdal.org/](http://www.nostdal.org/) .. (under "public projects" at the top). I do not know whether there are other libraries or frameworks out there that do the same; perhaps someone else knows?

---

### Post by era86 on 2010-10-01
Hey thanks for the prompt replies.  I've decided to take the sub-session/viewport approach (or something similar).  When the customer goes to create a pizza, the function that sets the options (i.e. first topping) will check if an ID is passed.  If it is not, it creates a new config and passes the ID back.  It also sets a timestamp on it that is continually being checked to see if it should expire.

If the client passes down an ID, then it looks for the ID, modifies the config, and returns the same ID back.  If the ID doesn't exist in session, then it creates a new config and returns the ID.

I think this will handle the multiple browser issue on a single session.  I guess my only concern now is checking for zombie (expired) configs.  Do I do that on every action as well?  Should this be done more consistently (perhaps before every request to create a new pizza).  I guess it makes me uncomfortable to think that the zombie check is done on a customer action rather than consistently elsewhere.

Thanks again!

---

### Post by Some Penguin on 2010-10-01
TMTOWTDI.

Examples --
(1)  Accept input on page 1 of form, submit sends it to servlet which forwards it to a JSP that contains the next form -- carrying over values from previous page in hidden fields.  It's probably not an issue in your particular case, but the browser can be used to modify those fields (w/ appropriate plug-ins).    This reduces the amount of work required to store state because it's just being accumulated.

(2) Use the ID-based bit as you're suggesting (note:  IDs should be very non-contiguous and the allocator should of course be MT-safe, unless you enjoy the possibility of users seeing each other's data).  

One basic approach (again, from a Java perspective) would be to use the very nifty MapMaker class from the Google Collections library ([http://google-collections.googlecode.com/svn/trunk/javadoc/index.html?com/google/common/collect/MapMaker.html]("http://google-collections.googlecode.com/svn/trunk/javadoc/index.html?com/google/common/collect/MapMaker.html")) to create a map which

(a) associates your  generated request ids (Strings -- e.g. MD5 hash of a secret string + something based on the time) to a Map containing parameters
(b) has a reasonable concurrency level, and
(c) has an expiration date of, say, 45 minutes or some other value longer than you expect to need to need the mappings

(3) Use the same ID id, but instead base on how many sessions you want to keep at once, by extending LinkedHashMap (id -> data), setting whatever the desired capacity is, and overriding 'removeEldestEntry' to remove if and only if the map has reached that capacity.  LHMs are not guaranteed to be thread-safe, IIRC, so you'd want to do something like wrap it in Collections.synchronizedMap.  This will be less performant than the MapMaker approach, which is more along the lines of a proper ConcurrentHashMap.  

(4) Use the same ID approach, but store the data in a ConcurrentHashMap.   When an ID is created, add an ID / expiration date pair to a ConcurrentLinkedQueue.  One thread is created which periodically wakes up, peeks at the first item in the queue, and if it's expired, removes it from the CHM and the queue (and checks the next item).   You could also have it remove an item even if it is not expired because the CHM is getting huge -- in the case of a DOS attack, this trades one failure mode (system crash due to out-of-memory) for another (requests being invalidated early).

(5) Use the same ID approach, again store the data in  a CHM, and when an ID is created, submit a 'remove this key from map' task to a Timer or a ScheduledThreadPoolExecutor.

---

