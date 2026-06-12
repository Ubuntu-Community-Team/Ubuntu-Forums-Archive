---
title: "Need help with C++ program."
date: 2006-04-16
forum: Programming Talk
---

### Post by Gray. on 2006-04-16
I wanted to create a program (basic I think) that would allow the user to input a number of values for variables (say a=3 and b=2) then they enter an equation to input these variables into (say 2a*b). And basically the program will calculate the answer correctly (12). I tried to myself but I keep getting stuck at when they have to input the equation they wish to insert the values into.

```

#include <iostream>
using namespace std;

int main ()
{
   float a, b, c;
   cout << "Please enter value for a: ";
   cin >> a;
   cout << "Please enter value for b: ";
   cin >> b;
   cout << "Please enter equation you wish to solve: "
   ????????????
```

I'm sure it's something really simple but I've been tearing my hair out trying to get this thing done. I did all the really simple examples like Hello World and such. (And no it's not for some assignment or anything. I just wanted to make a small program to help me get a feel for programming.) Please tell me if I'mbeing too ambitious.

Please tell me if this is too ambitious for a first try.

---

### Post by cwaldbieser on 2006-04-16
[QUOTE=Gray.]I wanted to create a program (basic I think) that would allow the user to input a number of values for variables (say a=3 and b=2) then they enter an equation to input these variables into (say 2a*b). And basically the program will calculate the answer correctly (12). I tried to myself but I keep getting stuck at when they have to input the equation they wish to insert the values into.

```

#include <iostream>
using namespace std;

int main ()
{
   float a, b, c;
   cout << "Please enter value for a: ";
   cin >> a;
   cout << "Please enter value for b: ";
   cin >> b;
   cout << "Please enter equation you wish to solve: "
   ????????????
```

I'm sure it's something really simple but I've been tearing my hair out trying to get this thing done. I did all the really simple examples like Hello World and such. (And no it's not for some assignment or anything. I just wanted to make a small program to help me get a feel for programming.) Please tell me if I'mbeing too ambitious.

Please tell me if this is too ambitious for a first try.[/QUOTE]

This seems like it might be somewhat complex for an entry-level program in C++.  With tools that allow run-time evaluation of user inputed code, it might be easy, but C++ has no such built-in facility.  You would have to get the user input as a string and then parse it to make sure it conforms to the syntax you are expecting.  Tools like flex and bison would help, or maybe the boost::spirit parser would be easier.

You haven't explicitly stated what kind of arithmetic operations you want to perform on the variables, so it is somewhat difficult to guage the complexity of the parser you would need to write.

---

### Post by Retrix on 2006-04-16
This is a harder task than you seem to imagine and it may require a little more learning on your part. What you will need to do is to input the equation as a string and do some parsing on it. Look for the operators and operands and classify them as such - the best method would probably be to convert the equation into a binary tree. Then replace and simplify.
Also to start with I would suggest not allowing implicit operators such as 2a, and instead demand the user types 2*a. I would even go so far as to say begin with a reverse-polish-notation calculator, as it would be a lot easier to implement.

---

### Post by gerbman on 2006-04-16
[QUOTE=Gray.]I wanted to create a program (basic I think) that would allow the user to input a number of values for variables (say a=3 and b=2) then they enter an equation to input these variables into (say 2a*b). And basically the program will calculate the answer correctly (12). I tried to myself but I keep getting stuck at when they have to input the equation they wish to insert the values into.

```

#include <iostream>
using namespace std;

int main ()
{
   float a, b, c;
   cout << "Please enter value for a: ";
   cin >> a;
   cout << "Please enter value for b: ";
   cin >> b;
   cout << "Please enter equation you wish to solve: "
   ????????????
```

I'm sure it's something really simple but I've been tearing my hair out trying to get this thing done. I did all the really simple examples like Hello World and such. (And no it's not for some assignment or anything. I just wanted to make a small program to help me get a feel for programming.) Please tell me if I'mbeing too ambitious.

Please tell me if this is too ambitious for a first try.[/QUOTE]I think it's do-able if you restrict the types of equations they can enter and ignore operator precedence. For example, correctly evaluating a+b*c requires knowing that the multiplication should be performed first, and giving the user complete freedom as to the equation they enter would require parsing the input...not exactly trivial if you allow all the operators/symbols. However, ignoring precedence and requiring an operator between every variable/number would simplify things. You would need to figure out the locations of the variables, numbers, and operators in the equation, and then execute the corresponding operations in C++. For example:```
2*a+b*6
```here, every character in an even-numbered location is either a variable or number. Every character in an odd-numbered location is an operator. It might be easier to first process the equation for variables and then prompt the user for values.

Not sure if that makes any sense. In general, though, never try anything you think you can do easily...that's no way to learn programming :-)

---

### Post by jpkotta on 2006-04-16
[http://www.softnet.tuc.gr/~apdim/projects/e/](http://www.softnet.tuc.gr/~apdim/projects/e/)

---

### Post by kike_coello on 2006-04-17
its like somebody already said. to solve this problem you would need a binary tree and some type of input order so that the program knows how to solve (like parenthesis first then exponentiation, etc ,etc).

to keep it simple for a beginner as i assume you are, why don't you use a switch statement and display templates of equations that you can solve by hand. like you can have something like this on the screen and have the user pick:

a) linear
b) quadratic
c) cubic
...

then ask for the coefficients needed by the equation and solve for values of x

or use equations like areas or volumes like :

a) area of circle
b) area of triangle
c) area of square

use a switch for each letter that the user picks. 

hope i helped

---

