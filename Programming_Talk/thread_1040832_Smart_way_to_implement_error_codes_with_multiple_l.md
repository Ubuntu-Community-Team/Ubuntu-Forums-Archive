---
title: "Smart way to implement error codes with multiple languages?"
date: 2009-01-15
forum: Programming Talk
---

### Post by psycovic23 on 2009-01-15
Hey,

I'm working on a problem where error codes (and potentially, anything text in the application) must be replaceable with the same thing in a different language.  What are the general schemes that people use for this?

I heard of 2 things:

1) error codes...

if (ERROR)
print errorcode(1234)

2) translation wrapper

if (ERROR)
print wrapper("invalid")

where wrapper would then lead to a big lookup table for everything under "invalid".

Are these pretty much the most widely used ones or are there more efficient ones? Thanks!

---

### Post by nvteighen on 2009-01-16
Implementing error codes? Just throw out a number that is meaniningful for the program and then use some translator if you want to give information to the user. Anyway, in C, usually you define error codes through preprocessor macros that allow you to use mnemonics when coding.

E.g:
```

#define OUT_OF_RANGE 567

```

So, you write OUT_OF_RANGE instead of remembering that "567" means that.

But, in languages using exception handling, all of these seems absurd.

---

### Post by mike_g on 2009-01-16
Yeah, I would do what nvteighen said. Then you could have a config file mapping error codes to messages. This could then be replced by diffent versions with different translations.

---

