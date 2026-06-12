---
title: "Counting signal occurrences"
date: 2010-01-22
forum: Programming Talk
---

### Post by Henrik B on 2010-01-22
The application I'm developing is using up to 100% of the CPU time.
I ran Valgrind which told me that almost all the time was spent in the EventLoop of Qt.
So all I have to do now is to find out which event it is that keeps occurring.
Therefore I would like a tool which can count all events sent from Linux to my application and write a nice table with the occurrence count for each event.
Does anybody know if such a tool exists or is there an easy way to write a function which can sniff the events?

---

