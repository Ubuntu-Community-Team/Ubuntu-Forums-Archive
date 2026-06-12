---
title: "The case of the missing core dump."
date: 2007-03-08
forum: Programming Talk
---

### Post by 8086 on 2007-03-08
Whenever a program segfaults and says "Core dumped" it should leave a core dump somewhere, right? But as I was unable to find *any* core dump, what so ever, I thought it might be that ulimit was set to 0, but in Ubuntu it is set to Unlimited, in which case it shouldn't mean a thing. But where are the core dumps?

I used Slackware quite a while, and the core dumps were easily spotted in the working directory. Any ideas?

carl-erik

ps. I don't actually use them for anything. Just likes to know, that's all.
pps. Can one use these in GDB for debugging purposes?

---

### Post by Ragazzo on 2007-03-08
Did you use "ulimit -c unlimited" (with the -c option)? The core file should be in the directory where you run the malfunctioning program.

Edit: **man core** gives other common reasons why the core file isn't created. Also it's possible to disable core files in /etc/security/limits.conf (though it probably isn't edited).

---

