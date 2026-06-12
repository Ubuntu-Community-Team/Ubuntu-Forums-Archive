---
title: "Help saving data as ascii in scientific python"
date: 2009-01-19
forum: Programming Talk
---

### Post by Glenn Jones on 2009-01-19
Hi guys,

Sorry if this is a quation which is asked all the time but here goes. 

I have recently moved from matlab to use scientific python, specifically numpy, scipy and pylab. I am however having difficulties in trying to save some data in ascii format. The data looks like:

# header1
# header2 
# header 3
# header 4
x(1)    y(1)    z(1)
x(2)    y(2)    z(3)
 .       .       .
 .       .       .
 .       .       .
x(N)    y(N)    z(N)

The headers are all strings whilst x,y,z are a numpy array N,3 in size called XYZ.

I have tried the write command and the prickle to no avail. If anyone could help me out that would be much appreciated.

Cheers

---

### Post by jpkotta on 2009-01-20
I'm not all that familiar with Python and NumPy, but NumPy is just a module for Python right?  So you use Python to print out the array.
```

a = arange(15).reshape(5,3)
f = file("foo", 'a')

for i in range(a.shape[0]):
    s = ""
    for j in range(a.shape[1]):
        s += "%f\t" % a[i,j]
    f.write( s + "\n" )

f.close()

```

Can I ask why you're moving from Matlab?  I've been using Octave quite a bit, and I can see both advantages and disadvantages to switching to NumPy.

---

### Post by Glenn Jones on 2009-01-20
Thanks.

I guess I have a few different reasons for changing from matlab:

The availability of the matlab licences at the University. You would be waiting for an age to start work. 

I'm not happy with the quality of the matlab figures. Some come out great but the majority of my plots looked rather amateurish. Scientific python seemed like a logical move.

Finally I was keen to learn a new programming/scripting language and this gave me the excuse to do so.

Thanks again for the reply.

---

