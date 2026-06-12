---
title: "C compilation"
date: 2011-08-18
forum: Programming Talk
---

### Post by shashanksingh on 2011-08-18
This is not a practical doubt, these are the kind of questions that we need to know as supposedly "C Aptitude" and thus i need to be clear with it..#-o

Here are two snippets of code...

```

main()
{
        display(25);
        return 0;
}

float display(int x)
{
        printf("Display %d",25 );
}
```

```

main()
{
        display(25);
        return 0;
}

void display(int x)
{
        printf("Display %d",25 );
}
```

Now, I suppose the compiler when finds the call to display the first time does not have a definition yet, and assumes it to be 

int display();

and as in both the snippets, the return type of my succeeding definition does not match the above. (I was esxpecting a compile error)
However, the second one compiles with warnings whereas the first one gives an error.....

---

### Post by nickleboyblue on 2011-08-18
The second one probably shouldn't compile, I have no idea why it would.  In both cases, your display function is not yet defined or mentioned in your program when you try to use it.  In other languages, you might be able to get away with it.  Like you said, the program doesn't know your functions yet when it tries to execute main().

If you need help with this sort of thing, please post at least a little bit of your compile errors/warnings to give us at least some idea of what happened.

For those non-programmers that are a bit more confused, all code needs to be loaded into memory before the main() function can be executed, and all code needs to be aware of any other code it uses or calls in a function call.  This might not be the best explanation for why the first one wouldn't compile, but it describes at least a little about what is actually going on when a program gets compiled.

---

### Post by karlson on 2011-08-18
> **shashanksingh said:**
> This is not a practical doubt, these are the kind of questions that we need to know as supposedly "C Aptitude" and thus i need to be clear with it..#-o

Here are two snippets of code...

```

main()
{
        display(25);
        return 0;
}

float display(int x)
{
        printf("Display %d",25 );
}
```

```

main()
{
        display(25);
        return 0;
}

void display(int x)
{
        printf("Display %d",25 );
}
```

Now, I suppose the compiler when finds the call to display the first time does not have a definition yet, and assumes it to be 

int display();

and as in both the snippets, the return type of my succeeding definition does not match the above. (I was esxpecting a compile error)
However, the second one compiles with warnings whereas the first one gives an error.....

I am still not sure what the question is?

The reason the 1st snippet doesn't compile is because you are returning a float with no return statement.

---

### Post by Arndt on 2011-08-18
> **karlson said:**
> I am still not sure what the question is?

The reason the 1st snippet doesn't compile is because you are returning a float with no return statement.

No, it is not. When you use -Wall, gcc says "warning: control reaches end of non-void function", but it is only a warning.

---

### Post by shashanksingh on 2011-08-18
> **nickleboyblue said:**
> The second one probably shouldn't compile, I have no idea why it would.  In both cases, your display function is not yet defined or mentioned in your program when you try to use it.  In other languages, you might be able to get away with it.  Like you said, the program doesn't know your functions yet when it tries to execute main().

If you need help with this sort of thing, please post at least a little bit of your compile errors/warnings to give us at least some idea of what happened.

For those non-programmers that are a bit more confused, all code needs to be loaded into memory before the main() function can be executed, and all code needs to be aware of any other code it uses or calls in a function call.  This might not be the best explanation for why the first one wouldn't compile, but it describes at least a little about what is actually going on when a program gets compiled.


Here's what gcc -Wall <file> gives..

When I compile with void display(), I get this:

```

x.c:3:1: warning: return type defaults to &#8216;int&#8217;
x.c: In function &#8216;main&#8217;:
x.c:5:4: warning: implicit declaration of function &#8216;display&#8217;
x.c: At top level:
x.c:9:6: warning: conflicting types for &#8216;display&#8217;
x.c:5:4: note: previous implicit declaration of &#8216;display&#8217; was here
``` 

Whereas when I compile with float display(), I get :

```

x.c:3:1: warning: return type defaults to &#8216;int&#8217;
x.c: In function &#8216;main&#8217;:
x.c:5:4: warning: implicit declaration of function &#8216;display&#8217;
x.c: At top level:
x.c:9:7: error: conflicting types for &#8216;display&#8217;
x.c:5:4: note: previous implicit declaration of &#8216;display&#8217; was here
x.c: In function &#8216;display&#8217;:
x.c:12:1: warning: control reaches end of non-void function
```

SO, basically my confusion is, why only a warning with void, and an error with float; while both are not the correct return types.

---

### Post by MadCow108 on 2011-08-18
the compiler always assumes int when no return type is given.
in the first one the implicit declaration is in principle compatible with the conflicting one, both take a 4byte object and return a 4 byte object
It is still very wrong of course.

the second one returns nothing which is incompatible with the implicit declaration so it errors out.

always take these warnings seriously and tell the compiler what type this function is.
```

/* forward declaration */
void display(int x);

int main(int argc, char * argv[])
{
        display(25);
        return 0;
}

void display(int x)
{
        printf("Display %d",25 );
}
```

---

### Post by shashanksingh on 2011-08-18
> **MadCow108 said:**
> the compiler always assumes int when no return type is given.
in the first one the implicit declaration is in principle compatible with the conflicting one, both take a 4byte object and return a 4 byte object
It is still very wrong of course.

the second one returns nothing which is incompatible with the implicit declaration so it errors out.

always take these warnings seriously and tell the compiler what type this function is.
```

/* forward declaration */
void display(int x);

int main(int argc, char * argv[])
{
        display(25);
        return 0;
}

void display(int x)
{
        printf("Display %d",25 );
}
```

This is one of those questions that are meant to be this way, to test the aptitude of the programmer.

As you said, the float and int should be somewhat compatible according to the argument. But that's what is more curious, the float gives an ERROR while a void still goes through with just a WARNING......

---

### Post by unknownPoster on 2011-08-18
> **shashanksingh said:**
> This is one of those questions that are meant to be this way, to test the aptitude of the programmer.

As you said, the float and int should be somewhat compatible according to the argument. But that's what is more curious, the float gives an ERROR while a void still goes through with just a WARNING......

No they aren't. An int is not a float so they are not "somewhat compatible."

Try storing a float such as 6.89 as an int and see what happens.

YOU as the programmer are expected to know what types your functions accept as parameters and what they return.

---

### Post by Bachstelze on 2011-08-18
> **shashanksingh said:**
> This is one of those questions that are meant to be this way, to test the aptitude of the programmer.

As you said, the float and int should be somewhat compatible according to the argument. But that's what is more curious, the float gives an ERROR while a void still goes through with just a WARNING......

This is because the "default" is void, not int.

> 6.5.2.2 Function calls

5. If the expression that denotes the called function has type pointer to function returning an
object type, the function call expression has the same type as that object type, and has the
value determined as specified in 6.8.6.4. **Otherwise, the function call has type void.** If
 an attempt is made to modify the result of a function call or to access it after the next
sequence point, the behavior is undefined.


And yes, float and int are not compatible, as demonstrated by

```
firas@aoba ~ % cat test.c       
int display(int);

int main(void)
{
        display(25);
        return 0;
}

float display(int x)
{
        printf("Display %d",25 );
}
firas@aoba ~ % cc -o test test.c
test.c:9:7: error: conflicting types for &#8216;display&#8217;
test.c:1:5: note: previous declaration of &#8216;display&#8217; was here
test.c: In function &#8216;display&#8217;:
test.c:11:9: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;

```

> **unknownPoster said:**
> No they aren't. An int is not a float so they are not "somewhat compatible."

That argument is a bit weak...

> 6.2.7 Compatible type and composite type

1 Two types have compatible type if their types are the same. Additional rules for
 determining whether two types are compatible are described in 6.7.2 for type specifiers,
  in 6.7.3 for type qualifiers, and in 6.7.5 for declarators. 46)

[...]

46) Two types need not be identical to be compatible.


---

