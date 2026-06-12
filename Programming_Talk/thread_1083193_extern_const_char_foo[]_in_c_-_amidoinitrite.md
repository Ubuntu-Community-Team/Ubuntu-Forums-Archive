---
title: "extern const char* foo[] in c - amidoinitrite?"
date: 2009-02-28
forum: Programming Talk
---

### Post by Bulletbeast on 2009-02-28
Hi, guys. I have the following question. Programming in C, I have a header file which is included in every file of my project, and, among other things, defines a const char* foo[], which I want to have available in any file that needs it.

However, I have read that having the following in the header file is wrong:
**const char* foo[] = { "qwe", "asd", "zxc" };**
And, indeed, it gives me an error about a duplicate definition.

I have tried putting the following in my header file:
**extern const char* foo[];**
And initializing it from main.c like this:
[b]const char* foo[0] = "qwe";
const char* foo[1] = "asd";
const char* foo[2] = "zxc";[/b]
but this, depending on exact details, either doesn't compile or segfaults the first time the array is read (which is from another module).

So, eh, what's the correct way of doing this?

---

### Post by movieman on 2009-02-28
const char *foo[] = { "qwe", "asd", "zxc" };

---

### Post by WW on 2009-02-28
To expand on movieman's post, put
```

const char* foo[] = {"qwe","asd","zxc"};

```
in just one C file (e.g. in main.c) and put
```

extern const char* foo[];

```
in your header file.

---

### Post by Bulletbeast on 2009-03-01
This was how I was doing it originally, but then why does the folowing code segfault?

```
for (i=0; i<EQUIP_SLOTS; i++)
{
  printf("%s", equip_slots[i]);
}
```

---

### Post by nvteighen on 2009-03-01
> **Bulletbeast said:**
> This was how I was doing it originally, but then why does the folowing code segfault?

```
for (i=0; i<EQUIP_SLOTS; i++)
{
  printf("%s", equip_slots[i]);
}
```
Difficult to know without looking at the whole source. Are you sure EQUIP_SLOTS is the correct value?

---

### Post by Bulletbeast on 2009-03-01
And indeed, this seems to have been the problem. Stupid o' me. Strange how it didn't output the first few values, though.

---

