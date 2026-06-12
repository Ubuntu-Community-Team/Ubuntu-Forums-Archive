---
title: "strlen(pointer) for pointers to doubles"
date: 2009-01-19
forum: Programming Talk
---

### Post by Subespaciovectorial on 2009-01-19
Hi guys. I need a little help with pointers in c++. I have a function like this:

[PHP]
bool LI(char *pointer)
{
 bool answ;

 if (strlen(pointer)>5)
  answ=0;
 else
  answ=1;

 return answ;
}
[/PHP]
No problem with pointer to char; but I need a pointer to double (actually, a pointer to an element of class "Vector", but let's try with doubles for the moment). My question is: is there a "strlen" function for pointers to doubles?

If you think there isn't, can you help me to build one? (explain me what are templates if your answer use them).

---

### Post by jimi_hendrix on 2009-01-19
what do you need? the number of didgits in the double?!!?

---

### Post by Subespaciovectorial on 2009-01-19
> **jimi_hendrix said:**
> what do you need? the number of didgits in the double?!!?

I need to know the size of the array. I'm using the pointer as a list of elements. I need to know how many elements the list has. Like this:

[PHP]

double *list=new double [237]
for (int i=0; i<237; i++) list[i]=sin(i)   // ... for example

bool LI(double *list)
{
 if (amount_of_elements(list)>10)
  return 0;
 else
  return 1;
}

delete [] list;
[/PHP]

I need the function LI to read that list has 237 elements inside. amount_of_elements(list) should be equal to 237, like strlen does with pointers to chars.

---

### Post by Zugzwang on 2009-01-19
> **Subespaciovectorial said:**
> 
I need the function LI to read that list has 237 elements inside. amount_of_elements(list) should be equal to 237, like strlen does with pointers to chars.

There is no such function. You need to pass the length of an array around with the pointer to it. That's also the reason why many C standard functions need the length of a given array as a parameter.

---

### Post by Subespaciovectorial on 2009-01-19
> **Zugzwang said:**
> There is no such function.

That's dissapointing :(

So, if such a function doesn't exist, is there any way to build it?

---

### Post by Wybiral on 2009-01-19
Write your own abstraction for the array... Some class that stores the allocated size when it's constructed.

Or, use the STL. You said you want vector sizes, right? You know they have a ".size()" method? Or did you mean an array of some type "vector"

PS, pointers are not always arrays, you should specify that you mean a pointer to a dynamically allocated array.

---

### Post by Subespaciovectorial on 2009-01-19
> **Wybiral said:**
> 
Or did you mean an array of some type "vector"?

Sorry that's what I mean. I the user gives a list of vectors to the function (list has, for example, 23 elements of my own class).

> **Wybiral said:**
> 
PS, pointers are not always arrays, you should specify that you mean a pointer to a dynamically allocated array.

I know the difference, that's because I'm talking about lists.

For the people who know maths, I'm trying to create a boolean funcion "LI" that takes a list of vectors (my vectors, not c++ vectors) and determines if they are linearly independent. The program doesn't know how long is the dimension of the subspace. If you have a 5-dimensional space, you can create a 3-dimensional only if the 3 base-vectors are LI. So you have vectors of size 5, and an amount of vectors equal to 3. If the user creates a list of the three vectors, can I know how many vectors does the list have?

---

### Post by Wybiral on 2009-01-19
Your users either need to pass the lengths in or use a better representation of the lists than arrays (such as an STL container, which will have some method for grabbing the size). Having it accept an STL container would probably be the most idiomatic C++ way of doing it.

---

### Post by Subespaciovectorial on 2009-01-19
> **Wybiral said:**
> Having it accept an STL container would probably be the most idiomatic C++ way of doing it.

That sounds very interesting. Can you tell me about STL containers? I didn't know about them.

---

### Post by Wybiral on 2009-01-19
If you're going to code in C++, knowing the STL well is practically a must: [http://www.cplusplus.com/reference/stl/](http://www.cplusplus.com/reference/stl/)

---

### Post by JupiterV2 on 2009-01-19
> **wybiral said:**
> if you're going to code in c++, knowing the stl well is practically a must: [http://www.cplusplus.com/reference/stl/](http://www.cplusplus.com/reference/stl/)

+1

---

### Post by nvteighen on 2009-01-20
FYI: The only reason why strlen() is possible in C (because it's a C function, not a C++) is because strings are required to be NULL-terminated... so it can detect the string's end by checking where the '\0' character is.

Of course, if your string is not NULL-terminated, strlen() results in undefined behaivor.

That's the "problem" with C and C++: you have to be aware of these implementation details in order to use these languages correctly.

---

### Post by Subespaciovectorial on 2009-01-22
Thanks for the advices guys.

---

