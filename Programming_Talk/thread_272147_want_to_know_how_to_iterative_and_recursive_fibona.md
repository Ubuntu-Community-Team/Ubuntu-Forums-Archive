---
title: "want to know how to iterative and recursive fibonacci programs in perl and python"
date: 2006-10-05
forum: Programming Talk
---

### Post by baldy1324 on 2006-10-05
i want to know how to make a fibonacci sequence program for two different methods in perl and python
1. iterative (while loop of making a-b,b-c...)
2. recurisive-calling the function itself again and again
i want the programs to make a fibonacci sequence go to a certain number and print all the numbers
if you have any code please post it
thanks

---

### Post by ghostdog74 on 2006-10-05
you can use generators in Python:
```

def fib():
    a, b = 0, 1
    while 1:
        yield a
        a, b = b, a + b
 
fibo = fib()
for x in range(100):
    print fibo.next(), 

```

---

### Post by Desi-Tek.com on 2006-10-05
is it that small in python? great .. in java it takes 2times more code than that

```
 class Fibonacci
{
   public static void main(String[] arguments)
   {
      // The line below initialises an integer variable called
      // length to the value of the parameter passed to the program.
      // This value needs to be converted (parsed) before
      // it can be used.
      int length = Integer.parseInt(arguments[0]);
      int number1 = 0;
      int number2 = 1;
      int sum = 0;
   
      System.out.print(number1);
      
      for (int i = 0; i < length; i++)
      {
         System.out.print(" " + number2);
         sum = number1 + number2;
         number1 = number2;
         number2 = sum;
      }
      
      System.out.println();
   }
} 
```

---

### Post by ghostdog74 on 2006-10-05
how bout this?
```

 public static int fibonacci (int num) {
	int calc = 0; 
	if (num <= 1) 
	    calc = num;
	else          
	    calc = fibonacci (num - 1) + fibonacci (num);
	return calc;
   }

```

---

### Post by asimon on 2006-10-06
Have a look at [Fibonacci number program @ Wikepedia](http://en.wikipedia.org/wiki/Fibonacci_number_program#Ruby).

---

