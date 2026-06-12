---
title: "Constraint class in Python"
date: 2009-10-27
forum: Programming Talk
---

### Post by sprince09 on 2009-10-27
Hi guys,

I'm writing some code for a project which needs to use mathematical constraints such as -1 <= x <= 3, f(x) > 50, -inf < 50 <= 400, etc...

So far, I've written a small class in Python which can check whether a given input value is within a certain range, and returns True or False. It's usage looks like (basically):

```
>>>c1 = constraint(0, 500)
>>>print c1(300), c1(0), c1(500), c1(2000)
True True True False
```

This works great so long as I'm looking at a single 1 dimensional function (ie f(x)). My problem is that I'm most definitely not using a single one dimensional function, and so I need some way to keep track of which constraints belong to which variables. For example, I might have a function of 3 variables, f(x,y,z) where I need to have constraint equations on x, y, z, and/or f(x,y,z).

Basically, I'm looking for suggestions on how I could go about implementing this in a nice way. It seems cumbersome to attach a variable name to each constraint and also to each variable as a way to identify them to each other, so I'm assuming there's an elegant way to do this, and that I just don't see it. Maybe there's even a standard module that implements something like this?

---

### Post by Reiger on 2009-10-27
In JavaScript you can do something like this:

```

/* evaluate constraint objects with init(context), evaluate(), and get()  */
function checkAll(constraints) {
  // context property list
  var context {
    valid: true, // cumulative &#8216;validity&#8217; check
    constraints: constraints // enable constraints to access other constraints
  };
  var result= { }; //result property list
  for(var c in constraints) {
    constraints[c].init(context);
    constraints[c].evaluate();
    result[c] = constraints[c].get();
  }
  return result;
}

/* simple wrapper function returning a closure that calls realCheck as function() on evaluate(). */
function checkWrapper(realCheck) {
  return function() {
    this.context;
    this.valid // is the constraint met? 
    this.init= function(env) { this.context = env; this.valid = env.valid; };
    /* this implementation automatically fails if the previous constraint had set the context.valid field to false! */ 
    this.evaluate() { if(this.valid) { this.valid= realCheck(); this.context.valid = this.valid; } };
    this.get() { return this.valid; };
  }
}

```

Closures like that can be modeled using objects with appropriate init() and callback() methods.

Python can probably use dictionaries or something to model the property lists.

For an idea of how you can write automated tests for your constraints implementation:

```

/* construct a simple test constraint checking whether or not intVal == 22 */
function testCase(intVal) {
   return checkWrapper(function() { return intVal == 22; });
}

/* test the theory: run a couple of testCase() objects */
function run() {
   return checkAll({
     first: testCase(22), // should come out as valid
     second:testCase(55) // should come out as invalid
   });
}
/* test the result of run() against the expected values: */
function test() {
   var vals = run();
   return vals.first && ! vals.second;
}

```

---

### Post by diesch on 2009-10-27
Maybe like that:
```

class Function(object):
    def __call__(self, *args, **kwargs):
        raise NotImplementedError


class Times(Function):

    def __init__(self, n):
        self.n = n
        
    def __call__(self, x):
        return self.n*x
        

class ThreeDFunc(Function):
    def __call__(self, x,y,z):
        return x+y+z
        

class Constraint(object):
    def __init__(self, min, max, func):
        self.min = min
        self.max = max
        self.func = func
        

    def __call__(self, *args, **kwargs):
        return self.min < self.func(*args, **kwargs) < self.max
        
        
        
c1 = Constraint(1, 10, Times(2))
print c1(0), c1(3), c1(10)

c2 = Constraint(1, 10, ThreeDFunc())
print c2(1,2,3), c2(4,5,6), c2(8,9,0), 


```

---

### Post by sprince09 on 2009-10-27
Alright guys, here's what I came up with:

```
import math


################################################################################
# class: constraint
################################################################################

class Constraint(object):
    """fixme class documentation"""
    
    def __init__(self, min, max, varname, min_mode='inc', max_mode='inc', logic='or'):
        
        # cleanup input
        if(min_mode == 'inclusive'):
            min_mode = 'inc'
        elif(min_mode == 'exclusive'):
            min_mode = 'exc'
        
        if(max_mode == 'inclusive'):
            max_mode = 'inc'
        elif(max_mode == 'exclusive'):
            max_mode = 'exc'
        
        # make sure modes are good
        if((min_mode != 'inc') & (min_mode != 'exc')):
            raise ValueError('Invalid value of Constraint.min_mode')
        
        if((max_mode != 'inc') & (max_mode != 'exc')):
            raise ValueError('Invalid value of Constraint.max_mode')
        
        if((logic != 'and') & (logic != 'or')):
            raise ValueError('Constraint.logic must be \'and\' or \'or\'')
        
        # check that min < max
        if(min > max):
            raise ValueError('Constraint.min must be <= Constraint.max')
        
        # check that varname is not ''
        if(varname == ''):
            raise ValueError('Constraint.varname cannot be \'\'');
        
        self.min = min
        self.max = max
        self.min_mode = min_mode
        self.max_mode = max_mode
        self.varname = varname
        self.logic = logic
    
    
    def __call__(self, value):
        """Returns True if value is within the constraint, or False otherwise"""
        if(self.min_mode == 'inc'):
            if(self.max_mode == 'inc'):
                if((value <= self.max) & (value >= self.min)):
                    return True
                else:
                    return False
            elif((value < self.max) & (value >= self.min)):
                return True
            else:
                return False
            
        elif(self.max_mode == 'inc'):
            if((value <= self.max) & (value > self.min)):
                return True
            else:
                return False
        elif((value < self.max) & (value > self.min)):
            return True
        else:
            return False


################################################################################
# class: FitFunc
################################################################################

class FitFunc(object):
    """fixme class documentation"""
    
    def __init__(self, func, ivars, iconstraints, ovar=[], oconstraints=[]):
        
        # make sure input is ok
        # number of iconstraints must be greater than or equal to num of ivars
        # number of oconstraints must be greater than or equal to num of ovar
        if(len(ivars) > len(iconstraints)):
            raise ValueError('len(FitFunc.ivars) must be <=len(FitFunc.iconstraints)');
        elif(len(ovar) > len(oconstraints)):
            raise ValueError('len(FitFunc.ovar) must be <= len(FitFunc.oconstraints)');
        
        # assign values to class
        self.func = func
        self.ivars = ivars
        self.ovar = ovar
        self.iconstraintDict = {}
        self.oconstraintDict = {}
        
        # assign constraint, varname pairs to dictionary
        for varname in ivars:
            for constraint in iconstraints:
                if(constraint.varname == varname):
                    self.iconstraintDict[constraint] = varname
        for varname in ovar:
            for constraint in oconstraints:
                if(constraint.varname == varname):
                    self.oconstraintDict[constraint] = varname
    
    
    def __call__(self, values):
        """Returns FitFunc.func(values) if all constraints (anded) are True,
        otherwise returns float('nan').
        """
        
        # check input constraints
        c_check = 0
        for constraint in self.iconstraintDict:
            if(constraint.logic == 'and'):
                for i in range(len(self.ivars)):
                    if(self.ivars[i] == self.iconstraintDict[constraint]):
                        if(constraint(values[i]) == False):
                            return float('nan')
            else:
                for i in range(len(self.ivars)):
                    if(self.ivars[i] == self.iconstraintDict[constraint]):
                        if(constraint(values[i]) == True):
                            c_check += 1
        
        # if the 'or' logic is being used with the Constrain object, then 
        # c_check gets incremented once any time a Constraint object evaluates
        # to True for a given variable name. So, if c_check >= the number of
        # variable names in FitFunc, then the or operation was true.
        if(c_check < len(self.ivars)):
            return float('nan')
            
        
        # evaluate func
        output = self.func(values)
        
        # check output constraints
        for constraint in self.oconstraintDict:
            if(constraint(output) == False):
                return float('nan')
        
        # all good, return output from  function
        return output
        


## Run test code if this module is run as a script
if __name__ == "__main__":
    
    # dummy test function
    def f(x):
        """ Returns the value of the following function:
            
            f(xi) = sum(2*xi^2 + xi^2 * sin(xi))
            
        where xi is an n dimensional array of input values. This function has 
        exactly one global minimum at xi = 0, and is used to test the pso
        module.
        """
        
        out = 0
        for value in x:
            out += 2*value*value + value*value*math.sin(value)
        return out
    
    
    # run module test
    var1 = 'x1'
    var2 = 'x2'
    vars = [var1, var2]
    c1 = Constraint(0, 30.0, var1)
    c2 = Constraint(-30, -1, var1)
    c3 = Constraint(float('-inf'), 100, var2, max_mode='exclusive')
    constraints = [c1, c2, c3]
    
    ff = FitFunc(f, vars, constraints)
    print ff([-40, 10]), ff([-30, 100]), ff([-10, 50])
    #(prints: nan nan 4598.46497683 as expected)


```


That get's the logic down at least, now I need to do some optimization, documentation, etc... Thanks for the suggestions!

---

### Post by Can+~ on 2009-10-27
As someone mentioned before, a closure fits perfectly for this:

[PHP]def constraint_range(min, max):
	
	def closure(x):
		return x > min and x < max
	
	return closure

constraint1 = constraint_range(-5, 5)
constraint2 = constraint_range(-3, 8)

constraint3 = lambda x: constraint1(x) and constraint2(x)

print map(constraint3, [-7, -2, -1, 0, 1, 3, 5, 7, 15])[/PHP]

---

### Post by wmcbrine on 2009-10-28
> **Can+~ said:**
> x > min and x < maxDon't forget, Python allows this notation:
```
min < x < max
```
Although, "min" and "max" are built-ins, so I wouldn't use those names.

---

### Post by sprince09 on 2009-10-28
I'll take a look at closures, they seem pretty useful...

---

### Post by sprince09 on 2009-10-28
Alright, I've got a question: what's the advantage of using a closure instead of just using __call__? Doesn't __call__ achieve the same affect in this case?

---

