---
title: "Proof of Concept: String linked list, practical?"
date: 2009-08-22
forum: Programming Talk
---

### Post by OutOfReach on 2009-08-22
Hey guys,
I was just sitting around, very bored. And all of a sudden I started thinking about strings. (I absolutely dread c strings). And I came up with the idea of strings made up of linked lists.

For example, every node is a character, something like this:
'H'->'e'->'l'->'l'->'o'->NULL

I came up with a rather pathetic pros/cons list:
**Pros**:
*Easier string operations (e.x. node addition/removal). Thanks to the nature of linked lists.
*No need to worry about null terminators, etc.
*Not that heavy on resources. (I'm debating over this, see below)
*End-developer has something that 'Just Works (tm)'

**Cons**:
*Slight operation performance decrease? Since, we do need to go through all the nodes (characters) to get to the one we want.

The reason I think it isn't that heavy is because each node is composed of a character (8 bytes) and a pointer to the next node. The main linked list contains a pointer to the head and a pointer to the tail, also an int (4 bytes). So if a string had 10 characters, it would be 8*10=80, 80+4=84, 84 bytes in total. Is this correct? I'm not sure.

This kind of string, me thinks, would not be so good for large strings (e.x. paragraphs).

Sources can be downloaded [here]("http://dl.getdropbox.com/u/961374/linked_str.tar.gz").
To build, follow these steps:
```

mkdir build
cd build
cmake ..
make
./testing_app

```

So, tell me what you think about the concept, not the code (the code was just quickly hacked together, but critiques are welcome though). **Would it be practical in real world use?**

(Note: a somewhat better (longer) explanation is at [my blog]("http://null-reference.blogspot.com/2009/08/stringsmade-out-of-linked-lists-whaaa.html"))

---

### Post by JordyD on 2009-08-22
Reminds me of [Greenspun's Tenth Rule]("http://en.wikipedia.org/wiki/Greenspun%27s_Tenth_Rule").

---

### Post by lisati on 2009-08-22
If it works well for what you're doing, go for it! 
Perhaps it's the nature of the programs I've worked on in the past, but I still find the idea of the characters being in consecutive memory locations easier to grasp. Comparisons can be easier if you don't have an excess of pointers to work with.

---

### Post by Can+~ on 2009-08-23
> The reason I think it isn't that heavy is because each node is composed of a **character (8 bytes)** and a pointer to the next node. The main linked list contains a pointer to the head and a pointer to the tail, also an int (4 bytes). So if a string had 10 characters, it would be 8*10=80, 80+4=84, 84 bytes in total. Is this correct? I'm not sure.

8 Byte Character?

ASCII char [1B]
Pointer(x86) [4B]

> Pros:
*Easier string operations (e.x. node addition/removal). Thanks to the nature of linked lists.

I'm not seeing it. Yes, you could delete some characters, but adding them? Having to allocate dynamically **each** letter and then link everything? How's that easier?

Heap can get Fragmented. Having each character requesting memory, would be like taking the highway to that.

> *No need to worry about null terminators, etc.

If you wrap a char* and a variable int inside a struct and make sure it updates accordingly, you get that exact same benefit.

> *Not that heavy on resources. (I'm debating over this, see below)
Cons:
*Slight operation performance decrease? Since, we do need to go through all the nodes (characters) to get to the one we want.


The processor will waste time jumping from location to location just to read everything, when current C-strings are pretty much linear:

Normal: "Start at 0x???????, read X bytes"
List: "Start at 0x??????? read 5 bytes, jump to address, repeat"

> *End-developer has something that 'Just Works (tm)'

End-developer would've switched to a higher level language if strings are that much of a hassle, even C++ has a string class (Java, Python, Perl, all of them work strings naturally). You can even hack your own (char* + int size) struct and use it (see above), or use an already existing library like better-string.

Sorry, I don't see the advantages. I'm usually all-in for making things easier rather than faster, but I don't see anything particularly good about this.

I also had a similar idea, but instead of per-letter, it was per-word, but I eventually abandoned it.

---

### Post by OutOfReach on 2009-08-23
> **Can+~ said:**
> 8 Byte Character?

ASCII char [1B]
Pointer(x86) [4B]

Ahh, forgive me then. So it would indeed be a rather large data type.

> 
I'm not seeing it. Yes, you could delete some characters, but adding them? Having to allocate dynamically **each** letter and then link everything? How's that easier?

Heap can get Fragmented. Having each character requesting memory, would be like taking the highway to that.

True, wouldn't the same be true for normal char * strings? You have to realloc space for the extra character. Linking everything together doesn't require that much of a process, but I see where you're going.

> 
The processor will waste time jumping from location to location just to read everything, when current C-strings are pretty much linear:

Normal: "Start at 0x???????, read X bytes"
List: "Start at 0x??????? read 5 bytes, jump to address, repeat"

Yes, this was my main doubt, jumping through everything to get to a certain point. Usually, in a small string this should take short time, but in longer strings you might definitely be able to see the performance hit.

> 
End-developer would've switched to a higher level language if strings are that much of a hassle, even C++ has a string class (Java, Python, Perl, all of them work strings naturally). You can even hack your own (char* + int size) struct and use it (see above), or use an already existing library like better-string.

Well, I'm still here :), and yes I already extensively use the better-string library for most of my projects. But why not provide a non-hassle way for handling strings? Strings are trivial, they shouldn't be such a hassle.

In my opinion, I think the advantages level out the disadvantages. For example, splitting a string at a certain point (.split() function in Python) would be harder working with raw C strings, linked lists on the other hand would be somewhat easier.

---

### Post by Can+~ on 2009-08-23
> **OutOfReach said:**
> In my opinion, I think the advantages level out the disadvantages. For example, splitting a string at a certain point (.split() **[COLOR=#CC0000]method[/COLOR]** in Python) would be harder working with raw C strings, linked lists on the other hand would be somewhat easier.

The C-approach to splitting, is usually using the [strtok]("http://www.cplusplus.com/reference/clibrary/cstring/strtok/") and using the value "on the moment", instead of storing it, but you can always go ahead and store it.

And strings are trivial for higher-level languages because of the abstraction involved. C sees everything (even functions) as just blocks of memory waiting to be worked with (Imperative Paradigm).

And I remember writing something about this type of ["DIY" way of life]("http://lambdagrok.wikidot.com/forum/t-153164/blub-paradox-and-mental-models-of-computation#post-509717").

---

### Post by napsy on 2009-08-23
A way practical approach would be if you implement a string structure if the way how C string work bothers you that much.

```

typedef struct {
    char  *string;
    size_t length;
} string_t;

```

Then you can implement string operations for your type like for copying, comparison, etc.

---

### Post by OutOfReach on 2009-08-23
> **Can+~ said:**
> 
And I remember writing something about this type of ["DIY" way of life]("http://lambdagrok.wikidot.com/forum/t-153164/blub-paradox-and-mental-models-of-computation#post-509717").

Hmm, that's a very interesting read, not only that but the whole blub paradox concept. and I must say I agree with most of it, and it has made me think a little. but, at times there comes a situation were you need to use a lower-level language such as C, but you would still like some level of simplicity with things such as strings, even if that means reinventing the wheel.

As for the original idea, I can safely say that it does have it's flaws, maybe I'll fix the general idea when I have time, but I'll just stick with better-string for now :)

---

### Post by Lux Perpetua on 2009-08-23
> **OutOfReach said:**
> 
I came up with a rather pathetic pros/cons list:
**Pros**:
*Easier string operations (e.x. node addition/removal). Thanks to the nature of linked lists.
...As far as I can see, linked lists make it easy to add and remove stuff at an arbitrary location (provided you already have a reference to that location), but everything else belongs to arrays. For example, random access to elements in a linked list is expensive but very cheap on an array. Arrays use less memory. Sequential access, while straightforward on a linked list, is still probably slower than on an array, since it involves dereferencing a pointer rather than simply incrementing one.

---

### Post by OutOfReach on 2009-08-23
> **Lux Perpetua said:**
> As far as I can see, linked lists make it easy to add and remove stuff at an arbitrary location (provided you already have a reference to that location), but everything else belongs to arrays. For example, random access to elements in a linked list is expensive but very cheap on an array. Arrays use less memory. Sequential access, while straightforward on a linked list, is still probably slower than on an array, since it involves dereferencing a pointer rather than simply incrementing one.

Yes, fact is that every datatype has it's advantages/disadvantages.
Hmm, the dereferencing shouldn't be a problem, IMO sequential access might be faster on arrays.

---

### Post by hessiess on 2009-08-23
A lot of functional languages, i.e. Haskell do store strings as a linked list. In a functional language manipulating linked list strings is slower as the data is imitable, resulting in a lot of mallocing under the hood. In a language like C where you have mutable data it should be possible to make it pretty fast, espetily if you store an array of pointers into the list, for example to every hundredth or so node. removing the need to recourse through the whole list to get to a spasific part.

---

### Post by OutOfReach on 2009-08-23
> **hessiess said:**
> A lot of functional languages, i.e. Haskell do store strings as a linked list. In a functional language manipulating linked list strings is slower as the data is imitable, resulting in a lot of mallocing under the hood. In a language like C where you have mutable data it should be possible to make it pretty fast, espetily if you store an array of pointers into the list, for example to every hundredth or so node. removing the need to recourse through the whole list to get to a spasific part.

Indeed, I have considering something like that, a cache of some sort. Then I thought that it might, just might over complicate things a bit. but I'll definitely look for things similar to that idea since it would significantly increase lookup times

---

### Post by nvteighen on 2009-08-23
It may be a good idea when you need a quick string data structure with basic capabilities in a project of yours, though my instinct tells me you'll need a double linked list to have it working well.

The array based model in C is actually not that bad... You've got a number identifying each character in the string for direct access. The issue lies actually somewhere else, in C static typing, which forces you to either specify the size of the string at compile time... making your string immutable in length or use dynamic memory and forcing yourself to use by malloc() and friends. And C static typing is not its own fault, but actually derived from how memory works in computers.

So, you may want to research on new memory architectures... :p

---

