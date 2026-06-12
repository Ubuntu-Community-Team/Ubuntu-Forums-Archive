---
title: "Pointers in C"
date: 2011-08-18
forum: Programming Talk
---

### Post by shashanksingh on 2011-08-18
If *p is a pointer, why is it that *p++ increments the pointer and not the Value pointed by it?

It confused me with the normal convention, shouldn't it increment the dereferenced value? :confused:

---

### Post by cgroza on 2011-08-18
Take a look at operator precedence:[ http://en.cppreference.com/w/cpp/language/operator_precedence]("http://en.cppreference.com/w/cpp/language/operator_precedence")
Postfix operators have high precedence.
*'s precedence is lower.

---

### Post by shashanksingh on 2011-08-18
> **cgroza said:**
> Take a look at operator precedence.

[Operator precedence]("http://www.difranco.net/cop2220/op-prec.htm")

From the above link, I think C will do the increment first and then dereferencing.
So does that mean it will increment "p" first and then return the value at p?
If yes, can someone pls eplain what happens at the third printf statement?

```

#include <stdio.h>

int main()
{
	char c[]="Hello";
	char *p=c;
	printf("%c\n",*p++);
	printf("%c\n",*p);
	printf("%c\n",++*p);
	return 0;
}

```

The above code gives me this:

```

H
e
f


```

---

### Post by cgroza on 2011-08-18
Take a look at Note 2 in the link you provided:

> 
**Note 2:**Postfix increment/decrement have high  						precedence, but the actual increment or decrement of the  						operand is delayed (to be accomplished sometime before  						the statement completes execution). So in the statement  						[FONT=Courier New][SIZE=2]**y = x * z++; ** 					[/SIZE][/FONT]the current value of 						[FONT=Courier New][SIZE=2]**z**[/SIZE][/FONT] is  						used to evaluate the expression (*i.e., * 					[FONT=Courier New][SIZE=2]**z++ **[/SIZE][/FONT]evaluates to  					[FONT=Courier New][SIZE=2]**z**[/SIZE][/FONT])  						and [FONT=Courier New][SIZE=2]**z**[/SIZE][/FONT]  						only incremented after all else is done. See ** 					[FONT=Courier New][SIZE=2] 					[postinc.c]("http://www.difranco.net/cop2220/examples/k&r_examples/postinc.c")[/SIZE][/FONT]**  						for another example.

---

### Post by Bachstelze on 2011-08-18
> **shashanksingh said:**
> If *p is a pointer, why is it that *p++ increments the pointer and not the Value pointed by it?




> **shashanksingh said:**
> 
```

#include <stdio.h>

int main()
{
	char c[]="Hello";
	char *p=c;
	printf("%c\n",*p++);
	printf("%c\n",*p);
	printf("%c\n",++*p);
	return 0;
}

```

The above code gives me this:

```

H
e
f


```

**In this code, *p is not a pointer! p is a pointer, *p is a char!**

For heaven's sake, I've told you that at least three times!

---

### Post by Arndt on 2011-08-18
> **shashanksingh said:**
> [Operator precedence]("http://www.difranco.net/cop2220/op-prec.htm")

From the above link, I think C will do the increment first and then dereferencing.
So does that mean it will increment "p" first and then return the value at p?
If yes, can someone pls eplain what happens at the third printf statement?


Precedence has inherently nothing to with when something is performed. It has to do with which of several possible parenthesizations (if there is such a word) to choose when no parentheses are given.

*p++ means one of (*p)++ and *(p++). It in fact means the latter.

Try out these expressions:
*p++
(*p)++
*(p++)
*++p
*(++p)
++*p
++(*p)

In the more well-known case of arithmetic operators, like 4 + 5 * 7,
"precedence" can in fact be equated with "performing first", so the ++ operator is a little unusual that way. It may even be unique - does anyone know other examples?

---

### Post by karlson on 2011-08-18
> **shashanksingh said:**
> 
From the above link, I think C will do the increment first and then dereferencing.
So does that mean it will increment "p" first and then return the value at p?


No it means that it will increment p and return the value that used to be p in your case.  Not the value at p.  *p returns the value at p.

p++ returns the value of p preincrement.

---

