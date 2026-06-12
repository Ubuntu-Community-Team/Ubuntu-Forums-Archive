---
title: "perl debugging (lucid)"
date: 2010-06-09
forum: Programming Talk
---

### Post by w2vy on 2010-06-09
I have a perl script that opens a pipe to another program (gnubg) and runs fine for a variable time.

Then I get the famed "Out of Memory!" error.

The problem is the perl is compiled with usemymalloc=N
so there is very little that I can do to find the cause.

While things run fine both perl and gnubg stay as a even memory usage.

I have ulimit set to 200mb and have raised the limit to 500mb and it still fails.

I believe some error is causing something to go wild and consume memory... the question is what!

I'd Love to get perl traceback!

I see perl-debug but I am not sure if this gives me what I need.

Any tips?

Tom

---

