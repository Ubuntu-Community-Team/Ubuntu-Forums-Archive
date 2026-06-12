---
title: "[c][gtk] Communication between main thread and other threads"
date: 2012-09-06
forum: Programming Talk
---

### Post by mikazika on 2012-09-06
Hi,

I want to send a signal/message... to the main thread from some other thread. According to that signal main thread will choose which function to execute (creating window for example).

The first idea was to use gtk methods for creating a new signal, connecting and emitting it, but these methods request an instance to connect to...

Any idea will be helpful.

---

### Post by mikazika on 2012-09-06
I have found solution in the function g_idle_add. If someone need an  example, you could see it at  [http://www.gtkforums.com/viewtopic.php?f=3&t=54863&p=69869&hilit=main+thread#p69869](http://www.gtkforums.com/viewtopic.php?f=3&t=54863&p=69869&hilit=main+thread#p69869).

---

