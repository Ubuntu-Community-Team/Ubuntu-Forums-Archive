---
title: "Viewing last lines of another xterm"
date: 2011-01-06
forum: Programming Talk
---

### Post by pzs on 2011-01-06
This is really a shell question, rather than programming, but this looked like the most appropriate place for it.

I run large processes from my machine at work and then come home to check on them. Usually, I use screen but sometimes I forget. Then the process is an hour in and I don't want to restart it.

When I get home, I can tell from the files generated whether it has worked or not, but if it has broken, I can't look at the error message. Is there a way to grab the last 20 or so lines of a specific xterm? I thought there might be a tty tool of some type. I don't need to interact with the xterm, just look at that error message.

Thanks,

Peter

---

### Post by worksofcraft on 2011-01-06
> **pzs said:**
> This is really a shell question, rather than programming, but this looked like the most appropriate place for it.

I run large processes from my machine at work and then come home to check on them. Usually, I use screen but sometimes I forget. Then the process is an hour in and I don't want to restart it.

When I get home, I can tell from the files generated whether it has worked or not, but if it has broken, I can't look at the error message. Is there a way to grab the last 20 or so lines of a specific xterm? I thought there might be a tty tool of some type. I don't need to interact with the xterm, just look at that error message.

Thanks,

Peter

No I don't think there is.
What you can do is pipe output and error streams to /tmp/build.log and then I run tail /tmp/build.log to get a running display of progress and errors.

p.s. oh actually I tell a lie, there are [hacker tools]("http://www.hackinglinuxexposed.com/articles/20040608.html") like xwd that let you view remote windows, but you would have to make your system very unsafe to be able to use it from home.

---

