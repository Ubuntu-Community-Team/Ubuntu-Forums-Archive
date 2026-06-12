---
title: "Need clarification on pointer use in C++"
date: 2007-03-11
forum: Programming Talk
---

### Post by barney_1 on 2007-03-11
Hi Folks,

I'm using a book called "Teach Yourself C++" by Herbert Schildt to learn the language.  I used a java based lecture called Thinking in C by Bruce Eckel to get me ramped up for C++.

In the book, I'm doing the exercises for section 1.5 where I am supposed to write a program that uses a class to store information on library book.  I need to store title, author, and number on hand.  I am able to do this but when I look up the answer in the back I find that he used pointers and I didn't.  Here is the function I have questions about:
```
void card::store(char *t, char *name, int num);
{
  strcpy(title, t);
  strcpy(author, name);
  number = num;
}
```

So, 'title' and 'author' are private char's from the class 'card'.  What I don't understand is that in the main function of the program this function is passed strings but as you can see in the declaration of the card::store function he is using the pointers *t and *name.  Why is the use of pointers here better than the use of something like 'char t[]'?

---

### Post by hod139 on 2007-03-11
> **barney_1 said:**
> 
```
void card::store(char *t, char *name, int num);
{
  strcpy(title, t);
  strcpy(author, name);
  number = num;
}
```So, 'title' and 'author' are private char's from the class 'card'.  What I don't understand is that in the main function of the program this function is passed strings but as you can see in the declaration of the card::store function he is using the pointers *t and *name.  Why is the use of pointers here better than the use of something like 'char t[]'?

From this code block you posted, I would strongly suggest you do not use this reference.  In C++ there is no reason not to use std::string, and his use of strcpy is **extremely** bad.

```
void card::store(const std::string & t, const std::string & name, int num);
{
  title = t;
  author = name;
  number = num;
}
```

And the member fields title and author would both be std::string.


ALso, it looks like I am not alone in [not recommending]("http://www.accu.informika.ru/cgi-bin/accu/rvout.cgi?from=0pb_McGraw-Hill&file=t001453a") that book.

---

### Post by angelmartinezn on 2007-03-11
[..]

```
void card::store(const std::string & t, const std::string & name, int num);
{
  title = t;
  author = name;
  number = num;
}
```

[...]

But... by this way the vars. passed to the function and the card->members will be pointing to the same memory region, won't they?

I'm not quite sure... but I think it.

Àngel.

---

### Post by hod139 on 2007-03-11
> **angelmartinezn said:**
> [..]

But... by this way the vars. passed to the function and the card->members will be pointing to the same memory region, won't they?


Nope.  The wonderful thing about using the C++ standard template library is that stuff works the way you expect.  The std::string assignment operator will copy the string and destroy the previous contents automagically.

---

### Post by barney_1 on 2007-03-11
Thanks for the help.  It's nice that this was pointed out to me before I got too far along in the book (I'm still on chapter 1).  I think I'm going to start again with a book that is "Highly Recommended" on the list that hod139 linked to in the second post.  The book is available for download, and is recommended on the sticky in this forum:  "Thinking in C++" by Bruce Eckel

---

