---
title: "C++ puzzle :-)"
date: 2010-01-22
forum: Programming Talk
---

### Post by akvino on 2010-01-22
int iter = 4;
	iter = (iter++) + (iter++);
	cout << "\n Iter after iter++ is " << iter << endl;

	int iter2 = 4;
	iter2 = ++iter2 + ++iter2;
	cout << "\n Iter2 after ++iter2 is " << iter2 << endl;

Question - what is the value of 'iter', and what is the value of 'iter2'?


Can you describe this process step by step as compiler makes instructions and adds integers to provide answer?

---

### Post by NovaAesa on 2010-01-23
Just from looking at the code, I would assume that iter would have a value of 9 and iter2 would have a value of 11. I haven't run the code though, so I could be wrong.

I'm assuming that the side effect of say iter++ would occur in a left to right fashion in any given expression.


EDIT: I'm wrong, I just ran the code and it's 10 and 12 on g++. Hmmm, I can tell I will be thinking about this for the next little while...

---

### Post by gnometorule on 2010-01-23
I'm answering this for ANSI C, which I know far better, but as it's a subset of C++ (more or less), results should be the same.

(1) Because of side-effects galore, you can't prescribe the exact disassembly.

(2) however, no matter how the compiler decides to implement this, the result should be

iter = 10
iter2 = 12

(3) As the side-effect resolution cannot be predicted, I assume for simplicity that the + operator first resolves its left operand; then its right operand.

(4) Iter2 (LHS/RHS wrt to the '+' operator)

- increment j before adding (LHS), so j = 5
- increment j again before adding (RHS), so j =6
- now, note that this is on the function stack the same j, so....
- we add 6+6 = 12

(5) Iter:

- use i, remember still need to increment (LHS) AFTER a use, so i = 4
- use i on RHS (which still is 4 as it has not been used), keep in mind that i needs to be (again) incremented after use, so i RHS = 4 too
- use those i's by adding them, result = 8
- assign 8 to the left hand side of the '=' (NOTE BELOW)
- now execute the two increments still missing, aka, (++(++ 8 ')= 10

I believe that the compiler could at the NOTE BELOW step also increment first here, result 10; and then assign this 10 to the left hand side of the '='

EDIT: Acutally, last 2 lines - that changes the answer. While most compilers probably will evaluate this to 10, if the NOTE BELOW happens (and it seems legit), then the double increment would relate to the i as currently in memory (my - flawed - logic above applies it to the 4+4 which is just some as-yet unassigned tmp value), increment that i (still = 4) to 6, which then is overridden by the addition of 4+4 on the right-hand side of the '='. In that case, the final result for iter would be iter = 8. So my final answer and no life-line is that...

iter2 = 12
iter = 10 or 8, compiler dependent, with most compilers probably making it 10.

---

### Post by denarced on 2010-01-23
nice little puzzle :)
I got the first right but the second baffled me until I read the explanation. I got 11 on the second one, but of course it's 12.

Cute little brain-teaser for saturday morning :D

---

### Post by daasdingo on 2010-01-23
wow, the second one is just crazy,
i would have said 11 for sure until I read the explanation

---

### Post by not_a_phd on 2010-01-23
Looks to me as if someone is fishing for an answer to a homework or take-home exam question. ):P

---

### Post by akvino on 2010-01-23
> **not_a_phd said:**
> Looks to me as if someone is fishing for an answer to a homework or take-home exam question. ):P

Haha NO. What happened is I got 12 on teh second one just testing some code, and I didn't know how to explain it... Nice that someone knows compiler stuff better than I do..... 

Yes it is a nice little puzzle.:D:popcorn:

---

### Post by dribeas on 2010-01-23
The result is 'Undefined Behavior'. The standard explicitly prohibits that usage (more than one modification to the same variable within a single sentence).

In the first part of the code:
```

int var = 1;
var = (var++) + (var++);

```

The explicit execution of the post increment (before the compiler performs any optimization it may want) is creating temporary variables for the return values of the post-increment operations. Then it can reorder the code in many ways, three of which are:

```

// option 1: result=4
int tmp1 = var; // 1
int tmp2 = var; // 1
var = tmp1 + tmp2; // 2
++var;  // 3
++var;  // 4

// option 2: result=3
int tmp1 = var; // 1
++var;
int tmp2 = var; // 2
++var;
var = tmp1+tmp2; // 3

// option 3: result=2
int tmp1 = var; // 1
int tmp2 = var; // 1
++var;
++var; 
var = tmp1 + tmp2; // 2

```

The same goes for the pre-increment operator. Two possible outcomes could be:

```

// condensed:
int var = 1;
var = ++var + ++var;

// option 1: 
var = var +1; // var = 2
var = var +1; // var = 3
var = var + var;  // var = 6 (3+3)

// option 2: - the compiler stores temporary values into other registers
var = var +1; // 2
int value1 = var; // 2 - store value after first preincrement
var = var +1; // 3
var = var + value1; // 5

```

The first version is probably the first thing that would come to mind. The explanation of the second version is:

```

load var into register 1
increment register 1
save register 1 to var # ++var performed in register 1, keeping value for later use: 2

load var into register 2
increment register 2
save register 2 to var # ++var performed in register 2, keeping value for later use: 3

sum register1 and register2
store into var

```

The conclusion is that code should never ever perform more than one modification to the same variable between two sequence points (and thus adhere to what the standard requires for a well-formed program)

---

### Post by akvino on 2010-01-23
Wow I just learned two things from the same thread...


Thanks :D

---

