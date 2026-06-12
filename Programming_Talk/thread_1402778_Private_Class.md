---
title: "Private Class?"
date: 2010-02-09
forum: Programming Talk
---

### Post by djbushido on 2010-02-09
Can anyone think of a purpose for a private class? We were talking in my class and thought I would ask. I don't personally see a purpose, but didn't know if anybody else had an idea. Other than taking up code space and adding more lines.

---

### Post by nvteighen on 2010-02-09
> **djbushido said:**
> Can anyone think of a purpose for a private class? We were talking in my class and thought I would ask. I don't personally see a purpose, but didn't know if anybody else had an idea. Other than taking up code space and adding more lines.

What do you mean by "private class"? For me it's a class that cannot be used outside the module it's written... those are quite useful when you think you need some abstraction but you don't want it to be at your library's API.

Or is something else?

---

### Post by djbushido on 2010-02-09
Sorry, I meant the "private" keyword.
For instance, a protected class may be created, and then used by classes that inherit the base class. I didn't know if a "private class CLASS_WHATEVER" served any purpose in the coding world.

---

### Post by nvteighen on 2010-02-09
> **djbushido said:**
> Sorry, I meant the "private" keyword.
For instance, a protected class may be created, and then used by classes that inherit the base class. I didn't know if a "private class CLASS_WHATEVER" served any purpose in the coding world.

You mean "private inheritance"? Ah... well... it serves to make your class uninheritable (you create a wrapper class that privately inherits your "real" class)... kinda Java's "final" keyword...

But no, it's not actually *that* useful.

---

### Post by Some Penguin on 2010-02-09
> **djbushido said:**
> Can anyone think of a purpose for a private class? We were talking in my class and thought I would ask. I don't personally see a purpose, but didn't know if anybody else had an idea. Other than taking up code space and adding more lines.

 In Java?  You could use this to protect inner classes from access by possibly malicious subclasses of the parent if you didn't want to mark the parent 'final', perhaps.  It might be useful if you were writing a security-conscious SDK or the like.

---

### Post by azagaros on 2010-02-09
a private class?  I have to wonder which language I am talking about.

In libraries out there, there are classes which are not documented, more than likely they are helper classes which have no real purpose except to the library.  This just means which scope they are relative to and who has access to them.

I guess I never thought about a private class before but I can see instances when I don't want a class inheritable but those are rare and usually related to internal workings of a library I am putting together.

I hope this is food for though.

---

### Post by djbushido on 2010-02-09
On that note, I meant C++.
Also, I guess I was a bit off, but as I remember a "private" class wouldn't be allowed to be accessed. I.e., it would be totally invisible, and therefore useful only for taking up space. I could be wrong, I'm always learning! :)

---

