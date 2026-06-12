---
title: "Programming in C: character to int"
date: 2008-10-10
forum: Programming Talk
---

### Post by Shippou on 2008-10-10
Hello there...

I think this is one of the most-asked questions in C. And I think most of the answers would be atoi().

But then, atoi converts a string into its number counterpart. But what I really need is to convert only a specific array element at one time.

Our machine problem currently is an assembly adding calculator. It involves a C main function calling an Assembly code. But then I cannot use int because the calculator is specified to handle addition problems up to 100 digits each addend.

As a workaround, I tried this algorithm, and it works on paper. But then I get an error (I am compiling and running the code in Windows because our prof required it)... You know, the popup message that tells you to report the problem to m$ (I haven't reported it, anyway.).

```

for (i=nomax-1; i>=0; i--) {
    noup = atoi(num1);
    nodown=atoi(num2[i]);
    sum[i-1] = (noup+nodown+carry)%10;
    carry = (noup+nodown+carry)/10;
}

```

Anyway, the function where this is under is defined as:

```

void mysum (char num1[], char num2[], char* sum) 

```

sum is an array at the main function.

Any ideas? Please help.

---

### Post by Shippou on 2008-10-10
bump...

Sorry I have to bump...

---

### Post by dwhitney67 on 2008-10-10
> **Shippou said:**
> ...

```

for (i=nomax-1; i>=0; i--) {
    noup = atoi(num1);
    nodown=atoi(num2[i]);
    sum[i-1] = (noup+nodown+carry)%10;
    carry = (noup+nodown+carry)/10;
}

```

Anyway, the function where this is under is defined as:

```

void mysum (char num1[], char num2[], char* sum) 

```

sum is an array at the main function.

Any ideas? Please help.

You may need to supply more information as to what the problem is.  Is it a compiler error, or a runtime error?  And more specifically, what is the error?

Btw, concerning the following statement:
```
    nodown=atoi(num2[i]); 
```
I do not think it is doing what you expect.  The atoi() function accepts a null-terminated char string (const char *).  I get the impression you think you are passing it a single-character; you are not.  You are passing a char string that merely has been offsetted by the index i.  And whether your string is null-terminated is unknown.

If your strings num1[] and num2[] contain digits, then subtract character '0' to yield the integer value of the character.  Something like:
[PHP]
char num1[3] = { '1', '2', '3' };

int value1 = num1[0] - '0';    // value1 == 1
int value2 = num1[1] - '0';    // value2 == 2
int value3 = num1[2] - '0';    // value3 == 3
[/PHP]

---

### Post by Shippou on 2008-10-10
I've implemented the character-'0' approach.

I was hoping that there was a built-in function in C that can do that (like atoi()). Thanks for the help.

---

### Post by lisati on 2008-10-11
Have a look at the condition for your loop. There will come a time when the loop whirls round with i=0. Which element of sum will be updated?

---

### Post by Shippou on 2008-10-11
There is no problem with the character to int conversion anymore.

I'll just have to figure out how to make the sum print the correct sum (via pointers again).

*sigh* Hard work again...

---

### Post by dwhitney67 on 2008-10-11
> **Shippou said:**
> There is no problem with the character to int conversion anymore.

I'll just have to figure out how to make the sum print the correct sum (via pointers again).

*sigh* Hard work again...
Did you read lisati's post?  When the index of your for-loop reaches zero, your code will have trouble when sum[i-1] is referenced.  Perhaps the for-loop conditional should be i > 0??

Also, how do you know what the value of nomax is?  Is this passed to the function as a parameter?  I do not recall seeing it before (when you posted the function declaration).

---

