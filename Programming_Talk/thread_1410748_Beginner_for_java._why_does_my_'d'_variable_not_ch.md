---
title: "Beginner for java. why does my 'd' variable not change from zero and the others do?"
date: 2010-02-19
forum: Programming Talk
---

### Post by javastudent on 2010-02-19
import java.util.*;

public class Sort
{
	public static void main(String[] args)
	{
		Scanner kb = new Scanner(System.in);

		System.out.println("Enter three whole numbers. Please press enter after each number.");

		int a = kb.nextInt();
		int b = kb.nextInt();
		int c = kb.nextInt();

		int e = 0;
		int f = 0;
		int d = 0;


		while (d != 0 || e != 0 || f != 0)

			if(a<=b && a<=c)

			d = a;
				else if ((b<=a) && (b<=c))
				d = b;
				else if (c<=a && c<=b)
				d = c;



		 if (a>=b && a>=c)
			f = a;
				else if (b>=a && b>=c)
				f = b;
				else if (c>=a && c>=b)
				f = c;

		 if (a<f && a>d)
			e = a;
				else if(b<f && b>d)
				e = b;
				else if(c<f && c>d)
				e = c;

		System.out.println("In ascending order:"+ d + "" + e +""+ f);


	}
}

---

### Post by dwhitney67 on 2010-02-19
Look at what you have done here:
```

int e = 0;
int f = 0;
int d = 0;


while (d != 0 || e != 0 || f != 0)
...

```
The conditional in the while-statement will always evaluate to false.

Since you have neglected to utilize any curly brackets in your code, I cannot tell if you intended the second and third if-blocks to be part of the while-loop, but as it stands now, they are not.  You should (almost) always use curly-brackets to delineate where a block of code begins and ends.  It makes reading and maintaining the code a lot easier.

---

### Post by GregBrannon on 2010-02-19
Reevaluate your while statement.

Your code would be easier to read by adding brackets.

---

### Post by nvteighen on 2010-02-19
> **GregBrannon said:**
> 
Your code would be easier to read by adding brackets.

Actually, his code would only make sense by adding brackets...

---

### Post by kernelnewbie1 on 2010-02-19
Hello,
as dwhitney67 pointed out the while loop condition always evaluates false , so any thing after while is neglected , usually a set of statements to be executed on success of a loop condition are enclosed in curly braces are put after while() , but if its only single statement that need to be iterated then curly braces is not necessary, since u have not used curly braces the next statement after while if(..) is considered as the statement of iteration since loop condition is false the if statement is ignored , and thus the statement of execution on if condition being true and all else if --else branch related to the if condition is never executed ,hence d is left unchanged (d = 0)

seeing your code , i felt that while loop is unnecessary , as while is used for iterative tasks and is no way related to your logic

removing the while()  and using <= and >= in last if-else block might give you the desired output

p.s:
"An error is the best way to begin programming !"

---

### Post by alexk82 on 2010-02-19
I'm not trying to throw you under a bus, but what are you trying to learn with this program? while there maybe issues with how the code works you should take a look at how you are solving a problem using java.  as this is not a java issue but a logic issue

---

