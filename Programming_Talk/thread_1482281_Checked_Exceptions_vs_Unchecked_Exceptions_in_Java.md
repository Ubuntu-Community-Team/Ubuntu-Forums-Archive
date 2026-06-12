---
title: "Checked Exceptions vs Unchecked Exceptions in Java"
date: 2010-05-13
forum: Programming Talk
---

### Post by s3a on 2010-05-13
I'm really confused as to what this all means. I'm sure it's something simple but I would REALLY appreciate it if someone could give me like a super short summary followed by an elaboration on the similarities and especially the differences. Please don't talk to me in an extremely sophisticated way.

Thanks in advance!

---

### Post by Queue29 on 2010-05-13
> **s3a said:**
> I'm really confused as to what this all means. I'm sure it's something simple but I would REALLY appreciate it if someone could give me like a super short summary followed by an elaboration on the similarities and especially the differences. Please don't talk to me in an extremely sophisticated way.

Thanks in advance!

Checked exceptions are exceptions that Java forces you to deal with. For example, opening/ reading from a file, you must either have the method throw IOException, or place the code in try/catch blocks.

An unchecked exception is one that Java does not force you to check, such ArrayIndexOutOfBoundsException. You don't need (and shouldn't to begin with) to check for this exception every time you write a for loop to write over an Array.

Rule of thumb: unchecked exceptions occur when there are logic errors with your program. Things that you as a programmer got wrong, and are able to fix in your own code (like dividing by zero, or going out of bounds on an array). Checked exceptions come up when there are things that can go wrong that you can't control, like opening a file that doesn't exist, or making a connection to a server that isn't responding, etc.

---

### Post by Some Penguin on 2010-05-13
I'll say that's *mostly* the case.

There are some oddities.  For instance, the Java compiler will happily let you create a TreeSet using a type that does not implement Comparable, without specifying a Comparator during construction.  e.g.

```

TreeSet<AtomicInteger> dontDoThis = new TreeSet<AtomicInteger>();

```

is legal, despite the fact that it is guaranteed to explode with a ClassCastException if you ever attempt to actually populate this with a plain AtomicInteger, because you didn't specify a comparator; you can't specify a comparator after construction; and AtomicInteger, unlike Integer, is not Comparable.  CCE is an unchecked exception, so the compiler will not force you to catch it or cover it via a Throws.

---

### Post by NovaAesa on 2010-05-13
> **Some Penguin said:**
> I'll say that's *mostly* the case.

There are some oddities.  For instance, the Java compiler will happily let you create a TreeSet using a type that does not implement Comparable, without specifying a Comparator during construction.  e.g.

```

TreeSet<AtomicInteger> dontDoThis = new TreeSet<AtomicInteger>();

```

is legal, despite the fact that it is guaranteed to explode with a ClassCastException if you ever attempt to actually populate this with a plain AtomicInteger, because you didn't specify a comparator; you can't specify a comparator after construction; and AtomicInteger, unlike Integer, is not Comparable.  CCE is an unchecked exception, so the compiler will not force you to catch it or cover it via a Throws.

I don't really see this as being inconsistent. After all, it's a logic error to try to try to put anything into a TreeSet without a comparitor if the E type doesn't implement Comparable. It's kinda like how the following code will compile fine but still throw an exception.

The Java compiler will also happily allow:
```

String s = null;
int l =	s.length();

```

EDIT: however, I do see that sort of thing (type safety gone wrong) as a flaw in the language... In this case it's stemming from the fact that there is both a Comparable version and a Comparitor version of TreeSet.

---

### Post by s3a on 2010-05-14
Thanks everyone! I particularly liked Queue29's explanation a lot. However, my teacher also wrote this:

"Checked exception are Exception and any of its subclasses,
excluding class RuntimeException and its subclasses.

Unchecked exceptions are RuntimeException and any of its subclasses."

can someone explain what this means please?

---

### Post by Some Penguin on 2010-05-14
The granddaddy of all Throwable bits is, well, Throwable.

Exception and Error are both subclasses of Throwable.
RuntimeException is a subclass of Exception.


RuntimeExceptions and Errors are unchecked; other Exceptions are checked.

---

### Post by soltanis on 2010-05-14
Your teacher basically said the same thing the other two posters above did; checked exceptions are those which you can anticipate as going wrong, such as files not opening or not existing, whereas unchecked exceptions could happen anywhere due to some general programming fault, probably in the programmer's logic.

---

### Post by s3a on 2010-05-15
Thanks everyone!

---

### Post by slavik on 2010-05-16
checked exceptions == probably fatal to core logic and can be "checked" (is file there? is socket open? etc.)
unchecked exceptions == could be fatal but cannot be predicted

---

