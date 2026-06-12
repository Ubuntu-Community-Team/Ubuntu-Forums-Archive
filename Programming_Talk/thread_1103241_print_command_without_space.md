---
title: "print command without space"
date: 2009-03-22
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-03-22
I want to print a series of strings each without space to the stdout
using print command is it possible.

The situation i am considering is a two-dimensional array and is very complicated unlike the case below.
```

for i in range(5):
        print a[i],



```
 
This will print with space between the output

Is there any better way to print without space apart from writing the string into another list and then printing the joined list.

---

### Post by elCabron on 2009-03-22
One way is to join all array elements to one string before sending it to stdout:

```
print ''.join(a)
```

another method could be to use backspace characters to remove the previous spaces:

```
for i in range(5):
    print "\b" + a[i],
```

Possibly someone with more Python knowledge will have better solutions ;)

---

### Post by Can+~ on 2009-03-22
This might be one of the reasons why python3 changed print from a statement, to a function.

[PHP]for i in (3,4,5):
    print(i,end="")[/PHP]

I have a vague remember on how to do it on python <2.6.

And also, the pythonic way of transversing sequences, is:

[PHP]for element in a:
        print element,[/PHP]

---

### Post by 7raTEYdCql on 2009-03-22
I tried the above second code and i am not getting the desired result.

This is what i am getting:
I am getting the string followed by ambiguous characters.

---

### Post by Can+~ on 2009-03-22
> **i.mehrzad said:**
> I tried the above second code and i am not getting the desired result.

This is what i am getting:
I am getting the string followed by ambiguous characters.

No, actually, that wasn't the idea of the code, it was just a presentation on how to do stuff, usually, instead of using the range() element, transverse by the implicit iterator of python.

Could you share more of your code?

---

### Post by 7raTEYdCql on 2009-03-22
I was talking about "\b" operator.

---

### Post by 7raTEYdCql on 2009-03-22
I got the problem myself.

i used sys.stdout.write(a[j])

This prints without any spaces.

---

### Post by monkeyking on 2009-03-22
> **i.mehrzad said:**
> I want to print a series of strings each without space to the stdout
using print command is it possible.

The situation i am considering is a two-dimensional array and is very complicated unlike the case below.
```

for i in range(5):
        print a[i],



```
 
This will print with space between the output

Is there any better way to print without space apart from writing the string into another list and then printing the joined list.

Maybe you should also state which program language you are using.

good luck though

---

### Post by elCabron on 2009-03-23
> **i.mehrzad said:**
> I tried the above second code and i am not getting the desired result.

This is what i am getting:
I am getting the string followed by ambiguous characters.

This simple test:
```
a = [ "ab", "cd", "ef", "gh", "ij"]
for i in range(5):
    print "\b" + a[i],
```

gives me this output:
```
abcdefghij
```

But his might be different in your case, maybe it's an option to migrate to Python 3 ? :p

---

### Post by 7raTEYdCql on 2009-03-23
> **elCabron said:**
> This simple test:
```
a = [ "ab", "cd", "ef", "gh", "ij"]
for i in range(5):
    print "\b" + a[i],
```

gives me this output:
```
abcdefghij
```

But his might be different in your case, maybe it's an option to migrate to Python 3 ? :p

Dont know why but when i tried it in Idle on Windows it returned me some wierd characters between the variables. Nice one though. Thanks alot.

---

