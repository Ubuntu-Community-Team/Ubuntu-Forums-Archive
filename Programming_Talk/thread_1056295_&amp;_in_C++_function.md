---
title: "&amp; in C++ function"
date: 2009-01-31
forum: Programming Talk
---

### Post by cybo on 2009-01-31
i'm reading a book on C++ and there i found a declaration of the following copy constructor:

stack::stack(const stack& old_stack)

1) can someone explain why there is an '&' there? i know that '&' means grab address of the variable, but i have never seen it used in the function declaration.

2) the book is somewhat unclear what a copy constructor is. can someone give a more clear explanation of it?

thank you in advance.

---

### Post by nitro_n2o on 2009-01-31
This is C++ reference, slightly different than the idea of grabbing an address in C

you can start knowing more about it from here [http://en.wikipedia.org/wiki/Reference_(C%2B%2B](http://en.wikipedia.org/wiki/Reference_(C%2B%2B)) 


check this out for the copy constructor [http://www.fredosaurus.com/notes-cpp/oop-condestructors/copyconstructors.html](http://www.fredosaurus.com/notes-cpp/oop-condestructors/copyconstructors.html)

---

### Post by thelamb on 2009-01-31
The & in function arguments means 'pass argument by reference'. 
Normal arguments(without the &) are passed by value. Let me try to explain the difference:

If you pass an argument by value the following happens:
```

void byValue( int Bar )
{ // The value of Foo(0) is copied to Bar(and here the copy constructor is called). Foo will be exactly the same after this function returns.
[INDENT]Bar++;[/INDENT]
}

void byRef( int& Bar )
{ // Bar is now exactly the same as Foo, so any operation on Bar will effect Foo.
[INDENT]Bar++;[/INDENT]
}

void byConstRef( const int& Bar )
{
[INDENT]Bar++; // Not allowed, Bar is a const ref![/INDENT]
}

int main()
{
[INDENT]int Foo = 0;
byValue( Foo );// Foo is still 0 after this

byRef( Foo ); // Foo is now 1

byConstRef( Foo ); // The function is not able to change Foo, so it is still 0 after this. [/INDENT]

}


```

Now what is the advantage of byref? ... the copy constructor is not called ;) so in essence it is faster(especially for large objects).

The downside is that sometimes you don't want 'Foo' to change when you pass it to a function(it is considered bad programming to assume that the 'byRef' function doesn't change Foo - if you come back to your code a year later will you still remember this? What if you change the 'byRef' at that point and don't realise that the Foo variable is changed now aswell).
That is what 'const' is for in this case, if you pass an argument with const int& then you cannot change anything to this argument in the function, so this is mostly used when passing large objects to a function.

Hope this made things a bit clearer.

---

### Post by shadylookin on 2009-01-31
an & means you're passing it a reference

a copy constructor is supposed to take an object and make a copy of it

for instance 

Object object1();

Object object2(object1); 

means object 2 should be a clone of object1

---

### Post by monkeyking on 2009-02-01
Or smaller example is a swap function.

[PHP]
void myswap1(int a, int b){ 
\\this will make a copy of the original values
\\ a,b are local to this function
  int tmp = a;
  a = b;
  b = tmp;
}
void myswap2(int& a, int& b){
  int tmp = a;
  a = b;
  b = tmp;
}
int main(){
  int a=5;
  int b=7;
  myswap1(a,b);\\doesn't change the valus of a or b
  myswap2(a,b);\\will change the values.
  return 0;

}



[/PHP]

---

### Post by cybo on 2009-02-01
thank you everyone. i think i got it.

---

