---
title: "Compiler warning message - how to solve?"
date: 2009-04-26
forum: Programming Talk
---

### Post by Krupski on 2009-04-26
Hi all,

I've got a small program that calls a function to free up "malloc'd" memory and print a string to stderr when called (if there's an error).

Here's the function:

```

int done(int rc, char *msg)
{
    free(buf);
    free(strings);
    if (msg != NULL) fprintf(stderr, "%s\n", msg);
    return rc;
}

```

...and I would typically use it like this:

```

[COLOR="Red"]**if (buf == NULL) return done(1, "error allocating buffer memory");**[/COLOR]

```

What's supposed to happen is:
(1) Free allocated memory
(2) Print the string passed as *msg
(3) Pass the return code from rc to the returned int of the function.

It all works, but I get this compiler warning:

```

nodups.c: In function ‘int main()’:
[COLOR="Red"]**nodups.c:30: warning: deprecated conversion from string constant to ‘char*’**[/COLOR]

```

What am I doing wrong?

Thanks in advance...

-- Roger

---

### Post by Namtabmai on 2009-04-26
change
```
int done(int rc, char *msg)
```

to

```
int done(int rc, const char *msg)
```

As the error said, "something" is a string **constant** but your original prototype introduces an implicit cast to a **non** constant string.

---

### Post by Krupski on 2009-04-26
> **Namtabmai said:**
> change
```
int done(int rc, char *msg)
```

to

```
int done(int rc, const char *msg)
```

As the error said, "something" is a string **constant** but your original prototype introduces an implicit cast to a **non** constant string.

Ah! I thought it was a const char problem... so I actually tried making the error strings like this:

```

    const char *err_msg[5] = {"msg1", "msg2"...etc...};

```

Then using "err_msg[n]" in place of the strings... but I got the same error message.

Now I see that I was on the right track, but the wrong road!  :)

Thanks so much for the help!

-- Roger

---

### Post by Krupski on 2009-04-26
Another quick question... is this legal (the part in red)?

```

const char *err_msg[6] = {
    [COLOR="Red"]**NULL,**[/COLOR]
    "allocating buffer memory",
    "allocating string pointer memory",
    "reallocating buffer memory",
    "reallocating string pointer memory",
    "reading standard input",
};

```

Is it legal to use "NULL" as a string?


Thanks!

-- Roger

---

### Post by Arndt on 2009-04-27
> **Krupski said:**
> Another quick question... is this legal (the part in red)?

```

const char *err_msg[6] = {
    [COLOR="Red"]**NULL,**[/COLOR]
    "allocating buffer memory",
    "allocating string pointer memory",
    "reallocating buffer memory",
    "reallocating string pointer memory",
    "reading standard input",
};

```

Is it legal to use "NULL" as a string?

Thanks!

-- Roger

Yes, "NULL" is supposed to be defined so it can be used as an expression which will be converted to a NULL pointer in any pointer context.

Just "0" has the same effect here, but "NULL" is clearer.

(I'm using double quotes here to set the literal expression apart from the concept of a NULL pointer. I don't mean the string syntax where the double quotes appear literally in the code - I would probably use code tag quoting for that.)

---

### Post by Krupski on 2009-04-27
> **Arndt said:**
> Yes, "NULL" is supposed to be defined so it can be used as an expression which will be converted to a NULL pointer in any pointer context.

Just "0" has the same effect here, but "NULL" is clearer.

(I'm using double quotes here to set the literal expression apart from the concept of a NULL pointer. I don't mean the string syntax where the double quotes appear literally in the code - I would probably use code tag quoting for that.)

Thank you for the reply!

Yes, I want (err_msg[0] == NULL) since the exit function I use depends on it to NOT print an error message if "NULL" is passed to it.

Thanks again!

-- Roger

---

