---
title: "I forget when i leave my pc"
date: 2011-08-15
forum: Programming Talk
---

### Post by nickos on 2011-08-15
When i leave my computer i forget what i have been doing in my computer.I mean that i may write a program and all that stuff but when i am not in front of my computer i have no inspiration and no idea how i made the program and stuff.
Is that normal and does this happen to other people?

---

### Post by slavik on 2011-08-15
document your code! :)

---

### Post by cgroza on 2011-08-15
[BAD JOKE]
I assume you code Perl?
[/BAD JOKE]
Just comment your code, especially if the above is valid.

---

### Post by nickos on 2011-08-15
document what ? :D

no i code in C if thats a problem :P

when i say forget i mean that i cant "code" in my mind without beeing in front of my computer if you get what im trying to say :/

---

### Post by cgroza on 2011-08-15
> **nickos said:**
> 

when i say forget i mean that i cant "code" in my mind without beeing in front of my computer if you get what im trying to say :/
Then write it on paper, and then when you get in front of your computer type it in. :D

---

### Post by nickos on 2011-08-15
nah,sorry you dont get what im trying to say,i always save my work :D

i mean that for ex i can only "make" menus,toolbars,tables etc only when im in front of my computer but when i try to do that or make a quick revision in my mind i cant even think how its done but when im in front of my keyboard and screen i seem to code everything correctly :o is that a common fact or is it just me?

---

### Post by ruffEdgz on 2011-08-15
> **nickos said:**
> nah,sorry you dont get what im trying to say,i always save my work :D

i mean that for ex i can only "make" menus,toolbars,tables etc only when im in front of my computer but when i try to do that or make a quick revision in my mind i cant even think how its done but when im in front of my keyboard and screen i seem to code everything correctly :o is that a common fact or is it just me?

Whenever I'm not in front of my computer but I need or want to write something down so I don't forget, I make 'pseudo code' ([http://en.wikipedia.org/wiki/Pseudocode](http://en.wikipedia.org/wiki/Pseudocode)) with any comments so I know why I was thinking that way. Its a great way to collect your thoughts before you hit the coding side of things if you can't get in front of a computer.

To answer questions about 'is it normal', I don't see why not since everyone thinks the same way so the way a person codes will be away different then you and how you come up with that code will also be different. For me, I can't think of the exact coding names all the time but I think I'm pretty good in the pseudo code aspect to get me going if I am talking to someone else about a project or if I can't get in front of a computer to type down my thoughts.

Cheers!

---

### Post by slavik on 2011-08-16
your mind is not for code, your mind is for concepts. think of what you want to do, what changes to make. do not think about what the code looks like (maybe except what libraries/data structures to use)

---

### Post by DotNate on 2011-08-16
I'm exactly the opposite.  I've been known to dream about code I've been writing and wake in the middle of the night with the solution to whatever problem it was I happened to be working on that day.

---

### Post by DangerOnTheRanger on 2011-08-16
> **DotNate said:**
> I'm exactly the opposite.  I've been known to dream about code I've been writing and wake in the middle of the night with the solution to whatever problem it was I happened to be working on that day.

Same here. It's almost spooky how I dream about coding in Python, and then I wake up and remember exactly what I was typing in my dream. :)

[QUOTE=slavik]
your mind is not for code, your mind is for concepts. think of what you  want to do, what changes to make. do not think about what the code looks  like (maybe except what libraries/data structures to use)     
[/QUOTE]

I agree with this. Try thinking at a higher level - like, think about the algorithms your code will use, instead of the actual code that will implement those algorithms. It's almost useless to think up such code in your head - it's probably wrong, anyway; especially with a language such as C.

---

### Post by cgroza on 2011-08-16
> **DangerOnTheRanger said:**
> Same here. It's almost spooky how I dream about coding in Python, and then I wake up and remember exactly what I was typing in my dream. :)

And I thought I had some kind of super power. Not fair!:P

---

### Post by slavik on 2011-08-17
> **DotNate said:**
> I'm exactly the opposite.  I've been known to dream about code I've been writing and wake in the middle of the night with the solution to whatever problem it was I happened to be working on that day.
it's not you dreaming up actual code, it is you dreaming up an algorithm of solving the problem.

---

### Post by nvteighen on 2011-08-17
Apart from writing easy-to-read-and-understand code, also document it, i.e. use comments.

In C, comments are introduced by two mechanisms.

```

/* This is a multiline comment. You can write whatever you want, 
 * as long as you want, without any impact on the executable's size
 * because comments are always treated by the compiler like 
 * whitespace. Multiline comments are introduced by '/*' and closed 
 * by '*/'.
 *
 * The '*' at the beginning of every line isn't required, but it's
 * a handy convention for visually recognizing the comment better.
 */

```

The multiline comment is available in all C standards.

Then, there's the single-line comment, which was backported from C++... backported from BCPL, which was a predecessor of C. No, I don't know why the original C and even the C89 standard didn't allow them. The current C99 standard does support them and nearly every compiler has supported them as an extension nevertheless.

```

int main(void)
{
    int myvar = 9; // This variable is super-important.
    // As you see, single-line comments are introduced by '//'.

    return myvar;
}

```

Using comments is very useful: they act as notes, documentation or whatever you want to state in natural language. Of course, try to comment things that aren't blatantly obvious from reading the code. Usually, comments are not about 'what' something is, but about the reasons something is there or in a particular fashion.

Hope this helps.

---

### Post by The Cog on 2011-08-20
> **DangerOnTheRanger said:**
> Same here. It's almost spooky how I dream about coding in Python, and then I wake up and remember exactly what I was typing in my dream. :)
I do that sometimes. But if I look at what I was coding in my dream, it's usually complete garbage.

---

