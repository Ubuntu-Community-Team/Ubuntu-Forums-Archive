---
title: "Best Way to Implement Boolean Logic Trees?"
date: 2009-12-03
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-12-03
Simple problem statement:

I have some number of boolean variables and 3 boolean connectives: AND, OR, and NOT.  The variables and connectives will be joined to form a boolean logic tree and we are interested in knowing the final result at the root based on some configuration of values for the leaves (the boolean variables).  Here's the hard part: I want to make a program in C++ such that someone else can easily configure the tree.  Bonus: It would be nice if I could break the tree up into smaller trees so that the intermediate evaluation results can be obtained as well.  So instead of one big tree, maybe I would like a forest of trees where the root of one tree could be the leaf of another.

More detail / background if needed / interested:

I need to program a tester for binning.  The test program is written in C++ and during testing, several boolean variables (counters) are populated with pass / fail based on testing results.  Ultimately, a bin between 0 and 100 is assigned which best summarizes (as good as a single number can) the results of the test.  The final bin is determined based on the counters set therefore, some counters are more important than others.  

Basically, I want to know the best way to implement boolean logic trees.  The leaves of the tree would be the counters and the branches or I guess places where the branches join the tree would be the boolean logic connectives (and, or, not, etc.).  So does anyone have any idea on the best way to do this?  Goal is to make it configurable.  If the counters and boolean conditions always stayed the same, I would just write one very long if-condition.  But the counters and conditions will change often enough that I want the boolean logic tree to be easily setup.  Since others will be doing the setup, I would also like something that is easy to explain to others how to use.  Any ideas / advice?

---

### Post by Arndt on 2009-12-03
> **SNYP40A1 said:**
> Simple problem statement:

I have some number of boolean variables and 3 boolean connectives: AND, OR, and NOT.  The variables and connectives will be joined to form a boolean logic tree and we are interested in knowing the final result at the root based on some configuration of values for the leaves (the boolean variables).  Here's the hard part: I want to make a program in C++ such that someone else can easily configure the tree.  Bonus: It would be nice if I could break the tree up into smaller trees so that the intermediate evaluation results can be obtained as well.  So instead of one big tree, maybe I would like a forest of trees where the root of one tree could be the leaf of another.



How will this configuration performed by others be done? Through a configuration file/GUI, or by writing code in C++?

Would a simple class with members for connective, left and right operand  (no right operand in the case of NOT) suffice? A member for the name of a leaf, and a print method, too. What more?

---

### Post by Can+~ on 2009-12-03
So you want to achieve something like a specific Parsing Tree? Doesn't sound all that hard, although, the difficult task would be how to feed it.

Now, an easy way to parse something like this, is with a Pre-fix notation:

```
if (a && (b || c))
```

```
(&& a (|| b c))
```

And in this moment, you realize why LISP is the way it is. Because the emphasis is not on the values, but in the task to do with them, so it becomes natural that this syntax itself creates a "tree" that specifies how the data in the leaves is parsed and transverses it upward until it reaches the root.

Does this answer the question? Probably not, but you may have an idea on what to look for now.

---

### Post by lisati on 2009-12-03
> **SNYP40A1 said:**
> 
I need to program a tester for binning.  The test program is written in C++ and during testing, several **boolean** variables (**counters**) are populated with pass / fail based on testing results.  Ultimately, a bin between 0 and 100 is assigned which best summarizes (as good as a single number can) the results of the test.  The final bin is determined based on the counters set therefore, some counters are more important than others.  


<aside>
:confused: Just a minor observation relating to semantics: I might be mistaken but aren't boolean values limited to two possible values, thus making them unsuitable for counting?

Having said that, I think I get what you're trying to do: evaluating a numeric variable in such a way that has a boolean result.

---

### Post by SNYP40A1 on 2009-12-03
Yes, it is a parse tree and I see the connection with LISP.  I would like it to be easily configurable so a GUI would be nice rather than C++ code.  I guess I would like to be able to do something like this:

A = B && C;
D = (H || E);
C = B && !D;
...

Where H, E, and B would be assigned values, the other variables would be calculated by the above equations.  Note that some equations depend on others so it would be nice if the order of evaluation could be inferred, but not necessary.  Is there any C++ software library for doing this?  Function Parser comes close:

[http://warp.povusers.org/FunctionParser/](http://warp.povusers.org/FunctionParser/)

Any advice on how to go about mapping the boolean variables or symbols to their actual values which change dynamically?

---

### Post by SNYP40A1 on 2009-12-03
> **lisati said:**
> <aside>
:confused: Just a minor observation relating to semantics: I might be mistaken but aren't boolean values limited to two possible values, thus making them unsuitable for counting?

Having said that, I think I get what you're trying to do: evaluating a numeric variable in such a way that has a boolean result.

I see the confusion.  By counter I mean a boolean variable with a numeric label.  So the label is the "counting" part, but the value is either true or false.  The word counter caused confusion.  But basically I have a bunch of symbols that take true/false values.  I want to find some way of describing a syntax tree in order to evaluate other variables.

---

