---
title: "how to &quot;do something&quot; when my pygtk app starts but not in the __init__ method..."
date: 2008-02-17
forum: Programming Talk
---

### Post by Choad on 2008-02-17
i want my app to do some things when it starts up but they could be both cpu intensive and involve network lag... so how can i get it so that the gui comes up straight away and remains responsive? if i put it in the __init__ method than the window doesn't show till it's finished doing it's shiz

could this be a time to use threads?

---

### Post by CptPicard on 2008-02-17
Yep.. sounds like threading would be the way to go... launch your initialization stuff in a thread, then launch your GUI and join() the init thread, or use some more fine-grained method to recognize when the GUI is ready to actually do something with whatever you inited.

---

### Post by Choad on 2008-02-18
[http://ubuntuforums.org/showthread.php?p=4354960#post4354960](http://ubuntuforums.org/showthread.php?p=4354960#post4354960)

new thread

---

