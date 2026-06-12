---
title: "Precedence of equality and relational operator"
date: 2009-09-21
forum: Programming Talk
---

### Post by dE_logics on 2009-09-21
Suppose we have a situation (statement)>(statement2)==(statement3) 
Question is what will happen if (statement)>(statement2) is true or false?...what will happen is not defined, so this term as a whole (statement)>(statement2)==(statement3) should return an error, but it does not - 

if('Z' == 'Z' > 'A')
		printf("this should not be valid");

Gets compiled perfectly but no matter what I do, it never enters the body of the for statement.

---

### Post by MadCow108 on 2009-09-21
(statement1)>(statement2) return 0 or 1  depending on result
the relation operators <><=>= have higher precedence than == so it evaluates:
'Z' > 'A' first which gives result 1
and then
'Z' == 1
which is false

this on the other hand evaluates to true:
1 == 'Z' > 'A'
because it first does the relation then the equality

also this gives true:
'Z'=='Z'==1
because as all operators have same precedence it goes through this from left to right(because == evaluates from left to right, assignments preincrements and typecasts would evaluate right to left)
so it does: 'Z' == 'Z' => 1 (true) and then 1 == 1 => 1 (true)

you should use paranthese to make sure you use the right evaluation order and to make it readable without knowing the precedences by heart

the precedences are listed here in descending order:
[http://msdn.microsoft.com/en-us/library/2bxt6kc4(VS.71).aspx](http://msdn.microsoft.com/en-us/library/2bxt6kc4(VS.71).aspx)

---

### Post by dE_logics on 2009-09-21
> you should use paranthese to make sure you use the right evaluation order and to make it readable without knowing the precedences by heart

Yeah, I thought about that, but I was wondering what happens if I run into a code for which I should know all this...


Nothing Microsoft man...

Thanks for the help.

---

### Post by dwhitney67 on 2009-09-21
> **dE_logics said:**
> Yeah, I thought about that, but I was wondering what happens if I run into a code for which I should know all this...


You do what all professional s/w developers do... you insult the original s/w developer who wrote the code.

Coding is an unrecognized art-form; everyone seems to have their own style.  What should be avoided when writing code is any form of ambiguity.  If one's intent is to compare A and B, then to see how that result compares to C, then as MadCow stated, parenthesis ought to be used to indicate (ie advertise) which operation has precedence.  Don't rely on compiler "tricks" to accomplish a goal.

IMO, it would have been convenient if those who developed the compiler(s) would have shunned support of precedence for one type of operator versus that of another.  A conditional would be easier to read if it were processed from left-to-right.  Of course, compiler developers are not considerate of how people think, but instead of how computers think.

---

### Post by Arndt on 2009-09-21
> **dE_logics said:**
> Yeah, I thought about that, but I was wondering what happens if I run into a code for which I should know all this...



Note that not all languages behave exactly the same way. Python, for example, gives < and == the same priority and resolves the ambiguity using associativity rules.

---

### Post by issih on 2009-09-21
Precedence order is built right into mathematical logic... so I don't really think you can yoink it out that easily.

Either way, the appropriate response to any situation like this is to write a little noddy program to test what happens. If you don't know, experiment :)

---

### Post by Arndt on 2009-09-21
> **issih said:**
> Precedence order is built right into mathematical logic... so I don't really think you can yoink it out that easily.

Either way, the appropriate response to any situation like this is to write a little noddy program to test what happens. If you don't know, experiment :)

In what way is it built into mathematical logic?

---

### Post by dE_logics on 2009-09-21
Ok...ok, sure shot I wont use it man, I was wondering if others use it...

---

### Post by issih on 2009-09-21
If you want to be pedantic read "nomenclature" not "logic"...

None the less, there are well defined and well known precedence rules defining mathematical behaviour..any programming language that did not follow these would be rightly shunned.

The logical follow on is that some form of precedence ordering for operators is required, which then by extension may as well apply to everything else.

I don't disagree in any way with the idea that a system that required the use of parenthesis to disambiguate things would be preferable in many ways, but in the real world mathematical precedence order is expected, and more confusion would be caused if it wasn't implemented.

Nonetheless, my main point stands..if you don't know, check!

---

### Post by dE_logics on 2009-09-21
Yeah, programming languages should follow the standard precedence as defined by mathematics...what's the use of making you own?...it only produces havoc(aaaa...there there should be some reason...)

---

### Post by Arndt on 2009-09-22
> **dE_logics said:**
> Yeah, programming languages should follow the standard precedence as defined by mathematics...what's the use of making you own?...it only produces havoc(aaaa...there there should be some reason...)

The result of a comparison is not often used as an operand in mathematics, so there simply is no standard precedence. The symbol == as such isn't used at all, as far as I know.

---

### Post by dE_logics on 2009-09-23
Yep...righ!...forgot about that.

But relational operators are use...'inequality'

---

