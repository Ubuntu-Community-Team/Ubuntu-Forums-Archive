---
title: "Python 2.x vs. 3.x"
date: 2010-02-04
forum: Programming Talk
---

### Post by Wink2tall on 2010-02-04
Should I start by learning 2.x first and then moving on and will it be important to learning 3.x or is it okay to just skip 2.x and dive right into 3.x? 

Thanks!
-Wink

---

### Post by Grenage on 2010-02-04
I would (and am) learning with Python 3; I don't see the point in learning an older version, one can always cover deprecated features if required.

---

### Post by raydeen on 2010-02-04
I had started with 2.x but have recently moved to 3.x. 3 has a lot more features and a better syntax in some cases. It can't hurt to get a reference guide of the differences between 2 and 3 just in case you need to work with some older code. The differences aren't terribly dramatic. Actually most recent books (even back to '06) will reference both versions when displaying code examples.

2.x: print 'Hello World'

3.x: print ('Hello World') # print is a function in 3.x instead of a statement

There are some more in-depth changes to the language but I've found going back and forth between 2 and 3 isn't too difficult (at least not at my n00b level).

---

### Post by nvteighen on 2010-02-04
The issue is that Python 3.x is still lacking libraries widely used; that's a major obstacle towards adoption. Moreover, you have to think that Debian one of the major GNU/Linux distribution is just making its transition from 2.5 to 2.6 (in the testing and unstable branches) because of stability concerns. Like it or not, a lot of people need/want to have their projects to run on Debian flawlessly.

Currently, to make anything moderately useful, you are forced to use 2.x or to use 3.x and reimplement a lot of stuff. (e.g. I'm not sure of the state of PyGtk for Python 3)

In the end, as always, the market rules... and that's why 2.x will still be there for a while.

---

### Post by Wink2tall on 2010-02-05
Well thank you all for you information. I think I will go with 2.x and then just work my way up to 3.x, that way I can use either one depending on what the application\program is for.:)

---

