---
title: "need help while reading strings from file"
date: 2009-05-01
forum: Programming Talk
---

### Post by TheLions on 2009-05-01
ok I need to make a C program that will read strings from a text file and put it in a memory as a array of strings.

file look like
aaa bbb ccc ddd ....
111 222 333 444 ....

I want to read only first line, but the problem is that first line can contain form 1 to 30 different strings.

Can anybody make a code form me or even detailed pseudocode?

---

### Post by BugFixBug on 2009-05-01
> **TheLions said:**
> ok I need to make a C program that will read strings from a text file and put it in a memory as a array of strings.

file look like
aaa bbb ccc ddd ....
111 222 333 444 ....

I want to read only first line, but the problem is that first line can contain form 1 to 30 different strings.

Can anybody make a code form me or even detailed pseudocode?

you could do something with a fgetc and check for (\r)\n to stop getting chars (finding end of line) and check for whitespace to separate words

---

### Post by MeLight on 2009-05-01
each string is 3 letters long and they are separated by a single space?

---

### Post by TheLions on 2009-05-01
> **BugFixBug said:**
> you could do something with a fgetc and check for (\r)\n to stop getting chars (finding end of line) and check for whitespace to separate words

Can you please elaborate how to do that?
I spent 3 hours messing with scanf and loops and I didn't succeeded.:(


> **MeLight said:**
> each string is 3 letters long and they are separated by a single space?

No string have from 1 to 20 chars, and yes they are separated by single space.

---

### Post by Arndt on 2009-05-01
> **TheLions said:**
> Can you please elaborate how to do that?
I spent 3 hours messing with scanf and loops and I didn't succeeded.:(




No string have from 1 to 20 chars, and yes they are separated by single space.

You could look at 'strtok' too.

---

### Post by BugFixBug on 2009-05-01
> **TheLions said:**
> Can you please elaborate how to do that?
I spent 3 hours messing with scanf and loops and I didn't succeeded.:(



i dont have the time to make a ready to go script but ill give you a rough example

```

for ( /* get char with fgetc and save it // in for *** long as not = \n )
{
    if (this is a alphabetical char or number)
    {
        if (!inword)
        {
          j++; // start a new word
        }
        // save the char in a array[j][i] = c
    }
    else if (inword)
    {
         inword = false;
         // append \0 to the current string// array[j][i] = '\0'
    }
    else
    {
         // just discard this char // dont do i++
    }
}

```

hope it will help

google fgetc that might help aswell

---

### Post by TheLions on 2009-05-01
> **Arndt said:**
> You could look at 'strtok' too.

> **BugFixBug said:**
> i dont have the time to make a ready to go script but ill give you a rough example

```

for ( /* get char with fgetc and save it // in for *** long as not = \n )
{
    if (this is a alphabetical char or number)
    {
        if (!inword)
        {
          j++; // start a new word
        }
        // save the char in a array[j][i] = c
    }
    else if (inword)
    {
         inword = false;
         // append \0 to the current string// array[j][i] = '\0'
    }
    else
    {
         // just discard this char // dont do i++
    }
}

```

hope it will help

google fgetc that might help aswell


Thank you!

---

