---
title: "Strings in Java are not garbage-collected?"
date: 2007-01-22
forum: Programming Talk
---

### Post by pmasiar on 2007-01-22
I am reading Head-First java, AppendixB, Immutability. (BTW very good book and series - even above O'Reilly good standard, recommended) They say that string in Java are immutable (which is OK with me), and...

**Strings are stored in special "String Pool" which is not garbage-collected,** ever. So all discarder string will sit there, wasting memory live zombies, never alive and never destroyed. Please tell me it is not true! Tell me it is just bad dream! even better, send me a link. :-)

---

### Post by hod139 on 2007-01-22
Java strings are immutable and final. This is why there is also a stringbuffer class, which can be significantly faster than the string class depending on what you are doing.   Strings are nice because they are inherently thread safe.

As for the string pool, I believe that there is a fixed size and eventually, if the limit is exceeded, the memory is reclaimed.

---

### Post by Npl on 2007-01-22
Strings ARE garbage collected like everything else.
The String-Pool is for static String-Literals only.
eg.

String s1 = "String";
String s2 = "Pool";
String s3 = "String-Pool-Content";

s1,s2,s3 are just your regular garbagecollected-Objects. The Literals however are put in the String-Pool by the compiler. If the Compiler is smart enough he will only store "String-Pool-Content" and create substrings for s1 and s2.

Edit: the compiler will do something like this:

static final String pool = "String-Pool-Content";

void func()
{
String s1 = pool.subString(0,6);
String s2 = pool.subString(8,12);
String s3 = pool;
}

---

### Post by pmasiar on 2007-01-23
OK thanks. Looks like I was almost right: String literals will stay in pool forever (you have no confirmed links to disprove it, so I trust O'Reilly book above your opinion, sorry).

Workaround: don't use String, use StringBuffer. 

String variable (references) are destroyed by GC, but literals will stay in String Pool. At least they are stored efficiently. :-( This might be the reason why Java leaks memory. 

Scarry how such a fundamental object as String has so huge gap in functionality. In a language used mostly for web apps == fancy text processing.

Oh well.

---

### Post by lnostdal on 2007-01-23
> **pmasiar said:**
> OK thanks. Looks like I was almost right: String literals will stay in pool forever (you have no confirmed links to disprove it, so I trust O'Reilly book above your opinion, sorry).

Workaround: don't use String, use StringBuffer. 

String variable (references) are destroyed by GC, but literals will stay in String Pool. At least they are stored efficiently. :-( This might be the reason why Java leaks memory. 

Scarry how such a fundamental object as String has so huge gap in functionality. In a language used mostly for web apps == fancy text processing.

Oh well.

I might be too tired to understand/explain, but:

```

#include <stdio.h>
#include <assert.h>

char* blah1 = "hello";
char* blah2 = "hello";
char* blah3 = "Hello";


int main(int argc, char **argv){
  printf("%p %p %p\n", blah1, blah2, blah3);
  assert(blah1 == blah2 && blah2 != blah3); // implies blah3 != blah1

  blah3 = blah2;
  printf("%p %p %p\n", blah1, blah2, blah3);
  assert(blah1 == blah2 && blah2 == blah3); // implies blah3 == blah1
  assert(blah1 == "hello"); // Yup; this also. Even literals from other compilation units.
    
  return(0);}


/*
  lars@ibmr52:~/programming/c$ gcc -Wall -g a.c -o a && ./a
  0x80485ac 0x80485ac 0x80485b2
  0x80485ac 0x80485ac 0x80485ac
*/

```

Nothing leaks -- as nothing is (edit: or can be) continually "created" at runtime. There is only one "hello" and one "Hello" allocated at all times no matter how many variables "use" them. It's a one cost thing, statically allocated at loading-time alongside the space required for the code itself. 

(point is -- i'm thinking Java does the same thing with its string-literals; but i might be wrong)

---

### Post by Seine on 2007-01-23
Yes, Java Strings are immutable. Note the [PasswordCallback.getPassword()]("http://java.sun.com/j2se/1.4.2/docs/api/javax/security/auth/callback/PasswordCallback.html#getPassword()") api uses char[] for the password. If a String was used it could be located in the heap as a form of attack.

---

### Post by Npl on 2007-01-23
> **pmasiar said:**
> OK thanks. Looks like I was almost right: String literals will stay in pool forever (you have no confirmed links to disprove it, so I trust O'Reilly book above your opinion, sorry).

Workaround: don't use String, use StringBuffer. 

String variable (references) are destroyed by GC, but literals will stay in String Pool. At least they are stored efficiently. :-( This might be the reason why Java leaks memory. 

Scarry how such a fundamental object as String has so huge gap in functionality. In a language used mostly for web apps == fancy text processing.

Oh well.The Stringpool is static (look up what that means) and gets loaded and unloaded (deallocated) with the Class. No leaking, no heap.
Just think of it as beeing part of the executeable instructions.

if you do
int var = 5;
the literal 5 gets stored static too.

---

### Post by pmasiar on 2007-01-23
> **Npl said:**
> The Stringpool is static (look up what that means) and gets loaded and unloaded (deallocated) with the Class. No leaking, no heap.
Just think of it as beeing part of the executeable instructions..

IIUC Static means - it will stay forever, never subjected to GC. Am I wrong? Do you have some links when class are loaded and unloaded? I understand that it is not on heap (if it would, GC would eat it if not used), but I am not sure when StringPool is deallocated.

---

### Post by Npl on 2007-01-23
Yes and no.
static in Java means its "part of the class". If the Class gets deleted, so does all its static storage, but Classes are never unloaded in the default ClassLoader AFAIK.

You cant "deallocate" the Stringpool as you need it aslong as you need the class.

lets say you have a simple function
void f()
{
 String s1 =  "myString";
 // do something 
}

each time the funtion is called, you create the reference s1 ON THE HEAP and point it to your static StringPool, you cant deallocate the Stringpool even if there is no heap-variable referencing it - as its still referenced by the FUNCTION (and in turn is a depency of the Class). You need it for initializing of variables.

Another example:

void f( int i)
{
 String s1 = Integer.toString( i );
}

This creates a reference s1 ON THE HEAP, creates an String-Instance ON THE HEAP and points s1 to it. Will be garbage-collected like any other object.

Its only literals that are made static, they are needed for initialization anyway so you really cant get rid of them anytime. Stringbuffers are more flexible, but arent more memroy-efficient, besides that the compiler already transparently uses them each time you "add" Strings.

---

