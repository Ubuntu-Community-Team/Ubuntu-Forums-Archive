---
title: "return by value"
date: 2010-10-07
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-07
You know it's been a long time and on totally different compilers, but one thing I'm really pleased with in g++, the Linux C++ compiler is how it actually handles "return by value" properly: You see once upon a time if you wrote...
[php]
my_class func() {
     my_class Result;
     ... code to fill build the result...
     return Result;
}
[/php]
... then it would run a constructor for the local variable "Result"... it would then do all the code in the function and when it get's to *return* it did a copy constructor to the destination that was specified in the calling code.

So like if *my_class* above contained some huge blob (binary large object) of data then it would all get copied, and if inside func() various pointers had been initialized to said item then they would all become invalid for the copy!

Anyway, with all these new languages like Java being used for didactic purposes... languages that only handle references and take garbage collection for granted... I was wondering whether anyone thinks that teaching an understanding of such concepts even has any value at all?

---

### Post by PaulM1985 on 2010-10-07
What about the cases when you actually want it to return a copy, rather than return a reference?  

As an example, if you have an internal layer and a user interface layer and your user interface gets a list of objects from the internal layer to display to the user, do you want it to get a copy of the internal objects or an actual reference to the internal objects?

By returning a reference to the internal objects the interface is then able to not only make changes to the list (maybe remove one of your internal objects which may invalidate links within your internal system) but would have a reference to each object in the list, so the interface would be able to make physical changes to the internal objects.

I think it is important to know the difference between returning values and returning references.  Returning values may be expensive, but you can be sure that one component won't be invalidating the internals of another.

I am not saying that returning references is wrong, I am just saying there are instances when it would be better and safer to return copies.

Paul

---

### Post by nvteighen on 2010-10-07
> **worksofcraft said:**
> You know it's been a long time and on totally different compilers, but one thing I'm really pleased with in g++, the Linux C++ compiler is how it actually handles "return by value" properly: You see once upon a time if you wrote...
[php]
my_class func() {
     my_class Result;
     ... code to fill build the result...
     return Result;
}
[/php]
... then it would run a constructor for the local variable "Result"... it would then do all the code in the function and when it get's to *return* it did a copy constructor to the destination that was specified in the calling code.

So like if *my_class* above contained some huge blob (binary large object) of data then it would all get copied, and if inside func() various pointers had been initialized to said item then they would all become invalid for the copy!

Anyway, with all these new languages like Java being used for didactic purposes... languages that only handle references and take garbage collection for granted... I was wondering whether anyone thinks that teaching an understanding of such concepts even has any value at all?

My opinion on this is the following:

1. Languages that are pass-by-reference by default are better for beginners because in the real world, you usually don't copy stuff each time you do some action to something... except when copying something, of course.

2. But a programmer has to know how a computer works because even we, those who love subtly abstracted high-level programming in Common Lisp :D, use them... and you have to know that a computer actually knows about chunks of data and that, as there's something called a stack, in a lower-level there's something called pass-by-value that also have to know.

---

### Post by worseisworser on 2010-10-07
> **worksofcraft said:**
> You know it's been a long time and on totally different compilers, but one thing I'm really pleased with in g++, the Linux C++ compiler is how it actually handles "return by value" properly: You see once upon a time if you wrote...
[php]
my_class func() {
     my_class Result;
     ... code to fill build the result...
     return Result;
}
[/php]
... then it would run a constructor for the local variable "Result"... it would then do all the code in the function and when it get's to *return* it did a copy constructor to the destination that was specified in the calling code.

So like if *my_class* above contained some huge blob (binary large object) of data then it would all get copied, and if inside func() various pointers had been initialized to said item then they would all become invalid for the copy!

Anyway, with all these new languages like Java being used for didactic purposes... languages that only handle references and take garbage collection for granted... I was wondering whether anyone thinks that teaching an understanding of such concepts even has any value at all?

The problem you describe and some, any, pass-by semantic isn't really related. If copy your object in a half-arsed fashion (and to make this clear; you can do this regardless of what the default pass-by semantics of some language is) you will get trouble.

So to answer your question; yes, of course it makes sense learning this because of course one also copy in languages that has pass by reference.

---

### Post by worksofcraft on 2010-10-07
> **PaulM1985 said:**
> What about the cases when you actually want it to return a copy, rather than return a reference?  

As an example, if you have an internal layer and a user interface layer and your user interface gets a list of objects from the internal layer to display to the user, do you want it to get a copy of the internal objects or an actual reference to the internal objects?

By returning a reference to the internal objects the interface is then able to not only make changes to the list (maybe remove one of your internal objects which may invalidate links within your internal system) but would have a reference to each object in the list, so the interface would be able to make physical changes to the internal objects.

I think it is important to know the difference between returning values and returning references.  Returning values may be expensive, but you can be sure that one component won't be invalidating the internals of another.

I am not saying that returning references is wrong, I am just saying there are instances when it would be better and safer to return copies.

Paul

I agree fully :)

The code I quoted is in fact not returning a reference. It is returning by value... **and it does it without copying**... It's quite clever and constructs what appears to be a local variable actually directly in the result space.

What I don't know is if it will always manage to do that or if it must sometimes still do the copy from internal local variable to final destination.

---

### Post by worksofcraft on 2010-10-07
... see here this puts it to the test and even prevents it from being some kind of special case optimization from inlining:
[php]

#include <stdio.h>

struct my_blob {
	int BigifyMe[50];
	my_blob() {
		printf("constructing my_blob at %p\n", this);
	}
	~my_blob() {
		printf("destructing my_blob from %p\n", this);
	}
	// copy constructor
	my_blob(const my_blob &Blob) {
		printf("copy construction from %p to %p\n", &Blob, this);
	}
	// copy assignment
	my_blob & operator= (const my_blob &Blob) {
		printf("transfer copy from %p to %p\n", &Blob, this);
		return *this;
	}
};

typedef my_blob (* volatile foxy)(); // prevent inline expansion

my_blob make_blob() {
	my_blob Blob;
	// do whatever with the blob
	for (int I = 0; I < 50; ++I) Blob.BigifyMe[I] = I;
	return Blob; // by value
}

int main() {
	foxy Fox = make_blob;
	my_blob NewBlob = (*Fox)();
	return 0;
}
[/php]
and look... only one instance is ever created and destroyed and no assignmnet or copy constructors are involved!
```

$> g++ blob.cc
$> ./a.out
constructing my_blob at 0x7fffe9f81cf0
destructing my_blob from 0x7fffe9f81cf0
$>

```

---

### Post by worseisworser on 2010-10-07
Uh, why would any copying or assignments of my_blob be done here in the first place? You are not passing anything, nor are you copying anything. Fox refers to the make_blob *function*.

```

#include <stdio.h>
#include <iostream>

using namespace std;


struct MyBlob {
  int bigify_me[50];

  MyBlob() {
    printf("constructing MyBlob at %p\n", this);
  }

  ~MyBlob() {
    printf("destructing MyBlob from %p\n", this);
  }

  // copy constructor
  MyBlob(const MyBlob &blob) {
    printf("copy construction from %p to %p\n", &blob, this);
  }

  // copy assignment
  MyBlob & operator= (const MyBlob &blob) {
    printf("transfer copy from %p to %p\n", &blob, this);
    return *this;
  }
};


MyBlob makeBlob() {
  MyBlob blob;
  for(int i = 0; i < 50; ++i)
    blob.bigify_me[i] = i;
  return blob;
}


MyBlob passAndReturn(MyBlob some_blob){
  return some_blob;
}


int main() {
  MyBlob blob = makeBlob();
  MyBlob copy_of_blob = blob;
  cout << endl;

  cout << "passAndReturn:" << endl;
  MyBlob returned_blob = passAndReturn(blob);

  cout << endl <<  "..end.." << endl;
  return 0;
}

```

```

lnostdal@blackbox:~/programming/c$ g++ -g -Wall -o blah blah.cpp && ./blah
constructing MyBlob at 0x7fff56e97840
copy construction from 0x7fff56e97840 to 0x7fff56e97770

passAndReturn:
copy construction from 0x7fff56e97840 to 0x7fff56e975d0
copy construction from 0x7fff56e975d0 to 0x7fff56e976a0
destructing MyBlob from 0x7fff56e975d0

..end..
destructing MyBlob from 0x7fff56e976a0
destructing MyBlob from 0x7fff56e97770
destructing MyBlob from 0x7fff56e97840
lnostdal@blackbox:~/programming/c$ 

```

PS: I've never seen anyone use a combination of ThisStyle for variables, this_style for types and this_style for functions before. *sigh*  ..I'm _so_ glad I'm not a "real programmer".

edit: oh, wait; you're talking about what happens (or does not happen given <some compiler>) in makeBlob? i.e., no copy constructor called? why is this interesting?  [http://en.wikipedia.org/wiki/Return_value_optimization](http://en.wikipedia.org/wiki/Return_value_optimization)

IMHO I find it silly. If I care about performance I'd explicitly do this, if I didn't care for performance I would certainly not want undefined behavior (what happens depends on the compiler). I.e., both cases are fail. Short talk here: [http://yosefk.com/c++fqa/ctors.html#fqa-10.9](http://yosefk.com/c++fqa/ctors.html#fqa-10.9)

---

### Post by worksofcraft on 2010-10-07
> **worseisworser said:**
> 
IMHO I find it silly...

I don't think you understand the code I wrote.
Perhaps this makes it clearer:
[php]

#include <stdio.h>

struct my_blob { 
    my_blob *Self; 
    my_blob() {
        Self = this; 
        printf("constructing my_blob at %p\n", this); 
    }
    ~my_blob() { 
        printf("destructing my_blob from %p\n", this); 
    }
    int was_copied() {
         if (Self != this) printf("I'm a copy\n");
         else printf("I'm the original that make_blob made\n");
         return (Self != this);
    }
}; 

typedef my_blob (* volatile foxy)(); // prevent inline expansion 

my_blob make_blob() { 
    my_blob Blob; 
    printf("hello I'm make_blob and I'm about to return my value!\n");
    return Blob; // by value 
} 

int main() { 
    foxy Fox = make_blob; 
    my_blob NewBlob = (*Fox)(); 
    return NewBlob.was_copied(); 
} 
[/php]
```

$> g++ newblob.cc
$> ./a.out
constructing my_blob at 0x7fff9caaf370
hello I'm make_blob and I'm about to return my value!
I'm the original that make_blob made
destructing my_blob from 0x7fff9caaf370

```

... as for conventions and styles of capitalization, I'm afraid mine predates what you use and I see no reason to change it.

However, next time you're in your time machine do pop back and explain to K&R that they need to capitalize types like "int" and "float" and do educate them into rewriting the standard library functions all in CamelCase while you are at it.

---

### Post by Simian Man on 2010-10-07
This is compiler optimization 101, something most compilers will do if they can.  I really don't think this is an interesting topic outside of compiler writers.

---

### Post by dwhitney67 on 2010-10-07
> **worksofcraft said:**
> 
... as for conventions and styles of capitalization, I'm afraid mine predates what you use and I see no reason to change it.

How long have you been in the s/w profession?  I've been in it for some time myself, and I have been able to adapt to new, preferred, styles.

---

### Post by CptPicard on 2010-10-07
> **worksofcraft said:**
> 
The code I quoted is in fact not returning a reference. It is returning by value... **and it does it without copying**... It's quite clever and constructs what appears to be a local variable actually directly in the result space.

What I don't know is if it will always manage to do that or if it must sometimes still do the copy from internal local variable to final destination.

As Simian Man said... this is about the C++ [return value optimization]("http://en.wikipedia.org/wiki/Return_value_optimization"), and only indirectly related to pass semantics and whether you need to "understand" them.

The latter paragraph here condenses some of my feelings about C++ and the way it handles the combination of low level stuff and higher level semantics (note: it really is different semantics, not just "hiding library calls") added on top -- a bit poorly. After all, this is a case of C++-specific interactions between low level value return, copy constructor, object destructors and the assignment operator -- and in the end, a magical bypass of everything under certain conditions. "Not really knowing" *when* the compiler will manage to RVO, when the alternative is internal exploding pointers, seems to me to be totally unacceptable.

Actually, I think dribeas pointed out a long time ago that RVO is in the standard, however, you still need to be able to tell when it will happen if you want to trust it (answer: it will happen if the compiler can figure out a unique value on the call stack that will always end up being returned). Having to "know" something like this  is again IMO dangerous in such a simple feature as returning a value from a function... when I was learning C++ years ago, "how to return large objects from a function and if I must always resort to reference counting" was a a thing that stumped me for a long, long time!

Personally, I can't quite accept the argument that "a good programmer should just know the tool". Programming languages are supposed to be *good* tools, and it is trivially obvious that for example INTERCAL doesn't fit the bill. Also, I fail to understand the general benefit one derives from understanding this particular quirk of C++, although you most certainly *must* if you program C++.

Now, if you want an opinion regarding the original question... first of all, when it comes to the memory management point, one has to understand that C++ has this design issue because it has to explicitly implement a strategy for memory management within its other language semantics.

The memory management problem in itself is a general resource management issue that is *mostly* solved, and when one needs to do the stuff by hand, once you've learned to solve resource-management problems once, you'll be able to solve them always. After that, the issue becomes either manual labor or a design constraint or both.

So, languages that assume a memory manager will at least not have to run into similar problems here that C++ has.

The pass by value vs. pass by reference semantics question is a separate issue. Even in languages which are pass by reference (or, more generally, make use of "bindings") the idea of a call stack is certainly significant -- if you consider recursion, then we simply are not talking about a stack of values but a stack of bindings of certain symbol to different values. The concept of the call stack does not require an actual C-style value stack, although the C stack is certainly an example.

In the end, it's about the definition of the semantics of the language... in some languages, 'x' is actually a "physical box" with a value in it (C), in some other languages, it just evaluates to a value, like in mathematics (Lisp, Python...). Certainly a programmer *must* understand both ways of seeing this, but to think that the C-style view is somehow particularly generally important and informative has yet to be proven to me. Actually, I would say that deeply ingrained C-thinking makes it much harder to obtain the Lisp-view which is far more useful when considering what things like compilers and interpreters actually do -- and interestingly, a *lot* of problems can be cast in terms of writing compilers/interpreters because *automated symbolic manipulation is what computers do in the first place*...

---

### Post by nvteighen on 2010-10-07
Ok, if I've understood the discussion well, there's something I may be helpful with... being myself a bit of an "outsider" :)

There's no difference when some function is supposed to return something by value but under the hood it actually does it by reference. When you use return by value, all you want is your value back in a way that doesn't touch the stack frame it comes from and it shouldn't matter to you whether it was copied or it is a reference coming from a stack frame that has been popped off and therefore is unreachable.

Of course, the inverse is not possible. If you want something to be returned by reference, you are specifying that you want your value back but also, that you don't want it to be a copy.

In other words, "return by value" is the unmarked term, whereas "return by reference" is the marked term. In a situation where you want return by value, it might actually be a return by reference (only true under some specific conditions), but not viceversa.

---

### Post by worseisworser on 2010-10-07
> **worksofcraft said:**
> I don't think you understand the code I wrote.
Perhaps this makes it clearer:
[php]

#include <stdio.h>

struct my_blob { 
    my_blob *Self; 
    my_blob() {
        Self = this; 
        printf("constructing my_blob at %p\n", this); 
    }
    ~my_blob() { 
        printf("destructing my_blob from %p\n", this); 
    }
    int was_copied() {
         if (Self != this) printf("I'm a copy\n");
         else printf("I'm the original that make_blob made\n");
         return (Self != this);
    }
}; 

typedef my_blob (* volatile foxy)(); // prevent inline expansion 

my_blob make_blob() { 
    my_blob Blob; 
    printf("hello I'm make_blob and I'm about to return my value!\n");
    return Blob; // by value 
} 

int main() { 
    foxy Fox = make_blob; 
    my_blob NewBlob = (*Fox)(); 
    return NewBlob.was_copied(); 
} 
[/php]
```

$> g++ newblob.cc
$> ./a.out
constructing my_blob at 0x7fff9caaf370
hello I'm make_blob and I'm about to return my value!
I'm the original that make_blob made
destructing my_blob from 0x7fff9caaf370

```


Yes, see my edit already. You seemed to talk about pass-by semantics instead of RVO; or perhaps mixing the two.

edit: Wait, no, what? You did actually reply to my edit and you still think I misunderstood you? I did not; you where referring to RVO, and I have no trouble understanding what that is; I think it is silly.


> 
... as for conventions and styles of capitalization, I'm afraid mine predates what you use and I see no reason to change it.

However, next time you're in your time machine do pop back and explain to K&R that they need to capitalize types like "int" and "float" and do educate them into rewriting the standard library functions all in CamelCase while you are at it.

This isn't K&R C; it's C++, and using the same style as the STL does for user/application code isn't common. Not my problem though.

---

### Post by dwhitney67 on 2010-10-07
> **worksofcraft said:**
> 
```

    int was_copied() {
         **if (Self != this) printf("I'm a copy\n");**
         else printf("I'm the original that make_blob made\n");
         return (Self != this);
    } 

```

The conditional within the if-statement will NEVER be true, unless you go out of your way to reassign Self to some value other than what you have assigned within the constructor.

When I think about even more (and jeez, I wish I hadn't), the contents of the method amount to nothing.  The method will always print the same statement, and it will always return the int equivalent of the boolean value false, which is zero.

---

### Post by lisati on 2010-10-07
*sigh* /me longs for a day when things were simpler, and the average programmer didn't have to worry too much about how values got dropped into variables and data structures when calling up and returning from a function or subroutine.

---

### Post by worseisworser on 2010-10-07
Sounds like you're talking about one of dem dere "obsolete", academic, hippyish languages, lisati.

..hehe.. x)

edit:
Btw. the full name for this is actually NRVO (named return value optimization) in this particular case.

---

### Post by worksofcraft on 2010-10-07
> **dwhitney67 said:**
> The conditional within the if-statement will NEVER be true, unless you go out of your way to reassign Self to some value other than what you have assigned within the constructor.

When I think about even more (and jeez, I wish I hadn't), the contents of the method amount to nothing.  The method will always print the same statement, and it will always return the int equivalent of the boolean value false, which is zero.

... always ?
[php]
#include <stdio.h>

struct my_blob { 
    my_blob *Self; 
    my_blob() {
        Self = this; 
        printf("constructing my_blob at %p\n", this); 
    }
    ~my_blob() { 
        printf("destructing my_blob from %p\n", this); 
    }
    int was_copied() {
         if (Self != this) printf("I'm a copy\n");
         else printf("I'm the original that make_blob made\n");
         return (Self != this);
    }
}; 

my_blob make_blob(int Ac) {
	// a pointless "if" that makes a point
	if (Ac) {
		my_blob Blob1; 
		return Blob1; // by value
	}
	else {
		my_blob Blob2; 
		return Blob2; // by value
	}
} 

int main(int Ac, char **Av) { 
    my_blob NewBlob = make_blob(Ac); 
    return NewBlob.was_copied(); 
} 
[/php]
perhaps you stopped thinking too soon? :popcorn:
```

$> g++ newblob.cc
$> ./a.out
constructing my_blob at 0x7fff762a8b10
destructing my_blob from 0x7fff762a8b10
I'm a copy
destructing my_blob from 0x7fff762a8b50
$> echo $?
1

```

Now my impression about optimizations is that the code still has to produce the same result. Otherwise the compiler is choosing to solve a different problem :shock:

---

### Post by worksofcraft on 2010-10-07
of course you can with a single key stroke change the make_blob to return it's value by reference and I really do wonder what percentage of IT students and professionals would understand why they are getting a reference to an object that has already been destroyed.

You can also do funny things like make the make_blob function recursive and see how this "optimization" is doing something totally different.
[php]
my_blob make_blob(int Ac) {
	my_blob Blob = Ac? make_blob(Ac-1): make_other_blob();
	++RecursionCount;
	return Blob; // by value
}
[/php]
```

$> ./a.out a b c
constructing my_blob at 0x7fff93444c60
1 blobs were constructed by 5 calls to make_blob
I'm the original that make_blob made
destructing my_blob from 0x7fff93444c60

```
Once upon a time I wanted to suggest the inclusion of a void pointer named "that" into the language in analogy of the "this" pointer, so that we could then use "placement new" to construct our function's output result:
[php]
my_blob make_blob(int Ac) {
	my_blob *Result = new (that) my_blob;
	return *Result; // by value
} 
[/php]
Which I still think would be better than a compiler dependent optimization, but at best I didn't think anyone would know what I was talking about.

p.s. so that means I'm in total agreement with the sentiment expressed by CptPicard on this issue:

> **CptPicard said:**
>  "Not really knowing" *when* the compiler will manage to RVO, when the alternative is internal exploding pointers, seems to me to be totally unacceptable.

---

### Post by dwhitney67 on 2010-10-07
> **worksofcraft said:**
> 
perhaps you stopped thinking too soon? :popcorn:


I just now realized that you failed to implement a copy-constructor, thus for your copied object, the pointer Self is never initialized to anything... in other words, it is a dangling pointer.

Add this to your code, and re-test:
```

    my_blob(const my_blob& other) {
        Self = this; 
        printf("copy-constructing my_blob at %p\n", this); 
    } 

```
Anyhow, if you are trying to prove that an object was copied, then so what?  Is this a bad thing?  The shallow-copy should be expected, however for a deep-copy to succeed, you need to develop the additional code.  I'm sorry if this doesn't suit you.

---

### Post by worksofcraft on 2010-10-07
> **dwhitney67 said:**
> I just now realized that you failed to implement a copy-constructor, thus for your copied object, the pointer Self is never initialized to anything... in other words, it is a dangling pointer.

Add this to your code, and re-test:
```

    my_blob(const my_blob& other) {
        Self = this; 
        printf("copy-constructing my_blob at %p\n", this); 
    } 

```
Anyhow, if you are trying to prove that an object was copied, then so what?  Is this a bad thing?  The shallow-copy should be expected, however for a deep-copy to succeed, you need to develop the additional code.  I'm sorry if this doesn't suit you.

It doesn't leave an uninitialized pointer. The default copy constructor copies a pointer that is pointing to the original. It isn't a question of "what suits me". It's a question of it producing completely different results.

The reason I posted this is because I had a load of functions that worked like this:
[php]
char * make_me_a_string(char * Buffer, size_t BufferSize);
// and I converted them to something like this:
string make_me_a_string();
[/php]
... and since the code is expected to get hammered I was concerned about whether the strings would get copied over and over (which would not be acceptable IMO) or if it was going to be intelligent about it.

> **dwhitney67 said:**
> How long have you been in the s/w profession?  I've been in it for some time myself, and I have been able to adapt to new, preferred, styles.

In everyday English we capitalise proper names and not the "class" of person that they belong to:
Jack and Jill are nobility. Not jack and jill are Nobility.

IMOe the "new" reversal of established tradition and common practice are of little value or relevance. I wasn't active in the industry when they became popular and I'm certainly not going to go reformat all my old code to try and please unidentified 3rd parties.

... as for comments from some along the lines of "this isn't interesting"... well honestly, don't feel obliged to take part in this discussion!

p.s. anyway I'm marking this thread as solved because I suspect it will just be all negative remarks trashing the whole topic from here on.

---

### Post by lisati on 2010-10-07
> **worseisworser said:**
> Sounds like you're talking about one of dem dere "obsolete", academic, hippyish languages, lisati.

..hehe.. x)


:D I was dreaming of a time when I was learning the [s]basics[/s] fundamentals of Fortran and didn't need to concern myself with having a basic grasp of OOP, C++, etc., and when decisions about "return by value" and "return by reference" weren't relevant. (I do recall "call by value" and "call by reference" being mentioned on the course as something to be aware of, but it was a long time ago.)

---

