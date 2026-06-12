---
title: "c++ for statement vs if"
date: 2007-07-12
forum: Programming Talk
---

### Post by zerobinary on 2007-07-12
i don't quite want what is for statement i know is a loop but what's the purpose for for statement and what's the difference between for and if statement

---

### Post by aks44 on 2007-07-12
A **for** statement's purpose is to execute it's body several times, kinda like a **while**, depending on it's initialization / condition / increment parts.

eg.

```
for (initialization ; condition ; increment)
{
  body;
}
```

is equivalent to

```
initialization;
while (condition)
{
  body;
  increment;
}
```

An **if** statement executes it's body only *once* if the condition is met.



What book are you reading that doesn't explain that? :-s

---

### Post by Jucato on 2007-07-12
The basic difference:

The for statement is used to repeat a statement or a group of statements (a block). This is called repetition.

The if statement is used to choose a different path of action. This is called selection.

For example, you want X to be multiplied by itself N number of times. You use a repetition statement like for.

You want your program to print out "Good morning!" if it's morning (by checking the time), you use a selection statement like if. Like what aks44 said, the if's body only executes if the condition is met (true). Otherwise, it will skip the if's body and proceed with the rest of the program. (Unless the "if" comes with an "else").

---

### Post by zerobinary on 2007-07-12
thx

---

### Post by slavik on 2007-07-13
and if can be emulated using for, but not vice versa. :)

---

### Post by bashologist on 2007-07-13
With for loops you can also initialize multiple variables and increment multiple.

Source Example:
```
#include <iostream>

using namespace std;

int main()
{
	for ( int i = 1, x = 10; i < x; i += 2, x ++ )
	{
		cout << "i: " << i << "\tx: " << x << endl;
	}
	return true;
}

```
Output:
```
i: 1    x: 10
i: 3    x: 11
i: 5    x: 12
i: 7    x: 13
i: 9    x: 14
i: 11   x: 15
i: 13   x: 16
i: 15   x: 17
i: 17   x: 18
```

---

