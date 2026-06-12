---
title: "OOP:  whats the point of public and private?"
date: 2008-09-06
forum: Programming Talk
---

### Post by codeking on 2008-09-06
I've been doing OOP for a few years (C++ and PHP), but I have never gotten the point of public and private.  Why does it make a difference?

---

### Post by StOoZ on 2008-09-06
encapsulation.

you have a class , which has an internal , complex method (the private in this case) to calculate something , which you dont want the user to directly use it , but , you will call it from another method (the public in this case) that simplifies the usage of it... just one example.
also in inheritance , private methods are not inherited.

---

### Post by jimi_hendrix on 2008-09-06
same thing goes with data types...and i find it helps with my organization

---

### Post by Reiger on 2008-09-06
More specifically: if you want an external object to do raw manipulations without any safety check (for benefit or performance or coding convenience) you want public; but if you are shy of the possible consequences you want private.

Essentially this is why interfaces in the Java-speak always define public things (little point in promising something the user isn't allowed to use...) but also why virtually all data structures are thoroughly locked off from the outside world, leaving only authorized methods to 'question' the content.

---

### Post by issih on 2008-09-06
The point as such is that you define the public methods as an interface to the functionality of a class, but can keep the actual implementation of those methods locked away in private internal methods, that way you can completely change the implementation of the code, to increase accuracy/speed/etc without any code which depend on the class in question being compromised in any way. In essence if you leave the public interfaces alone, you can't break the compatibility of the class with your codebase.

in essence it is a syntactical way of organising code for simpler reuseability, much like OO programming in its entirety.

---

### Post by DavidBell on 2008-09-06
@ Stooz, small correction private methods are inhertited, it's just that they are not accessable in derived classes.

@codeking, the general pattern is you declare your variables private/protected and you manipulate them via public methods, this way you can ensure control over how the variables are used.

quick example```

class Test
    {private:
        int count; /// counts something internally
     public:
        int GetCount()
            {return count;
            }
    };
```
Now everyone can read the 'count' variable, but on-one can edit it from outside - only the class itself can adjust it, ensuring 'count' is kept up to date in a controlled manner.

At the same time I always think everything is optional in C++, small projects you can just declare everything public if you want, but as projects get larger and more complex controlled access becomes more important and increases reliablibity of the code.

HTH DB

---

### Post by StOoZ on 2008-09-06
> **DavidBell said:**
> @ Stooz, small correction private methods are inhertited, it's just that they are not accessable in derived classes.

@codeking, the general pattern is you declare your variables private/protected and you manipulate them via public methods, this way you can ensure control over how the variables are used.

quick example```

class Test
    {private:
        int count; /// counts something internally
     public:
        int GetCount()
            {return count;
            }
    };
```
Now everyone can read the 'count' variable, but only the class itself can adjust it, ensuring 'count' is kept up to date in a controlled manner.

At the same time I always think everything is optional in C++, small projects you can just declare everything public if you want, but as projects get larger and more complex controlled access becomes more important and increases reliablibity of the code.

HTH DB

I didnt mean private inheritance , I meant  that when you have:

class base {
private :
int a;
}

class derived : public base {
// a from base is not accessible here
}


thats what I meant , see this:
[http://www.parashift.com/c++-faq-lite/basics-of-inheritance.html]("http://www.parashift.com/c++-faq-lite/basics-of-inheritance.html")


data in private sections of a class , is NOT accessible from the outside , nor from derived classes.

---

### Post by kjohansen on 2008-09-06
then there is the compromise of protected in some languages.

In StOoZ's example a protected variable would be inherited but still "private" to everything else.

---

### Post by ThinkBuntu on 2008-09-06
In my opinion, private methods have two purposes:
[LIST=1]
[*]To protect your program from stupid programmers (assuming they can view the source or read an API)
[*]To paint yourself in a corner
[/LIST]
When you're programming in the OO paradigm, there's no risk of conflicting names, etc. because everything class is its own namespace. I feel the same way about interfaces: I don't need my code restricting what I can do with a class, practice should dictate principle.

The only exception may be, for example, a plugin environment, but in that case secure code should be responsible for security in the first place.

---

