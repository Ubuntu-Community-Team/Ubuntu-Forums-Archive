---
title: "Problem with C Language Scanner"
date: 2011-07-18
forum: Programming Talk
---

### Post by rathin.saran on 2011-07-18
Hi Guys,

I am trying to write a tokenizer/scanner for the C programming language in C itself. The only issue(?) is that it is even recognising code fragments such as 

                + /* comment */ =
                - =
                * //comment
                =

as +=, -=, *= assignment operators.

It is fine with scanning +=, -= *= etc. when they come without any whitespaces in the middle.

No C compiler in my sight allows whitespaces like \n, \f, comments etc. in the middle of +=, -=, >>, etc. operators. Shall I fix my tokenizer code? Is this behavior tolerable according to the C language standards?

I am a noob undergrad and just curious.


Thanks in Advance!

---

### Post by GeneralZod on 2011-07-18
The C++ standard explicitly forbids tokens to contain whitespace (in which it includes comments, in this context) except in string literals and header names : I'd be extremely surprised if C differed from this.

---

### Post by rathin.saran on 2011-07-18
Thanks for your reply. I am going to fix the tokenizer soon. Thanks again!

---

