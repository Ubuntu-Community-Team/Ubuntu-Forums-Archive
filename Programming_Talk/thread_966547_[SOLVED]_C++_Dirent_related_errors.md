---
title: "[SOLVED] C++ Dirent related errors"
date: 2008-11-01
forum: Programming Talk
---

### Post by Stoodle on 2008-11-01
I'm getting
```
 error: ‘d_name’ was not declared in this scope
```
for 
```
 fileName = *fileInfo.*d_name;
```
fileName is a string. And fileInfo pointer to a dirent structure.  d_name is a character array.

I'm also getting
```
request for member ‘d_name’ in ‘fileInfo’, which is of non-class type ‘dirent*’
```
for
```
cout << "fileInfo.d_name" << *fileInfo.d_name << "\n";
```
I think it's just a syntax error but I can't figure out what's wrong for the life of me. I'd appreciate if you guys told me what you think is wrong.

---

### Post by issih on 2008-11-01
I'm making some guesses here. Mainly that d_name is a member variable of the Dirent class (N.B. classes really should be named with capital letters to avoid potential conflict with inbuilt functions).

If that assumption is right, I think most of your problems come from your dereferencing of pointers.

```
 fileName = *fileInfo.*d_name;
```

here you attempt to dereference both fileinfo (a pointer to a Dirent class) and d_name. This can't be right, and because of the * in front of d_name I suspect the compiler is looking for a pointer named d_name at the same scope level as the fileName and fileInfo objects.

You could do it like this:

```
fileName = (*fileInfo).d_name
```

I'm pretty sure about the precedence order of the operators here so I'm fairly certain the brackets are necessary, I'd definitely use anyway, for clarity.

Alternatively do it like this:

```
fileName = fileInfo->d_Name
```

where the -> operator means step into the class held by this pointer.

As for your second problem I think that again you have dereferencing problems

```
cout << "fileInfo.d_name" << *fileInfo.d_name << "\n";
```

here the compiler is following the method call before dereferencing the fileInfo pointer, so its looking for a d_Name variable on a pointer to a Dirent Variable rather than in the class itself.

Again either using brackets or the -> operator should sort you out

Hope that helps

---

### Post by cl333r on 2008-11-01
For the filename issue, just use
char *filename
instead of
string filename

d_name shouldn't have a star sign infront of it.
[http://www.gnu.org/software/libtool/manual/libc/Simple-Directory-Lister.html#Simple-Directory-Lister](http://www.gnu.org/software/libtool/manual/libc/Simple-Directory-Lister.html#Simple-Directory-Lister)

---

### Post by issih on 2008-11-01
Can't agree there, c++ std strings are quite happy to be initialised from char* arrays, the compiler does all the implicit conversions for you.

---

### Post by rnodal on 2008-11-01
Try
> fileName = fileInfo->d_name;

-r

---

### Post by Stoodle on 2008-11-01
Thanks guys. Doing (*fileInfo).d_name or fileInfo->d_name worked. I'm not sure why what I was doing was wrong though.  Also, is anyone else noticing that ubuntuforums.org is screwed up right now? There are no images and the background is just white.

---

### Post by dribeas on 2008-11-02
> **Stoodle said:**
> Thanks guys. Doing (*fileInfo).d_name or fileInfo->d_name worked. I'm not sure why what I was doing was wrong though.  Also, is anyone else noticing that ubuntuforums.org is screwed up right now? There are no images and the background is just white.

This code:
```

fileName = [COLOR="Blue"]*[/COLOR]fileInfo[COLOR="Red"].*[/COLOR]d_name;

```

uses a dereference operator ([COLOR="Blue"]*[/COLOR]) and a pointer to member ([COLOR="Red"].*[/COLOR]) operator, the meaning of which is complex. I will start with the basics: plain pointers.

```

struct X
{
   int x1;
   int x2;
   int *xp;
};
int main()
{
   int i = 10;
   X x;

   x.x1 = 1;
   x.x2 = 2;
   x.xp = &i; // pointer points to i

   X *ptr = &x; // pointer to x

   // Added code from below
}

```

That is the basic code, now some operations:

Access x1 attribute through the pointer

```

   (*ptr).x1 = 5;
   ptr->x1 = 5; 

```

The pointer ptr is dereferenced to get to an X instance. Member attribute x1 is obtained. The effect is changing the value of x.x1. Both syntaxes are equivalent.

Access 'i' through x and ptr:

```

   *x.xp = 20; // x.xp is a pointer to i
   *(*ptr).xp = 20; // dereference as above to get to the X object
                    // then dereference the xp attribute
   *ptr->xp = 20;   // equivalent to above

```

As you can see, multiple dereferences are all used with the * to the left.

From here on is quite advanced, if you are a beginner consider just browsing or even skipping this part. Just know that .* and ->* have special meanings and that for plain pointer dereferencing you should always do it from the left.

The syntax used above (x.*y) is the dereference operator for member pointers, which are a complete different story. Pointers to members allow you to create a variable that, when applied to an object of the defined class through the .* or ->* operators will be the equivalent to a plain pointer to the data element in that particular instance of the class. I already said it was not for the faint of heart, didn't I?

They represent (so to say) the offsets that the compiler must apply to get to a particular member attribute/method once it has an instance of the class.

Maybe it is easier with an example:
```

// X defined as above
int main()
{
   X x;
   X x2;
   int X::* ptr; // [1]

   ptr = &X::x1; // [2]
   x.*ptr = 5; // [3]

   ptr = &X::x2; // [4]
   x.*ptr = 5; // [5]
   x2.*ptr = 5; // [6]
}

```

In [1] ptr is defined as a pointer to a member attribute of X of type int. In [2] it gets the reference of x1 member of class X, this means that the line in [3] modifies x.x1 to get 5. In [4] the pointer gets the address of the x2 member of X, so that [5] modifies x.x2, even if [3] and [5] are the exact same line, the effect is different. In [6] the same pointer is used, but as the left hand side of the .* is x2, the change is equivalent to x2.x2 = 5.

Now, I have never seen this in production code, but you can see each so often the equivalent code to call member functions.

```

class X
{
public:
   void f();
   void g();
   void h();
};

void apply( void (X::* ptr) (void), X& o )
{
   o.*ptr();
}
// easier to read:
// typedef void (X::*) (void) ptrType;
// void apply( ptrType ptr )

int main()
{
   X x;
   apply( &X::f, x ); // equivalent to a call to x.f()
   apply( &X::g, x ); // ... x.g()
}

```

This is a rather simple example, but this allows the simulation of a function pointer in C where the function is indeed a member method (C function pointer syntax cannot be used with members).

Your initial syntax:

```

fileName = *fileInfo.*d_name;

```

really means: dereference the pointer obtained after dereferencing member pointer 'd_name' when applied to 'fileInfo'. The compiler is trying to find a member pointer by the name of 'd_name' that is not found, and thus the ''d_name not defined'' error.

Anyway, most people never get to see or use this language functionality, so whether you understood it or not, you won't probably need it.

---

