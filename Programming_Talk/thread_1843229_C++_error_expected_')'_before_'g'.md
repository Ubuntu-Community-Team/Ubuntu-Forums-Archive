---
title: "C++ error: expected ')' before 'g'"
date: 2011-09-13
forum: Programming Talk
---

### Post by yoda2031 on 2011-09-13
The offending line:
"NeuralNet(Genome g)"

Context:
NeuralNet() is a constructor in the NeuralNet class, Genome is an abstract base class extended by RobotGenome (the class we later pass to NeuralNet in this particular program).

G++ seems to be implying that I can't actually -name- the Genome that is passed as an argument.  Obviously, removing the name introduces other errors and everything else I've tried simply doesn't work.

I am very new to C++ but come from a C background, am I doing something patently wrong?

---

### Post by PaulM1985 on 2011-09-13
Can you post all your code?

Does your NeuralNet class include the header for the Genome class?

Does your Genome class implement the assignment operator?  The assignment operator shows how to copy a class:

```

Genome a;
Genome b;
b = a; // <- Need to have assignment operator implemented for this to work

```

In your example, the constructor for the NeuralNet class takes "Genome g".  What this means is that when you create your NeuralNet, using something like:
```

Genome g1;
NeuralNet net(g1);

```

The "g1" passed in is copied so that it can be used in the constructor.  This is called "pass-by-value".  If you put an "&" sign infront of your "g", so the constructor is now NeuralNet(Genome &g), this is called pass by reference.  An actual reference to the object is now passed into the constructor.  This is called "pass-by-reference".  What do you intend your NeuralNet class to contain?  A copy of the genome passed in of a reference to the genome passed in?

Read about pass-by-reference and pass-by-value.

Paul

---

### Post by Senesence on 2011-09-13
"Genome g" would imply an instance of Genome, but you can't have instances of an abstract class ([http://www.cplusplus.com/doc/tutorial/polymorphism/](http://www.cplusplus.com/doc/tutorial/polymorphism/)).

Try "Genome* g" instead (obviously, you would be passing in via address then).

---

### Post by yoda2031 on 2011-09-13
> **PaulM1985 said:**
> Can you post all your code?

Does your NeuralNet class include the header for the Genome class?


It did not.  Thank you.  How often is it the embarrassingly obvious problems that you just can't solve?

---

