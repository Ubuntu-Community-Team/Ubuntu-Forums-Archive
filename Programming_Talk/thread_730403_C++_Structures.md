---
title: "C++ Structures"
date: 2008-03-20
forum: Programming Talk
---

### Post by Sinkingships7 on 2008-03-20
it's not so much that i don't understand them, or how they work.
it's that i don't understand their purpose.

i think i'd have an easier time learning and accepting structures if someone were to explain how and why they're useful. perhaps some examples of situations where they'd be most useful.

---

### Post by LaRoza on 2008-03-20
They are classes, but everything is public by default. 

Rare they are in C++.

---

### Post by Sinkingships7 on 2008-03-20
> **LaRoza said:**
> They are classes, but everything is public by default. 

Rare they are in C++.

so i don't really have to worry about having to use them often, if at all? is there always an open alternative, or is there any situation where you would have to use a structure?

EDIT: what's a class?

---

### Post by Jessehk on 2008-03-20
If you have not been exposed to OOP (object-oriented programming, involving classes and methods, etc), this forum is probably not the best place to learn. 

That said, I can give examples of struct's being used as they would in C.

A struct is typically used to encapsulate a group of multiple variables. Doing so allows them to be manipulated and passed as a whole rather than as a group. For example, a piece of fruit could be represented as a struct like this:

```

#define NAME_MAX 256

struct Fruit {
    char name[NAME_MAX + 1];
    double price;
};

```

Now, instead of having several variables that you must keep track of, there is just one. For example,

```

void buy_fruit( struct Fruit *f ) {
    printf( "You have bought a(n) %s for $%.2lf\n", f->name, f->price );
}

int main( void ) {
    /* Let's create an instance of a fruit.
     * An apple costs 10 cents.
     */
    struct Fruit apple = {
        "apple",
        0.10
    };
    
    buy_fruit( &apple );
    
    return 0;
}

```

Will output:
```

You have bought a(n) apple for $0.10

```

I'm sure other people here will have plenty of other examples.
I will also point out that in C++, there are a few fundamental changes, but the overall idea/concept (if you're using struct's in this sense, and not in the OOP sense) is the same. If you're looking for a good C++ book, [this one](http://mindview.net/Books/TICPP/ThinkingInCPP2e.html) is fairly good and download-able for free. It explains classes and structures very extensively.

---

### Post by |{urse on 2008-03-20
oh man structures are very important if you want to define a bunch of variables and keep them in one place (i.e. structure) then use the whole structure to output or input etc. very important when it comes to encapsulation and it also makes definition easier when you have 1283746247634583477 variables to define of different datatypes but need to remember what theyre all for.

---

### Post by LaRoza on 2008-03-20
C++ structs aren't anything like C structs.

If you don't know what a class is, don't worry about structs. When you get to classes, just substitute the word "struct" for "class" and remember the default access is public.

structs are not normally used in C++ because that is for what classes are made.

---

### Post by CptPicard on 2008-03-20
> **Sinkingships7 said:**
> so i don't really have to worry about having to use them often, if at all?

No, you don't really need to bother much with them, but... structs are sometimes handy as a very lightweight data structure you use to group stuff together, and when you don't bother with using a class. If you are a competent C++ programmer, there is no reason why you would NOT use a struct if you felt like it.

>  is there always an open alternative

Yes, use a class. Although a class without methods if essentially a struct (which qualifications as regards inheritance), see below.

> EDIT: what's a class?

Sorry, but this just made me giggle a bit.. quite a punchline. No hard feelings, everyone is once a beginner ;) ;)

See, your question would be reasonable if you did know what a class is and were just wondering what structs are doing in C++ when you have classes. If you didn't have classes, you'd pretty much have to use  structs, which you actually did back in C for the purpose.

A struct is nothing but a record that groups values together so that you can use that record as a kind of data type. Alternatively, think of it as a bit of an "array" with different types for its members (although you can't index it by numbers, you have to use member names).

You could for example have a struct for a "person" which contains information about that person -- person.name, person.address, so on. Then you could have, say, an array of many people --- person arr[].

Now, in C++ the concept of struct is extended into that of a class. A class combines both data (as in the struct) and methods that operate on that data. So you can have for example a method "move" for a person that moves the person into a different address, writing the new address into the address field and maybe doing something else behind the scenes too....

But yeah, the easy answer is that structs are sort of legacy stuff in C++, which you theoretically could do without. Read about classes and you'll get it :)

---

### Post by |{urse on 2008-03-20
If you plan on learning OO then structures are VERY important.

---

### Post by Jessehk on 2008-03-20
> 
C++ structs aren't anything like C structs.


I never said they were. I said that if used without taking into account OOP, the use of them in C++ is virtually identical.

---

### Post by CptPicard on 2008-03-20
> **|{urse said:**
> If you plan on learning OO then structures are VERY important.

Well, actually... you could remove structs from C++ completely. Java doesn't have structs. But you certainly would have to understand what a class is, which is a harder concept of course.

> **Jessehk said:**
> I never said they were. I said that if used without taking into account OOP, the use of them in C++ is virtually identical.

An interesting point is that if you remove the idea of classes and objects but still keep structs and inheritance, you get something like Haskell's type classes.. but that's another topic. Just a thought.

---

### Post by LaRoza on 2008-03-20
> **|{urse said:**
> If you plan on learning OO then structures are VERY important.

In concept, yes, but classes are the main OO feature of C++.

---

### Post by |{urse on 2008-03-20
Lol as well @ "whats a class" :lolflag: (not in a mean way)

---

### Post by Wybiral on 2008-03-20
I still use structs occasionally in C++ when I need a pack of members that don't associate with any methods (mostly just as a convention for saying "Hey, no methods").

---

### Post by Sinkingships7 on 2008-03-20
thank you all for your useful posts.

just so i'm not interpreted the wrong way, i would like you to know that i am not an inexperienced programmer, just new to c++   :p

i'm quite fluent in QBasic. i just hate it lol


and i'm not new to OOP. i know some of that as well, so you're answers do make sense. 


so just as a final thought to take with me, it's safe to say that the purpose of a structure reaches no further than for organization for the sake of remembrance in large programs where many variables exist?

---

### Post by LaRoza on 2008-03-20
> **Wybiral said:**
> I still use structs occasionally in C++ when I need a pack of members that don't associate with any methods (mostly just as a convention for saying "Hey, no methods").

[php]
struct madnessOfWybiral
{
     std::string method(void)
     {
          return "There is a method to your madness";
     }
}
[/php]

---

### Post by CptPicard on 2008-03-20
It's not that simple really.. it is not just a memory aid. With my example of a "person" struct you can have an arbitrary number of instances of the person struct in memory, and can refer to members at will.

If you did not have structs, you would have to explicitly have a variable for each member of each person. As you can probably see, it would be impossible and at least unwieldy to have "person1_name, person1_address, person2_name, person2_address"... and the impossible bit is trying to have "person_n_name, person_n_address".

EDIT: ok, well, it is conceivable that you'd just malloc a block of RAM and do pointer arithmetic and appropriate casting but that would be awful, and you'd be just reinventing structs in a nasty way.

---

### Post by Sinkingships7 on 2008-03-20
wait... so a struct is like declaring one variable, and therefore takes less memory no matter how many members the struct holds?

---

### Post by LaRoza on 2008-03-20
> **Sinkingships7 said:**
> wait... so a struct is like declaring one variable, and therefore takes less memory no matter how many members the struct holds?

No, it is a class but with default public access. 

Instead of trying to get it here, you are better of learning it on the tutorial/book/class you are using.

A struct and class take up the amount of space they do, which is the total of their members.

Now a union on the other hand, take the space of the largest member. (Wait till you get there!) I don't know if Unions are in C++ though.

---

### Post by Wybiral on 2008-03-20
> **LaRoza said:**
> [php]
struct madnessOfWybiral
{
     std::string method(void)
     {
          return "There is a method to your madness";
     }
}
[/php]

I know that they can have methods, but I use them as a convention for not having methods (IMO, only classes should have methods, C++ should have never tried to change that).

---

### Post by LaRoza on 2008-03-20
> **Wybiral said:**
> I know that they can have methods, but I use them as a convention for not having methods (IMO, only classes should have methods, C++ should have never tried to change that).

I was joking, just a play on words I thought was funny.

I don't get it either, but it is not my place to question committees.

---

### Post by CptPicard on 2008-03-20
No, it is not like some quantum thingy.. ;)

(Incidentally there was something like that called union in C but let's not go there)

A struct is a record. As simple as that really. It has the fields you define it to have, and has the memory consumption of its member variables taken together.

Think of a 3-vector expressed as a struct -- it's probably the most trivial example. It has the x, y and z coordinates. It takes the space of 3 * sizeof(float), if it is declared as 

```

struct vect {
   float x;
   float y;
   float z;
}; // yes true LaRoza... :-)
```

---

### Post by LaRoza on 2008-03-20
> **CptPicard said:**
> 
Think of a 3-vector expressed as a struct -- it's probably the most trivial example. It has the x, y and z coordinates. It takes the space of 3 * float, if it is declared as 

```

struct vect {
   float x;
   float y;
   float z;
}
```

(I mentioned unions a while back... :))

Isn't there supposed to be a semicolon at the end?

---

### Post by Sinkingships7 on 2008-03-20
> **LaRoza said:**
> (I mentioned unions a while back... :))

Isn't there supposed to be a semicolon at the end?

yes lol

---

### Post by CptPicard on 2008-03-20
I suppose the best way for you to see the need for a struct-like concept, be it the C-struct or the C++ class, is to really think of what you would need as a programmer if you were building a 3D graphics program that operates on a lot of these vectors, or a contact list address book that operates on people's contact details... if you try to get by without structs, you'll quickly wish you had them.. :)

---

### Post by Sinkingships7 on 2008-03-20
> **CptPicard said:**
> I suppose the best way for you to see the need for a struct-like concept, be it the C-struct or the C++ class, is to really think of what you would need as a programmer if you were building a 3D graphics program that operates on a lot of these vectors, or a contact list address book that operates on people's contact details... if you try to get by without structs, you'll quickly wish you had them.. :)

just because it would all be so unorganized?

---

### Post by LaRoza on 2008-03-20
> **Sinkingships7 said:**
> just because it would all be so unorganized?

Because it would be impossible.

---

### Post by CptPicard on 2008-03-20
Well, answer the question.. how would you do it? Handling an arbitrary number of records of, say, a byte, float and a double? :) (excluding the really nasty answer of actually doing raw pointer arithmetic into a block of memory, which arrays of structs are syntactic sugar for..)

---

### Post by LaRoza on 2008-03-20
Here is an example of the use of a struct: [http://ubuntuforums.org/showpost.php?p=4415696&postcount=3](http://ubuntuforums.org/showpost.php?p=4415696&postcount=3)

It is a very simple struct (just two integer members), try to rewrite that without structs. Possible, yes...

---

### Post by CptPicard on 2008-03-20
I really want to see what he comes up with.... 	:-\" 

;)

---

### Post by pmasiar on 2008-03-20
@OP: seems like you are rather beginner. Much easier start would be with Python - you have less to worry about proper types, and trying your ideas is much simpler in a shell, without writing half-a-page of code just to try a call and check the result.

---

### Post by LaRoza on 2008-03-20
> **pmasiar said:**
> @OP: seems like you are rather beginner. Much easier start would be with Python - you have less to worry about proper types, and trying your ideas is much simpler in a shell, without writing half-a-page of code just to try a call and check the result.

I was thinking that as well, but it seems the OP does have some programming experience. I wonder if there is a specific reason to learn C++?

---

### Post by Sinkingships7 on 2008-03-20
if i ever do learn python (which i'm sure i will), it will be strictly for the sake of knowledge and fun. python, in my eyes, is not a good starting language for someone who plans on pursuing a life-long career as a programmer. not to say that it can't be done, and it would definitely be fun and addicting, i'm sure, but it's simplicity would make learning languages after it more challenging, whereas if someone can get a good foothold on something like c++ (for reasons we're all aware of), learning all the essentials of any language wouldn't be too hard of a challenge, simply because c++ has the basic concepts a would-be programmer needs to really understand the base of high-level languages and how they work.

i am NOT, of course, saying that is the most efficient, as most people would say learning C is a much better idea if you want to grasp the fundamentals of programming before diving into several other languages, but it is my choice. for whatever reason, i really enjoy c++. it's fun for me, and is bound to be quite useful (seeing as some of the most used programs today are written it, including OS's) based on it's dominance (save for perhaps java) in the job market.



also, you may find it nice to know that it wasn't until about 10 mintues ago that i finally grasped structures lol. i just thought a lot, used the example below, and made up some situations where it would be incredibly useful. that link you gave me helped quite a bit too. i don't even want to attempt to code that without classes/structs. ```
#include <iostream>
using namespace std;

enum bloodType { unknown, A, B, AB, O };
enum rhFactor { negative, positive };

struct bloodPressure
{
	int systolic;
	int diastolic;
};

struct donorInfo
{
	bloodType type;
	rhFactor rh;
	bloodPressure bp;
	int heartRate;
};


int main()
{
	donorInfo currentDonor;
	
	currentDonor.type = A;
	currentDonor.rh = positive;
	currentDonor.bp.systolic = 130;
	currentDonor.bp.diastolic = 74;
	currentDonor.heartRate = 69;
	
	cout << "The donor's blood pressure is " << currentDonor.bp.diastolic
	     << " over " << currentDonor.bp.systolic << endl;
	     
	return 0;
}
```



EDIT: i don't really feel like editing the first paragraph, but re-reading it, i would have liked to word it differently. python would definitely give it's student a basic concept of high-level languages. what i was trying to say was that C++ would give a programmer *more* than a basic understanding, and would really dive into some of the more advanced features of most languages. it's harder, but more worth it, IMO. it is just a preference though. i have absolutely nothing against python.

---

### Post by LaRoza on 2008-03-20
> **Sinkingships7 said:**
> if i ever do learn python (which i'm sure i will), it will be strictly for the sake of knowledge and fun. python, in my eyes, is not a good starting language for someone who plans on pursuing a life-long career as a programmer. not to say that it can't be done, and it would definitely be fun and addicting, i'm sure, but it's simplicity would make learning languages after it more challenging, whereas if someone can get a good foothold on something like c++ (for reasons we're all aware of), learning all the essentials of any language wouldn't be too hard of a challenge, simply because c++ has the basic concepts a would-be programmer needs to really understand the base of high-level languages and how they work.

i am NOT, of course, saying that is the most efficient, as most people would say learning C is a much better idea if you want to grasp the fundamentals of programming before diving into several other languages, but it is my choice. for whatever reason, i really enjoy c++. it's fun for me, and is bound to be quite useful (seeing as some of the most used programs today are written it, including OS's) based on it's dominance (save for perhaps java) in the job market.



Python is a good starting language in many's eyes, but it really doesn't matter where you start. (For careers, Google hired the Python creator, so there must be some merit)

C is what OS's are written in, but kernel writing is not a typical programming task.

Have fun, and learn, that is what matters. Be careful though, Blub should never be learned, and your statements here are dangerously close.

---

### Post by CptPicard on 2008-03-20
> **Sinkingships7 said:**
> i'm sure, but it's simplicity would make learning languages after it more challenging, whereas if someone can get a good foothold on something like c++ (for reasons we're all aware of), learning all the essentials of any language wouldn't be too hard of a challenge, simply because c++ has the basic concepts a would-be programmer needs to really understand the base of high-level languages and how they work.

Okay, cool.. I want some C/C++ hacker to explain to me [Haskell's monads]("http://en.wikipedia.org/wiki/Monads_in_functional_programming") please. They are a very high-level concept but apparently truly trivial to C++ gods. :)

This has been discussed here ad nauseam already, and frankly, those who are in your camp are [blub programmers]("http://www.paulgraham.com/avg.html"). ;)

> i am NOT, of course, saying that is the most efficient

You always, always want to learn in the most efficient manner possible. Pain is not an end unto itself.

> i really enjoy c++. it's fun for me,

"I only know C++ and QBasic, therefore, they are good choices for me" ;)

> and is bound to be quite useful (seeing as some of the most used programs today are written it, including OS's) based on it's dominance (save for perhaps java) in the job market.

Productivity is Important At Work. You will see high-level languages be adopted more and more.

> i don't even want to attempt to code that without classes/structs. 

I wouldn't even want to attempt coding some of my current projects in C -- I want generator functions... ;)

> 
would really dive into some of the more advanced features of most languages..

Such as? C++ is low-level and yes it teaches you about bit fiddling, but it doesn't even have closures or fully re-entrant continuations (and being low-level, it would be really difficult to even include them..).

Look them up. :)

---

### Post by Sinkingships7 on 2008-03-20
i don't think you guys understood. or perhaps i should've worded it differently.

i am not saying that C++ is the best language. not even trying to come close. what i'm saying is that i personally like it. i'm also not saying that i prefer it, as i haven't tasted too many other languages. i'm just saying that, after looking at so many languages source-codes for some time, and reading so many articles on the matter, C++ made the most sense to me. it opens a lot of windows.

i'm more than certain that i will learn many other languages. it's not C++ that i love. it's programming. no matter the case, i find programming exciting.


and don't make fun of me for knowing qbasic lol
i didn't know what i was doing. they made me do it! :lolflag:

---

### Post by CptPicard on 2008-03-20
> 
i'm more than certain that i will learn many other languages. it's not C++ that i love. it's programming. no matter the case, i find programming exciting.

Then you will eventually discover that you really enjoy the high-level conceptual parts of it, and dislike the drudgery more and more. Seriously, the most fascinating abstractions are not even really possible in low level languages as they are very difficult to compile to static code :)

I am, neither, saying that you could call yourself a well-rounded programmer without being capable in a low-level language, but on the other hand... I figured out structs over 10 years ago, am trying to get monads right now, and rarely, if ever, use a low-level language for anything.

---

### Post by Wybiral on 2008-03-20
You seem to be suggesting that C++ is a better choice for you because Python is easier? Smart programmers don't pursue a language because it is hard, they do the opposite. You should never do more work than you have to do. C++ won't teach you any more about programming than Python, it will only teach you more about the pains of programming in C++.

---

### Post by Sinkingships7 on 2008-03-20
> **Wybiral said:**
> You seem to be suggesting that C++ is a better choice for you because Python is easier? Smart programmers don't pursue a language because it is hard, they do the opposite. You should never do more work than you have to do. C++ won't teach you any more about programming than Python, it will only teach you more about the pains of programming in C++.

because of how hard it can be to program in c++, learning other languages will not be as hard. that's what i was saying.

---

### Post by LaRoza on 2008-03-20
OP, we are not saying all this because C++ is bad, or that you are, but we don't want you to be a blub programmer.

Learn C++, then learn Python/Perl/Rub/PHP/C/Java/Lisp/Haskell/Ada/D/etc

(etc isn't a language that I know of)

---

### Post by Sinkingships7 on 2008-03-20
> **LaRoza said:**
> OP, we are not saying all this because C++ is bad, or that you are, but we don't want you to be a blub programmer.

Learn C++, then learn Python/Perl/Rub/PHP/C/Java/Lisp/Haskell/Ada/D/etc

(etc isn't a language that I know of)


lol

see? at least you understand. i would never limit myself to one, or even 2 or 3 languages. i will be as well-rounded as i can. aside from qbasic (since it hardly counts), i'm just starting out. i'll get there, i promise. just give me time. i just want strong roots. coding in c++ has another advantage: it teaches you to become a better debugger. i don't believe i am wrong in that statement.

---

### Post by LaRoza on 2008-03-20
> **Sinkingships7 said:**
> lol

see? at least you understand. i would never limit myself to one, or even 2 or 3 languages. i will be as well-rounded as i can. aside from qbasic (since it hardly counts), i'm just starting out. i'll get there, i promise. just give me time. i just want strong roots. coding in c++ has another advantage: it teaches you to become a better debugger. i don't believe i am wrong in that statement.

No, I am just soft spoken :)

I started with C++, and didn't really get C++ until I had learned C and Python (or PHP, don't remember which)

I never use C++ now.

You will find that languages are just tools, and you want the tools to do all the work that they can do for the task. You wouldn't use a screwdriver with a handle with the same diametre as the shaft as that would just make you work harder (no, it would require you to increase the force, if you want to be technical. Work will remain the same)

Always try to use the most efficient tool that you know. (This means learn a lot)

---

### Post by Sinkingships7 on 2008-03-20
> **LaRoza said:**
> No, I am just soft spoken :)

I started with C++, and didn't really get C++ until I had learned C and Python (or PHP, don't remember which)

I never use C++ now.

You will find that languages are just tools, and you want the tools to do all the work that they can do for the task. You wouldn't use a screwdriver with a handle with the same diametre as the shaft as that would just make you work harder (no, it would require you to increase the force, if you want to be technical. Work will remain the same)

Always try to use the most efficient tool that you know. (This means learn a lot)

may i ask what your most efficient "tool" is and what you do with it?

another reason i'm starting with c++ is for the job market. is that a bad idea as well? it just seems quite dominant to me.

---

### Post by Wybiral on 2008-03-20
> **Sinkingships7 said:**
> because of how hard it can be to program in c++, learning other languages will not be as hard. that's what i was saying.

But it doesn't work like that. Programming is all about knowing how and when to use the right algorithms and data structures to solve problems. C++ is hard because it enforces rules that don't exist in other languages. Learning C++ isn't going to make other languages easier, it's only going to make C++-like languages easier.

You can learn about pointers and memory management all you want, but that's not going to teach you how to write an efficient A* tree search or when to use it for that matter. The general concepts are more important than the details.

There's nothing wrong with learning C++ if you realize this. The problem is mostly that C++ carries more baggage in terms of what is expected of the programmer. This makes dealing with those higher-level abstractions more time-consuming and harder to manage (it's going to take longer to learn how to write those algorithms in a low level language like C++ because you will be wasting too much time worrying about C++'s stricter rules and limitations).

---

### Post by LaRoza on 2008-03-20
> **Sinkingships7 said:**
> may i ask what your most efficient "tool" is and what you do with it?

another reason i'm starting with c++ is for the job market. is that a bad idea as well? it just seems quite dominant to me.

There are 10 considerations for the most efficient tool:

[list]
[*] What you have available (which is limited by knowledge, and the requirements of the task)
[*] Personal preference and skill
[/list]

I have a limited amount of knowledge, and have been programming for only a year.

I typically use Python, PHP, ECMAScript.

It may have high numbers in terms of employment, but I see more jobs for Java, SQL, PHP, and .NET.

There is a link in the sticky about getting jobs.

---

### Post by Sinkingships7 on 2008-03-20
> **Wybiral said:**
> But it doesn't work like that. Programming is all about knowing how and when to use the right algorithms and data structures to solve problems. C++ is hard because it enforces rules that don't exist in other languages. Learning C++ isn't going to make other languages easier, it's only going to make C++-like languages easier.

You can learn about pointers and memory management all you want, but that's not going to teach you how to write an efficient A* tree search or when to use it for that matter. The general concepts are more important than the details.

There's nothing wrong with learning C++ if you realize this. The problem is mostly that C++ carries more baggage in terms of what is expected of the programmer. This makes dealing with those higher-level abstractions more time-consuming and harder to manage (it's going to take longer to learn how to write those algorithms in a low level language like C++ because you will be wasting too much time worrying about C++'s stricter rules and limitations).

there's actually a lot more truth in what you just said then i would care to admit. then i ask this of you: i have searched, high and low, for a good tutorial on python. alas, i failed. if someone could point me towards a tutorial that actually makes sense, that would be wonderful.

---

### Post by LaRoza on 2008-03-20
> **Sinkingships7 said:**
> there's actually a lot more truth in what you just said then i would care to admit. then i ask this of you: i have searched, high and low, for a good tutorial on python. alas, i failed. if someone could point me towards a tutorial that actually makes sense, that would be wonderful.

The official one on python.org, my sig, pmasiar's sig.

---

### Post by CptPicard on 2008-03-20
And by the way, structs are tuples in Python. ;)

---

### Post by Wybiral on 2008-03-20
> **Sinkingships7 said:**
> there's actually a lot more truth in what you just said then i would care to admit. then i ask this of you: i have searched, high and low, for a good tutorial on python. alas, i failed. if someone could point me towards a tutorial that actually makes sense, that would be wonderful.

The best way to learn Python is to take advantage if it's interactive terminal. Just open up the Python prompt, grab a few tutorials, and start trying things out. It's hard to find a "master tutorial" that will just make sense to you... You're much better off reading a few at a time and gaining bits and pieces from each. And if you get stuck on something, there are several Python programmers around this forum that will probably chime in.

---

### Post by LaRoza on 2008-03-20
> **Wybiral said:**
> The best way to learn Python is to take advantage if it's interactive terminal. Just open up the Python prompt, grab a few tutorials, and start trying things out. It's hard to find a "master tutorial" that will just make sense to you... You're much better off reading a few at a time and gaining bits and pieces from each. And if you get stuck on something, there are several Python programmers around this forum that will probably chime in.

That interactive terminal (in several languages, but in this case Python) is very useful, and I typically use it daily.

There are a bunch of resources on my wiki, that are very good.

There are Python programmers on this forum? Where? They are so quiet.

---

### Post by pmasiar on 2008-03-21
> **Sinkingships7 said:**
>  good tutorial on python

See wiki in my sig.

And for sure read about [Blub programming language](http://www.paulgraham.com/avg.html) - you are very close to that thinking, as others mentioned. Blub thinking prevents you to learn why other languages (other than your first) are useful - it limits how you think about programming.

Learning languages is dangerous to your mind: the way first language work becomes the way your mind works, and sometimes you need to unlearn old to be able to really grok new language, with concepts missing in the old. If you read Blub link above, you understand, if you did not, go and do it :-) 

OK, simple example: try explain to a QBasic programmer what is difference between class method and object method, or what is inheritance. See?

You are not completely lost yet - only someone who refuses to accept new ideas and sticks to first Blub is lost. :-)

---

