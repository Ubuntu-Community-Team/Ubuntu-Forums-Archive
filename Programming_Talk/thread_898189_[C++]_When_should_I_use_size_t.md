---
title: "[C++] When should I use size_t?"
date: 2008-08-23
forum: Programming Talk
---

### Post by NovaAesa on 2008-08-23
I understand *what* std::size_t is, I just don't know when and where to use it. It's just a typedef for unsigned int right?

I'm totally confused about when and where to use it. I have googled around and it seems that it needs to be used when referring to the size of something? For instance, I am making a linked list, so which parts would I have as size_t and which parts as unsigned int, or as just normal int?

If you people could clear this up for me I would be greatful.

---

### Post by slavik on 2008-08-23
IMO, you answered your own question, but an example of size_t use would be when you want to find out the size of the list (how many elements there are).

---

### Post by NovaAesa on 2008-08-23
Okay so if I have a method that returns the number of nodes in the list, I would use size_t as the methods return type, right? This is a somewhat obvious case, the return value **is** the size of something. I'm looking for more of a hard and fast definition as to where to use it though. Say for example I write a method that will return a pointer to the data in the nth node in the list, what type should n (as an argument to the method) be? This case doesn't seem to be as well defined. The n isn't the size of linked list as such, but it is always going to be less than or equal to it. So what to use in this case, size_t or int?

Hope that made sense.

---

### Post by slavik on 2008-08-23
> **NovaAesa said:**
> Okay so if I have a method that returns the number of nodes in the list, I would use size_t as the methods return type, right? This is a somewhat obvious case, the return value **is** the size of something. I'm looking for more of a hard and fast definition as to where to use it though. Say for example I write a method that will return a pointer to the data in the nth node in the list, what type should n (as an argument to the method) be? This case doesn't seem to be as well defined. The n isn't the size of linked list as such, but it is always going to be less than or equal to it. So what to use in this case, size_t or int?

Hope that made sense.
it does ... in C++ you would return a reference that points to the node you want. :)

---

### Post by NovaAesa on 2008-08-23
Okay, but what about the parameter to the method? Should it be something like this:
```
Node* getNode(int n);
```
or,
```
Node* getNode(std::size_t n);
```
(these would obviously be in the .h file as they are just the definitions rather than the actual implimentations)

---

### Post by slavik on 2008-08-23
I would use the first one, as you are looking at a node number something, not at getnode with a size parameter.

edit: not only that, but you could handle negative indexes, too. like -1 would give you the last node and such. (Perl does this with arrays).

---

### Post by NovaAesa on 2008-08-23
So you're saying that size_t is only ever used when I am talking about the size of something? Never used when I am talking about something that is only related to size? Sorry if I seem a bit slow with this, I just want to make user I have an exact understanding of it.

---

### Post by slavik on 2008-08-23
when you want the 5th node, the 5 is not really related to size, the 5 is a position, but when you ask a list how big it is, you get a size back.

---

### Post by StOoZ on 2008-08-23
so for a node , why not to use a ptrdiff_t instead of size_t?

---

### Post by dribeas on 2008-08-23
> **NovaAesa said:**
> 
```
Node* getNode(std::size_t n);
```


My advice would be: do it as the standard does. Standard list does not have a method to return the nth element but std::vector has. 
```

reference operator[](size_type n);
const reference operator[](size_type n) const;

```
Now the rationale: whenever you ask for the n-th element, that has to be compared against the size of the list. If you index and size types are different (size or signed-ness) you can run into trouble. As an example, assume that for some implementation with size_t being unsigned int (32bits) you create a list/vector with 2^31 + 1 elements. If you used signed ints as indexes you could not be able to reach the last element with a positive index.

   David

---

### Post by NovaAesa on 2008-08-23
> **dribeas said:**
> 
Now the rationale: whenever you ask for the n-th element, that has to be compared against the size of the list. If you index and size types are different (size or signed-ness) you can run into trouble. As an example, assume that for some implementation with size_t being unsigned int (32bits) you create a list/vector with 2^31 + 1 elements. If you used signed ints as indexes you could not be able to reach the last element with a positive index.

That's sort of what I was thinking... That does make sense really. Position in the list is *kinda* related to size.

I would ask my proff for my programming class directly, but 3 day weekend, so I wont see him til Tuesday.

---

### Post by nvteighen on 2008-08-23
Though it seems you have solved your problem by finding an alternative. For you to know:

size_t is just an unsigned int.

Why should you use it instead of int when referring to sizes or array indices? To avoid having negative sizes or positions and subsequent illegal memory access... By using size_t you don't have to check if the variable is > 0 because it will always be by definition.

But, size_t can be treacherous. If you happen to assign, e.g -2 to a size_t variable, the number will be substracted from the size_t's limit and you'll probably get a big positive number that will also result in illegal memory access...

size_t may also be useful when you need to use integer's memory space at full. You surely know that if in your platform (signed) int is 4-bytes long, you'll be able to use 2-byte long positives and 2-byte long negatives (aprox.). With size_t, unsigned int, you can use 4-byte long positive numbers, specially useful when you certainly know that some variable will never hit a negative value.

---

### Post by mujambee on 2008-08-23
> **nvteighen said:**
> size_t may also be useful when you need to use integer's memory space at full. You surely know that if in your platform (signed) int is 4-bytes long, you'll be able to use 2-byte long positives and 2-byte long negatives (aprox.). With size_t, unsigned int, you can use 4-byte long positive numbers, specially useful when you certainly know that some variable will never hit a negative value.

Could you elaborate?

As far as I know, if an int is 4-bytes long, that is, 32-bit long, you can use 31-bit positives and 31-bit negatives OR 32-bit unsigneds.

What do you mean by 2-byte long positives and 2-byte long negatives.

---

### Post by nvteighen on 2008-08-23
> **mujambee said:**
> Could you elaborate?

As far as I know, if an int is 4-bytes long, that is, 32-bit long, you can use 31-bit positives and 31-bit negatives OR 32-bit unsigneds.

What do you mean by 2-byte long positives and 2-byte long negatives.

**EDIT:** Oh man... now I realize what was my mistake.. yeah... 31 bits = 2 bytes... great! Sorry.

It's because, to represent negative values, you usually use the Two's complement (see [http://en.wikipedia.org/wiki/Two%27s_complement](http://en.wikipedia.org/wiki/Two%27s_complement)).

What really happens is that, when you have a signed data type, you have to hold the sign somewhere. Conventionally, the first bit is used to represent the sign: 0 is +, 1 is -. So, in a (signed char) value, your number will have to fit in 31-bits, so the real upper limit is reduced to the half... to both sides of zero. In a unsigned value, all 32-bits are used to represent the value.

---

### Post by mujambee on 2008-08-23
Yes, I already knew that.

What puzzles me is [COLOR=Navy]*"2-byte longs"*[/COLOR].  What do you mean by 2 bytes?  31 bits is not 2 bytes, is almost 4!!

---

### Post by nvteighen on 2008-08-23
> **mujambee said:**
> Yes, I already knew that.

What puzzles me is [COLOR=Navy]*"2-byte longs"*[/COLOR].  What do you mean by 2 bytes?  31 bits is not 2 bytes, is almost 4!!

See my edit above. It just means I'm stupid today :p

---

### Post by mujambee on 2008-08-23
:p

---

### Post by dribeas on 2008-08-23
> **nvteighen said:**
> size_t is just an unsigned int.
...
But, size_t can be treacherous. If you happen to assign, e.g -2 to a size_t variable, the number will be substracted from the size_t's limit and you'll probably get a big positive number that will also result in illegal memory access...


size_t is not required to be unsigned int, but rather an unsigned integer type. Well, that is taking things to the limit: in most cases it is unsigned int.

Sadly enough assignment of a negative integer into an unsigned type does not fire warnings... But nevertheless, you only need to care for numbers greater than some limit, which you have to care about in both cases.

---

