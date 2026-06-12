---
title: "Python and vectorize"
date: 2010-05-26
forum: Programming Talk
---

### Post by C++buntu on 2010-05-26
Hi everyone,

I have a little question about vectorizing strategies in Python.

If, for example, I want to vectorize the following simple Python function:

```

def F2Cv(F):
    if isinstance(F, (int, float)):
        if F < -459.67:
            raise ValueError('%gF is a non-physical value' % F)
        else:
            value = (5./9)*(F - 32)
    elif isinstance(F, ndarray):
        value = where(F < -459.67, None, (5./9)*(F - 32))
    else:
        raise TypeError('F must be int, float or array, not %s' % type(F))
    return value

```

The problem with this implementation is that I cannot use it for plotting purpose because of the None...

What is the better strategy here? I want that my function check for possible bad input (i.e. F < -459.67) and works for array type...

Thanks for the advice

---

### Post by lavinog on 2010-05-26
Why not do a check for none in the array and raise an error.

---

### Post by C++buntu on 2010-05-26
> **lavinog said:**
> Why not do a check for none in the array and raise an error.

It's my first guess, but for some reasons, I think it's not optimal. I want to use the result of this function directly to plot...but if i need to check for the None, it's none optimal ;)

---

### Post by lavinog on 2010-05-26
BTW: calculating 5./9 everytime is not optimal.

You can do a test for the minimum value:
```

const5div9 = 5. / 9

if F.min() >= -459.67:
    value = ( F - 32 ) * const5div9
else:
    raise ValueError('%gF is a non-physical value' % F.min())

```

---

### Post by C++buntu on 2010-05-26
> **lavinog said:**
> BTW: calculating 5./9 everytime is not optimal.

You can do a test for the minimum value:
```

const5div9 = 5. / 9

if F.min() >= -459.67:
    value = ( F - 32 ) * const5div9
else:
    raise ValueError('%gF is a non-physical value' % F.min())

```

Ah, good one! I will remember this.

---

### Post by soltanis on 2010-05-26
Unless Python is totally alien to the concept of optimization it will automatically do that for you. Then again Python has done some pretty stupid things in the past (see: Global Interpreter Lock) so I wouldn't give it too much credit, but looks like premature optimization to me.

---

### Post by StephenF on 2010-05-26
Why are you sanitizing your inputs here?

---

