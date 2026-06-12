---
title: "ruby symbols,  :string (colon followed by a string literal)"
date: 2009-09-14
forum: Programming Talk
---

### Post by cybo on 2009-09-14
i'm trying to understand what they (ruby symbols) mean but i'm still confused. other languages call it string interning. i have programmed before but as it turns out i didn't program much. can someone explain what is the purpose of ruby symbols and how do they work?

here is an example from the book:

:Object
:my_variable
:"Ruby rules"
a = 'cat'
:'catsup' --> :catsup
:'#{a}sup' --> :catsup
:'#{a}sup' --> :"\#{a}sup"

any help is appreciated.

---

### Post by Ruhe on 2009-09-15
Read: [http://www.rubytips.org/2008/01/26/what-is-a-ruby-symbol-symbols-explained/](http://www.rubytips.org/2008/01/26/what-is-a-ruby-symbol-symbols-explained/)

---

### Post by cybo on 2009-09-16
Ruhe, thanks for the link. it helped, somewhat. if anyone knows other links to ruby symbol explanations i would appreciate it

---

