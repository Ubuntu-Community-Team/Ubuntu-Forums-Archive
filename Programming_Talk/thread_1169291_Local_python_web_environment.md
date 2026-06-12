---
title: "Local python web environment"
date: 2009-05-25
forum: Programming Talk
---

### Post by Bios Element on 2009-05-25
I'm looking at learning python for web design. As I've been looking around it seems my best option would be to go with a python web framework such as pylons, django, web.py ETC however configuring them to work on a local server is proving to be very difficult.

Anyone happen to have any ideas on what I could do? I've tried both apache and lighttpd (Which I'm actually loving.) and have yet to get more then a standard .py helloworld script to work.

While some of the frameworks have a local dev server, when you "close" then with ctrl-C, part of the python process keeps going and ties up the port it was using and I have to go manually kill the process. Of course that isn't something that I want to do while I'm developing a website.

---

### Post by Bios Element on 2009-05-25
Well I still don't have a solution but I've found after I hit Ctrl-C it goes from "running" to "stopped". I still cannot start up the server on the same port until I try to kill it which turns it into a zombie process.

After that I can re-start the server.

---

### Post by soltanis on 2009-05-26
```

ps -e | grep [process name] | awk '{print $1}' | xargs kill -9

```

Welcome to Unix.

---

### Post by Bios Element on 2009-05-26
> **soltanis said:**
> ```

ps -e | grep [process name] | awk '{print $1}' | xargs kill -9

```

Welcome to Unix.

Hardly ideal but that's a heck of an easier solution then anything I've already came up with.

---

