---
title: "Can't use assignment operator to set contents of a char[] member of a class"
date: 2009-06-07
forum: Programming Talk
---

### Post by CC_machine on 2009-06-07
```

class GUINum 
{
 public:
  int x, y;
  float value;
[B]  char prefixtext[20];
  char suffixtext[20];[/B]
  void update(); 
};

```

Later on i have

```

  GUINum GUIForceNum;

[B]  GUIForceNum.prefixtext = "KeyForce: ";
  GUIForceNum.suffixtext = "*vel N";[/B]

```

It complains with:
```

main.cpp:57: error: incompatible types in assignment of &#8216;const char [11]&#8217; to &#8216;char [20]&#8217;
main.cpp:58: error: incompatible types in assignment of &#8216;const char [7]&#8217; to &#8216;char [20]&#8217;

```

I understand that a const char and a char are different, but why doesn't the assignment operator convert them as it does with strings and chars? I've tried a load of ways around this, but can't seem to make it work. I can't comprehend why I can set the contents of a local char[20] but not one that's a public member of a class.

:(

Thanks in advance for any help, I'm sure I'm missing something simple :)

---

### Post by MadCow108 on 2009-06-07
this kind of statement is actually illegal:
char * str = "const char";
as it are two different types char and const char.
For some reason (I think historic) it works.

In case of classes the compiler is probably more strict.
also this doesn't work:
char test[20];
test="blabla";


this should be the correct solution:
```

strncpy(GUIForceNum.prefixtext,"KeyForce: ",20);
strncpy(GUIForceNum.suffixtext,"*vel N",20);

```

(or just use strings)

---

### Post by dwhitney67 on 2009-06-07
> **MadCow108 said:**
> ...

(or just use strings)

+1.  Just use STL strings.

---

### Post by Lux Perpetua on 2009-06-08
> **MadCow108 said:**
> 
In case of classes the compiler is probably more strict.
also this doesn't work:
char test[20];
test="blabla";
It has nothing to do with classes. In C or C++, the name of an array is not an lvalue: it cannot be assigned to.

---

### Post by noway2 on 2009-06-08
I think the problem is more fundamental.

When you declare a variable of type char, you are indicating that its contents may change.  Similarly, if you declare a char array, as in prefixtext[20], the contents of the array may change.

Now, in your class, you are in effect using pointers to point to the first element of this array and place const data there, where const indicates that the data can't change.

This is at conflict with your data type, which says that the array will point to something that CAN change.

The two options I see are to either declare the initializer at compile time and leave it const, or use a form of strcpy to copy the const data to the changeable variable.

---

### Post by Habbit on 2009-06-08
> **MadCow108 said:**
> this kind of statement is actually illegal:
char * str = "const char";
as it are two different types char and const char.
For some reason (I think historic) it works.


In old compilers, string literals were of type char*, not const char*. However, once compilers started compacting string literals (i.e. saving only one copy of a literal repeated many times in a program), they decided to make them const char* so that hell would not break loose. I don't know whether the rule "string literals are const char*" was in the standard to begin with or was added in later revisions, but it was not until the early 2000s that compilers started actually enforcing it because there was a lot of old code that had to be changed.

Nevertheless, the name of an array with auto storage (i.e. not a malloc'ed or new[]'ed array) is not an lvalue. The right way to fill it with data is with a loop or, if you have a source array, with memcpy and friends like str(n)cpy for char arrays.

---

### Post by Lux Perpetua on 2009-06-09
> **noway2 said:**
> I think the problem is more fundamental.

When you declare a variable of type char, you are indicating that its contents may change.  Similarly, if you declare a char array, as in prefixtext[20], the contents of the array may change.

Now, in your class, you are in effect using pointers to point to the first element of this array and place const data there, where const indicates that the data can't change.

This is at conflict with your data type, which says that the array will point to something that CAN change.

The two options I see are to either declare the initializer at compile time and leave it const, or use a form of strcpy to copy the const data to the changeable variable.I'm not sure what you're trying to say, but I think you're implying that **char prefixtext[20]** and **char suffixtext[20]** are effectively pointers to char, which is not correct. That's the whole point: they are arrays, not pointers, and in particular, you don't get to choose what they point to. Const has nothing to do with it.

---

### Post by Arppa on 2009-06-10
> **Lux Perpetua said:**
> I'm not sure what you're trying to say, but I think you're implying that **char prefixtext[20]** and **char suffixtext[20]** are effectively pointers to char, which is not correct. That's the whole point: they are arrays, not pointers, and in particular, you don't get to choose what they point to. Const has nothing to do with it.

Well, arrays are pointers. If we have an array **char prefixtext[20]**, the name of the array, prefixtext, is only a pointer to the first element of the array. When we assign value to **prefixtext[n]**, we could just as well write ***(prefixtext+n)**. (This also explains why the index of the first element in an array is 0 and not 1)

---

### Post by Habbit on 2009-06-10
> **Arppa said:**
> Well, arrays are pointers. If we have an array **char prefixtext[20]**, the name of the array, prefixtext, is only a pointer to the first element of the array. When we assign value to **prefixtext[n]**, we could just as well write ***(prefixtext+n)**. (This also explains why the index of the first element in an array is 0 and not 1)
Indeed, but the variable naming the array does not behave as a normal pointer: if you say "int myarray[5]" it would be illegal to say "myarray++", while if you had said "int* myarray = new int[5]", the previous increment operator would have been valid (and advanced myarray to point to the second item in the array). In other words, "int myarray[5]" behaves (in assignment contexts) as "int * const myarray = new int[5]": you cannot reassign it to point somewhere else. Notice that this does not affect constructs like "*(myarray+1)" because you are not modifying myarray in that statement.

---

### Post by noway2 on 2009-06-19
> **Lux Perpetua said:**
> I'm not sure what you're trying to say, but I think you're implying that **char prefixtext[20]** and **char suffixtext[20]** are effectively pointers to char, which is not correct. That's the whole point: they are arrays, not pointers, and in particular, you don't get to choose what they point to. Const has nothing to do with it.

I am a bit behind here, but to clarify what I meant:

The assignment statement is attempting to assign data of type const char to a variable of type char.  When an object is of type const, it is an indication that it can not be changed.  For example, if it code for an embedded system that is running out of FLASH memory.  A variable of type char, however, is a reference to an item that can be changed.

Depending on how the assignments are handled by the compiler, such as if it treats an array as a pointer to the first element of the array, the error message could be indicating that an attempt was made to reference something that can not be changed by a variable that allows change, which can lead to unpredictable results.  In other words, it is illegal to POINT To a const object with a non const object because it is not type safe.

If I remember correctly, the book Thinking in C++ had a really good discussion on this subject and described how this function is much more tightly regulated in C++ than it was in plain C.

---

