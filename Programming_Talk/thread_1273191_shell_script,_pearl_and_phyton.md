---
title: "shell script, pearl and phyton"
date: 2009-09-23
forum: Programming Talk
---

### Post by A_M_S on 2009-09-23
Hi.

I have experience in C/C++ (under windows) but none in scripting languages.
 
Could anyone tell me, what are the major diferences between shell script, pearl and phyton?


Tnx.

---

### Post by wmcbrine on 2009-09-23
Shell script is mostly used to coordinate various external commands; another way to put it is that it automates what you'd type on the command line. Python and Perl are more self-contained, complete, powerful languages.

Python is a lot less cryptic than Perl. But I don't know enough about Perl to tell you what its advantages over Python might be.

---

### Post by scragar on 2009-09-23
Perl is very good at using regular expressions and shorthand to reduce typing, it's also a much older and more complete in terms of how many libararies you may use for it.

It is harder to read though, as wmcbrine said.
```
#!/usr/bin/perl
while(<STDIN>){
  exit if not @_;
  print shift if( m/cheese/ );
}
```That shows just how cryptic perl can be, but it also shows how powerfull perl can be, that small amount of code will ask for lines of input endlessly, and for each line that contains the word "cheese" it will return the first argument passed, then the second and so on until it's either killed off or you run out of arguments.

---

### Post by Can+~ on 2009-09-23
AS mentioned above, Perl syntax can go very cryptic some times, on the other hand, python has a clearer one (in exchange of whitespace and more typing):

[PHP]import random

mylist = [1, 2, 3, 4, 6, 9, 14, 15, 20]

# Random shuffling
random.shuffle(mylist)

print "Unsorted:", mylist

# List sorting method
mylist.sort()

print "Sorted:", mylist
print "Partition:", mylist[3:6]

# for-loop Iteration
for item in mylist:
	print item[/PHP]

(Figured: Random sample of shuffling, ordering, slicing and iteration.)

---

### Post by A_Fiachra on 2009-09-23
Bash shell programming can accomplish a lot -- it's a loosely typed language with several nice storage mechanism and good support for structured programming.

Perl is based, in a large part, on Bourne and Korn shell ideas, but it introduces a much richer framework to allow general purpose programming across platforms and full life cycle development of serious tools.  A large part of the human genome project has relied on Perl, for example.  There are tons of Perl applications in the sciences, math, artificial intelligence, web and user interface worlds, for example.

Python is a younger language and having its growing pains, but basically much more OO-friendly than either Bash or Perl and also a general purpose programming language along the lines of Java, but not as pedantically OO.

People's major complaint about Perl is that it is a "write-only" language:

```


my %f = (
  map {
    my $l = $_ < 0
        ? (($_ + 10) * 10)
        : (($_ + 1) * 100);

    ($_, $_ && "$l%")
  } -9 .. 9
);


```

It's not unusual to see insane scribble where there is real code -- and that's a mild example.

```

#!      /usr/bin/perl
''=~('(?{'.('.,)@^{'^'^^@.*[').'"'.('@(]^{>@/^@@,{.@,@{@>>@@,_'^'*].*[_.@*(%^[^%^,[(_]+%^}').',$/})')

```

is legal code that is *obfuscated*!!!

I happen to love Perl -- I've been using it for years and it rocks -- but it takes a **long **time to get handy at Perl.

Python has a much more gentle learning curve, and it supports a lot of really useful programming paradigms right out of the box.

```

from heapq import heappush, heappop
heap = []
data = [1, 3, 5, 7, 9, 2, 4, 6, 8, 0]
for item in data:
    heappush(heap, item)
sorted = []
while heap:
    sorted.append(heappop(heap))
print sorted
data.sort()
print data == sorted

```

What?  It has a heap library ready for use!!!  It has WWW tools ready?  It has marshaling, persistence, metaprogramming, system, threading, regular expression and a ton of other libraries already installed and waiting to be used???

The downside of "batteries included" is version maintenance -- as new features are added to the language, old libraries break -- Python is, so far, doing a much better job than Sun has done with Java, which had a lot of growing pains.  But it is not like C++ -- which supports everything from the beginning of time and ends up becoming an overly complicated language that supports a lot of paradigms, often badly.  (If C++ is an OO language why doesn't it have built is support for introspection?  STL provides it, but C++ has no native and useful introspection support.)

---

### Post by ve4cib on 2009-09-23
> Perl is executable line noise.
Python is executable pseudo-code.

I don't know who said that, but it sums up the major differences quite nicely.  Python's biggest strength (and, according to some its biggest flaw) is that in *forces* you to write legible code.  Whitespace defines scope, so you must format your code properly or else it simply does not work.

Perl, as has been illustrated, has no such legibility requirement.  Like C you can make it as cryptic and obfuscated as you like, or you can be sensible about it, format it properly, and add comments where necessary.

Perl and Python really serve largely-interchangeable roles.  They're both general-purpose scripting languages.  From what I understand -- I am a relative newb when it comes to Perl (but I've been doing Python for years) -- Python is much more object-oriented than Perl.  I honestly don't even know if Perl *has* objects.  It might.  Anyway, my understanding is that Perl tends to be more C-style, procedural code, whereas Python lets you do more object-oriented, C++/C#/Java kind of stuff.  You can still do procedural programming with Python if you prefer that though.

Generally-speaking though anything you can do with Perl you can do in Python, and vice-versa.  The choice of which to use largely depends on the coder's preference and the environment in which they're working.

---

### Post by A_Fiachra on 2009-09-24
Perl doesn't have objects as such -- it does have the bless keyword -- which ties data to a package name, allowing encapsulation, inheritance (via the @ISA package variable) and polymorphism.

So called "new style" objects in Python started in 2.4?  Or was it an earlier version of Python?

---

### Post by ve4cib on 2009-09-24
Not too sure about that.  I started learning Python back when 2.4 was new and never really touched anything earlier than that.  From what I recall the new-style objects were present then, so they've been around since at least 2.4.  Possibly earlier

---

### Post by A_M_S on 2009-09-24
Tnx for the tips! :)

---

### Post by alzaf on 2009-09-24
I haven't done anything in C or C++ for years (apart from a recent dabbling in C which gave me flashbacks of cryptic error messages and hunting about for missing end brackets) and haven't tried Perl but I like Python as it is good for being able to write small programs quickly and having well described error messages. I also like it because the code is easy to read due to using whitespace as scope which makes it  IMIHO easy to maintain for a casual programmer like myself who may not amend the code for a long period after it was written.

---

