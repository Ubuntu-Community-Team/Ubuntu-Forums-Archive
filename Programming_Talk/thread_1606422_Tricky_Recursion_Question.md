---
title: "Tricky Recursion Question"
date: 2010-10-26
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-10-26
Say that I want to parse a parenthesis-grouped string that looks like this:

(sin((4 + 5) * pi))

I want to represent this function in a parse tree such that '+' is an operator that will have two child nodes, 4 and 5.  '*' is an operator that will have 2 children, (4 + 5) and pi...and so on.  To do this, I'd like some function that can return "levels" of grouping parenthesis.  The best way to do this, I'm guessing, is probably by using a recursive function.  I was thinking that the function would be something like: 

String getGroup(int level)
{
    //returns parenthesis-grouped string at level
}

For example, getGroup(0) would return 4 + 5.  getGroup(1) would reuturn (4 + 5) * pi.  getGroup(2) would return sin((4 + 5) * pi).  I think I could hack something up using a recursive function and Java's Pattern and Match classes (trying to do this in Java), but was wondering if there's an easier implementation that relies on regular expressions.  Any one got a better idea?

---

### Post by Simian Man on 2010-10-26
Your getGroup function isn't a great way to solve this problem.  Look into [recursive descent]("http://en.wikipedia.org/wiki/Recursive_descent_parser").

---

### Post by mo.reina on 2010-10-27
implemented in python3.1

```
class Tree(object):
    
    def __init__(self, exp):
        self.exp = exp
        self.children = []
        self.operator = []
        import re
        # splits on first parentheses if present
        if re.search(r'(\(.*\))', self.exp):
            for child in [a for a in re.split(r'(\(.*\))', self.exp)]:
                #matches operator at beginning or end, extracts operator
                if re.search(r'^.?(\+|\-|\*|\\)', child) or re.search(r'(\+|\-|\*|\\).?$', child.rstrip()):
                    self.operator = str(re.search(r'((\+|\-|\*|\\))', child).group(0))
                    child = child.replace(self.operator, '').lstrip().rstrip()
                self.children.append(child)
        else:
            self.children = re.split(r'\+|\-|\*|\\', self.exp)
            self.operator = str(re.search(r'((\+|\-|\*|\\))', self.exp).group(0))
        #in case of shorthand notation like "sin(10 + 10)"
        if self.operator == []:
            self.operator = "*"

    def output(self, levels=0):
        # recurs depending on levels, 0 = 1st level evaluation, 1 = 2nd level evaluation, etc.
        if levels > 0:
            for child in self.children:
                if len(child) > 0:
                    #only equations wrapped in parentheses are used for recursion
                    if child.startswith("("):
                        Tree(child[1:-1]).output(levels - 1)
        else:
            for child in self.children:
                if len(child) > 0:
                    print('child: {}'.format(child))
            print('operator: {}'.format(self.operator))
```

usage:

```
>>> from functree import Tree
>>> equation = 'sin(5 + (10 * pi))'
>>> test = Tree(equation)
>>> test.output(0)
child: sin
child: (5 + (10 * pi))
operator: *
>>> test.output(1)
child: 5
child: (10 * pi)
operator: +
>>> test.output(2)
child: 10 
child:  pi
operator: *
>>> 

```

the code is a bit long because of all the parsing, otherwise the theory is quite simple, you have a class that accepts an equation, splits it, then sends the equation inside parentheses to another instance of the same class.

---

