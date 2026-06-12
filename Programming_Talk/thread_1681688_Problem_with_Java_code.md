---
title: "Problem with Java code"
date: 2011-02-04
forum: Programming Talk
---

### Post by stamatiou on 2011-02-04
Hey guys,
I have written a script in Java but I something is wrong....
The purpose of this program is to calcualate the average of your grades....
```
import java.util.Scanner;
class papi {
	public static void main (String args[]){
		Scanner input = new Scanner(System.in);
		System.out.println("How many grades do you have?");
		int grades = input.nextInt();
		int total = 0;
		int grade;
		int average;
		int counter = 0;
		while (counter < grades){
			System.out.println("Put your average number:");
			grade = input.nextInt();
			total = total + grade;
			counter++;			
		}
		average = total/grades;
		System.out.println("Your average grade is " + average);
	}
	
}

```
But when it is the time for the script to show the average it shows the last number....

---

### Post by noneofthem on 2011-02-04
Hello there!

I just tested your code on my machine and it works fine. I couldn´t find any obvious errors either. How do you use that script? As I said, in Eclipse (3.5.2) using Java 1.6.0.22) everything is alright here. There must be an error somewhere else.

---

### Post by stamatiou on 2011-02-05
> **noneofthem said:**
> Hello there!

I just tested your code on my machine and it works fine. I couldn´t find any obvious errors either. How do you use that script? As I said, in Eclipse (3.5.2) using Java 1.6.0.22) everything is alright here. There must be an error somewhere else.
And it makes an average? In my computer it prints me the last number...

---

### Post by GregBrannon on 2011-02-05
Each number input is assigned to 'grade', but your last line which prints the result, prints 'average' which is the result of total/grades.  It would be purely coincidental if the result printed is the same as the last number input.

Suggestions:
Use more descriptive variable names.  This is a simple program in which it's easy to remember the purpose of the handful of variables, but in a program of several hundred lines and almost as many variables, it may be hard to remember the difference between variables named 'grade' and 'grades'.

Expressions like 'total = total + grade;' can be (are usually) written as 'total += grade;'

When the number of times a loop will execute is known, the 'for' loop is the more typical choice.  As you've shown, a 'while' loop can always be constructed to replace a 'for' loop, but avoid it unless the assignment requires it.

---

### Post by PaulM1985 on 2011-02-05
Another thing that you may wish to consider is that your average will always appear to be rounded down.  This is because you are using integer division.

if you used:
```

double average = (double)total / (double) grades;

```

The current code would average grades 5 and 6 to be 5, whereas this would give you 5.5.

Paul

---

### Post by forrestcupp on 2011-02-05
> **GregBrannon said:**
> It would be purely coincidental if the result printed is the same as the last number input.Right. The last number you entered just happened to be the same as the average.

> **PaulM1985 said:**
> 
if you used:
```

double average = (double)total / (double) grades;

```If you did the double thing, you would avoid that coincidence.

---

### Post by stamatiou on 2011-02-05
Million thanks guys...):P:guitar:

---

