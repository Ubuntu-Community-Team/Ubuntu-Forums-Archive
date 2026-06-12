---
title: "User Input in C++ Without the &quot;cin&quot; keyword"
date: 2010-05-06
forum: Programming Talk
---

### Post by TehCodr on 2010-05-06
Like the title suggests, is there a way to get input in c++ without cin? printf() prints out without cout, so is there something that gets input without cin?

---

### Post by dwhitney67 on 2010-05-06
You should consider getting a hold of a C programming reference manual.

Look into fgets() or scanf().

---

### Post by jwbrase on 2010-05-06
What's wrong with cin? After having learned programming with Java's overly wordy input methods I was delighted to find that in C++.

---

### Post by Tony Flury on 2010-05-07
just a small correction - cin is not a "keyword" like "for" or "while". It is a pre-opened input stream which is stdin (which could be a redirected file, console or pipe) it is exactly the same as stdin in C.

where you have "cin >> <variable>", you can use any file stream handle - for instance "myFile >> <variable>".

the C++ methodology has a major advantage over things like fscanf etc. you can overload the >> operator and allow your main program to do things like : 

```

class MyClass
{
//..... some stuff
} ; 

int main( void )
{
   MyClass MyInstance;

   cin >> MyInstance;
}

```

Where the detail of how to actual get the data for the Class is defined in the class by overloading the ">>" operator.

---

### Post by MadCow108 on 2010-05-07
and for the really low level there are also the open/write/read/close system calls

but use of those is not recommend (even less than the use of the C input/output functions)

---

### Post by ziuciek on 2010-05-07
I suggest using scanf_s rather than scanf simply because it is safer. The difference between scanf and scanf_s is that you have to declare the maximum length of the input you expect.
eg:
scanf("%s", &text);
scanf_s("%s", &text, 12); //now you can't put here longer input than 12 characters

---

### Post by MadCow108 on 2010-05-07
you can also do that without nonstandard (microsoft specific) extensions using the width modifier:
%20s for 20 chars
but you need to null terminate yourself

---

### Post by TehCodr on 2010-05-07
> **dwhitney67 said:**
> You should consider getting a hold of a C programming reference manual.

Look into fgets() or scanf().

I probably should, thanks for the suggestions :)

> **jwbrase said:**
> What's wrong with cin? After having learned programming with Java's overly wordy input methods I was delighted to find that in C++.
The cin keyword is a stream, and streams can "flood", "drain", and "fail". I'm also looking into alternatives for fstream and sstream.

> **ziuciek said:**
> I suggest using scanf_s rather than scanf simply because it is safer. The difference between scanf and scanf_s is that you have to declare the maximum length of the input you expect.
eg:
scanf("%s", &text);
scanf_s("%s", &text, 12); //now you can't put here longer input than 12 characters
Thanks, great suggestion :)

---

### Post by MadCow108 on 2010-05-07
the C functions fprintf scanf etc are also streams!

and what do you mean with flood, drain, fail?
well fail is clear, but every io operation can fail. There is nothing you can do about that ...

---

### Post by Lux Perpetua on 2010-05-07
> **TehCodr said:**
> The cin keyword is a stream, and streams can "flood", "drain", and "fail". I'm also looking into alternatives for fstream and sstream.First of all, "cin" isn't a keyword; it's a normal identifier. Secondly, C++ streams are no less reliable than FILE pointers in C or POSIX file descriptors (the lowest level attainable from user space).

---

### Post by nvteighen on 2010-05-08
> **TehCodr said:**
> 
The cin keyword is a stream, and streams can "flood", "drain", and "fail". I'm also looking into alternatives for fstream and sstream.


And the C procedures can lead to security issues: string-based buffer overflows and the like. Not to mention that C strings are already a nightmere to use and that C++ streams are designed to work with C++ STL strings!

IMO, it's crazy to try replacing C++ input and output systems for the C ones unless needed because of external reasons. C works that way because it is designed to work at a minimum level of abstraction, while C++ aims to be something totally different. It's possible one of the positive aspects I recognize in C++, a language I really hate.

Anyway, you better use fgets() instead of scanf() as it's **much** safer.

---

