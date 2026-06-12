---
title: "String or Text manipulation in (Dr)Scheme"
date: 2008-02-22
forum: Programming Talk
---

### Post by 1337455 10534 on 2008-02-22
Every language I try has a different approach to working with strings.
Scheme doesn't seem to have an approach at all.
You can define a function and required parameters, but unless you have an (and ( or a (cond ( you can't do multiple tasks in 1 function, and even if you do use them, all of those tasks must return a boolean value (in most cases they do not).

Say I want a function to move around strings (no, this isn't homework, but I will be learning Scheme next year in Intro to Programming so im curious.)
```

(define (flip3 a b c)
 (;; however i can rearrange a, b or c)
)
;; or is it with symbols? eg 'a 'b 'c?

```

---

### Post by ghostdog74 on 2008-02-22
this mindset is unacceptable, especially since I guess you are still schooling? you can't go around hating this language and hating that language if they don't "appeal" to you. ( probably because you already have this mindset that Python is "God" to you? )  Every languages has their quirks and their way of doing things and they are being used in different areas. You just have to open up your mind, accept and enjoy the learning process, while you still can. It will do you good in the future.

---

### Post by 1337455 10534 on 2008-02-22
I'm sorry for sounding like an idiot, but I just can't figure Scheme out.
Python is the only thing i really know.

---

### Post by ghostdog74 on 2008-02-22
here's one way you can go about. Forget any other languages and any negative thoughts you may have in your mind when you are learning a new language. Learn with an open mind.

---

### Post by lnostdal on 2008-02-23
i might not be able to help you .. i know Common Lisp very well and haven't used Scheme tbh .. i believe Scheme is a small language with a small library so you might not find as many tools to manipulate strings there as there are in other languages .. you might need to go "outside the standard" and find libraries that do what you need

for instance -- Common Lisp while being a much larger language and having a larger library, does not have support for regular expressions built in .. and to deal with this i need a library [http://weitz.de/cl-ppcre/](http://weitz.de/cl-ppcre/)

 .. but i need a question -- what are you looking for? .. maybe this [http://www.r6rs.org/final/html/r6rs/r6rs-Z-H-14.html#node_sec_11.12](http://www.r6rs.org/final/html/r6rs/r6rs-Z-H-14.html#node_sec_11.12)

edit:
hmm .. wait a sec .. ghostdog74 seems to be right .. this is just a rant from someone who is trying to skip past the first chapters of his Scheme book or tutorial isn't it?

---

