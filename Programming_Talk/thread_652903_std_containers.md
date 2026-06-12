---
title: "std containers"
date: 2007-12-29
forum: Programming Talk
---

### Post by joebanana on 2007-12-29
I have a std::priority_queue container. How do I decrease one of it's elements priority? I know that its using vector for strorage. Should I get the element from priority_queue delete it from priority_queue decrease its key and readd it? Is this the right way. How can I access this element. Pls help.

---

### Post by thk on 2007-12-29
I think the answer is that you are using the wrong data structure.

If you really want to do this, you will have to remove the element and re-add it into the queue. The storage elements are arranged as a heap so you cannot simply move them to any position.

---

### Post by joebanana on 2007-12-29
I am implementing dijkstra. I have the java code and it's using priority_queue and there is a line q.decrease_key(w, value). Where q is priority_queue, w is object that is stored in q and value is the new value of priority.

---

### Post by amo-ej1 on 2007-12-29
I think you're stuck on some ugly java code then. If you look at the prototype of the Java priority queue (see [http://java.sun.com/j2se/1.5.0/docs/api/java/util/PriorityQueue.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/PriorityQueue.html) ) you will also notice there is no member function to lower the priority.

How is that decrease_key implemented ?

---

