---
title: "Function initialization and declaration in C"
date: 2010-08-31
forum: Programming Talk
---

### Post by jfreak_ on 2010-08-31
So my friend says that they MUST be done SEPARATELY, while I from my experiance know that it can be done together, like for example:
My friend's version

```
void add();

void add()
{
......
}
void main()
{
add();
}
```

My version
```
void add()
{
......
}
void main()
{
add();
}
```

So could anyone give me reliable source which says which one or both of us is correct(To show my friend)?

---

### Post by Bachstelze on 2010-08-31
First, a function that takes no argument should have void as its argument list: void add(void)

Second, main returns int: int main(void)

As for your actual question, declaring the prototype is not required if all the functions are in the same file:

```
int fact(int n)
{
    if (n == 0)
        return 1;
    else
        return n*fact(n-1);
}

int main(void)
{
    return fact(2);
}
```

That will work. However, if the functions are in separate files:

fact.c:

```
int fact(int n)
{
    if (n == 0)
        return 1;
    else
        return n*fact(n-1);
}
```

main.c:

```
int main(void)
{
    return fact(2);
}
```

That will not work (the compiler will tell you that fact is not declared). You must add the declaration for fact:

```
int fact(int);

int main(void)
{
    return fact(2);
}
```

That will work.

---

### Post by xb12x on 2010-08-31
Not to put to fine a point on it, but the function fact() should be declared before being called in main(). This is because the compiler needs to know about the stack requirements when calling fact(), especially if fact() returns something other than an int. Without the declaration before being called the compiler assumes fact() returns an int.

Move the fact() declaration/initialization after the function main() in the file then compile with the -Wall option and you will get the warning

warning: implicit declaration of function ‘fact’

---

