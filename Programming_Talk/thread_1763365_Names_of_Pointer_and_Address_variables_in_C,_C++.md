---
title: "Names of Pointer and Address variables in C, C++"
date: 2011-05-20
forum: Programming Talk
---

### Post by rajn on 2011-05-20
Hi,
I am quite confused about naming conventions. Consider this program for example in which values of x and y are swapped.

[COLOR=#0066ff]#include <iostream.h>
4:
5:      void swap(int *x, int *y);
6:
7:      int main()
8:      {
9:        int x = 5, y = 10;
10:
11:        cout << "Main. Before swap, x: " << x << " y: " << y << "\n";
12:        swap(&x,&y);
13:        cout << "Main. After swap, x: " << x << " y: " << y << "\n";
14:     return 0;
15:      }
16
17:      void swap (int *px, int *py)
18:      {
19:        int temp;
20:
21:        cout << "Swap. Before swap, *px: " << *px << " *py: " << *py << "\n";
22:
23:        temp = *px;
24:        *px = *py;
25:        *py = temp;
26:
27:        cout << "Swap. After swap, *px: " << *px << " *py: " << *py << "\n";
28:
29: }[/COLOR]



This is what I am now confused about :

*x would mean x is a pointer to an int i.e., x is the address of an integer variable
&x would mean x is a variable pointed to.
That does not sound correct. How can x refer to two different things. Yet the program works.

Therefore, what I would like to know is this:

if I have a variable 'v'
to declare a reference to 'v' do I have to necessarily name it as &v (or any &dummy1 would work)
similarly to declare a pointer to that variable should it necessarily be *v or *dummy2 should work.


Thank you,
rajn

---

### Post by cgroza on 2011-05-20
> &x would mean x is a variable pointed to.x is always the same variable.

When you do &x, you basically getting it's address in the memory.

I think in this context, the & is called the reference operator (I am probably wrong, so correct me.).

With it, you can initialize a pointer, so you can do:
```

int * x_ptr = &x;
```

---

### Post by psusi on 2011-05-20
The meaning of * and & depend on whether you are defining a variable or referencing one.  When defining variables, & makes it a reference and * makes it a pointer.  When referring to variables, & references, or gets the address of, the variable, and * dereferences, or follows the pointer to what it points to.

Does that clear things up?

---

### Post by JupiterV2 on 2011-05-20
> **rajn said:**
> Hi,
I am quite confused about naming conventions. Consider this program for example in which values of x and y are swapped.

....

This is what I am now confused about :

*x would mean x is a pointer to an int i.e., x is the address of an integer variable
&x would mean x is a variable pointed to.
That does not sound correct. How can x refer to two different things. Yet the program works.

Therefore, what I would like to know is this:

if I have a variable 'v'
to declare a reference to 'v' do I have to necessarily name it as &v (or any &dummy1 would work)
similarly to declare a pointer to that variable should it necessarily be *v or *dummy2 should work.


Thank you,
rajn

An asterisk '*' specifically denotes that a variable is a pointer. It points to an area of memory where a variable is stored. It is also used to 'dereference' a pointer so that its value can be set/obtained. In the case of C++, its sometimes referred to as 'pass-by-reference' when used as a function parameter.

The ampersand '&' is the 'address-of' operator, or in the case of C++, it can also be used as the 'pass-by-value' operator.

An example helps best:

[PHP]
#include <stdio.h>

/* This function takes the memory address of a variable as an argument */
static int
pass_by_reference (int* integer_ptr)
{
  /* In this case, the asterisk tells us we're dereferencing 
     the variable, allowing us to work with its value */
  *integer_ptr += 2;

  printf ("The value of the variable at memory location %p is "
          "now %d\n", integer_ptr, *integer_ptr);
}

int
main (void)
{
  /* local scope, can't be accessed outside of main ()...or
     can it? */
  int my_local_int = 0;

  printf ("Currently, my_local_int = %d\n", my_local_int);

  /* now we get the address of the local variable my_local_int
     and pass it to our function. Note that we're passing the
     address of our variable, and not the value it contains,
     to our function. That way our function can 'refer' to our
     local variable and interact with it. */
  pass_by_reference (&my_local_int);

  printf ("Now my_local_int = %d\n", my_local_int);

  return 0;
}[/PHP]

So, the '*' and '&' are operators, not variable names. You can call a variable anything you want (well, within the limitations of the C or C++ specification). 

P.S. I hope this compiles...I'm not at a location where I can test it right now! =)

---

### Post by rajn on 2011-05-20
Thanks for the response. I guess, I was a bit unclear about my confusion.

If you see my program the line below declares x and y as pointers

[COLOR=#0066ff]     void swap(int *x, int *y); 
 [COLOR=Black]
On the other hand the lines
[/COLOR][/COLOR][COLOR=#0066ff]       int x = 5, y = 10;
10:
11: 
12:        swap(&x,&y);[/COLOR]

[COLOR=Black]define x and y as integer variables. That is my confusion.  The letter 'x' is a reserved character for an integer variable, but in the declaration is seems to be a pointer too.

 To be more specific

Can I replace the first line by 
void swap(int *xx, int *yy)

and

int x=5, y = 10;
.....
swap(&zx, &zx) /*some dummy names */

If I make these changes the program does not run i.e., looks like I have to name the pointer and the reference by the 'same set of letters' that I define the variable i.e.,
if the variable x is named [COLOR=Green]int[/COLOR] howareyou 
then the program above runs if I make all variable names the same i.e., 
void(int *howareyou, int *y)
void(&howareyou, &y)

But that is weird because how can the same name "howareyou" is a variable and also a pointer......


A part of the answer is provided by JupiterV2. In his example the pointer has different letter characters for pointer name viz [/COLOR][COLOR=#000000][COLOR=#0000bb]int[/COLOR][COLOR=#007700]* [/COLOR][COLOR=#0000bb]integer_ptr
[COLOR=Black]but his variable is [/COLOR][/COLOR][/COLOR][COLOR=#000000][COLOR=#0000bb]int my_local_int[/COLOR][/COLOR][COLOR=#000000][COLOR=#0000bb] [COLOR=Black]and not[/COLOR] int integer_ptr.
[COLOR=Black]
And the program runs. Therefore it means the characters used for naming pointer ('my_local_int) need not be the characters to be used for naming the variable it is pointing to.

But if I change the statement [/COLOR][/COLOR][/COLOR][COLOR=#000000][COLOR=#0000bb]pass_by_reference [/COLOR][COLOR=#007700](&[/COLOR][COLOR=#0000bb]my_local_int[/COLOR][COLOR=#007700]);
to
[COLOR=Black]pass_by_reference(&integer_ref), the program does not run. 
This implies the characters used for naming the variable ("my_local_int") should be used to name the reference too. 

I do not see this rule explicitly written out in any C books. And that is really my confusion.

So my question: [COLOR=Red]is the processor supposed to understand that if &A is a reference then the character 'A' has to be the variable name
but if the pointer is *xyz then the variable name it points to need not be  the characters 'xyz' it could be anything including 'xyz'.[/COLOR]

Is there a rule like that in C or C++.
[/COLOR][/COLOR][/COLOR][COLOR=Black] rajn
[/COLOR]

---

### Post by cgroza on 2011-05-20
Are you familiar with the concept of variable scope?

---

### Post by rajn on 2011-05-20
> **cgroza said:**
> Are you familiar with the concept of variable scope?

Ok, fine.

How if I place the statement

void swap(int x, int y) inside the main? 
Now all are in scope...(assuming I am allowed to define a function inside main...), would it work?
Or is there still a conflict of type for 'x'
rajn

---

### Post by cgroza on 2011-05-20
You don't need to declare a function in main.
You can, but you don't need to and is not recommended.
Here is an example:

```

#include <iostream>

using namespace std;
void swap(int& x, int& y);



int main(int argc, char** args)
{
    int var1 = 10;
    int var2 = 20;

    swap(var1, var2);

    cout << var1 << endl << var2 << endl;
}

void swap(int& x, int& y)
{
    int& temp = x;

    x = y;
    y = temp;
}


```

---

### Post by dwhitney67 on 2011-05-20
My $0.02... don't bother re-implementing the wheel.
```

#include <algorithm>
#include <iostream>

int main()
{
   int x = 10;
   int y = 20;

   std::cout << "BEFORE: x = " << x << ", y = " << y << std::endl;

   std::swap(x, y);

   std::cout << "AFTER : x = " << x << ", y = " << y << std::endl;
}

```

The swap() function above is a templated-function; thus it can be used on other data types besides ints.  For example:
```

#include <string>
#include <algorithm>
#include <iostream>

class Foo
{
public:
   Foo(const int v, const std::string& s) : value(v), str(s) {}

   friend std::ostream& operator<<(std::ostream& os, const Foo& f)
   {
      os << f.value << " (" << f.str << ")";
      return os;
   }

private:
   int         value;
   std::string str;
};

int main()
{
   Foo x(10, "ten");
   Foo y(20, "twenty");

   std::cout << "BEFORE: " << "x = " << x << ", y = " << y << std::endl;

   std::swap(x, y);

   std::cout << "AFTER : " << "x = " << x << ", y = " << y << std::endl;
}

```

---

### Post by psusi on 2011-05-20
> **rajn said:**
> define x and y as integer variables. That is my confusion.  The letter 'x' is a reserved character for an integer variable, but in the declaration is seems to be a pointer too.

main() and swap() are different functions so they each have their own local scope.  The x defined in main() is an int, but is unknown to swap().  swap() defines its own x as a pointer to an int as an argument.

---

### Post by rajn on 2011-05-20
Ok, thank you everyone. 
I think the issue is partially resolved by at least two - psusi and cgroza - who correctly pointed out the scope of the functions.

My intention was not really to write a 'swap()' function. My intention was to understand this:
if for example,

main{

int *x = NULL;
int x=10;
somefunction(&x);
someexpression(*x);
print(x);

}

Does the character x create a name conflict. Or x is just a dummy name and the three x's have no correlation. 

*How does compiler know that somefunction (&x) should use the variable x?
>Because it runs an algorithm in the background to strip & and then look at character x and then tries to find a variable character with same name? How else would the very first swap function in my first post work?

But now how about the pointer declaration. Does compiler again runs its strip process in the background to get rid of * and then declares x to be an address? So it must point out a conflict as soon as it sees the int x declaration.  Is that true? I am trying to run a program to see that right away. 



Sorry for my rambling.

---

### Post by cgroza on 2011-05-20
This is your variable declaration in plain English:
You declare a pointer x.
You declare an int value x.
Int value x hides the pointer x.

It think the pointer x still resides in the stack, but you no longer have a reference to it because you overwrote its name with a int value named x.

Both will be destroyed on scope exit.
```

someexpression(*x);
```Here you are using the dereference operator on x which is no longer a pointer, but an int value.

---

### Post by simeon87 on 2011-05-20
> **rajn said:**
> Ok, thank you everyone. 
I think the issue is partially resolved by at least two - psusi and cgroza - who correctly pointed out the scope of the functions.

My intention was not really to write a 'swap()' function. My intention was to understand this:
if for example,

main{

int *x = NULL;
int x=10;
somefunction(&x);
someexpression(*x);
print(x);

}

Does the character x create a name conflict. Or x is just a dummy name and the three x's have no correlation. 

*How does compiler know that somefunction (&x) should use the variable x?
>Because it runs an algorithm in the background to strip & and then look at character x and then tries to find a variable character with same name? How else would the very first swap function in my first post work?

But now how about the pointer declaration. Does compiler again runs its strip process in the background to get rid of * and then declares x to be an address? So it must point out a conflict as soon as it sees the int x declaration.  Is that true? I am trying to run a program to see that right away. 



Sorry for my rambling.

That's not how a compiler works. A compiler performs various operations on the source code to determine the machine code for that platform. The first stage is turning the source code into tokens. So you may have that

```
int x = 0;
```

is turned into

```
int     reserved word
x       identifier
=       equals
0       number
;       semicolon
```

In the next stage, the compiler recognizes that this sequence of tokens is actually a variable declaration. So then it knows that x is a variable of type int and it is assigned the value 0.

Similarly, if you have * then it'll recognize a pointer and similar for &.

---

### Post by cgroza on 2011-05-20
Also:
```
somefunction(&x); //valid, you are passing a reference to int value x.
someexpression(*x);  //invalid, you are using the dereference operator on a non-pointer variable.

```

---

### Post by Arndt on 2011-05-23
> **rajn said:**
> Ok, thank you everyone. 
I think the issue is partially resolved by at least two - psusi and cgroza - who correctly pointed out the scope of the functions.

My intention was not really to write a 'swap()' function. My intention was to understand this:
if for example,

main{

int *x = NULL;
int x=10;
somefunction(&x);
someexpression(*x);
print(x);

}



I think no one commented on this: the above doesn't even compile - you can't have two variables with the same name in the same scope.

---

