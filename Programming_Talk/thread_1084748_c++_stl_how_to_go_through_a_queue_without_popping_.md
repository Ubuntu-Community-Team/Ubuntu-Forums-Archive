---
title: "c++ stl: how to go through a queue without popping elements"
date: 2009-03-02
forum: Programming Talk
---

### Post by cybo on 2009-03-02
i have just started looking into an stl in c++

i have queue and need to go through it without popping elements from it, just like you would go through an array

```
for (i = 0; i < len; i++)
  queue[i]
```

is there a way to do it with stl?

---

### Post by johnl on 2009-03-02
Hi,  

Check out this page: [http://www.sgi.com/tech/stl/queue.html](http://www.sgi.com/tech/stl/queue.html)

> 
A queue is an adaptor that provides a restricted subset of Container functionality A queue is a "first in first out" (FIFO) data structure. [1] That is, elements are added to the back of the queue and may be removed from the front; Q.front() is the element that was added to the queue least recently. **Queue does not allow iteration through its elements.** [2]


Footnote #2 gives more information why that is.

Hope this helps!

---

### Post by tneva82 on 2009-03-02
Maybe some other container would be more suitable? I use vector or list if I expect to remove elements from middle of container where list is(as far as I know) more efficient than vector.

Probably one of those two would fit more like what you want to do.

So somehow like this:

vector<int> myVector;

for(int i=0;i<10;i++) {
myVector.push_back(i);
}

for(int i=0;i<myVector.size();i++) {
myVector[i];
}

---

### Post by cybo on 2009-03-04
thank you everyone.

---

### Post by Crimsonblah on 2009-03-04
Another great how-to site for the STL is this one:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialC++STL.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialC++STL.html)

I've found it especially useful on how to initialize 2D or 3D vectors, since the error messages given by the compiler are not very user friendly.

---

