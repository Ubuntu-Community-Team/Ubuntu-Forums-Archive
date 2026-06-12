---
title: "C++, best way to evaluate tree of boolean rules on floating point numbers?"
date: 2010-06-29
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-06-29
Sorry for the long post...**important parts are in bold**.

I am working on a project that involves collecting and analyzing lots of data.  For each test instance, I collect thousands of parameters in the form of floating point numbers and strings.  I would like to specify boolean conditions to run on each of these data instances and then count / log the number of passing / failing instances.  Each number is associated with a test name that I am currently storing in a map.  At the end of each test instance, I would like to iterate through my map and run the relevant boolean conditions (matched by test name) on the collected data.  So I am looking for:

1a) An easily modifiable way of specifying these boolean rules -- basically a database or collection of all the rules needed for each test instance.
1b) A way to evaluate these boolean rules.

2) Furthermore, is there a framework that would allow me to set boolean rules based on the result of other boolean rules?  This would require some way to specify dependency, evaluating the dependent rules first before evaluating the rules that depend on other boolean results.

One solution that I can think of would be a map and set of binary trees composed of boolean conditions.  Each boolean condition is stored in the map, the key is a 4 digit integer which is logged in our datalogs.  Then there is a set of trees.  Each node in the tree contains the 4 digit integer "result" that we log which matches a key in the previously mentioned map of boolean conditions.  Only the root of the tree is logged.  The binary branches of a given node are evaluated according to the operator stored in the parent node.  The leaves are boolean conditions that evaluate according to collected test data.  Individual boolean conditions are printed by storing a tree that only contains 1 node.  

**So based on this idea, a further refinement of what I am looking for is:**

1a) Something that allows me to store boolean conditions to be evaluated.
1b) Something that allows me to evaluate stored boolean conditions (boolean conditions composed of either numeric or string test parameters -- but I can stick to numeric only if that makes things easier).

[B]3) Something that allows me to easily describe set of trees composed of boolean conditions to evaluate. Requirement is that they are easily modifiable, XML might be a good solution for specifying the trees and boolean conditions -- don't want it to be hard-coded.
4) Using 1a and 1b, something that allows me to evaluate these trees.[/B]

Any ideas?

---

### Post by soltanis on 2010-06-29
Yeah, that sounds like a binary tree to me. I'm not sure whether XML is the best way to write that, though, it doesn't seem particularly optimized for this task.

Maybe you could do something like this?

```

Label: condition ? yes : no;

```

Where I'm obviously borrowing C syntax of the ternary operator, but basically, you have a label, a condition, and if it evaluates true, you evaluate the next condition labeled "yes" or if false, evaluate the condition labeled "no". For the logging part, you'd only need to specify the label and the outcome of the test, like

```

Label: true

```

Since it's only boolean conditions you seem to be evaluating, I'd think that simplifies things, no?

---

