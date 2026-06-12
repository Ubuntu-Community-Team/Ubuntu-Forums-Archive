---
title: "Launch Bash Script IN TERMINAL through startup applications"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by jamesaepp on 2013-01-31
I have a red eclipse server.

It has a server.sh file with the 'chmod +x' applied.

If I add the file to startup applications, it loads the server, but in the background where I don't want it.

I want to be able to see the actual content of the shell as the server is running.

:confused::confused::confused:

Suggestions?

===================
Ubuntu 12.04 w/ all reps up-to-date

---

### Post by papibe on 2013-01-31
Hi jamesaepp.

I believe what you want is launching a terminal window that runs your script inside of it. Is that right?

Try this:
```
gnome-terminal -x /path/to/yourscript.sh
```
Change the for the proper terminal, and options if you are running other desktop different that Unity and Gnome.

Let us know how it goes.
Regards.

---

### Post by jamesaepp on 2013-01-31
> **papibe said:**
> Hi jamesaepp.

I believe what you want is launching a terminal window that runs your script inside of it. Is that right?

Try this:
```
gnome-terminal -x /path/to/yourscript.sh
```
Change the for the proper terminal, and options if you are running other desktop different that Unity and Gnome.

Let us know how it goes.
Regards.

Worked exactly as I wanted. Thanks.

---

