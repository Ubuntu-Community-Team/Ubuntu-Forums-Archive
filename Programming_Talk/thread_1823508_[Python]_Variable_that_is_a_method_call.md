---
title: "[Python] Variable that is a method call"
date: 2011-08-12
forum: Programming Talk
---

### Post by Frozen Forest on 2011-08-12
It's possible to store a call in variable then use this "call variable", or maybe there is something similar? Instead of having if..elif.else statements when the answer is known after the first test.

Pseudo code
[PHP]
operation = None
if var in 'read1':
    operation = read(True)
elif var in 'read2':
    operation = read(False)
else:
    operation = read(True) + Read(False)

while True:
    data = operation
    # use data
[/PHP]

---

### Post by cgroza on 2011-08-12
You can do this, if this is what you mean:

```


def Function(s):
    print s

my_func = Function
my_func("test")

```

---

### Post by smartbei on 2011-08-12
You can indeed do things like this. One way would be as cgroza posted, creating a function for each option and setting a temporary variable to the wanted one:
[php]
def option1():
    print '1'
def option2():
    print '2'

if flag:
    chosen_option = option1
else:
    chosen_option = option2

while True:
    data = chosen_option()
[/php]

Something that could make this more useful perhaps is defining the functions in place. This is especially true if there are many small options. To do this use the lambda keyword:

[php]
...
if flag:
    chosen_option = lambda: print '1'
else:
    chosen_option = lambda: print '2'
...
[/php]
You can read more about python and lambda here: [http://www.secnetix.de/olli/Python/lambda_functions.hawk](http://www.secnetix.de/olli/Python/lambda_functions.hawk)

---

