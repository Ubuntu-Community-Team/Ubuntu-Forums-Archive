---
title: "[Theory]Aliasing? What?"
date: 2009-01-22
forum: Programming Talk
---

### Post by fiddler616 on 2009-01-22
Today, during computer science class (Java) we were talking about how primitive data types stores a value to a specific place in memory, and copying actually copies the value too. Then we talked about how objects point to a memory place, so
```
String a = "   Hey";
String b = a;
a.trim();

```
could lead to problems with b. I already knew this, and was kind of bored, so I raised my hand and asked *why* multiple pointers to the same data were necessary. She said "Oh, it's very necessary, but explaining it now would confuse everyone else--just look up aliasing when you get home." So I did, on Wikipedia, and quite frankly I don't get it.
So could someone please explain aliasing in plainer English? Or should I just take it on faith, and pursue it in college or whatever?
Thanks.

---

### Post by myrtle1908 on 2009-01-22
This will do a better job explaining it than I could: [http://www.vias.org/javacourse/chap08_09.html](http://www.vias.org/javacourse/chap08_09.html)

---

### Post by fiddler616 on 2009-01-22
> **myrtle1908 said:**
> This will do a better job explaining it than I could: [http://www.vias.org/javacourse/chap08_09.html](http://www.vias.org/javacourse/chap08_09.html)

Thanks, but I was hoping more for a why, not a how. If aliasing is such a bug-prone concept, why is it so crucial?

---

### Post by LasherHN on 2009-01-22
I might be wrong but I think it's because it helps when you want a function to use data that's outside of the function.

If for example you are using a really big array (think 1000000+ entries) you would waste memory if you would just copy the array, but if you just have a function to know the reference (the alias) would still be able to use it without having redundancy.

---

### Post by fiddler616 on 2009-01-22
> **LasherHN said:**
> I might be wrong but I think it's because it helps when you want a function to use data that's outside of the function.

If for example you are using a really big array (think 1000000+ entries) you would waste memory if you would just copy the array, but if you just have a function to know the reference (the alias) would still be able to use it without having redundancy.
So instead of letting the function use array foo, you make a *new* pointer name bar, and have *that* point at the array? And this avoids redundancy? Confusing...

---

### Post by LasherHN on 2009-01-22
It avoids redundancy of data, because that way you would still have only one array, instead of having the same data array twice.

---

### Post by fiddler616 on 2009-01-22
> **LasherHN said:**
> It avoids redundancy of data, because that way you would still have only one array, instead of having the same data array twice.
Oh, I see what your saying, sorry.
But why not just have one pointer per array?

---

### Post by LasherHN on 2009-01-22
If you use different functions in your code data is usually exchanged between them. Every time this happens a new reference for the data is created for the new function to use. I think that's the only way I can't really remember if I've ever used two references for the same object inside of one function.

---

### Post by fiddler616 on 2009-01-22
> **LasherHN said:**
> If you use different functions in your code data is usually exchanged between them. Every time this happens a new reference for the data is created for the new function to use.I guess that makes sense, thanks for all your responses! (If only the button wasn't broken...)

---

### Post by lloyd_b on 2009-01-22
> **fiddler616 said:**
> Thanks, but I was hoping more for a why, not a how. If aliasing is such a bug-prone concept, why is it so crucial?
Because the act of creating a copy of an object is wasteful, both in terms of the memory required, as well as the CPU time required for the copying.

Generally speaking, you *never* want to copy an object if you can help it.  In the case of your simple String, it's a pretty trivial process, but consider that if you're dealing with a large, complex object, you could be looking at a copy operation on kilobytes even megabytes of data!

I think part of the problem with the "String" object is that you can create one without a specific "new", so it isn't quite as obvious that you are creating an object.  Take a look at this:
```
MyObject fred = new MyObject(10, 20, 30);
MyObject barney = fred;
```
In this case, the "new" on the first line makes it clear you are creating an object, and assigning a pointer to it in the variable "fred". Thus the "barney = fred" copies the pointer, not the data. But with
```
int wilma = 5;
int betty = wilma;
```
you are dealing with an "int" (which is *not* an object) so there's no pointer involved - the "=" actually copies the data from "wilma" to "betty".  Now look at
```
String pebbles = "Cute";
String bambam = pebbles;
```
Because there's no "new", you may be fooled into thinking that you're copying the data from "pebbles" into "bambam".  But "String" starts with a capital letter, which means it's an object, which means the rules from "fred" and "barney" apply, not the rules from "wilma" and "betty".

(And yes, I *did* watch way too many Flintstones cartoons when I was a kid :-))

It might be clearer if the creators of the language had forced you do an explicit "new" to create the "String" object
```
String a = new String("    Hey");
String b = a;
```
to maintain consistency with how other objects are created, but for whatever reason they chose not to.

---

### Post by fiddler616 on 2009-01-22
> **lloyd_b said:**
> Because the act of creating a copy of an object is wasteful, both in terms of the memory required, as well as the CPU time required for the copying.

Generally speaking, you *never* want to copy an object if you can help it. 
Yeah, I definitely agree with not having duplicates. But the question I have is for this:
```

String foo = new String "kangaroo";
String artichoke = foo;

```
Why do we need to have both foo and artichoke? Everything that happens to foo will happen to artichoke, and the other way around, so why have two pointers? There's only one instance of "kangaroo", but I still feel like it's redundant.

---

### Post by CptPicard on 2009-01-22
Of course you do not *need* two references in a case like that. I believe it is there just for demonstration purposes -- to make the point that there is no value copying going on.

When passing stuff to a function call, it's a whole different matter of course.

---

### Post by slavik on 2009-01-22
please keep in mind that strings are final ;)

EDIT: the whole aliasing thing is so that you can pass objects by value. in java, Object has a copy method (Python calls this clone AFAIK). so if you want to have a new object that is a copy of an old one, you do a = b.copy();

---

### Post by CptPicard on 2009-01-22
Actually it's clone() in Java as well.

---

### Post by fiddler616 on 2009-01-22
> **CptPicard said:**
> Of course you do not *need* two references in a case like that. I believe it is there just for demonstration purposes -- to make the point that there is no value copying going on.

When passing stuff to a function call, it's a whole different matter of course.
Thank you!
I think I'll worry about function calls later though :)

*Tries to mark as solved*

---

### Post by fiddler616 on 2009-01-22
> **slavik said:**
> please keep in mind that strings are final ;)

EDIT: the whole aliasing thing is so that you can pass objects by value. in java, Object has a copy method (Python calls this clone AFAIK). so if you want to have a new object that is a copy of an old one, you do a = b.copy();
*Thanks*
Just to get my terminology straight, what's slicing? I could've sworn I've heard that in the context of copying immutable data types, but I really couldn't say...

---

### Post by lloyd_b on 2009-01-22
> **fiddler616 said:**
> Yeah, I definitely agree with not having duplicates. But the question I have is for this:
```

String foo = new String "kangaroo";
String artichoke = foo;

```
Why do we need to have both foo and artichoke? Everything that happens to foo will happen to artichoke, and the other way around, so why have two pointers? There's only one instance of "kangaroo", but I still feel like it's redundant.The only reason I can think of offhand is to have a backup of the original object.  For instance```
String foo = new String ("kangaroo");
String bar = foo;
...
foo = new String("wallaby");
```
At this point, you have the original object stored in "bar", and a new object stored in "foo".  If you hit some sort of critical failure, and want to back out of what you've done, you can do so easily.

Note that this a pretty contrived example - in the real world, the need for this is pretty rare - as a rule, you should avoid having redundant pointers to the same object, simply to avoid the potential bugs associated with aliasing.

---

### Post by CptPicard on 2009-01-22
Now, that's a C/C++ concept... when you have a struct X that has, say, two ints, and struct Y that has just one int, if you pass a struct X by value into a function expecting a struct Y, you lose the other int -- it gets "sliced off".

---

### Post by fiddler616 on 2009-01-22
> **CptPicard said:**
> Now, that's a C/C++ concept... when you have a struct X that has, say, two ints, and struct Y that has just one int, if you pass a struct X by value into a function expecting a struct Y, you lose the other int -- it gets "sliced off".
Oh. Maybe I read about it when it was dealing with taking bits of lists? i. e.
[PHP]
>>>x =  [1, 2, 3]
>>>y = x[1:]
>>>print y
[2, 3][/PHP]

---

### Post by fiddler616 on 2009-01-22
> **lloyd_b said:**
> The only reason I can think of offhand is to have a backup of the original object.  For instance```
String foo = new String ("kangaroo");
String bar = foo;
...
foo = new String("wallaby");
```
At this point, you have the original object stored in "bar", and a new object stored in "foo".  If you hit some sort of critical failure, and want to back out of what you've done, you can do so easily.

Note that this a pretty contrived example - in the real world, the need for this is pretty rare - as a rule, you should avoid having redundant pointers to the same object, simply to avoid the potential bugs associated with aliasing.
OK, that makes a lot of sense, thanks.

---

### Post by slavik on 2009-01-22
yeah, that slicing is when you want a slice of the pie ... not the whole thing :)

---

### Post by fiddler616 on 2009-01-22
> **slavik said:**
> yeah, that slicing is when you want a slice of the pie ... not the whole thing :)Maybe I'm too intuitive of a person, but that actually made perfect sense to me, and cemented a concept into my brain. Nice one!
Edit: Dipped in Ubuntu on the 522nd post--well played with the randomization, matthew--I really wasn't expecting it.

---

