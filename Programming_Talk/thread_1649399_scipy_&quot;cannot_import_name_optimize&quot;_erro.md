---
title: "scipy &quot;cannot import name optimize&quot; error"
date: 2010-12-20
forum: Programming Talk
---

### Post by Cenko on 2010-12-20
Hi,

I installed scipy and numpy from source to my ubuntu 10.04.

I have a weird error.

When I run python interpreter I can simply do without error:

```
from scipy import optimize
```

I have a sample fitting program called sinusfit, which imports optimize. Here is the program:

```

from numpy import arange, sin, random, array, pi

x = arange(0,6e-2,6e-2/100)
A,k,theta = 10, 1.0/3e-2, pi/6
y_true = A*sin(2*pi*k*x+theta)
y_meas = y_true + 2*random.randn(len(x))
 
def residuals(p, y, x):
        A,k,theta = p
        err = y-A*sin(2*pi*k*x+theta)
        return err
        
def peval(x, p):
        return p[0]*sin(2*pi*p[1]*x+p[2])
        
p0 = [8, 1/2.3e-2, pi/3]
print array(p0)
 
from scipy import optimize
 
plsq = optimize.leastsq(residuals, p0, args=(y_meas, x))
 
print plsq[0]
print array([A, k, theta])
 
import matplotlib.pyplot as plt
plt.plot(x,peval(x,plsq[0]),x,y_meas,'o',x,y_true)
plt.title('Least-squares fit to noisy data')
plt.legend(['Fit', 'Noisy', 'True'])
plt.show()
```

When I write this code line by line in ipython, it runs without problem.
When I run it by

```
./sinusfit.py
```

or

```
python sinusfit.py
```

it gives error:

```
ImportError: cannot import name optimize
```

More weird, after this error when I run python and try to import optimize I get the same error. Error is gone when I close and open a new terminal.

Is there a simple thing i'm missing?

---

### Post by Cenko on 2011-09-06
Wow, it was the stupidest possible reason. In the directory I was working, I made a trial file called scipy. So when I import scipy, it was loading the contents of the file, and ofcourse not finding optimize...

---

### Post by Pynalysis on 2011-10-11
Thanks for sharing the resolution to this problem.

---

