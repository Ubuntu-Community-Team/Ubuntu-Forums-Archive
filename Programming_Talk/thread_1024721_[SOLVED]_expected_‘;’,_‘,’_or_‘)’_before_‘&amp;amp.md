---
title: "[SOLVED] expected ‘;’, ‘,’ or ‘)’ before ‘&amp;amp;’ token -- wtf?"
date: 2008-12-29
forum: Programming Talk
---

### Post by Bulletbeast on 2008-12-29
Hi all. Resumed work on libdissonance today after a break, for some reason prefixing functions with an underscore was breaking them. Feels good to be back. Anyway, can anyone tell me why does this line:

**int tune(note* tuning, int &strings, const char* tunestr)**

result in:

**chord.c:192: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;&&#8217; token**

?

---

### Post by mike_g on 2008-12-29
if "strings" is meant to be a pointer then:
```
int tune(note* tuning, [COLOR="DarkRed"]int *strings[/COLOR], const char* tunestr)
```
or, if its a pointer to a pointer:
```
int tune(note* tuning, int **strings, const char* tunestr)
```
AFAIK the & bit should not appear in your prototype.

---

### Post by Bulletbeast on 2008-12-29
I'm trying to pass strings by value in order to return several values, and use the return statement for an error code. After said break from writing in C, it somehow eludes my mind how to do this, so I looked it up:

```
void foo(int &fe, int &fi, int fo)
{
   fe += fo;
   fi += fe;
   return;
}
```

Amirite?

---

### Post by nvteighen on 2008-12-29
> **Bulletbeast said:**
> I'm trying to pass strings by value in order to return several values, and use the return statement for an error code. After said break from writing in C, it somehow eludes my mind how to do this, so I looked it up:

```
void foo(int &fe, int &fi, int fo)
{
   fe += fo;
   fi += fe;
   return;
}
```

Amirite?
That's C++ (references), not C! :)

---

### Post by Bulletbeast on 2008-12-29
Oh.
And if I'm sticking to C only, what do I do?

---

### Post by nvteighen on 2008-12-29
Well, you can't pass strings by value, because they are always a pointer to its first character. You have to do what mike_g has told you in post #2

---

### Post by Bulletbeast on 2008-12-29
Lol, "strings" is the name of an int, as in the strings of a musical instrument (: So what do I do in that case?

---

### Post by nvteighen on 2008-12-29
> **Bulletbeast said:**
> Lol, "strings" is the name of an int, as in the strings of a musical instrument (: So what do I do in that case?
Ah, ok!

You want "strings" to be modified, right? ok, using the code from your post:
```

void foo(int *fe, int *fi, int fo)
{
    *fe += fo;
    *fi += *fe;
    return;
}

```

The * dereference operator accesses the pointer's content for reading or writing. Yes, it's rather weird that you also use it when declaring a pointer, but C's philosophy is to declare variables as they look when you use them. Using a pointer without * will manipulate the memory address the pointer holds, not its contents.

---

### Post by Bulletbeast on 2008-12-29
Yeah, I think I understand it now. Thanks a lot! (:

EDIT: Yes, works like a bloody charm, it does, and so does my program. (:

---

