---
title: "[C] Pass array of structs and modiy array inside struct"
date: 2010-08-21
forum: Programming Talk
---

### Post by simeon87 on 2010-08-21
Ok, despite all the similar threads written on this, I'm still struggling with it.

I want to pass an array of structs to a function and to modify a part of a struct, which itself is an array.

I have a typedef struct as follows:

```
typedef struct Slot {
    int x;
    int y;
    int dir; // 0 = across, 1 = down
    int length;
    int count;
    int done; // {0, 1}
    char cs[MAX_WORD_LENGTH];
    int fixed[MAX_WORD_LENGTH]; // 0 = read/write, 1 = read
} Slot;
```

I have a function clear_slot:

```
void clear_slot(Slot* slots, int n_slots, int index) {
    Slot slot = slots[index];
    // other code here
    printf("%i can be cleared\n", l);
    slot.cs[l] = ' ';
    printf("%i is now %c\n", l, slot.cs[l]);
}
```

I declare my array of structs like this, after which I populate it:

```
Slot slots[n_slots];
```

And finally, I call the function like this:

```
clear_slot(slots, n_slots, recent_index);
```

Using printf, I can confirm the cs array of a Slot struct is modified correctly. But the change is no longer visible after the function is over.

So I must be modifying a copy instead of the real struct but I'm already passing a pointer to the first element of the array so how come I'm not pointing to the real struct?

---

### Post by sharathcshekhar on 2010-08-21
In your function clear_slot()
```

Slot slot = slots[index];

```
Should be 
```

Slot *slot = &(slots[index]);
slot -> cs[l] = ' ';

```

---

### Post by simeon87 on 2010-08-21
Thank you very much sharathcshekhar, that indeed works! I'll think a bit more as to why it works: I thought slots[index] would be sufficient but apparently you need to get a pointer explicitly to modify it properly.

---

### Post by MadCow108 on 2010-08-21
you do not need to get the pointer explicitly, but is often saves some typing
You can also do it like this:
```

slots[index].cs[l] = ' ';

```

But this here:
```

Slot slot = slots[index];

```
makes a copy of slots[index] which you modify. This copy is then deleted when the function returns and the changes lost.
= operator on C structures is equivalent to memcpy(dest_ptr, source_ptr, sizeof(structure))

---

### Post by simeon87 on 2010-08-21
> **MadCow108 said:**
> you do not need to get the pointer explicitly, but is often saves some typing
You can also do it like this:
```

slots[index].cs[l] = ' ';

```

But this here:
```

Slot slot = slots[index];

```
makes a copy of slots[index] which you modify. This copy is then deleted when the function returns and the changes lost.
= operator on C structures is equivalent to memcpy(dest_ptr, source_ptr, sizeof(structure))

Ah, I learned something new there, thanks :)

---

### Post by dwhitney67 on 2010-08-21
> **simeon87 said:**
> 
I declare my array of structs like this, after which I populate it:

```
Slot slots[n_slots];
```


FYI... this type of declaration does not follow ANSI C standards.  It may work for you today, but tomorrow?

---

### Post by Npl on 2010-08-21
> **dwhitney67 said:**
> FYI... this type of declaration does not follow ANSI C standards.  It may work for you today, but tomorrow?Its not in the age old ANSI C Standard, but its in C99. It should work everywhere today and if not then it will hopefully fixed tomorrow.

---

