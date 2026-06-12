---
title: "NetBeans Problem?"
date: 2008-09-08
forum: Programming Talk
---

### Post by Pergi on 2008-09-08
Hello, i am learning Java and i want to ask something.
At NetBeans i am trying to solve a problem from the book that i am reading and when i am writing

```
byte iVar=1;
iVar=iVar*2;
```

NetBeans shows an exclamation mark that says "Possible loss of precision"
But when i write

```
byte iVar=1;
iVar*=2;
```

It is ok for NetBeans.

The question is: "iVar=iVar*2;" and "iVar*=2;" is the same thing, right?
So why NetBeans give wrong for the first one and not and for the second?

I know that i am newbie, before some days i started to learning Java :)

Thanks for reading.

---

### Post by leg on 2008-09-08
This is more related to the variables type than anything else. The default type for an integral number is an int. The warning is generated with the first one as the result of ivar*2 will be an int. Not sure why it doesn't happen for the second one but I will bet that this is the basis of whats occurring.

---

### Post by tinny on 2008-09-08
leg is right.

A byte in Java can have the following range -128 to 127 (inclusive).

An int in Java can have the following range -2,147,483,648 to 2,147,483,647.

So as you can see you need to be careful when dealing with both int's and bytes.

The first line does not give you an error because your environment is smart enough to know that "1" falls within the range of a byte.
[PHP]byte iVar=1;
[/PHP]

If you where to change this statement to the following you would get an error (because 128 doesn't fall within the range of a byte).
[PHP]byte iVar=128;
[/PHP]

The second line gives you a error because you are doing integer arithmetic and assigning the result to a byte variable. Your environment is not smart enough to know if the result will fall within the range of a byte, so it gives you an error. 
[PHP]
iVar=iVar*2;
[/PHP]

---

### Post by aloshbennett on 2008-09-09
Brilliant catch!
You would find on the net that i*=2 is syntactically same as i=i*2, but it is not.

> i*=2 expands to i = (type of i)(i*2)

The reason is very logical. i = i*2 is made of two unlreated statements.
1. Compute value of i*2.
2. Assign the value to a variable (in this case 'i' itself)
Java enforces type check here because LHS and RHS could belong to different datatypes.

But when you say, i*=2, you are explicitly saying that you want to modify the value of 'i' and hence the result has to be of the same type as 'i'. Though it can be broken down into an operation and assignment, the syntax binds them together and they are not independent anymore. Java assumes that you want to modify the value of i and makes life easier by doing the type casting implicitly.

To give an example
> byte i=2;
i*=100

Should expand to 200 which is outside the range of byte. But it type casts itself to byte and you would find that the value of i is -56.

---

