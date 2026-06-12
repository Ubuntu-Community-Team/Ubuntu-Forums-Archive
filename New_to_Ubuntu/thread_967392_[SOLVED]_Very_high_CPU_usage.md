---
title: "[SOLVED] Very high CPU usage"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by lavadisco on 2008-11-02
My machine is a Sager dual-core 2.4GHz intel CPU laptop w/2GB of RAM. I'm running Intrepid on it. When I start my computer, everything runs fine for a good while with typical CPU usage. Then, at some point that I have yet to be able to quantify, CPU on one of the cores shoots up to nearly 100% and about 15% on the other, as shown by the System Monitor. By then my processor fans are going like crazy. I then close every single program I have running, including System Monitor, and run top in a terminal. It tells me that two processes, "klog" and "dd" are using up all my CPU. What are these and why is this happening?

---

### Post by detroit/zero on 2008-11-02
It could be a problem with the system monitor itself. I've seen that problem reported around here and in other linux forums. I was experiencing it, too, so I remove the system monitor from my panel and started using conky.

Try removing the system monitor from your panel, and monitor you CPU usage with htop. Does the problem persist without the monitor in your panel?

---

### Post by lavadisco on 2008-11-02
You know, I think that worked. Problem seems to have gone away. Thanks!

---

### Post by emshains on 2008-11-02
Although I tend to use top,but when I sometimes use the system monitor, it usually shows that it eats 50% of my 1.6ghz sempron, even when I have no other app running in the background.




P.s. If you're problem is solved please mark the thread as solved.

---

### Post by lavadisco on 2008-11-02
Let me give it another day or so before I mark it solved. Just want to be sure. So far so good though...

---

