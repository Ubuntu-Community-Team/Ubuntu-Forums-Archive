---
title: "C++ help"
date: 2007-10-10
forum: Programming Talk
---

### Post by sdmike on 2007-10-10
Is there something I can put inbetween the gaps of the else ifs to move the code along. 
```

while (true)
{
if (value1 >= 1 && value1 <= 100)
<----HERE
else if (value2 >= 1 && value2 <= 100)
<----HERE
else if (value3 >= 1 && value3 <= 100)
<----HERE
else
cout << "Error" << endl;
break;
```
I just want to make sure these numbers in a file are checked to see if the are between 1 and 100. If not the program stops and prints Error.

---

### Post by totalnub on 2007-10-10
if i were checking 3 numbers, i would
```

if (value1 < 1 || value1 > 100 || value2 < 1 || value2 > 100 || value < 1 || value3 >100)
{
    cout << "ERROR";
    break;
}
rest of code here

```

---

### Post by exhume on 2007-10-10
> **totalnub said:**
> if i were checking 3 numbers, i would
```

if (value1 < 1 || value1 > 100 || value2 < 1 || value2 > 100 || value < 1 || value3 >100)
{
    cout << "ERROR";
    break;
}
rest of code here

```

That is exactly how I would do it, although I am not exactly certain of the purpose of that break. it looks pretty unnecessary to me.

---

### Post by dwhitney67 on 2007-10-10
In your case the break would not be necessary.

If you are looking to merely continue programming and compiling without getting syntax errors, just insert an opening '{' and a closing '}' after the if-statement and each else-if statement.  Thus:

```
if ( condition1 )
{
}
else if ( condition2 )
{
}
else
{
}
```

It is prudent, and a standard practice in many organizations to place {} brackets, even if only one statement follows an "if" or "for-loop" statment.  Whether you put the opening bracket on the same line as the line containing the condition-check is up to you.  I personally prefer the style shown above.

I just re-read your OP... what do you mean "move the code along"??

---

### Post by derrywang on 2007-10-10
yes. correct.

---

