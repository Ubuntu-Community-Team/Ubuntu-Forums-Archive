---
title: "Mathematics problem"
date: 2011-04-14
forum: Programming Talk
---

### Post by erotavlas on 2011-04-14
Hi,
I have to solve a mathematics problem. I have to compute the optimal value of function of several variables. The function is maximized and/or minimized by nested variables x,y... For instance min(x) max(y) f(x,y). The order of evaluation of the nested min/max is important.
The function is known and the variables take a values from a known finite domain. I have thought a solution where I store a matrix of all possible values for x, y and the value of the function for every pair of values. After I can find the value of y for which the function is maximum, then I can find in the set of the remaining possible values for x, the value for which the function is minimized by x. This reasoning can be extended to a big number of nested variables.
My approach is not very efficient for a large number of variables...
Do you have a better idea than mine?

Thank you

---

### Post by Tony Flury on 2011-04-14
I would start with some analysis of the function - if it is algebraic - it might be possible to work out the relationship between x and y that give the highest value result.

> 
After I can find the value of y for which the function is maximum
 
using what value of x - for most functions if you chose a different value of x here you would find that a different value of y causes a maximum

> 
then I can find in the set of the remaining possible values for x, the value for which the function is minimized by x. 

Do you want the maximum or the minimum ?

> 
This reasoning can be extended to a big number of nested variables.


I am assuming you want to find the x,y pair that gives you the biggest result from your function, and you can't analyse the function to get a simple x to y relationship.
If so then all you will need is a neseted y loop and an x loop. You don't need to store every possible value, but you will need to loop through all the combinations - and keep a note of the largeset result found so far - and what x and Y values caused that value - you don't need to store any result smaller than the biggest you have already found 

Code : 
```

largestVal = -1000000000000
optx =0 
opty =0
for x from -1000 to 1000
   for y from -1000 to 1000
      val = func(x, y)
      if val > largestVal then
         largestVal = val
         optx = x
         opty = y 
     End if 
   Next y
Next x

```
This will find the first biggest value - if the function generates the same value highest more than once the above code wont find any of the subsequent maxima, but could be adapted to do so relatively easily.

---

### Post by erotavlas on 2011-04-14
Probably I have not explained well what I should do.
I have a function of several variables like f(x,y,z) = x+y+z (trivial example) and I want to find the value of the variables x,y,z for which the function assume the assume the optimal value. The operations of min/max are nested like min over x min over y max over z of f(x,y,z). The optimal value depends on the domain from which the variables x,y,z take the their values. The domain is known.

For example in trivial case where the domain for all variables is the same and it is composed of (0,1)
max over z f(x,y,z) = 3 (x = 1, y = 1, z = 1)
min over y f(x,y,1) = 1 (x = 0, y = 0, z = 1)
min over x f(x,0,1) = 1 (x = 0, y = 0, z = 1) 
The optimal value is 1 for x = 0, y = 0, z = 1.

I can use a sort of recursive method to evaluate a variable at a time. From the internal one to the external one.

Now, I hope I was more clear.

---

### Post by simeon87 on 2011-04-14
This is linear programming and there exist algorithms that solve these problems efficiently. I did this years ago but it involves matrices and related mathematics. Basically you're constructing an n-dimensional object and then you're walking along the boundaries to find the optimal values for each of the variables.

Search online for LP solvers and you can feed your problem as input to these programs. If you really need to implement the algorithm yourself then you should research this topic more and see what algorithms they use.

---

### Post by BkkBonanza on 2011-04-14
Assuming that you don't have an algebraic expression and cannot use differential calculus to solve for the max/min...

Then I guess you'd iterate over the domain you want and store the conditions when a max/min occurs. That is, you don't need to store all the intermediate values but only when a result exceeds a previous result, and the inputs that produce that.

eg. for values x,y,z you can set up nested loops to vary each, when a max occurs you store the x,y,z that produces it. After that you only update the max if a new set of x,y,z causes a higher max. 

Probably for more specifics you need to provide a more concrete example of the inputs and results you expect.

---

### Post by erotavlas on 2011-04-14
> **simeon87 said:**
> This is linear programming and there exist algorithms that solve these problems efficiently. I did this years ago but it involves matrices and related mathematics. Basically you're constructing an n-dimensional object and then you're walking along the boundaries to find the optimal values for each of the variables.

Search online for LP solvers and you can feed your problem as input to these programs. If you really need to implement the algorithm yourself then you should research this topic more and see what algorithms they use.

It is not a Linear Programming problem. A standard LP problem consists of an objective function plus a set of constraints. The objective function is maximized or minimized over all the variables. In my case I have to maximize or minimize over the single variables.

---

### Post by simeon87 on 2011-04-14
> **erotavlas said:**
> It is not a Linear Programming problem. A standard LP problem consists of an objective function plus a set of constraints. The objective function is maximized or minimized over all the variables. In my case I have to maximize or minimize over the single variables.

Yes, but you do have constraints and you can perform LP multiple times. For example, if you have min(x) max(y) f(x, y) then you can first perform max(y) f(x, y) and then later min(x) over the outcome of that. I'm not sure if I'm understanding your problem correctly though.

The constraints of your LP problem are the bounds of your domains, so for example x <= 200 and x >= -200 if x is bounded by those values.

Your problem may not be exactly LP but I think it's worth exploring if you could formulate your problem as such and then use an existing LP solver.

---

### Post by erotavlas on 2011-04-14
I'm thinking about a better solution where instead to store the matrix of all values of variables, I can represent the matrix as a search-tree.
At the root of the tree there is the most external variable while at the leaves there is the most internal variable.
I can start my search from the leaves (most internal variable) of the tree and for each node I can decide which variables is minimizing or maximizing the function. So I can continue up to the root of the tree.
This solution avoids the problem of storing the matrix for big problem.
I don't know if there are algorithms to search in a tree starting from the leaves.
Do those algorithms exist?

---

