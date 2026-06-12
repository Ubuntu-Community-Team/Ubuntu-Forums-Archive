---
title: "[PHP/C] how would you do this?"
date: 2011-06-10
forum: Programming Talk
---

### Post by LoneWolfJack on 2011-06-10
Hey guys,

I'm currently doing some preparations for an upcoming PHP project and I'd like to ask for some input.

The project calls for PHP files (call them extensions) that can't be included by the core PHP application. I can't really give much more detail here without violating the NDA, but apparently the customer wants his clients to be able to add to the core project but without enabling them to access the core files or the database directly.

To make this more complex, the extensions can't be standalone scripts that you would call like "domain.tld/extension.php".

So far, I've come up with the following solutions:

1. in fact, I DO include the extensions via some sort of module management. This would, however, only work if it is possible to restrict PHP functionality on a per-folder basis regardless of the caller file. I highly doubt this would work (in fact, restricting functions on a per directory basis doesn't work at all last time I checked).

2. build an API. It seems, however, that performance would suffer because every shell command that is passed through PHP is executed in a new shell. Some testing confirmed that we're talking about 0.05 seconds per shell command - too much to be seriously considered.

3. build a PHP extension. this should work, but given that this would have to be in C, it would really strain the budget

4. ???

So basically, I'm wondering if someone has another idea I haven't come up with yet.

---

### Post by simeon87 on 2011-06-10
Why can't the scripts be standalone files? Can't an extension be a number of PHP files (the code) and a text file that lists all files of that extension (the index). Then, you can read that text file from your core PHP and see which code files are involved. You can then load those and call the appropriate functions (as defined clearly to your customer). Not sure how C comes into this picture though.

---

### Post by LoneWolfJack on 2011-06-10
Like I said, the customer doesn't want the clients to be able to access the core files. If we would use includes, it would be possible to at least get a list of functions of the core project as well as to access all globals.

You are not making much sense to me when it comes to your proposed solution. Can you rephrase please?

C would be involved when building an extension for PHP itself, just like the gd or mysql extensions.

---

### Post by simeon87 on 2011-06-10
I didn't know that include would enable the customer to access some of the functions/data in the core.

In that case my solution might not make sense. My idea was a text file with:

```
/extension/file_one.php
/extension/file_two.php
/extension/file_three.php
```

which can then be read by the core. You could also implement this in C is what I'm thinking now. Your software could then call predefined functions - based on whatever the extension is supposed to do, so something like:

```
func_one();
```

where func_one() is somewhere in the extension's code files and the list of functions that the customer can define is clearly defined.

---

### Post by LoneWolfJack on 2011-06-10
well, that won't work because we're looking for a bottom-up architecture. what you're proposing is a top-down architecture, which would greatly limit usefulness of the system. 

but thanks for trying to help.

---

### Post by simeon87 on 2011-06-10
How exactly does the core system interact with the extension then? You could also let the customer specify the available functions if you do not wish to dictate that.

---

### Post by LoneWolfJack on 2011-06-10
figuring out how to let core and extension communicate is the whole point. the core system will have to read the url and then decide what extension to trigger. the extension itself needs to be able to freely generate HTML code, but also has to be able to load relevant data through the core system (like, for example, users).

as soon as extension files are included, the extension will have direct access to the core system (functions, globals...), which is something the customer doesn't want.

---

### Post by simeon87 on 2011-06-10
> **LoneWolfJack said:**
> figuring out how to let core and extension communicate is the whole point. the core system will have to read the url and then decide what extension to trigger. the extension itself needs to be able to freely generate HTML code, but also has to be able to load relevant data through the core system (like, for example, users).

as soon as extension files are included, the extension will have direct access to the core system (functions, globals...), which is something the customer doesn't want.

If the extension needs to load data through the core system then the extension will always have access to some functions in the core. You could make an intermediate system which hides the core's functions but then the customer will have to call the functions in the intermediate system (which can be considered the exposed part of your core system).

At some point the extension will have to be aware of the core's existence (i.e., the functions that it can call) or, possibly, the core will have to know that an extension exists.

I don't think you can make a system with extensions that are oblivious to the core to which they belong because both must interact to do something meaningful.

---

### Post by LoneWolfJack on 2011-06-10
there are several possibilities, for example: namespaces and "friend" classes, but all of them have other drawbacks.

I have 15 years of experience writing PHP code myself, but because you can never know everything I was hoping someone would jump in with a clever idea to solve this problem.

in the end, the only feasible solution probably is a native PHP extension.

---

