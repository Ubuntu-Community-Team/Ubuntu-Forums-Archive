---
title: "Datatypes and algorithims help please"
date: 2008-04-03
forum: Programming Talk
---

### Post by jubej on 2008-04-03
Hello!

Im a student at umeås university in Sweden. And at the momment the course im studyng is  Datatypes and algorithims.

Im reading a book that is writen by a local teacher. The problem is that i dont really get it.

I understand that datatypes can be abstract of fisicaly, but in a way that i dont understand fysics datatypes are also implemented.

thereare som ways togo to contruct datatypes:

först make a MODEL of the datatype that represents some real world model.
like list can be compared to to a binder. you can take or insert paper in it or nothing at all but the binder its always there.

Then what follows its then ORGANITATION where you explain the organitation of the datatype like in list that its organasi like elements that are arange  in a before after linjear order.

Then there is the INfORMAL SPECIFICATION.
here you  describe the operations (methods) that the datatype can have. and with parameters that can be used.

The FORMAL Specification
is where you bescribe everything in a mathematical manner with axioms and all right?

Now for the problem its the interface describsion.

exampel for an interface av the operation INSERT for a list datatype:

Insert(v:val, p;pos, l:List(val)) --> (List (val), pos)

I think that insert is the operation right? and that you can put a value in a certain position, in what i think is l:List(val)? and the result will be  a list with a value in the position p like this (List(val),pos)?

but i get confuse by the whole line l:List(val) isnt this already a lsit why write the list again?

and how will i write this in java? because i belive this is not the code for the operation (method) right?

please can some one explain about datatypes and how to go from the modell to the real think in java? you can take a exampel like for LIST or ARRAY or TABELL? because i feel like i dont get it on how to all this steps works.

thnx for any help.

---

### Post by Shin_Gouki2501 on 2008-04-03
=> stuy is about organizing
- organize how you retrieve information
- inform yourself using the internet, learn how to use search ( wikipedia , google) , learn which source or examples work for you and which not
- wikipedia (english) provides very nice external links which actually contain describiotns, java applets( animations) and explainations.
IT seems you have some Code there which is related to binary search trees or AVL trees. TRy too look up those as depicted above.
If you then have further questions, just ask

---

### Post by CptPicard on 2008-04-03
I'm not sure where you're seeing AVL trees there, Shin. :)

jubej, seems like your teacher is some formalism freak who is trying to shove it down the throats of unprepared students. We actually had a bit of an ideological struggle at my university between two teachers who both taught the undergraduate Data Structures class regarding this.

Frankly, I don't quite understand the syntax of your formal specification. It doesn't, to me, seem to define a function from operation definition to operation result. And no, it has nothing to do with how you'd actually go about implementing it in Java.

First of all you need to think about what an abstract datatype actually is. Essentially you're defining your own abstractions -- sort of your own "entities" for your programs that "describe" some phenomenon or piece of your problem, and behave in ways that help you solve that problem. I know that this sounds a bit esoteric at first sight but bear with me...

First think about the datatypes you get from just plain Java (with a bit of simplification). Let's say you've got Integers, Floats and Characters. The first describe whole numbers, and you can use them to represent quantities. The second ones describe real numbers, and you can use them to describe *continuous* quantities. The last can be used to describe letters. Each of these hold a value of their type.

They also have handy operations -- you can add up Integers and Floats for example, and let's say that you can sort your Characters in alphabetical order. Also, there is the interesting relationship that an Integer is a Float, but not the other way around. So you can use an Integer where-ever you'd use a Float.

Okay, now... let's say you want to start handling Complex numbers. There is no ready-made datatype for holding them. This is where you end up having to *define* your own datatype. You stick a real and imaginary part into a class, and redefine operations so that you can for example add up objects of class Complex. You can also add support for Ints and Floats, so that you can add them as real parts just as well.

Now.. your formal specification would be the axioms of complex numbers. Your implementation can be pretty much anything, as long as it behaves according to that "interface" that has been agreed upon -- external users can use your complex class as a complex number, no matter *how it works inside*.

The rest is just an extension of this simple idea. You can have, for example, a List... which "promises" its users that it will always keep its members in order, and it hand out for example the first and last of the list when asked.

Your teacher really is making this sound so much more difficult than it is... ;)

---

### Post by jubej on 2008-04-03
CptPicard

thnx for your answer, your explanation really helpt me undestand more than the book.

but could you help me with an example of one datatype like list or array?
thay are sure implemented in java but i want to know how would your interface look like and the code in java or c.

maybe if i see a real example then i can understand the steps uncluded.

like lest say that you want to make a datatype list. what will you steps be, let say that the List  can have empty, and you can INSERT and REMOVE elements and maybe inspect and move next etc.

how would you do? 
how will your interface look like and the implemetation.

they have an explanation on LIST here but man, this writer complicates thins like i never seen before.

only the explanation for the interface and the informal explanation took me like 5 hour and i still dont get it.

by the way you should be our class teacher :)

---

### Post by Joe Beam on 2008-04-03
[http://www.docjar.com/html/api/java/util/ArrayList.java.html](http://www.docjar.com/html/api/java/util/ArrayList.java.html)

look at the add,remove, and clear

---

### Post by CptPicard on 2008-04-03
> **jubej said:**
> 
but could you help me with an example of one datatype like list or array?


Well... there you go for a List interface:

[http://java.sun.com/j2se/1.5.0/docs/api/java/util/List.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/List.html)

You could of course abstract it a little bit more to make it non-language-dependant. After all, all lists behave more or less the same... implementation details do not matter that much at the highest abstraction level you think on.

I am being intentionally pedantic here btw and messing with you -- I want you to get the point that we're dealing with abstractions here that on the algorithmics scale of things have nothing to do with implementation language... however, that particular interface is the way it can be made to look like in Java, and that's how Sun's engineers abstracted it.

> 
how would you do? 
how will your interface look like and the implemetation.


Interface and implementation should be, in a sense, separate. As long as your implementation fulfills the promises made by the interface -- that is, it behaves like the interface says it will, everything will be fine.

Interestingly, you could implement your *own* List that implements Sun's List interface... and your implementation could be completely different from what Sun did, *as long as it works the same looked from the outside*.

Now... how to implement a list... that is a data structures class homework assignment -- that is your problem, as a programmer ;)


> 
by the way you should be our class teacher :)

Thanks. Too bad I escaped academia a few years ago due to a nasty experience with a Master's Thesis :)

---

