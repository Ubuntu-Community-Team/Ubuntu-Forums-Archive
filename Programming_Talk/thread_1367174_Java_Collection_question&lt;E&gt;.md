---
title: "Java Collection question&lt;E&gt;"
date: 2009-12-29
forum: Programming Talk
---

### Post by hoboy on 2009-12-29
I have read this link 
[http://download.java.net/jdk7/docs/api/java/util/Collection.html](http://download.java.net/jdk7/docs/api/java/util/Collection.html)
in order to understand an example I have seen
in the example there is a this method,
public < T extends Response> void excute(Action<T>action)
from the link upward I have looked at 
addAll(Collection<? extends E> c)
but still I don't understand this <T extends Response>, 
is this mean what I suspect ?
 that T is a sub class of Response ?

---

### Post by Habbit on 2009-12-29
Indeed, the "extends Response" puts an upper bound on the type T: it must be a subtype of Response (note that this includes Response itself). The other type of constraint available reads "T super U", where T must be either U or a supertype (up to Object).

Note that if the T type itself is not required (most of the time), you can avoid the generic method and just use a wildcard like the Collection interface does: "public void execute(Action<? extends Response>action)".

---

### Post by hoboy on 2009-12-29
> **Habbit said:**
> Indeed, the "extends Response" puts an upper bound on the type T: it must be a subtype of Response (note that this includes Response itself). The other type of constraint available reads "T super U", where T must be either U or a supertype (up to Object).

Note that if the T type itself is not required (most of the time), you can avoid the generic method and just use a wildcard like the Collection interface does: "public void execute(Action<? extends Response>action)".

Thanks very much, that has clarified thinks

---

