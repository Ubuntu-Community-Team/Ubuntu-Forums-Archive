---
title: "Is there any difference in For loop and While loop in C  ?"
date: 2012-05-27
forum: Programming Talk
---

### Post by prismctg on 2012-05-27
Actually i dont find any difference in for and while loop in C ... as i m python background people !! If i m not wrong ; we can do same task using for or while loop in C .. So my question is , Is there any difference in these for and while loops ?

---

### Post by Bachstelze on 2012-05-27
You can do the same task with a for and a while loop in virtually every language (including Python). Which one to use is mostly a matter of style and code readability. In general you use a for loop when you know in advance how many iterations will be needed, and a while loop when you don't.

---

### Post by lisati on 2012-05-27
Each style of coding a loop has its merits. Sometimes a "for" loop results in tidier code than a "while" loop, and sometimes the reverse is true.

---

### Post by r-senior on 2012-05-27
In this sense a C for loop and while loop are equivalent:

```
int [COLOR="Red"]i = 0[/COLOR];
while ([COLOR="SeaGreen"]i < 10[/COLOR]) {
    puts("Hello");
    [COLOR="Blue"]i++[/COLOR];
}

```

```

int i;
for ([COLOR="Red"]i = 0[/COLOR]; [COLOR="SeaGreen"]i < 10[/COLOR]; [COLOR="Blue"]i++[/COLOR]) {
    puts("Hello");
}

```

C does not have an equivalent of Python's for loop (also found in Objective-C, Java and others), which iterates over an iterable -- like a list, a tuple or generator:

```

with open filename as f:
    [COLOR="Red"]for line in f[/COLOR]:
        print line

```

I think this might be what you are thinking of. Python's while loop is the same idea as C but the for loops are different. The C style for loop is simulated in Python by using a range function to generate an iterable:

```

for i in xrange(10):
    print 'Hello'

```

---

### Post by roelforg on 2012-05-27
> **r-senior said:**
> In this sense a C for loop and while loop are equivalent:

```
int [COLOR=Red]i = 0[/COLOR];
while ([COLOR=SeaGreen]i < 10[/COLOR]) {
    puts("Hello");
    [COLOR=Blue]i++[/COLOR];
}

``````

int i;
for ([COLOR=Red]i = 0[/COLOR]; [COLOR=SeaGreen]i < 10[/COLOR]; [COLOR=Blue]i++[/COLOR]) {
    puts("Hello");
}

```C does not have an equivalent of Python's for loop (also found in Objective-C, Java and others), which iterates over an iterable -- like a list, a tuple or generator:

```

with open filename as f:
    [COLOR=Red]for line in f[/COLOR]:
        print line

```I think this might be what you are thinking of. Python's while loop is the same idea as C but the for loops are different. The C style for loop is simulated in Python by using a range function to generate an iterable:

```

for i in xrange(10):
    print 'Hello'

```

C++ does have those loops:
They're called for-range-loops.
This is how:
```

int some_array[]={1,2,3,4,5,6,7,8,4,6,3,6,32,5};
for (int item : some_array)
 cout << item << endl;

```

---

### Post by Barrucadu on 2012-05-27
C and C++ are different languages; C does not have a for loop like that.

---

### Post by roelforg on 2012-05-27
> **Barrucadu said:**
> C and C++ are different languages; C does not have a for loop like that.

I didn't say it did, but since r-senior started mentioning what languages have them, i figured i'd pitch in.

---

### Post by prismctg on 2012-05-27
Thank you everyone ; specially R-senior

---

