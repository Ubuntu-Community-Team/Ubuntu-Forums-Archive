---
title: "Common Lisp: your opinion"
date: 2015-05-14
forum: Programming Talk
---

### Post by veddox on 2015-05-14
Hello everyone,

here is a question for those of you who have some experience with Common Lisp: what do you think of it?

I started learning it about half a year ago, and have slightly mixed feelings. On the one hand, it is a beautiful language, more elegant than any other one I know, and incredibly powerful at the language level. On the other hand, it appears to lack real-world relevance: no inbuilt library, comparatively few third-party libraries, and precious few open-source projects using it.

Now, like I said, I'm still a newbie in the Lisp domain, so I might have missed stuff in my appraisal.

I'd love to use it more, because I really enjoy programming in CL. But when push comes to shove on a new project, I find it a lot easier to go with Python instead - it gives me the library to do whatever I need, and I can code at about four times the speed (although that's probably a matter of practice).

What is your experience?

---

### Post by tgalati4 on 2015-05-14
I used LISP and EMACs in college in 1983, so it has been around a while.  Yes, Python is modern and better suited for today's computing environment.  Still, there is something addictive about using LISP.

---

### Post by flaymond on 2015-05-21
Love the common lisp! The best for mathematical prototype analysis. I just go for Ruby, for me it's a modern Scheme + Clojure without many brackets of CL. The Python lambdas techniques may be familiar to CL users. :D

---

### Post by CptPicard on 2015-05-21
Most of the point of learning Lisp really is how it generally evolves your thinking processes about programming. It's such a great example of a nearly no-syntax language with exactly as much as is needed, but no more, of in-built language constructs as are needed to subsequently build pretty much anything.

> **InterProg said:**
> Love the common lisp! The best for mathematical prototype analysis. I just go for Ruby, for me it's a modern Scheme + Clojure **without many brackets** of CL. The Python lambdas techniques may be familiar to CL users. :D

You're missing about half of the point of a Lisp there. It is exactly the style of syntax that enables the macro system.

As for practicality I'd recommend Clojure over Common Lisp. The JVM and the available libraries are hard to beat.

---

### Post by flaymond on 2015-05-22
I just point my opinion, not to start a flame war about programming languages. Thanks.

---

### Post by veddox on 2015-05-22
Clojure sounds interesting - I have to take a closer look at that!

In the past two weeks I have been working on my first non-trivial Common Lisp project, and I found that even though I am still a lot slower than I would be with Python, that is offset by the fact that the resulting program is only about half the length, thanks to Lisps succinctness and macros. There are still a couple of issues I have not completely solved yet (I need networking and threading capabilities for my project), but I'll cross that bridge when I get to it...

---

### Post by CptPicard on 2015-05-23
> **InterProg said:**
> I just point my opinion, not to start a flame war about programming languages. Thanks.

It was not an attempt to start any flamewars; it's just that the brackets really are fundamental as to what Lisp is, they provide what is called [homoiconicity]("http://en.wikipedia.org/wiki/Homoiconicity").

---

### Post by cyberslayer on 2015-05-26
> **veddox said:**
> Hello everyone,

here is a question for those of you who have some experience with Common Lisp: what do you think of it?

I started learning it about half a year ago, and have slightly mixed feelings. On the one hand, it is a beautiful language, more elegant than any other one I know, and incredibly powerful at the language level. On the other hand, it appears to lack real-world relevance: no inbuilt library, comparatively few third-party libraries, and precious few open-source projects using it.

Now, like I said, I'm still a newbie in the Lisp domain, so I might have missed stuff in my appraisal.

I'd love to use it more, because I really enjoy programming in CL. But when push comes to shove on a new project, I find it a lot easier to go with Python instead - it gives me the library to do whatever I need, and I can code at about four times the speed (although that's probably a matter of practice).

What is your experience?

My opinion is the Common Lisp is a better langauge than Python, but Python has better libraries.  Usually, for smaller programs such as scripts, libraries are more important so I use Python for those.  Common Lisp is often superior for larger projects, especially if speed is more important (contrary to popular belief, you can write very fast code in Common Lisp).  Common Lisp does have a number of third party libraries through the quicklisp package manager.  You should be able to code in both quickly given enough practice.

---

