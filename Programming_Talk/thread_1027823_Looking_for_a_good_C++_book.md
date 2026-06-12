---
title: "Looking for a good C++ book"
date: 2009-01-01
forum: Programming Talk
---

### Post by jdunn on 2009-01-01
I'm looking for recommendations for a good, easy-to-understand beginners C++ book for someone who already has some programming experience with Java.  The book should also be a good reference.  Some coverage, at least in brief, of some advanced topics such as multi-threading and remote procedure calls would be nice too.  Thanks.

---

### Post by lordikyiky on 2009-01-01
depending on how good you are with java, The Standard C++ Bible is a good reference.  It goes pretty in depth with core language of C++.  I don't think it has the more advanced topics you mentioned, in fact it basically just covers the language itself.  It has a nice discussion on pointers and C++ classes which are two of the big differences between java and C++.

---

### Post by CptPicard on 2009-01-01
Bruce Eckel's Thinking in C++ books are available free and legally on the web. They are good, and esp. for someone like you who already has programming experience... you can skip the parts you find are too easy going.

---

### Post by mpsii on 2009-01-01
Get the book "Thinking in C++, Volume 1 (2nd Edition) by Bruce Eckel

[Amazon Link]("http://www.amazon.com/Thinking-C-Introduction-Standard-One/dp/0139798099/ref=sr_1_1?ie=UTF8&s=books&qid=1230858316&sr=1-1")

---

### Post by sonofusion82 on 2009-01-01
There are many good C++ books around, "Think In C++" is a good one...
I have recently heard of the book by Stroustrup (one of the C++ inventor) titled "Programming: Principles and Practice Using C++" with some good reviews, but I have not got it myself yet.
However, unlike most newer languages like Java, C# & Python that has the "batteries include" policy, the "advanced topics" such as GUI, multi-threading and RPC are not part of C++ standard libraries, they are rarely included in most C++ books.
Once you are comfortable with C++, you will have to pick up additional frameworks such as Qt, GTK, MFC or others to give you the libraries you need for multi-threading, GUI, etc

---

### Post by giuspen on 2009-01-01
here's in my opinion the best C++ tutorial: [http://www.cplusplus.com/doc/tutorial/]("http://www.cplusplus.com/doc/tutorial/")
Regards.

---

### Post by ankursethi on 2009-01-02
*Thinking in C++* is probably your best bet. Volume 1 covers the basics, so you might want to skip it and get volume 2 instead. In any case, you can read both of them online for free on Bruce Eckel's website (Google it).

I was recently reccomended *The C++ Programming Language* by the folks over at StackOverflow.com. I personally don't like the looks of that book, but you might want to check it out at the store.

---

### Post by samjh on 2009-01-02
Please read the stickies.

This is my recommendation from one of the links in the stickied thread:
[http://ubuntuforums.org/showpost.php?p=4770179&postcount=18](http://ubuntuforums.org/showpost.php?p=4770179&postcount=18)

---

### Post by dribeas on 2009-01-02
C++ Primer, by Stanley B. Lippman

The C++ Programming Language, by Bjarne Stroustrup

Both center on the language. As it has been said, it is not part of the language (yet) but part of some libraries. The standard is being revised and there should be a new standard some time this year. The new standard will cover threading but I don't think it will have RPC.

Anyway, in the meantime, I recommend that you read the standard C++ books and use the Boost libraries for the threading part. Boost libs are probably the best to learn for a couple of reasons. They are cross platform, the libraries are complex internally but easy to use externally and they are probably the closest thing to the new standard available. In particular, and besides the threading libs, I really recommend everyone to know about the boost::smart_ptr, boost::bind and boost::signal libs. Then boost::function and boost::lambda are of use, and there are a whole set of libs for specific problems (date and time manipulation

Of the other frameworks and libraries mentioned, QT is the weirdest with regard to the language and while it is multiplatform it is not pure C++. It pushes the language around with a whole set of macro definitions that almost change the language. It has its own implementation for some of the things that are already there in the STL... so it won't be of great help for a beginner to learn that way.

---

### Post by jdunn on 2009-02-10
Thanks.  I ended up getting the Thinking in C++ books, used.  General consensus is, they are the best books around on C++.  I couldn't handle using the free html docs as references, which is why I bought the books.

---

