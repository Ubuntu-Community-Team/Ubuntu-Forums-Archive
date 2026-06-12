---
title: "Linear Programming: Scheduler"
date: 2008-12-09
forum: Programming Talk
---

### Post by turezky on 2008-12-09
Note: Not actually a programming question... :)
Hi Everyone,
I've got a problem. I need to prepare a linear programming model (e.g Objective function and Constraints). The topic is bus scheduling. Actually it is some sort of bus which moves like a metro, so it's called "Metrobus" down here. Believe it or not, but the issue is similar to call center scheduling...

In any period of time (or just slot), a definite number of buses is required for passenger transportation. 
Each bus operates for definite (or variable e.g min and max hours) time period during the day. Of course, the shift (or hours bus operates without interruption) is at least twice smaller than the total number of slots.

I need to create a model which would schedule the buses operations for any day (assign the shift to the bus), given the amount of passengers (or sequentially the number of buses) required for each slot.

You can see the working example of what I need by following this link:
[http://www.math.vu.nl/~sapot/software/shift-scheduling/scheduler.php](http://www.math.vu.nl/~sapot/software/shift-scheduling/scheduler.php)
Note: it's done with the call-center in mind.

Thanks in advance!

---

### Post by hod139 on 2008-12-09
I'm not exactly sure what you are asking.  Are you looking for a language to model the problem in?  If so, the two popular modeling languages are [AMPL]("http://www.ampl.com/") and [GAMS]("http://www.gams.com/").  If you want to actually solve these problems, there are many solvers available online for free at [NEOS]("http://neos.mcs.anl.gov/neos/solvers/index.html").  Some solvers only accept AMPL files, other GAMS (a few both).

---

### Post by turezky on 2008-12-10
Actually language is not important.
I need to build these contstraints.
Like:
```

X1 + X2 >= Demand1
X3 + X4 >= Demand2
```
Something in that sort..

---

### Post by hod139 on 2008-12-10
I'm still not understanding what you are looking for.  Here is a solution for a simple linear program related to your post, written in AMPL.

**foo.mod:**
```

param Demand{1..2};
var X{1..4};

## Optimization function 
minimize Obj: sum {i in 1..4} X[i];

subject to

constraint1: X[1] + X[2] >= Demand[1];
constraint2: X[3] + X[4] >= Demand[2];

```**foo.data**
```

param Demand := 
   1 4  
   2 6;

```**foo.run**
```

solve;
display X;

```Submitting these three files to the MOSEK solver on NEOS returns:

```

processing commands.

4 variables, all linear
2 constraints, all linear; 4 nonzeros
1 linear objective; 4 nonzeros.


Return code - 0  [MSK_RES_OK]
MOSEK finished. (interior-point iterations - 0, primal simplex iterations - 0 dual simplex iterations - 0)
Problem status    : PRIMAL_AND_DUAL_FEASIBLE
Solution status   : OPTIMAL
Primal objective  : 10
Dual objective    : 10

X 
[*] :=
1  0
2  4
3  0
4  6

```;

---

