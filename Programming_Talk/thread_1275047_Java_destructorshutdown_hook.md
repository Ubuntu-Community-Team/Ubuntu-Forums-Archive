---
title: "Java destructor/shutdown hook"
date: 2009-09-25
forum: Programming Talk
---

### Post by the_real_fourthdimension on 2009-09-25
Hey All

I'm building a system in java that makes use of a database implementation that works by serializing data structures to give the program persistent storage.  On system exit these objects are serialized to a file, and on system initialization they're rebuilt.  I would like to add some crash protection to this implementation so that the objects are also serialized to a file even when the program or jvm crashes.  How can I do this?  I've looked into using destructors, but they're only called when GC is run, and these objects will never be GC'd.  I haven't been able to find enough information about using Runtime.addShutdownHook to know if that will work in event of a crash or not.  Is that a good solution, or is there something else I haven't found yet?
Thanks.

---

### Post by johnl on 2009-09-25
Why not periodically serialize your objects to disk while running?  I am not a java expert, but I don't know if you can rely on running code in response to a 'crash'.

---

### Post by Alcareru on 2009-09-25
> **johnl said:**
> Why not periodically serialize your objects to disk while running?  I am not a java expert, but I don't know if you can rely on running code in response to a 'crash'.

I second that. And as far as I konw there is no such thing as a destructor in java. There is the infameous finalize()-method, which is called when the object is trashed, but before using that method you have to accnowledge that these methods are called in "random" order, at "random" times if at all. About the suhtdownhooks I don't know much. They might be usefull or they might not. If you use them take into consideration that they are only called at shutdown and not when object is trashed or goes out of scope.

P.S. Something about shutdownHooks:
[http://www.certpal.com/blogs/2009/08/java-shutdown-hooks/](http://www.certpal.com/blogs/2009/08/java-shutdown-hooks/)

---

### Post by froggyswamp on 2009-09-25
You are trying to win a war by waging a bad strategy at the expense of right tactics.
Serialization for serious stuff is bad as in "bad". Not only don't you get the safety of a modern enterprise-level database, but you can't even add/remove a single field to the persisted serialized stuff, not to mention other issues like JVM vendor & version.

---

### Post by the_real_fourthdimension on 2009-09-25
> **froggyswamp said:**
> You are trying to win a war by waging a bad strategy at the expense of right tactics.
Serialization for serious stuff is bad as in "bad". Not only don't you get the safety of a modern enterprise-level database, but you can't even add/remove a single field to the persisted serialized stuff, not to mention other issues like JVM vendor & version.

Yeah, that was my first thought.  However, I didn't write the requirements for this system, and the requirements state that I can't use any sort of external database, so serialization is my best remaining option.  But are you saying that objects recreated from other serialized objects are read only?

I want to stay away from finalize because GC is not going to run on these objects.  I was hoping to find something a little more global than a shutdown hook...  but maybe a shutdown hook with periodic serialization is the best option given this scenario.  Thanks for your help.

---

### Post by drubin on 2009-09-26
> **the_real_fourthdimension said:**
> Yeah, that was my first thought.  However, I didn't write the requirements for this system, and the requirements state that I can't use any sort of external database, so serialization is my best remaining option.  But are you saying that objects recreated from other serialized objects are read only?\

One word [Json]("http://json.org").

---

