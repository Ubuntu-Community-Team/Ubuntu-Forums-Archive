---
title: "Problem with 'const' variables"
date: 2008-10-07
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-10-07
I am having trouble using const variables with functions that expect non-const variables of the same type. Here's a recent example. I have a function which returns **const GList***. I want to know the size of this list but the **g_list_length(GList*)** doesn't compile. I get this error: > error: invalid conversion from &#8216;const GList*&#8217; to &#8216;GList*&#8217;

So how do I get the size of a const GList?
EDIT: The function that returns const is a gstreamer function, not my own.

---

### Post by Tomosaur on 2008-10-07
> **SledgeHammer_999 said:**
> I am having trouble using const variables with functions that expect non-const variables of the same type. Here's a recent example. I have a function which returns **const GList***. I want to know the size of this list but the **g_list_length(GList*)** doesn't compile. I get this error: 

So how do I get the size of a const GList?

Possibly dumb question - are you sure you really need a const? Obviously I may be being an idiot here - but it would definitely solve your problem. Simplest answer, so it's worth a go :P

---

### Post by SledgeHammer_999 on 2008-10-07
Oops sorry, the function "I have" isn't mine... It is a function of gstreamer...

---

### Post by Trail on 2008-10-07
Well, you can always hard-cast it to a Glist* or use const_cast<Glist*>(foo).

The essence, though, is that your own function is returning a pointer to a Glist object that should be constant. g_list_length() does not guarantee that it will not make alterations to the object, so by default the compiler rejects this to guarantee const-correctness. If you are sure g_list_length() doesn't change it, then just cast it to non-const (but document this). Otherwise, you may have to rethink if your object really has to be immutable, to re-plan your const-correctess, or to supply a const version of g_list_length().

---

### Post by kpatz on 2008-10-07
> **SledgeHammer_999 said:**
> I am having trouble using const variables with functions that expect non-const variables of the same type. Here's a recent example. I have a function which returns **const GList***. I want to know the size of this list but the **g_list_length(GList*)** doesn't compile. I get this error: 

So how do I get the size of a const GList?Cast the variable to a non-const, for example:

[php]
  const GList* p;
  p = function_that_returns_the_const_Glist();
  q = g_list_length((Glist*)p);  // Cast const to non-const here
[/php]

---

### Post by SledgeHammer_999 on 2008-10-07
Hey guys the const is returned by the a gstreamer function.
@kpatz
This is what I did... I just wanted to know if there was another way, maybe better/safer.

---

### Post by Trail on 2008-10-07
const_cast :P

---

### Post by DrMega on 2008-10-07
> **SledgeHammer_999 said:**
> Hey guys the const is returned by the a gstreamer function.
@kpatz
This is what I did... I just wanted to know if there was another way, maybe better/safer.

Are you sure? I'm not for a second saying your wrong, its a long time since I've done any original C, but I don't understand why a function would return a const, or why you would have a const pointer.

consts don't change after declaration, so I can't see why one would be returned from a function, and as you usually declare a pointer and then allocate some memory, and use that pointer to point to the start of the allocated memory, I can't see why you'd have a const pointer.

Of course I might have missed the point entirely.

---

### Post by Tomosaur on 2008-10-07
Ah well if you have no control over the returned const, then casting to a non-const is your only real way to go.

Have you tried making a shallow copy using g_list_copy, or does that give you the same issue?

Either way it seems like your best option is to just cast to a non-const when you need to.

---

### Post by SledgeHammer_999 on 2008-10-07
I also asked in #gstreamer channel at IRC and they said the typecast is ok as long as I don't modify data with the list... So I am going with the typecast. Thank you all.

---

