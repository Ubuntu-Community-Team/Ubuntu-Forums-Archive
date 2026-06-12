---
title: "memory allocation question"
date: 2008-04-12
forum: Programming Talk
---

### Post by StOoZ on 2008-04-12
I would like to know, what is the difference between these two:
> char* ptr = new char[4]
ptr = "ggg";
delete[] ptr;
ptr = new char[5];

and:
> char* ptr = new char[4]
ptr = "ggg";
ptr = new char[5];


as you can see, one uses a delete , and the other , just plain renewing, I cant figure out, what is the difference of the final outcome.

---

### Post by Wybiral on 2008-04-12
Run the second one in a loop and see what happens :)

Don't! It's not "renewing" it's just grabbing more and more memory and losing it to the abyss. You MUST explicitly free all memory that you allocate with "delete".

---

### Post by aks44 on 2008-04-12
Or, just run the first one and see what happens... I wouldn't be surprised if you get a core dump...

---

### Post by Wybiral on 2008-04-12
> **aks44 said:**
> Or, just run the first one and see what happens... I wouldn't be surprised if you get a core dump...

lol, I missed that one.

When you say
```

ptr = "string";

```

Keep in mind that "string" is a pointer to a string literal... You're not copying that string into the memory you allocated, you're actually just losing grid of that allocated memory (lost to the abyss). You have to copy it.

But, you should be using the string class for this anyway...

---

### Post by StOoZ on 2008-04-12
ok , so lets assume I used strcpy for the first one and not just "string" which is constant.

when I use the new, without delete, if I have this :
char* ptr = new char[5];
strcpy(ptr,"fine");

and I do this:
ptr = new char[10];

I assumed that I I'll try to check the output of:
ptr[0];
I'll see the letter 'f'.,  but its not the case,even thought the address is the same, how come?

---

### Post by aks44 on 2008-04-12
> **StOoZ said:**
> ok , so lets assume I used strcpy for the first one and not just "string" which is constant.

when I use the new, without delete, if I have this :
char* ptr = new char[5];
strcpy(ptr,"fine");

and I do this:
ptr = new char[10];

That's called a *_memory leak_*. Again, you *_have to_* [COLOR="DarkRed"]delete[/COLOR] any [COLOR="DarkRed"]new[/COLOR]'ed memory, and [COLOR="DarkRed"]delete[][/COLOR] any [COLOR="DarkRed"]new[][/COLOR]'ed memory.


> **StOoZ said:**
> but its not the case,even thought the address is the same, how come?

The pointer's address obviously stays the same, but the pointed-to address (IOW the *_contents_* of the pointer) changed.


Keep in mind that a pointer is a memory area (aka. variable) that contains the address of another memory area.

---

### Post by lnostdal on 2008-04-12
offtopic: beware; you have just found an orange with two layers of peeling on it .. O_O .. edit: and, lol, not even tinfoil can save you now .. (to quote your sig., aks44)

ontopic: ok, seriously .. pointers can be confusing .. draw some boxes and arrows .. it helps sometimes =)

---

