---
title: "delete specific columns in 2d numpy array"
date: 2012-04-25
forum: Programming Talk
---

### Post by abraxas334 on 2012-04-25
i have a [4x10] numpy array.
I want to remove all columns where just one negative number can be found

So my orriginal array may look like this:
[HTML]
>>>np_states
array([[ -3.00000000e-01,   9.79046844e-06,   1.47256220e-01,
          1.72133291e-02,   1.02045857e-02,   1.28577429e-01,
          3.64340296e-02,   9.19883478e-02,   4.72512761e-01,
          2.92455461e-02],
       [  6.02805796e-07,   4.99891856e-05,   4.48680965e-01,
          6.87139172e-01,   7.73983848e-01,   1.47036533e-01,
          6.66368384e-01,   5.97163549e-01,   2.81824566e-01,
          7.04446005e-01],
       [  9.99999166e-01,   9.99904115e-01,   3.49703181e-01,
          1.96402961e-01,   1.66155685e-01,   9.52311133e-02,
          9.32325746e-02,   1.39345379e-01,   1.62651543e-01,
          2.47597672e-01],
       [  7.97715696e-08,   3.61049370e-05,   5.43596347e-02,
          9.92445381e-02,   4.96558810e-02,   6.29154924e-01,
          2.03965012e-01,   1.71502725e-01,   8.30111304e-02,
          1.87107764e-02]])



[/HTML]

then array.sign looks like this:
[HTML]
array([[-1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.],
       [ 1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.],
       [ 1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.],
       [ 1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.]])


[/HTML]

then i  want to do something like this:
[HTML]
array = np.delete(np_states, 0,1)
[/HTML]
so the first column with the negative entry is deleted. Now i have a bunch of these arrays with various amounts of negative sgins, how can I return the column indices for which I need to delete the columns?

Thanks!

---

