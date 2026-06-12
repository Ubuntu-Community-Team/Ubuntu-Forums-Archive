---
title: "Increase precision of calculating very small numbers : numpy"
date: 2011-11-27
forum: Programming Talk
---

### Post by radiocognition on 2011-11-27
Hello UbuntuLand:

I am working on a piece of code for a scientific computing project.  For this particular computation, I need to calculate the scaling behavior of a measure between two matrices (i.e. calculate very small numbers ~10**(-20).  My code is attached below.

```

# A few libraries you might need
from numpy import cos, log
from numpy.linalg import eig


def fidelity(A, B):
    '''
    Calculates the fidelity between two unitaries.  Applys the method
    used in Multi-Qubit Compensation Sequences paper.
    '''
    # Use a Taylor series, might help avoid rounding
    # def NewCos(x):
    #     c = 1 - (x**2)/2 + (x**4) / (4*3*2)
    #     return c
    
    [q,Q] = eig(A.H * B)
    f = 1j* log(q)
    f = f - min(f)
    fidlty = min( cos( f/2.0 ) )
    return fidlty


def infidelity(A, B):
    '''
    Calculates the infidelity beween to unitaries.  Applies the method
    used in Multi-Qubit Comensation Sequences paper.
    '''
    return 1 - fidelity(A,B)

```

I will now describe in more detail what I am trying to do. Fidelity is a function that takes as its input two matrices (A,B) and returns a scalar.  Fidelity is bounded between 0 and 1, but in my case the fidelity is very, very close to 1.  I would like to calculate the infidelity (1 - fidelity(A,B)).  My problem is, at some point where A and B are very nearly identical, the fidelity function starts returning "1" instead of "0.999999999999 ... ", for two matrices that should not return a fidelity of "1".  This may seem like splitting hairs, but in my case, the problem is pretty serious.

I have attached a graph that used the previous code to calculate Infidelity.  The program breaks around ~ 10**(-15)
[IMG]http://ww2.chemistry.gatech.edu/~jmerrill3/scaling-plot.png[/IMG]

Any ideas on how to avoid this problem?  All entries in the matrices are type complex128.  I tried implementing a Taylor series for the cosine, thinking that it might be rounding happening in the numpy library, but it was not as helpful.  Is there some basic tenet of numerical programming that I have missed?

Any help would be greatly appreciated.

---

### Post by MadCow108 on 2011-11-27
my guess is the issue is not the cos but the subtraction
```
f = f - min(f)
```

subtractions of similar valued data should be avoided in numerical processing as it exibits loss of significance.
can it be avoided?

also complex128 are two 64 bit doubles so you only have 16 digits of precision per number anyway, you cannot improve beyond that.
you might have to resort to arbitrary precision libraries like mpmath or gmp.

---

### Post by radiocognition on 2011-11-27
> **MadCow108 said:**
> my guess is the issue is not the cos but the subtraction
```
f = f - min(f)
```

subtractions of similar valued data should be avoided in numerical processing as it exibits loss of significance.
can it be avoided?

also complex128 are two 64 bit doubles so you only have 16 digits of precision per number anyway, you cannot improve beyond that.
you might have to resort to arbitrary precision libraries like mpmath or gmp.

Thanks for your advice, there is a workaround for the subtraction.  I will first try that, and then move to mpmath or gmp.  If I fix the issue I will update this thread and mark it solved.

---

### Post by radiocognition on 2011-11-27
Thanks, the subtraction workaround is working great.  Now calculating down to around 1E-40.  Marking thread as solved.

---

