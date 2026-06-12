---
title: "How can I use the shell script to real-time detect the print job form word processors"
date: 2019-02-10
forum: Programming Talk
---

### Post by starlitsky on 2019-02-10
I want to detect the print job that sends by the word processors (like LibreOffice, Openoffice), I know that use shell script to run the endless loop is a bad solution, so I want to know if there was any method to deal with this detection? 

I was stuck in this problem for weeks but still doesn't get any solution...


OS: virtual box Ubuntu 16.04, use CUPS


My English is not very well, but I will try my best to explain my question, hope somebody can reply to this question :)

---

### Post by TheFu on 2019-02-11
I have no idea how to make it work, but **inotify** would be where I started.  From the manpage:
```

NAME
       inotify - monitoring filesystem events

DESCRIPTION
       The  inotify API provides a mechanism for monitoring filesystem events.
       Inotify can be used to monitor individual files, or to monitor directo-
       ries.   When  a  directory is monitored, inotify will return events for
       the directory itself, and for files inside the directory.

```

---

### Post by starlitsky on 2019-02-12
Thank for your reply! I will search for more information about this solution to try its feasibility.

---

