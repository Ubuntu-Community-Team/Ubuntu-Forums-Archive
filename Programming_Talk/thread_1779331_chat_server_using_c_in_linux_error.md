---
title: "chat server using c in linux error"
date: 2011-06-10
forum: Programming Talk
---

### Post by kapil1503 on 2011-06-10
hello everyone,
i am new to linux and networking. i am trying to make a chat server using socket programming but the problem is only one way chat occurs. could anyone please help me in knowing in where i am going wrong.
thanks in advance.

---

### Post by gmargo on 2011-06-10
Well, you're making a good start.  Here's a couple of recommendations to help you get further:


[LIST=1]
[*]server: third argument to accept(2) is incorrect; should be a pointer to socklen_t.  This is preventing the server from accepting the connection.  Be sure to check the return value from accept(2).  Also be sure to use the "-Wall" argument to the compiler, and pay close attention to all warnings.
[*]server: discards first character from client.  Intentional?  Also be sure to check return value from every read(2) and write(2) call.
[*]client: "arr" array needs a declared size or else you'll overwrite stack memory.
[*]client: write(2) calls are writing the "length" integer instead of the "arr" buffer.  Same with read(2) calls.
[/LIST]

---

