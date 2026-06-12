---
title: "Problem with DrRacket example"
date: 2012-02-20
forum: Programming Talk
---

### Post by xytron on 2012-02-20
I'm following the tutorial "An Introduction to Racket with Pictures" to become acquainted with Racket.

It's not working. It states that to draw pictures, I must first load some picture functions and to use
 
```

#lang slideshow

```

in the definitions area and click the "run" button, when I do that nothing happens but I don't get any error messages either.

Then I enter the code in the interactions area;

```

(circle 10)

```

only to get the following error;

**reference to undefined identifier: circle**

This happens with anything I try for* #lang*.

I am using the "Pretty Big" language.

Any ideas?

Thank you.

---

### Post by petru.marginean on 2012-07-14
I have a similar issue: I just downloaded the latest version (v5.2.1), I  chose the "Beginning Student" language, and I typed ```
#lang racket
``` in the top area, and pressed <Run>.
I get the error:
```
module: this function is not defined
```.

Any idea what's wrong?
What I could do to investigate this issue?

Here is a screenshot:

[IMG]http://dl.dropbox.com/u/65655385/drracket-error01.png[/IMG]

Thanks,
PM

---

### Post by dfeltey on 2012-07-14
As far as I can tell the problem is the interaction between choosing the  "Beginning Student" language and simultaneously trying to use the #lang directive.

If you choose "Beginning Student" as your language, then that is the language you will be writing in and the #lang directive is unsupported in this dialect of racket. 

To use the #lang directive, you need to, from the language menu, tell racket to use the language specified by the #lang directive.

---

### Post by petru.marginean on 2012-07-15
Thanks, using the option "Use the language declared in the source" (Language/Choose Language.." solved the issue.

Many thanks for help,
PM

---

