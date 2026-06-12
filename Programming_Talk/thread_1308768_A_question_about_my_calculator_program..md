---
title: "A question about my calculator program."
date: 2009-10-31
forum: Programming Talk
---

### Post by hector_ronado on 2009-10-31
Hi, I was having problem with my program. It still have some error when I typed in 5.0 and it only showed up 5 or I typed some other words that wasn't digit and it will be a big error. Can someone tell me what should I do to fix this?
Here's my homework assignment:
   Write a Program that models a simple calculator. Each data entry line should consist of a valid operator (from the list below), and the right-hand operand. Assume that the left-hand operand is the accumulated value in the calculator, with an initial value of 0.0. 
  Acceptable operators: 
  + ..Add 
  - ..Subtract 
  * ..Multiply 
  / ..Divide 
  ^ ..Power (raise left operand to the power of the right operand) 
  q or = ..Quit 
  Your Calculator should display the accumulated value after each operation. A sample run might be: 
  + 5.0 
  Result so far is 5.00 
  ^ 2 
  Result so far is 25.00 
  / 2.0 
  Result so far is 12.50 
  Q 0 
  The final result is 12.50 
  Include (define and call) at least THREE functions: 
  
[LIST]
[*]a function that displays      instructions to the user.
[*]a function do_next_op()      that has 3 input parameters (the operator, the operand, and the current      accumulated value), and returns the new value for the accumulated value. An      alternative implementation may use 2 input parameters (operator and      operand), and 1 input/output parameter (the accumulated value)
[*]at least one other      function - of your choice! Make sure that it does something useful.
[/LIST]
  
Here's my program code:
```

#include <iostream>
#include <cmath>
using namespace std;

void instruction ();
float do_next_op ( float&, float&, char );

int main()
{

instruction(); // displays instruction
float total;
float newentry;
char op;

total = 0;
// initialisation

cin >> op;
while (op != 'Q' && op != 'q' && op != '=')
{
cin >> newentry;
do_next_op (total, newentry, op);
cin >> op;
}
cout << "the final result is " << total << endl;

system ("pause");
return 0;
}

void instruction()
{

}

float do_next_op ( float &total, float &newentry,char op)
{

switch (op)
{
case '+': total = total + newentry;
break;
case '-': total = total - newentry;
break;
case '*': total = total * newentry;
break;
case '/': total = total / newentry;
if (newentry == 0)
{
cout << "divide by zero is unexecutable" << endl;
}
break;
case '^': total = pow (total,newentry);
break;
default : cout << " Unacceptable Operator(" << op << ")" << endl;
}

cout << "result so far is " << total << endl;
cout << endl;

return (total);
}

```

---

### Post by hector_ronado on 2009-11-01
Can someone help me out?

---

### Post by Sinkingships7 on 2009-11-01
Putting your code in between code tags would help us help you.

---

### Post by hector_ronado on 2009-11-01
I already put my code in code tag~~

---

### Post by Sinkingships7 on 2009-11-01
My bit of testing showed that your program worked well to the specifications.

I'm guessing your "big error" problem is from when you try to store a string in a float variable? If so, you may want to ignore this since it doesn't seem to be a requirement for the assignment.

If you want to fix it anyway, read up on exceptions and clearing the input stream (cin).

---

### Post by hector_ronado on 2009-11-02
But when I typed in +5.0, it should display 5.00. And my program only showed up 5, here's the biggest error...XD So can you tell me what should I change?

---

### Post by eightmillion on 2009-11-02
You need to tell cout to show the the point for values that are whole numbers. Something like this:
```
    cout << showpoint;
    cout.precision(3); // default precision is 6, which would print 5.00000
```

---

### Post by dwhitney67 on 2009-11-02
> **Sinkingships7 said:**
> My bit of testing showed that your program worked well to the specifications.
...

You're kidding right?  Did you try to perform a division using 0 as the denominator (ie. newentry)?  Ok I'll concede that you only did a 'bit' of testing, but still, the bug in the code is quite obvious with a spot-check.  You don't even need to run the code.  Maybe zero cannot be represented exactly as 0.0000000?

---

### Post by dwhitney67 on 2009-11-02
@ the OP

For a calculator application, you should consider treating the "Calculator" as an object.  To do so, you declare/define it as a class that provides support for the various operations that you wish to perform.

For example:
```

#include <iostream>
#include <stdexcept>

class Calculator {
public:
   Calculator(double value = 0) : myTotal(value) {}

   double operator+(double value) {
      return (myTotal += value);
   }

   double operator-(double value) {
      return (myTotal -= value);
   }

   double operator*(double value) {
      return (myTotal *= value);
   }

   double operator/(double value) {
      if (value == 0) throw std::runtime_error("divisor cannot be zero!");

      return (myTotal /= value);
   }

   friend std::ostream& operator<<(std::ostream& os, const Calculator& calc) {
      os << calc.myTotal;
      return os;
   }

private:
   double myTotal;
};

int main() {
   Calculator calc;

   calc + 5;
   calc - 1;
   calc * 7;
   calc / 2;

   std::cout << "calc = " << calc << std::endl;

   try {
      calc / 0;
   }
   catch (std::exception& e) {
      std::cerr << "Test dividing by zero... " << e.what() << std::endl;
   }
}

```

---

### Post by Sinkingships7 on 2009-11-02
> **dwhitney67 said:**
> You're kidding right?  Did you try to perform a division using 0 as the denominator (ie. newentry)?  Ok I'll concede that you only did a 'bit' of testing, but still, the bug in the code is quite obvious with a spot-check.  You don't even need to run the code.  Maybe zero cannot be represented exactly as 0.0000000?

Yeah, I noticed that right away. I really did mean the parts about a "bit" and "to the specifications". It didn't say he needed to catch errors.

I'll admit my post was of little use, though. I was quite tired.

---

